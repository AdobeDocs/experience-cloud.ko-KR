---
title: 이탈 요약
description: 바운스 요약 보고서를 통해, 전송된 캠페인의 상태와 발생할 수 있는 오류에 대해 알아보십시오.
audience: end-user
level: Intermediate
badge: label="제한된 가용성" type="Informative" url="../campaign-standard-migration-home.md" tooltip="Campaign Standard 마이그레이션된 사용자로 제한됨"
exl-id: b341edad-aa82-43d8-a5a1-b33a19973a1a
TQID: https://experienceleague.adobe.com/gfOXWpdQvONw72sdpnGehwpXcgte16B6dLiWV2LZXOc
product_v2:
  - id: d0a3eab4-7b10-4d96-a71e-6c0f8e7b7c87
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
topic_v2:
  - id: aa2f3246-cb95-4b30-8899-fdf7d73550cc
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
source-git-commit: ad84694f2f6f45e4ee30fc51379106835ac302be
workflow-type: tm+mt
source-wordcount: 298
ht-degree: 8%

---

# 이탈 요약{#bounce-summary}

이 보고서에는 반송 자동 처리뿐만 아니라 게재 중에 발생한 전체 하드 및 소프트 오류에 대해 자세히 설명되어 있습니다.

![](assets/campaign_reports_bounces.png)

각 테이블은 요약 번호와 차트로 표시됩니다. 세부 사항이 각각의 시각화 설정에 표시되는 방식을 변경할 수 있습니다.

**Flop 5 다시 분할**&#x200B;은(는) 격리 수가 가장 많은 5개의 게재를 나열합니다.

**바운스 이유** 표에는 각 게재의 바운스를 초래한 오류 유형에 사용할 수 있는 데이터가 포함되어 있습니다.

* **[!UICONTROL 사용자 알 수 없음]**: 잘못된 전자 메일 주소로 게재를 보낼 때 생성되는 오류 유형입니다.
* **[!UICONTROL 잘못된 도메인]**: 도메인이 잘못되었거나 더 이상 존재하지 않는 전자 메일 주소로 게재를 보낼 때 생성되는 오류 유형입니다.
* **[!UICONTROL 연결할 수 없음]**: 일시적으로 연결할 수 없는 도메인과 같이 메시지 게재 문자열에서 발생한 오류 유형입니다.
* **[!UICONTROL 계정 사용 안 함]**: 더 이상 존재하지 않는 전자 메일 주소로 게재를 보낼 때 생성되는 오류 유형입니다.
* **[!UICONTROL 사서함 가득 참]**: 받는 사람의 받은 편지함이 가득 찼을 때 생성되는 오류 유형입니다. 이 오류가 생성되기 전에 메시지를 전달하려고 5번 시도합니다.
* **[!UICONTROL 연결되지 않음]**: 메시지를 보낼 때 받는 사람의 휴대폰이 꺼져 있거나 네트워크에 연결되어 있지 않은 경우 발생하는 오류 유형입니다.

  >[!NOTE]
  >
  >이 유형의 오류는 모바일 채널의 게재에만 관련이 있습니다.

* **[!UICONTROL 거부됨]**: 인터넷 서비스 공급자(ISP)가 주소를 거부할 때 생성되는 오류 유형입니다. 예를 들어 보안 규칙이 스팸 방지 소프트웨어에 의해 적용된 경우.

**도메인 다시 분할** 테이블에는 받는 사람 도메인에 따라 배달하는 동안 발생한 전반적인 문제가 표시됩니다.
