---
title: 쪽 매기기
description: 페이지 매김 작업을 수행하는 방법에 대해 알아봅니다.
audience: developing
content-type: reference
topic-tags: campaign-standard-apis
role: Developer
level: Experienced
badge: label="제한된 가용성" type="Informative" url="../campaign-standard-migration-home.md" tooltip="Campaign Standard 마이그레이션된 사용자로 제한됨"
exl-id: d6ebce3c-1e84-4b3b-a68d-90df4680af64
source-git-commit: 11c49b273164b632bcffb7de01890c6f9d7ae9c2
workflow-type: tm+mt
source-wordcount: '169'
ht-degree: 1%

---

# 쪽 매기기

기본적으로 25개의 리소스가 목록에 로드됩니다.

**_lineCount** 매개 변수를 사용하면 응답에 나열된 리소스 수를 제한할 수 있습니다.  그런 다음 **next** 노드를 사용하여 다음 결과를 표시할 수 있습니다.

>[!NOTE]
>
>페이지 매김 요청을 수행하려면 항상 **next** 노드에서 반환된 URL 값을 사용하십시오.
>
>**_lineStart** 요청은 계산되며 항상 **next** 노드에 반환된 URL 내에서 사용해야 합니다.

<br/>

***샘플 요청***

프로필 리소스의 레코드 1개를 표시하는 샘플 GET 요청.

```
-X GET https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/profile?_lineCount=1 \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer <ACCESS_TOKEN>' \
-H 'Cache-Control: no-cache' \
-H 'X-Api-Key: <API_KEY>'
```

페이지 매김을 수행할 **next** 노드를 사용한 요청에 대한 응답입니다.

```
{
    "content": [
        {
            "PKey": "<PKEY>",
            "firstName": "John",
            "lastName":"Doe",
            "birthDate": "1980-10-24",
            ...
        }
    ],
    "next": {
        "href": "https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/profile/email?_lineCount=10&_
        lineStart=@Qy2MRJCS67PFf8soTf4BzF7BXsq1Gbkp_e5lLj1TbE7HJKqc"
    }
    ...
}
```

기본적으로 **next** 노드는 많은 양의 데이터가 있는 테이블과 상호 작용할 때 사용할 수 없습니다. 페이지 매김을 수행하려면 호출 URL에 **_forcePagination=true** 매개 변수를 추가해야 합니다.

```
-X GET https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/profile?_forcePagination=true \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer <ACCESS_TOKEN>' \
-H 'Cache-Control: no-cache' \
-H 'X-Api-Key: <API_KEY>'
```

>[!NOTE]
>
>테이블 크기가 큰 것으로 간주되는 레코드 수는 Campaign Standard **XtkBigTableThreshold** 옵션에 정의되어 있습니다. 기본값은 100,000 레코드입니다.
