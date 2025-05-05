---
title: 엔드포인트
description: API 엔드포인트에 대해 자세히 알아보십시오.
audience: developing
content-type: reference
topic-tags: campaign-standard-apis
role: Data Engineer
level: Experienced
badge: label="제한된 가용성" type="Informative" url="../campaign-standard-migration-home.md" tooltip="마이그레이션된 사용자 Campaign Standard으로 제한됨"
exl-id: 9f6d3da6-374d-47f5-bc8f-b31b19cbb5ca
source-git-commit: 14d8cf78192bcad7b89cc70827f5672bd6e07f4a
workflow-type: tm+mt
source-wordcount: '191'
ht-degree: 9%

---

# 엔드포인트 {#endpoints}

Adobe Campaign REST API에 사용할 수 있는 엔드포인트:

* **/profileAndServices**: 기본 제공 필드와 상호 작용합니다. 확장 필드는 이 끝점으로 액세스할 수 없습니다.
* **/profileAndServicesExt**: 프로필 또는 서비스 사용자 지정 리소스 확장 중에 추가된 사용자 지정 필드와 상호 작용합니다. 사용자 지정 리소스에 대한 자세한 정보는 [이 섹션](custom-resources.md)을 참조하세요.
* **/&lt;transactionalAPI>**: 트랜잭션 메시지 API와 상호 작용합니다(트랜잭션 메시지 API 끝점의 이름은 인스턴스 구성에 따라 다름). 이 작업에 대한 자세한 정보는 [이 섹션](managing-transactional-messages.md)을 참조하십시오.
* **/workflow/execution**: 워크플로우와 상호 작용합니다. 이 작업에 대한 자세한 정보는 [이 섹션](controlling-a-workflow.md)을 참조하십시오.

기본적으로 **profileAndServices** 및 **profileAndServicesExt** API에 사용할 수 있는 기본 리소스는 다음과 같습니다.

* **/profile**: Campaign 데이터베이스의 프로필과 상호 작용합니다. 서비스에 프로필을 추가하려면 **/service** 끝점을 사용하세요. Campaign의 프로필에 대한 자세한 내용은 [Campaign 설명서](https://helpx.adobe.com/kr/campaign/standard/audiences/using/about-profiles.html)를 참조하세요.
* **/service**: 구독 서비스를 관리합니다. Campaign의 서비스에 대한 자세한 내용은 [Campaign 설명서](https://helpx.adobe.com/kr/campaign/standard/audiences/using/creating-a-service.html)를 참조하세요.

>[!NOTE]
>
>확장 또는 생성된 다른 모든 리소스는 **ProfileAndServicesExt** API를 통해서만 사용할 수 있습니다. 액세스하려면 **Profile** 리소스에 연결되어 있어야 합니다.
