---
title: 글로벌 금지 목록
description: 글로벌 금지 목록 살펴보기
hide: true
exl-id: 40aef987-52a3-470b-88ca-c716a116bdfc
source-git-commit: 9d12eece2ca9f8f36951f8575bb0ac42bc10a728
workflow-type: tm+mt
source-wordcount: '618'
ht-degree: 96%

---

# 글로벌 금지 목록 {#global-suppression-list}

금지 목록은 고객이 게재에서 제외하려는 이메일 주소로 구성되어 있습니다. 이러한 연락처로 전송하면 전송 평판과 게재 속도가 떨어질 수 있기 때문입니다. 현재 Adobe는 참여도 및 메일링 평판에 유해한 것으로 증명된 악성 이메일 주소의 최신 목록을 업데이트하여 이메일이 전송되지 않도록 합니다. 이 목록은 모든 Adobe 고객에게 공통으로 적용되는 글로벌 금지 목록에서 관리됩니다. 글로벌 금지 목록에 포함된 주소와 도메인 이름은 숨겨집니다. 게재 보고서에는 제외된 수신자 수만 표시됩니다.

이제 내부적으로 사용 가능한 인터페이스에서 글로벌 금지 목록을 관리할 수 있습니다. 이 목록은 게재 가능성 컨설턴트에 의해서만 유지 관리됩니다. 글로벌 금지 목록에는 이메일 또는 도메인 주소가 포함될 수 있습니다.

## 글로벌 금지 목록 액세스

제외된 이메일 주소 및 도메인의 세부 목록에 액세스하려면 **[!UICONTROL 글로벌 금지 목록]**&#x200B;으로 이동하십시오.

>[!CAUTION]
>
>글로벌 금지 목록을 조회하고, 내보내고, 관리할 수 있는 권한은 할당된 배포 목록에 따라 다릅니다. 추가 정보

다음 두 개의 탭이 표시됩니다. **[!UICONTROL 이메일]** 및 **[!UICONTROL 도메인]**.

필터를 사용하여 목록을 탐색할 수 있습니다.

## 주소 및 도메인 추가

현재 글로벌 금지 목록에 주소를 추가하는 방법에는 두 가지가 있습니다.

* 게재 가능성 팀에서 선별한 목록입니다.
* 서드파티 서비스 제공업체 Blackbox에서 제공하는 목록입니다.

이메일 주소나 도메인을 [한 번에 하나씩](#add-one-address-or-domain) 추가하거나 CSV 파일 업로드를 통해 [일괄 모드](#upload-csv-file)로 추가할 수 있습니다.

이 작업을 수행하려면 **[!UICONTROL 이메일 또는 도메인 추가]** 버튼을 선택한 다음 아래 방법 중 하나를 따르십시오.

### 하나의 주소 또는 도메인 추가 {#add-one-address-or-domain}

1. **[!UICONTROL 하나씩]** 옵션을 선택합니다.

1. 주소 유형을 선택합니다. **[!UICONTROL 이메일 주소]** 또는 **[!UICONTROL 도메인 주소]**.

1. 전송에서 제외할 이메일 주소 또는 도메인을 입력합니다.

   >[!NOTE]
   >
   >유효한 이메일 주소(예: abc@company.com) 또는 도메인(예: abc.company.com)을 입력했는지 확인합니다.

1. 필요한 경우 이유를 지정합니다.

   >[!NOTE]
   >
   >이 필드에는 32~126 사이로 구성된 모든 ASCII 인쇄 가능 문자가 허용됩니다. 예를 들어 [이 페이지](https://en.wikipedia.org/wiki/Wikipedia:ASCII#ASCII_printable_characters){target="_blank"}에서 전체 목록을 찾을 수 있습니다.

1. **[!UICONTROL 제출]**&#x200B;을 클릭하여 확인합니다.

### CSV 파일 업로드 {#upload-csv-file}

1. **[!UICONTROL CSV 업로드]** 옵션을 선택합니다.

1. 아래 열과 형식이 포함된 CSV 템플릿을 다운로드하여 사용할 수 있습니다.

   ```
   TYPE,VALUE,COMMENT
   EMAIL,abc@somedomain.com,Comment
   DOMAIN,somedomain.com,Comment
   ```

   >[!CAUTION]
   >
   >CSV 템플릿의 열 이름을 변경하지 마십시오.
   >
   >파일 크기는 1MB를 초과해서는 안 됩니다.

1. 금지 목록에 추가하려는 모든 이메일 및/또는 도메인으로 CSV 템플릿을 채웁니다.

   >[!NOTE]
   >
   >**댓글** 열에는 32~126 사이로 구성된 모든 ASCII 문자가 허용됩니다. 예를 들어 [이 페이지](https://en.wikipedia.org/wiki/Wikipedia:ASCII#ASCII_printable_characters){target="_blank"}에서 전체 목록을 찾을 수 있습니다.

1. 완료되면 CSV 파일을 드래그 앤 드롭한 다음 **[!UICONTROL 제출]**&#x200B;을 클릭하여 확인합니다.

>[!NOTE]
>
>업로드가 완료되면 인터페이스에서 상태를 확인하여 업로드가 성공적으로 완료되었는지 확인합니다. [방법 알아보기](#recent-uploads)

### 최근 업로드 상태 확인 {#recent-uploads}

**[!UICONTROL 최근 업로드]** 버튼을 클릭하여 업로드한 최신 CSV 파일의 상태를 확인합니다.

가능한 상태는 다음과 같습니다.

* **[!UICONTROL 보류 중]**: 파일 업로드가 진행 중입니다.
* **[!UICONTROL 오류]**: 기술적인 문제 또는 파일 형식 오류로 인해 파일 업로드 프로세스가 실패했습니다.
* **[!UICONTROL 완료]**: 파일 업로드 프로세스가 정상적으로 완료되었습니다.

업로드하는 도중 일부 주소가 올바른 형식이 아닌 경우 글로벌 금지 목록에 추가되지 않습니다.

이 경우 업로드가 완료되면 보고서와 연결됩니다. 다운로드하여 발생한 오류를 확인할 수 있습니다.

## 주소 제거

글로벌 금지 목록에서 주소를 제거하려면 **[!UICONTROL 삭제]** 버튼을 사용합니다.

>[!CAUTION]
>
>서드파티 서비스 제공업체 Blackbox에서 자동으로 추가한 주소나 도메인은 컨설턴트가 인터페이스를 통해 제거할 수 없습니다. 이 작업은 백엔드 티켓을 통해서만 수행할 수 있습니다.
