---
title: 앱의 경험 롤아웃 통합
description: 웹 서비스, 웹 속성, 모바일 앱 또는 데스크탑 애플리케이션이든 관계없이 Adobe Experience Rollouts를 애플리케이션에 통합하는 방법을 알아봅니다.
source-git-commit: 5dfb2fad7d04fc7f681337195de9c26e8aa26a09
workflow-type: tm+mt
source-wordcount: '161'
ht-degree: 0%

---


# 앱의 경험 롤아웃 통합 {#integrate}

이 섹션에서는 모든 경험 롤아웃 클라이언트에 대한 통합 지침을 애플리케이션 유형별로 정리하여 제공합니다.

## 통합 경로 선택 {#choose}

애플리케이션 유형과 일치하는 안내서를 선택합니다.

1. [시작 안내서](startup-guide.md) — 모든 통합 단계에 대한 높은 수준의 개요를 보려면 여기에서 시작하십시오.
2. [데스크톱 응용 프로그램](desktop-applications.md) — 데스크톱 앱용 Direct REST API 통합
3. [모바일 애플리케이션](mobile-applications.md) — 모바일 앱용 REST API 통합
4. [웹 응용 프로그램](web-applications.md) — 웹 속성에 대한 REST API 통합
5. [웹 서비스](web-services.md) — 백 엔드 서비스를 위한 서버측 SDK 통합
6. [SDK](sdks.md) — SDK 아키텍처, 사전 요구 사항 및 사용 가능한 SDK
7. [통합 단계](integration-steps.md) - 자세한 단계별 통합 지침

## 애플리케이션 유형 개요 {#overview}

| 애플리케이션 유형 | 권장 통합 |
|---|---|
| **웹 서비스/백 엔드** | Java SDK 또는 Node.js SDK |
| **웹 응용 프로그램** | REST API - 기능 API V3 |
| **모바일 응용 프로그램** | REST API - 기능 API V3 |
| **데스크톱 응용 프로그램** | REST API - 기능 API V2 |
