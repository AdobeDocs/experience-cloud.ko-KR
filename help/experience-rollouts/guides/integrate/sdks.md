---
title: SDK
description: Adobe Experience Rollouts의 SDK 아키텍처 및 Android에서 사용할 수 있는 모바일 SDK 확장에 대해 알아봅니다.
exl-id: 110a440d-b52a-4e1e-a94f-86f9741a223a
source-git-commit: fcb1d36fc92b3954a902d818a98f579672c577e9
workflow-type: tm+mt
source-wordcount: '172'
ht-degree: 3%

---

# SDK {#sdks}

Experience Rollouts는 기능 플래그를 애플리케이션에 통합하기 위한 SDK를 제공합니다. 이 페이지에서는 SDK 아키텍처 및 사용 가능한 옵션에 대해 설명합니다.

## SDK 아키텍처 {#architecture}

모든 Experience Rollouts SDK는 동일한 핵심 아키텍처를 공유합니다.

* **초기화** — SDK이 시작 시 구성되어 있으며 Experience Rollouts 서비스에 등록됩니다.
* **기능 검색** — SDK은 기능 플래그 데이터를 검색하고 플래그를 로컬로 평가합니다.
* **캐싱** — SDK은 기능 플래그 데이터를 캐시하고 TTL(Configurable Polling Interval)에 새로 고칩니다.
* **오류 처리** — 서비스를 사용할 수 없는 경우 SDK은 로컬 캐시에서 기능 플래그 평가를 계속 제공합니다.

## 사용 가능한 SDK {#available-sdks}

### Android 확장 {#android-extension}

Android용 Experience Rollout 확장 기능은 Adobe Experience Platform Mobile SDK과 통합됩니다.

설치 지침은 [Android 확장 통합 안내서](../sdk-releases/android/android-extension-integration-guide.md)를 참조하십시오.

>[!NOTE]
>
>웹 및 기타 모바일 플랫폼을 위한 추가 SDK 옵션이 준비 중이며 곧 제공될 예정입니다. 조기 액세스 지침은 Adobe 담당자에게 문의하십시오.

## 참조 - {#see-also}

* [Android 확장 통합 안내서](../sdk-releases/android/android-extension-integration-guide.md)
* [웹 서비스](web-services.md)
* [통합 단계](integration-steps.md)
