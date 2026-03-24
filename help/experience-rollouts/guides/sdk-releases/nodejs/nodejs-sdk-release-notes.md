---
title: Node.js SDK 릴리스 노트
description: 게시된 모든 버전에서 새 기능, 개선 사항 및 버그 수정에 대한 변경 로그를 포함하여 Experience Rollouts Node.js SDK에 대한 릴리스 노트입니다.
source-git-commit: 9bfe0e55e89c1d7fbd77cde63831a6a186820e24
workflow-type: tm+mt
source-wordcount: '161'
ht-degree: 1%

---


# Node.js SDK 릴리스 노트 {#nodejs-sdk-release-notes}

이 페이지에는 경험 롤아웃 Node.js SDK의 릴리스 내역이 나열됩니다. 통합 설정에 대해서는 [Node.js SDK 통합 안내서](nodejs-sdk-integration-guide.md)를 참조하십시오.

## 버전 1.0.10 {#v1-0-10}

**버그 수정 및 소켓 개선**

* 예약된 캐시를 새로 고치는 동안 발생한 `ESOCKETTIMEDOUT` 예외를 해결했습니다. `createInstance()`의 `featureRequestHttpParams` 및 `ingestAnalyticsHttpParams`에서 `maxSockets` 매개 변수를 제거했습니다.
* HTTP 304(수정되지 않음) 응답 후 캐시 가능 클라이언트가 캐시 불가로 잘못 표시되던 버그를 수정했습니다.
* `isReleaseBitEnabled()`을(를) 제거했습니다. 이 메서드는 더 이상 지원되지 않습니다.
* 더 나은 진단을 위해 로깅 출력이 개선되었습니다.
* 테스트 및 적용 범위 폴더는 게시된 npm 패키지에 더 이상 포함되지 않습니다.

## 버전 1.0.5 {#v1-0-5}

**안정성 개선**

캐시 새로 고침 처리 및 SDK 초기화 극단적 사례에 대한 일반적인 수정 사항.

## 버전 1.0.3 {#v1-0-3}

**초기 안정 릴리스**

인증된 기능, 익명의 기능 및 기본 전체 롤아웃 기능 플래그 검색을 지원하는 Node.js SDK의 첫 번째 프로덕션 릴리스.

## 참조 - {#see-also}

* [Node.js SDK 통합 안내서](nodejs-sdk-integration-guide.md)
* [Java SDK 릴리스 노트](../../sdk-releases/java/java-sdk-release-notes.md)
* [SDK](../../integrate/sdks.md)
