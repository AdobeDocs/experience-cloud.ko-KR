---
title: 시작 안내서
description: 액세스 요청에서 첫 번째 기능 플래그 만들기에 이르기까지, 다음 단계에 따라 애플리케이션을 Adobe Experience 롤아웃과 통합합니다.
exl-id: 7aa09535-45fa-4ddf-9e3f-a23f8a8ee666
source-git-commit: 2a946868f58e25f8aafbf3ccfcf6571e7d0d8d20
workflow-type: tm+mt
source-wordcount: '286'
ht-degree: 1%

---

# 시작 안내서 {#startup-guide}

다음 단계에 따라 경험 롤아웃을 애플리케이션에 통합합니다.

## 1단계: 액세스 요청 {#step-1-access}

경험 롤아웃 콘솔에 대한 액세스를 요청하고 팀에 참여합니다. 단계별 지침은 [액세스 요청](../console/request-access.md)을 참조하십시오.

## 2단계: 애플리케이션 온보드 {#step-2-onboard}

액세스 권한을 얻은 후 Experience Rollouts 콘솔에 로그인하고 애플리케이션이 팀 아래에 나열되는지 확인합니다. 그렇지 않은 경우 팀 관리자에게 추가하도록 요청하십시오. [응용 프로그램 온보딩](../applications/onboard-your-application.md)을 참조하세요.

온보딩 전에 다음 사항을 준비하십시오.

| 요구 사항 | 세부 사항 |
|---|---|
| **응용 프로그램 ID** | Experience Rollouts API를 호출할 때 사용되는 고유 클라이언트 식별자입니다. 사용 가능한 경우 애플리케이션의 기존 클라이언트 ID를 사용합니다. |
| **서버측 클라이언트** | 서버측 SDK과 통합하는 경우 적절한 권한이 있는 관리 클라이언트 ID가 필요합니다. |
| **데스크톱 클라이언트** | 클라이언트 ID 대신 제품 코드와 제품 버전을 사용할 수 있습니다. |

## 3단계: 자격 증명 가져오기 {#step-3-credentials}

서버측 SDK을 통해 통합하는 경우 서비스 토큰 클라이언트 ID가 필요합니다. SDK에서 API를 호출하려면 먼저 경험 롤아웃 지원 센터에 문의하여 클라이언트 ID를 허용 목록에추가된으로 받으십시오.

## 4단계: SDK을 사용하여 통합 {#step-4-integrate}

응용 프로그램 유형에 대해 [통합 단계](integration-steps.md)를 따르십시오. 스택에 맞는 경로를 선택합니다.

* **웹 서비스** → Java SDK 또는 Node.js SDK
* **웹 및 모바일 앱** → Web SDK 또는 모바일 SDK(준비 중)
* **데스크톱 앱** → SDK(준비 중)

## 5단계: 첫 번째 기능 플래그 만들기 및 테스트 {#step-5-feature-flag}

통합이 완료되면 콘솔에서 첫 번째 기능 플래그를 만들고 테스트합니다.

* [첫 번째 기능 플래그 만들기](../feature-flags/create-your-first-feature-flag.md)

## 참조 - {#see-also}

* [앱의 경험 롤아웃 통합](integrating-in-your-app.md)
* [통합 단계](integration-steps.md)
* [SDK](sdks.md)
