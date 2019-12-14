---
title: Launch와 Experience Cloud 통합 구현
description: Adobe Experience Cloud 구현에서 대상, A4T 및 고객 속성 통합의 유효성을 검사하는 방법을 알아봅니다. 이 수업은 Launch를 사용하여 웹 사이트에서 Experience Cloud 구현 자습서의 일부입니다.
seo-description: null
seo-title: Launch와 Experience Cloud 통합 구현
solution: Experience Cloud
translation-type: tm+mt
source-git-commit: e9dee6d0aa3b775d0ce617e2b2c57b56de491b8d

---


# Experience Cloud 통합

이 단원에서는 방금 구현한 솔루션 간의 주요 통합을 살펴봅니다. 좋은 소식은 이전 학습 과정을 완료함으로써 통합의 코드 측면을 이미 구현했다는 것입니다. 이 단원에서 읽고 유효성을 검사하는 것 외에 추가로 작업을 수행할 필요는 없습니다.

## 학습 목표

이 단원을 마치면 다음을 수행할 수 있습니다.

1. 대상 공유, Analytics for Target(A4T) 및 고객 속성 통합에 대한 기본 사용 사례 설명
1. 이러한 통합의 기본 클라이언트측 구현 측면에 대한 유효성 검사

## 전제 조건

이 튜토리얼의 지침을 따르기 전에 이 튜토리얼의 모든 이전 강의를 완료해야 합니다.

>[!NOTE] 이러한 통합을 완벽하게 사용하는 데 필요하고 이 자습서의 범위를 벗어난 많은 사용자 권한 요구 사항, 계정 구성 및 프로비저닝 단계가 있습니다. 현재 Experience Cloud 구현에서 이러한 통합을 사용하고 있지 않은 경우 다음을 고려해야 합니다.
>
> * [코어 서비스 통합](https://docs.adobe.com/content/help/en/core-services/interface/about-core-services/core-services.html)의 전체 요구 사항 검토
> * [Analytics for Target 통합](https://docs.adobe.com/content/help/en/target/using/integrate/a4t/before-implement.html)을 위한 전체 요구 사항 검토
> * Have an Administrator of your Experience Cloud Organization [request provisioning of these integrations](https://www.adobe.com/go/audiences)


## 대상자

[대상은](https://docs.adobe.com/content/help/en/core-services/interface/audiences/audience-library.htm) People 코어 서비스의 일부이며 솔루션 간에 대상을 공유할 수 있습니다. 예를 들어 Audience Manager에서 대상을 만들고 이를 사용하여 Target을 통해 개인화된 컨텐츠를 제공할 수 있습니다.

이미 수행한 A4T를 구현하기 위한 주요 요구 사항은 다음과 같습니다.

1. Adobe Experience Platform ID 서비스 구현
1. Audience Manager 구현
1. Target 및 Analytics와 같은 대상을 받거나 만들려는 다른 솔루션 구현

### 대상 통합 유효성 확인

대상 통합을 확인하는 가장 좋은 방법은 실제로 대상을 만들고, 다른 솔루션에 공유한 다음, 다른 솔루션에서 완전히 사용하는 것입니다(예: AAM 세그먼트에 자격이 있는 방문자가 해당 세그먼트를 타깃팅된 Target 활동을 자격이 있는지 확인). 그러나 이 작업은 이 자습서의 범위를 벗어납니다.

이러한 유효성 검사 단계는 클라이언트측 구현에서 볼 수 있는 중요한 부분인 방문자 ID에 중점을 둡니다.

1. Open the [Luma site](https://luma.enablementadobe.com/content/luma/us/en.html)

1. Make sure the Debugger is mapping the Launch property to *your* Development environment, as described in the [earlier lesson](launch-switch-environments.md)

   ![디버거에 표시된 실행 개발 환경](images/switchEnvironments-debuggerOnWeRetail.png)

1. 디버거의 네트워크 탭으로 이동

1. 모든 **[!UICONTROL 요청 지우기를]** 클릭하여 정리합니다.

1. 루마 페이지를 다시 로드하여 디버거에 Target 및 Analytics 요청이 모두 표시되는지 확인합니다.

1. 루마 페이지를 다시 불러오기

1. 이제 디버거의 네트워크 탭에 4개의 요청이 표시됩니다. Target에는 2개, Analytics에는 2개가 있습니다

1. "Experience Cloud 방문자 ID" 행을 확인합니다. 솔루션별로 모든 요청에 있는 ID는 항상 동일해야 합니다.

   ![일치하는 SDID 확인](images/integrations-matchingECIDs.png)

1. 이 ID는 방문자별로 고유하며, 동료에게 이러한 단계를 반복하도록 요청하여 확인할 수 있습니다.

## Analytics for Target (A4T)

The [Analytics for Target (A4T)](https://docs.adobe.com/content/help/en/target/using/integrate/a4t/a4t.html) integration allows you to leverage your Analytics data as the source for reporting metrics in Target.

이미 수행한 A4T를 구현하기 위한 주요 요구 사항은 다음과 같습니다.

1. Adobe Experience Platform ID 서비스 구현
1. Analytics 페이지 보기 비콘 전에 Target 페이지 로드 요청을 실행합니다.

A4T는 Target에서 Analytics로의 서버측 요청을 Analytics 페이지 보기 비콘과 함께 결합하는 방식으로 작동하며, 이 비콘은 "히트 스티칭"이라고 합니다.  히트 스티칭은 활동을 전달하는 타겟 요청에서 Analytics 페이지 보기 비콘의 매개 변수와 일치하는 매개 변수를 필요로 합니다. 이 매개 변수를 SDID(보충 데이터 ID)라고 합니다.

### A4T 구현의 유효성 검사

A4T 통합을 확인하는 가장 좋은 방법은 A4T를 사용하여 Target 활동을 실제로 만들고 보고 데이터를 확인하는 것입니다. 하지만 이 자습서의 범위는 아닙니다. 이 자습서에서는 보충 데이터 ID가 솔루션 호출 간에 일치하는지 확인하는 방법을 보여줍니다.

**SDID의 유효성을 확인하려면**

1. Open the [Luma site](https://luma.enablementadobe.com/content/luma/us/en.html)

1. Make sure the Debugger is mapping the Launch property to *your* Development environment, as described in the [earlier lesson](launch-switch-environments.md)

   ![디버거에 표시된 실행 개발 환경](images/switchEnvironments-debuggerOnWeRetail.png)

1. 디버거의 네트워크 탭으로 이동

1. 모든 **[!UICONTROL 요청 지우기를]** 클릭하여 정리합니다.

1. 루마 페이지를 다시 로드하여 디버거에 Target 및 Analytics 요청이 모두 표시되는지 확인합니다.

1. 루마 페이지를 다시 불러오기

1. 이제 디버거의 네트워크 탭에 4개의 요청이 표시됩니다. Target에는 2개, Analytics에는 2개가 있습니다

1. 보조 데이터 ID 행을 찾습니다. 첫 번째 페이지 로드의 ID는 Target과 Analytics 간에 일치해야 합니다. 두 번째 페이지 로드 시에도 이 ID가 일치해야 하지만, 첫 번째 페이지 로드 시와 다릅니다.

   ![일치하는 SDID 확인](images/integrations-matchingSDIDs.png)

A4T 활동의 일부인 페이지 로드 범위(단일 페이지 앱 제외)에서 추가 Target 요청을 하는 경우, 고유한 이름(target-global-mbox가 아님)을 지정하여 초기 Target 및 Analytics 요청의 SDID를 계속 유지할 수 있도록 하는 것이 좋습니다.

## 고객 속성

[고객](https://docs.adobe.com/content/help/en/core-services/interface/customer-attributes/attributes.html) 속성은 고객 관계 관리(CRM) 데이터베이스에서 데이터를 업로드하고 Adobe Analytics 및 Adobe Target에서 활용할 수 있는 People Core Service의 일부입니다.

이미 수행한 고객 속성을 구현하기 위한 주요 요구 사항은 다음과 같습니다.

1. Adobe Experience Platform ID 서비스 구현
1. Set Customer Ids via the Id Service *before* Target and Analytics fire their requests (which you accomplished using the rule ordering feature in Launch)

### 고객 속성 구현 유효성 확인

고객 ID가 이전 교육 과정에서 Identity Service와 Target 모두에 전달되었는지 이미 확인했습니다. 또한 Analytics 히트에서 고객 ID의 유효성을 확인할 수 있습니다.
현재 고객 ID는 Experience Cloud Debugger에 표시되지 않는 몇 가지 매개 변수 중 하나이므로 브라우저의 JavaScript 콘솔을 사용하여 볼 수 있습니다.

1. 루마 사이트 열기
1. 브라우저의 개발자 도구를 엽니다
1. 네트워크 탭으로 이동
1. 필터 필드에 Adobe Analytics 요청에 대해 표시되는 내용을 제한할 `b/ss` 항목을 입력합니다

   ![개발자 도구를 열고 네트워크 탭을 필터링하여 Analytics 요청만 표시합니다.](images/aam-openTheJSConsole.png)

1. 사이트의 **[!UICONTROL 오른쪽]** 상단 모서리에 있는 로그인 링크를 클릭합니다.

   ![상단 탐색에서 로그인을 클릭합니다.](images/idservice-loginNav.png)

1. 사용자 이름으로 `test@adobe.com` 입력
1. 암호로 `test` 입력
1. [로그인] **[!UICONTROL 단추]** 클릭

   ![자격 증명을 입력하고 로그인을 클릭합니다.](images/idservice-login.png)

1. 개발자 도구에서 볼 수 있는 비콘도 트리거하는 홈 페이지로 돌아가야 합니다. 계정 정보 페이지로 이동하는 경우 WE.RETAIL 로고를 클릭하여 홈 페이지로 돌아갑니다.
1. 요청을 클릭하고 머리글 탭을 선택합니다
1. 중첩된 매개 변수가 표시될 때까지 아래로 스크롤합니다.
   1. cid - 요청의 고객 ID 부분에 대한 표준 구분 기호입니다.
   1. crm_id - Identity Service 단원에서 지정한 사용자 지정 통합 코드입니다.
   1. id - `Email (Hashed)` 데이터 요소에서 가져오는 고객 ID 값
   1. as - 인증 상태, "1"이 있는 경우 로그인
   ![Analytics 고객 ID 유효성 검사](images/integrations-analyticsCustomerIDValidation.png)

[다음 "속성 게시" &gt;](publish.md)