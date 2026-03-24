---
title: 원하는 대상 기준 가져오기
description: 콘솔 및 GET 기능 API를 사용하여 Experience 롤아웃 관리 API에서 사용할 올바른 대상 기준 JSON 구조를 생성하는 방법에 대해 알아봅니다.
source-git-commit: 6ecedbfc6c7de392f214f3f8f2e71aa18e1bacb9
workflow-type: tm+mt
source-wordcount: '224'
ht-degree: 1%

---


# 원하는 대상 기준 가져오기 {#get-audience-criteria}

관리 API의 대상 기준 필드는 손으로 작성하기 복잡할 수 있는 구조화된 JSON 형식을 사용합니다. 권장 접근 방법은 콘솔을 사용하여 원하는 대상자를 작성한 다음 API를 통해 JSON 표현식을 검색하는 것입니다.

## 단계 {#steps}

원하는 대상 기준에 대한 JSON을 가져오려면 다음 단계를 수행합니다.

1. Experience Rollouts 콘솔에서 API 호출에 사용할 대상 기준을 사용하여 임시 기능 플래그를 만듭니다.
2. 저장한 후 브라우저 URL에서 기능 플래그 ID를 확인합니다. 이 ID는 클라이언트 ID 뒤에 있는 URL에 표시됩니다. 예를 들어 `.../feature-flags/1191/22080`에서 기능 ID는 `22080`입니다.
3. 해당 기능 ID를 사용하여 [ID별 기능 가져오기](feature-flags-management-api.md#get-feature-by-id) 끝점을 호출합니다.
4. 응답 JSON에서 `audience` 필드를 찾습니다. 여기에는 필요한 정확한 대상 기준 구조가 포함되어 있습니다.
5. `audience` 값을 복사하여 각 규칙 개체에서 `id` 특성을 제거합니다. 기능 API 만들기 또는 업데이트 호출에서 사용하십시오.

## 예 {#example}

GET `/m/api/v1/mgmt/feature/22080`을(를) 호출한 후 응답에는 다음이 포함됩니다.

```json
{
  "audience": [
    {
      "id": 10034665,
      "criteria": {
        "and": [
          {
            "operator": "EQ",
            "attr": "LOCALE",
            "val": "EN",
            "ruleId": 1,
            "category": "default"
          }
        ]
      }
    }
  ]
}
```

기능 만들기 호출에서 사용하려면 대상 개체에서 `id` 필드를 제거하십시오.

```json
{
  "audience": [
    {
      "criteria": {
        "and": [
          {
            "operator": "EQ",
            "attr": "LOCALE",
            "val": "EN",
            "ruleId": 1,
            "category": "default"
          }
        ]
      }
    }
  ]
}
```

## 참조 - {#see-also}

* [기능 플래그 관리 API](feature-flags-management-api.md)
* [애플리케이션에 대한 클라이언트 ID 가져오기](get-client-id.md)
* [관리 패치 API](management-patch-api.md)
