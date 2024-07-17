---
title: 브랜딩
description: 브랜드를 할당하는 방법 살펴보기
audience: administration
context-tags: branding,overview;branding,main
role: Admin
level: Experienced
badge: label="제한된 가용성" type="Informative" url="../campaign-standard-migration-home.md" tooltip="마이그레이션된 사용자 Campaign Standard으로 제한됨"
exl-id: 8f6a5255-0245-497b-880f-d91ea82ee19e
source-git-commit: 34c6f8a137a9085b26c0ea8f78930cff6192cfc9
workflow-type: tm+mt
source-wordcount: '481'
ht-degree: 18%

---

# 브랜드 할당 {#branding-assign}

>[!IMPORTANT]
>
>브랜딩 옵션은 현재 이메일 및 푸시 게재로 제한됩니다.

## 템플릿에 브랜드 연결 {#linking-a-brand-to-a-template}

브랜드에 대해 정의된 매개 변수를 사용하려면 게재 템플릿에 연결해야 합니다. 이렇게 하려면 템플릿을 만들거나 편집해야 합니다.

템플릿이 브랜드에 연결됩니다. 이메일 편집기에서 **기본 발신자의 이메일 주소**, **기본 발신자 이름**&#x200B;또는 **로고**&#x200B;와 같은 요소는 구성된 브랜드 데이터를 사용합니다.

>[!BEGINTABS]

>[!TAB Adobe Campaign V8]

게재 템플릿을 만들려면 기본 제공 템플릿을 복제하거나, 기존 게재를 템플릿으로 변환하거나, 처음부터 게재 템플릿을 만들 수 있습니다. [자세히 알아보기](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/create-templates)

일단 템플릿이 생성되면 브랜드에 연결할 수 있습니다. 방법은 다음과 같습니다.

1. Adobe Campaign 탐색기에서 **[!UICONTROL 리소스]** `>` **[!UICONTROL 템플릿]** `>` **[!UICONTROL 게재 템플릿]**(으)로 이동합니다.

1. 게재 템플릿을 선택하거나 기존 템플릿을 복제합니다.

   ![](assets/branding_assign_V8_1.png)

1. 선택한 게재 템플릿의 **[!UICONTROL 속성]**&#x200B;에 액세스합니다.

   ![](assets/branding_assign_V8_2.png)

1. **[!UICONTROL 일반]** 탭의 **[!UICONTROL 브랜딩]** 드롭다운에서 브랜드를 선택합니다.

   ![](assets/branding_assign_V8_3.png)

1. 구성이 완료되면 **확인**&#x200B;을 선택합니다.

이제 이 템플릿을 사용하여 게재를 보낼 수 있습니다.

>[!TAB Adobe Campaign 웹]

게재 템플릿을 만들려면 기본 제공 템플릿을 복제하거나, 기존 게재를 템플릿으로 변환하거나, 처음부터 게재 템플릿을 만들 수 있습니다. [자세히 알아보기](https://experienceleague.adobe.com/en/docs/campaign-web/v8/msg/delivery-template)

일단 템플릿이 생성되면 브랜드에 연결할 수 있습니다. 방법은 다음과 같습니다.

1. **[!UICONTROL 게재]** 왼쪽 메뉴에서 **[!UICONTROL 템플릿]** 탭으로 이동한 다음 게재 템플릿을 선택합니다.

   ![](assets/branding_assign_web_1.png)

1. **[!UICONTROL 설정]**&#x200B;을 클릭합니다.

   ![](assets/branding_assign_web_2.png)

1. **[!UICONTROL 게재]** 탭에서 **[!UICONTROL 브랜딩]** 필드에 액세스하고 템플릿에 연결할 브랜드를 선택합니다.

   ![](assets/branding_assign_web_3.png)

1. 선택을 확인하고 템플릿을 저장합니다.

이제 이 템플릿을 사용하여 게재를 보낼 수 있습니다.

>[!ENDTABS]

## 게재에 브랜드 할당 {#assigning-a-brand-to-an-email}

>[!BEGINTABS]

>[!TAB Adobe Campaign V8]

새 독립 실행형 게재를 만들려면 아래 단계를 수행하십시오.

1. 새 게재를 만들려면 **[!UICONTROL 캠페인]** 탭으로 이동합니다.

1. **[!UICONTROL 게재]**&#x200B;를 클릭하고 기존 게재 목록 위에 있는 **[!UICONTROL 만들기]** 단추를 클릭합니다.

   ![](assets/branding_assign_V8_4.png)

1. 게재 템플릿을 선택합니다.

1. 선택한 게재 템플릿의 **[!UICONTROL 속성]**&#x200B;에 액세스합니다.

   ![](assets/branding_assign_V8_5.png)

1. **[!UICONTROL 일반]** 탭의 **[!UICONTROL 브랜딩]** 드롭다운에서 브랜드를 선택합니다.

   ![](assets/branding_assign_V8_6.png)

1. 구성이 완료되면 **확인**&#x200B;을 선택합니다.

1. 게재를 개인화할 수 있습니다. 전자 메일 만들기에 대한 자세한 내용은 [전자 메일 디자인 및 보내기](https://experienceleague.adobe.com/en/docs/campaign-web/v8/msg/email/create-email) 섹션을 참조하세요.

>[!TAB Adobe Campaign 웹]

새 독립 실행형 게재를 만들려면 아래 단계를 수행하십시오.

1. 왼쪽 레일의 **[!UICONTROL 게재]** 메뉴로 이동한 다음 **[!UICONTROL 게재 만들기]** 단추를 클릭합니다.

   ![](assets/branding_assign_web_4.png)

1. 채널로 이메일 또는 푸시 알림 을 선택하고 목록에서 게재 템플릿을 선택합니다.

1. **[!UICONTROL 게재 만들기]** 버튼을 클릭하여 확인합니다.

1. **[!UICONTROL 속성]** 페이지에서 **[!UICONTROL 설정]**&#x200B;을 클릭합니다.

   ![](assets/branding_assign_web_5.png)

1. **[!UICONTROL 배달]** 탭에서 **[!UICONTROL 브랜딩]** 필드에 액세스합니다.

   ![](assets/branding_assign_web_6.png)

1. 템플릿에 연결할 브랜드를 선택합니다.

   ![](assets/branding_assign_web_7.png)

1. 게재를 개인화할 수 있습니다. 전자 메일 만들기에 대한 자세한 내용은 [첫 번째 전자 메일 만들기](https://experienceleague.adobe.com/en/docs/campaign-web/v8/msg/email/create-email) 섹션을 참조하세요.

>[!ENDTABS]
