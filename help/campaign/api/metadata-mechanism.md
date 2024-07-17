---
title: 메타데이터 메커니즘
description: 메타데이터 메커니즘에 대해 자세히 알아봅니다.
audience: developing
content-type: reference
topic-tags: campaign-standard-apis
role: Data Engineer
level: Experienced
badge: label="제한된 가용성" type="Informative" url="../campaign-standard-migration-home.md" tooltip="마이그레이션된 사용자 Campaign Standard으로 제한됨"
exl-id: 58ec0999-b28a-4198-8d57-729b074c6a6d
source-git-commit: 14d8cf78192bcad7b89cc70827f5672bd6e07f4a
workflow-type: tm+mt
source-wordcount: '236'
ht-degree: 1%

---

# 메타데이터 메커니즘 {#metadata-mechanism}

GET 요청에서 **resourceType**&#x200B;을(를) 사용하여 리소스 메타데이터를 검색할 수 있습니다.

`GET /profileAndServices/resourceType/<resourceName>`

응답은 리소스의 기본 메타데이터를 반환합니다(다른 모든 필드는 설명적이거나 내부적입니다).

* **Content** 노드가 리소스의 필드를 반환합니다. **content** 노드의 각 필드에 대해 다음 필드를 찾을 수 있습니다.

   * &quot;apiName&quot;: API에 사용되는 특성의 이름입니다.
   * &quot;type&quot;: 상위 수준 유형 정의(문자열, 숫자, 링크, 컬렉션, 열거형...)입니다.
   * &quot;dataPolicy&quot;: 필드 값은 지정된 정책 규칙을 따라야 합니다. 예를 들어 dataPolicy 규칙이 &quot;email&quot;로 설정된 경우 값은 유효한 이메일이어야 합니다. PATCH 또는 POST 중에 dataPolicy는 값을 확인하거나 값을 수정하여 변환할 수 있습니다(예: smartCase).
   * &quot;category&quot;: 쿼리 편집기에 있는 필드의 범주를 제공합니다.
   * &quot;resType&quot;: 기술 유형입니다.

     type이 &quot;link&quot; 또는 &quot;collection&quot; 값으로 완료된 경우 resTarget 값은 링크가 타깃팅한 리소스의 이름입니다.
&quot;type&quot;이 &quot;enumeration&quot; 값으로 완료되면 &quot;values&quot; 필드가 추가되고 각 열거형 값은 **values** 노드에 자세히 표시됩니다.

* **필터** 노드는 연결된 필터를 검색할 URL을 반환합니다. 필터에 대한 자세한 내용은 [이 섹션](filtering.md) 섹션을 참조하십시오.

<!-- créer une section au même niveau sur les liens -->
<!-- dans l'exemple: birthdate, email +  mettre 2 liens : un de type 1-1 , 1-N
si on prend l'exemple de l'org unit, on aura un bon exemple lien -->
<!-- plus reparler du node Data -->

<br/>

***샘플 요청***

리소스에 대한 GET 요청을 수행합니다.

```
-X GET https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/resourceType/profile \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer <ACCESS_TOKEN>' \
-H 'Cache-Control: no-cache' \
-H 'X-Api-Key: <API_KEY>'
```

프로필 리소스에 대한 전체 설명을 반환합니다.

```
{
...
"content": {
  "email": {...},
    ...
    },
"data": "/profileAndServices/profile/",
"filters": {
        "href": "https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/resourceType/<PKEY>"
    },
"help": "Identified profiles",
"href": "https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/profile/metadata",
"label": "Profiles",
"mandatory": false,
"name": "profile",
"pkgStatus": "never",
"readOnly": false,
"schema": "nms:recipient",
"type": "item"
}
```
