---
title: 관리 패치 API
description: Experience Rollouts PATCH API를 사용하여 전체 개체를 전달하지 않고 기능 플래그, 기능 그룹 또는 팀 간 기능 그룹의 개별 필드를 업데이트합니다.
source-git-commit: 6ecedbfc6c7de392f214f3f8f2e71aa18e1bacb9
workflow-type: tm+mt
source-wordcount: '301'
ht-degree: 3%

---


# 관리 패치 API {#management-patch-api}

PATCH API를 사용하면 요청 본문에서 전체 개체를 전송하지 않고 기능 플래그, 기능 그룹 또는 크로스 팀 기능 그룹의 특정 필드를 업데이트할 수 있습니다. 이 기능은 대상 규칙 변경, 상태 전환 또는 변형 백분율 조정과 같은 타겟팅된 업데이트에 유용합니다.

## 기능 플래그 PATCH {#feature-flag-patch}

기능 플래그의 하나 이상의 필드를 업데이트합니다.

| | |
|---|---|
| **끝점** | `PATCH /m/api/v1/mgmt/feature/{featureFlagId}` |
| **메서드** | PATCH |

### 요청 헤더 {#ff-request-headers}

모든 요청에는 [일반적인 요구 사항](feature-management-apis-overview.md#common-requirements)에 설명된 헤더가 필요합니다.

### 경로 매개 변수 {#ff-path-param}

| 매개변수 | 유형 | 설명 | 필수 여부 |
|---|---|---|---|
| `featureFlagId` | 정수 | 업데이트할 기능 플래그의 숫자 ID입니다. | 예 |

### 요청 본문 {#ff-request-body}

업데이트할 필드만 전달합니다. 이 응답은 항상 업데이트된 기능 플래그 개체 전체를 반환합니다.

**예 — 설명 업데이트만:**

```json
{
  "description": "Updated description"
}
```

**예 — 기존 대상 제거:**

```json
{
  "audience": null
}
```

**예 — 대상이 없을 때 새 대상을 추가합니다.**

```json
{
  "audience": [
    {
      "criteria": {
        "and": [
          { "operator": "EQ", "attr": "sandboxType", "val": "DEVELOPMENT", "ruleId": 1, "category": "contextual" }
        ]
      }
    }
  ]
}
```

**예 — 기존 대상 규칙을 업데이트합니다.**

```json
{
  "audience": [
    {
      "id": 10020035,
      "criteria": {
        "and": [
          { "operator": "EQ", "attr": "sandboxType", "val": "PRODUCTION", "ruleId": 1, "category": "contextual" }
        ]
      }
    }
  ]
}
```

**예 — 상태 및 변형 비율 변경:**

```json
{
  "state": "disabled",
  "variations": [
    {
      "id": 10017188,
      "variantName": "Variation 1",
      "variantPercentage": 80.0
    }
  ]
}
```

>[!NOTE]
>
>기존 대상 규칙을 업데이트할 때 규칙의 `id`(GET 기능 응답에서 사용 가능)을 포함하여 적절히 업데이트하십시오. 변형을 업데이트할 때 중복을 만들지 않도록 변형의 `id`을(를) 포함하십시오.

### 응답 {#ff-response}

| 상태 | 설명 |
|---|---|
| `200` | 성공. 응답 본문은 완전히 업데이트된 기능 플래그 객체입니다. |
| `400` | 잘못된 페이로드. |
| `403` | 권한이 부족합니다. |
| `417` | 동시 업데이트 충돌. 현재 기능을 가져온 후 다시 시도하십시오. |

## 기능 그룹 PATCH {#feature-group-patch}

기능 그룹의 하나 이상의 필드를 업데이트합니다. 요청 및 응답 구조는 기능 플래그 PATCH과 동일합니다. 끝점만 다릅니다.

| | |
|---|---|
| **끝점** | `PATCH /m/api/v1/mgmt/group/{featureGroupId}` |
| **메서드** | PATCH |

## 크로스 팀 기능 그룹 PATCH {#ctfg-patch}

팀 간 기능 그룹의 하나 이상의 필드를 업데이트합니다. v2 릴리스 끝점을 사용합니다.

| | |
|---|---|
| **끝점** | `PATCH /m/api/v2/mgmt/release/{CTFGId}` |
| **메서드** | PATCH |

## 참조 - {#see-also}

* [기능 플래그 관리 API](feature-flags-management-api.md)
* [기능 그룹 관리 API](feature-group-management-api.md)
* [릴리스 관리 API](release-management-apis.md)
* [기능 관리 API 개요](feature-management-apis-overview.md)
