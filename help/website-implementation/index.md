---
title: Adobe Experience Platform Launch를 사용하여 웹 사이트에서 Adobe Experience Cloud 구현
description: Launch를 사용하여 웹 사이트에서 Experience Cloud를 구현하는 것은 프런트 엔드 개발자 또는 웹 사이트에서 Adobe Experience Cloud 솔루션을 구현하는 방법을 배우고자 하는 기술 마케터에게 완벽한 시작점입니다.
seo-description: null
seo-title: Adobe Experience Platform Launch를 사용하여 웹 사이트에서 Adobe Experience Cloud 구현
solution: Experience Cloud
translation-type: tm+mt
source-git-commit: 7166d2933cc99bcbbd4713fba8f87fb0826b711e

---


# 개요

_Launch를 사용하여 웹 사이트에서_ Experience Cloud를 구현하는 것은 프런트 엔드 개발자 또는 웹 사이트에서 Adobe Experience Cloud 솔루션을 구현하는 방법을 배우고자 하는 기술 마케터에게 완벽한 시작점입니다.

각 단원에는 Experience Cloud를 구현하고 그 가치를 이해하는 데 도움이 되는 방법 연습과 기초 정보가 포함되어 있습니다.  콜아웃은 Adobe의 이전 태그 관리자(다이내믹 태그 관리)에서 마이그레이션하는 고객에게 유용할 수 있는 정보를 강조 표시하기 위해 제공됩니다. 데모 사이트는 자습서를 완료하기 위해 제공되므로 안전한 환경에서 기본 기술을 배울 수 있습니다. 이 튜토리얼을 완료한 후에는 자체 웹 사이트에서 Launch를 통해 모든 마케팅 솔루션을 구현할 수 있습니다.

이 작업을 완료하면 다음을 수행할 수 있습니다.

* 론치 속성 만들기

* 웹 사이트에 론치 속성 설치

* 다음 Adobe Experience Cloud 솔루션을 추가합니다.
   * **[Adobe Experience Platform ID 서비스](id-service.md)**
   * **[Adobe Target](target.md)**
   * **[Adobe Analytics](analytics.md)**
   * **[Adobe Audience Manager](audience-manager.md)**

* 규칙 및 데이터 요소를 만들어 Adobe 솔루션으로 데이터 전송

* Adobe Experience Cloud Debugger를 사용하여 구현 유효성 검사

* 개발, 스테이징 및 프로덕션 환경을 통해 Launch에 변경 사항 게시

>[!NOTE] 다음과 같은 플랫폼에도 유사한 다중 솔루션 자습서를 사용할 수 있습니다.
>
> * [모바일 iOS Swift™ 애플리케이션에서 Experience Cloud 구현](/help/mobile-ios-swift-implementation/index.md)
* [Mobile iOS Objective-C 애플리케이션에서 Experience Cloud 구현](/help/mobile-ios-objective-c-implementation/index.md)
* [모바일 Android 애플리케이션에서 Experience Cloud 구현](/help/mobile-android-implementation/index.md)


## 전제 조건

이 단원에서는 Adobe ID와 연습을 완료하는 데 필요한 권한이 있다고 가정합니다. 그렇지 않은 경우 액세스 권한을 요청하려면 Experience Cloud 관리자에게 문의해야 할 수 있습니다.

* Launch의 경우 확장 기능을 개발, 승인, 게시, 관리 및 관리할 수 있는 권한이 있어야 합니다. For more information on Launch permissions, see [the documentation](https://docs.adobe.com/content/help/en/launch/using/reference/admin/user-permissions.html).
* Adobe Analytics의 경우, 이 자습서를 완료하는 데 사용할 추적 서버 및 보고서 세트를 알고 있어야 합니다
* Audience Manager의 경우 Audience Manager 하위 도메인("파트너 이름" "파트너 ID" 또는 "파트너 하위 도메인"이라고도 함)을 알고 있어야 합니다.

또한 HTML 및 JavaScript와 같은 프런트 엔드 개발 언어를 잘 알고 있다고 가정합니다. 이러한 언어를 통달하지 않아도 단원을 완료할 수 있지만, 코드를 읽고 이해할 수 있으면 단원을 최대한 활용할 수 있습니다.

## Launch 정보

Adobe Experience Platform Launch는 Adobe의 차세대 웹 사이트 태그 및 모바일 SDK 관리 기능입니다. Launch를 사용하면 고객의 기대에 부응하는 경험을 제공하는 데 필요한 모든 분석, 마케팅 및 광고 솔루션을 간단하게 배포하고 관리할 수 있습니다. Launch에는 추가 비용이 없습니다. 모든 Adobe Experience Cloud 고객에게 제공됩니다.

웹 사이트용 Launch를 사용하면 데스크탑 및 모바일 사이트에서 사용되는 분석, 마케팅 및 광고 솔루션과 관련된 모든 JavaScript를 중앙에서 관리할 수 있습니다. 예를 들어 Adobe Analytics를 배포하는 경우 Launch는 AppMeasurement JavaScript 라이브러리를 관리하고, 변수를 채우고, 요청을 실행합니다.

론치 컨테이너 태그는 DTM보다 60% 가벼우며 Google 태그 관리자보다 40% 가볍습니다. 사용자 지정 코드를 포함하여 컨테이너의 콘텐츠가 축소됩니다. 모두 모듈식입니다. 항목이 필요하지 않으면 라이브러리에 포함되지 않습니다. 따라서 빠르고 컴팩트하게 구현됩니다.

또한 Launch는 타사 공급업체에서 Launch를 통해 솔루션을 쉽게 배포할 수 있는 익스텐션을 만들 수 있는 플랫폼입니다. 확장은 Launch UI 및 클라이언트 기능을 확장하는 코드 패키지(JavaScript, HTML 및 CSS)입니다. Launch는 운영 체제로 생각할 수 있으며 확장은 작업을 성취하기 위해 사용하는 응용 프로그램입니다.

## 단원 정보

이 단원에서는 Adobe Experience Cloud를 Luma라는 가짜 소매 웹 사이트로 구현하게 됩니다. Luma [사이트에는](https://luma.enablementadobe.com/content/luma/us/en.html) 사실적인 구현을 만들 수 있는 풍부한 데이터 레이어와 기능이 있습니다. 고유한 Experience Cloud 조직에 Launch 속성을 만들고 Experience Cloud Debugger를 사용하여 호스팅된 Luma 사이트에 매핑합니다.

[![루마 웹 사이트](images/overview-luma.png)](https://luma.enablementadobe.com/content/luma/us/en.html)

## 도구 가져오기

1. 브라우저 전용 확장을 사용할 예정이므로 [Chrome 웹 브라우저](https://www.google.com/chrome/)/를 사용하여 자습서를 완료해 주십시오
1. Add the [Adobe Experience Cloud Debugger](https://chrome.google.com/webstore/detail/adobe-experience-cloud-de/ocdmogmohccmeicdhlhhgepeaijenapj) extension to your Chrome browser
1. Download the [sample html page](https://www.enablementadobe.com/multi/web/basic-sample.html) (right-click on this link and click "Save Link As")
1. 샘플 html 페이지를 변경할 수 있는 텍스트 편집기를 사용할 수 있습니다. (없는 경우 Brackets를 사용하는 것이 [좋습니다](http://brackets.io/))
1. 루마 [사이트 책갈피 지정](https://luma.enablementadobe.com/content/luma/us/en.html)

>[!NOTE] Chrome에서 Luma 사이트를 열어 이 자습서를 보다 쉽게 완료할 수 있으며 이 자습서를 읽고 다른 브라우저에서 시작 인터페이스 단계를 완료할 수 있습니다.

그럼 시작해 보겠습니다!

[다음 "시작 속성 만들기" &gt;](launch.md)