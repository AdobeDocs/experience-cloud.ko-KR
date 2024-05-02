---
title: 브랜딩
description: 브랜드를 할당하는 방법 살펴보기
audience: administration
context-tags: branding,overview;branding,main
role: Admin
level: Experienced
badge: label="제한된 가용성" type="Informative" url="../campaign-standard-migration-home.md" tooltip="마이그레이션된 사용자 Campaign Standard으로 제한됨"
source-git-commit: 51abadc86b97097d13824651d8c50d4ddd014a51
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

>[!TAB Adobe Campaign]

게재 템플릿을 만들려면 기본 제공 템플릿을 복제하거나, 기존 게재를 템플릿으로 변환하거나, 처음부터 게재 템플릿을 만들 수 있습니다. [자세히 알아보기](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/create-templates)

일단 템플릿이 생성되면 브랜드에 연결할 수 있습니다. 다음 작업을 수행하십시오.

1. 다음으로 이동 **[!UICONTROL 리소스]** `>` **[!UICONTROL 템플릿]** `>` **[!UICONTROL 게재 템플릿]** Adobe Campaign 탐색기를 참조하십시오.

1. 게재 템플릿을 선택하거나 기존 템플릿을 복제합니다.

   ![](assets/branding_assign_V8_1.png)

1. 액세스 **[!UICONTROL 속성]** 선택한 게재 템플릿

   ![](assets/branding_assign_V8_2.png)

1. 다음에서 **[!UICONTROL 일반]** 탭에서 브랜드를 선택합니다. **[!UICONTROL 브랜딩]** 드롭다운.

   ![](assets/branding_assign_V8_3.png)

1. 구성이 완료되면 다음을 선택합니다. **확인**.

이제 이 템플릿을 사용하여 게재를 보낼 수 있습니다.

>[!TAB Adobe Campaign 웹]

게재 템플릿을 만들려면 기본 제공 템플릿을 복제하거나, 기존 게재를 템플릿으로 변환하거나, 처음부터 게재 템플릿을 만들 수 있습니다. [자세히 알아보기](https://experienceleague.adobe.com/en/docs/campaign-web/v8/msg/delivery-template)

일단 템플릿이 생성되면 브랜드에 연결할 수 있습니다. 다음 작업을 수행하십시오.

1. 다음으로 이동 **[!UICONTROL 템플릿]** 탭, **[!UICONTROL 게재]** 왼쪽 메뉴에서 게재 템플릿을 선택합니다.

   ![](assets/branding_assign_web_1.png)

1. 클릭 **[!UICONTROL 설정]**.

   ![](assets/branding_assign_web_2.png)

1. 다음에서 **[!UICONTROL 게재]** 탭, 액세스 **[!UICONTROL 브랜딩]** 필드에 추가하고 템플릿에 연결할 브랜드를 선택합니다.

   ![](assets/branding_assign_web_3.png)

1. 선택을 확인하고 템플릿을 저장합니다.

이제 이 템플릿을 사용하여 게재를 보낼 수 있습니다.

>[!ENDTABS]

## 게재에 브랜드 할당 {#assigning-a-brand-to-an-email}

>[!BEGINTABS]

>[!TAB Adobe Campaign]

새 독립 실행형 게재를 만들려면 아래 단계를 수행하십시오.

1. 새 게재를 만들려면 **[!UICONTROL 캠페인]** 탭.

1. 클릭 **[!UICONTROL 게재]** 을(를) 클릭하고 **[!UICONTROL 만들기]** 기존 게재 목록 위에 있는 단추입니다.

   ![](assets/branding_assign_V8_4.png)

1. 게재 템플릿을 선택합니다.

1. 액세스 **[!UICONTROL 속성]** 선택한 게재 템플릿

   ![](assets/branding_assign_V8_5.png)

1. 다음에서 **[!UICONTROL 일반]** 탭에서 브랜드를 선택합니다. **[!UICONTROL 브랜딩]** 드롭다운.

   ![](assets/branding_assign_V8_6.png)

1. 구성이 완료되면 다음을 선택합니다. **확인**.

1. 게재를 개인화할 수 있습니다. 전자 메일 만들기에 대한 자세한 내용은 [이메일 디자인 및 보내기](https://experienceleague.adobe.com/en/docs/campaign-web/v8/msg/email/create-email) 섹션.

>[!TAB Adobe Campaign 웹]

새 독립 실행형 게재를 만들려면 아래 단계를 수행하십시오.

1. 다음으로 이동 **[!UICONTROL 게재]** 왼쪽 레일에서 메뉴를 클릭하고 **[!UICONTROL 게재 만들기]** 단추를 클릭합니다.

   ![](assets/branding_assign_web_4.png)

1. 채널로 이메일 또는 푸시 알림 을 선택하고 목록에서 게재 템플릿을 선택합니다.

1. **[!UICONTROL 게재 만들기]** 버튼을 클릭하여 확인합니다.

1. 다음에서 **[!UICONTROL 속성]** 페이지, 클릭 **[!UICONTROL 설정]**.

   ![](assets/branding_assign_web_5.png)

1. 다음에서 **[!UICONTROL 게재]** 탭, 액세스 **[!UICONTROL 브랜딩]** 필드.

   ![](assets/branding_assign_web_6.png)

1. 템플릿에 연결할 브랜드를 선택합니다.

   ![](assets/branding_assign_web_7.png)

1. 게재를 개인화할 수 있습니다. 전자 메일 만들기에 대한 자세한 내용은 [첫 번째 이메일 만들기](https://experienceleague.adobe.com/en/docs/campaign-web/v8/msg/email/create-email) 섹션.

>[!ENDTABS]
