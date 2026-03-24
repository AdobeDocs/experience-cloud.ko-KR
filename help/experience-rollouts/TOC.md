---
audience: user
user-guide-title: Adobe Experience 롤아웃
user-guide-description: Adobe Experience 롤아웃을 사용하여 애플리케이션 전반에서 기능 플래그, 제어된 롤아웃 및 타겟팅된 릴리스를 관리하는 방법을 알아봅니다.
source-git-commit: cd1d882942705f51440ae99f4ce6daf467d3283c
workflow-type: tm+mt
source-wordcount: '315'
ht-degree: 6%

---


# Adobe Experience 롤아웃 {#experience-rollouts}

+ [개요](home.md)
+ 시작하기 {#get-started}
   + [경험 롤아웃 소개](getting-started/introduction.md)
   + [경험 롤아웃을 사용하는 이유](getting-started/why-use-experience-rollouts.md)
   + [경험 롤아웃 모드](getting-started/experience-rollouts-modes.md)
+ 개념 {#concepts}
   + [기능 플래그란 무엇입니까](concepts/what-is-a-feature-flag.md)
   + [기능을 활성화 및 비활성화하는 기능 플래그](concepts/feature-flags-to-enable-disable-features.md)
   + [여러 기능을 제어하는 기능 그룹](concepts/feature-groups-to-control-multiple-features.md)
   + [릴리스 관리 개념](concepts/concept-of-release-management.md)
   + [경험 롤아웃의 릴리스 관리](concepts/release-management.md)
   + [점진적 롤아웃](concepts/gradual-rollout.md)
+ 안내서 {#guides}
   + 콘솔 시작하기 {#console}
      + [경험 롤아웃 콘솔에 로그인합니다.](guides/console/log-in-to-the-console.md)
      + [환경 개요](guides/console/environments-overview.md)
      + [액세스 요청](guides/console/request-access.md)
      + [팀 및 해당 관리자](guides/console/teams-and-admins.md)
      + [새 팀 만들기](guides/console/create-a-new-team.md)
   + 팀 {#teams}
      + [팀 관리](guides/teams/manage-teams.md)
      + [사용자 역할](guides/teams/user-roles.md)
      + [팀에 구성원 추가](guides/teams/add-team-members.md)
      + [팀 관리 FAQ](guides/teams/team-management-faq.md)
   + 애플리케이션 {#applications}
      + [애플리케이션 관리](guides/applications/manage-applications.md)
      + [애플리케이션 온보드](guides/applications/onboard-your-application.md)
   + 경험 롤아웃 통합 {#integrate}
      + [앱의 경험 롤아웃 통합](guides/integrate/integrating-in-your-app.md)
      + [시작 안내서](guides/integrate/startup-guide.md)
      + [데스크탑 애플리케이션](guides/integrate/desktop-applications.md)
      + [모바일 애플리케이션](guides/integrate/mobile-applications.md)
      + [웹 애플리케이션](guides/integrate/web-applications.md)
      + [웹 서비스](guides/integrate/web-services.md)
      + [SDK](guides/integrate/sdks.md)
      + [통합 단계](guides/integrate/integration-steps.md)
      + [Adobe Developer Console에서 API 애플리케이션 구독](guides/integrate/subscribe-to-api-application.md)
   + 기능 플래그 및 릴리스 {#feature-flags-releases}
      + [기능, 기능 그룹 및 릴리스](guides/feature-flags/features-feature-groups-releases.md)
      + [첫 번째 기능 플래그 만들기](guides/feature-flags/create-your-first-feature-flag.md)
      + [점진적으로 롤아웃할 기능 설정](guides/feature-flags/set-feature-gradual-rollout.md)
      + [기능 그룹 만들기](guides/feature-flags/create-a-feature-group.md)
      + [기능 그룹을 설정하여 점진적으로 롤아웃](guides/feature-flags/set-feature-group-gradual-rollout.md)
      + [기능 플래그를 사용하여 A/B 테스트](guides/feature-flags/a-b-testing.md)
      + [릴리스 및 팀 간 기능 그룹](guides/feature-flags/releases-and-cross-team-feature-groups.md)
      + [전체 워크플로 릴리스](guides/feature-flags/release-workflow-end-to-end.md)
      + [릴리스 요청](guides/feature-flags/request-a-release.md)
      + [릴리스 대상 규칙 업데이트](guides/feature-flags/update-release-audience-rules.md)
      + [릴리스 상태](guides/feature-flags/release-states.md)
      + [팀 간 기능 그룹 만들기](guides/feature-flags/create-cross-team-feature-group.md)
      + [릴리스 관리 FAQ](guides/feature-flags/release-management-faqs.md)
      + [Analytics](guides/feature-flags/analytics.md)
      + [예약](guides/feature-flags/schedule.md)
   + 대상 기준 {#audience}
      + [기능 플래그 및 기능 그룹의 대상자](guides/audience/audience-in-feature-flags-and-feature-groups.md)
      + [대상 규칙에서 컨텍스트 사용](guides/audience/using-context-in-audience-rules.md)
      + [복잡한 대상 규칙](guides/audience/complex-rules.md)
      + [대상 규칙에서 Enterprise 조직 데이터 사용](guides/audience/using-enterprise-org-data.md)
      + [대상 기준에 백분율 규칙 추가](guides/audience/adding-percentage-rules.md)
      + [클라이언트 IP 컨텍스트 변수가 있는 대상 규칙](guides/audience/clientip-rule.md)
   + 환경 간 워크플로우 {#cross-environment}
      + [교차 환경 개념](guides/cross-environment/cross-environment-concept.md)
      + [환경에 애플리케이션 연결](guides/cross-environment/associate-environments.md)
      + [환경 간 기능 플래그 보기](guides/cross-environment/view-feature-flags-across-environments.md)
      + [기능 플래그 가져오기](guides/cross-environment/import-feature-flags.md)
   + 자동화된 롤아웃 {#automated-rollouts}
      + [자동화된 롤아웃 만들기](guides/automated-rollouts/create-automated-rollout.md)
      + [자동화된 롤아웃 개념](guides/automated-rollouts/automated-rollout-concept.md)
      + [롤아웃 계획 모니터링 및 편집](guides/automated-rollouts/monitor-edit-rollout-plan.md)
   + 지원 {#support}
      + [문제 해결](guides/support/troubleshooting.md)
      + [지원 받기](guides/support/get-support.md)
      + [지원 문의](guides/support/contact-support.md)
   + SDK 릴리스 {#sdk-releases}
      + Java SDK {#java-sdk}
         + [Java SDK 통합 안내서](guides/sdk-releases/java/java-sdk-integration-guide.md)
         + [Java SDK 릴리스 노트](guides/sdk-releases/java/java-sdk-release-notes.md)
      + Node.js SDK {#nodejs-sdk}
         + [Node.js SDK 통합 안내서](guides/sdk-releases/nodejs/nodejs-sdk-integration-guide.md)
         + [Node.js SDK 릴리스 노트](guides/sdk-releases/nodejs/nodejs-sdk-release-notes.md)
      + [SDK 벤치마킹](guides/sdk-releases/java-sdk-benchmarking.md)
<!--+ Feature API {#feature-api}
  + [GET Feature API V3](feature-api/get-feature-api-v3.md)
  + [GET Feature API V2](feature-api/get-feature-api-v2.md)
+ Management API {#management-api}
  + [Feature management APIs overview](management-api/feature-management-apis-overview.md)
  + [Feature flags management API](management-api/feature-flags-management-api.md)
  + [Feature group management API](management-api/feature-group-management-api.md)
  + [Release management APIs](management-api/release-management-apis.md)
  + [Get client ID for an application](management-api/get-client-id.md)
  + [Get desired audience criteria](management-api/get-audience-criteria.md)
  + [Management patch API](management-api/management-patch-api.md)-->
