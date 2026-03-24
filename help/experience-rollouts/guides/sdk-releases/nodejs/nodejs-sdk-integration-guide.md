---
title: Node.js SDK 통합 안내서
description: Experience Rollouts Node.js SDK을 백엔드 서비스에 통합하여 기능 플래그를 검색하고 평가하는 방법에 대해 알아봅니다.
source-git-commit: 9bfe0e55e89c1d7fbd77cde63831a6a186820e24
workflow-type: tm+mt
source-wordcount: '254'
ht-degree: 1%

---


# Node.js SDK 통합 안내서 {#nodejs-sdk-integration-guide}

Experience Rollouts Node.js SDK 는 Node.js 서비스를 위한 서버측 라이브러리입니다. 기능 플래그 데이터를 로컬로 캐시하고 모든 요청에서 동기 API 호출 없이 플래그를 평가합니다.

>[!NOTE]
>
>Node.js SDK은 서버측에서만 사용하도록 설계되었습니다. 클라이언트측 웹 애플리케이션의 경우 기능 API V3 REST 엔드포인트를 직접 호출합니다.

## 전제 조건 {#prerequisites}

Node.js SDK을 통합하기 전에 다음을 확인하십시오.

* Node.js 서버측 응용 프로그램
* Adobe Developer Console을 통해 얻은 **API 키** 및 **서비스 토큰** — [API 애플리케이션 구독](../../integrate/subscribe-to-api-application.md) 참조
* **응용 프로그램 클라이언트 ID**&#x200B;이(가) Experience Rollouts 콘솔에 등록되었습니다. [응용 프로그램 온보드](../../applications/onboard-your-application.md)를 참조하십시오.

## SDK 설치 {#install}

프로젝트의 `package.json`에 SDK 추가:

```json
"@floodgate/fg-client-sdk": "~1.0.10"
```

그런 다음 코드에 필요합니다.

```javascript
const { floodgateClient } = require('@floodgate/fg-client-sdk');
```

## SDK 초기화 {#initialize}

응용 프로그램 시작 시 `createInstance()`을(를) 한 번 호출합니다.

```javascript
floodgateClient.createInstance(
  {
    adobeIoApiKey: "<YOUR_API_KEY>",
    clientIds: ["<CLIENT_ID_1>", "<CLIENT_ID_2>"],
    env: "PRD",    // Use "STG" for Stage
    featureRequestHttpParams: {
      timeout: 60 * 1000  // Optional: request timeout in ms
    },
    ingestAnalyticsHttpParams: {
      timeout: 5 * 1000   // Optional: analytics timeout in ms
    }
  },
  function(cb) {
    // Fetch a fresh service token from IMS and pass it in the callback
    cb(null, SERVICE_TOKEN);
  },
  function() {
    return true;  // Return false to disable analytics
  },
  function(response) {
    // Called when the SDK initializes successfully
    console.log("SDK initialized");
  },
  function(err) {
    // Called if initialization fails
    console.error("SDK init error:", err);
  }
);
```

## 기능 플래그 검색 {#retrieve-features}

기능 플래그는 콜백에서 비동기적으로 반환됩니다. 사용자 컨텍스트를 기반으로 적절한 방법을 선택합니다.

### 인증된 사용자 {#authenticated-user}

```javascript
floodgateClient.getFeatures(
  {
    userAccessToken: "<USER_ACCESS_TOKEN>",
    visitorId: "<VISITOR_ID>",
    clientId1: "<CLIENT_ID>",
    meta: true
  },
  function(err, features) {
    if (err) {
      // Handle error and serve default experience
      return;
    }
    const isEnabled = floodgateClient.isFeatureEnabled(features, "MY_FEATURE_FLAG");
    // Serve experience based on isEnabled
  }
);
```

### 익명 사용자 {#anonymous-user}

사용 가능한 사용자 액세스 토큰이 없는 경우 릴리스 플래그를 사용하거나 토큰을 생략하여 전체 롤아웃 릴리스를 받습니다.

```javascript
floodgateClient.getFeatures(
  {
    releaseFlag: "<RELEASE_FLAG>",
    visitorId: "<VISITOR_ID>",
    clientId1: "<CLIENT_ID>",
    meta: false
  },
  callback
);
```

### 기본 전체 롤아웃 릴리스 {#default-releases}

액세스 토큰과 릴리스 플래그가 제공되지 않으면 SDK에서 **전체 롤아웃** 또는 **기준선** 상태로 기능을 반환합니다.

```javascript
floodgateClient.getFeatures(
  {
    clientId1: "<CLIENT_ID>",
    visitorId: "<VISITOR_ID>",
    meta: false
  },
  callback
);
```

## 기능이 활성화되어 있는지 확인 {#check-feature}

```javascript
const isEnabled = floodgateClient.isFeatureEnabled(features, "MY_FEATURE_FLAG");

if (isEnabled) {
  // Serve the new experience
} else {
  // Serve the default experience
}
```

## 디버그 로깅 활성화 {#debug-logging}

자세한 SDK 로그를 사용하려면 `createInstance()`을(를) 호출할 때 디버그 수준 로거 인스턴스를 전달합니다.

```javascript
const bunyan = require('bunyan');
const logger = bunyan.createLogger({ name: "fg", sourceType: "SDK", level: "debug" });

floodgateClient.createInstance(
  { ..., log: logger },
  ...
);
```

## 참조 - {#see-also}

* [Node.js SDK 릴리스 노트](nodejs-sdk-release-notes.md)
* [SDK](../../integrate/sdks.md)
* [API 애플리케이션 구독](../../integrate/subscribe-to-api-application.md)
* [통합 단계](../../integrate/integration-steps.md)
