---
title: 환경 개요
description: Adobe Experience Rollouts의 단계 및 프로덕션 환경과 각 환경을 사용해야 하는 시기에 대해 알아봅니다.
source-git-commit: 9bfe0e55e89c1d7fbd77cde63831a6a186820e24
workflow-type: tm+mt
source-wordcount: '204'
ht-degree: 4%

---


# 환경 개요 {#environments}

경험 롤아웃은 개별 환경을 제공하므로 라이브 사용자에게 변경 사항을 홍보하기 전에 기능 플래그를 확인할 수 있습니다.

## 사용 가능한 환경 {#available-environments}

| 환경 | 용도 |
|---|---|
| **단계** | 테스트 및 유효성 검사. 이 환경을 사용하여 기능 플래그를 프로덕션에서 활성화하기 전에 구성하고 테스트하십시오. |
| **프로덕션** | 라이브 롤아웃 여기에 구성된 기능 플래그는 실제 사용자 기반에 대해 평가됩니다. |

>[!IMPORTANT]
>
>스테이지에서 변경한 사항은 자동으로 프로덕션으로 이월되지 않습니다. 기능 플래그 및 대상 규칙은 각 환경에서 별도로 구성해야 합니다.

## 환경 선택 {#selecting}

Experience Rollouts 콘솔에 로그인한 후 인터페이스 상단의 환경 전환기에서 환경을 선택합니다. 기능 플래그를 만들거나 수정하기 전에 올바른 환경에서 작업하고 있는지 확인하십시오.

## 모범 사례 {#best-practices}

구성 오류를 방지하고 프로덕션 대상자를 보호하려면 다음 권장 사항을 따르십시오.

* 항상 먼저 **단계**&#x200B;에서 기능 플래그를 만들고 테스트하십시오.
* 프로덕션에서 복제하기 전에 스테이지에서 대상 규칙, 비율 롤아웃 및 타깃팅 논리의 유효성을 검사하십시오.
* [환경 간 워크플로](../cross-environment/cross-environment-concept.md)를 사용하여 환경 간 플래그 상태를 보고 관리합니다.

## 참조 - {#see-also}

* [콘솔에 로그인](log-in-to-the-console.md)
* [환경에 애플리케이션 연결](../cross-environment/associate-environments.md)
* [환경 간 기능 플래그 보기](../cross-environment/view-feature-flags-across-environments.md)
