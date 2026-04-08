---
title: Android 통합을 위한 Experience Rollout Extension 안내서
description: Android에서 Experience Rollout 확장을 Adobe Experience Platform Mobile SDK과 통합하는 방법을 알아봅니다.
source-git-commit: fcb1d36fc92b3954a902d818a98f579672c577e9
workflow-type: tm+mt
source-wordcount: '934'
ht-degree: 7%

---


# Android용 경험 롤아웃 확장 {#android-extension-integration-guide}

이 안내서에서는 Android에서 Experience Rollout 확장을 Adobe Experience Platform Mobile SDK과 통합하는 방법을 설명합니다.

## 전제 조건 {#prerequisites}

Experience Rollout 확장을 구현하려면 먼저 다음을 확인하십시오.

* [Adobe Experience Platform 데이터 수집](https://experience.adobe.com/#/data-collection)에 구성된 모바일 속성
* Experience Rollout 확장이 모바일 속성에 설치되고 구성되었습니다
* Adobe Experience Cloud 조직 ID
* 최소 SDK: API 21(Android 5.0 Lollipop)

## 확장 종속성 {#extension-dependencies}

Experience Rollout 확장을 사용하려면 다음 Adobe Experience Platform 확장이 필요합니다.

| 확장 기능 | 설명 | 필수 여부 |
|---|---|---|
| Mobile Core | 구성 및 이벤트 처리를 포함한 핵심 기능 제공 | 예 |
| 라이프사이클 | 모바일 SDK에 대한 애플리케이션 라이프사이클 및 세션 데이터를 수집합니다. | 예 |
| Edge Network | Adobe Experience Platform Edge Network과의 통신 활성화 | 예 |
| EDGE ID | Edge Network에 대한 사용자 ID 관리 | 예 |

이러한 확장이 데이터 수집 모바일 속성에 설치되고 앱 종속성에 포함되어 있는지 확인합니다.

## 데이터 수집에서 경험 롤아웃 확장 구성 {#configure}

### 확장 설치 {#install-extension}

1. [Adobe Experience Platform 데이터 수집](https://experience.adobe.com/#/data-collection)에 로그인합니다.
1. **태그** 탭을 선택하고 모바일 속성을 선택합니다.
1. **확장** > **카탈로그**(으)로 이동합니다.
1. **경험 롤아웃 확장**&#x200B;을 검색하고 **설치**&#x200B;를 선택하십시오.
1. 확장 설정을 구성합니다.

   | 설정 | 설명 |
   |---|---|
   | 샌드박스 | 경험 롤아웃 구성이 포함된 Adobe Experience Platform 샌드박스 |
   | 애플리케이션 ID | 경험 롤아웃에서 애플리케이션의 고유 식별자 |
   | 데이터 세트 ID | Analytics 이벤트 데이터에 대한 Adobe Experience Platform 데이터 세트 ID |

1. **저장**&#x200B;을 선택합니다.
1. 구성을 업데이트하려면 [게시 프로세스](https://experienceleague.adobe.com/en/docs/experience-platform/tags/publish/overview)를 따르십시오.

### 환경 파일 ID 가져오기 {#environment-file-id}

1. 모바일 속성에서 **환경**(으)로 이동합니다.
1. 환경에 대한 **설치** 열 아래의 상자 아이콘을 선택합니다.
1. **모바일 설치 지침** 대화 상자에서 **환경 파일 ID**&#x200B;를 복사합니다.

## 앱에 경험 롤아웃 확장 추가 {#add-to-app}

### 종속성 추가 {#add-dependencies}

Mobile SDK 종속성을 프로젝트에 추가합니다. Experience Rollout 확장을 사용하려면 아래에 나열된 Mobile Core 및 Edge 관련 확장이 필요합니다.

#### BOM과 함께 Gradle 사용(권장) {#gradle-bom}

앱의 `build.gradle.kts` 파일에 다음 종속성을 추가하십시오.

```kotlin
dependencies {
    // Adobe Experience Platform Mobile SDK BOM
    implementation(platform("com.adobe.marketing.mobile:sdk-bom:3.+"))

    // Required extensions
    implementation("com.adobe.marketing.mobile:core")
    implementation("com.adobe.marketing.mobile:lifecycle")
    implementation("com.adobe.marketing.mobile:edge")
    implementation("com.adobe.marketing.mobile:edgeidentity")

    // Experience Rollout extension
    implementation("com.adobe.marketing.mobile:rollout")
}
```

#### Gradle(Groovy) 사용 {#gradle-groovy}

```groovy
dependencies {
    // Adobe Experience Platform Mobile SDK BOM
    implementation platform('com.adobe.marketing.mobile:sdk-bom:3.+')

    // Required extensions
    implementation 'com.adobe.marketing.mobile:core'
    implementation 'com.adobe.marketing.mobile:lifecycle'
    implementation 'com.adobe.marketing.mobile:edge'
    implementation 'com.adobe.marketing.mobile:edgeidentity'

    // Experience Rollout extension
    implementation 'com.adobe.marketing.mobile:rollout'
}
```

>[!IMPORTANT]
>
>프로덕션 애플리케이션의 경우 Adobe에서는 동적 버전 대신 명시적 버전 번호를 사용하는 것이 좋습니다. 자세한 내용은 [Gradle 종속성 관리](https://docs.gradle.org/current/userguide/dependency_management.html)를 참조하십시오.

### 권한 추가 {#add-permissions}

`AndroidManifest.xml` 파일에 다음 권한을 추가합니다.

```xml
<uses-permission android:name="android.permission.INTERNET" />
<uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
```

### SDK 초기화 {#initialize-sdk}

Experience Rollout 확장 API를 호출하기 전에 `Application` 클래스에서 Mobile SDK을 초기화하십시오. 모바일 속성의 환경 파일 ID를 `MobileCore.initialize`과(와) 함께 사용하면 데이터 수집에 게시한 롤아웃 설정이 앱에서 선택됩니다.

#### MobileCore.initialize 사용 {#mobile-core-initialize}

Android BOM 버전 3.8.0부터 사용할 수 있는 이 API는 자동으로 확장을 등록하고 라이프사이클 추적을 활성화합니다.

>[!IMPORTANT]
>
>프로덕션 앱의 경우 `LoggingMode.ERROR`만 사용합니다. 릴리스 빌드에 `DEBUG` 또는 `VERBOSE`을(를) 사용하지 마십시오.

**Kotlin**

```kotlin
import android.app.Application
import com.adobe.marketing.mobile.LoggingMode
import com.adobe.marketing.mobile.MobileCore

class MainApplication : Application() {

    override fun onCreate() {
        super.onCreate()

        MobileCore.setLogLevel(LoggingMode.ERROR)

        // Initialize with your Environment File ID from Data Collection
        MobileCore.initialize(this, "YOUR_ENVIRONMENT_FILE_ID")
    }
}
```

**Java**

```java
import android.app.Application;
import com.adobe.marketing.mobile.LoggingMode;
import com.adobe.marketing.mobile.MobileCore;

public class MainApplication extends Application {

    @Override
    public void onCreate() {
        super.onCreate();

        MobileCore.setLogLevel(LoggingMode.ERROR);

        // Initialize with your Environment File ID from Data Collection
        MobileCore.initialize(this, "YOUR_ENVIRONMENT_FILE_ID", null);
    }
}
```

### 응용 프로그램 클래스 등록 {#register-application}

`AndroidManifest.xml`에서 `Application` 클래스 등록:

```xml
<application
    android:name=".MainApplication"
    ... >
</application>
```

## 평가 컨텍스트 {#evaluation-context}

`FeatureEvaluationContext`에는 타깃팅 특성(롤아웃 규칙 일치에 사용됨)과 선택적 ID(분석에 사용됨)가 포함되어 있습니다.

| 메서드 | 필수 여부 | 설명 |
|---|---|---|
| `withIdentity(namespace, id)` | 아니요 | 첫 번째 인수: ID 네임스페이스([Adobe ID 네임스페이스](https://experienceleague.adobe.com/ko/docs/experience-platform/identity/features/namespaces) 참조). 두 번째 인수: ID 값. 이 평가를 위해 분석에 해당 네임스페이스 및 ID를 표시하려는 경우 이를 포함합니다. 제공되지 않으면 기본적으로 Analytics에서 ECID를 사용합니다. 기능 활성화 결정을 내리는 데 사용되지 않습니다. |
| `withAttributes(map)` | 아니요 | `Map<String, List<String>>`. 키는 롤아웃 규칙에 사용되는 컨텍스트 특성 이름입니다(예: `locale`, `platform`, `appVersion`, `deviceType`). 값은 현재 사용자/세션에 대한 해당 키의 후보 특성 값 목록입니다(예: `["en_US"]` 또는 `["phone"]`). |

**Kotlin**

```kotlin
import com.adobe.marketing.mobile.rollout.FeatureEvaluationContext

val attrs = mapOf(
    "locale" to listOf("en_US"),
    "platform" to listOf("ANDROID"),
    "appVersion" to listOf("3.0.0")
)

val ctx = FeatureEvaluationContext.builder()
    .withIdentity("Email", "customer@example.com")
    .withAttributes(attrs)
    .build()
```

**Java**

```java
import com.adobe.marketing.mobile.rollout.FeatureEvaluationContext;
import java.util.Arrays;
import java.util.HashMap;
import java.util.List;
import java.util.Map;

Map<String, List<String>> attrs = new HashMap<>();
attrs.put("locale", Arrays.asList("en_US"));
attrs.put("platform", Arrays.asList("ANDROID"));
attrs.put("appVersion", Arrays.asList("3.0.0"));

FeatureEvaluationContext ctx = FeatureEvaluationContext.builder()
        .withIdentity("Email", "customer@example.com")
        .withAttributes(attrs)
        .build();
```

### 샘플 타깃팅 속성 {#sample-attributes}

| 속성 | 설명 | 값 예 |
|---|---|---|
| `locale` | 사용자의 로케일/언어 | `["en_US"]`, `["fr_FR"]` |
| `platform` | 플랫폼 식별자 | `["ANDROID"]` |
| `appVersion` | 애플리케이션 버전 | `["3.0.0"]` |
| `deviceType` | 장치 유형 | `["phone"]`, `["tablet"]` |

## API 참조 {#api-reference}

### isFeatureEnabled {#is-feature-enabled}

`isFeatureEnabled`은(는) 특정 컨텍스트에 대해 경험 롤아웃 기능이 설정되어 있는지 여부를 반환합니다. `featureKey`, `FeatureEvaluationContext`(Analytics에 대한 선택적 타기팅 특성 및 선택적 ID) 및 콜백을 전달합니다. [평가 컨텍스트](#evaluation-context)를 참조하십시오.

**서명**

*Kotlin*

```kotlin
Rollout.isFeatureEnabled(
    featureKey: String,
    evaluationContext: FeatureEvaluationContext,
    callback: AdobeCallback<Boolean>
)
```

*Java*

```java
Rollout.isFeatureEnabled(
    String featureKey,
    FeatureEvaluationContext evaluationContext,
    AdobeCallback<Boolean> callback);
```

**매개 변수**

| 매개변수 | 유형 | 설명 |
|---|---|---|
| `featureKey` | 문자열 | 경험 롤아웃에서 평가할 기능 키 |
| `evaluationContext` | 기능 평가 컨텍스트 | 필요에 따라 분석에 대한 타기팅 특성 및 선택적 ID를 포함합니다. 빈 컨텍스트의 경우 `FeatureEvaluationContext.builder().build()`을(를) 사용합니다. [평가 컨텍스트](#evaluation-context)를 참조하십시오. |
| `callback` | AdobeCallback&lt;부울> | 기능이 활성화된 경우 `true`(으)로 호출되고 그렇지 않은 경우 `false`로 호출됩니다. `AdobeCallbackWithError<Boolean>`을(를) 전달하여 `fail(...)`을(를) 처리할 수도 있습니다. |

**예**

*Kotlin*

```kotlin
import com.adobe.marketing.mobile.AdobeCallback
import com.adobe.marketing.mobile.rollout.Rollout

Rollout.isFeatureEnabled(
    "new-checkout-experience",
    ctx,
    object : AdobeCallback<Boolean> {
        override fun call(isEnabled: Boolean?) {
            if (isEnabled == true) {
                showNewCheckout()
            } else {
                showDefaultCheckout()
            }
        }
    }
)
```

*Java*

```java
import com.adobe.marketing.mobile.AdobeCallback;
import com.adobe.marketing.mobile.rollout.Rollout;

Rollout.isFeatureEnabled(
    "new-checkout-experience",
    ctx,
    new AdobeCallback<Boolean>() {
        @Override
        public void call(Boolean isEnabled) {
            if (Boolean.TRUE.equals(isEnabled)) {
                showNewCheckout();
            } else {
                showDefaultCheckout();
            }
        }
    }
);
```

### getFeature {#get-feature}

`getFeature`이(가) 제공된 컨텍스트에 대해 평가된 기능 페이로드를 반환합니다. 활성화/비활성화보다 더 필요하고 기능 메타데이터 또는 값을 원하는 경우 이 API를 사용하십시오.

**서명**

*Kotlin*

```kotlin
Rollout.getFeature(
    featureKey: String,
    evaluationContext: FeatureEvaluationContext,
    callback: AdobeCallback<FeatureEvaluationResult>
)
```

*Java*

```java
Rollout.getFeature(
    String featureKey,
    FeatureEvaluationContext evaluationContext,
    AdobeCallback<FeatureEvaluationResult> callback);
```

**매개 변수**

| 매개변수 | 유형 | 설명 |
|---|---|---|
| `featureKey` | 문자열 | 경험 롤아웃에서 평가할 기능 키 |
| `evaluationContext` | 기능 평가 컨텍스트 | 필요에 따라 분석에 대한 타기팅 특성 및 선택적 ID를 포함합니다. 빈 컨텍스트의 경우 `FeatureEvaluationContext.builder().build()`을(를) 사용합니다. [평가 컨텍스트](#evaluation-context)를 참조하십시오. |
| `callback` | AdobeCallback&lt;FeatureEvaluationResult> | 평가된 기능 페이로드와 함께 호출됩니다. 기능을 찾을 수 없으면 `null`일 수 있습니다. `AdobeCallbackWithError<FeatureEvaluationResult>`을(를) 전달하여 `fail(...)`을(를) 처리할 수도 있습니다. |

**응답**

*FeatureEvaluationResult*

| 필드 | 유형 | 설명 |
|---|---|---|
| `id` | 정수 | 숫자 기능 식별자 |
| `key` | 문자열 | 기능 키 |
| `releaseKey` | 문자열? | 사용 가능한 경우 이 기능의 릴리스 키 |
| `meta` | 문자열? | 사용 가능한 경우 기능 메타데이터를 JSON 문자열로 |
| `analyticsParam` | AnalyticsParam? | 평가된 기능에 대한 Analytics 세부 정보 |

*AnalyticsParam*

| 필드 | 유형 | 설명 |
|---|---|---|
| `releaseId` | 정수 | 숫자 릴리스 식별자 |
| `featureId` | 정수 | 숫자 기능 식별자 |
| `variantId` | 문자열? | 변형 식별자 |

**예**

*Kotlin*

```kotlin
import com.adobe.marketing.mobile.AdobeCallback
import com.adobe.marketing.mobile.rollout.FeatureEvaluationResult
import com.adobe.marketing.mobile.rollout.Rollout

Rollout.getFeature(
    "new-checkout-experience",
    ctx,
    object : AdobeCallback<FeatureEvaluationResult> {
        override fun call(feature: FeatureEvaluationResult?) {
            val meta = feature?.meta
            if (!meta.isNullOrEmpty()) {
                applyMetaDrivenExperience(meta)
            } else {
                showFallbackExperience()
            }
        }
    }
)
```

*Java*

```java
import com.adobe.marketing.mobile.AdobeCallback;
import com.adobe.marketing.mobile.rollout.FeatureEvaluationResult;
import com.adobe.marketing.mobile.rollout.Rollout;

Rollout.getFeature(
    "new-checkout-experience",
    ctx,
    new AdobeCallback<FeatureEvaluationResult>() {
        @Override
        public void call(FeatureEvaluationResult feature) {
            String meta = feature != null ? feature.getMeta() : null;
            if (meta != null && !meta.isEmpty()) {
                applyMetaDrivenExperience(meta);
            } else {
                showFallbackExperience();
            }
        }
    }
);
```

### refreshCache {#refresh-cache}

기본적으로 Experience Rollout 확장은 구성할 수 있는 일정에 따라 서버의 최신 롤아웃 규칙 및 기능을 정기적으로 동기화합니다. 예약된 다음 동기화보다 빨리 업데이트해야 하는 경우 `refreshCache`을(를) 호출하여 새로 고침을 강제로 수행합니다. 일반적인 사례로는 로그인 후 또는 앱 상태가 타겟팅에 영향을 미치는 방식으로 변경되는 경우가 있습니다.

**구문**

*Kotlin*

```kotlin
Rollout.refreshCache()
```

*Java*

```java
Rollout.refreshCache();
```

### extensionVersion {#extension-version}

경험 롤아웃 확장의 버전 문자열을 반환합니다.

**구문**

```kotlin
Rollout.extensionVersion(): String
```

**예**

*Kotlin*

```kotlin
val version = Rollout.extensionVersion()
```

*Java*

```java
String version = Rollout.extensionVersion();
```

## API 요약 {#api-summary}

| API | 반환 |
|---|---|
| `isFeatureEnabled(featureKey, evaluationContext, callback)`. `FeatureEvaluationContext`은(는) 규칙에 대한 타깃팅 특성과 analytics에 대한 선택적 ID를 전달합니다. [기능 평가](#is-feature-enabled)를 참조하세요. | 콜백을 통한 부울 |
| `getFeature(featureKey, evaluationContext, callback)`. 특정 컨텍스트에 대해 평가된 기능 페이로드를 반환합니다. [getFeature](#get-feature)을(를) 참조하십시오. | 콜백을 통한 FeatureEvaluationResult |
| `refreshCache()` | 무효 |
| `extensionVersion()` | 문자열 |

## 참조 - {#see-also}

* [모바일 애플리케이션](../../integrate/mobile-applications.md)
* [통합 단계](../../integrate/integration-steps.md)
* [SDK](../../integrate/sdks.md)
