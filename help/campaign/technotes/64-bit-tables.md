---
title: Adobe Campaign 웹 사용자 인터페이스
description: 64비트 테이블
badge: label="제한된 가용성" type="Informative" url="../campaign-standard-migration-home.md" tooltip="마이그레이션된 사용자 Campaign Standard으로 제한됨"
source-git-commit: 47b06a42fad73254025d8e21d14724f6fe93345b
workflow-type: tm+mt
source-wordcount: '181'
ht-degree: 1%

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
| nms:broadLogRcp | id |
| nms:trackingLogRcp | id |
| nms:excludeLogRcp | id |
| nms:broadLogVisitor | id |
| nms:trackingLogVisitor | id |
| nms:propositionRcp | interactionId |
| nms:propositionVisitor | interactionId |
| nms:webTrack링 로그 | id |
| nms:tmpBroadcast | message-id |
| nms:tmpMarketingPressure | message-id |
| nms:tmpBroadcastExclusion | message-id |
| nms:tmpBroadcastPaper | message-id |
| nms:broadLogAppSubRcp | id |
| nms:trackingLogAppSubRcp | id |
| nms:excludeLogAppSubRcp | id |
| nms:webEvent | broadLogSrc-id, broadLogRemkt-id |
| nms:broadLogMid | mktBroadLogId |
| nms:mirrorPageSearch | remoteMessageId |


