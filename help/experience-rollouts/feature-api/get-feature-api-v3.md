---
title: GET 기능 API V3
description: 웹 및 모바일 애플리케이션에 대한 기능 플래그를 검색하는 데 사용되는 경험 롤아웃 기능 API V3에 대한 API 참조입니다.
source-git-commit: 6ecedbfc6c7de392f214f3f8f2e71aa18e1bacb9
workflow-type: tm+mt
source-wordcount: '679'
ht-degree: 9%

---


# GET 기능 API V3 {#get-feature-api-v3}

기능 API V3은 웹 및 모바일 애플리케이션에서 기능 플래그를 검색하기 위한 기본 엔드포인트입니다. ID와 콘솔에 구성된 대상 규칙에 따라 사용자가 사용할 수 있는 기능 및 릴리스를 반환합니다.

**끝점:** `GET {HOST}/fg/api/v3/feature`

스테이지에 `https://p13-stage.adobe.io`을(를) 사용하고 프로덕션에 `https://p13n.adobe.io`을(를) 사용합니다.

## 요청 {#request}

### 요청 헤더 {#request-headers}

| Header | 유형 | 설명 | 필수 여부 |
|---|---|---|---|
| `x-api-key` | 문자열 | Adobe Developer Console에서 애플리케이션의 API 키. 스테이지 및 프로덕션에 대해 별도로 프로비저닝해야 합니다. | 예 |
| `Authorization` | 문자열 | 인증되지 않은 시나리오의 경우 **필요하지 않습니다**. 인증된 사용자에 대해 `Bearer <AccessToken>`을(를) 사용합니다. 서버측 SDK 캐싱 시나리오에 `Bearer <ServiceToken>`을(를) 사용합니다. | 아니요 |
| `x-adobe-uuid` | 문자열 | 고유 방문자 또는 장치 ID. 인증되지 않은 사용자에 대한 비율 롤아웃을 지원하고 세션 및 인증되지 않은 전환에서 인증되지 않은 전환으로 끈적임을 유지하는 데 사용됩니다. | 아니요 |

### 쿼리 매개변수 {#query-parameters}

| 매개변수 | 유형 | 설명 | 필수 여부 |
|---|---|---|---|
| `clientId` | 문자열 | 경험 롤아웃 콘솔에서 온보딩되는 애플리케이션의 클라이언트 ID입니다. | 예 |
| `ignore_rf` | 부울 | `true`이면 릴리스 플래그가 무시되고 클라이언트에 대한 모든 릴리스가 반환됩니다. 기본값: `false`. | 아니요 |
| `rf` | 문자열 | 릴리스 플래그. `ignore_rf`이(가) `false`인 경우에만 사용됩니다. | 아니요 |
| `meta` | 부울 | `true`이면 각 기능에 대한 메타데이터가 응답에 포함되어 있으며 값이 Base64로 인코딩된 키-값 쌍으로 반환됩니다. 기본값: `false`. | 아니요 |
| `userId` | 문자열 | 서비스 토큰이 필요합니다. 기능 플래그를 검색할 사용자의 GUID입니다. | 아니요 |
| *컨텍스트 매개 변수* | N/A | 위에 나열되지 않은 모든 쿼리 매개 변수는 컨텍스트 변수로 처리되며 대상 규칙을 평가하는 데 사용됩니다. 여러 값을 `?key1=val1&key2=val2`(으)로 전달합니다. 예: `?clientLanguage=ja_JP&contractCurrency=JPY`. | 아니요 |

## 응답 {#response}

### 응답 상태 코드 {#response-status}

| 상태 코드 | 설명 |
|---|---|
| `200 OK` | 응답 본문에서 반환된 기능 플래그 데이터. |
| `304 Not Modified` | 클라이언트가 전달한 ETag가 최신 서버 상태와 일치합니다. 이를 no-op로 처리 — 변경 내용을 적용하지 않습니다. |
| `400 Bad Request` | `clientId`이(가) 온보딩되지 않았거나 요청이 잘못되었습니다. |
| `403 Forbidden` | API 키가 잘못되었거나 애플리케이션이 Adobe Developer Console에서 Experience Rollouts API를 구독하지 않습니다. |

### 응답 헤더 {#response-headers}

| Header | 설명 |
|---|---|
| `x-request-id` | 디버깅에 대한 고유한 요청 식별자입니다. 모든 지원 요청에 이 항목을 포함하십시오. |
| `ETag` | 이 사용자 기능의 현재 서버 상태를 나타내는 토큰입니다. 후속 요청에서 이 값을 `If-None-Match`(으)로 전달합니다. 상태가 변경되지 않은 경우 API는 `304`을(를) 반환합니다. |
| `x-adobe-fg-poll-interval` | 클라이언트의 로컬 캐시에 대한 TTL(초)입니다. 이 간격이 경과한 후에만 API를 다시 호출합니다. |

### 응답 본문 {#response-body}

응답은 다음과 같은 최상위 필드가 있는 JSON 개체입니다.

| 필드 | 유형 | 설명 |
|---|---|---|
| `api_version` | 문자열 | API 버전. 내부 필드 — 처리가 필요하지 않습니다. |
| `json_version` | 문자열 | JSON 스키마 버전. 내부 필드 — 처리가 필요하지 않습니다. |
| `ttl` | 정수 | 캐시 TTL(초). `x-adobe-fg-poll-interval` 응답 헤더와 같은 값입니다. 기본값: 300. |
| `caching_enabled` | 부울 | `true`이면 기능 평가가 클라이언트에서 로컬로 수행됩니다. `false`이면 각 요청에 대해 서버측에서 평가가 수행됩니다. |
| `client_analytics_params` | 오브젝트 | 애플리케이션에 대한 Analytics 구성. 아래의 [client_analytics_params 필드](#client-analytics-params)를 참조하십시오. |
| `releases` | 배열 | 사용자가 사용할 수 있는 릴리스 및 기능 플래그 목록입니다. 아래의 [릴리스 필드](#releases-fields)을(를) 참조하십시오. |

#### client_analytics_params 필드 {#client-analytics-params}

| 필드 | 설명 |
|---|---|
| `app_id` | 애플리케이션의 숫자 ID입니다. |
| `safe_event_required` | 이 클라이언트에 대해 리타겟팅 이벤트가 활성화된 경우 `true`. |
| `analytics_required` | 항상 V3 응답에서 `false`을(를) 사용합니다. |

#### 릴리스 필드 {#releases-fields}

| 필드 | 설명 |
|---|---|
| `release_name` | 사용자가 사용할 수 있는 릴리스 또는 기능 그룹의 이름입니다. |
| `bit_index` | 릴리스 비트 색인. 음수 값은 전체 롤아웃 상태를 나타냅니다. |
| `features` | 사용자가 사용할 수 있는 기능 플래그 키 배열. 사용자가 자격이 있고 플래그가 활성화 상태인 경우에만 기능 키가 반환됩니다. 애플리케이션 논리를 작성하는 데 필요한 기본 필드입니다. |
| `meta` | 기능과 연결된 선택적 Base64 인코딩 메타데이터입니다. 사용하기 전에 디코딩합니다. |
| `release_analytics_params` | 각 적격 기능에 대한 분석 메타데이터 개체의 배열입니다. 아래의 [release_analytics_params 필드](#release-analytics-params)를 참조하십시오. 컨트롤 그룹 시나리오에서 `features`이(가) 비어 있습니다. |

#### release_analytics_params 필드 {#release-analytics-params}

| 필드 | 유형 | 설명 |
|---|---|---|
| `app_id` | 정수 | 애플리케이션 ID. |
| `release_id` | 정수 | 릴리스 ID. |
| `bit_index` | 정수 | 릴리스 비트 인덱스. 사용하지 않음. |
| `variant_id` | 정수 | 사용자가 컨트롤 그룹에 있으면 `0`이고, 그렇지 않으면 0이 아닙니다. |
| `feature_id` | 정수 | 내부 기능 ID. |
| `f_key` | 문자열 | 기능 플래그 키. |

## 샘플 요청 및 응답 {#sample}

### 샘플 요청 {#sample-request}

```http
GET /fg/api/v3/feature?clientId=MyWebApp&meta=true HTTP/1.1
Host: p13n.adobe.io
Authorization: Bearer <ACCESS_TOKEN>
x-api-key: <YOUR_API_KEY>
If-None-Match: <ETAG>
```

### 샘플 응답 — 테스트 그룹의 사용자 {#sample-response-test}

```json
{
  "api_version": "0.1",
  "json_version": "0.1",
  "clients": {
    "MyWebApp": {
      "analyticsVersion": "2.0",
      "client_analytics_params": {
        "app_id": 1378,
        "safe_event_required": false,
        "analytics_required": false
      },
      "releases": [
        {
          "bit_index": -160,
          "release_name": "||features||",
          "features": ["ff1", "ff2", "ff3"],
          "release_analytics_params": [
            {
              "app_id": 1378,
              "release_id": -1,
              "bit_index": -160,
              "variant_id": 10040476,
              "feature_id": 26059,
              "f_key": "ff1",
              "analytics_required": true
            }
          ]
        }
      ]
    }
  },
  "ttl": 60
}
```

### 샘플 응답 — 컨트롤 그룹의 사용자 {#sample-response-control}

사용자가 컨트롤 그룹에 있는 경우 `features` 배열은 비어 있고 `variant_id`은(는) `0`입니다.

```json
{
  "api_version": "0.1",
  "json_version": "0.1",
  "clients": {
    "MyWebApp": {
      "releases": [
        {
          "bit_index": -160,
          "release_name": "||features||",
          "features": [],
          "release_analytics_params": [
            {
              "app_id": 1378,
              "release_id": -1,
              "bit_index": -160,
              "variant_id": 0,
              "feature_id": 26059,
              "f_key": "ff1"
            }
          ]
        }
      ]
    }
  },
  "ttl": 60
}
```

## 참조 - {#see-also}

* [GET 기능 API V2](get-feature-api-v2.md)
* [웹 애플리케이션](../guides/integrate/web-applications.md)
* [모바일 애플리케이션](../guides/integrate/mobile-applications.md)
* [통합 단계](../guides/integrate/integration-steps.md)
