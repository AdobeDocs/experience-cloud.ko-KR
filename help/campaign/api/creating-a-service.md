---
title: API를 사용하여 서비스 만들기
description: API를 사용하여 서비스를 만드는 방법을 알아봅니다
role: Data Engineer
level: Experienced
badge: label="제한된 가용성" type="Informative" url="../campaign-standard-migration-home.md" tooltip="마이그레이션된 사용자 Campaign Standard으로 제한됨"
exl-id: 91bbce9e-a618-4be2-840b-c7d021271f4e
source-git-commit: 14d8cf78192bcad7b89cc70827f5672bd6e07f4a
workflow-type: tm+mt
source-wordcount: '86'
ht-degree: 0%

---

# API를 사용하여 서비스 만들기{#creating-a-service-api}

서비스 리소스에서 **POST** 요청을 사용하여 서비스를 만듭니다.

특정 특성을 사용하여 서비스를 만들려면 해당 특성을 페이로드에 추가하십시오. 그렇지 않으면 기본 서비스와 함께 새 서비스가 만들어집니다.

<br/>

***샘플 요청***

특정 특성이 있는 서비스를 만들기 위한 샘플 POST 요청입니다.

```
-X POST https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/service/ \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer <ACCESS_TOKEN>' \
-H 'Cache-Control: no-cache' \
-H 'X-Api-Key: <API_KEY>'
-i
-d {
-d "label": "My newsletter",
-d "messageType": "email",
-d "name": "email_newsletter",
-d "start": "2019-10-06"
-d }
```

업데이트된 속성으로 새로 생성된 서비스를 반환합니다.

```
{
    "PKey": "<PKEY>",
    "builtIn": false,
    "created": "2019-09-26 12:00:37.005Z",
    "href": "https://mc.adobe.io/<ORGANIZATION>/profileAndServices/service/@NLscZuVHxdVu9rPftvrMWFfR1zRIxQGswSOmGLrK09JTF_iWhB0JCUHEndA_vvy__k9mzOYa5NVkcWDcrK8qGh0wygahX9kRcD44kiWWSEceShn3",
    "label": "My newsletter",
    ...
}
```
