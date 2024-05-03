---
title: 사용자 정의 리소스
description: API를 통한 사용자 지정 리소스 관리에 대해 자세히 알아보기/
audience: developing
content-type: reference
topic-tags: campaign-standard-apis
role: Data Engineer
level: Experienced
badge: label="제한된 가용성" type="Informative" url="../campaign-standard-migration-home.md" tooltip="마이그레이션된 사용자 Campaign Standard으로 제한됨"
source-git-commit: 84b72258789ba61016deb813e93bdca0ea142712
workflow-type: tm+mt
source-wordcount: '182'
ht-degree: 2%

---

# 사용자 정의 리소스 {#custom-resources}

Adobe Campaign에는 다양한 리소스를 통해 데이터를 정의하는 데이터 모델이 사전 정의되어 있습니다. 리소스를 확장하여 제공되는 데이터 모델을 보강하여 구매 또는 제품 테이블과 같은 사용자 지정 필드 또는 사용자 지정 테이블을 추가할 수 있습니다.

사용자 지정 리소스는 API를 통해 **/profileAndServicesExt** 끝점 및 사용자 지정 리소스 이름입니다.

`https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServicesExt/<resourceName>/`

>[!NOTE]
>
>기본 제공 리소스가 아닌 리소스의 경우 항상 <b>&quot;cus&quot;</b> 리소스 이름 앞에 접두사를 추가합니다.

사용자 지정 리소스는 프로필 테이블에 연결되어 있는 한 모든 작업을 수행할 수 있습니다. 예를 들어 아래 표 구조를 고려해 보겠습니다.

![대체 텍스트](assets/cusresources.png)

이 경우 의 모든 리소스는 **거래**, **거래 세부 정보** 및 **제품** 테이블이 연결된 경우에만 사용할 수 있습니다. **프로필** 테이블.

<br/>

***샘플 요청***

확장된 profileAndServicesExt 리소스에 액세스하기 위한 샘플 GET 요청입니다.

```
-X GET https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServicesExt/\
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer <ACCESS_TOKEN>' \
-H 'Cache-Control: no-cache' \
-H 'X-Api-Key: <API_KEY>' \
```

연결된 모든 사용자 지정 리소스 목록을 반환합니다. 그런 다음 리소스 URL을 사용하여 이 설명서에 설명된 API 작업을 수행할 수 있습니다.

```
{
"apiName": "resourceType",
"cusProduct": {
        "content": ...,
        "data": "/profileAndServicesExt/cusProduct/",
        "help": "Product",
        "href": "https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServicesExt/cusProduct/metadata",
        "name": "cusProduct",
        "type": "collection"
    },
"cusTransaction": {
        "content": ...,
        "data": "/profileAndServicesExt/cusTransaction/",
        "help": "Product",
        "href": "https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServicesExt/cusTransaction/metadata",
        "name": "cusProduct",
        "type": "collection"
    },
    ...
}
```
