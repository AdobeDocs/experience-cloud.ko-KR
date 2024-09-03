---
title: 브랜딩
description: 브랜드 구성 방법 살펴보기
audience: administration
context-tags: branding,overview;branding,main
role: Admin
level: Experienced
badge: label="제한된 가용성" type="Informative" url="../campaign-standard-migration-home.md" tooltip="마이그레이션된 사용자 Campaign Standard으로 제한됨"
exl-id: 7afc802d-e90c-48c8-aa04-3ea543dfdfbc
source-git-commit: 62c2f2e7a6f5dd347749e963a655b717cd5c7310
workflow-type: tm+mt
source-wordcount: '377'
ht-degree: 42%

---

# 브랜드 구성 {#branding-configure}

>[!IMPORTANT]
>
>최종 사용자가 브랜드를 만들거나 수정할 수 없습니다. 이러한 작업은 Adobe Campaign 기술 관리자가 수행해야 합니다. 요청이 있으면 Adobe 고객 지원 센터에 문의하십시오.

Adobe Campaign V8의 브랜드는 **[!UICONTROL 관리 > 플랫폼 > 브랜딩]** 메뉴에서 찾을 수 있습니다.

**[!UICONTROL 브랜드]**&#x200B;는 다음과 같은 특성에 의해 정의됩니다.

* 브랜드를 정의하고 개인화하는 **[!UICONTROL 이미지]**&#x200B;입니다. 이 섹션에는 다음 필드가 포함되어 있습니다.

   * 인터페이스에 표시되는 **[!UICONTROL 레이블]**
   * **[!UICONTROL ID]**
   * **[!UICONTROL 브랜드 이름]**
   * 브랜드의 **[!UICONTROL 웹 사이트 URL]** 및 **[!UICONTROL 웹 사이트 레이블]**
   * **[!UICONTROL 브랜드 로고]**

  ![](assets/branding_1.png)

* 캠페인 수신자에게 표시되는 내용을 개인화하는 **[!UICONTROL 보낸 전자 메일의 헤더 매개 변수]**. 이 섹션에는 다음 필드가 포함되어 있습니다.

   * 브랜드 이메일 주소가 있는 **[!UICONTROL 발신자(이메일 주소)]**.
   * 브랜드 이름이 있는 **[!UICONTROL 발신자(이름)]**.
   * 고객이 회신할 수 있는 이메일 주소가 있는 **[!UICONTROL 회신 대상(이메일 주소)]**.
   * 브랜드 이름이 있는 **[!UICONTROL 회신 대상(이름)]**.
   * 오류가 발생한 경우 사용할 이메일 주소가 있는 **[!UICONTROL 오류(이메일 주소)]**.

  >[!IMPORTANT]
  >
  >이메일의 헤더 매개 변수를 업데이트한 후 템플릿에서 만든 이메일에서 발신자의 이름 및 이메일 주소가 변경되지 않은 경우, 템플릿의 고급 설정을 확인하십시오.

  ![](assets/branding_2.png)

* **[!UICONTROL 브랜드 구성]**&#x200B;은(는) 랜딩 페이지 액세스를 위한 추적에도 사용되는 서버를 정의합니다. 이 섹션에는 다음 필드가 포함되어 있습니다.

   * **[!UICONTROL 브랜드 하위 도메인]**&#x200B;이(가) 이 브랜드와 관련된 지정된 하위 도메인 URL을 참조합니다. Adobe에서 위임이 요청됩니다.

  추적, 미러 및 애플리케이션 서버에 대한 구성은 라우팅과 연관된 별도의 외부 계정에 저장됩니다. 이러한 설정은 프로비저닝 중에 적용되므로 수정해서는 안 됩니다. URL을 표시하려면 외부 계정에서 **[!UICONTROL 브랜딩 접두사]** 탭에 액세스하십시오.

  ![](assets/branding_3.png)

* **[!UICONTROL URL 구성 추적]** 메뉴를 사용하면 Adobe Analytics 및 Google Analytics과 같은 Web Analytics 도구와의 통합을 위한 추가 매개 변수를 정의하여 URL 추적을 개선할 수 있습니다.

  **[!UICONTROL 추가 URL 매개 변수]** 메뉴를 사용하여 적용 가능성 조건과 함께 추가 매개 변수를 키-값 쌍으로 만드십시오. 각 매개 변수 이름은 고유해야 하며 비어 있지 않아야 하고, 각 매개 변수 값은 비어 있지 않아야 합니다. 적용 가능성 조건은 비어 있을 수 있지만 이러한 값 중 JST 태그를 포함할 수 있는 값은 없습니다.

  이러한 매개 변수는 **[!UICONTROL 도메인 이름 목록]**&#x200B;에 지정된 모든 도메인 이름과 일치하는 추적된 URL에 적용되며, 여기에는 정규 표현식이 포함될 수 있습니다.
