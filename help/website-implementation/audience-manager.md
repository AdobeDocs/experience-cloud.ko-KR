---
title: Launch를 통해 Adobe Audience Manager 구현
description: 서버측 전달 및 시작을 사용하여 웹 사이트에서 Adobe Audience Manager를 구현하는 방법을 알아봅니다. 이 수업은 Launch를 사용하여 웹 사이트에서 Experience Cloud 구현 자습서의 일부입니다.
seo-description: null
seo-title: Launch를 통해 Adobe Audience Manager 구현
solution: Experience Cloud
translation-type: tm+mt
source-git-commit: e9dee6d0aa3b775d0ce617e2b2c57b56de491b8d

---


# Adobe Audience Manager 추가

이 단원에서는 서버측 전달을 사용하여 Adobe Audience Manager를 활성화하는 단계를 안내합니다.

[AAM](https://docs.adobe.com/content/help/en/audience-manager/user-guide/aam-home.html) (Adobe Audience Manager)은 온라인 고객 데이터 관리를 위한 업계 선도적인 서비스를 제공하므로 디지털 광고주와 출판업체는 데이터 자산을 제어하고 활용하여 성공적인 매출을 창출할 수 있습니다.

## 학습 목표

이 단원을 마치면 다음을 수행할 수 있습니다.

1. 웹 사이트에서 Audience Manager를 구현하는 두 가지 주요 방법 설명
1. Analytics 비콘의 서버측 전달을 사용하여 Audience Manager 추가
1. Audience Manager 구현 유효성 확인

## 전제 조건

이 단원을 수료하려면 다음을 수행해야 합니다.

1. 론치 구성, Adobe Analytics [를](launch.md)추가하고 [ID 서비스](analytics.md)추가의 [지침을](id-service.md)수료했습니다.

1. 이 자습서에 사용 중인 보고서 세트에 대해 서버측 전달을 활성화할 수 있도록 Adobe Analytics에 대한 관리 액세스 또는 아래 지침에 따라 조직의 기존 관리자에게 이를 수행하도록 요청할 수 있습니다.

1. "Audience Manager 하위 도메인"("파트너 이름" "파트너 ID" 또는 "파트너 하위 도메인"이라고도 함) Audience Manager가 이미 실제 웹 사이트에 구현되어 있는 경우 실제 웹 사이트로 이동하여 디버거를 여는 것이 가장 쉽습니다. 하위 도메인은 Audience Manager 섹션의 요약 탭에서 사용할 수 있습니다.

   ![디버거를 사용하여 실제 웹 사이트에서 Audience Manager 하위 도메인을 찾을 수 있습니다](images/aam-debugger-partner.png)

Audience Manager가 아직 구현되지 않은 경우 다음 지침에 따라 Audience Manager 하위 도메인을 [얻으십시오](https://docs.adobe.com/content/help/en/audience-manager-learn/tutorials/web-implementation/how-to-identify-your-partner-id-or-subdomain.html).

## 구현 옵션

다음 두 가지 방법으로 웹 사이트에서 Audience Manager를 구현할 수 있습니다.

* **SSF(Server-Side Forwarding)**- Adobe Analytics를 사용하는 고객의 경우 구현하기 쉽고 권장됩니다. Adobe Analytics는 Adobe의 백엔드에 있는 AAM으로 데이터를 전달하여 페이지에서 요청을 하나 더 줄일 수 있도록 합니다. 또한 주요 통합 기능을 사용할 수 있고 Audience Manager 코드 구현 및 배포에 대한 모범 사례를 준수할 수 있습니다.

* **클라이언트측 DIL**—이 방법은 Adobe Analytics가 없는 고객을 위한 것입니다. DIL 코드(데이터 통합 라이브러리 코드, AAM JavaScript 구성 코드)는 웹 페이지에서 Audience Manager로 직접 데이터를 전송합니다.

이 튜토리얼에서는 Adobe Analytics를 이미 배포했으므로 서버측 전달을 사용하여 Audience Manager를 배포하게 됩니다. For a complete description and requirements list for Server-Side forwarding, please review the [documentation](https://docs.adobe.com/content/help/en/analytics/admin/admin-tools/server-side-forwarding/ssf.html), so that you are familiar with how it works, what is required, and how to validate.

## 서버측 전달 활성화

SSF 구현을 수행하는 데는 두 가지 주요 단계가 있습니다.

1. Analytics 관리 콘솔에서 "전환"을 활성화하여 보고서 세트별로 Analytics *에서 Audience Manager로 데이터를 전달합니다*.
1. Launch를 통해 수행되는 제자리에 코드를 넣습니다. 이 기능이 제대로 작동하려면 Adobe Experience Platform ID Service 익스텐션과 Analytics 익스텐션이 설치되어 있어야 합니다(아래에 설명된 AAM 익스텐션이 실제로 *필요하지 않습니다* ).

### Analytics 관리 콘솔에서 서버측 전달 활성화

Adobe Analytics에서 Adobe Audience Manager로 데이터를 전달하려면 Adobe Analytics 관리 콘솔의 구성이 필요합니다. 데이터 전달을 시작하는 데 최대 4시간이 걸릴 수 있으므로 이 단계를 먼저 수행해야 합니다.

#### Analytics 관리 콘솔에서 SSF를 활성화하려면

1. Experience Cloud UI를 통해 Analytics에 로그인합니다. Analytics에 대한 관리자 액세스 권한이 없는 경우 Experience Cloud 또는 Analytics 관리자에게 문의하여 액세스 권한을 할당하거나 이러한 단계를 완료해야 합니다.

   ![Adobe Analytics에 로그인](images/aam-logIntoAnalytics.png)

1. Analytics의 상단 탐색에서 관리 **[!UICONTROL &gt; 보고서 세트를]**&#x200B;선택하고 목록에서 Audience Manager로 전달할 보고서 세트를 선택(다중 선택)합니다.

   ![관리 콘솔 클릭](images/aam-analyticsAdminConsoleReportSuites.png)

1. 보고서 세트 화면에서 보고서 세트를 선택하고 설정 편집 &gt; 일반 **[!UICONTROL &gt; 서버측 전달을 선택합니다]**.

   ![SSF 메뉴 선택](images/aam-selectSSFmenu.png)

   >[!WARNING] 위에 설명된 대로, 이 메뉴 항목을 보려면 관리자 권한이 있어야 합니다.

1. 서버측 전달 페이지에서 정보를 읽고 보고서 세트에 **[!UICONTROL 대해 서버측 전달을]** 활성화하라는 상자를 선택합니다.

1. **[!UICONTROL 저장]**&#x200B;을 클릭합니다

   ![전체 SSF 설정](images/aam-enableSSFcomplete.png)

>[!NOTE] SSF는 보고서 세트별로 활성화해야 하므로 실제 보고서 세트에 SSF를 배포할 때 이 단계를 반복하십시오.
>
>또한 SSF 옵션이 회색으로 표시되면 옵션을 활성화하려면 "보고서 세트를 Experience Cloud 조직에 매핑해야 합니다. 이 내용은 [설명서](https://docs.adobe.com/content/help/en/core-services/interface/about-core-services/report-suite-mapping.html)에 자세히 나와 있습니다.

이 단계가 완료되고 Adobe Experience Platform ID 서비스가 활성화되어 있으면 데이터가 Analytics에서 AAM으로 전달됩니다. 하지만 응답이 AAM에서 페이지(및 Audience Analytics 기능을 통해 Analytics)로 올바르게 돌아오도록 프로세스를 완료하려면 Launch에서도 다음 단계를 완료해야 합니다. 걱정 마, 아주 쉬워.

### Launch에서 서버측 전달 활성화

SSF 활성화를 위한 두 단계 중 두 번째 단계입니다. Analytics Admin Console에서 스위치를 이미 역전시킨 경우 이제 해당 코드를 추가해야 합니다. 오른쪽 상자를 선택하기만 하면 Launch가 자동으로 수행합니다.

>[!NOTE] Analytics 데이터의 서버측 전달을 AAM으로 구현하기 위해 AAM 확장이 **아닌** Launch에서 Analytics 확장을 실제로 편집/구성합니다. AAM 익스텐션은 Adobe Analytics가 없는 사용자에 대해 클라이언트측 DIL 구현에만 사용됩니다. 따라서 다음 단계는 Analytics 확장으로 전송하여 설정할 때 올바르게 됩니다.

#### 론치에서 SSF를 활성화하려면

1. 확장 **[!UICONTROL &gt; 설치됨으로]** 이동하고 클릭하여 Analytics 확장 기능을 구성합니다.

   ![Analytics 확장 구성](images/aam-configAnalyticsExtension.png)

1. 섹션 `Adobe Audience Manager` 확장

1. Analytics 데이터를 Audience **[!UICONTROL Manager와 자동으로 공유하려면 이 확인란을 선택합니다]**. 이렇게 하면 Audience Manager "모듈"(코드)이 Analytics `AppMeasurement.js` 구현에 추가됩니다.

1. "Audience Manager 하위 도메인"("파트너 이름", "파트너 ID" 또는 "파트너 하위 도메인"이라고도 함)을 추가합니다. 다음 지침에 따라 Audience Manager 하위 도메인을 [얻습니다](https://docs.adobe.com/content/help/en/audience-manager-learn/tutorials/web-implementation/how-to-identify-your-partner-id-or-subdomain.html).

1. 라이브러리에 **[!UICONTROL 저장 및 빌드를 클릭합니다.]**

   ![SSF 구성](images/aam-configLaunchSSF.png)

이제 서버측 전달 코드가 구현되었습니다!

### 서버측 전달 유효성 검사

서버측 전달이 실행 중인지 확인하는 주요 방법은 Adobe Analytics 히트에 대한 응답을 보는 것입니다. 우리는 곧 그것에 도달할 것입니다. 동시에, 그것이 우리가 원하는 방식으로 작동하는지 확인하는데 도움이 되는 몇 가지 다른 것들을 확인합시다.

#### 코드가 올바르게 로드되는지 확인

Adobe Launch가 전달을 처리하기 위해 설치하는 코드, 특히 AAM에서 페이지로의 응답을 Audience Manager"Module"이라고 합니다. Experience Cloud Debugger를 사용하여 Experience Cloud Debugger가 로드되었는지 확인할 수 있습니다.

1. 루마 사이트 열기
1. 브라우저에서 디버거 아이콘을 클릭하여 Experience Cloud 디버거를 엽니다
1. 요약 탭에서 아래로 스크롤하여 분석 섹션으로 이동합니다.
1. Verify that **AudienceManagement** is listed under the Modules section

   ![디버거에서 AAM 모듈 유효성 검사](images/aam-verifyAAMmodule.png)

#### 디버거에서 파트너 ID 확인

다음으로, 디버거가 올바른 "파트너 ID"(AKA 파트너 하위 도메인 등)를 선택하는지 확인할 수 있습니다. 를 사용하십시오.

1. 디버거에 있는 동안 계속 요약 탭에서 Audience Manager 섹션으로 스크롤합니다.
1. "파트너"에서 파트너 ID/하위 도메인 확인

   ![디버거에서 파트너 ID 유효성 검사](images/aam-verifyPartnerID.png)

>[!WARNING] 디버거의 Audience Manager 섹션이 "데이터 통합 라이브러리"인 "DIL"을 참조하며, 일반적으로 여기에서 구현한 서버측 접근 방식이 아니라 클라이언트측 구현을 참조합니다. 사실은 AAM "모듈"(이 SSF 접근 방식에서 사용)이 클라이언트측 DIL 라이브러리와 동일한 코드를 많이 사용하므로 이 디버거가 현재 이와 같이 보고하고 있습니다. 이 자습서의 단계를 수행했으며 이 검증 섹션의 나머지 항목이 올바르면 서버측 전달이 제대로 작동하는지 확인할 수 있습니다.

#### Analytics 요청 및 응답 확인

네, 이게 가장 큰 겁니다. Analytics에서 Audience Manager로 데이터를 서버측에서 전달하지 않는 경우 Analytics 비콘(2x2 픽셀 제외)에 대한 응답이 없습니다. 그러나 SSF를 수행하는 경우 Analytics 요청과 응답에서 확인할 수 있는 항목이 있으며, 이 항목이 제대로 작동하는지 알 수 있습니다.
안타깝게도 현재 Experience Cloud 디버거는 비콘에 대한 응답 표시를 지원하지 않습니다. 따라서 Charles Proxy 또는 브라우저의 개발자 도구와 같은 다른 디버거/패킷 스니퍼를 사용해야 합니다.

1. 브라우저에서 개발자 도구를 열고 네트워크 탭으로 이동합니다.
1. 필터 필드에 Adobe Analytics 요청에 대해 표시되는 내용을 제한할 `b/ss` 항목을 입력합니다
1. Analytics 요청을 보려면 페이지를 새로 고칩니다.

   ![개발자 도구 열기](images/aam-openTheJSConsole.png)

1. Analytics 비콘(요청)에서 "콜백" 매개 변수를 찾습니다. 다음과 같이 설정됩니다. `s_c_il[1].doPostbacks`

   ![AA 요청 - 콜백 매개 변수](images/aam-callbackParam.png)

1. Analytics 비콘에 대한 응답이 있습니다. 요청에서 호출된 대로 doPostbacks에 대한 참조가 포함되며, 가장 중요한 것은 "stuff" 개체가 있어야 합니다. 여기에서 AAM 세그먼트 ID가 브라우저로 다시 전송됩니다. "물건" 개체가 있다면 SSF가 작동합니다!

   ![AA 응답 - 개체](images/aam-stuffObjectInResponse.png)

>[!WARNING] 거짓 "성공" - 응답이 있고 모든 것이 작동하는 것처럼 보이면 "물건" 개체가 있는지 **확인합니다** . 그렇지 않은 경우 응답에 "status":"SUCCESS"라는 메시지가 표시될 수 있습니다. 이것이 이상하게 들리겠지만, 이것은 실제로 그것이 제대로 **작동하지 않는다는** 증거이다. 이 메시지가 표시되면 이 두 번째 단계(론치의 코드)를 완료했지만 Analytics 관리 콘솔의 전달이 아직 완료되지 않았음을 의미합니다(이 섹션의 첫 단계). 이 경우 Analytics 관리 콘솔에서 SSF를 활성화했는지 확인해야 합니다. 만약 당신이 가지고 있다면, 그리고 아직 4시간이 되지 않았다면, 인내심을 가지세요.

![AA 응답 - 잘못된 성공](images/aam-responseFalseSuccess.png)

[다음 "Experience Cloud 통합" &gt;](integrations.md)