---
title: 통합 단계
description: 애플리케이션 유형에 대한 통합 단계에 따라 Adobe Experience 롤아웃을 웹 서비스, 웹 또는 모바일 앱 또는 데스크탑 애플리케이션에 연결합니다.
source-git-commit: b82520eebe0070b5f76e0f7daeb2bb79a4bccca0
workflow-type: tm+mt
source-wordcount: '220'
ht-degree: 3%

---


# 통합 단계 {#integration-steps}

애플리케이션 유형과 일치하는 통합 경로를 선택합니다.

## 웹 서비스 {#web-services}

백엔드 서비스는 서버측 SDK을 사용하여 통합됩니다. 기술 스택에 사용할 SDK을 선택하십시오.

**Java**

설정, 종속성 구성 및 초기화에 대해서는 [Java SDK 통합 안내서](../sdk-releases/java/java-sdk-integration-guide.md)를 따르십시오.

**Node.js**

설정 및 초기화는 [Node.js SDK 통합 안내서](../sdk-releases/nodejs/nodejs-sdk-integration-guide.md)를 따르십시오.

**다른 언어**

스택이 위에 나열되지 않은 경우 **기능 API V3**&#x200B;과(와) 직접 통합하십시오(이 안내서의 기능 API 섹션 참조). 지침이 필요한 경우 경험 롤아웃 지원 센터에 문의하십시오.

## 웹 및 모바일 애플리케이션 {#web-mobile}

웹 및 모바일 응용 프로그램에서 **기능 API V3**&#x200B;을(를) 호출하여 현재 사용자에 대한 기능 플래그를 검색하고 응용 프로그램에 조건부 논리를 적용합니다.

전체 API 참조는 이 안내서의 기능 API 섹션에서 **GET 기능 API V3**&#x200B;을(를) 참조하십시오.

## 데스크탑 애플리케이션 {#desktop}

데스크톱 응용 프로그램에서 기능 플래그를 검색하려면 **기능 API V2**&#x200B;을(를) 호출합니다.

전체 API 참조는 이 안내서의 기능 API 섹션에서 **GET 기능 API V2**&#x200B;를 참조하십시오.

>[!IMPORTANT]
>
>데스크탑 클라이언트는 API 응답의 TTL 값을 준수해야 하며 API를 사용할 수 없는 경우 정상적인 오류 처리를 구현해야 합니다. 요구 사항은 [데스크톱 응용 프로그램](desktop-applications.md)을 참조하십시오.

## 참조 - {#see-also}

* [시작 안내서](startup-guide.md)
* [SDK](sdks.md)
* [웹 서비스](web-services.md)
* [데스크탑 애플리케이션](desktop-applications.md)
