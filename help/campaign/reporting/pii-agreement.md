---
title: 동적 보고서 시작
description: 다이내믹 보고 사용 계약에 대한 자세한 내용
level: Beginner
badge: label="제한된 가용성" type="Informative" url="../campaign-standard-migration-home.md" tooltip="마이그레이션된 사용자 Campaign Standard으로 제한됨"
audience: end-user
exl-id: 9fcef466-f306-480e-b42e-d18daa8bcf06
source-git-commit: dbdf1c4f8b676c73a7cc3a46af2838ebb9326457
workflow-type: tm+mt
source-wordcount: '523'
ht-degree: 1%

---

# 동적 보고 사용 계약 {#pii-agreement}

동적 보고 사용 계약의 목적은 데이터 처리에 대한 팝업 동의로 작동하는 것입니다. 기본적으로 계약은 표시만 되며 관리 권한이 할당된 사용자만 수락하거나 거부할 수 있습니다.

동적 보고 사용 계약에 액세스하려면 **[!UICONTROL 도구]** > **[!UICONTROL 고급]** > **[!UICONTROL 배포 마법사]**&#x200B;를 선택하십시오.

![](assets/pii-agreement.png)

다음 세 가지 옵션을 사용할 수 있습니다.

* **[!UICONTROL 나중에 묻기]**: 계약에 동의하거나 동의하지 않으면 프로필 차원이 보고서에 표시되지 않고 고객의 개인 식별 정보가 수집 또는 전송되지 않습니다.
* **[!UICONTROL 동의]**: 이 계약에 동의하면 Adobe Campaign에서 고객의 개인 식별 정보를 수집하고 이를 보고 또는 데이터 센터로 전송하는 권한을 부여합니다.
* **[!UICONTROL 거부]**: 계약을 거부하면 프로필 차원이 보고서에 표시되지 않고 고객의 개인 식별 정보가 수집되거나 전송되지 않습니다. 이 경우 externalID는 계속 수집되고 최종 사용자를 식별하는 데 사용됩니다.

아래 표에는 지역에 따라 이 계약에 동의한 후 발생한 사항이 표시됩니다.

|  | 다이내믹 보고 | Microsoft Dynamics 365 커넥터 |
|---|---|---|
| 아메리카 및 APAC(아시아 태평양) | **사용 가능한 기능**. <br>미국 보고 센터에 푸시된 모든 기본 프로필(예: 도시, 국가/지역, 주, 성별 및 연령 기준 세그먼트) 및 사용자 지정 프로필 정보. | **사용 가능한 기능**. <br>모든 기본 및 사용자 지정 프로필 필드와 Adobe Campaign 이벤트 필드가 미국 데이터 센터에서 처리됩니다. |
| EMEA(유럽 중동 및 아프리카) | **사용 가능한 기능**. <br>EMEA 보고 센터에 푸시된 모든 기본 제공(예: 도시, 국가/지역, 주, 성별 및 연령 기준 세그먼트) 및 사용자 지정 프로필 정보. | **기능을 사용할 수 있습니다.** <br>EMEA 데이터 센터에서 처리된 기본 및 사용자 지정 프로필 필드와 Adobe Campaign 이벤트 필드. <br>**[!UICONTROL 제어 데이터&#x200B;]**- Adobe I/O 등록 데이터와 미국 데이터 센터에서 전송 및 저장된 고객 최종 사용자 이벤트의 ID가 들어 있습니다. |

아래 표에는 지역에 따라 이 계약을 거절한 후 발생한 내용이 표시됩니다. 이 계약을 거부하더라도 게재 및 Microsoft Dynamics 365 통합에 대한 보고를 계속 사용할 수 있습니다.

| 지역 | 다이내믹 보고 | Microsoft Dynamics 365 커넥터 |
|---|---|---|
| 아메리카 및 APAC(아시아 태평양) | **사용 가능한 기능**. <br> ExternalID를 제외하고 기본 및 사용자 지정 프로필 정보가 미국 보고 센터로 푸시되지 않았습니다. | **사용 가능한 기능**. <br>외부 ID와 받는 사람 ID를 제외하고 기본 프로필 필드나 사용자 지정 프로필 필드를 미국 데이터 센터로 보내지 않습니다. <br>미러 페이지 ID를 제외하고 미국 데이터 센터에서 처리된 모든 Adobe Campaign 이벤트 필드. |
| EMEA(유럽 중동 및 아프리카) | **사용 가능한 기능**. <br>기본 및 사용자 지정 프로필 정보가 ExternalID를 제외하고 EMEA 보고 센터로 푸시되지 않았습니다. | **기능을 사용할 수 있습니다.** <br>외부 ID와 받는 사람 ID를 제외하고 기본 프로필 또는 사용자 지정 프로필 필드가 EMEA 데이터 센터로 전송되지 않았습니다. <br>미러 페이지 ID를 제외하고 EMEA 데이터 센터에서 처리된 모든 Adobe Campaign 이벤트 필드. |

이 선택은 최종적이지 않습니다. **[!UICONTROL 관리]** > **[!UICONTROL 플랫폼]** > **[!UICONTROL 옵션]**&#x200B;에서 **[!UICONTROL realtimeReporting_collectPII]** 옵션을 선택하여 언제든지 변경할 수 있습니다.

값은 언제든지 변경할 수 있습니다. 값 1은 **[!UICONTROL 나중에 묻기]**, 2 **[!UICONTROL 거부]** 및 3 **[!UICONTROL 수락]**&#x200B;에 해당합니다.
