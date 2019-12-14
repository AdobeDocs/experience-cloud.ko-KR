---
title: Launch를 사용하여 Adobe Experience Platform Identity Service 구현
description: Adobe Experience Platform ID 서비스 확장을 추가하고 고객 ID 설정 작업을 사용하여 고객 ID를 수집하는 방법을 알아봅니다. 이 단원은 모바일 iOS Swift 애플리케이션에서 Experience Cloud 구현 자습서의 일부입니다.
seo-description: null
seo-title: Launch를 사용하여 Adobe Experience Platform Identity Service 구현
solution: Experience Cloud
translation-type: tm+mt
source-git-commit: e9dee6d0aa3b775d0ce617e2b2c57b56de491b8d

---


# Adobe Experience Platform ID 서비스 추가

Adobe [Experience Platform Identity Service는](https://docs.adobe.com/content/help/en/id-service/using/home.html) 솔루션 간 대상 공유와 같은 Experience Cloud 기능을 강화하기 위해 모든 Adobe 솔루션에 대해 공통 방문자 ID를 설정합니다.  또한 고객 ID를 서비스로 보내 크로스 디바이스 타깃팅과 CRM(Customer Relationship Management) 시스템과의 통합을 활성화할 수 있습니다.

ID 서비스는 Mobile Core 익스텐션의 일부이므로 Mobile SDK를 설치할 ***때 이미 구현했습니다***! 현재 이 자습서에는 고객 ID 설정에 대한 지침이 포함되어 있지 않습니다. 고객 ID 설정 [방법에 대한 자세한 내용은 설명서를 참조하십시오](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/mobile-core/identity/identity-api-reference).

## 유효성 검사 단계

ID 서비스에 대한 호출을 확인하려면 Xcode 또는 Developer Studio에서 샘플 앱을 실행하고 디버그 콘솔을 열고 요청 및 응답을 찾습니다.

1. **ID 서비스에** 요청(다음으로 콘솔 필터링) `demdex.net`이 예에서는 ID(`d_mid`)가 이미 설정되었으며 다시 보고되고 있습니다.

   ```swift
   2019-01-15 12:11:45.164590-0500 BusDemoSwift[52399:5056322] [AMSDK DEBUG <com.adobe.module.identity>]: Sending request (https://dpm.demdex.net/id?d_rtbd=json&d_ver=2&d_orgid=7ABB3E6A5A7491460A495D61@AdobeOrg&d_mid=17179986463578698626041670574784107777&d_blob=j8Odv6LonN4r3an7LhD3WZrU1bUpAkFkkiY1ncBR96t2PTI&dcs_region=9)
   ```

1. **ID 서비스에서 응답** (콘솔 필터링 대상 `ID Service`). 이 `mid` 값이 위의 요청에서 `d_mid` 값과 일치하는 방식을 확인하십시오.

   ```swift
   2019-01-15 12:11:45.681821-0500 BusDemoSwift[52399:5056322] [AMSDK DEBUG <com.adobe.module.identity>]: ID Service - Got ID Response (mid: 17179986463578698626041670574784107777, blob: j8Odv6LonN4r3an7LhD3WZrU1bUpAkFkkiY1ncBR96t2PTI, hint: 9, ttl: "604800000 ms")
   
[다음 "Adobe Target VEC 지원 추가" &gt;](target-vec.md)
