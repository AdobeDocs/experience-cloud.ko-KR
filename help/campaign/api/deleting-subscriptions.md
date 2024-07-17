---
title: 구독 삭제
description: API를 사용하여 구독을 삭제하는 방법 알아보기
role: Data Engineer
level: Experienced
badge: label="제한된 가용성" type="Informative" url="../campaign-standard-migration-home.md" tooltip="마이그레이션된 사용자 Campaign Standard으로 제한됨"
exl-id: 76e2d102-c877-41a6-af87-2f407201a572
source-git-commit: 14d8cf78192bcad7b89cc70827f5672bd6e07f4a
workflow-type: tm+mt
source-wordcount: '246'
ht-degree: 0%

---

# API로 구독 삭제 {#mdeleting-subscriptions-api}

<!--NOTE TO WRITER: There are two duplicate headings that seem to have the same content. Delete one? Rename if different?-->

## 특정 프로필에 대한 서비스 구독 삭제 {#deleting-service-subscription}

이 절차는 3단계로 구성됩니다.

1. 원하는 프로필에 대한 구독 URL을 검색합니다.
1. 구독 URL에 대한 GET 요청을 수행합니다.
1. 원하는 서비스 URL에 대해 DELETE 요청을 수행합니다.

삭제 요청이 성공하면 응답 상태는 204 콘텐츠 없음입니다.

<br/>

***샘플 요청***

아래 샘플 페이로드는 서비스에서 프로필 구독을 취소하는 방법을 보여 줍니다. 먼저 프로필을 검색하기 위한 GET 요청을 수행합니다.

```
-X GET https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/profile/<PKEY> \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer <ACCESS_TOKEN>' \
-H 'Cache-Control: no-cache' \
-H 'X-Api-Key: <API_KEY>'
```

프로필에 대한 구독 URL을 반환합니다.

```
  {
    ...
    "postalAddress":...,
    "preferredLanguage": "none",
    "subscriptions": {
      "href": "https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/profile/<PKEY>/subscriptions/"
    },
  }
```

구독 URL에 대한 GET 요청을 수행합니다.

```
-X GET https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/profile/<PKEY>/subscriptions \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer <ACCESS_TOKEN>' \
-H 'Cache-Control: no-cache' \
-H 'X-Api-Key: <API_KEY>'
```

선택한 프로필에 대한 구독 목록을 각 구독한 서비스에 대한 URL과 함께 반환합니다.

```
...
"service": {
  "PKey": "<PKEY>",
  "href": "https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/service/<PKEY>",
  "label": "Sport Newsletter",
  "name": "SVC1",
  "title": "Sport Newsletter (SVC1)"
},
...
```

원하는 서비스 URL에 대해 DELETE 요청을 수행합니다.

```
-X DELETE https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/service/<PKEY> \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer <ACCESS_TOKEN>' \
-H 'Cache-Control: no-cache' \
-H 'X-Api-Key: <API_KEY>'
```

<!-- + réponse -->

## 특정 프로필에 대한 서비스 구독 삭제

이 절차는 3단계로 구성됩니다.

1. 원하는 서비스 및 해당 구독 URL을 검색합니다.
1. 구독 URL에 대해 GET 요청을 수행하여 모든 프로필 구독을 검색합니다.
1. 원하는 프로필 구독 URL에 대해 DELETE 요청을 수행합니다.

삭제 요청이 성공하면 응답 상태는 204 콘텐츠 없음입니다.

<br/>

***샘플 요청***

서비스 레코드를 검색합니다.

```
-X GET https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/service/<PKEY> \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer <ACCESS_TOKEN>' \
-H 'Cache-Control: no-cache' \
-H 'X-Api-Key: <API_KEY>'
```

서비스에 대한 구독 URL을 반환합니다.

```
{
  ...
  "messageType": "email",
  "mode": "newsletter",
  "name": "SVC3",
  "subScenarioEventType": "subscriptionEvent",
  "subscriptions": {
    "href": "https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/service/<PKEY>/subscriptions/"
  },
  "targetResource": "profile",
  ...
},
```

구독 URL에 대한 GET 요청을 수행합니다.

```
-X GET https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/service/<PKEY>/subscriptions \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer <ACCESS_TOKEN>' \
-H 'Cache-Control: no-cache' \
-H 'X-Api-Key: <API_KEY>'
```

각 프로필 구독에 대한 URL(href)과 함께 선택한 서비스에 대한 구독 목록을 반환합니다.

```
{
  "PKey": "<PKEY>",
  "created": "2019-03-26 08:58:04.764Z",
  "email": "",
  "expirationDate": "",
  "href": "https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/service/<PKEY>/subscriptions/<PKEY>",
  "metadata": "subscriptionRcp",
  "service": ...,
  "serviceName": "SVC3",
  "subscriber": ...,
  ...
}
```

원하는 프로필 구독 URL에 대해 DELETE 요청을 수행합니다.

```
-X DELETE https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/service/<PKEY>/subscriptions/<PKEY> \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer <ACCESS_TOKEN>' \
-H 'Cache-Control: no-cache' \
-H 'X-Api-Key: <API_KEY>'
```

<!-- + réponse -->
