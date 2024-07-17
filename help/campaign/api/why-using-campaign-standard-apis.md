---
title: Campaign Standard API를 사용하는 이유
description: Campaign Standard API 및 이를 사용하는 이유에 대해 자세히 알아보십시오.
audience: developing
content-type: reference
topic-tags: campaign-standard-apis
role: Data Engineer
level: Experienced
badge: label="제한된 가용성" type="Informative" url="../campaign-standard-migration-home.md" tooltip="마이그레이션된 사용자 Campaign Standard으로 제한됨"
exl-id: ef045e5d-cd02-44a0-9a1e-d468483a38d9
source-git-commit: 14d8cf78192bcad7b89cc70827f5672bd6e07f4a
workflow-type: tm+mt
source-wordcount: '481'
ht-degree: 1%

---

# Campaign Standard API의 장점 {#why-using-campaign-standard-apis}

Adobe Campaign Standard은 기존 시스템을 Campaign 플랫폼과 통합하여 실제 문제를 실시간으로 해결할 수 있도록 하는 API를 제공합니다.

등록 또는 옵트아웃 페이지와 같은 공개 웹 사이트는 프로필 정보를 저장하기 위해 백엔드 시스템에 연결해야 합니다. Adobe Campaign과 같은 백엔드 시스템은 프로필 데이터를에 수집하고 이에 대해 사용자 지정 작업을 수행할 수 있는 유연성과 기능을 갖추고 있습니다.

다음은 몇 가지 예입니다.

* 잠재 고객 온라인 등록.
* 기존 고객 프로필 및 마케팅 커뮤니케이션 환경 설정 관리.
* 이벤트 기반 트랜잭션 통신 트리거 - 주문 확인, 예약 일정, 암호 재설정 등.
* 장바구니 포기 전자 메일 통신까지.

랜딩 페이지에 등록하면 고객 또는 잠재 고객이 이름과 이메일 주소를 등록할 수 있습니다. Campaign Standard이 프로필 정보 및 환경 설정을 캡처하면 사용자의 관심사에 따라 개인화된 메시지를 보낼 수 있습니다.

이 요소는 아래 요소로 빌드됩니다.

1. Campaign API 리스너를 사용하는 등록 양식입니다.

   ![대체 텍스트](assets/apis_uc1.png)

1. 확인란을 기반으로 수행할 사용자 지정 작업입니다. &quot;이메일 특별 행사&quot;를 선택하는 고객은 일반 등록 프로세스와 비교하여 선물 쿠폰이 포함된 다른 사용자 정의 메일을 받게 됩니다.

   ![대체 텍스트](assets/apis_uc2.png)

1. 프로필은 이메일의 &quot;업데이트 세부 정보&quot; 링크를 클릭한 후 세부 정보를 변경할 수 있습니다. 이렇게 하면 프로필이 &quot;프로필 및 환경 설정 세부 정보 업데이트&quot; 페이지로 이동합니다. 작업을 수행하기 위해 프로필 세부 사항(Pkey)이 Campaign 서버에 전달되고 프로필을 검색하여 나타냅니다. 프로필에서 &quot;업데이트&quot; 버튼을 클릭하면 정보가 시스템에 업데이트됩니다(PATCH 명령을 통해).

   ![대체 텍스트](assets/apis_uc3.png)

Campaign Standard API 요청을 숙지하는 데 도움이 되는 요청 컬렉션을 사용할 수 있습니다. JSON 형식의 이 컬렉션은 일반적인 사용 사례를 나타내는 미리 디자인된 API 요청을 제공합니다.

아래 단계에서는 컬렉션을 가져와 Campaign Standard 데이터베이스에서 프로필을 만드는 데 사용하는 단계별 사용 사례를 설명합니다.

>[!NOTE]
>
>이 예제에서는 Postman을 사용합니다. 그러나 좋아하는 REST 클라이언트를 자유롭게 사용할 수 있습니다.

1. [여기](https://helpx.adobe.com/content/dam/help/en/campaign/kb/working-with-acs-api/_jcr_content/main-pars/download_section/download-1/KB_postman_collection.json.zip)를 클릭하여 JSON 컬렉션을 다운로드합니다.

1. Postman을 열고 **파일** / **가져오기** 메뉴를 선택합니다.

1. 다운로드한 파일을 창으로 끌어서 놓습니다. 미리 디자인된 API 요청, 사용할 준비가 되었습니다.

   ![대체 텍스트](assets/postman_collection.png)

1. **프로필 만들기** 요청을 선택한 다음 POST 요청과 **헤더** 탭을 사용자 정보(&lt;ORGANIZATION>, &lt;API_KEY>, &lt;ACCESS_TOKEN>)로 업데이트하십시오. 이 작업에 대한 자세한 정보는 [이 섹션](setting-up-api-access.md)을 참조하십시오.

   ![대체 텍스트](assets/postman_uc1.png)

1. 새 프로필에 추가할 정보로 **본문** 탭을 입력한 다음 **보내기** 단추를 클릭하여 요청을 실행합니다.

   ![대체 텍스트](assets/postman_uc2.png)

1. 개체가 생성되면 기본 키(PKey)가 연결됩니다. 요청 응답과 다른 속성에 표시됩니다.

   ![대체 텍스트](assets/postman_uc3.png)

1. Campaign Standard 인스턴스를 열고 페이로드의 모든 정보와 함께 프로필이 생성되었는지 확인합니다.

   ![대체 텍스트](assets/postman_uc4.png)
