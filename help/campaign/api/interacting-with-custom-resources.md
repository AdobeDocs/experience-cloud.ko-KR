---
title: 사용자 지정 리소스와 상호 작용
description: API를 통한 사용자 지정 리소스 관리에 대해 자세히 알아보기/
audience: developing
content-type: reference
topic-tags: campaign-standard-apis
role: Data Engineer
level: Experienced
badge: label="제한된 가용성" type="Informative" url="../campaign-standard-migration-home.md" tooltip="마이그레이션된 사용자 Campaign Standard으로 제한됨"
exl-id: 19bfeecb-da60-479c-a929-0cfb72ef59e3
source-git-commit: 14d8cf78192bcad7b89cc70827f5672bd6e07f4a
workflow-type: tm+mt
source-wordcount: '155'
ht-degree: 0%

---

# 사용자 지정 리소스와 상호 작용 {#interacting-with-custom-resources}

**/customResources** 끝점을 사용하면 REST의 Campaign 사용자 지정 리소스를 표시할 수 있습니다. 이 API를 기반으로 사용자 지정 엔티티와 외부 엔드포인트 간의 통합을 사용할 수 있습니다.

/customResources 끝점의 동작은 /profileAndServices 끝점과 동일합니다.

이 API 내에 노출되는 사용자 지정 리소스는 다음과 같습니다.

* /profileAndServicesExt 아래에 노출되지 않은 모든 엔터티
* 프로필에 연결되어 있지 않은 모든 엔티티와 이러한 엔티티의 경우 1차 하위 구성요소 및 손자
* 기본적으로 연결되어 있지 않은 모든 엔티티와 그 자식 및 손자

>[!NOTE]
>/profileAndServicesExt에서 사용할 수 있는 사용자 지정 리소스는 /customResources API에 노출되지 않습니다.


다음은 사용자 지정 리소스에서 메타데이터를 검색하는 예입니다.

```
GET /customResources/resourceType/<customResourceName>
```

생성, 업데이트 또는 삭제를 수행하려면 GET, POST, PATCH, DELETE이 사용됩니다.

```
POST /customResources/<customResourceName>
```
