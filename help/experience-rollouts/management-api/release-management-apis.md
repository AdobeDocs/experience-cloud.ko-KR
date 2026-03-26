---
title: 릴리스 관리 API
description: 릴리스 및 크로스 팀 기능 그룹을 가져오고, 만들고, 편집하기 위한 엔드포인트를 포함하여 Experience Rollouts 릴리스 관리 API에 대한 API 참조입니다.
exl-id: e8d1d025-0645-4cf2-921f-d94c9f71282d
source-git-commit: 454b5c719a5f8be82d1ed835da58bfca6316def2
workflow-type: tm+mt
source-wordcount: '490'
ht-degree: 13%

---

# 릴리스 관리 API {#release-management-apis}

릴리스 관리 API를 사용하면 프로그래밍 방식으로 릴리스 및 CTFG(크로스 팀 기능 그룹)를 검색, 생성 및 편집할 수 있습니다. 이러한 API는 v2 관리 엔드포인트를 사용합니다.

**기본 경로:** `/m/api/v2/mgmt/release`

모든 요청에는 [일반적인 요구 사항](feature-management-apis-overview.md#common-requirements)에 설명된 헤더와 아래 나열된 추가 헤더가 필요합니다.

## 추가 필수 헤더 {#additional-header}

| Header | 설명 | 필수 여부 |
|---|---|---|
| `x-user-context-org` | 조직의 숫자 팀 ID입니다. 이 값은 팀 설정 아래의 경험 롤아웃 콘솔에서 찾을 수 있습니다. | 예 |

## ID로 릴리스 가져오기 {#get-release}

숫자 ID로 단일 릴리스 또는 팀 간 기능 그룹을 검색합니다.

| | |
|---|---|
| **끝점** | `GET /m/api/v2/mgmt/release/{id}` |
| **메서드** | GET |

### 쿼리 매개변수 {#get-query-params}

| 매개변수 | 유형 | 설명 | 기본 |
|---|---|---|---|
| `includePermissions` | 부울 | 이 릴리스를 업데이트하거나 삭제할 수 있는 권한을 포함합니다. | `true` |
| `includeOrg` | 부울 | 이 릴리스에 대한 조직 정보를 포함합니다. | `true` |
| `includeAnalyzeInfo` | 부울 | 분석 정보를 포함합니다. | `false` |

### 응답 {#get-response}

| 상태 | 설명 |
|---|---|
| `200` | 성공. 응답 본문이 릴리스 개체입니다. [릴리스 개체 참조](#release-object)를 참조하십시오. |
| `400` | 잘못된 릴리스 ID 또는 잘못된 요청. |

## 릴리스 만들기 {#create-release}

새 릴리스 또는 팀 간 기능 그룹을 만듭니다.

| | |
|---|---|
| **끝점** | `POST /m/api/v2/mgmt/release` |
| **메서드** | POST |

### 요청 본문 {#create-request-body}

요청 본문에서 [Release 개체](#release-object)를 사용합니다. 만들 때는 팀 간 기능 그룹(`CROSS_TEAM_FEATURE_GROUP` 형식)의 경우 `status`을(를) `"SAVED"`(으)로, 표준 릴리스(`RELEASE` 형식)의 경우 `"DRAFT"`(으)로 설정해야 합니다.

**샘플 — 팀 간 기능 그룹 만들기:**

```json
{
  "params": {
    "rolloutType": "manual",
    "cohortingType": "guid",
    "tags": [],
    "canContextOverridePUP": false,
    "label": "my-cross-team-group"
  },
  "status": "SAVED",
  "type": "CROSS_TEAM_FEATURE_GROUP",
  "name": "my-cross-team-group",
  "description": null,
  "meta": "",
  "variations": [{ "variantPercentage": 100, "variantName": "Variant 1", "features": [] }],
  "audience": [{}],
  "clients": [],
  "pollInterval": 300,
  "org": { "id": "95" },
  "comment": ""
}
```

### 응답 {#create-response}

| 상태 | 설명 |
|---|---|
| `200` | 성공. 응답 본문은 생성된 릴리스 객체입니다. |
| `400` | 잘못된 페이로드. |

## 릴리스 편집 {#edit-release}

기존 릴리스 또는 팀 간 기능 그룹을 업데이트합니다. `id` 필드를 포함하는 전체 릴리스 개체를 전달합니다.

| | |
|---|---|
| **끝점** | `PUT /m/api/v2/mgmt/release/{id}` |
| **메서드** | PUT |

### 응답 {#edit-response}

| 상태 | 설명 |
|---|---|
| `200` | 성공. 응답 본문은 업데이트된 릴리스 개체입니다. |
| `417` | 동시 업데이트 충돌. 릴리스는 GET 및 PUT 호출 간에 수정되었습니다. 현재 릴리스를 가져온 후 다시 시도하십시오. |

## 릴리스 개체 참조 {#release-object}

| 필드 | 유형 | 설명 | 필수 여부 |
|---|---|---|---|
| `id` | 정수 | 릴리스 ID. 업데이트 호출에만 필요합니다. | 조건부 |
| `name` | 문자열 | 릴리스 이름. 최대 50자. 패턴: `^[a-zA-Z0-9_ ,.:()-]*$`. 고유해야 합니다. | 예 |
| `description` | 문자열 | 선택적 설명. 최대 255자. | 아니요 |
| `type` | 문자열 | 표준 릴리스의 경우 `"RELEASE"`, 팀 간 기능 그룹의 경우 `"CROSS_TEAM_FEATURE_GROUP"`입니다. | 예 |
| `status` | 문자열 | 릴리스 상태. IMS의 경우: 만들기 시 `"DRAFT"`; 업데이트 시 `"DRAFT"`, `"SAVED"`, `"PUBLISHED"`. CTFG의 경우 `"SAVED"`을(를) 만들 때, `"SAVED"`을(를) 업데이트할 때 `"PUBLISHED"`을(를) 만듭니다. | 예 |
| `clients` | 배열 | 이 릴리스와 연결된 애플리케이션. 각 항목에는 `id`(숫자) 및 `imsClientId`(문자열)이 필요합니다. | 아니요 |
| `audience` | 배열 | 대상 규칙 목록입니다. [조건 개체](feature-flags-management-api.md#condition-object)를 참조하십시오. | 아니요 |
| `variations` | 배열 | 변형 목록. 제출 중에는 1개의 변형만 지원됩니다. | 제출에 필요 |
| `params` | 오브젝트 | 릴리스 매개 변수. [지원되는 매개 변수 필드](#supported-params)를 참조하십시오. | 제출에 필요 |
| `org` | 오브젝트 | 조직 개체. `id`을(를) 포함해야 합니다. | 아니요 |

### 지원되는 매개변수 필드 {#supported-params}

| 필드 | 유형 | 설명 | 필수 여부 |
|---|---|---|---|
| `label` | 문자열 | 표시 이름. 최대 50자. | 예 |
| `tags` | Array\&lt;String\> | 선택적 태그입니다. 각각 최대 50자까지 사용할 수 있습니다. | 아니요 |
| `canContextOverridePUP` | 부울 | `true`이면 컨텍스트 규칙이 프로필 규칙을 재정의합니다. 기본값: `false`. | 예 |
| `isBetaRelease` | 부울 | `true`이면 베타 릴리스로 표시합니다. 기본값: `false`. | 아니요 |

### 변형 개체 {#variation-object}

| 필드 | 유형 | 설명 | 필수 여부 |
|---|---|---|---|
| `id` | 정수 | 변형 ID. 업데이트 호출에만 필요합니다. | 조건부 |
| `variantName` | 문자열 | 변형 이름. 최대 50자. | 예 |
| `variantPercentage` | 더블 | 이 변형을 받는 대상자의 백분율입니다. 범위: [0, 100]. | 예 |
| `features` | 배열 | 이 변형에 포함된 기능입니다. 각 항목에는 `id`, `name`, `clientId` 및 `state`이(가) 포함되어야 합니다. | 아니요 |

## 참조 - {#see-also}

* [기능 관리 API 개요](feature-management-apis-overview.md)
* [기능 플래그 관리 API](feature-flags-management-api.md)
* [기능 그룹 관리 API](feature-group-management-api.md)
