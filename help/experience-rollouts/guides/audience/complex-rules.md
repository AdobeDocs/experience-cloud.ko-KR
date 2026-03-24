---
title: 복잡한 대상 규칙
description: 대량 값 제한 및 여러 조건에서 규칙을 분할하는 방법을 포함하여 Adobe Experience 롤아웃에서 크거나 복잡한 대상 규칙 세트로 작업하는 방법에 대해 알아봅니다.
source-git-commit: 3f3f7145b3c58dc721cbeb850e9e8571e3255bb1
workflow-type: tm+mt
source-wordcount: '234'
ht-degree: 0%

---


# 복잡한 대상 규칙 {#complex-rules}

## 벌크 값 제한 {#bulk-value-limits}

단일 대상 규칙(예: 긴 이메일 주소 목록)에 많은 수의 값을 추가할 때 규칙이 허용된 최대 크기를 초과했음을 나타내는 오류가 발생할 수 있습니다.

각 대상 규칙에는 속성당 크기 제한이 있습니다. 이메일 주소의 경우 제한은 고정된 수가 아닌 항목의 총 문자 길이에 따라 다릅니다. 일반적인 지침으로, 규칙당 약 **100-115개의 이메일 주소를 사용**&#x200B;하십시오.

이 제한이 허용하는 것보다 더 많은 항목을 타깃팅해야 하는 경우 목록을 더 작은 청크로 분할하고 중첩된 논리를 사용하여 개별 OR 연결 조건으로 적용합니다.

## 복잡한 규칙에 중첩 논리 사용 {#nested-logic}

중첩 논리를 사용하면 여러 대상 조건을 정확한 AND/OR 컨트롤과 결합할 수 있습니다. 활성화하려면:

1. 필요한 대상 조건을 추가합니다.
2. 대상 규칙 섹션에서 **중첩 논리**&#x200B;을(를) 사용하도록 설정합니다.
3. 각 조건에는 숫자가 지정됩니다. 이러한 숫자를 참조하는 논리 표현식을 입력합니다(예: ).
   * `1 and (2 or 3)`
   * `(1 and 2) or 3`
   * `(1 and 2) or (3 and 4)`

이것은 다른 기준과 함께 백분율 규칙에 사용된 것과 동일한 메커니즘입니다. 작동하는 예제는 [대상 기준에 백분율 규칙 추가](adding-percentage-rules.md)를 참조하십시오.

## 참조 - {#see-also}

* [기능 플래그 및 기능 그룹의 대상자](audience-in-feature-flags-and-feature-groups.md)
* [대상 기준에 백분율 규칙 추가](adding-percentage-rules.md)
* [릴리스 대상 규칙 업데이트](../feature-flags/update-release-audience-rules.md)
