---
title: 론치 속성 만들기
description: Launch 인터페이스에 로그인하고 Launch 속성을 만드는 방법을 알아봅니다. 이 수업은 Launch를 사용하여 웹 사이트에서 Experience Cloud 구현 자습서의 일부입니다.
seo-description: null
seo-title: 론치 속성 만들기
solution: Experience Cloud
translation-type: tm+mt
source-git-commit: 7166d2933cc99bcbbd4713fba8f87fb0826b711e

---


# 론치 속성 만들기

이 단원에서는 첫 번째 Launch 속성을 만듭니다.

속성은 사이트에 태그를 배포할 때 기본적으로 확장, 규칙, 데이터 요소 및 라이브러리로 채우는 컨테이너입니다.

## 전제 조건

다음 몇 가지 강의를 마치려면 Launch에서 환경 개발, 승인, 게시, 관리 및 게시 권한이 있어야 합니다. 사용자 인터페이스 옵션을 사용할 수 없으므로 이러한 단계를 완료할 수 없는 경우 Experience Cloud 관리자에게 문의하여 액세스 권한을 요청하십시오. For more information on Launch permissions, see [the documentation](https://docs.adobe.com/content/help/en/launch/using/reference/admin/user-permissions.html).

## 학습 목표

이 단원을 마치면 다음을 수행할 수 있습니다.

* Launch 사용자 인터페이스에 로그인
* 새 론치 속성 만들기
* 론치 속성 구성

## Launch로 이동

**Launch에 액세스하려면**

1. Adobe Experience [Cloud에 로그인](https://experiencecloud.adobe.com)

1. 솔루션 ![전환기 아이콘](images/launch-solutionSwitcher.png) 을 클릭하여 솔루션 전환기를 엽니다

1. 메뉴에서 **[!UICONTROL 실행]** 선택 ![아이콘을 사용하여 솔루션전환기를 열고 활성화를 클릭합니다](images/launch-solutionSwitcherActivation.png)

1. Adobe **[!UICONTROL Experience Cloud Launch]**&#x200B;에서 시작으로 **[!UICONTROL 이동 단추를 클릭합니다]**

   ![시작 단추를 클릭합니다.](images/launch-goToLaunch.png)

You should now see the `Properties` screen (if no properties have ever been created in the account, this screen might be empty):

![속성 화면](images/launch-propertiesScreen.png)

Launch를 자주 사용하는 경우 다음 URL을 책갈피로 지정하고 직접 https://launch.adobe.com에 로그인할 수도 [있습니다.](https://launch.adobe.com)

## 속성 만들기

속성은 사이트에 태그를 배포할 때 기본적으로 확장, 규칙, 데이터 요소 및 라이브러리로 채우는 컨테이너입니다. 속성은 하나 이상의 도메인과 하위 도메인을 그룹화한 것일 수 있습니다. 이 자산들은 유사하게 관리 및 추적할 수 있습니다. 예를 들어 하나의 템플릿을 기반으로 한 여러 개의 웹 사이트가 있고 이러한 웹 사이트 모두에서 동일한 자산을 추적하려 하는 경우, 여러 도메인에 하나의 속성을 적용할 수 있습니다. 속성 만들기에 대한 자세한 내용은 제품 설명서의 ["회사 및 속성"](https://docs.adobe.com/content/help/en/launch/using/reference/admin/companies-and-properties.html) 을 참조하십시오.

**속성 만들기**

1. 새 **[!UICONTROL 속성]** 단추를 클릭합니다.

   ![새 속성 클릭](images/launch-addNewProperty.png)

1. 속성 이름 지정(예: `Launch Tutorial` 또는 `Daniel's Launch Tutorial`)
1. 도메인으로 Luma 데모 사이트가 호스팅되는 도메인이므로 입력합니다. `enablementadobe.com` "도메인" 필드가 필요하지만 Launch 속성은 구현된 모든 도메인에서 작동합니다. 이 필드의 주 목적은 규칙 빌더에서 메뉴 옵션을 미리 채우는 것입니다.
1. 저장 **[!UICONTROL 단추를]** 클릭합니다

   ![새 속성 만들기](images/launch-newProperty.png)

새 속성은 속성 페이지에 표시됩니다. Note that if you check the box next to the property name, options to **[!UICONTROL Configure]** or **[!UICONTROL Delete]** the property appear above the property list. 속성 이름(예:) `Launch Tutorial`to open the `Overview` screen.
![속성 이름을 클릭하여 엽니다](images/launch-openProperty.png)

[다음 "시작 포함 코드 추가" &gt;](launch-add-embed.md)
