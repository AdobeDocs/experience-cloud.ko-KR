---
title: 브랜딩
description: 브랜딩 ID를 관리하는 데 사용할 수 있는 모든 도구를 살펴봅니다
audience: administration
context-tags: branding,overview;branding,main
role: Admin
level: Experienced
badge: label="제한된 가용성" type="Informative" url="../campaign-standard-migration-home.md" tooltip="마이그레이션된 사용자 Campaign Standard으로 제한됨"
source-git-commit: 51abadc86b97097d13824651d8c50d4ddd014a51
workflow-type: tm+mt
source-wordcount: '324'
ht-degree: 18%

---

# 브랜딩 시작 {#branding-gs}

>[!IMPORTANT]
>
>최종 사용자가 브랜드를 만들거나 수정할 수 없습니다. 이러한 작업은 Adobe Campaign 기술 관리자가 수행해야 합니다. 요청이 있으면 Adobe 고객 지원 센터에 문의하십시오.

모든 회사에는 시각적 요소와 기술적 세부 사항을 정의하는 브랜드 가이드라인이 있습니다. Adobe Campaign은 이러한 지침을 중앙에서 관리하는 데 도움이 되므로 이메일의 로고부터 캠페인에 사용된 URL 및 도메인에 이르기까지 모든 작업에서 일관된 브랜드 이미지를 고객에게 제공할 수 있습니다.

기술 관리자는 Adobe Campaign 내에서 여러 브랜드를 만들고 관리할 수 있습니다. 이를 통해 로고 및 이메일 추적 설정을 포함하여 브랜드 정체성을 구성하는 모든 요소를 정의할 수 있습니다. 이러한 브랜드가 생성되면 게재에 쉽게 연결할 수 있습니다.

Campaign에서 조직의 새 엔터티를 추가하거나 다른 하위 도메인에서 보내야 하는 새 유형의 이메일을 만들 수 있습니다. 이렇게 하려면 아래 단계를 수행합니다.

1. **새 하위 도메인 구성** - Adobe에서 사용할 새 하위 도메인의 경우 첫 번째 단계는 이를 구성하는 것입니다. 다음을 통해 이 작업을 수행할 수 있습니다. [캠페인 Campaign 컨트롤 패널](https://experienceleague.adobe.com/docs/control-panel/using/subdomains-and-certificates/subdomains-branding.html?lang=ko) 또는 Adobe 기술 담당자에게 문의하십시오. 하위 도메인 구성에 대해 자세히 알아보기 [이 페이지에서](https://experienceleague.adobe.com/en/docs/deliverability-learn/deliverability-best-practice-guide/additional-resources/campaign/ac-domain-name-setup).

   >[!NOTE]
   >
   >컨트롤 패널은 모든 관리 사용자가 액세스할 수 있습니다. 사용자에게 관리자 권한을 부여하는 단계는 [이 페이지](https://experienceleague.adobe.com/docs/control-panel/using/discover-control-panel/managing-permissions.html?lang=ko#discover-control-panel)에 자세히 설명되어 있습니다.

1. **게재 템플릿 만들기** - 새 브랜드를 사용할 수 있게 되면 가장 좋은 방법은 이 새 브랜드를 참조하는 빈 게재 템플릿을 하나 이상 만드는 것입니다. [자세히 알아보기](branding-assign.md).

1. **게재 기능 지침 확인** - 새 도메인 사용을 시작하기 전에 Adobe 전달성 팀과 전략에 대해 논의해야 합니다. 모범 사례를 정의하는 데 도움이 됩니다. 예를 들어 도메인 간에 IP를 분할하기 위해 새 선호도를 만들어야 하는지 및/또는 램프 업 계획을 정의해야 하는지 등이 여기에 포함됩니다.

