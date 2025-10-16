---
title: 반드시 알아야 할 사항
description: API를 사용하기 전에 반드시 읽어야 합니다.
audience: developing
content-type: reference
topic-tags: campaign-standard-apis
role: Developer
level: Experienced
badge: label="제한된 가용성" type="Informative" url="../campaign-standard-migration-home.md" tooltip="Campaign Standard 마이그레이션된 사용자로 제한됨"
exl-id: 9e2d1b59-55a5-4715-adfb-35191a9df536
source-git-commit: 11c49b273164b632bcffb7de01890c6f9d7ae9c2
workflow-type: tm+mt
source-wordcount: '383'
ht-degree: 0%

---

# 반드시 알아야 할 사항 {#must-read}

## 기술 요구 사항

* Adobe Campaign API는 서버 간 전용이어야 합니다.
* 구현하려는 사용 사례가 Adobe Campaign API에서 허용하는 규모와 일치하는 경우 항상 Adobe 기술 담당자에게 문의하십시오.
* AdobeIO 액세스를 설정하려면 특정 권한이 필요합니다. Adobe 지원 센터에 문의하여 문제를 해결하십시오.

## 권한 및 액세스

* 기본적으로 Adobe Campaign API는 관리자 컨텍스트를 사용하므로 조직 단위 및 역할은 적용되지 않습니다.
* Adobe Campaign API는 역할 컨텍스트에서 제외됩니다.
* 조직 단위 또는 역할을 사용하여 API를 구성하려면 먼저 Adobe 기술 담당자에게 문의하십시오.

## 리소스 표시

모든 API 리소스는 **JSON**&#x200B;에서 URL 확장을 사용하거나 HTTP Accept 헤더 내에서 사용할 수 있습니다.

`GET /profileAndServices/<resourceName>.json`

>[!NOTE]
>
>URL에 확장이 없으면 **json 형식은 콘텐츠 형식의 기본 형식입니다**.

<br/>

***요청 샘플***

```
-X GET https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/profile.json \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer <ACCESS_TOKEN>' \
-H 'Cache-Control: no-cache' \
-H 'X-Api-Key: <API_KEY>'
```

## 기본 키 및 URL

* URL을 직접 작성하지 마십시오. 모든 URL은 API에 의해 반환됩니다. 그러나 최상위 리소스 이름을 기반으로 URL을 작성할 수 있습니다.

* 예제를 보여 주는 자동 기본 키(PKey) 값은 다른 특정 배포에서 작동하기 위한 것이 아닙니다. Adobe Campaign API에서 생성됩니다.

* Adobe Campaign에서 생성한 자동 기본 키 값은 외부 데이터베이스 또는 웹 사이트에 저장해서는 안 됩니다. 데이터베이스 정의에 특정 키 필드를 생성하고 개발 중에 사용해야 합니다.

## 사용자 정의 키 {#custom-keys}

프로필 리소스가 사용자 지정 키 필드로 확장된 경우, 이 필드를 Adobe Campaign에서 생성한 자동 기본 키 대신 키로 사용할 수 있습니다.

`GET /.../profileAndServicesExt/profile/<customKey>`

키 값이 원본 키와 다른 경우 PATCH 작업을 사용하여 사용자 지정 키를 수정할 수 없거나 Adobe에서 제공하는 비즈니스 키 대신 자신의 비즈니스 키를 URI로 사용하는 경우 수정할 수 없습니다.

**최상위 프로필 리소스**&#x200B;에만 사용자 지정 키를 사용하십시오. URL은 API에 의해 반환되며 직접 작성해서는 안 됩니다.

<br/>

***샘플 요청***

사용자 지정 키를 사용하여 프로필에 대한 구독을 검색하려면 사용자 지정 키에 대해 GET 작업을 수행하십시오.

```
-X GET https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServicesExt/profile/<customKey> \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer <ACCESS_TOKEN>' \
-H 'Cache-Control: no-cache' \
-H 'X-Api-Key: <API_KEY>'
```

반환된 구독 URL에 대해 GET 요청을 수행합니다.

```
-X GET <SUBSCRIPTION_URL> \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer <ACCESS_TOKEN>' \
-H 'Cache-Control: no-cache' \
-H 'X-Api-Key: <API_KEY>'
```

프로필에 대한 구독 목록을 반환합니다.

```
"service": {
"PKey": "<PKEY>",
"href": "https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/service/<PKEY>",
"label": "Sport Newsletter",
"name": "SVC1",
"title": "Sport Newsletter (SVC1)"
}
```
