---
title: Experience Cloud 트리거 만들기 및 관리
description: Adobe Experience Cloud 트리거 UI 살펴보기
hide: true
hidefromtoc: true
source-git-commit: ce0faf9fab45c931feb666ac0c77f5ab5c231746
workflow-type: tm+mt
source-wordcount: '483'
ht-degree: 25%

---

# Experience Cloud 트리거 만들기 {#create-triggers}

>[!NOTE]
>
> Experience Cloud 트리거를 위한 새로운 사용자 인터페이스는 소비자 행동을 관리하고 사용자 경험을 개인화할 수 있는 직관적인 경험을 제공합니다. 이전 인터페이스로 다시 전환하려면 **[!UICONTROL 클래식 모드로 이동]** 버튼을 클릭합니다.

트리거를 생성하고 트리거 조건을 구성합니다. 예를 들어, 장바구니 포기와 같은 지표 또는 제품 이름과 같은 차원과 같이, 방문 중의 트리거 규칙에 대한 기준을 지정할 수 있습니다. 규칙이 충족되면 트리거가 실행됩니다.

1. Experience Cloud에서 고급 메뉴, 트리거 순으로 선택합니다.

   ![](assets/triggers_7.png)

1. 트리거 홈 페이지에서 **[!UICONTROL 트리거 만들기]**&#x200B;그런 다음 트리거 유형을 지정합니다.

   다음 세 가지 유형의 트리거를 사용할 수 있습니다.

   * **[!UICONTROL 포기]**: 방문자가 제품을 보고 장바구니에 추가하지 않을 경우에 실행할 트리거를 만들 수 있습니다.

   * **[!UICONTROL 작업]**: 예를 들어 뉴스레터 등록, 이메일 가입 또는 신용 카드 신청(확인) 후에 동작할 트리거를 만들 수 있습니다. 유통업의 경우 회원 프로그램에 등록한 방문자를 대상으로 트리거를 만들 수 있습니다. 미디어 및 엔터테인먼트에서는 특정 프로그램을 시청하고 설문 조사에 응답하기를 원하는 방문자를 대상으로 트리거를 만들 수 있습니다.

   * **[!UICONTROL 세션 시작 및 세션 종료]**: 세션 시작 및 세션 종료 이벤트에 대한 트리거를 만듭니다.

   ![](assets/triggers_1.png)

1. 추가 **[!UICONTROL 이름]** 그리고 **[!UICONTROL 설명]** 트리거를 만듭니다.

1. Analytics를 선택합니다. **[!UICONTROL 보고서 세트]** 이 트리거에 사용됩니다. 이 설정은 사용할 보고 데이터를 식별합니다.

   [보고서 세트에 대해 자세히 알아보기](https://experienceleague.adobe.com/docs/analytics/admin/admin-tools/manage-report-suites/c-new-report-suite/t-create-a-report-suite.html).

1. 을(를) 선택합니다 **[!UICONTROL 작업 없음 후 트리거]** 유효 기간

1. 에서 **[!UICONTROL 포함 필수 방문]** 및 **[!UICONTROL 배제 필수 방문]** 카테고리에서는 발생을 원하거나 원하지 않는 기준이나 방문자 행동을 정의할 수 있습니다. 다음을 지정할 수 있습니다 **및** 또는 **또는** 결정하는 기준에 따라 조건 내 또는 조건 간에 논리를 지정합니다.

   예를 들어 다음과 같은 간단한 장바구니 포기 트리거를 위한 규칙을 만들 수 있습니다.

   * **[!UICONTROL 포함 필수 방문]**: `Carts (metric) Is greater or equal to 1` 장바구니에 하나 이상의 품목을 사용하여 방문자를 타깃팅합니다.
   * **[!UICONTROL 배제 필수 방문]**: `Checkout (metric) Exists.` 장바구니에서 품목을 구입한 방문자를 제거하기 위해.

   ![](assets/triggers_2.png)

1. 클릭 **[!UICONTROL 컨테이너]** 트리거를 정의하는 규칙, 조건 또는 필터를 설정하고 저장할 수 있습니다. 이벤트가 동시에 발생하도록 하려면 이벤트를 동일한 컨테이너에 배치해야 합니다.

   각 컨테이너는 히트 수준에서 독립적으로 처리됩니다. 즉, 두 개의 컨테이너가 **[!UICONTROL 및]** 연산자인 경우, 두 개의 히트가 요구 사항을 충족하는 경우에만 규칙이 분류됩니다.

1. 에서 **[!UICONTROL 메타데이터]** 필드 **[!UICONTROL + Dimension]** 방문자의 행동과 관련된 특정 캠페인 차원 또는 변수를 선택하려면 다음을 수행하십시오.

   ![](assets/triggers_3.png)

1. **[!UICONTROL 저장]**&#x200B;을 클릭합니다.

1. 새로 만든 항목을 선택합니다 **[!UICONTROL 트리거]** 목록에서 트리거 세부 사항 보고서에 액세스합니다.

   ![](assets/triggers_4.png)

1. 트리거의 세부 보기에서 실행된 트리거 수에 대한 보고서에 액세스할 수 있습니다. 필요한 경우 연필 아이콘을 사용하여 트리거를 편집할 수 있습니다.

   ![](assets/triggers_5.png)
