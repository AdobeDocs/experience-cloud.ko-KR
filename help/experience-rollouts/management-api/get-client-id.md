---
title: 애플리케이션에 대한 클라이언트 ID 가져오기
description: 관리 API를 호출할 때 필요한 Experience Rollouts 콘솔에서 애플리케이션에 대한 숫자 클라이언트 ID를 찾는 방법에 대해 알아봅니다.
source-git-commit: 6ecedbfc6c7de392f214f3f8f2e71aa18e1bacb9
workflow-type: tm+mt
source-wordcount: '193'
ht-degree: 1%

---


# 애플리케이션에 대한 클라이언트 ID 가져오기 {#get-client-id}

기능 플래그 및 기능 그룹 관리 API에는 기능이 속한 응용 프로그램을 식별하기 위해 숫자 `clientId`이(가) 필요합니다. API 인증에 사용되는 문자열 기반 IMS 클라이언트 ID와 다릅니다.

응용 프로그램에 대한 숫자 클라이언트 ID를 찾으려면 다음 단계를 따르십시오.

## 단계 {#steps}

응용 프로그램에 대한 숫자 클라이언트 ID를 찾으려면 다음 단계를 수행합니다.

1. 경험 롤아웃 콘솔에 로그인합니다.
2. **기능 및 릴리스**(으)로 이동합니다.
3. **기능 플래그** 탭을 선택합니다.
4. **응용 프로그램** 드롭다운을 열고 클라이언트 ID가 필요한 응용 프로그램을 선택합니다.
5. 브라우저의 주소 표시줄에 있는 URL을 확인합니다. `feature-flags/` 뒤에 표시되는 숫자는 해당 응용 프로그램의 숫자 클라이언트 ID입니다.

예를 들어 URL이 `.../feature-flags/1191/...`(으)로 끝나는 경우 클라이언트 ID는 `1191`입니다.

## API 호출에서 클라이언트 ID 사용 {#use-in-api}

이 값을 관리 API 요청에 `clientId` 매개 변수로 전달합니다. 예를 들어 기능 플래그를 만들 때 다음을 수행합니다.

```json
{
  "name": "my-feature-flag",
  "clientId": 1191,
  "state": "disabled"
}
```

## 참조 - {#see-also}

* [기능 플래그 관리 API](feature-flags-management-api.md)
* [기능 그룹 관리 API](feature-group-management-api.md)
* [원하는 대상 기준 가져오기](get-audience-criteria.md)
