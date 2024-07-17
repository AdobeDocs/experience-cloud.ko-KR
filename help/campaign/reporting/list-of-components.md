---
title: 구성 요소 목록
description: 여기에서 사용 가능한 모든 구성 요소 목록 찾기     동적 보고서와 해당 정의.
level: Beginner
audience: end-user
badge: label="제한된 가용성" type="Informative" url="../campaign-standard-migration-home.md" tooltip="마이그레이션된 사용자 Campaign Standard으로 제한됨"
exl-id: 5c58db92-7878-4c70-b076-a393f1cda8b7
source-git-commit: 34c6f8a137a9085b26c0ea8f78930cff6192cfc9
workflow-type: tm+mt
source-wordcount: '770'
ht-degree: 1%

---

# 구성 요소 목록 {#list-of-components}

두 구성 요소가 호환되지 않으면 셀에 **없음** 값이 표시됩니다.

## 차원 {#dimensions}

아래 표는 보고서에 사용된 차원 목록과 해당 정의를 제공합니다.

<table> 
 <thead> 
  <tr> 
   <th> Dimension<br/> </th> 
   <th> 정의<br/> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 브라우저<br/> </td> 
   <td> 메시지를 열거나 클릭한 브라우저.<br/> </td> 
  </tr> 
  <tr> 
   <td> 캠페인<br/> </td> 
   <td> 캠페인의 레이블과 ID입니다.<br/> </td> 
  </tr> 
  <tr> 
   <td> 배달<br/> </td> 
   <td> 게재 레이블 및 ID입니다.<br/> </td> 
  </tr> 
  <tr> 
   <td> 장치<br/> </td> 
   <td> 이메일/SMS/푸시 알림이 열리거나 보거나 클릭한 장치.<br/> </td> 
  </tr> 
  <tr> 
   <td> 실패 이유<br/> </td> 
   <td> 각 게재에 대해 바운스를 발생시키는 오류 유형(예: 사용자 알 수 없음, 잘못된 도메인 또는 사서함 가득 참).<br/> </td> 
  </tr> 
  <tr> 
   <td> 모바일 앱 이름<br/> </td> 
   <td> 모바일 응용 프로그램 이름<br/> </td> 
  </tr>
  <tr> 
   <td> 플랫폼<br/> </td> 
   <td> 메시지를 열고/보고/클릭한 장치의 플랫폼입니다.<br/> </td> 
  </tr> 
  <tr> 
   <td> 프로필<br/> </td> 
   <td> 프로필 리소스 확장 중에 만들어진 기본 및 사용자 지정 프로필 필드를 다시 그룹화합니다.<br/> </td> 
  </tr> 
  <tr> 
   <td> 받는 사람 도메인<br/> </td> 
   <td> 전자 메일을 여는 데 사용되는 도메인입니다.<br/> </td> 
  </tr> 
  <tr> 
   <td> 반복 게재<br/> </td> 
   <td> 반복 게재의 레이블 및 ID입니다.<br/> </td> 
  </tr> 
  <tr> 
   <td> 보낸 사람 도메인<br/> </td> 
   <td> 전자 메일을 보내는 데 사용되는 도메인입니다.<br/> </td> 
  </tr> 
  <tr> 
   <td> 보낸 사람 IP<br/> </td> 
   <td> 전자 메일을 보내는 데 사용되는 IP입니다.<br/> </td> 
  </tr> 
  <tr> 
   <td> 추적 URL<br/> </td> 
   <td> 메시지에서 사용자가 클릭한 URL입니다.<br/> </td> 
  </tr> 
  <tr> 
   <td> 추적 URL 범주<br/> </td> 
   <td> 추적 URL에 할당된 범주.<br/> </td> 
  </tr> 
  <tr> 
   <td> 추적 URL 레이블<br/> </td> 
   <td> 미러 페이지와 같이 URL에 지정된 레이블은 당사로 연락하거나 엽니다.<br/> </td> 
  </tr> 
  <tr> 
   <td> 트랜잭션 게재<br/> </td> 
   <td> 트랜잭션 게재의 레이블 및 ID입니다.<br/> </td> 
  </tr> 
  <tr> 
   <td> 변형<br/> </td> 
   <td> A/B 테스트 시 이메일 변형.<br/> </td> 
  </tr> 
 </tbody> 
</table>

## 지표 {#metrics}

아래 표는 보고서에 사용된 지표 목록과 게재 유형에 따라 해당 정의를 제공합니다.

### 이메일 지표 {#email-and-sms-metrics}

<table> 
 <thead> 
  <tr> 
   <th> 지표<br/> </th> 
   <th> 정의<br/> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 차단 목록<br/> </td> 
   <td> 스팸 또는 정크 메일로 선언된 받는 사람의 수입니다.<br/> </td> 
  </tr> 
  <tr> 
   <td> 차단 목록에 추가하다 속도<br/> </td> 
   <td> 차단 목록에 추가하다 게재 비율(<br/>) </td> 
  </tr> 
  <tr> 
   <td> 바운스 + 오류<br/> </td> 
   <td> 보낸 총 메시지 수와 관련하여 게재 및 자동 반환 처리 중에 누적된 총 오류.<br/> </td> 
  </tr> 
  <tr> 
   <td> 바운스 + 오류율<br/> </td> 
   <td> 보낸 전자 메일과 비교하여 반송된 전자 메일의 비율입니다.<br/> </td> 
  </tr> 
  <tr> 
   <td> <br/> 클릭 </td> 
   <td> 게재에서 콘텐츠를 클릭한 횟수입니다.<br/> </td> 
  </tr> 
  <tr> 
   <td> 클릭스루 비율<br/> </td> 
   <td> 게재 중 클릭 비율입니다.<br/> </td> 
  </tr> 
  <tr> 
   <td> 배달됨<br/> </td> 
   <td> 보낸 총 메시지 수와 관련하여 성공적으로 보낸 메시지 수입니다.<br/> </td> 
  </tr> 
  <tr> 
   <td> 게재율<br/> </td> 
   <td> 성공적으로 보낸 메시지의 비율입니다.<br/> </td> 
  </tr> 
  <tr> 
   <td> 하드 바운스<br/> </td> 
   <td> 잘못된 이메일 주소와 같은 총 영구 오류 수입니다.<br/> </td> 
  </tr> 
  <tr> 
   <td> 하드 바운스 비율<br/> </td> 
   <td> 영구 오류로 인해 실패한 게재의 비율입니다.<br/> </td> 
  </tr> 
  <tr> 
   <td> 미러 페이지<br/> </td> 
   <td> 미러 페이지 링크를 클릭한 수신자 수입니다.<br/> </td> 
  </tr> 
  <tr> 
   <td> 미러 페이지 속도<br/> </td> 
   <td> 총 게재 메시지와 비교한 미러 페이지 링크 클릭 비율입니다.<br/> </td> 
  </tr> 
  <tr> 
   <td> 오퍼 클릭수<br/> </td> 
   <td> 게재에서 오퍼를 클릭한 횟수입니다.<br/> </td> 
  </tr> 
  <tr> 
   <td> 오퍼 클릭률<br/> </td> 
   <td> 오퍼 클릭률입니다.<br/> </td> 
  </tr> 
  <tr> 
   <td> <br/> 열기 </td> 
   <td> 메시지가 게재된 횟수입니다.<br/> </td> 
  </tr> 
  <tr> 
   <td> 열람률<br/> </td> 
   <td> 열린 메시지의 비율입니다.<br/> </td> 
  </tr> 
  <tr> 
   <td> 처리됨/전송됨<br/> </td> 
   <td> 게재에 대한 총 전송 수입니다.<br/> </td> 
  </tr> 
  <tr> 
   <td> 격리<br/> </td> 
   <td> 반송되어 주소가 격리된 메시지 수입니다.<br/> </td> 
  </tr> 
  <tr> 
   <td> 격리 비율<br/> </td> 
   <td> 보낸 메시지와 비교하여 격리한 비율입니다.<br/> </td> 
  </tr> 
  <tr> 
   <td> 거부됨<br/> </td> 
   <td> SMTP 서버에서 스팸으로 분류된 메시지 수입니다.<br/> </td> 
  </tr> 
  <tr> 
   <td> 거부된 비율<br/> </td> 
   <td> 거부됨으로 표시된 메시지의 비율입니다.<br/> </td> 
  </tr> 
  <tr> 
   <td> 소프트 바운스<br/> </td> 
   <td> 전체 받은 편지함과 같은 총 임시 오류 수입니다.<br/> </td> 
  </tr> 
  <tr> 
   <td> 소프트 바운스 비율<br/> </td> 
   <td> 일시적인 이유로 실패한 게재의 비율입니다.<br/> </td> 
  </tr> 
  <tr> 
   <td> 고유 클릭수<br/> </td> 
   <td> 게재에서 콘텐츠를 클릭한 수신자 수입니다.<br/> </td> 
  </tr> 
  <tr> 
   <td> 고유 열기 수<br/> </td> 
   <td> 게재를 연 수신자 수입니다.<br/> </td> 
  </tr> 
  <tr> 
   <td> 구독 취소된 고유 <br/> </td> 
   <td> 구독 취소 링크를 클릭한 수신자 수입니다.<br/> </td> 
  </tr> 
  <tr> 
   <td> 구독 취소 비율<br/> </td> 
   <td> 배달된 메시지와 비교하여 고유한 구독 취소 수입니다.<br/> </td> 
  </tr> 
  <tr> 
   <td> 구독 취소됨<br/> </td> 
   <td> 구독 취소 링크를 클릭한 횟수입니다.<br/> </td> 
  </tr> 
 </tbody> 
</table>

<!--
### Push notification metrics {#push-notification-metrics}

<table> 
 <thead> 
  <tr> 
   <th> Metric<br/> </th> 
   <th> Definition<br/> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Bounces + Errors<br/> </td> 
   <td> Total of errors cumulated during delivery in relation to the total number of sent messages, e.g. errors from MCPNS or provider.<br/> </td> 
  </tr> 
  <tr> 
   <td> Bounce + Error rate<br/> </td> 
   <td> Percentage of push notifications that bounced compared to push notifications sent.<br/> </td> 
  </tr> 
  <tr> 
   <td> Click<br/> </td> 
   <td> Number of times a push notification has been delivered to the device and clicked on by the user. The user either wanted to view the notification, which will then be moved to Push Open tracking, or dismiss it.<br/> </td> 
  </tr> 
  <tr> 
   <td> Click through rate<br/> </td> 
   <td> Percentage of users who interacted with the push notification.<br/> </td> 
  </tr> 
  <tr> 
   <td> Delivered<br/> </td> 
   <td> Number of push notifications successfully sent, in relation to the total number of sent push notifications.<br/> </td> 
  </tr> 
  <tr> 
   <td> Delivered rate<br/> </td> 
   <td> Percentage of push notifications successfully sent.<br/> </td> 
  </tr> 
  <tr> 
   <td> Impressions<br/> </td> 
   <td> Number of times a push notification has been delivered to the device and left untouched in the notification center. In most cases, impressions number should be similar to the delivered number. This ensures that the device got the message and relayed that information back to the server.<br/> </td> 
  </tr> 
  <tr> 
   <td> Processed/sent<br/> </td> 
   <td> Total number of push notifications sent.<br/> </td> 
  </tr> 
  <tr> 
   <td> Open<br/> </td> 
   <td> Total number of push notifications delivered to the device and clicked on by users thus opening the app. This is similar to the Push Click except a Push Open will not be triggered if the notification was dismissed.<br/> </td> 
  </tr> 
  <tr> 
   <td> Open rate<br/> </td> 
   <td> Percentage of opened push notifications.<br/> </td> 
  </tr> 
  <tr> 
   <td> Unique clicks<br/> </td> 
   <td> Number of times a unique user interacts with the push notification, e.g. clicks on the notification or button.<br/> </td> 
  </tr> 
  <tr> 
   <td> Unique impressions<br/> </td> 
   <td> Number of impressions by recipient.<br/> </td> 
  </tr> 
  <tr> 
   <td> Unique Opens<br/> </td> 
   <td> Number of recipients who opened the delivery.<br/> </td> 
  </tr> 
 </tbody> 
</table>

### In-App metrics {#in-app-metrics}

<table> 
 <thead> 
  <tr> 
   <th> Metric<br/> </th> 
   <th> Definition<br/> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Delivered<br/> </td> 
   <td> Total number of In-App messages delivered to the device by the service provider.<br/> </td> 
  </tr> 
  <tr> 
   <td> Impressions<br/> </td> 
   <td> Total of In-App messages seen by recipients depending on whether trigger criterion was met.<br/> </td> 
  </tr> 
  <tr> 
   <td> In-App clicks <br/> </td> 
   <td> Total number of recipients who clicked on Button 1 or Button 2.<br/> </td> 
  </tr> 
  <tr> 
   <td> In-App click through rate<br/> </td> 
   <td> Percentage of users who clicked on Button 1 or Button 2 compared to users who saw the message.<br/> </td> 
  </tr> 
  <tr> 
   <td> In-App dismissal<br/> </td> 
   <td> Total number of messages that recipients dismissed either by clicking the close button or auto-dismiss.<br/> </td> 
  </tr> 
  <tr> 
   <td> In-App dismissal rate<br/> </td> 
   <td> Percentage of In-App messages that recipients dismissed.<br/> </td> 
  </tr> 
  <tr> 
   <td> Processed/sent<br/> </td> 
   <td> Total number of In-App messages sent from Adobe Campaign as part of the delivery sent process.<br/> </td> 
  </tr> 
  <tr> 
   <td> Unique impressions<br/> </td> 
   <td> Number of impressions by a unique recipient.<br/> </td> 
  </tr> 
  <tr> 
   <td> Unique In-App clicks<br/> </td> 
   <td> Number of times recipients clicked on Button 1 or Button 2.<br/> </td> 
  </tr> 
  <tr> 
   <td> Unique In-App dismissals<br/> </td> 
   <td> Number of time recipients dismissed an In-App message.<br/> </td> 
  </tr> 
 </tbody> 
</table>
-->

## 세그먼트 {#segments}

아래 표는 보고서에 사용된 세그먼트 목록과 해당 정의를 제공합니다.

<table> 
 <thead> 
  <tr> 
   <th> 세그먼트<br/> </th> 
   <th> 정의<br/> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 나이: 붐 세대 1<br/> </td> 
   <td> 1946년부터 1954년까지 출생한 수신자.<br/> </td> 
  </tr> 
  <tr> 
   <td> 나이: 붐 세대 2<br/> </td> 
   <td> 1955년부터 1965년까지 출생한 수신자.<br/> </td> 
  </tr> 
  <tr> 
   <td> 나이: 18세부터 25<br/> </td> 
   <td> 18세에서 25세 사이의 수신자.<br/> </td> 
  </tr> 
  <tr> 
   <td> 나이: 26세부터 30<br/> </td> 
   <td> 26세에서 30세 사이의 수신자.<br/> </td> 
  </tr> 
  <tr> 
   <td> 나이: 31~40<br/> </td> 
   <td> 31세에서 40세 사이의 수신자.<br/> </td> 
  </tr> 
  <tr> 
   <td> 나이: 41~50<br/> </td> 
   <td> 41세에서 50세 사이의 수신자.<br/> </td> 
  </tr> 
  <tr> 
   <td> 나이: 세대 X<br/> </td> 
   <td> 1966년부터 1976년까지 출생한 수신자.<br/> </td> 
  </tr> 
  <tr> 
   <td> 나이: Y세대(밀레니얼)<br/> </td> 
   <td> 1977년부터 1994년까지 출생한 수신자.<br/> </td> 
  </tr> 
  <tr> 
   <td> 나이: 세대 Z<br/> </td> 
   <td> 1995년부터 오늘까지 출생한 수신자.<br/> </td> 
  </tr> 
  <tr> 
   <td> 연령: 50<br/>보다 큼 </td> 
   <td> 연령이 50세 이상인 수신자.<br/> </td> 
  </tr> 
  <tr> 
   <td> 나이: 25<br/> 미만 </td> 
   <td> 연령이 25.<br/>세 미만인 수신자 </td> 
  </tr> 
  <tr> 
   <td> 연령: 30<br/> 미만 </td> 
   <td> 연령이 30.<br/>세 미만인 수신자 </td> 
  </tr> 
  <tr> 
   <td> 나이: 40<br/> 미만 </td> 
   <td> 연령이 40.<br/> 미만인 수신자 </td> 
  </tr> 
  <tr> 
   <td> 연령: 50<br/> 미만 </td> 
   <td> 연령이 50.<br/>세 미만인 수신자 </td> 
  </tr> 
  <tr> 
   <td> 수명: 자동 생성<br/> </td> 
   <td> 1945년 또는 그 이전에 태어난 수신자.<br/> </td> 
  </tr> 
  <tr> 
   <td> 모든 방문<br/> </td> 
   <td> 모든 받는 사람<br/> </td> 
  </tr>
 </tbody> 
</table>
