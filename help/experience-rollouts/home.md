---
title: Adobe Experience 롤아웃
description: Adobe Experience 롤아웃을 사용하여 제어된 롤아웃, 기능 플래그 및 타겟팅된 대상 관리를 통해 안전하고 점진적으로 기능을 전달하는 방법을 알아봅니다.
exl-id: c400d75d-d928-4cf6-a094-1a2f443389f0
source-git-commit: 4a3133f014a9bb9d6ed26eb9d9f763db79ce63b3
workflow-type: tm+mt
source-wordcount: '343'
ht-degree: 1%

---

# Adobe Experience 롤아웃 {#experience-rollouts-home}

Adobe Experience Rollouts를 통해 제품 팀은 재배포나 중단 없이 새로운 기능을 점진적이고 안전하게 배송할 수 있습니다. 누가 무엇을, 언제, 어떤 속도로 보는지 정의합니다. 문제가 발생하면 즉시 기능을 끕니다. 잘 진행되면 일정에 따라 대상을 확장합니다.

## 수행 가능한 작업

**새로운 기능을 볼 사용자를 제어합니다.** 특정 사용자, 조직, 지역 또는 사용자 지정 속성에 대한 Target 릴리스입니다. 작은 그룹으로 시작하여 경험을 검증한 다음 콘솔에서 코드 변경 없이 모두 확장합니다.

**A/B 실험 실행** 대상의 서로 다른 세그먼트에 다양한 변형을 제공하고 더 나은 성과를 측정합니다. 전체 릴리스 전에 결과를 사용하여 정보에 입각한 제품 결정을 내릴 수 있습니다.

**릴리스 위험을 줄입니다.** 대규모 변경 사항을 보다 작고 제어된 롤아웃으로 나눕니다. 버그 또는 성능 문제가 나타나면 영향을 받는 기능만 비활성화합니다. 나머지 응용 프로그램은 안정적인 상태를 유지합니다.

**여러 팀을 조정합니다.** 팀 간 기능 그룹을 사용하면 여러 팀이 하나의 조정된 릴리스에 참여할 수 있으며, 각 팀은 공통의 롤아웃 일정 및 대상을 공유하면서 각자의 기능 플래그를 관리합니다.

## 첫 번째 기능 온보드

경험 롤아웃에서 가치를 얻는 단계는 다음 세 단계로 시작됩니다.

1. **팀과 응용 프로그램을 설정합니다** — 콘솔에 대한 [액세스 요청](guides/console/request-access.md)을 수행한 다음 [응용 프로그램을 온보딩합니다](guides/applications/onboard-your-application.md). 따라서 Experience Rollouts에서 제공할 클라이언트를 알 수 있습니다.

2. **기능 플래그 만들기 및 게시** — [첫 번째 기능 플래그 만들기](guides/feature-flags/create-your-first-feature-flag.md) 안내서에 따라 플래그를 정의하고 초기 대상을 설정하고 환경에 게시합니다.

3. **응용 프로그램과 통합** - 런타임 시 기능 플래그를 검색하고 적용할 수 있도록 앱을 Experience Rollouts API 또는 SDK에 연결합니다. 응용 프로그램 유형에 대한 [통합 단계](guides/integrate/integration-steps.md)(으)로 시작합니다.

첫 번째 플래그가 라이브되면 대상을 세분화하고, 점진적 롤아웃을 구성하고, 저장에서 전체 롤아웃으로 승격할 수 있습니다.

## 도움이 필요하십니까?

문제가 예상대로 작동하지 않으면 [문제 해결 안내서](guides/support/troubleshooting.md)에서 가장 일반적인 문제를 다룹니다. 기타 정보는 [지원팀에 문의](guides/support/contact-support.md)하세요.
