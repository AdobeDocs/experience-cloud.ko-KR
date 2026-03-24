---
title: SDK 벤치마킹
description: 일반적인 로드 조건에서 다양한 수의 기능 플래그에 대한 응답 시간 측정을 포함하여 Adobe Experience 롤아웃에 대한 Java SDK 벤치마킹 결과를 검토하십시오.
source-git-commit: 8b8b5db1a28af3a3ac29aecf26482f70eb84c714
workflow-type: tm+mt
source-wordcount: '249'
ht-degree: 7%

---


# SDK 벤치마킹 {#sdk-benchmarking}

Experience Rollouts Java SDK은 통합 팀이 인프라 내에서 SDK을 실행할 때 예상할 수 있는 리소스 및 응답 시간을 신뢰할 수 있게 예측하기 위해 벤치마킹되었습니다.

## 테스트 환경 {#test-environment}

벤치마킹은 다음과 같은 고정 구성을 사용하여 스프링 부트 애플리케이션에서 수행되었습니다.

* **CPU 코어:** 8
* **JVM 메모리:** 4096MB

## 테스트 가정 {#test-assumptions}

다음 조건은 모든 벤치마크 실행에서 일정하게 유지되었습니다.

* 기능 플래그 테스트됨: 8~128
* 기능 플래그당 컨텍스트 변수: 2(유형 `STRING`, 길이 36자)
* 평균 로드: 분당 15,000개 요청(RPM)
* 활성 스레드: 100

## 결과 {#results}

아래 표는 기능 플래그 수가 증가함에 따라 `getFeatures()` 호출에 대한 99.99번째 백분위수 응답 시간을 보여 줍니다.

| 기능 플래그 수 | 플래그당 컨텍스트 변수 | 응답 시간(ms, p99.99) |
|---|---|---|
| 8 | 2 | &lt; 0.5 |
| 16 | 2 | &lt; 0.5 |
| 32 | 2 | &lt; 0.5 |
| 64 | 2 | &lt; 1 |
| 128 | 2 | &lt; 1 |

## 결과 해석 {#interpretation}

위의 벤치마크는 설명된 특정 테스트 조건에서의 성능을 나타냅니다. SDK은 애플리케이션의 인프라 내에서 실행되므로 실제 응답 시간은 환경에 따른 요인에 따라 달라집니다.

* 사용 가능한 CPU 및 코어 수
* JVM 힙 크기 및 가비지 수집 동작
* 스레드 가용성 및 컨텍스트 전환
* 요청 시 현재 시스템 로드

이러한 수치를 프로덕션 환경에 대한 보장된 성능 목표가 아닌 계획 기준으로 사용합니다.

## 참조 - {#see-also}

* [Java SDK 통합 안내서](java/java-sdk-integration-guide.md)
* [Java SDK 릴리스 노트](java/java-sdk-release-notes.md)
* [SDK](../integrate/sdks.md)
