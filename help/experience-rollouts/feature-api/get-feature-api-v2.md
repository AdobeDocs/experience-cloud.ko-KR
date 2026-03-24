---
title: GET 기능 API V2
description: 데스크탑 애플리케이션에 대한 기능 플래그를 검색하는 데 사용되는 Experience Rollouts 기능 API V2에 대한 API 참조입니다.
source-git-commit: 6ecedbfc6c7de392f214f3f8f2e71aa18e1bacb9
workflow-type: tm+mt
source-wordcount: '525'
ht-degree: 11%

---


# GET 기능 API V2 {#get-feature-api-v2}

기능 API V2는 데스크탑 애플리케이션 통합을 위해 설계되었습니다. 인증된 사용자에 대한 기능 플래그 및 릴리스 데이터를 검색하여 표준 클라이언트 ID 외에도 제품 코드 및 제품 버전을 애플리케이션 식별자로 지원합니다.

**끝점:** `GET {HOST}/fg/api/v2/feature`

스테이지에 `https://p13-stage.adobe.io`을(를) 사용하고 프로덕션에 `https://p13n.adobe.io`을(를) 사용합니다.

## 요청 {#request}

### 요청 헤더 {#request-headers}

| Header | 유형 | 설명 | 필수 여부 |
|---|---|---|---|
| `x-api-key` | 문자열 | Adobe Developer Console에서 애플리케이션의 API 키. 스테이지 및 프로덕션에 대해 별도로 프로비저닝해야 합니다. | 예 |
| `Authorization` | 문자열 | `Bearer <AccessToken>` 또는 `Bearer <ServiceToken>`. | 예 |
| `x-adobe-uuid` | 문자열 | 고유 방문자 또는 장치 ID. 인증되지 않은 시나리오에서 롤아웃 비율을 지정하고 세션 일관성을 유지하는 데 사용됩니다. | 아니요 |

### 쿼리 매개변수 {#query-parameters}

| 매개변수 | 유형 | 설명 | 필수 여부 |
|---|---|---|---|
| `clientId` | 문자열 | 경험 롤아웃 콘솔에서 온보딩된 애플리케이션의 클라이언트 ID. 여러 값을 전달할 수 있습니다. `clientId=C1&clientId=C2`. | 아니요 |
| `p` | 문자열 | 제품, 버전, 플랫폼, 로케일 문자열(PVPL 형식). 예: `PHSP:17.0:WIN:en_US`. 여러 값을 전달할 수 있습니다. `p=PHSP:17.0:WIN:en_US&p=PPRO:8:WIN:en_US`. 제품 코드 및 제품 버전만 평가에 사용됩니다. | 아니요 |
| `meta` | 부울 | `true`이면 각 기능에 대해 Base64로 인코딩된 메타데이터가 반환됩니다. 기본값: `false`. | 아니요 |
| *컨텍스트 매개 변수* | N/A | 모든 추가 키-값 쌍은 대상 규칙 평가를 위한 컨텍스트 변수로 처리됩니다. 예: `clientLanguage=ja_JP&contractCurrency=JPY`. | 아니요 |

>[!NOTE]
>
>응용 프로그램을 식별하려면 `clientId` 또는 `p` 중 하나 이상이 필요합니다.

## 응답 {#response}

### 응답 상태 코드 {#response-status}

| 상태 코드 | 설명 |
|---|---|
| `200 OK` | 응답 본문에서 반환된 기능 플래그 데이터. |
| `304 Not Modified` | ETag는 현재 서버 상태와 일치합니다. no-op로 처리 — 변경 사항이 적용되지 않습니다. |
| `401 Unauthorized` | 인증 토큰이 잘못되었습니다. |

### 응답 헤더 {#response-headers}

| Header | 설명 |
|---|---|
| `x-request-id` | 디버깅에 대한 고유한 요청 식별자입니다. 모든 지원 요청에 이 항목을 포함하십시오. |
| `ETag` | 사용자의 현재 기능 상태를 나타내는 토큰입니다. 후속 요청에 `If-None-Match`(으)로 전달합니다. 변경되지 않으면 `304`을(를) 반환합니다. |
| `x-adobe-fg-poll-interval` | 클라이언트의 로컬 캐시에 대한 TTL(초)입니다. 이 간격이 경과한 후에만 API를 다시 호출합니다. |

### 응답 본문 {#response-body}

응답은 다음과 같은 최상위 필드가 있는 JSON 개체입니다.

| 필드 | 유형 | 설명 |
|---|---|---|
| `api_version` | 문자열 | API 버전. 내부 필드 — 처리가 필요하지 않습니다. |
| `json_version` | 문자열 | JSON 스키마 버전. 내부 필드 — 처리가 필요하지 않습니다. |
| `ttl` | 정수 | 캐시 TTL(초). 기본값: 300. |
| `clients` | 오브젝트 | 클라이언트 ID(또는 PVPL 문자열)를 릴리스 데이터에 매핑. 각 키에는 아래에 설명된 필드가 포함되어 있습니다. |

#### 클라이언트별 응답 필드 {#per-client-fields}

| 필드 | 설명 |
|---|---|
| `releases` | 사용자가 적격한 릴리스 배열. 아래의 [릴리스 필드](#releases-fields)을(를) 참조하십시오. |
| `client_analytics_params` | Analytics 구성 개체입니다. 아래의 [client_analytics_params 필드](#analytics-fields)를 참조하십시오. |

#### 릴리스 필드 {#releases-fields}

| 필드 | 설명 |
|---|---|
| `release_name` | 릴리스 또는 기능 그룹의 이름입니다. |
| `bit_index` | 릴리스 비트 인덱스. 사용하지 않음. 릴리스 상태에 따라 `null` 또는 음수일 수 있습니다. |
| `features` | 사용자가 사용할 수 있는 기능 플래그 키 배열. 기능 키는 사용자가 자격이 있고 플래그가 활성화되어 있을 경우에만 나타납니다. |
| `meta` | 선택적 Base64 인코딩 메타데이터입니다. 사용하기 전에 디코딩합니다. |
| `release_analytics_params` | 적격 기능에 대한 분석 메타데이터. 컨트롤 그룹 시나리오에서 `features`이(가) 비어 있습니다. |

#### release_analytics_params 필드 {#release-analytics-params}

| 필드 | 유형 | 설명 |
|---|---|---|
| `app_id` | 정수 | 애플리케이션 ID. |
| `release_id` | 정수 | 릴리스 ID. |
| `bit_index` | 정수 | 사용하지 않음. |
| `variant_id` | 정수 | 컨트롤 그룹인 경우 `0`이고, 그렇지 않은 경우 0이 아닙니다. |
| `feature_id` | 정수 | 내부 기능 ID. |
| `f_key` | 문자열 | 기능 플래그 키. |

#### client_analytics_params 필드 {#analytics-fields}

| 필드 | 유형 | 설명 |
|---|---|---|
| `app_id` | 정수 | 애플리케이션 ID. |
| `safe_event_required` | 부울 | 리타겟팅 이벤트가 활성화된 경우 `true`. |
| `analytics_required` | 부울 | Analytics가 비활성화되어 있거나 기본 흐름일 경우 `false`, Kinesis 흐름이 활성화되어 있을 경우 `true`. |

## 샘플 요청 및 응답 {#sample}

### 샘플 요청 {#sample-request}

```http
GET /fg/api/v2/feature?clientId=MyDesktopApp&p=PHSP:17.0:WIN:en_US&meta=true HTTP/1.1
Host: p13n.adobe.io
Authorization: Bearer <ACCESS_TOKEN>
x-api-key: <YOUR_API_KEY>
If-None-Match: <ETAG>
```

### 샘플 응답 {#sample-response}

```json
{
  "api_version": "0.1",
  "json_version": "0.1",
  "clients": {
    "PHSP:17.0:WIN:en_US": {
      "analyticsVersion": "1.0",
      "releases": []
    },
    "MyDesktopApp": {
      "analyticsVersion": "1.0",
      "client_analytics_params": {
        "app_id": 388,
        "safe_event_required": false,
        "analytics_required": false
      },
      "releases": [
        {
          "bit_index": 160,
          "release_name": "||features||",
          "features": ["feature_a", "feature_b"],
          "release_analytics_params": [
            {
              "app_id": 388,
              "release_id": -1,
              "bit_index": 160,
              "variant_id": 10031741,
              "feature_id": 2918,
              "f_key": "feature_a"
            }
          ],
          "meta": []
        }
      ]
    }
  },
  "ttl": 300
}
```

## 참조 - {#see-also}

* [GET 기능 API V3](get-feature-api-v3.md)
* [데스크탑 애플리케이션](../guides/integrate/desktop-applications.md)
* [통합 단계](../guides/integrate/integration-steps.md)
