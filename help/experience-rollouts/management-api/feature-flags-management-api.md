---
title: 기능 플래그 관리 API
description: 애플리케이션에 대한 기능 플래그를 가져오고, 만들고, 업데이트하고, 삭제할 엔드포인트를 비롯한 경험 롤아웃 기능 플래그 관리 API에 대한 API 참조입니다.
source-git-commit: 8a92b7a3e8c52da8bb2474f52c831e159420b878
workflow-type: tm+mt
source-wordcount: '650'
ht-degree: 12%

---


# 기능 플래그 관리 API {#feature-flags-management-api}

기능 플래그 관리 API를 사용하면 경험 롤아웃에서 애플리케이션에 대한 기능 플래그를 프로그래밍 방식으로 생성, 읽기, 업데이트 및 삭제할 수 있습니다.

**기본 경로:** `/m/api/v1/mgmt/feature`

모든 요청에는 [일반적인 요구 사항](feature-management-apis-overview.md#common-requirements)에 설명된 헤더가 필요합니다.

## 모든 기능 플래그 가져오기 {#get-all-features}

지정된 응용 프로그램에 대한 모든 기능 플래그를 검색합니다.

| | |
|---|---|
| **끝점** | `GET /m/api/v1/mgmt/feature` |
| **메서드** | GET |

### 쿼리 매개변수 {#get-all-query-params}

| 매개변수 | 유형 | 설명 | 필수 여부 |
|---|---|---|---|
| `clientId` | 정수 | 애플리케이션의 숫자 ID입니다. [클라이언트 ID 가져오기](get-client-id.md)를 참조하십시오. `imsClientId`이(가) 제공되지 않으면 필수입니다. | 조건부 |
| `imsClientId` | 문자열 | 애플리케이션의 문자열 형식 클라이언트 ID. `clientId`이(가) 제공되지 않으면 필수입니다. | 조건부 |
| `nonReleaseFeature` | 부울 | 그룹 또는 릴리스와 연결되지 않은 독립 기능 플래그를 포함하려면 `true`(으)로 설정하십시오. API 기반 워크플로에 필요합니다. | 예 |

### 응답 {#get-all-response}

| 상태 | 설명 |
|---|---|
| `200` | 성공. 응답 본문에 기능 플래그 객체 목록이 포함되어 있습니다. |

응답 본문에 `features` 배열이 있습니다. 각 요소는 [FeatureDTO 개체 참조](#featuredto-object)에 설명된 필드가 있는 기능 플래그 개체입니다.

**샘플 응답:**

```json
{
  "features": [
    {
      "id": 22079,
      "name": "new.FF.1",
      "clientId": 1191,
      "state": "enabled",
      "description": "first feature flag",
      "release": { "id": 2631, "name": "FF.group", "status": "SAVED" },
      "audience": null,
      "params": { "label": "new FF 1", "rolloutType": "manual" }
    },
    {
      "id": 22080,
      "name": "new.FF.2",
      "clientId": 1191,
      "state": "enabled",
      "description": "second feature flag",
      "audience": [
        {
          "id": 10034665,
          "criteria": { "and": [{ "operator": "EQ", "attr": "LOCALE", "val": "EN" }] }
        }
      ]
    }
  ]
}
```

## ID별 기능 플래그 가져오기 {#get-feature-by-id}

숫자 ID로 단일 기능 플래그를 검색합니다.

| | |
|---|---|
| **끝점** | `GET /m/api/v1/mgmt/feature/{featureId}` |
| **메서드** | GET |

### 응답 {#get-by-id-response}

| 상태 | 설명 |
|---|---|
| `200` | 성공. 응답 본문이 단일 [FeatureDTO 개체](#featuredto-object)입니다. |
| `400` | 기능 ID가 잘못되었습니다. |

## 기능 플래그 만들기 {#create-feature}

새 기능 플래그를 만듭니다.

| | |
|---|---|
| **끝점** | `POST /m/api/v1/mgmt/feature` |
| **메서드** | POST |

### 요청 본문 {#create-request-body}

요청 본문은 [FeatureDTO 개체](#featuredto-object)입니다. 작성하려면 다음 필드가 필요합니다.

| 필드 | 필수 여부 | 참고 |
|---|---|---|
| `name` | 예 | 기능 플래그 키. 최대 50자. 패턴: `^[a-zA-Z0-9_.-]*$` |
| `clientId` | 예 | 숫자 애플리케이션 ID입니다. [클라이언트 ID 가져오기](get-client-id.md)를 참조하십시오. |
| `state` | 예 | `"enabled"` 또는 `"disabled"` |

### 응답 {#create-response}

| 상태 | 설명 |
|---|---|
| `200` | 성공. 응답 본문에 `{ "generatedFeatureId": <id> }`이(가) 포함되어 있습니다. |
| `400` | 잘못된 페이로드. |
| `403` | 이 클라이언트 또는 대상 규칙에 대한 권한이 부족합니다. |
| `417` | 개발자 역할이 있는 사용자는 공용 규칙이 있는 기능을 저장할 수 없습니다. 하나 이상의 대상 규칙이 필요합니다. |

**샘플 요청:**

```json
{
  "name": "my-new-feature",
  "clientId": 1191,
  "state": "disabled",
  "description": "A new feature flag",
  "meta": "VGVzdA==",
  "audience": [
    {
      "criteria": {
        "and": [{ "operator": "EQ", "attr": "COUNTRY", "category": "default", "ruleId": 1, "val": "US" }]
      }
    }
  ],
  "variations": [{ "variantPercentage": 100, "variantName": "Variation 1" }],
  "params": { "label": "My New Feature", "tags": [] }
}
```

## 기능 플래그 업데이트 {#update-feature}

기존 기능 플래그를 업데이트합니다. `id` 필드를 포함하여 전체 [FeatureDTO 개체](#featuredto-object)를 전달합니다.

| | |
|---|---|
| **끝점** | `PUT /m/api/v1/mgmt/feature` |
| **메서드** | PUT |

### 응답 {#update-response}

| 상태 | 설명 |
|---|---|
| `200` | 성공. 응답 본문은 업데이트된 FeatureDTO 개체입니다. |
| `400` | 잘못된 페이로드. |
| `403` | 권한이 부족합니다. |
| `417` | 동시 업데이트 충돌. 먼저 현재 기능을 가져온 다음 `params`의 최신 `version` 값으로 다시 시도하십시오. |

## 기능 플래그 삭제 {#delete-feature}

숫자 ID로 기능 플래그를 삭제합니다.

| | |
|---|---|
| **끝점** | `DELETE /m/api/v1/mgmt/feature/{featureId}` |
| **메서드** | DELETE |

### 응답 {#delete-response}

| 상태 | 설명 |
|---|---|
| `204` | 성공. 응답 본문이 없습니다. |
| `403` | 권한이 부족합니다. |

## FeatureDTO 개체 참조 {#featuredto-object}

| 필드 | 유형 | 설명 | 필수 여부 |
|---|---|---|---|
| `id` | 정수 | 기능 플래그 ID. 업데이트 호출에만 필요합니다. | 조건부 |
| `name` | 문자열 | 기능 플래그 키(API 응답으로 반환됨). 최대 50자. 패턴: `^[a-zA-Z0-9_.-]*$` | 예(만들기) |
| `clientId` | 정수 | 숫자 애플리케이션 ID입니다. | 예 |
| `state` | 문자열 | `"enabled"` 또는 `"disabled"` | 예 |
| `meta` | 문자열 | API 응답의 기능과 함께 Base64로 인코딩된 메타데이터가 반환되었습니다. 최대 1024자. | 아니요 |
| `description` | 문자열 | 설명을 표시합니다. 최대 225자. | 아니요 |
| `audience` | 배열 | 대상 규칙 목록입니다. [FeatureRule 개체](#featurerule-object)를 참조하십시오. 이 항목을 생성하려면 [원하는 대상 기준을 얻으십시오](get-audience-criteria.md). | 아니요 |
| `variations` | 배열 | 변형 목록. 최대 3. [FeatureVariation 개체](#featurevariation-object)를 참조하십시오. | 아니요 |
| `params` | 오브젝트 | 추가 메타데이터. 지원되는 키: `label`(UI의 표시 이름), `tags`(문자열 배열). | 아니요 |
| `release` | 오브젝트 | 릴리스/그룹 연결. `null` 플래그가 그룹에 없는 경우. 읽기 전용. | 아니요 |

### FeatureVariation 개체 {#featurevariation-object}

| 필드 | 유형 | 설명 | 필수 여부 |
|---|---|---|---|
| `id` | 정수 | 변형 ID. 업데이트 호출에만 필요합니다. | 조건부 |
| `variantName` | 문자열 | 변형 이름. 고정 값: `"Variation 1"`, `"Variation 2"`, `"Variation 3"`. | 예 |
| `variantPercentage` | 소수 | 이 변형을 받는 대상자의 백분율입니다. 은(는) 0보다 크고 100보다 작아야 하며 최대 소수 둘째 자리가 있어야 합니다. | 예 |

### FeatureRule 개체 {#featurerule-object}

| 필드 | 유형 | 설명 | 필수 여부 |
|---|---|---|---|
| `id` | 정수 | 규칙 ID. 업데이트 호출에만 필요합니다. 새 규칙을 추가할 때 `null`(으)로 설정합니다. | 조건부 |
| `criteria` | 오브젝트 | 대상 규칙을 정의하는 조건 개체입니다. [조건 개체](#condition-object)를 참조하십시오. | 예 |

### 조건 개체 {#condition-object}

| 필드 | 유형 | 설명 |
|---|---|---|
| `and` | Array\&lt;Condition\> | 모든 조건이 참이어야 합니다. |
| `or` | Array\&lt;Condition\> | 하나 이상의 조건이 true여야 합니다. |
| `not` | 조건 | 이 조건은 false여야 합니다. |
| `attr` | 문자열 | 평가할 사용자 특성(예: `COUNTRY`, `LOCALE`). |
| `operator` | 문자열 | 비교 연산자(예: `EQ`, `IN`, `LT`). |
| `val` | 문자열 | 비교할 값입니다. |
| `meta` | 오브젝트 | 선택적 조건 메타데이터입니다. `desc` 필드는 UI에서 표시 레이블을 설정합니다. |

각 조건에서 `and`, `or` 또는 `not` 중 하나 또는 `attr`, `operator` 및 `val`의 조합을 제공해야 합니다.

## 참조 - {#see-also}

* [기능 관리 API 개요](feature-management-apis-overview.md)
* [관리 패치 API](management-patch-api.md)
* [애플리케이션에 대한 클라이언트 ID 가져오기](get-client-id.md)
* [원하는 대상 기준 가져오기](get-audience-criteria.md)
