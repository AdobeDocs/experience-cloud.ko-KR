---
title: 사용자 정의 프로필 차원 만들기
description: 사용자 지정 프로필 데이터를 기반으로 사용자 지정 프로필 차원을 만드는 방법을 알아봅니다.
audience: reporting
content-type: reference
level: Intermediate
source-git-commit: 5a7337c44d6ca5ee4403d9fe0b65246b629afacd
workflow-type: tm+mt
source-wordcount: '457'
ht-degree: 3%

---

# 사용자 정의 프로필 차원 만들기{#creating-a-custom-profile-dimension}

수신자 스키마 확장 중에 생성된 사용자 지정 프로필 데이터를 기반으로 보고서를 만들고 관리할 수도 있습니다.

* [1단계: 수신자 스키마 확장](##extend-schema)
* [2단계: 새 사용자 정의 필드 연결](#link-custom)
* [3단계: 동적 보고서를 만들어 수신자를 사용자 지정 프로필 차원으로 필터링합니다](#create-report)

## 1단계: 수신자 스키마 확장 {#extend-schema}

새 프로필 필드를 추가하려면 스키마를 확장해야 합니다. 아래 단계를 따르십시오.

1. 다음 위치로 이동 **[!UICONTROL 관리]** > **[!UICONTROL 구성]** > **[!UICONTROL 데이터 스키마]** 폴더의 Explorer에서 폴더를 검색합니다.

   ![](assets/custom_field_1.png)

1. 사용자 지정 수신자 스키마를 식별하고 선택합니다. 기본 제공 nms:recipient 스키마를 아직 확장하지 않은 경우 다음을 참조하십시오. [이 절차](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/developer/shemas-forms/extend-schema).

1. 스키마 편집기에 사용자 정의 필드를 추가합니다.

   예를 들어 수신자 스키마에 충성도 사용자 정의 필드를 추가하려면:

   ```
   <attribute label="Loyalty" name="loyalty" type="string"/>
   ```

   ![](assets/custom_field_2.png)

1. **[!UICONTROL 저장]**&#x200B;을 클릭합니다.

1. 그런 다음 사용자 정의 broadLogRcp 스키마를 식별하고 선택합니다. 기본 제공 게재 로그 스키마를 아직 확장하지 않은 경우 다음을 참조하십시오. [이 절차](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/developer/shemas-forms/extend-schema).

1. 스키마 편집기에 수신자 스키마와 동일한 사용자 지정 필드를 추가합니다.

   ![](assets/custom_field_3.png)

1. **[!UICONTROL 저장]**&#x200B;을 클릭합니다.

1. 스키마에 대한 수정 사항을 적용하려면 다음을 통해 데이터베이스 업데이트 마법사를 시작합니다. **[!UICONTROL 도구]** > **[!UICONTROL 고급]** > **[!UICONTROL 데이터베이스 구조 업데이트]** 데이터베이스 구조 업데이트를 실행합니다. [자세히 알아보기](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/developer/shemas-forms/update-database-structure)

   ![](assets/custom_field_4.png)

이제 수신자가 새 프로필 필드를 사용하고 선택할 준비가 되었습니다.

## 2단계: 새 사용자 정의 필드 연결 {#link-custom}

>[!NOTE]
>
> 동적 보고서에 최대 20개의 사용자 지정 필드만 추가할 수 있습니다.

프로필 필드가 생성되었으므로 해당 동적 보고 차원에 연결해야 합니다.

1. 다음 위치로 이동 **[!UICONTROL 관리]** > **[!UICONTROL 구성]** > **[!UICONTROL 데이터 스키마]** > **[!UICONTROL 추가 보고 필드]** 폴더의 Explorer에서 폴더를 검색합니다.

   ![](assets/custom_field_5.png)

1. 클릭 **[!UICONTROL 신규]** 를 클릭하여 해당 동적 보고 차원을 만듭니다.

1. 선택 **[!UICONTROL 표현식 편집]** 수신자 스키마를 탐색하여 이전에 만든 사용자 지정 프로필 필드를 찾습니다.

   ![](assets/custom_field_6.png)

1. **[!UICONTROL 마침을 클릭합니다]**.

1. 차원을 입력합니다 **[!UICONTROL 레이블]**&#x200B;를 동적 보고에 표시하고 을 클릭합니다. **[!UICONTROL 저장]**.

   ![](assets/custom_field_7.png)

이제 사용자 지정 프로필 필드를 보고서에서 사용자 지정 프로필 차원으로 사용할 수 있습니다. 사용자 지정 프로필 차원을 삭제하려면 해당 차원을 선택하고 **[!UICONTROL 삭제]** 아이콘.

이제 수신자 스키마가 이 프로필 필드로 확장되고 사용자 지정 차원이 생성되었으므로 게재에서 수신자를 타겟팅할 수 있습니다.

## 3단계: 동적 보고서를 만들어 수신자를 사용자 지정 프로필 차원으로 필터링합니다 {#create-report}

게재를 보낸 후 사용자 지정 프로필 차원을 사용하여 보고서를 분류할 수 있습니다.

1. 다음에서 **[!UICONTROL 보고서]** 탭에서 기본 제공 보고서를 선택하거나 **[!UICONTROL 만들기]** 단추를 클릭하여 처음부터 새로 시작합니다.

   ![](assets/custom_field_8.png)

1. 다음에서 **[!UICONTROL Dimension]** 범주, 클릭 **[!UICONTROL 프로필]** 그런 다음 사용자 지정 프로필 차원을 자유 형식 테이블로 끌어서 놓습니다.

   ![](assets/custom_field_9.png)

1. 지표를 드래그하여 놓아 데이터 필터링을 시작합니다.

1. 필요한 경우 작업 공간에 시각화를 끌어서 놓습니다.
