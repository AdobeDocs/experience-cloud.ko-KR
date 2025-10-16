---
title: 트랜잭션 메시지 관리
description: API를 사용하여 트랜잭션 메시지를 관리하는 방법에 대해 알아봅니다.
audience: developing
content-type: reference
topic-tags: campaign-standard-apis
role: Developer
level: Experienced
badge: label="제한된 가용성" type="Informative" url="../campaign-standard-migration-home.md" tooltip="Campaign Standard 마이그레이션된 사용자로 제한됨"
exl-id: 00d39438-a232-49f1-ae5e-1e98c73397e3
source-git-commit: 11c49b273164b632bcffb7de01890c6f9d7ae9c2
workflow-type: tm+mt
source-wordcount: '752'
ht-degree: 1%

---

# 트랜잭션 메시지 관리 {#managing-transactional-messages}

>[!AVAILABILITY]
>
>현재 REST API를 사용하는 트랜잭션 메시지는 이메일 및 SMS 채널에서 사용할 수 있습니다. 트랜잭션 이벤트에만 사용할 수 있습니다(데이터 보강은 Adobe Campaign V8이 작동하는 방식과 유사한 페이로드만 통해 사용 가능).

트랜잭션 이벤트를 만들고 게시한 후에는 이 이벤트의 트리거를 웹 사이트에 통합해야 합니다.

예를 들어 고객 중 한 명이 장바구니에 있는 제품을 구매하기 전에 웹 사이트를 떠날 때마다 &quot;장바구니 포기&quot; 이벤트를 트리거하려는 경우가 있습니다. 이렇게 하려면 웹 개발자는 REST 트랜잭션 메시지 API를 사용해야 합니다.

1. [트랜잭션 이벤트의 전송](#sending-a-transactional-event)을(를) 트리거하는 POST 메서드에 따라 요청을 보냅니다.
1. POST 요청에 대한 응답에는 GET 요청을 통해 하나 이상의 요청을 보낼 수 있는 기본 키가 포함되어 있습니다. 그러면 [이벤트 상태](#transactional-event-status)를 가져올 수 있습니다.

## 트랜잭션 이벤트 보내기 {#sending-a-transactional-event}

트랜잭션 이벤트는 다음 URL 구조의 POST 요청을 통해 전송됩니다.

```
POST https://mc.adobe.io/<ORGANIZATION>/campaign/<transactionalAPI>/<eventID>
```

* **&lt;조직>**: 개인 조직 ID. [이 섹션](must-read.md)을 참조하십시오.

* **&lt;transactionalAPI>**: 트랜잭션 메시지 API 끝점입니다.

  트랜잭션 메시지 API 끝점의 이름은 인스턴스 구성에 따라 다릅니다. 값 &quot;mc&quot; 다음에 개인 조직 ID가 오면 해당합니다. 조직 ID가 &quot;geometrixx&quot;인 Geometrixx 회사의 예를 살펴보겠습니다. 이 경우 POST 요청은 다음과 같습니다.

  `POST https://mc.adobe.io/geometrixx/campaign/mcgeometrixx/<eventID>`

* **&lt;eventID>**: 보낼 이벤트 유형입니다. 이 ID는 이벤트 구성을 만들 때 생성됩니다

### POST 요청 헤더

요청에는 &quot;Content-Type: application/json&quot; 헤더가 포함되어야 합니다.

문자 집합을 추가해야 합니다(예: **utf-8**). 이 값은 사용 중인 REST 응용 프로그램에 따라 다릅니다.

```
-X POST \
-H 'Authorization: Bearer <ACCESS_TOKEN>' \
-H 'Cache-Control: no-cache' \
-H 'X-Api-Key: <API_KEY>' \
-H 'Content-Type: application/json;charset=utf-8' \
-H 'Content-Length:79' \
```

### POST 요청 본문

이벤트 데이터는 JSON POST 본문 내에 포함되어 있습니다. 이벤트 구조는 해당 정의에 따라 다릅니다.

이벤트에 연결된 트랜잭션 메시지 전송을 관리하기 위해 다음과 같은 선택적 매개 변수를 이벤트 콘텐츠에 추가할 수 있습니다.

* **만료**(선택 사항): 이 날짜 이후에 트랜잭션 이벤트 전송이 취소됩니다.
* **예약됨**(선택 사항): 이 날짜부터 트랜잭션 이벤트가 처리되고 트랜잭션 메시지가 전송됩니다.

>[!NOTE]
>
>만료 및 예약됨 매개 변수의 값은 ISO 8601 형식을 따릅니다. ISO 8601은 날짜와 시간을 구분하기 위해 대문자 &quot;T&quot;의 사용을 지정합니다. 그러나 가독성을 높이기 위해 입력 또는 출력에서 제거할 수 있습니다.

### 통신 채널 매개 변수

사용할 채널에 따라 페이로드에는 아래 매개 변수가 포함되어야 합니다.

* 이메일 채널: &quot;mobilePhone&quot;
* SMS 채널: &quot;email&quot;

페이로드에 &quot;mobilePhone&quot;만 포함된 경우 SMS 통신 채널이 트리거됩니다. 페이로드에 &quot;이메일&quot;만 포함된 경우 이메일 통신 채널이 트리거됩니다.

아래 예제는 SMS 통신이 트리거되는 페이로드를 보여 줍니다.

```
curl --location 'https://mc.adobe.io/<ORGANIZATION>/campaign/mcAdobe/EVTcartAbandonment' \
--header 'Authorization: Bearer <ACCESS_TOKEN>' \
--header 'Cache-Control: no-cache' \
--header 'X-Api-Key: <API_KEY>' \
--header 'Content-Type: application/json;charset=utf-8' \
--header 'Content-Length: 79' \
--data '
{
  "mobilePhone":"+9999999999",
  "scheduled":"2017-12-01 08:00:00.768Z",
  "expiration":"2017-12-31 08:00:00.768Z",
  "ctx":
  {
    "cartAmount": "$ 125",
    "lastProduct": "Leather motorbike jacket",
    "firstName": "Jack"
  }
}'
```

페이로드에 &quot;email&quot;과 &quot;mobilePhone&quot;이 모두 포함된 경우 기본 통신 방법은 이메일이 됩니다. 두 필드가 모두 있을 때 SMS를 보내려면 &quot;wishedChannel&quot; 매개 변수를 사용하여 페이로드에 명시적으로 지정해야 합니다.

### POST 요청에 대한 응답

POST 응답은 트랜잭션 이벤트를 만든 시점의 상태를 반환합니다. 현재 상태(이벤트 데이터, 이벤트 상태...)를 검색하려면 GET 요청의 POST 응답에서 반환되는 기본 키를 사용하십시오.

`GET https://mc.adobe.io/<ORGANIZATION>/campaign/<transactionalAPI>/<eventID>/`

<br/>

***샘플 요청***

이벤트를 전송하기 위한 POST 요청.

```
-X POST https://mc.adobe.io/<ORGANIZATION>/campaign/mcAdobe/EVTcartAbandonment \
-H 'Authorization: Bearer <ACCESS_TOKEN>' \
-H 'Cache-Control: no-cache' \
-H 'X-Api-Key: <API_KEY>' \
-H 'Content-Type: application/json;charset=utf-8' \
-H 'Content-Length:79'

{
  "
  
  
  ":"test@example.com",
  "scheduled":"2017-12-01 08:00:00.768Z",
  "expiration":"2017-12-31 08:00:00.768Z",
  "ctx":
  {
    "cartAmount": "$ 125",
    "lastProduct": "Leather motorbike jacket",
    "firstName": "Jack"
  }
}
```

POST 요청에 대한 응답입니다.

```
{
  "PKey":"<PKEY>",
  "ctx":
  {
    "cartAmount": "",
    "lastProduct": "",
    "firstName": ""
  }
  "email":"",
  "scheduled":"2017-12-01 08:00:00.768Z",
  "expiration":"2017-12-31 08:00:00.768Z",
  "href": "mcAdobe/EVTcartAbandonment/<PKEY>",
  "serverUrl":" https://myserver.com ",
  "status":"pending",
  "type":""
}
```

### 트랜잭션 이벤트 상태 {#transactional-event-status}

응답에서 &quot;상태&quot; 필드를 사용하면 이벤트 처리 여부를 알 수 있습니다.

* **보류 중**: 이벤트가 보류 중입니다. 방금 트리거되면 이벤트가 이 상태로 전환됩니다.
* **처리**: 이벤트가 게재를 보류 중입니다. 메시지로 변환되고 메시지를 보내는 중입니다.
* **일시 중지됨**: 이벤트 프로세스가 일시 중지되고 있습니다. 더 이상 처리되지 않고 Adobe Campaign 데이터베이스의 큐에 보관됩니다.
* **처리됨**: 이벤트가 처리되었으며 메시지를 성공적으로 보냈습니다.
* **무시됨**: 일반적으로 주소가 격리된 경우 게재가 이벤트를 무시했습니다.
* **deliveryFailed**: 이벤트를 처리하는 동안 게재 오류가 발생했습니다.
* **routingFailed**: 라우팅 단계가 실패했습니다. 지정된 이벤트 유형을 찾을 수 없는 경우 이러한 문제가 발생할 수 있습니다.
* **tooOld**: 이벤트를 처리하기 전에 이벤트가 만료되었습니다. 이 문제는 다양한 이유로 발생할 수 있습니다. 예를 들어 전송이 여러 번 실패하거나(이벤트가 더 이상 최신 상태가 아님) 서버가 오버로드된 후 더 이상 이벤트를 처리할 수 없는 경우입니다.
