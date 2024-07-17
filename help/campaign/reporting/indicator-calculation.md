---
title: 지표 계산
description: 모든 지표의 공식 목록을 사용하여 보고서 결과를 이해합니다.
level: Intermediate
audience: end-user
badge: label="제한된 가용성" type="Informative" url="../campaign-standard-migration-home.md" tooltip="마이그레이션된 사용자 Campaign Standard으로 제한됨"
exl-id: 06fb21a5-ae98-4c14-97f0-7f851d60ae7d
source-git-commit: 34c6f8a137a9085b26c0ea8f78930cff6192cfc9
workflow-type: tm+mt
source-wordcount: '388'
ht-degree: 1%

---

# 지표 계산{#indicator-calculation}

>[!NOTE]
>
>대용량 및 실시간 분석을 보다 효과적으로 처리하고 관리하기 위해 동적 보고에서는 고유 개수 예측에 대해 대략적인 집계를 사용합니다. 대략적인 집계는 제한된 메모리 사용을 제공하며 종종 정확한 계산보다 빠릅니다.

아래 표는 게재 유형에 따라 다양한 보고서에서 사용되는 지표 목록과 해당 계산 공식을 보여 줍니다.

## 이메일 게재 {#email-delivery}

<table> 
 <thead> 
  <tr> 
   <th> <strong>레이블</strong> <br/> </th> 
   <th> <strong>필드 이름</strong> <br/> </th> 
   <th> <strong>지표 계산 수식</strong> <br/> </th> 
   <th> <strong>댓글</strong><br/> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 사용하지 않는 계정<br/> </td> 
   <td> @disabled<br/> </td> 
   <td> count(@failureReason=4)<br/> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 차단 목록<br/> </td> 
   <td> @blacklisted<br/> </td> 
   <td> count(@failureReason=8, @failureType=2)<br/> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 차단 목록에 추가하다 속도<br/> </td> 
   <td> @rateBlacklisted<br/> </td> 
   <td> @blacklisted/@sent<br/> </td> 
   <td> 요금 계산의 분모는 보낸 개수(배달된 + 바운스 수)를 기반으로 합니다.<br/> </td> 
  </tr> 
  <tr> 
   <td> 바운스 + 오류<br/> </td> 
   <td> @bounces<br/> </td> 
   <td> count(@status=2)<br/> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 바운스 + 오류율<br/> </td> 
   <td> @rateBounces<br/> </td> 
   <td> @bounces/@sent<br/> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> <br/> 클릭 </td> 
   <td> @clicks<br/> </td> 
   <td> count(@trackingUrlType=1 또는 10 또는 11)<br/> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 클릭스루 비율<br/> </td> 
   <td> @clickthrough<br/> </td> 
   <td> @uniqueclicks/@delivered<br/> </td> 
   <td> 요율 계산의 분모는 배달된 것만 기반으로 합니다.<br/> </td> 
  </tr> 
  <tr> 
   <td> 배달됨<br/> </td> 
   <td> @delivered<br/> </td> 
   <td> count(@status=1)<br/> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 게재율<br/> </td> 
   <td> @rateDelivered<br/> </td> 
   <td> @delivered/@sent<br/> </td> 
   <td> 요금 계산의 분모는 보낸 개수(배달된 + 바운스 수)를 기반으로 합니다.<br/> </td> 
  </tr> 
  <tr> 
   <td> 하드 바운스<br/> </td> 
   <td> @hardBounces<br/> </td> 
   <td> count(@failureType=2 및 @failureReason=8)<br/> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 하드 바운스 비율<br/> </td> 
   <td> @rateHardBounces<br/> </td> 
   <td> @hardBounces/@sent<br/> </td> 
   <td> 요금 계산의 분모는 보낸 개수(배달된 + 바운스 수)를 기반으로 합니다.<br/> </td> 
  </tr> 
  <tr> 
   <td> 잘못된 도메인<br/> </td> 
   <td> @invalidDomain<br/> </td> 
   <td> count(@failureReason=2)<br/> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 사서함 가득 참<br/> </td> 
   <td> @mailBoxFull<br/> </td> 
   <td> count(@failureReason=5)<br/> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 미러 페이지<br/> </td> 
   <td> @mirrorPage<br/> </td> 
   <td> count(@trackingUrlType=6)<br/> </td> 
   <td> 요율 계산의 분모는 배달된 것만 기반으로 합니다.<br/> </td> 
  </tr> 
  <tr> 
   <td> 미러 페이지 속도<br/> </td> 
   <td> @rateMirrorPage<br/> </td> 
   <td> @mirrorPage/@delivered<br/> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 연결되지 않음<br/> </td> 
   <td> @notConnected<br/> </td> 
   <td> count(@failureReason=6)<br/> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> <br/> 열기 </td> 
   <td> @uniqueOpens<br/> </td> 
   <td> count(@trackingUrlType=2 + unique(@trackingUrlType=1,2,3,6,10,11) - unique(@trackingUrlType=2))<br/> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 열람률<br/> </td> 
   <td> @rateOpens<br/> </td> 
   <td> @opens/@delivered<br/> </td> 
   <td> 요율 계산의 분모는 배달된 것만 기반으로 합니다.<br/> </td> 
  </tr> 
  <tr> 
   <td> 격리<br/> </td> 
   <td> @quarantine<br/> </td> 
   <td> isQuarantine=true<br/> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 격리 비율<br/> </td> 
   <td> @rateQuarantine<br/> </td> 
   <td> @quarantine/@sent<br/> </td> 
   <td> 요금 계산의 분모는 보낸 개수(배달된 + 바운스 수)를 기반으로 합니다.<br/> </td> 
  </tr>
  <tr> 
   <td> 거부됨<br/> </td> 
   <td> @rejected<br/> </td> 
   <td> count(@failureReason=20, @failureType=2)<br/> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 거부된 비율<br/> </td> 
   <td> @rateRejected<br/> </td> 
   <td> @rejected/@sent<br/> </td> 
   <td> 요금 계산의 분모는 보낸 개수(배달된 + 바운스 수)를 기반으로 합니다.<br/> </td> 
  </tr> 
  <tr> 
   <td> 처리됨/전송됨<br/> </td> 
   <td> @sent<br/> </td> 
   <td> @delivered + @bounces<br/> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 소프트 바운스<br/> </td> 
   <td> @softBounces<br/> </td> 
   <td> count(@failureType=1)<br/> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 소프트 바운스 비율<br/> </td> 
   <td> @rateSoftBounces<br/> </td> 
   <td> @softBounces/@sent<br/> </td> 
   <td> 요금 계산의 분모는 보낸 개수(배달된 + 바운스 수)를 기반으로 합니다.<br/> </td> 
  </tr> 
  <tr> 
   <td> 고유 클릭수<br/> </td> 
   <td> @uniqueclicks<br/> </td> 
   <td> 고유 클릭수는 ThetaSketch 개념을 사용하여 계산됩니다. </a>.<br/> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 고유 열기 수<br/> </td> 
   <td> @uniqueopens<br/> </td> 
   <td> unique(@trackingUrlType=1,2,3,6,10,11)<br/> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 연결할 수 없는 <br/> </td> 
   <td> @unreachable<br/> </td> 
   <td> count(@failureReason=3)<br/> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 구독 취소<br/> </td> 
   <td> @unsubscribes<br/> </td> 
   <td> count(@trackingUrlType=3)<br/> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 구독 취소 비율<br/> </td> 
   <td> @rateUnsubscribes<br/> </td> 
   <td> @unsubscribes/@delivered<br/> </td> 
   <td> 요율 계산의 분모는 배달된 것만 기반으로 합니다.<br/> </td> 
  </tr> 
  <tr> 
   <td> 알 수 없는 사용자<br/> </td> 
   <td> @unknownUser<br/> </td> 
   <td> count(@failureReason=1)<br/> </td> 
   <td> </td> 
  </tr> 
 </tbody> 
</table>

<!--
## Push notification delivery {#push-notification-delivery}

<table> 
 <thead> 
  <tr> 
   <th> <strong>Label</strong> <br/> </th> 
   <th> <strong>Field name</strong> <br/> </th> 
   <th> <strong>Indicator calculation formula</strong> <br/> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Processed/sent<br/> </td> 
   <td> @sent<br/> </td> 
   <td> @count(status=sent)<br/> </td> 
  </tr> 
  <tr> 
   <td> Delivered<br/> </td> 
   <td> @delivered<br/> </td> 
   <td> @count(status=delivered)<br/> </td> 
  </tr> 
  <tr> 
   <td> Delivered rate<br/> </td> 
   <td> @rateDelivered<br/> </td> 
   <td> (@delivered/@sent)*100<br/> </td> 
  </tr> 
  <tr> 
   <td> Bounce + Error rate<br/> </td> 
   <td> @rateBounces<br/> </td> 
   <td> (@delivered/@sent)*100<br/> </td> 
  </tr> 
  <tr> 
   <td> Open<br/> </td> 
   <td> @opens<br/> </td> 
   <td> @count(status=open)<br/> </td> 
  </tr> 
  <tr> 
   <td> Open rate<br/> </td> 
   <td> @rateOpens<br/> </td> 
   <td> (@opens/@delivered)*100<br/> </td> 
  </tr> 
  <tr> 
   <td> Unique opens<br/> </td> 
   <td> @uniqueopens<br/> </td> 
   <td> Unique opens is calculated using ThetaSketch concepts of unique RecipientIds.<br/> </td> 
  </tr> 
  <tr> 
   <td> Impressions<br/> </td> 
   <td> @impressions<br/> </td> 
   <td> @count(status=delivered)<br/> </td> 
  </tr> 
  <tr> 
   <td> Unique impressions<br/> </td> 
   <td> @uniqueimpressions<br/> </td> 
   <td> @unique(@count(status=view))<br/> </td> 
  </tr> 
  <tr> 
   <td> Click<br/> </td> 
   <td> @clicks<br/> </td> 
   <td> @count(status=interact)<br/> </td> 
  </tr> 
  <tr> 
   <td> Unique clicks<br/> </td> 
   <td> @uniqueclicks<br/> </td> 
   <td> Unique clicks is calculated using ThetaSketch concepts.<br/> </td> 
  </tr> 
  <tr> 
   <td> Click through rate<br/> </td> 
   <td> @clickthrough<br/> </td> 
   <td> (@interact/@delivered)*100<br/> </td> 
  </tr> 
 </tbody> 
</table>

## In-App delivery {#in-app-delivery}

<table> 
 <thead> 
  <tr> 
   <th> <strong>Label</strong> <br/> </th> 
   <th> <strong>Field name</strong> <br/> </th> 
   <th> <strong>Indicator calculation formula</strong> <br/> </th> 
   <th> <strong>Comments</strong><br/> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Processed/sent<br/> </td> 
   <td> @sent<br/> </td> 
   <td> @count(status=sent)<br/> </td> 
   <td> sent=delivered<br/> </td> 
  </tr> 
  <tr> 
   <td> Delivered<br/> </td> 
   <td> @delivered<br/> </td> 
   <td> @count(status=delivered)<br/> </td> 
   <td> delivered=sent<br/> </td> 
  </tr> 
  <tr> 
   <td> Impressions<br/> </td> 
   <td> @impressions<br/> </td> 
   <td> @count(status=view) or @count(status=button 1 click + button 2 click + dismissals)<br/> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Unique impressions<br/> </td> 
   <td> @uniqueimpressions<br/> </td> 
   <td> @unique(@count(status=view))<br/> </td> 
   <td> For <span class="uicontrol">Target users based on their Campaign profile (inAppProfile)</span> template, user = Recipient Id.<br/> For <span class="uicontrol">Target all users of a Mobile app (inAppBroadcast)</span> and <span class="uicontrol">Target users based on their Mobile profile (inApp)</span> templates, user = MC Id or equivalent that represents a unique combination of user, mobile app and device.<br/> </td> 
  </tr> 
  <tr> 
   <td> In-App clicks <br/> </td> 
   <td> @inappclicks<br/> </td> 
   <td> @count (status=click)<br/> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Unique In-App clicks<br/> </td> 
   <td> @uniqueinapp<br/> </td> 
   <td> @unique(@count (status=clicks))<br/> </td> 
   <td> For <span class="uicontrol">Target users based on their Campaign profile (inAppProfile)</span> template, user = Recipient Id.<br/> For <span class="uicontrol">Target all users of a Mobile app (inAppBroadcast)</span> and <span class="uicontrol">Target users based on their Mobile profile (inApp)</span> templates, user = MC Id or equivalent that represents a unique combination of user, mobile app and device.<br/> </td> 
  </tr> 
  <tr> 
   <td> In-App click through rate<br/> </td> 
   <td> @inappclickthrough<br/> </td> 
   <td> Total clicks on Button 1 or Button 2/total impressions*100<br/> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> In-App dismissal<br/> </td> 
   <td> @dismissal<br/> </td> 
   <td> @count (status=close)<br/> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Unique In-App dismissals<br/> </td> 
   <td> @uniquedismissal<br/> </td> 
   <td> @unique(@count (status=close))<br/> </td> 
   <td> For <span class="uicontrol">Target users based on their Campaign profile (inAppProfile)</span> template, user = Recipient Id.<br/> For <span class="uicontrol">Target all users of a Mobile app (inAppBroadcast)</span> and <span class="uicontrol">Target users based on their Mobile profile (inApp)</span> templates, user = MC Id or equivalent that represents a unique combination of user, mobile app and device.<br/> </td> 
  </tr> 
  <tr> 
   <td> In-App dismissal rate<br/> </td> 
   <td> @dismissalrate<br/> </td> 
   <td> Total close/total impressions*100<br/> </td> 
   <td> </td> 
  </tr> 
 </tbody> 
</table>
-->
