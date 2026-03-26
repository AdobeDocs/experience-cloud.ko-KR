---
title: 애플리케이션 온보드
description: 팀이 기능 플래그를 만들고 관리할 수 있도록 새 애플리케이션을 Adobe Experience Rollouts에 온보딩하는 방법을 알아봅니다.
exl-id: d88c27a5-f490-4504-9764-5e4ce98fdf20
source-git-commit: 454b5c719a5f8be82d1ed835da58bfca6316def2
workflow-type: tm+mt
source-wordcount: '219'
ht-degree: 1%

---

# 애플리케이션 온보드 {#onboard-your-application}

새 응용 프로그램을 추가하려면 **관리자** 역할이 있어야 합니다. 역할을 확인하거나 업데이트해야 하는 경우 팀 관리자에게 문의하십시오.

## 새 애플리케이션 추가 {#add-application}

1. Experience Rollouts 콘솔에 로그인하고 **관리자 > 응용 프로그램**(으)로 이동합니다.

   >[!NOTE]
   >
   >**새 응용 프로그램** 단추가 표시되지 않으면 올바른 팀에 속해 있는지, **관리자** 역할이 있는지 확인하십시오.

2. **새 응용 프로그램**&#x200B;을 선택합니다.

3. 응용 프로그램 유형(웹, 모바일, 데스크톱 또는 서비스)과 일치하는 **채널**&#x200B;을 선택하십시오.

4. 다음 정보를 제공합니다.

   | 필드 | 설명 |
   |---|---|
   | **응용 프로그램 ID** | 코드에서 경험 롤아웃을 호출할 때 사용되는 고유 식별자입니다. 애플리케이션의 클라이언트 ID를 사용합니다. |
   | **TTL** | 애플리케이션당 캐시를 새로 고치는 폴링 간격(초)입니다. 서버측 SDK에만 적용됩니다. |
   | **팀** | 이 애플리케이션을 소유 및 관리할 팀입니다. 이 팀의 멤버만 기능 플래그를 만들고 편집할 수 있습니다. |

5. **추가**&#x200B;를 선택합니다. 이제 애플리케이션이 등록되었으며 기능 플래그를 구성할 준비가 되었습니다.

## 다음 단계 {#next-steps}

애플리케이션이 온보딩되면 팀에서 기능 플래그를 만들 수 있습니다.

* [첫 번째 기능 플래그 만들기](../feature-flags/create-your-first-feature-flag.md)
* [앱의 경험 롤아웃 통합](../integrate/integrating-in-your-app.md)

## 참조 - {#see-also}

* [애플리케이션 관리](manage-applications.md)
* [콘솔에 로그인](../console/log-in-to-the-console.md)
