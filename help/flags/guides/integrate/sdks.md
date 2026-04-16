---
title: SDK
description: 플래그의 SDK 아키텍처와 사용 가능한 AEP Web SDK 및 AEP Mobile SDK 확장 기능에 대해 알아봅니다.
hide: true
exl-id: 110a440d-b52a-4e1e-a94f-86f9741a223a
source-git-commit: b3e13a42c19eb7b8b7d5d402bf9a56f89f573044
workflow-type: tm+mt
source-wordcount: '193'
ht-degree: 4%

---

# SDK {#sdks}

플래그는 기능 플래그를 애플리케이션에 통합하는 SDK를 제공합니다. 플래그는 AEP Web SDK 및 AEP Mobile SDK을 통해 배포됩니다.

## SDK 아키텍처 {#architecture}

모든 플래그 SDK는 동일한 핵심 아키텍처를 공유합니다.

* **초기화** — SDK이 시작 시 구성되어 있으며 Flags 서비스에 등록됩니다.
* **기능 검색** — SDK은 기능 플래그 데이터를 검색하고 플래그를 로컬로 평가합니다.
* **캐싱** — SDK은 기능 플래그 데이터를 캐시하고 TTL(Configurable Polling Interval)에 새로 고칩니다.
* **오류 처리** — 서비스를 사용할 수 없는 경우 SDK은 로컬 캐시에서 기능 플래그 평가를 계속 제공합니다.

## 사용 가능한 SDK {#available-sdks}

### AEP 웹 SDK {#web-sdk}

웹용 Flags 확장은 Adobe Experience Platform 웹 SDK과 통합되어 웹 애플리케이션에서 플래그를 평가할 수 있습니다.

### Android 확장 {#android-extension}

Android용 플래그 확장은 Adobe Experience Platform Mobile SDK과 통합됩니다.

설치 지침은 [Android 확장 통합 안내서](../sdk-releases/android/android-extension-integration-guide.md)를 참조하십시오.

### iOS 확장 {#ios-extension}

iOS용 플래그 확장은 Adobe Experience Platform Mobile SDK과 통합됩니다.

설치 지침은 [iOS 확장 통합 안내서](../sdk-releases/ios/ios-extension-integration-guide.md)를 참조하십시오.

## 참조 - {#see-also}

* [Android 확장 통합 안내서](../sdk-releases/android/android-extension-integration-guide.md)
* [웹 서비스](web-services.md)
* [통합 단계](integration-steps.md)

<!-- -->
