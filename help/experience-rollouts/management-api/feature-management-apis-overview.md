---
title: 기능 관리 API 개요
description: 기능 플래그, 기능 그룹 및 릴리스를 프로그래밍 방식으로 생성, 읽기, 업데이트 및 삭제할 수 있는 Experience Rollouts 관리 API의 개요입니다.
source-git-commit: 6ecedbfc6c7de392f214f3f8f2e71aa18e1bacb9
workflow-type: tm+mt
source-wordcount: '284'
ht-degree: 0%

---


# 기능 관리 API 개요 {#feature-management-apis-overview}

Experience Rollouts 관리 API를 사용하면 기능 플래그, 기능 그룹 및 릴리스를 프로그래밍 방식으로 관리할 수 있습니다. 워크플로우를 자동화하거나 경험 롤아웃을 기존 배포 파이프라인에 통합해야 하는 팀은 콘솔 대신 이러한 API를 사용할 수 있습니다.

>[!NOTE]
>
>요청 시 서비스 토큰을 사용하여 관리 API에 대한 액세스 권한이 부여됩니다. 경험 롤아웃 지원 센터에 문의하여 액세스를 요청할 수 있는 비즈니스 근거를 제공하십시오.

## 사용 가능한 관리 API {#available-apis}

다음 관리 API를 사용할 수 있습니다.

* [기능 플래그 관리 API](feature-flags-management-api.md) - 응용 프로그램의 기능 플래그를 만들고, 읽고, 업데이트하고, 삭제합니다.
* [기능 그룹 관리 API](feature-group-management-api.md) - 기능 그룹에 대한 자동 롤아웃 계획을 만들고, 읽고, 업데이트하고, 삭제하고, 제어합니다.
* [릴리스 관리 API](release-management-apis.md) - 팀 간 기능 그룹 및 릴리스를 만들고 편집합니다.

## 일반적인 요구 사항 {#common-requirements}

모든 관리 API 호출에는 다음이 필요합니다.

* Adobe Developer Console의 **API 키** — [API 애플리케이션 구독](../guides/integrate/subscribe-to-api-application.md)을 참조하십시오.
* **IMS 사용자 액세스 토큰** 또는 **서비스 토큰**&#x200B;이(가) `Authorization` 헤더에서 `Bearer <token>`(으)로 전달되었습니다.
* `Content-Type: application/json` 헤더입니다.

API 키 및 토큰은 스테이지 및 프로덕션 환경에 대해 별도로 프로비저닝되어야 합니다.

## 도우미 안내서 {#helper-guides}

다음 안내서는 올바른 API 페이로드를 작성하는 데 도움이 됩니다.

* [응용 프로그램에 대한 클라이언트 ID 가져오기](get-client-id.md) — 기능 플래그 및 기능 그룹 관리 API에 필요한 숫자 클라이언트 ID를 조회합니다.
* [원하는 대상 기준 가져오기](get-audience-criteria.md) - 콘솔 및 GET API를 사용하여 올바른 대상 기준 JSON 구조를 생성합니다.
* [관리 패치 API](management-patch-api.md) — 전체 개체를 전달하지 않고 기능 플래그, 기능 그룹 또는 팀 간 기능 그룹의 개별 필드를 업데이트합니다.

## 참조 - {#see-also}

* [GET 기능 API V3](../feature-api/get-feature-api-v3.md)
* [GET 기능 API V2](../feature-api/get-feature-api-v2.md)
* [API 애플리케이션 구독](../guides/integrate/subscribe-to-api-application.md)
