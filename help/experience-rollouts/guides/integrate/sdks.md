---
title: SDK
description: Adobe Experience 롤아웃의 SDK 아키텍처와 Java 및 Node.js에 사용 가능한 SDK에 대해 알아봅니다.
source-git-commit: b82520eebe0070b5f76e0f7daeb2bb79a4bccca0
workflow-type: tm+mt
source-wordcount: '386'
ht-degree: 2%

---


# SDK {#sdks}

Experience Rollouts는 백엔드 서비스 통합을 위한 서버측 SDK를 제공합니다. 이 페이지에서는 SDK 아키텍처 및 사용 가능한 옵션에 대해 설명합니다.

## SDK 아키텍처 {#architecture}

모든 Experience Rollouts SDK는 동일한 핵심 아키텍처를 공유합니다.

* **초기화** — 단일 개체를 반환하는 `createInstance()` 호출을 통해 SDK이 구성됩니다.
* **기능 검색** — `getFeatures()` 메서드는 SDK에서 기능 플래그 데이터를 검색합니다.
* **캐싱** — SDK은 Experience Rollouts 서비스의 응답을 캐시합니다. 캐시 관리자는 구성 가능한 폴링 간격(TTL)에서 캐시를 새로 고칩니다.
* **오류 처리** — 서비스가 503을 반환하는 경우 캐시 관리자는 기존의 캐시된 데이터를 유지하고 기능 플래그 평가를 계속 제공합니다. 마지막 호출(304) 이후 데이터가 변경되지 않았다면, 캐시는 업데이트되지 않는다.

## 전제 조건 {#prerequisites}

SDK을 통합하기 전에 다음을 확인하십시오.

1. **응용 프로그램 ID** — Experience Rollouts 콘솔에 온보딩된 각 응용 프로그램의 클라이언트 ID입니다.
2. **서비스 토큰** — SDK에서 백그라운드에서 Experience Rollouts API를 호출하는 데 사용됩니다.
3. **API 키** - API 인증을 위해 서비스 토큰과 함께 사용됩니다.

## 사용 가능한 SDK {#available-sdks}

### Java SDK {#java-sdk}

Java SDK은 Maven을 통해 배포됩니다. 통합할 프로젝트의 `pom.xml`에 종속성을 추가하십시오. 봄 기반 애플리케이션의 경우 Maven 종속성은 애플리케이션이 완전히 로드되기 전에 SDK 캐시를 자동으로 설정합니다.

Java SDK에 대한 주요 사양:

* **지원되는 JDK:** JDK 8 이상
* **캐시 불가능 클라이언트:** SDK 버전 0.8부터 지원됩니다. 캐시할 수 없는 클라이언트의 경우 `getFeature()`이(가) 캐시에서 읽는 대신 라이브 API를 호출합니다. SDK은 백그라운드에서 폴링을 계속 수행하고 클라이언트가 캐시 가능해지면 캐시 기반 서비스로 전환합니다.

설치 지침은 [Java SDK 통합 안내서](../sdk-releases/java/java-sdk-integration-guide.md)를 참조하십시오.

### Node.js SDK {#nodejs-sdk}

Node.js SDK은 npm을 통해 배포됩니다.

설치 지침은 [Node.js SDK 통합 안내서](../sdk-releases/nodejs/nodejs-sdk-integration-guide.md)를 참조하십시오.

## SDK과 REST API 간 선택 {#sdk-vs-api}

| 시나리오 | 권장 사항 |
|---|---|
| 백엔드 Java 또는 Node.js 서비스 | 자동 캐싱 및 간소화된 통합에 적절한 SDK 사용 |
| 기타 백엔드 언어 | 기능 API V3를 직접 사용 — 이 안내서의 기능 API 섹션 을 참조하십시오. |
| 웹 또는 모바일 애플리케이션 | 기능 API V3를 직접 사용 — 이 안내서의 기능 API 섹션 을 참조하십시오. |
| 데스크탑 애플리케이션 | 기능 API V2를 직접 사용 — 이 안내서의 기능 API 섹션 을 참조하십시오. |

## 참조 - {#see-also}

* [웹 서비스](web-services.md)
* [통합 단계](integration-steps.md)
* [Java SDK 통합 안내서](../sdk-releases/java/java-sdk-integration-guide.md)
* [Node.js SDK 통합 안내서](../sdk-releases/nodejs/nodejs-sdk-integration-guide.md)
