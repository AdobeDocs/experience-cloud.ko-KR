---
title: Adobe Experience Cloud Debugger를 사용하여 실행 환경 전환
description: Experience Cloud Debugger를 사용하여 다른 Launch 포함 코드를 로드하는 방법을 알아봅니다. 이 수업은 Launch를 사용하여 웹 사이트에서 Experience Cloud 구현 자습서의 일부입니다.
seo-description: null
seo-title: Adobe Experience Cloud Debugger를 사용하여 실행 환경 전환
solution: Experience Cloud
translation-type: tm+mt
source-git-commit: 79d5274d09d66b80a49aba5db3e0a997d0f0ff61

---


# Experience Cloud Debugger를 사용하여 실행 환경 전환

In this lesson you will use the [Adobe Experience Cloud Debugger extension](https://chrome.google.com/webstore/detail/adobe-experience-cloud-de/ocdmogmohccmeicdhlhhgepeaijenapj) to replace the Launch property hardcoded on the [Luma demo site](https://luma.enablementadobe.com/content/luma/us/en.html) with your own property.

이 기술은 환경 전환이라고 하며 나중에 자체 웹 사이트에서 Launch를 사용하여 작업할 때 유용합니다. 브라우저에 프로덕션 웹 사이트를 로드할 수 있지만 *개발* 시작 환경을 사용하면 됩니다. 이를 통해 일반 코드 릴리스와 별도로 론치 변경 사항을 안전하게 만들고 확인할 수 있습니다.  결국, 일반적인 코드 릴리스에서 마케팅 태그 릴리스가 분리되는 것은 고객이 처음부터 Launch를 사용하는 주된 이유 중 하나입니다!

## 학습 목표

이 단원을 마치면 다음을 수행할 수 있습니다.

* 디버거를 사용하여 대체 실행 환경 로드
* 디버거를 사용하여 대체 실행 환경을 로드했는지 확인합니다

## 개발 환경의 URL 가져오기

1. In your Launch property, open the `Environments` page

1. In the **[!UICONTROL Development]** row, click the Install icon ![Install icon](images/launch-installIcon.png) to open the modal

1. 복사 아이콘 ![복사 아이콘을](images/launch-copyIcon.png) 클릭하여 포함 코드를 클립보드에 복사합니다

1. Click **[!UICONTROL Close]** to close the modal

   ![설치 아이콘](images/launch-copyInstallCode.png)

## 루마 데모 사이트에서 시작 URL 바꾸기

1. Open the [Luma demo site](https://luma.enablementadobe.com/content/luma/us/en.html) in your Chrome browser

1. 디버거 [아이콘](https://chrome.google.com/webstore/detail/adobe-experience-cloud-de/ocdmogmohccmeicdhlhhgepeaijenapj) 아이콘을 클릭하여 ![Experience Cloud 디버거 확장](images/icon-debugger.png) 열기

   ![디버거 아이콘 클릭](images/switchEnvironments-openDebugger.png)

1. 현재 구현된 론치 속성은 요약 탭에 표시됩니다

   ![디버거에 표시된 실행 환경](images/switchEnvironments-debuggerOnWeRetail-prod.png)

1. 도구 탭으로 이동

1. 론치 포함 코드 **[!UICONTROL 바꾸기 섹션으로 스크롤]**

1. Luma 사이트의 Chrome 탭이 디버거(이 튜토리얼의 탭 또는 Launch 인터페이스의 탭이 아님) 뒤에 있는지 확인합니다.  클립보드에 있는 포함 코드를 입력 필드에 붙여 넣습니다.

1. Luma 사이트의 모든 페이지가 Launch 속성에 매핑되도록 "luma.enablementadobe.com에 적용" 기능을 켜거나 끕니다.

1. 저장 **[!UICONTROL 단추를]** 클릭합니다

   ![디버거에 표시된 실행 환경](images/switchEnvironments-debugger-save.png)

1. 루마 사이트를 다시 로드하고 디버거의 요약 탭을 선택합니다. 이제 론치 섹션에서 개발 속성이 사용 중임을 확인할 수 있습니다. 두 속성 이름이 모두 사용자의 이름과 일치하는지 확인하고 환경에 "개발"이 표시되는지 확인합니다.

   ![디버거에 표시된 실행 환경](images/switchEnvironments-debuggerOnWeRetail.png)

>[!NOTE] 디버거가 이 구성을 저장하고 Luma 사이트로 돌아올 때마다 Launch 포함 코드를 바꿉니다. 다른 열린 탭에서 방문하는 다른 사이트에는 영향을 주지 않습니다. To stop the Debugger from replacing the embed code, click the **[!UICONTROL Remove]** button next to the embed code in the Tools tab of the Debugger.

튜토리얼을 계속 진행하면 Luma 사이트를 자체 Launch 속성에 매핑하여 Launch 구현의 유효성을 확인하는 이 기법을 사용합니다. 프로덕션 웹 사이트에서 Launch를 사용할 때 동일한 기술을 사용하여 변경 내용의 유효성을 확인할 수 있습니다.

[다음 "Adobe Experience Platform ID 서비스 추가" &gt;](id-service.md)