---
title: 클라이언트 IP 컨텍스트 변수가 있는 대상 규칙
description: IP 주소, CIDR 블록 및 네트워크 범위에 대한 지원을 포함하여 Adobe Experience 롤아웃의 대상 규칙에서 클라이언트 IP 컨텍스트 변수를 사용하는 방법을 알아봅니다.
source-git-commit: 3f3f7145b3c58dc721cbeb850e9e8571e3255bb1
workflow-type: tm+mt
source-wordcount: '215'
ht-degree: 1%

---


# 클라이언트 IP 컨텍스트 변수가 있는 대상 규칙 {#clientip-rule}

`clientip` 컨텍스트 변수를 사용하면 클라이언트 IP 주소를 기준으로 사용자를 타깃팅할 수 있습니다. 사용자가 애플리케이션에 액세스하는 네트워크에 따라 기능을 제한하거나 활성화하는 데 유용합니다(예: 회사 네트워크의 사용자에 대한 조기 액세스 제한).

## 지원되는 입력 유형 {#input-types}

`clientip` 컨텍스트 변수는 세 가지 유형의 입력 값을 지원합니다.

| 입력 유형 | 설명 | 지원되는 연산자 |
|---|---|---|
| **IP 주소** | 단일 IPv4 또는 IPv6 주소 | 같음, 같지 않음, In |
| **CIDR 블록** | CIDR 표기법의 IP 주소 범위(예: `192.168.1.0/24`) | 같음, In, 같지 않음 |
| **네트워크 범위** | 플랫폼에서 유지 관리하는 사전 정의된 명명된 네트워크 범위 | 의 일부임 |

## 클라이언트 IP 규칙 추가 {#adding-rule}

1. 콘솔에서 기능 플래그, 기능 그룹 또는 팀 간 기능 그룹을 엽니다.
2. **대상자** 탭으로 이동합니다.
3. **Context**&#x200B;에서 **clientip** 변수를 사용하여 조건을 추가합니다.
4. 연산자를 선택하고 값(IP 주소, CIDR 블록 또는 사전 정의된 네트워크 범위 선택)을 입력합니다.

## 참조 - {#see-also}

* [대상 규칙에서 컨텍스트 사용](using-context-in-audience-rules.md)
* [기능 플래그 및 기능 그룹의 대상자](audience-in-feature-flags-and-feature-groups.md)
* [복잡한 대상 규칙](complex-rules.md)
