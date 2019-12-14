---
title: Mobile iOS Objective-C 애플리케이션에서 Experience Cloud 구현
description: 모바일 iOS Objective-C Applications에서 Experience Cloud 구현은 모바일 iOS Objective-C 앱에서 Adobe Experience Cloud 솔루션을 구현하는 방법을 배우고자 하는 모바일 앱 개발자에게 완벽한 시작점입니다.
seo-description: null
seo-title: 'Mobile iOS Objective-C 애플리케이션에서 Experience Cloud 구현 '
solution: Experience Cloud
translation-type: tm+mt
source-git-commit: 7166d2933cc99bcbbd4713fba8f87fb0826b711e

---


# 개요

_모바일 iOS에서 Experience Cloud 구현 목표_ -CC 애플리케이션은 모바일 앱 개발자에게 iOS Objective-C 앱에서 Adobe Experience Cloud 솔루션을 구현하는 방법을 배우려는 최적의 시작점입니다.

각 단원에는 Experience Cloud를 구현하고 그 가치를 이해하는 데 도움이 되는 방법 연습과 기초 정보가 포함되어 있습니다.  데모 Objective-C 앱은 튜토리얼을 완료하기 위해 제공되므로 안전한 환경에서 기본 기법을 익힐 수 있습니다. 이 튜토리얼을 완료한 후에는 iOS Objective-C 앱에서 모든 Experience Cloud 솔루션을 구현할 수 있습니다.

이 튜토리얼을 완료하면 다음 작업을 수행할 수 있습니다.

* 모바일 시작 속성 만들기

* Objective-C 앱에 Launch 속성 설치

* 다음 Adobe Experience Cloud 솔루션을 구현합니다.
   * **[Adobe Experience Platform ID 서비스](id-service.md)**
   * **[Adobe Target](target-vec.md)**
   * **[Adobe Analytics](analytics.md)**
   * **[Adobe Audience Manager](audience-manager.md)**

* 개발, 스테이징 및 프로덕션 환경을 통해 Launch에 변경 사항 게시

>[!NOTE] 다음과 같은 플랫폼에도 유사한 다중 솔루션 자습서를 사용할 수 있습니다.
>
> * [모바일 iOS Swift™ 애플리케이션에서 Experience Cloud 구현](/help/mobile-ios-swift-implementation/index.md)
* [모바일 Android™ 애플리케이션에서 Experience Cloud 구현](/help/mobile-android-implementation/index.md)
* [Launch를 사용하여 웹 사이트에서 Experience Cloud 구현](/help/website-implementation/index.md)


## 전제 조건

이 단원에서는 Adobe ID와 연습을 완료하는 데 필요한 권한이 있다고 가정합니다. 그렇지 않은 경우 액세스 권한을 요청하려면 Experience Cloud 관리자에게 문의해야 할 수 있습니다.

* Launch의 경우 확장 기능을 개발, 승인, 게시, 관리 및 관리할 수 있는 권한이 있어야 합니다. For more information on Launch permissions, see [the documentation](https://docs.adobe.com/content/help/en/launch/using/reference/admin/user-permissions.html).
* Target의 경우 Adobe Target 인터페이스에 대한 승인자 수준 액세스 권한이 있어야 합니다
* Adobe Analytics의 경우, 이 자습서를 완료하는 데 사용할 추적 서버 및 보고서 세트를 알고 있어야 합니다

또한 목표-C의 iOS 개발에 익숙하다고 가정합니다. 학습 내용을 완성하기 위해 목표-C의 마스터가 될 필요는 없지만 코드를 쉽게 읽고 이해할 수 있다면 더 많은 기능을 활용할 수 있습니다.

## 단원 정보

이 수업에서는 Adobe Experience Cloud를 Experience Cloud 조직을 사용하여 "버스 예약"[이라는](https://github.com/Adobe-Marketing-Cloud/busbooking-mobileapps)데모 앱에 구현할 것입니다. 앱에는 기본 Experience Cloud 모바일 구현을 완료하기 전에 앱 내에서 완료할 수 있는 간단한 기능이 있습니다.

[![버스 예약 앱](images/mobile-busBookingApp.png)](https://github.com/Adobe-Marketing-Cloud/busbooking-mobileapps)

## 도구 가져오기

1. 이 자습서를 완료하려면 Mac®을 사용해야 합니다.
1. Xcode [다운로드](https://developer.apple.com/xcode/)
1. 버스 [예약 앱 다운로드](https://github.com/Adobe-Marketing-Cloud/busbooking-mobileapps)
1. 코드 [설치](https://guides.cocoapods.org/using/getting-started.html)

그럼 시작해 보겠습니다!

[다음 "시작 속성 만들기" &gt;](launch-create-a-property.md)