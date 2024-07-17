---
title: Adobe Campaign 웹 사용자 인터페이스
description: 64비트 테이블
badge: label="제한된 가용성" type="Informative" url="../campaign-standard-migration-home.md" tooltip="마이그레이션된 사용자 Campaign Standard으로 제한됨"
exl-id: ab5f01fd-4ad5-46e9-b132-011fe0f7bbd2
source-git-commit: 34c6f8a137a9085b26c0ea8f78930cff6192cfc9
workflow-type: tm+mt
source-wordcount: '181'
ht-degree: 6%

---

# 64비트 스키마 {#64-bit-tables}

Campaign Standard에서 Campaign v8로 간편하게 전환하기 위해 몇 개의 표가 32비트에서 64비트로 변경되었습니다. 실제로, Campaign Standard은 여러 기본 스키마에서 64비트 PK를 지원하는 반면, Campaign v8은 대부분의 스키마에서 32비트 PK를 지원합니다.

## 제한 사항

* 이 기술 변경 사항은 Campaign Standard에서 마이그레이션하는 고객에게만 적용됩니다.
* 스키마 및 브로드로그 확장은 64비트에서 지원되지 않습니다. 32비트로 유지됩니다.
* 기술 사용자에게 전송된 게재와 관련된 로그는 Campaign v8에서 사용할 수 없습니다.
* PostgreSQL만 지원됩니다.

## 수정된 스키마

다음은 64비트로 변경된 스키마와 수정된 속성 목록입니다.

| 스키마 이름 | 속성 이름 |
|--- |--- |
| nms:broadLogRcp | ID |
| nms:trackingLogRcp | ID |
| nms:excludeLogRcp | ID |
| nms:broadLogVisitor | ID |
| nms:trackingLogVisitor | ID |
| nms:propositionRcp | interactionId |
| nms:propositionVisitor | interactionId |
| nms:webTrack링 로그 | ID |
| nms:tmpBroadcast | message-id |
| nms:tmpMarketingPressure | message-id |
| nms:tmpBroadcastExclusion | message-id |
| nms:tmpBroadcastPaper | message-id |
| nms:broadLogAppSubRcp | ID |
| nms:trackingLogAppSubRcp | ID |
| nms:excludeLogAppSubRcp | ID |
| nms:webEvent | broadLogSrc-id, broadLogRemkt-id |
| nms:broadLogMid | mktBroadLogId |
| nms:mirrorPageSearch | remoteMessageId |
