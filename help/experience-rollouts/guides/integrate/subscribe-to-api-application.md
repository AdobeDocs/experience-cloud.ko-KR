---
title: Adobe Developer Console에서 API 애플리케이션 구독
description: 기능 플래그 엔드포인트를 호출할 수 있도록 Adobe Developer Console을 통해 애플리케이션을 Experience Rollouts API에 구독하는 방법을 알아봅니다.
source-git-commit: 120a2ea34682c878aaf6f6cb75504a8704d10e3d
workflow-type: tm+mt
source-wordcount: '278'
ht-degree: 3%

---


# Adobe Developer Console에서 API 애플리케이션 구독 {#subscribe-to-api}

애플리케이션에서 Experience Rollouts API를 호출하려면 [Adobe Developer Console](https://developer.adobe.com/console)을(를) 통해 구독해야 합니다. 그러면 Experience Rollouts에서 호출자를 식별하는 데 사용하는 클라이언트 ID가 애플리케이션에 제공됩니다.

## 전제 조건 {#prerequisites}

구독하기 전에 다음을 확인하십시오.

* 애플리케이션이 경험 롤아웃 콘솔에서 온보딩되었습니다. [애플리케이션 온보딩](../applications/onboard-your-application.md)을 참조하십시오.
* 조직의 Adobe Developer Console에 액세스할 수 있습니다.

## 경험 롤아웃 API 구독 {#subscribe}

애플리케이션을 Experience Rollouts API에 구독하려면 다음 단계를 따르십시오.

1. [Adobe Developer Console](https://developer.adobe.com/console)&#x200B;(으)로 이동하여 조직 자격 증명으로 로그인합니다.
2. 프로젝트를 선택하거나 새 프로젝트를 만듭니다.
3. **API 추가**&#x200B;를 선택합니다.
4. **경험 롤아웃 API**&#x200B;를 검색하여 선택하십시오.
5. 화면의 지침에 따라 API를 구성하고 자격 증명을 생성합니다.
6. 프로젝트에 대해 생성된 **클라이언트 ID**&#x200B;을(를) 확인합니다. 이 식별자는 Experience Rollouts API를 호출할 때와 Experience Rollouts 콘솔에서 애플리케이션을 온보딩할 때 사용하는 식별자입니다.

## 서버측 SDK 통합 {#server-sdk}

Java SDK 또는 Node.js SDK을 사용하여 통합하는 경우 API 키 외에 **서비스 토큰** 클라이언트 ID가 필요합니다. SDK은 서비스 토큰을 사용하여 백그라운드에서 경험 롤아웃 API를 호출할 수 있습니다.

>[!NOTE]
>
>서버측 SDK 클라이언트 ID는 API를 호출하기 전에 경험 롤아웃 지원에서 허용 목록에추가된으로 제공되어야 합니다. Developer Console 설정을 완료한 후 지원 센터에 문의하십시오.

## 참조 - {#see-also}

* [시작 안내서](startup-guide.md)
* [SDK](sdks.md)
* [애플리케이션 온보드](../applications/onboard-your-application.md)
* [통합 단계](integration-steps.md)
