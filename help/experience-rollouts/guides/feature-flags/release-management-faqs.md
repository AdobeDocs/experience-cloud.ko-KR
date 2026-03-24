---
title: 릴리스 관리 FAQ
description: Adobe Experience Rollouts의 릴리스 관리에 대한 일반적인 질문에 대한 답변을 찾아보십시오.
source-git-commit: d311efb995b20ffc17370d68d57dd84a8605896c
workflow-type: tm+mt
source-wordcount: '285'
ht-degree: 1%

---


# 릴리스 관리 FAQ {#release-management-faqs}

## 릴리스를 요청하려면 어떻게 합니까? {#request-release}

전체 프로세스 및 제공해야 하는 정보에 대해서는 [릴리스 요청](request-a-release.md)을 참조하십시오.

## 릴리스에 지원되는 대상 기준은 무엇입니까? {#audience-criteria}

릴리스는 다음 대상 규칙을 지원합니다.

* ID 유형(계정 유형)
* 국가
* 사용자 ID(GUID)
* 이메일 주소(개인 또는 벌크 목록)
* 이메일 도메인
* 클라이언트 IP
* 백분율(모든 사용자)
* 백분율(인증된 사용자만 해당)

중첩 조건을 포함하여 AND/OR 논리를 사용하여 여러 규칙을 결합할 수 있습니다. 단계별 구성 지침은 [릴리스 대상 규칙 업데이트](update-release-audience-rules.md)를 참조하십시오.

## 릴리스에 애플리케이션을 추가하려면 어떻게 합니까? {#onboard-application}

릴리스가 만들어지면 콘솔에서 릴리스를 열고 애플리케이션을 릴리스 구성에 추가합니다. 그런 다음 각 애플리케이션의 제품 릴리스 소유자가 관련 기능 플래그를 추가할 수 있습니다. 전체 시퀀스를 보려면 [워크플로 전체 릴리스](release-workflow-end-to-end.md)를 참조하십시오.

## 자격이 필요한 사용자에 대한 기능은 반환되지 않습니다. 문제를 해결하려면 어떻게 합니까? {#troubleshoot}

디버깅하려면 다음 단계를 따르십시오.

1. **릴리스 상태를 확인하십시오.** 기능을 제공하려면 릴리스가 **게시됨** 또는 **전체 롤아웃** 상태여야 합니다. [릴리스 상태](release-states.md)를 참조하세요.
2. **응용 프로그램 및 기능 플래그를 확인합니다.** 기능 플래그가 올바른 애플리케이션에 대해 만들어지고 애플리케이션이 올바른 릴리스와 연결되어 있는지 확인합니다.
3. **기능 플래그가 활성화되어 있는지 확인하십시오.** 릴리스가 활성 상태인 경우에도 비활성화된 플래그가 제공되지 않습니다.
4. **대상 기준을 검토합니다.** 사용자가 대상 규칙에 정의된 모든 조건을 충족하는지 확인합니다. 기능이 연결된 특정 릴리스에 대한 기준을 다시 확인하십시오.

## 참조 - {#see-also}

* [릴리스 요청](request-a-release.md)
* [릴리스 대상 규칙 업데이트](update-release-audience-rules.md)
* [릴리스 상태](release-states.md)
* [전체 워크플로 릴리스](release-workflow-end-to-end.md)
