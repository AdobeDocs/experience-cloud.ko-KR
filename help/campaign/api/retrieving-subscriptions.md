---
title: 구독 검색
description: API로 구독을 검색하는 방법 알아보기
role: Developer
level: Experienced
badge: label="제한된 가용성" type="Informative" url="../campaign-standard-migration-home.md" tooltip="Campaign Standard 마이그레이션된 사용자로 제한됨"
exl-id: 6d935074-3196-45c5-97cd-ccb7c80bbba8
source-git-commit: 11c49b273164b632bcffb7de01890c6f9d7ae9c2
workflow-type: tm+mt
source-wordcount: '207'
ht-degree: 0%

---

# API로 구독 검색 {#retrieving-subscriptions-api}

## 서비스를 구독한 프로필 검색

이 절차는 두 단계로 구성됩니다.

1. 원하는 서비스에 대한 구독 URL을 검색합니다.
1. 구독 URL에 대해 GET 요청을 수행합니다. 서비스에 대한 구독 목록을 각 관련 프로필과 함께 반환합니다.

>[!CAUTION]
>
>REST API는 사용할 URL이 포함된 &quot;href&quot; 속성을 반환합니다. <b>항상 응답에 포함된 URL을 사용하여 후속 API를 요청하십시오</b>.

<br/>

***샘플 요청***

GET 요청을 수행하여 서비스를 검색합니다.

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
    "name": "SVC1",
    "subscriptions": {
                "href": "https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/service/<PKEY>/subscriptions/"
    },
    ...
  },
```

구독 URL에 대해 GET 요청을 수행합니다.

```
-X GET https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/service/<PKEY>/subscriptions \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer <ACCESS_TOKEN>' \
-H 'Cache-Control: no-cache' \
-H 'X-Api-Key: <API_KEY>'
```

서비스에 대한 구독 목록이 연결된 각 프로필과 함께 표시됩니다.

```
  {
    ...
    "service": ...,
    "serviceName": "SVC3",
    "subscriber": {
        "PKey": "<PKEY>",
        "email": "",
        "firstName": "John",
        "href": "https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/profile/<PKEY>",
        "lastName": "Doe",
    },
  }
```

## 프로필이 구독한 서비스 검색

이 절차는 두 단계로 구성됩니다.

1. 주어진 프로필에 대한 구독 URL을 검색합니다.
1. URL에서 GET 요청을 수행합니다. 프로필에 대한 구독 목록과 각 관련 서비스를 반환합니다.

<br/>

***샘플 요청***

GET 요청을 수행하여 프로필을 검색합니다.

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
    ...
  }
```

구독 URL에 대해 GET 요청을 수행합니다.

```
-X GET https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/profile/<PKEY>/subscriptions \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer <ACCESS_TOKEN>' \
-H 'Cache-Control: no-cache' \
-H 'X-Api-Key: <API_KEY>'
```

프로필이 구독한 서비스 목록을 반환합니다.

```
  {
    ...
    "PKey": "<PKEY>",
    "created": "2017-03-03 10:54:00.363Z",
    "service": {
      "PKey": "<PKEY>",
      "href": "https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/service/<PKEY>",
      "label": "Sport Newsletter",
      "name": "SVC1",
      "title": "Sport Newsletter (SVC1)"
    },
    ...
  }
```
