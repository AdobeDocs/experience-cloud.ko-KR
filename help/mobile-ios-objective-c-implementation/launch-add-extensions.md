---
title: Mobile Launch 속성에 확장 추가
description: 모바일 Launch 속성에 확장을 추가하는 방법을 알아봅니다. 이 단원은 모바일 iOS에서 Experience Cloud 구현 목표-C 애플리케이션 자습서의 일부입니다.
seo-description: null
seo-title: Mobile Launch 속성에 확장 추가
solution: Experience Cloud
translation-type: tm+mt
source-git-commit: 7166d2933cc99bcbbd4713fba8f87fb0826b711e

---


# 확장 추가

이 단원에서는 Launch 속성에 확장을 추가합니다.

Launch는 Adobe 및 타사 공급업체에서 Launch를 통해 솔루션을 쉽게 배포할 수 있는 익스텐션을 만들 수 있는 플랫폼입니다. 익스텐션은 Launch 인터페이스와 클라이언트 기능을 확장하는 코드 패키지입니다. 익스텐션을 사용하면 특정 앱에 필요한 Adobe Experience Platform Mobile SDK의 부분만 선택할 수 있습니다.  Launch는 운영 체제로 생각할 수 있으며 확장은 작업을 성취하기 위해 사용하는 응용 프로그램입니다.

Adobe 솔루션(예: Target, Analytics 및 Audience Manager)을 구현하게 되므로 이를 지원하는 데 필요한 익스텐션을 추가합니다.

>[!WARNING] Mobile Launch 속성에서 Extensions를 추가 및 제거하려면 앱을 업데이트해야 합니다. 웹 사이트를 업데이트하지 않고도 언제든지 익스텐션을 추가하거나 제거할 수 있는 웹 론치 속성과 다릅니다.

## 전제 조건

이 단원을 수료하려면 Launch 사용자 계정에 "확장 기능 관리"에 대한 권한이 있어야 합니다. 사용자 인터페이스 옵션을 사용할 수 없으므로 이러한 단계를 완료할 수 없는 경우 Experience Cloud 관리자에게 문의하여 액세스 권한을 요청하십시오. For more information on Launch permissions, see [the documentation](https://docs.adobe.com/content/help/en/launch/using/reference/admin/user-permissions.html).

다음 솔루션 세부 정보가 필요합니다.

* 하나 이상의 Analytics 보고서 세트 ID를 참조하십시오. 보고서 세트에 앱 보고서가 [활성화되어](https://docs.adobe.com/content/help/en/analytics/admin/admin-tools/mobile-management.html)있어야 합니다. If you don't have a test/dev report suite that you can use for this tutorial, please [create one](https://docs.adobe.com/content/help/en/analytics/admin/manage-report-suites/new-report-suite/new-report-suite.html). 이 자습서에는 하나의 보고서 세트만으로도 충분하지만 실제 환경에서는 개발, 스테이징 및 프로덕션 환경에 다른 보고서 세트를 사용하려고 합니다.

* Analytics 추적 서버. 현재 구현, Adobe 컨설턴트 또는 고객 지원 센터 담당자로부터 추적 서버를 검색할 수 있습니다.

## 학습 목표

이 단원을 마치면 다음을 수행할 수 있습니다.

* 모바일 시작 속성에 확장 추가
*  Analytics 확장 구성
* Target 및 Target VEC 확장 구성

>[!NOTE] Adobe Audience Manager는 Analytics 확장 프로그램의 구성을 통해 구현할 수 있으므로 이 자습서에서 Audience Manager 확장 기능을 추가할 필요가 없습니다

## 사전 설치된 확장 프로그램 검토

1. 확장 **[!UICONTROL 탭을]** 클릭하여 확장 페이지로 이동합니다.
1. Mobile Core 및 `Profile` 익스텐션은 새 모바일 속성에 미리 설치되어 있습니다
1. Core **[!UICONTROL Extension에서]** 구성 버튼을 클릭하여 설정을 검사합니다.

   ![확장 탭으로 이동](images/mobile-extensions-installed-default.png)

1. Mobile Core 익스텐션은 모든 앱 구현에 필요한 핵심 Adobe Experience Platform Mobile SDK를 나타냅니다. 코어는 모든 Adobe 및 타사 익스텐션에서 필요한 Experience Cloud ID 서비스, 데이터 이벤트 허브, 규칙 엔진, 재사용 가능한 네트워킹, 디스크 액세스 루틴 등과 같은 일반적인 기능 및 프레임워크 세트를 포함합니다.  Mobile Core 익스텐션에 대한 자세한 내용은 [설명서를](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/mobile-core)참조하십시오.

   1. Adobe Experience Cloud 조직 ID는 자동으로 검색되고 미리 채워집니다.
   1. Experience Cloud Server 필드를 사용하면 방문자 ID 서비스 요청에 대한 사용자 지정 끝점을 지정할 수 있습니다. 이 튜토리얼에서는 기본 설정(비워 둡니다)을 사용합니다.
   1. 세션 시간 초과 필드를 사용하면 앱 라이프사이클 세션이 시간 초과되어야 하는 시기를 지정할 수 있습니다. 기본적으로 앱이 300초 동안 백그라운드에 있으면 시간 초과됩니다. 이 튜토리얼의 기본 설정을 사용합니다.

1. 설정을 변경하지 않았기 때문에 [취소] **[!UICONTROL 를]** 클릭하여 확장 구성을 그대로 둡니다

   ![구성을 종료하려면 취소를 클릭합니다.](images/mobile-extensions-core-cancel.png)

1. 프로필 확장을 사용하면 SDK가 클라이언트측 프로필에 데이터를 저장할 수 있습니다. 구성이 없으므로 볼 것이 없습니다. 프로필 확장에 대한 자세한 내용은 설명서를 [참조하십시오](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/profile).

## 솔루션 확장 추가

이제 이 튜토리얼에서 구현할 솔루션의 익스텐션을 추가해 보십시오. 모바일 응용 프로그램에서 Launch를 사용할 때는 확장이 추가 또는 제거될 때마다 앱을 업데이트해야 합니다. 나중에 시간을 절약하기 위해 이 단원의 모든 익스텐션을 추가합니다. 라이선스가 부여되지 않은 솔루션을 건너뛸 수 있습니다.

### Adobe Analytics 확장 추가

>[!NOTE] Adobe Analytics에 대한 라이선스가 없는 경우 이 섹션을 건너뛸 수 있습니다. 현재 모바일 속성에 대한 Analytics 익스텐션은 SDK 설정을 관리하는 용도로만 사용되며 규칙 작업과 같은 인터페이스 옵션을 Launch에 추가하지 않습니다.

**확장자를 추가하려면**

1. 카탈로그 탭을 클릭하여 _제거된_ 익스텐션을 확인합니다.

1. Adobe Analytics **[!UICONTROL 확장]** 프로그램을 찾아 설치를 **[!UICONTROL 클릭합니다]**

   ![Extensions 카탈로그로 이동하고 \[설치\]를 클릭하여 Analytics 확장 기능을 추가합니다](images/mobile-extensions-catalog-installAnalytics.png)

1. 미리 채워진 **[!UICONTROL 목록에서]** 보고서 세트를 선택합니다. 앱이 데이터를 전송할 보고서 세트입니다. 개발, 스테이징 및 프로덕션 환경에 대해 다른 보고서 세트를 선택할 수 있습니다.
1. Analytics **[!UICONTROL 추적]** 서버를 미리 채우거나 미리 채워진 목록에서 선택하거나 수동으로 입력해야 할 수 있습니다. 이것은 비콘이 전송될 도메인입니다(일반적으로 형식) `yoursite.sc.omtrdc.net`.
1. 오프라인 활성화 상자를 **[!UICONTROL 선택합니다]**. [오프라인 사용] 확인란을 선택하면 Analytics 히트가 장치가 오프라인 상태일 때 큐에 올라가 장치가 다시 온라인 상태가 되면 나중에 전송됩니다. 오프라인 추적을 사용하려면 보고서 세트의 타임스탬프가 활성화되어 **있는지** 확인합니다. 자세한 내용은 [ 문서](https://docs.adobe.com/content/help/en/analytics/implementation/javascript-implementation/offline-tracking.html)를 참조하세요.
1. Audience Manager 전달 **[!UICONTROL 상자를 선택합니다]**. 이렇게 하면 Analytics 데이터가 Audience Manager로 전달되므로 앱에서 Audience Manager로 추가 호출을 하지 않아도 됩니다. 이 연습에서는 Audience Manager가 있으므로 Analytics에서 데이터를 전달한다고 가정합니다. Audience Manager가 없는 경우 자체 구현을 위해 Analytics를 설정할 때 이 확인란을 선택하지 마십시오.
1. 이전 세션 정보를 **[!UICONTROL 소급 적용하는 확인란을 선택합니다.]**
1. 저장 **[!UICONTROL 단추를]** 클릭합니다

   ![Extensions 카탈로그로 이동하고 [설치]를 클릭하여 Analytics 확장 기능을 추가합니다](images/mobile-extensions-analytics-settings.png)

### Target 확장 추가

Adobe Target에는 두 개의 공식 익스텐션인 Adobe Target 익스텐션과 Adobe Target VEC 익스텐션이 있습니다. Adobe Target은 이전 모바일 SDK 사용자에게 익숙한 모든 API를 지원합니다. Adobe Target VEC 익스텐션은 마케터가 WYSIWYG(What-You-See-Is-What-You-Get) 인터페이스에서 페이지의 이미지 및 텍스트 요소를 변경하는 간단한 작업을 만들 수 있도록 해주는 Target의 Visual Experience Composer에 대한 지원을 추가합니다. 이 자습서에서는 두 가지 방법을 모두 사용합니다.

>[!NOTE] Adobe Target에 대한 라이센스가 없는 경우 이 섹션을 건너뛸 수 있습니다. 현재 모바일 속성에 대한 Target 익스텐션은 SDK 설정을 관리하는 용도로만 사용되며 규칙 작업과 같은 인터페이스 옵션을 Launch에 추가하지 않습니다.

**확장자를 추가하려면**

1. 카탈로그 탭을 클릭하여 _제거된_ 익스텐션을 확인합니다.

1. Adobe Target **[!UICONTROL 확장]** 프로그램을 찾아 설치를 **[!UICONTROL 클릭합니다]**

   ![Extensions 카탈로그로 이동하고 [설치]를 클릭하여 Target 확장을 추가합니다](images/mobile-extensions-catalog-installTarget.png)

1. 클라이언트 **[!UICONTROL 코드가]** 미리 채워집니다.
1. 환경 **[!UICONTROL ID를]** 비워 둡니다. 이 설정은 Adobe Target의 [호스트](https://docs.adobe.com/help/en/target/using/administer/hosts.html) 기능과 함께 사용되며, 이를 통해 데이터를 다른 보고 환경(예: 개발, 스테이징, 프로덕션)으로 전송할 수 있습니다. 기본적으로 데이터는 프로덕션 환경으로 전송됩니다.
1. 타겟 작업 **[!UICONTROL 공간 속성을]** 비워 둡니다. 이 설정은 Target Premium Enterprise 사용자 권한 [기능과 함께](https://docs.adobe.com/content/help/en/target/using/administer/manage-users/enterprise/property-channel.html) 사용됩니다.
1. 시간 초과를 **[!UICONTROL 5초로]** 설정합니다. 이 설정은 앱이 기본 컨텐츠를 표시하기 전에 Target 응답을 기다리는 시간을 제어합니다.
1. 저장 **[!UICONTROL 단추를]** 클릭합니다

   ![타겟 설정 구성](images/mobile-extensions-target-settings.png)

### Target VEC 확장 추가

이제 Target 확장이 추가되었으므로 Target VEC 확장을 추가할 수 있습니다.

>[!NOTE] Adobe Target에 대한 라이센스가 없는 경우 이 섹션을 건너뛸 수 있습니다. 현재 모바일 속성에 대한 Target VEC 익스텐션은 SDK 설정을 관리하는 용도로만 사용되며 규칙 작업과 같은 인터페이스 옵션을 Launch에 추가하지 않습니다.

**확장자를 추가하려면**

1. 카탈로그 탭을 클릭하여 _제거된_ 익스텐션을 확인합니다.

1. Adobe Target **[!UICONTROL VEC]** 익스텐션을 찾아 설치를 **[!UICONTROL 클릭합니다]**

   ![Extensions 카탈로그로 이동하고 [설치]를 클릭하여 Target 확장을 추가합니다](images/mobile-extensions-catalog-installTargetVEC.png)

1. 타겟 **[!UICONTROL 캠페인 자동 가져오기]**&#x200B;를 설정합니다`ON` . 이렇게 하면 앱이 처음 로드될 때 모든 Target 활동이 미리 반입되므로 수행해야 하는 요청 수가 줄어듭니다.
1. 백그라운드에서 **[!UICONTROL 가져오기]**&#x200B;작업을`OFF`수행합니다. 이 설정은 `Auto-Fetch Target Campaigns` 사용될 때만 나타납니다.  이 설정을 `OFF` 종료하면 앱의 홈 화면에서 VEC 활동을 실행할 수 있지만, 홈 화면이 표시되기 전에 Target 요청이 완료되었거나 시간 초과되었는지 확인하기 위해 앱 시작에 지연을 추가할 수 있습니다. 홈 화면에서 활동을 실행할 `OFF` 때 이 설정을 그대로 두고 그렇지 않을 `ON` 때 전환하는 것이 좋습니다.  이 설정은 앱을 업데이트하지 않고 론치 인터페이스에서 언제든지 변경할 수 있습니다.
1. 저장 **[!UICONTROL 단추를]** 클릭합니다

   ![Target VEC 설정 구성](images/mobile-extensions-targetVEC-settings.png)

그러면 됩니다! 속성에 익스텐션을 추가했으므로 라이브러리에 추가할 수 있습니다.

[다음 "라이브러리 만들기" &gt;](launch-create-a-library.md)
