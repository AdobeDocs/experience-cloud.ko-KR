---
title: 기능 그룹을 설정하여 점진적으로 롤아웃
description: Adobe Experience Rollouts에서 기능 그룹에 대한 비율 기반 점진적 롤아웃을 구성하는 방법을 알아봅니다.
source-git-commit: 9bfe0e55e89c1d7fbd77cde63831a6a186820e24
workflow-type: tm+mt
source-wordcount: '166'
ht-degree: 3%

---


# 기능 그룹을 설정하여 점진적으로 롤아웃 {#gradual-rollout-feature-group}

기능 그룹에 대한 롤아웃 비율이 **기본 정보** 탭에서 구성되었습니다. 롤아웃이 진행됨에 따라 언제든지 이 값을 위 또는 아래로 조정할 수 있습니다.

## 작동 방식 {#how-it-works}

롤아웃 비율(예: 60%)을 설정하면 정의된 대상자의 이 비율이 기능 그룹에 노출됩니다. 나머지 40%는 기본 동작을 받는 **컨트롤 그룹**&#x200B;에 배치됩니다.

(A/B 테스트를 위해) 여러 변형을 구성한 경우 노출 비율은 변형 간에 균등하게 분배됩니다. 예를 들어, 3개의 변형으로 60% 노출하면 변형당 20%가 되고, 대조군 그룹에서 40%가 됩니다.

언제든지 비율을 늘리거나 줄여 롤아웃을 확장, 축소 또는 일시 중지할 수 있습니다.

## 참조 - {#see-also}

* [기능 그룹 만들기](create-a-feature-group.md)
* [기능 플래그를 사용하여 A/B 테스트](a-b-testing.md)
* [점진적 롤아웃](../../concepts/gradual-rollout.md)
