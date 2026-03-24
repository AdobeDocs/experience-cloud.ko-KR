---
title: Java SDK 릴리스 노트
description: 게시된 모든 버전에서 새 기능, 개선 사항 및 버그 수정에 대한 변경 로그를 포함하여 Java SDK의 경험 롤아웃에 대한 릴리스 노트입니다.
source-git-commit: 9bfe0e55e89c1d7fbd77cde63831a6a186820e24
workflow-type: tm+mt
source-wordcount: '309'
ht-degree: 2%

---


# Java SDK 릴리스 노트 {#java-sdk-release-notes}

이 페이지에는 경험 롤아웃 Java SDK의 릴리스 내역이 나열됩니다. 통합 설정에 대해서는 [Java SDK 통합 안내서](java-sdk-integration-guide.md)를 참조하십시오.

## 버전 4.0.6 {#v4-0-6}

**응답의 컨트롤 그룹 데이터**

이제 REST 기능 API의 동작과 일치하는 SDK 응답에서 변형 및 제어 그룹 데이터를 검색할 수 있습니다. 이 기능을 사용하려면 `FloodgateConfiguration` 빌더에 `.includeControlGroup()`을(를) 추가하십시오.

## 버전 4.0.5 {#v4-0-5}

**안정성 및 성능 향상**

캐시 새로 고침 안정성 및 연결 처리에 대한 약간의 내부 개선 사항.

## 버전 4.0.4 {#v4-0-4}

**정책 개선 다시 시도**

일시적인 서비스 오류에 대한 기본 재시도 동작이 개선되었습니다.

## 버전 4.0.3 {#v4-0-3}

**버그 수정**

비동기 초기화에서 에지 사례에 대한 일반적인 안정성 수정 사항.

## 버전 4.0.1(Beta) {#v4-0-1-beta}

**4.x SDK의 Beta 릴리스**

DX 클라이언트 지원, DX 영역 구성 및 AEP(샌드박스) 지원이 도입되었습니다.

## 버전 3.1.0 {#v3-1-0}

**DX 클라이언트에 대한 스트리밍 지원**

SDK 클라이언트에 거의 실시간으로 플래그 업데이트를 알리는 SSE 기반 스트리밍 기능이 추가되었습니다.

## 버전 3.0.x {#v3-0-x}

**Java 11 요구 사항 도입**

버전 3.0.0부터 SDK에는 JDK 11 이상이 필요합니다. 이전 주요 버전은 JDK 8 이상을 지원합니다.

DX 클라이언트에 대한 참조별 지원 기능을 도입하여 기능 엔티티에서 ID로 재사용 가능한 대상 정의를 참조할 수 있습니다.

## 버전 2.x {#v2-x}

**캐시 불가능 클라이언트 지원(0.8)**

캐시할 수 없는 클라이언트는 SDK 캐시에서 읽는 대신 `getFeature()` live를 호출할 수 있습니다. SDK은 백그라운드에서 폴링을 계속 수행하고 클라이언트가 캐시 가능해지면 캐시 기반 서비스로 전환합니다.

추가 2.x 개선 사항에는 새 빌더 옵션(`alwaysCache()`, `neverCache()`, 사용자 지정 HTTP 클라이언트 및 Executor 지원), 기능 및 릴리스 키 필터링, 가장된 사용자 검색이 포함되었습니다.

## 버전 1.x {#v1-x}

초기 릴리스 시리즈. 지원되는 JDK 8+, Maven 종속성 통합, 기본 인증 및 익명 기능 플래그 검색.

## 참조 - {#see-also}

* [Java SDK 통합 안내서](java-sdk-integration-guide.md)
* [Node.js SDK 릴리스 노트](../../sdk-releases/nodejs/nodejs-sdk-release-notes.md)
* [SDK](../../integrate/sdks.md)
