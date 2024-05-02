---
title: 브랜딩
description: 브랜드 구성 방법 살펴보기
audience: administration
context-tags: branding,overview;branding,main
role: Admin
level: Experienced
badge: label="제한된 가용성" type="Informative" url="../campaign-standard-migration-home.md" tooltip="마이그레이션된 사용자 Campaign Standard으로 제한됨"
source-git-commit: 56f2d2ff4b2ba4184629615a14724e6640df6961
workflow-type: tm+mt
source-wordcount: '277'
ht-degree: 57%

---

# 브랜드 구성 {#branding-configure}

>[!IMPORTANT]
>
>최종 사용자가 브랜드를 만들거나 수정할 수 없습니다. 이러한 작업은 Adobe Campaign 기술 관리자가 수행해야 합니다. 요청이 있으면 Adobe 고객 지원 센터에 문의하십시오.

Adobe Campaign V8에서 브랜드는 **[!UICONTROL 관리 > 플랫폼 > 브랜딩]** 메뉴 아래의 제품에서 사용할 수 있습니다.

**[!UICONTROL 브랜드]**&#x200B;는 다음과 같은 특성에 의해 정의됩니다.

* 브랜드를 정의하고 개인화하는 **[!UICONTROL 이미지]**&#x200B;입니다. 이 섹션에는 다음 필드가 포함되어 있습니다.

   * 인터페이스에 표시되는 **[!UICONTROL 레이블]**
   * **[!UICONTROL ID]**
   * **[!UICONTROL 브랜드 이름]**
   * 브랜드의 **[!UICONTROL 웹 사이트 URL]** 및 **[!UICONTROL 웹 사이트 레이블]**
   * **[!UICONTROL 브랜드 로고]**

  ![](assets/branding_1.png)

* **[!UICONTROL 보낸 이메일의 헤더 매개변수]** 는 캠페인 수신자가 보게 되는 내용을 개인화합니다. 이 섹션에는 다음 필드가 포함되어 있습니다.

   * 브랜드 이메일 주소가 있는 **[!UICONTROL 발신자(이메일 주소)]**.
   * 브랜드 이름이 있는 **[!UICONTROL 발신자(이름)]**.
   * 고객이 회신할 수 있는 이메일 주소가 있는 **[!UICONTROL 회신 대상(이메일 주소)]**.
   * 브랜드 이름이 있는 **[!UICONTROL 회신 대상(이름)]**.
   * 오류가 발생한 경우 사용할 이메일 주소가 있는 **[!UICONTROL 오류(이메일 주소)]**.

  >[!IMPORTANT]
  >
  >이메일의 헤더 매개 변수를 업데이트한 후 템플릿에서 만든 이메일에서 발신자의 이름 및 이메일 주소가 변경되지 않은 경우, 템플릿의 고급 설정을 확인하십시오.

  ![](assets/branding_2.png)

* **[!UICONTROL 브랜드 구성]** 추적에 사용되는 서버와 랜딩 페이지 액세스를 정의합니다. 이 섹션에는 다음 필드가 포함되어 있습니다.

   * **[!UICONTROL 브랜드 하위 도메인]** 은(는) Adobe에서 위임이 요청된 이 브랜드와 관련된 지정된 하위 도메인 URL을 나타냅니다.

  추적, 미러 및 애플리케이션 서버에 대한 구성은 라우팅과 연관된 별도의 외부 계정에 저장됩니다. 이러한 설정은 프로비저닝 중에 적용되므로 수정해서는 안 됩니다. URL을 표시하려면 **[!UICONTROL 브랜딩 접두사]** 외부 계정의 탭입니다.

  ![](assets/branding_3.png)

<!--![](assets/branding_05.png)-->

<!--
* **[!UICONTROL Tracking URL configs]**, which defines the configuration of the URLs tracking for your brand.

  The additional parameters that allow the links to be tracked on external systems such as Web Analytics tools like Adobe Analytics or Google Analytics are defined here.
-->
