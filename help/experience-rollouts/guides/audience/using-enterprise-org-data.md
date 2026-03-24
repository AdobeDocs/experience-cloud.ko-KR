---
title: 대상 규칙에서 Enterprise 조직 데이터 사용
description: Adobe Experience Rollouts에서 엔터프라이즈 조직 ID를 대상 기준으로 사용하여 특정 고객 조직을 타깃팅하는 방법에 대해 알아봅니다.
source-git-commit: 3f3f7145b3c58dc721cbeb850e9e8571e3255bb1
workflow-type: tm+mt
source-wordcount: '237'
ht-degree: 1%

---


# 대상 규칙에서 Enterprise 조직 데이터 사용 {#enterprise-org-data}

경험 롤아웃은 엔터프라이즈 조직(org) ID를 기반으로 사용자를 타깃팅할 수 있습니다. 이를 통해 기능을 광범위하게 사용하기 전에 특정 고객 조직에 롤아웃할 수 있습니다.

## 대상 규칙에 조직 추가 {#adding-org-rule}

엔터프라이즈 조직 타깃팅은 **대상 규칙 > 프로필 > 엔터프라이즈**&#x200B;의 **대상** 탭에서 사용할 수 있습니다.

지원되는 조직 유형은 두 가지입니다.

### DME 조직 {#dme-orgs}

DME 조직은 조직 ID로 식별됩니다. 규칙을 생성할 때 조직 ID만 입력하십시오. 인증 소스는 포함하지 마십시오.

### DMA 조직 {#dma-orgs}

DMA 조직은 `XXXXXXXXXXXXXXXXXXXXXXXX@ADOBEORG` 형식의 조직 ID를 사용합니다. DMA 조직 ID 입력 시:

* `@ADOBEORG` 접미사를 포함한 전체 조직 ID를 사용하십시오.
* `ADOBEORG`을(를) 모두 대문자로 입력하십시오.

**예:** `57F22B5D5A5F83AE0A495E6E@ADOBEORG`

## 중요 정보 {#important-notes}

* 조직 기반 타깃팅은 사용자의 인증된 세션과 연결된 조직에 대해 평가됩니다. 테스트할 때 사용자가 올바른 조직에 로그인했는지 확인하십시오.
* 찾으려는 조직이 대상 기준에 표시되지 않거나 특정 조직의 예상대로 기능이 반환되지 않는 경우 경험 롤아웃 지원 센터에 문의하십시오.
* 사용 가능한 조직이 있는 단계 및 프로덕션 환경은 다를 수 있습니다. 프로덕션으로 승격하기 전에 스테이지에서 대상 규칙을 테스트하십시오.

## 참조 - {#see-also}

* [기능 플래그 및 기능 그룹의 대상자](audience-in-feature-flags-and-feature-groups.md)
* [릴리스 대상 규칙 업데이트](../feature-flags/update-release-audience-rules.md)
* [복잡한 대상 규칙](complex-rules.md)
