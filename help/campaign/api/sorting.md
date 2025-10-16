---
title: 정렬
description: 정렬 작업을 수행하는 방법에 대해 자세히 알아보기
audience: developing
content-type: reference
topic-tags: campaign-standard-apis
role: Developer
level: Experienced
badge: label="제한된 가용성" type="Informative" url="../campaign-standard-migration-home.md" tooltip="Campaign Standard 마이그레이션된 사용자로 제한됨"
exl-id: 7db25b8d-a6f1-4151-bf37-c47e9991ae48
source-git-commit: 11c49b273164b632bcffb7de01890c6f9d7ae9c2
workflow-type: tm+mt
source-wordcount: '98'
ht-degree: 10%

---

# 정렬

정렬은 기본적으로 오름차순으로 사용할 수 있습니다. 내림차순으로 정렬하려면 **%20desc**&#x200B;을(를) **_order** 매개 변수 값에 추가하십시오.

필드를 정렬할 수 있는지 확인하려면 리소스 메타데이터에 &quot;정렬 가능한&quot; 매개 변수를 확인하십시오. 이 작업에 대한 자세한 정보는 [이 섹션](metadata-mechanism.md)을 참조하십시오.

<br/>

***샘플 요청***

* 알파벳순으로 정렬된 데이터베이스에서 이메일을 검색하기 위한 샘플 GET 요청.

  ```
  -X GET https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/profile/email?_order=email \
  -H 'Content-Type: application/json' \
  -H 'Authorization: Bearer <ACCESS_TOKEN>' \
  -H 'Cache-Control: no-cache' \
  -H 'X-Api-Key: <API_KEY>'
  ```

  요청에 대한 응답입니다.

  ```
  {
  "content": [
      "adam@email.com",
      "allison.durance@example.com",
      "amy.dakota@mail.com",
      "andrea.johnson@mail.com",
      ...
  ]
  ...
  }
  ```

* 데이터베이스에서 이메일을 내림차순으로 검색하기 위한 샘플 GET 요청입니다.

  ```
  -X GET https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/profile/email?_order=email%20desc \
  -H 'Content-Type: application/json' \
  -H 'Authorization: Bearer <ACCESS_TOKEN>' \
  -H 'Cache-Control: no-cache' \
  -H 'X-Api-Key: <API_KEY>'
  ```

  요청에 대한 응답입니다.

  ```
  {
  "content": [
      "tombinder@example.com",
      "tombinder@example.com",
      "timross@example.com",
      "john.smith@example.com",
      ...
  ]
  }
  ```
