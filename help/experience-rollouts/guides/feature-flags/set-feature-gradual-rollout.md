---
title: 점진적으로 롤아웃할 기능 설정
description: Adobe Experience Rollouts의 기능 플래그에 대한 비율 기반 점진적 롤아웃을 구성하는 방법을 알아봅니다.
source-git-commit: 9bfe0e55e89c1d7fbd77cde63831a6a186820e24
workflow-type: tm+mt
source-wordcount: '148'
ht-degree: 3%

---


# 점진적으로 롤아웃할 기능 설정 {#gradual-rollout-feature}

기능 플래그에 대한 롤아웃 비율이 **기본 정보** 탭에서 구성되었습니다. 롤아웃이 진행됨에 따라 언제든지 이 값을 위 또는 아래로 조정할 수 있습니다.

## 작동 방식 {#how-it-works}

롤아웃 비율(예: 25%)을 설정하면 정의된 대상자의 해당 비율이 기능에 노출됩니다. 나머지 비율은 기본 경험을 받는 **컨트롤 그룹**&#x200B;에 배치됩니다.

롤아웃을 확장하거나 축소하기 위해 시간이 지남에 따라 비율을 늘리거나 줄일 수 있습니다. 비율을 0%로 낮추면 플래그를 삭제하지 않고 대상에 있는 모든 사람에게 기능이 효과적으로 꺼집니다.

## 참조 - {#see-also}

* [점진적 롤아웃](../../concepts/gradual-rollout.md)
* [기능 그룹을 설정하여 점진적으로 롤아웃](set-feature-group-gradual-rollout.md)
* [첫 번째 기능 플래그 만들기](create-your-first-feature-flag.md)
