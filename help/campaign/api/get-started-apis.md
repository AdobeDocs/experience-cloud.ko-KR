---
title: Campaign REST API 시작
description: Campaign과 다양한 기술의 통합을 통해 고유한 에코시스템을 구축할 수 있습니다.
audience: developing
content-type: reference
topic-tags: campaign-standard-apis
role: Data Engineer
level: Experienced
badge: label="제한된 가용성" type="Informative" url="../campaign-standard-migration-home.md" tooltip="마이그레이션된 사용자 Campaign Standard으로 제한됨"
exl-id: c6968252-a012-4029-bbb8-66f4f693e99b
source-git-commit: 14d8cf78192bcad7b89cc70827f5672bd6e07f4a
workflow-type: tm+mt
source-wordcount: '231'
ht-degree: 48%

---

# Campaign REST API 시작 {#get-started-apis}

>[!CAUTION]
>
>이 설명서는 Campaign v8로 마이그레이션하는 Adobe Campaign Standard 고객을 대상으로 합니다.
>
>API 호출을 수행하기 전에 라이선스 계약에 해당하는 크기 제한 사항을 확인하십시오. 자세한 정보는 이 [페이지](https://helpx.adobe.com/kr/legal/product-descriptions/campaign-standard.html#ITInfrastructureResourcesbyActiveProfilesTiers)를 참조하십시오.

Campaign REST API는 사용자가 사용하는 기술 패널과 Adobe Campaign을 연결하여 Adobe Campaign에 대한 **통합을 만들고** **고유한 에코시스템을 구축**&#x200B;할 수 있도록 해줍니다.

Adobe Campaign REST API를 사용하면 다음 기능에 액세스할 수 있습니다.

<table><tr>
 <td valign="top"><a href="retrieving-profiles.md"><img width="60px" alt="조건" src="assets/icon_profile.svg"/></a><p><a href="retrieving-profiles.md">프로필</a></p></td>
<td valign="top"><a href="creating-a-service.md"><img width="60px" alt="조건" src="assets/icon_services.svg"/></a><p><a href="creating-a-service.md">서비스 및 구독</a></p></td>
<td valign="top"><a href="interacting-with-custom-resources.md"><img width="60px" alt="조건" src="assets/icon_customresources.svg"/></a><p><a href="interacting-with-custom-resources.md">사용자 정의 리소스</a></p></td>
<td valign="top"><a href="controlling-a-workflow.md"><img width="60px" alt="조건" src="assets/icon_workflows.svg"/></a><p><a href="controlling-a-workflow.md">워크플로</a></p></td>
</tr></table>

Campaign REST API를 사용하려면 Adobe I/O 계정이 필요합니다. 이는 API 기능을 앞으로 나아가고 검색하기 위한 필수 첫 단계입니다.
이 작업에 대한 자세한 정보는 [이 섹션](setting-up-api-access.md)을 참조하십시오.

Adobe가 제공하는 API는 REST 인터페이스 및 JSON 페이로드와 함께 **표준 개념**&#x200B;을 사용합니다.

모든 엔드포인트는 API, 전체 API 참조, 코드 예제 및 빠른 시작 안내서를 조작할 때 알아야 하는 일반적인 개념과 함께 이 설명서에서 광범위하게 설명됩니다. 모든 예는 Postman과 함께 작동하지만 좋아하는 REST 클라이언트를 자유롭게 사용할 수 있습니다.

누락되었거나 잘못된 것 같은 경우에는 [커뮤니티](https://experienceleaguecommunities.adobe.com/t5/adobe-campaign-standard/ct-p/adobe-campaign-standard-community)에 문의하십시오.
