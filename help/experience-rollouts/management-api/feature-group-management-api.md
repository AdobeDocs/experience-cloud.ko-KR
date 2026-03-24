---
title: 기능 그룹 관리 API
description: 기능 그룹의 롤아웃 계획을 가져오고, 만들고, 업데이트하고, 삭제하고, 제어할 끝점을 포함하여 경험 롤아웃 기능 그룹 관리 API에 대한 API 참조입니다.
source-git-commit: db719ba7b9db91aea818d8ef216a28fcedc6aa65
workflow-type: tm+mt
source-wordcount: '575'
ht-degree: 14%

---


# 기능 그룹 관리 API {#feature-group-management-api}

기능 그룹 관리 API를 사용하면 자동화된 및 A/B 테스트 롤아웃 계획을 포함하여 경험 롤아웃에서 기능 그룹을 프로그래밍 방식으로 생성, 읽기, 업데이트 및 삭제할 수 있습니다.

**기본 경로:** `/m/api/v1/mgmt/group`

모든 요청에는 [일반적인 요구 사항](feature-management-apis-overview.md#common-requirements)에 설명된 헤더가 필요합니다.

## 모든 기능 그룹 가져오기 {#get-all-groups}

조직의 모든 기능 그룹을 검색합니다.

| | |
|---|---|
| **끝점** | `GET /m/api/v1/mgmt/group` |
| **메서드** | GET |

### 쿼리 매개변수 {#get-all-query-params}

| 매개변수 | 유형 | 설명 | 필수 여부 |
|---|---|---|---|
| `myOrg` | 부울 | 조직 정보를 포함하려면 `true`(으)로 설정하십시오. | 예 |
| `includeClientInfo` | 부울 | 각 그룹의 응용 프로그램 정보를 포함하려면 `true`(으)로 설정하십시오. | 예 |

### 응답 {#get-all-response}

| 상태 | 설명 |
|---|---|
| `200` | 성공. 응답 본문은 기능 그룹 객체의 배열입니다. |

## ID별 기능 그룹 가져오기 {#get-group-by-id}

숫자 ID로 단일 피쳐 그룹을 검색합니다.

| | |
|---|---|
| **끝점** | `GET /m/api/v1/mgmt/group/{groupId}` |
| **메서드** | GET |
| **쿼리 매개 변수** | `includeAnalyzeInfo=true`(선택 사항 — 응답에 analytics 데이터 추가) |

### 응답 {#get-by-id-response}

| 상태 | 설명 |
|---|---|
| `200` | 성공. 응답 본문은 피쳐 그룹 개체입니다. |
| `400` | 기능 그룹 ID가 잘못되었습니다. |

## 기능 그룹 만들기 {#create-group}

수동, 자동화된 또는 A/B 테스트 롤아웃 유형으로 새 기능 그룹을 만듭니다.

| | |
|---|---|
| **끝점** | `POST /m/api/v1/mgmt/group` |
| **메서드** | POST |

### 요청 본문 {#create-request-body}

요청 본문에서 [기능 그룹 개체](#feature-group-object)를 사용합니다. `params` 내의 `rolloutType`은(는) 필수이며 페이로드의 구조를 결정합니다.

**샘플 — 수동 롤아웃:**

```json
{
  "params": {
    "rolloutType": "manual",
    "label": "my-feature-group",
    "tags": [],
    "canContextOverridePUP": false
  },
  "status": "SAVED",
  "type": "group",
  "name": "my.feature.group",
  "description": "A manual feature group",
  "variations": [{ "variantPercentage": 100, "variantName": "Variant 1", "features": [] }],
  "audience": [{ "criteria": { "and": [{ "operator": "EQ", "attr": "COUNTRY", "val": "US", "ruleId": 1, "category": "default" }] } }],
  "clients": [],
  "org": { "id": 95 }
}
```

### 응답 {#create-response}

| 상태 | 설명 |
|---|---|
| `200` | 성공. 응답 본문은 생성된 피쳐 그룹 개체입니다. |
| `400` | 페이로드가 잘못되었습니다. 자세한 내용은 [오류 메시지](#error-messages)를 참조하세요. |
| `403` | 권한이 부족합니다. |

## 기능 그룹 업데이트 {#update-group}

기존 기능 그룹을 업데이트합니다. `id` 필드를 포함하여 만들기 요청 본문과 동일한 구조를 전달합니다.

| | |
|---|---|
| **끝점** | `PUT /m/api/v1/mgmt/group` |
| **메서드** | PUT |

### 응답 {#update-response}

| 상태 | 설명 |
|---|---|
| `200` | 성공. 응답 본문은 업데이트된 피쳐 그룹 개체입니다. |
| `400` | 잘못된 페이로드. |
| `403` | 권한이 부족합니다. |

## 기능 그룹 삭제 {#delete-group}

숫자 ID로 피쳐 그룹을 삭제합니다.

| | |
|---|---|
| **끝점** | `DELETE /m/api/v1/mgmt/group/{groupId}` |
| **메서드** | DELETE |

### 응답 {#delete-response}

| 상태 | 설명 |
|---|---|
| `204` | 성공. 응답 본문이 없습니다. |
| `403` | 권한이 부족합니다. |

## 피쳐 그룹 개체 참조 {#feature-group-object}

| 필드 | 유형 | 설명 | 필수 여부 |
|---|---|---|---|
| `id` | 정수 | 기능 그룹 ID. 업데이트 호출에만 필요합니다. | 조건부 |
| `name` | 문자열 | 기능 그룹 키. 최대 50자. 패턴: `^[a-zA-Z0-9_.-]*$` | 예(만들기) |
| `clients` | 배열 | 그룹과 연계된 애플리케이션. 각 항목에는 `id` 및 `imsClientId`이(가) 포함되어야 합니다. | 예 |
| `status` | 문자열 | `"SAVED"` 또는 `"PUBLISHED"` | 예 |
| `type` | 문자열 | 기능 그룹에 대해 항상 `"group"`을(를) 사용합니다. | 예 |
| `org` | 오브젝트 | 조직 세부 정보. `id`을(를) 포함해야 합니다. | 예 |
| `params` | 오브젝트 | 그룹 매개 변수. `rolloutType` 은(는) 필수입니다(`"manual"`, `"automated"` 또는 `"ab-testing"`). `label` 및 `tags`도 지원합니다. | 예 |
| `audience` | 배열 | 수동 롤아웃 유형에 대한 대상 규칙. | 아니요 |
| `variations` | 배열 | 변형 목록. [FeatureGroupVariation 개체](#featuregroupvariation-object)를 참조하십시오. | 아니요 |
| `phaseRollOutPlan` | 오브젝트 | 단계 롤아웃 계획. 자동화된 테스트 및 A/B 테스트 유형에 필요합니다. [PhaseRollOutPlan 개체](#phaserolloutplan-object)를 참조하십시오. | 조건부 |
| `description` | 문자열 | 선택적 표시 설명. 최대 225자. | 아니요 |

### FeatureGroupVariation 개체 {#featuregroupvariation-object}

| 필드 | 유형 | 설명 | 필수 여부 |
|---|---|---|---|
| `id` | 정수 | 변형 ID. 업데이트 호출에만 필요합니다. | 조건부 |
| `variantName` | 문자열 | 변형 이름. `"Variant 1"`(으)로 하드코딩됨. | 예 |
| `variantPercentage` | 소수 | 이 변형을 받는 대상자의 백분율입니다. 은(는) 0보다 크고 100보다 커야 합니다. | 예 |

### PhaseRollOutPlan 개체 {#phaserolloutplan-object}

| 필드 | 유형 | 설명 | 필수 여부 |
|---|---|---|---|
| `phaseRollOutBlocks` | 배열 | 단계 블록 및 대기 블록의 순서가 지정된 목록입니다. 마지막 블록은 단계 블록이어야 합니다. | 예 |
| `rollOutPlanState` | 문자열 | `"DRAFT"`, `"RUNNING"`, `"PAUSED"` 또는 `"ABORTED"` | 예 |

`phaseRollOutBlocks`의 각 블록은 대상 기준이 있는 `phaseRule`을(를) 포함하는 **단계 블록**(`isPhaseBlock: true`) 또는 `waitDuration`(상대) 또는 `executionDate`(고정 타임스탬프)을(를) 포함하는 `waitRule`을(를) 포함하는 **대기 블록**(`isPhaseBlock: false`)입니다.

## 오류 메시지 {#error-messages}

| 조건 | 상태 | 오류 메시지 |
|---|---|---|
| 이름이 잘못되었거나 비어 있음 | 400 | `Error: Invalid value for release name.` |
| 빈 대상 기준 | 400 | `Error: Release is not valid` |
| 자동화된 유형에 대한 여러 변형 | 400 | `Error: Feature variation is not valid. Variation name should be unique across variations` |
| 클라이언트가 없는 게시된 그룹 | 400 | `Error: At least one client must be associated with enabled feature group.` |
| 플랜의 마지막 블록이 단계 블록이 아닙니다. | 400 | `Error: The last block in the Phase Rollout plan should be phase block` |
| 대기 블록 시간 순서가 잘못됨 | 400 | `Error: Wait block timings are not in order in the phase rollout plan` |
| 일관성 없는 대기 블록 유형 | 400 | `Error: Wait block should be of same type.` |
| 활성화된 단계 블록 편집 | 400 | `Error: Activated phase block should not be changed` |
| 빈 롤아웃 유형 | 400 | `Error: Rollout type cannot be empty while feature group creation` |
| 단계 계획이 수동 유형으로 통과됨 | 400 | `Error: PhaseRollOutPlan can't be added with manual rollout type while feature group creation` |
| 일정이 게시됨 상태로 전달됨 | 400 | `Error: Schedule can't be added in published state while release/group creation` |

## 참조 - {#see-also}

* [기능 관리 API 개요](feature-management-apis-overview.md)
* [기능 플래그 관리 API](feature-flags-management-api.md)
* [관리 패치 API](management-patch-api.md)
