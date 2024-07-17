---
title: 동적 보고 문제 해결
description: 다이내믹 보고와 관련된 일반적인 질문을 여기에서 확인하십시오.
audience: end-user
level: Intermediate
badge: label="제한된 가용성" type="Informative" url="../campaign-standard-migration-home.md" tooltip="마이그레이션된 사용자 Campaign Standard으로 제한됨"
exl-id: a58fc8fd-e510-45ef-8fe9-c75ff4498113
source-git-commit: 34c6f8a137a9085b26c0ea8f78930cff6192cfc9
workflow-type: tm+mt
source-wordcount: '1239'
ht-degree: 1%

---

# 문제 해결{#troubleshooting}

이 섹션에서는 동적 보고와 관련된 일반적인 질문을 확인할 수 있습니다.

## 고유 열람 수 및 고유 클릭 수의 경우 집계 행의 개수가 개별 행의 개수와 일치하지 않습니다 {#unique-open-clicks-no-match}

이는 예상되는 비헤이비어입니다.
다음 예를 들어 이 동작을 설명할 수 있습니다.

프로필 P1 및 P2로 이메일이 전송됩니다.

P1은 첫 번째 날에 이메일을 두 번 연 다음 두 번째 날에 세 번 엽니다.

반면 P2는 첫 번째 날에 이메일을 한 번 열고 다음 날 다시 열지 않습니다.
다음은 전송된 이메일에 대한 프로필의 상호 작용을 시각적으로 표현한 것입니다.

<table> 
 <thead> 
  <tr> 
   <th align="center"> <strong>일</strong> <br/> </th> 
   <th align="center"> <strong>열기</strong> <br/> </th> 
   <th align="center"> <strong>고유 열기 수</strong> <br/> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td align="center"> 1<br/>일 </td> 
   <td align="center"> 2 + 1 = 3<br/> </td> 
   <td align="center"> 1 + 1 = 2<br/> </td> 
  </tr> 
  <tr> 
   <td align="center"> 2<br/>일 </td> 
   <td align="center"> 3 + 0 = 3<br/> </td> 
   <td align="center"> 1 + 0 = 1<br/> </td> 
  </tr>
 </tbody> 
</table>

전체 고유 열기 수를 이해하려면 값 3을 제공하는 **[!UICONTROL 고유 열기]**&#x200B;의 행 수를 합해야 합니다. 그러나 이메일이 2개의 프로필로만 타겟팅되었으므로 공개 비율은 150%로 표시되어야 합니다.

100보다 큰 백분율을 얻지 않기 위해 **[!UICONTROL 고유 열기 수]**&#x200B;의 정의는 열린 고유 브로드로그 수로 유지됩니다. 이 경우 P1이 1일과 2일에 이메일을 열었더라도 고유한 열림은 여전히 1입니다.

이렇게 하면 다음 테이블이 표시됩니다.

<table> 
 <thead> 
  <tr> 
   <th align="center"> <strong></strong> <br/> </th> 
   <th align="center"> <strong>열기</strong> <br/> </th> 
   <th align="center"> <strong>고유 열기 수</strong> <br/> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td align="center"> <strong>일 </strong><br/> </td> 
   <td align="center"> <strong> 6 </strong><br/> </td> 
   <td align="center"> <strong> 2</strong><br/> </td>
  </tr> 
  <tr> 
   <td align="center"> 1<br/>일 </td> 
   <td align="center"> 3<br/> </td> 
   <td align="center"> 2<br/> </td>
  </tr> 
  <tr> 
   <td align="center"> 2<br/>일 </td> 
   <td align="center"> 3<br/> </td> 
   <td align="center"> 1<br/> </td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>고유 개수는 HLL 기반 스케치를 기반으로 하며, 이는 큰 개수에서 약간의 부정확성을 야기할 수 있습니다.

## 열린 수가 데이터베이스 수와 일치하지 않습니다. {#open-counts-no-match-database}

이는 **[!UICONTROL 열기]** 작업을 추적할 수 없는 경우에도 열림 추적을 위해 동적 보고에서 추론이 사용되기 때문일 수 있습니다.

예를 들어 사용자가 클라이언트에서 이미지를 사용하지 않도록 설정하고 이메일의 링크를 클릭하면 **[!UICONTROL 열기]**&#x200B;가 데이터베이스에 의해 추적되지 않을 수 있지만 **[!UICONTROL 클릭]**&#x200B;은(는) 추적됩니다.

따라서 **[!UICONTROL Open]** 추적 로그 수가 데이터베이스에서 같은 수를 가질 수 없습니다.

이러한 항목이 **(으)로 추가됩니다. &quot;전자 메일 클릭은 전자 메일 열기를 의미합니다.&quot;**.

>[!NOTE]
>
>고유 카운트는 HLL 기반 스케치를 기반으로 하므로 카운트 간 사소한 불일치가 발생할 수 있습니다.

## 반복/트랜잭션 게재의 카운트는 어떻게 계산됩니까? {#counts-recurring-deliveries}

반복 및 트랜잭션 게재로 작업할 때 카운트는 상위 및 하위 게재 모두에 연결됩니다.
1일(RC1), 2일(RC2) 및 3일(RC3)에 매일 실행되도록 설정된 **R1**(이)라는 반복 게재의 예를 사용할 수 있습니다.
한 사람만 모든 하위 분만을 여러 번 열었다고 가정해 보겠습니다. 이 경우 개별 반복 하위 게재는 **[!UICONTROL 열기]** 수를 각각에 대해 1로 표시합니다.
그러나 동일한 사람이 모든 게재를 클릭했으므로 상위 반복 게재는 **[!UICONTROL 고유 열기]**&#x200B;도 1로 갖게 됩니다.

보고서는 다음과 같아야 합니다.

<table> 
 <thead> 
  <tr> 
   <th align="center"> <strong>배달</strong> <br/> </th> 
   <th align="center"> <strong>전송됨</strong> <br/> </th> 
   <th align="center"> <strong>배달됨</strong> <br/> </th>
   <th align="center"> <strong>열기</strong> <br/> </th> 
   <th align="center"> <strong>고유 열기 수</strong> <br/> </th>
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td align="center"> <strong>R1</strong><br/> </td> 
   <td align="center"> <strong>100</strong><br/> </td> 
   <td align="center"> <strong>90</strong><br/> </td> 
   <td align="center"> <strong>10</strong><br/> </td> 
   <td align="center"> <strong>3</strong><br/> </td> 
  </tr> 
  <tr> 
   <td align="center"> RC1<br/> </td> 
   <td align="center"> 20<br/> </td> 
   <td align="center"> 20<br/> </td> 
   <td align="center"> 6<br/> </td> 
   <td align="center"> 1<br/> </td> 
  </tr>
    <tr> 
   <td align="center"> RC2<br/> </td> 
   <td align="center"> 40<br/> </td> 
   <td align="center"> 30<br/> </td> 
   <td align="center"> 2<br/> </td> 
   <td align="center"> 1<br/> </td> 
  </tr> 
    <tr> 
   <td align="center"> RC3<br/> </td> 
   <td align="center"> 40<br/> </td> 
   <td align="center"> 40<br/> </td> 
   <td align="center"> 2<br/> </td> 
   <td align="center"> 1<br/> </td> 
  </tr> 
 </tbody> 
</table>

## 내 보고서 테이블에 있는 색깔의 의미는 무엇입니까? {#reports-color-signification}

보고서에 표시된 색상은 임의화되어 개인화할 수 없습니다. 진행률 표시줄을 나타내며 보고서에 도달한 최대 값을 더 잘 강조 표시할 수 있도록 표시됩니다.

아래 예에서 셀의 값은 100%이므로 셀의 색상은 동일합니다.

![](assets/troubleshooting_1.png)

**[!UICONTROL 조건부 서식]**&#x200B;을 사용자 지정으로 변경하면 값이 상한값에 도달하면 셀이 더 녹색이 됩니다. 반면, 하한에 도달하면 더 붉어집니다.

예를 들어 **[!UICONTROL 상한]**&#x200B;을 500으로 설정하고 **[!UICONTROL 하한]**&#x200B;을 0으로 설정합니다.

![](assets/troubleshooting_2.png)

## 보고서에 N/A 값이 표시되는 이유는 무엇입니까?

![](assets/troubleshooting_3.png)

**N/A** 값이 동적 보고서에 표시될 수 있습니다. 다음과 같은 세 가지 이유로 표시될 수 있습니다.

* 게재가 삭제되었으며 결과에 불일치를 일으키지 않도록 여기에 **N/A**(으)로 표시됩니다.
* **[!UICONTROL 트랜잭션 게재]** 차원을 보고서에 끌어다 놓을 때 **N/A** 값이 결과로 나타날 수 있습니다. 이 문제는 동적 보고서가 트랜잭션이 아닌 경우에도 모든 게재를 가져오기 때문에 발생합니다. 이 문제는 **[!UICONTROL 배달]** 차원을 보고서에 끌어다 놓을 때도 발생할 수 있지만, 이 경우 **N/A** 값이 트랜잭션 게재를 나타냅니다.
* 차원이 차원과 관련이 없는 지표와 함께 사용되는 경우. 아래 예에서는 이 게재에서 **[!UICONTROL 클릭]** 수가 0으로 설정되어 있어도 분류가 **[!UICONTROL 추적 URL]** 차원과 함께 추가됩니다.

  ![](assets/troubleshooting_4.png)

## 사용자 지정 대상 매핑을 사용할 때 게재 보고서에 불완전한 데이터가 표시됨

게재에서 가져온 사용자 지정 대상 매핑을 사용하고 다른 보고서에 데이터가 표시되지 않는 경우 해당 대상 매핑에 대한 보고 보강이 생성되지 않았을 수 있습니다.

이 문제를 해결하려면

* XML에서 Target 매핑을 가져온 후 보고 데이터 보강 또한 가져와야 합니다.

* Target 매핑을 가져오는 대신 Adobe Campaign 웹 사용자 인터페이스에서 직접 만들어 보고 데이터 보강 기능을 자동으로 만들 수 있습니다.

## 열 헤더 번호와 행 합계 간의 불일치

다음과 같은 경우 열 헤더 번호와 모든 행의 합계 간에 불일치가 예상됩니다.

* **고유 지표**: 고유한 지표를 사용하면 행 수의 단순 합계가 아닌 수신자 ID를 기반으로 하므로 헤더에 표시된 총 개수를 변경할 수 있습니다. 따라서 단일 프로필이 다양한 차원에서 수많은 이벤트를 트리거하여 데이터 세트에 여러 행이 발생할 수 있습니다. 그러나 헤더에서 각 프로필은 한 번만 카운트됩니다.

  예:

   * 프로필 A가 서로 다른 3일에 이메일을 여는 경우 일별 분류는 A를 3개의 행으로 표시하지만 헤더에서 A는 1로 계산됩니다.

   * 프로필 A가 같은 날 이메일에서 서로 다른 세 개의 링크를 클릭하는 경우, 추적 URL을 통한 분류는 세 행에 A를 표시하지만, 헤더에서 A는 1로 계산됩니다. 장치 및 브라우저별 분류에도 동일하게 적용됩니다.

* **열린 지표**: 열린 횟수는 실제 열린 이벤트와 고유 클릭 이벤트(수신자 ID당)의 합계를 집계하여 결정됩니다. 단, 열린 이벤트가 없으면 이메일 링크를 클릭할 수 없으므로 열린 이벤트가 발생하지 않은 경우는 제외합니다.

  예:

   * 프로필 A가 추적된 이메일을 열면(URL U1 포함) URL이 null로 표시되어 있는 열기 이벤트로 등록됩니다. 나중에 U1을 클릭하면 클릭 이벤트가 생성됩니다. A가 U1을 클릭하는 것도 오픈 이벤트로 계산되지만, U1에 대한 특정 오픈 이벤트는 없습니다. 따라서 A는 열린 고유 카운트에서 한 번만 카운트됩니다.

   * 프로필 R은 1일에 이메일을 열어 열기 이벤트를 등록하고 링크를 클릭합니다. 이후 2일 동안 R은 이메일을 다시 열고 링크를 다시 클릭하여 매일 클릭 이벤트를 생성합니다. R의 참여는 미결 번호에서 매일 추적되지만, R은 열 헤더에서 고유 참여에 초점을 맞춰 한 번만 카운트됩니다.

* **무효화된 이벤트**: 보고서에서 무효화된 이벤트는 처음에 성공으로 표시되었지만 다시 시도 후 최종적으로 실패한 게재 시도를 의미합니다. 이는 -1의 수로 표시됩니다. 혼동을 방지하기 위해 이러한 음수 카운트는 표시된 게재 지표 번호에서 제외됩니다. 따라서 게재 지표에 대한 모든 행의 합계가 열 헤더 번호와 일치하지 않을 수 있습니다.
