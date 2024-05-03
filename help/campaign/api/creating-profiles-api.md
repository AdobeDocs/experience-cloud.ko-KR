---
title: API를 사용하여 프로필 만들기
description: API를 사용하여 프로필을 만드는 방법에 대해 자세히 알아보십시오.
audience: developing
content-type: reference
topic-tags: campaign-standard-apis
role: Data Engineer
level: Experienced
badge: label="제한된 가용성" type="Informative" url="../campaign-standard-migration-home.md" tooltip="마이그레이션된 사용자 Campaign Standard으로 제한됨"
source-git-commit: 84b72258789ba61016deb813e93bdca0ea142712
workflow-type: tm+mt
source-wordcount: '110'
ht-degree: 0%

---

# API를 사용하여 프로필 만들기 {#creating-profiles-api}

프로필 만들기는 **POST** 프로필 리소스에 대한 요청입니다.

>[!CAUTION]
>
>을(를) 연결하려는 경우 <b>orgUnit</b> 작성된 프로필로, 이 필드로 프로필 리소스를 확장해야 하며, 확장을 게시한 후에서 POST 요청을 수행합니다. <b>ProfileAndServicesExt</b> 엔드포인트.
>
>프로필의 리소스 확장에 대한 자세한 내용은 <a href="https://helpx.adobe.com/campaign/standard/administration/using/organizational-units.html#partitioning-profiles">Campaign 설명서</a>.

<br/>

***샘플 요청***

이메일 &quot;john.doe@mail.com&quot;을 사용하여 프로필을 만드는 샘플 POST 요청.

```
-X POST https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/profile \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer <ACCESS_TOKEN>' \
-H 'Cache-Control: no-cache' \
-H 'X-Api-Key: <API_KEY>' \
-i
-d '{"email":"john.doe@mail.com"}'
```

&quot;john.doe@mail.com&quot; 이메일 주소를 사용하여 새로 만든 프로필을 반환합니다.

```
{
    "PKey": "<PKEY>",
    "firstName": "John",
    "lastName":"Doe",
    "birthDate": "1980-10-24",
    "email": "john.doe@mail.com",
    ...
}
```
