---
title: Launch를 통해 Adobe Audience Manager 구현
description: 서버측 전달 및 시작을 사용하여 웹 사이트에서 Adobe Audience Manager를 구현하는 방법을 알아봅니다. 이 단원은 모바일 iOS Swift 애플리케이션에서 Experience Cloud 구현 자습서의 일부입니다.
seo-description: null
seo-title: Launch를 통해 Adobe Audience Manager 구현
solution: Experience Cloud
translation-type: tm+mt
source-git-commit: e9dee6d0aa3b775d0ce617e2b2c57b56de491b8d

---


# Adobe Audience Manager 추가

이 단원에서는 Adobe Audience Manager를 서버측 전달을 사용하여 Experience Platform Mobile SDK에 구현하는 단계를 안내합니다.

[AAM](https://docs.adobe.com/content/help/en/audience-manager/user-guide/aam-home.html) (Adobe Audience Manager)은 온라인 고객 데이터 관리를 위한 업계 선도적인 서비스를 제공하므로 디지털 광고주와 출판업체는 데이터 자산을 제어하고 활용하여 성공적인 매출을 창출할 수 있습니다.

## 학습 목표

이 단원을 마치면 다음을 수행할 수 있습니다.

1. 모바일 앱에서 Audience Manager를 구현하는 두 가지 주요 방법 설명
1. Analytics 비콘의 서버측 전달을 사용하여 Audience Manager 추가
1. Audience Manager 구현 유효성 확인

## 전제 조건

이 단원을 수료하려면 다음을 수행해야 합니다.

1. 론치 구성 섹션의 강의를 완료하려면 론치 속성 [만들기](launch-create-a-property.md), [라이브러리](launch-add-extensions.md)[](launch-create-a-library.md)만들기 [및 Mobile SDK](launch-install-the-mobile-sdk.md)를설치합니다.

1. 이 자습서에 사용 중인 보고서 세트에 대해 서버측 전달을 활성화할 수 있도록 Adobe Analytics에 대한 관리 액세스 또는 아래 지침에 따라 조직의 기존 관리자에게 이를 수행하도록 요청할 수 있습니다.

Audience Manager가 아직 구현되지 않은 경우 다음 지침에 따라 Audience Manager 하위 도메인을 [얻으십시오](https://docs.adobe.com/content/help/en/audience-manager-learn/tutorials/web-implementation/how-to-identify-your-partner-id-or-subdomain.html).

## 구현 옵션

앱에서 Audience Manager를 구현하는 방법에는 두 가지가 있습니다.

* SSF(Server-Side Forwarding) - Adobe Analytics를 사용하는 고객을 위해 가장 쉽고 권장되는 구현 방법입니다. Adobe Analytics는 Adobe의 백엔드에 있는 AAM으로 데이터를 전달하므로 앱에서 Audience Manager로 직접 요청을 하지 않아도 됩니다. 또한 주요 통합 기능을 사용할 수 있고 Audience Manager 코드 구현 및 배포에 대한 모범 사례를 준수할 수 있습니다.

* 클라이언트측 DIL—이 방법은 Adobe Analytics가 없는 고객을 위한 것입니다. 앱의 Audience Manager 메서드는 데이터를 Audience Manager로 직접 전송합니다. 이 경우 모바일 시작 속성을 설정할 때 Launch의 Audience Manager 확장을 사용합니다.

이전에 이 자습서의 익스텐션 추가 [섹션에서](launch-add-extensions.md) Analytics 익스텐션을 설정하면 Analytics에서 Audience Manager로 서버 측 데이터 전달을 시작하는 상자를 선택하였습니다. 이렇게 하면 Audience Manager 세그먼트의 응답을 처리하는 데 필요한 코드가 앱에 동적으로 삽입됩니다. 이 튜토리얼에서는 Audience Manager 익스텐션을 추가하지 않습니다. 이는 Adobe Analytics가 없는 경우에만 사용할 수 있습니다.

## 서버측 전달 활성화

SSF 구현을 수행하는 데는 두 가지 주요 단계가 있습니다.

1. Analytics 관리 콘솔에서 "전환"을 활성화하여 보고서 세트별로 Analytics *에서 Audience Manager로 데이터를 전달합니다*.
1. Launch를 통해 **수행한** SDK 코드를 AAM에 데이터를 전달하는 Analytics 확장 프로그램의 상자를 선택하기만 하면 됩니다.

### Analytics 관리 콘솔에서 서버측 전달 활성화

Adobe Analytics에서 Adobe Audience Manager로 데이터를 전달하려면 Adobe Analytics 관리 콘솔의 구성이 필요합니다. 시스템에서 데이터 전달을 시작하는 데 최대 4시간이 걸릴 수 있으므로 전달을 해결하는 동안 주의하십시오.

#### Analytics 관리 콘솔에서 SSF를 활성화하려면

1. Experience Cloud UI를 통해 Analytics에 로그인합니다. Analytics에 대한 관리자 액세스 권한이 없는 경우 Experience Cloud 또는 Analytics 관리자에게 문의하여 액세스 권한을 할당하거나 이러한 단계를 완료해야 합니다.

   ![Adobe Analytics UI에 로그인](images/mobile-aam-logIntoAnalytics.png)

1. Analytics의 상단 탐색에서 관리 **[!UICONTROL &gt; 보고서 세트를]**&#x200B;선택하고 목록에서 Audience Manager로 전달할 보고서 세트를 선택(또는 다중 선택)합니다.

   ![관리 콘솔 클릭](images/mobile-aam-analyticsAdminConsoleReportSuites.png)

1. 보고서 세트 화면에서 보고서 세트를 선택하고 설정 편집 &gt; 일반 **[!UICONTROL &gt; 서버측 전달을 선택합니다]**.

   ![SSF 메뉴 선택](images/mobile-aam-selectSSFmenu.png)

   >[!WARNING] 위에 설명된 대로, 이 메뉴 항목을 보려면 관리자 권한이 있어야 합니다.

1. 서버측 전달 페이지에서 정보를 읽고 보고서 세트에 **[!UICONTROL 대해 서버측 전달을]** 활성화하라는 상자를 선택합니다.

1. **[!UICONTROL 저장]**&#x200B;을 클릭합니다

   ![전체 SSF 설정](images/mobile-aam-enableSSFcomplete.png)

>[!NOTE] SSF는 보고서 세트별로 활성화해야 하므로 실제 보고서 세트에 SSF를 배포할 때 이 단계를 반복하십시오.
>
>또한 SSF 옵션이 회색으로 표시되면 옵션을 활성화하려면 "보고서 세트를 Experience Cloud 조직에 매핑해야 합니다. 이 내용은 [설명서](https://docs.adobe.com/content/help/en/core-services/interface/about-core-services/report-suite-mapping.html)에 자세히 나와 있습니다.

Adobe Experience Platform ID Service가 구현된 경우 이 스위치를 사용하여 AAM에 데이터의 실제 전달을 시작합니다. 나머지 SSF 구현은 AAM으로 전달하기 위해 Analytics 확장의 상자를 선택하면 Launch에서 처리되던 코드에서 발생합니다.

이제 앱에 대해 서버측 전달 코드가 구현되었습니다!

### 서버측 전달 유효성 검사

서버측 전달이 작동 중이고 실행되는지 확인하는 주요 방법은 앱에서 나오는 Adobe Analytics 히트에 대한 응답을 보는 것입니다.

Analytics에서 Audience Manager로 데이터의 서버측 전달(SSF)을 수행하지 않는 경우 Analytics 비콘(2x2 픽셀 제외)에 대한 응답이 없습니다. 그러나 SSF를 활성화하면 Analytics 요청과 응답에서 확인할 수 있는 항목이 있으며, 이 항목이 제대로 작동하는지 알 수 있습니다.

Xcode 콘솔은 비콘에 대한 응답을 표시하지 않으므로 Charles Proxy와 같이 응답을 표시하는 다른 디버거/패킷 스니퍼를 사용해야 합니다(예: 아래 스크린샷에 표시).

1. 디버거를 열고 Adobe Analytics 요청에 대한 `b/ss`내용을 제한하는
1. 이전 연습에서 샘플 앱 빌드 및 실행
1. Analytics 요청에 대해 응답을 확인하십시오. 매개 변수 `dcs_region` 및 `uuid` 매개 변수를 포함해야 하며 "stuff" 개체도 있어야 합니다. 이 개체는 AAM 세그먼트 ID가 브라우저로 다시 전송되는 위치입니다(사용자가 속한 모든 세그먼트의 경우, AAM에서 쿠키 대상에 할당됨). "물건" 개체가 있다면 SSF가 작동합니다!

   ![AA 응답 - 개체](images/mobile-aam-AAresponseCharles.png)

>[!WARNING] 거짓 "성공" - 응답이 있고 모든 것이 작동하는 것처럼 보이면 "물건" 개체가 있는지 **확인합니다** . 그렇지 않은 경우 응답에 "status":"SUCCESS"라는 메시지가 표시될 수 있습니다. 이것이 이상하게 들리겠지만, 이것은 실제로 그것이 제대로 **작동하지 않는다는** 증거이다. 이 메시지가 표시되면 AAM으로 전달할 론치의 단계를 완료했지만 Analytics 관리 콘솔의 전달이 아직 완료되지 않았음을 의미합니다. 이 경우 Analytics 관리 콘솔에서 SSF를 활성화했는지 확인해야 합니다. 만약 당신이 가지고 있다면, 그리고 아직 4시간이 되지 않았다면, 인내심을 가지세요.

![AA 응답 - 잘못된 성공](images/mobile-aam-unsuccessful-SSF.png)

[다음 "속성 게시" &gt;](publish.md)