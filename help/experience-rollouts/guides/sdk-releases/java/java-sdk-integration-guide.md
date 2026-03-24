---
title: Java SDK 통합 안내서
description: Experience Rollouts Java SDK을 백엔드 서비스에 통합하여 기능 플래그를 검색하고 평가하는 방법을 알아봅니다.
source-git-commit: 9bfe0e55e89c1d7fbd77cde63831a6a186820e24
workflow-type: tm+mt
source-wordcount: '426'
ht-degree: 1%

---


# Java SDK 통합 안내서 {#java-sdk-integration-guide}

Experience Rollouts Java SDK은 모든 요청에 대해 동기 API 호출 없이 기능 플래그 데이터를 로컬로 캐시하고 플래그를 평가하는 서버측 라이브러리입니다. 이 안내서에서는 현재 SDK(4.x)를 다룹니다.

## 전제 조건 {#prerequisites}

Java SDK을 통합하기 전에 다음을 확인합니다.

* JDK 11 이상(SDK 버전 3.0.0 이상 필요, 이전 버전은 JDK 8+ 지원)
* Maven 기반 빌드 시스템
* Adobe Developer Console 프로젝트의 **API 키** 및 **서비스 토큰** 클라이언트 ID — [API 애플리케이션 구독](../../integrate/subscribe-to-api-application.md) 참조
* **응용 프로그램 클라이언트 ID**&#x200B;이(가) Experience Rollouts 콘솔에 등록되었습니다. [응용 프로그램 온보드](../../applications/onboard-your-application.md)를 참조하십시오.

## Maven 종속성 추가 {#maven-dependency}

Experience Rollouts Java SDK을 프로젝트의 `pom.xml`에 추가합니다.

```xml
<dependency>
  <groupId>com.adobe.cloudtech</groupId>
  <artifactId>fg-client-sdk</artifactId>
  <version>4.0.6</version>
</dependency>
```

## SDK 초기화 {#initialize}

`FloodgateClient.createInstance()`을(를) 사용하여 응용 프로그램 시작 시 SDK이 한 번 초기화됩니다. 메서드는 구성 빌더로 빌드하는 `FloodgateConfiguration` 개체를 사용합니다.

### 서비스 토큰 콜백 구현 {#service-token-callback}

SDK은 런타임 시 콜백 인터페이스를 사용하여 새 서비스 토큰을 검색합니다.

```java
private class FgConfigCallBack implements FGConfigBaseCallBack {

  @Override
  public String getIMSServiceToken() {
    // Fetch and return a valid service token
  }

  @Override
  public boolean isAnalyticsEnabled() {
    return false; // Set to true to enable analytics
  }
}
```

### 구성 개체 만들기 {#configuration}

구성 빌더를 사용하여 SDK을 설정합니다.

```java
FloodgateConfiguration configuration = FloodgateConfiguration.FloodgateConfigurationBuilder
    .aFloodgateConfiguration(
        FgEnv.PRD,                   // Use FgEnv.STG for Stage
        "<YOUR_API_KEY>",
        Set.of("<CLIENT_ID_1>", "<CLIENT_ID_2>"),
        new FgConfigCallBack(),
        CallType.ASYNC
    )
    .withRetryPolicy(retryPolicy)    // Optional: defaults to 5 retries, 10s interval
    .build();
```

스테이징 환경에는 `FgEnv.STG`을(를) 사용하고 프로덕션에는 `FgEnv.PRD`을(를) 사용합니다.

### 클라이언트 인스턴스 만들기 {#client-instance}

```java
FloodgateClient fgClient = FloodgateClient.createInstance(configuration);
```

## 기능 플래그 검색 {#retrieve-features}

### 인증된 사용자 {#authenticated-user}

IMS 액세스 토큰을 사용하여 현재 사용자에 대한 기능 플래그를 검색합니다.

```java
GetFeatureRequest request = GetFeatureRequestBuilder
    .aGetFeatureRequest("<CLIENT_ID>")
    .withAccessToken("<USER_ACCESS_TOKEN>")
    .withContext(context)
    .build();

FeaturesResponse[] features = fgClient.getFeatures(request);
```

### 익명 사용자 {#anonymous-user}

인증되지 않은 사용자의 경우 방문자 ID와 서비스 토큰을 전달합니다.

```java
GetFeatureRequest request = GetFeatureRequestBuilder
    .aGetFeatureRequest("<CLIENT_ID>")
    .withServiceToken("<SERVICE_TOKEN>")
    .withVisitorId("<VISITOR_ID>")
    .withContext(context)
    .build();

FeaturesResponse[] features = fgClient.getFeatures(request);
```

### 특정 기능 플래그 또는 릴리스 검색 {#specific-feature}

키로 단일 기능 플래그를 검색하려면 다음을 수행합니다.

```java
GetFeatureRequest request = GetFeatureRequestBuilder
    .aGetFeatureRequest("<CLIENT_ID>")
    .withAccessToken("<ACCESS_TOKEN>")
    .withFeatureKey("<FEATURE_KEY>")
    .build();
```

릴리스 키로 검색하려면 `.withFeatureKey()`을(를) `.withReleaseKey()`(으)로 바꾸십시오.

## 기능이 활성화되어 있는지 확인 {#check-feature}

```java
boolean isEnabled = FloodgateClient.isFeatureEnabled(features, "MY_FEATURE_FLAG");

if (isEnabled) {
  // Serve the new experience
} else {
  // Serve the default experience
}
```

릴리스 기반 검사의 경우:

```java
boolean isEnabled = FloodgateClient.isFeatureEnabled(features, "MY_RELEASE", "MY_FEATURE_FLAG");
```

## 캐시 관리 {#cache-management}

SDK은 기능 플래그 데이터를 캐시하고 콘솔에서 애플리케이션별로 설정된 폴링 간격에 따라 새로 고칩니다. 온디맨드 캐시 새로 고침을 트리거하려면

```java
fgClient.refreshClientCache("<CLIENT_ID>");
```

### 캐시 불가능 클라이언트 {#non-cacheable}

캐시 불가능 클라이언트의 경우 `getFeature()`에서 매번 라이브 API 호출을 수행합니다. SDK은 백그라운드 폴링을 계속 수행하고 클라이언트가 캐시 가능해지면 캐시 기반 서비스로 전환합니다. SDK 버전 0.8 이상에서 지원됩니다.

## 구성 옵션 {#configuration-options}

빌더에서 다음 선택적 구성 메서드를 사용할 수 있습니다.

| 옵션 | 메서드 | 설명 |
|---|---|---|
| 항상 캐시 사용 | `.alwaysCache()` | API에서 캐싱 응답을 우회합니다. 대상 규칙이 없는 플래그에 사용합니다. |
| 캐싱 비활성화 | `.neverCache()` | 기본 캐싱을 비활성화합니다. 사용자 지정 캐시 새로 고침 논리에 유용합니다. |
| 사용자 지정 HTTP 클라이언트 | `.withHttpClient(client)` | 자체 HTTP 클라이언트 사용 |
| 사용자 지정 Executor | `.withScheduledExecutorService(executor)` | 백그라운드 폴링을 위해 자체 예약된 Executor 사용 |
| 컨트롤 그룹 포함 | `.includeControlGroup()` | 기능 응답에서 컨트롤 그룹 데이터 반환 |

## 오류 처리 {#error-handling}

SDK 예외를 catch하기 위해 `getFeatures()` 호출을 줄바꿈합니다.

```java
try {
  features = fgClient.getFeatures(request);
} catch (FgClientException e) {
  int statusCode = e.getStatusCode();
  // Handle error and serve default experience
} catch (FgInitException e) {
  e.printStackTrace();
}
```

## 참조 - {#see-also}

* [Java SDK 릴리스 노트](java-sdk-release-notes.md)
* [SDK](../../integrate/sdks.md)
* [API 애플리케이션 구독](../../integrate/subscribe-to-api-application.md)
* [통합 단계](../../integrate/integration-steps.md)
