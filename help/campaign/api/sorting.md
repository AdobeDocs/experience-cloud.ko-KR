---
title: 정렬
description: 정렬 작업을 수행하는 방법에 대해 자세히 알아보기
audience: developing
content-type: reference
topic-tags: campaign-standard-apis
role: Data Engineer
level: Experienced
badge: label="제한된 가용성" type="Informative" url="../campaign-standard-migration-home.md" tooltip="마이그레이션된 사용자 Campaign Standard으로 제한됨"
source-git-commit: 84b72258789ba61016deb813e93bdca0ea142712
workflow-type: tm+mt
source-wordcount: '98'
ht-degree: 10%

---

# 정렬

정렬은 기본적으로 오름차순으로 사용할 수 있습니다. 내림차순으로 정렬하려면 다음을 추가합니다. **%20desc** (으)로 **순서(_O)** 매개 변수 값입니다.

필드를 정렬할 수 있는지 확인하려면 리소스 메타데이터에 &quot;정렬 가능한&quot; 매개 변수를 확인하십시오. 이 작업에 대한 자세한 정보는 [이 섹션](metadata-mechanism.md)을 참조하십시오.

<br/>

***샘플 요청***

* 알파벳순으로 정렬된 데이터베이스에서 이메일을 검색하기 위한 샘플 GET 요청입니다.

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

* 데이터베이스에서 알파벳 내림차순으로 이메일을 검색하기 위한 샘플 GET 요청입니다.

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
