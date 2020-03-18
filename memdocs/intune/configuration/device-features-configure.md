---
title: Microsoft Intune을 사용하여 iOS/iPadOS 또는 macOS 디바이스 프로필 만들기 - Azure | Microsoft Docs
description: iOS, iPadOS 또는 macOS 디바이스 프로필을 추가하거나 만든 다음, Microsoft Intune에서 AirPrint, 홈 화면의 레이아웃, 앱 알림, 공유 디바이스, 단일 로그인 및 웹 콘텐츠 필터 설정에 대한 설정을 구성합니다.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 02/18/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 48f890888d9bdb9d1df67596fb9125534e90a4d2
ms.sourcegitcommit: 3d895be2844bda2177c2c85dc2f09612a1be5490
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79350137"
---
# <a name="add-ios-ipados-or-macos-device-feature-settings-in-intune"></a>Intune에서 iOS, iPadOS 및 macOS 디바이스 기능 설정 추가

Intune에는 관리자가 iOS, iPadOS 및 macOS 디바이스를 제어하는 데 도움이 되는 많은 기능과 설정이 포함되어 있습니다. 예를 들어 관리자는 다음을 수행할 수 있습니다.

- 네트워크의 AirPrint 프린터에 사용자 액세스 허용
- 새 페이지 추가를 포함하여 홈 화면에 앱 및 폴더 추가
- 앱 알림 표시 여부 및 방법 선택
- 특히 공유 디바이스의 경우 메시지 또는 자산 태그를 표시하도록 잠금 화면 구성
- 사용자에게 안전한 Single Sign-On 환경을 제공하여 앱 간에 자격 증명 공유
- 성인 언어를 사용하는 웹 사이트 필터링 및 특정 웹 사이트 허용 또는 차단

Intune은 "구성 프로필"을 사용하여 조직의 요구 사항에 맞게 이러한 설정을 만들고 사용자 지정합니다. 프로필에 이러한 기능을 추가한 후에 해당 프로필을 조직의 iOS/iPadOS 및 macOS 디바이스에 푸시하거나 배포할 수 있습니다.

이 문서는 구성할 수 있는 다양한 기능을 설명하고, 디바이스 구성 프로필을 만드는 방법을 보여줍니다. [iOS/iPadOS](ios-device-features-settings.md) 및 [macOS](macos-device-features-settings.md) 디바이스에 사용 가능한 모든 설정을 볼 수도 있습니다.

## <a name="airprint"></a>AirPrint

AirPrint는 디바이스가 무선 네트워크를 통해 파일을 인쇄할 수 있는 Apple 기능입니다. Intune에서 AirPrint 정보를 디바이스에 추가할 수 있습니다.

Intune에서 구성할 수 있는 설정 목록은 [iOS/iPadOS의 AirPrint](ios-device-features-settings.md#airprint)와 [macOS의 AirPrint](macos-device-features-settings.md#airprint)를 참조하세요.

AirPrint에 대한 자세한 내용은 Apple 웹 사이트의 [AirPrint 정보](https://support.apple.com/HT201311)를 참조하세요.

적용 대상:

- iOS 7.0 이상
- iPadOS 13.0 이상
- macOS 10.10 이상

## <a name="app-notifications"></a>앱 알림

iOS 및 iPadOS 디바이스의 앱이 알림을 수신하는 방법을 선택합니다. 예를 들어 알림 센터에 표시되거나 잠금 화면에 표시되거나 사운드를 재생하도록 Intune에서 앱 알림을 보냅니다.

Intune에서 구성할 수 있는 설정 목록은 [iOS/iPadOS의 앱 알림](ios-device-features-settings.md#app-notifications)을 참조하세요.

이 기능에 대한 자세한 내용은 Apple 웹 사이트의 [알림](https://developer.apple.com/notifications/)을 참조하세요.

적용 대상:

- iOS 9.3 이상
- iPadOS 13.0 이상

## <a name="associated-domains"></a>연결된 도메인

연결된 도메인을 사용하여 `contoso.com` 같은 도메인과 앱 사이의 관계를 만들 수 있습니다. 이 기능을 사용하여 다음을 할 수 있습니다.

- 조직에서 앱과 웹 사이트 간에 데이터 및 로그인 자격 증명을 공유합니다.
- Single Sign-On 앱 확장, 범용 링크, 암호 자동 채우기 등 웹 사이트에 기반한 앱 기능을 사용합니다.

  예를 들어 연결된 도메인을 만들어 암호 자동 채우기가 앱에 연결된 웹 사이트의 자격 증명(예: 암호)을 추천하도록 허용합니다.

Intune에서 구성할 수 있는 설정 목록은 [macOS의 연결된 도메인](macos-device-features-settings.md#associated-domains)을 참조하세요.

이 기능에 대한 자세한 내용은 Apple 웹 사이트의 [앱의 연결된 도메인 설정](https://developer.apple.com/documentation/security/password_autofill/setting_up_an_app_s_associated_domains)을 참조하세요.

적용 대상:

- macOS 10.15 이상

## <a name="home-screen-layout"></a>홈 화면 레이아웃

이러한 설정은 iOS 및 iPadOS 디바이스의 도킹 및 홈 화면에서 앱 레이아웃과 폴더를 구성합니다. 다음과 같습니다.

- **도킹** 설정을 사용하여 앱 또는 폴더를 화면에 추가합니다. 예를 들어 디바이스 도킹에 Safari 및 메일 앱을 표시합니다.
- 홈 화면에 표시할 **페이지**와 각 페이지에 표시할 앱을 추가합니다. 예를 들어 **Contoso** 페이지를 추가하고 이 페이지에 설정 앱을 추가합니다.

Intune에서 구성할 수 있는 설정 목록은 [iOS/iPadOS의 홈 화면 레이아웃](ios-device-features-settings.md#home-screen-layout)을 참조하세요.

적용 대상:

- iOS 9.3 이상
- iPadOS 13.0 이상

## <a name="lock-screen-message"></a>잠금 화면 메시지

이러한 설정을 사용하여 로그인 창 및 잠금 화면에 사용자 지정 메시지 또는 텍스트를 표시합니다. 예를 들어 "분실 시, 돌려주기..." 메시지를 입력하고 자산 태그 정보를 표시할 수 있습니다.

Intune에서 구성할 수 있는 설정 목록은 [iOS/iPadOS의 잠금 화면 메시지 설정](ios-device-features-settings.md#lock-screen-message)을 참조하세요.

잠금 화면 메시지에 대한 자세한 내용은 Apple 웹 사이트의 [잠금 화면 메시지](https://developer.apple.com/documentation/devicemanagement/lockscreenmessage)를 참조하세요.

적용 대상:

- iOS 9.3 이상
- iPadOS 13.0 이상

## <a name="login-items"></a>로그인 항목

이 기능을 사용하여 사용자가 디바이스에 로그인하면 열리는 앱, 사용자 지정 앱, 파일 및 폴더를 선택할 수 있습니다.

Intune에서 구성할 수 있는 설정 목록은 [macOS의 로그인 항목](macos-device-features-settings.md#login-items)을 참조하세요.

적용 대상:

- macOS 10.13 이상

## <a name="login-window"></a>로그인 창

로그인하기 전에 사용자가 사용할 수 있는 로그인 화면 및 기능의 모양을 제어합니다. 예를 들어 사용자 지정 메시지가 있는 배너를 추가하고 절전 모드 단추 표시 여부 등을 선택합니다.

Intune에서 구성할 수 있는 설정 목록은 [macOS의 로그인 창](macos-device-features-settings.md#login-window)을 참조하세요.

적용 대상:

- macOS 10.7 이상

## <a name="single-sign-on"></a>Single Sign-On

대부분의 LOB(기간 업무) 앱이 보안을 지원하려면 일부 수준의 사용자 인증이 필요합니다. 대부분의 경우 인증은 사용자가 동일한 자격 증명을 반복적으로 입력해야 합니다. 사용자 환경을 개선하기 위해 개발자는 SSO(Single Sign-On)를 사용하는 앱을 만들 수 있습니다. Single Sign-On을 사용하면 사용자가 자격 증명을 입력해야 하는 횟수를 줄입니다.

Single Sign-On을 사용하려면 다음이 있어야 합니다.

- 디바이스의 Single Sign-On에서 사용자 자격 증명 저장소를 찾도록 코딩된 앱
- iOS/iPadOS 디바이스 Single Sign-On용으로 구성된 Intune입니다.

![Single Sign-On 창](./media/device-features-configure/sso-blade.png)

Intune에서 구성할 수 있는 설정 목록은 [iOS/iPadOS의 Single sign-on](ios-device-features-settings.md#single-sign-on)를 참조하세요.

적용 대상:

- iOS 7.0 이상
- iPadOS 13.0 이상

## <a name="single-sign-on-app-extension"></a>Single Sign-On 앱 확장

이러한 설정은 iOS, iPadOS 및 macOS 디바이스에서 SSO(Single Sign-On)를 사용하도록 설정하는 앱 확장을 구성합니다. 대부분의 LOB(기간 업무) 앱과 조직 웹 사이트에서는 일정 수준의 보안 사용자 인증이 필요합니다. 대부분의 경우 인증은 사용자가 동일한 자격 증명을 반복적으로 입력해야 합니다. SSO를 통해 사용자는 자격 증명을 한 번만 입력하면 앱 및 웹 사이트에 액세스할 수 있습니다. 사용자가 로그인한 후에는 앱 및 웹 사이트에 자동으로 액세스하거나 Face ID, Touch ID 또는 Apple 암호를 사용하여 액세스 권한을 얻을 수 있습니다.

Intune에서 이러한 설정을 사용하여 조직, ID 공급자 또는 Apple에서 만든 SSO 앱 확장을 구성합니다. SSO 앱 확장은 사용자 인증을 처리합니다. 이러한 설정은 리디렉션 유형 및 자격 증명 유형 SSO 앱 확장을 구성합니다.

- 리디렉션 유형은 OAuth 및 SAML2와 같은 최신 인증 프로토콜을 위해 설계되었습니다.
- 자격 증명 유형은 인증 시도/응답 인증 흐름을 위해 설계되었습니다. Apple에서 제공한 Kerberos 관련 자격 증명 확장과 일반 자격 증명 확장 중에서 선택할 수 있습니다.

Intune에서 구성할 수 있는 설정 목록은 [iOS/iPadOS SSO 앱 확장](ios-device-features-settings.md#single-sign-on-app-extension) 및 [macOS SSO 앱 확장](macos-device-features-settings.md#single-sign-on-app-extension)을 참조하세요.

SSO 앱 확장을 개발하는 방법에 대한 자세한 내용은 Apple 웹 사이트의 [Extensible Enterprise SSO](https://developer.apple.com/videos/play/tech-talks/301)를 참조하세요. 이 기능에 대한 Apple의 설명을 읽으려면 [Single Sign-on 확장 페이로드 설정](https://support.apple.com/guide/mdm/single-sign-on-extensions-mdmfd9cdf845/web)을 참조하세요. 

> [!NOTE]
> **SSO(단일 로그인) 앱 확장** 기능은 **SSO(단일 로그인)** 기능과 다릅니다.
>
> - **Single Sign-On 앱 확장** 설정은 iPadOS 13.0 이상, iOS 13.0 이상 및 macOS 10.15 이상에 적용됩니다. **Single Sign-On** 설정은 iPadOS 13.0 이상 및 iOS 7.0 이상에 적용됩니다.
>
> - **Single Sign-On 앱 확장** 설정은 ID 공급자나 조직에서 원활한 엔터프라이즈 로그온 환경을 제공하는 데 사용할 확장을 정의합니다. **Single Sign-On** 설정은 사용자가 서버 또는 앱에 액세스하는 경우에 대한 Kerberos 계정 정보를 정의합니다.
>
> - **Single Sign-On 앱 확장**은 Apple 운영 체제를 사용하여 인증합니다. 따라서 **Single Sign-On**보다 뛰어난 최종 사용자 환경을 제공할 수 있습니다.
>
> - 개발 관점에서 **Single Sign-On 앱 확장**은 모든 유형의 리디렉션 SSO 또는 자격 증명 SSO 인증을 사용할 수 있습니다. **Single Sign-On**을 사용할 경우 Kerberos SSO 인증만 사용할 수 있습니다.
>
> - Kerberos **Single Sign-On 앱 확장**은 Apple에서 개발되었으며 iOS/iPadOS 13.0 이상 및 macOS 10.15 이상 플랫폼에 기본 제공됩니다. 기본 제공 Kerberos 확장은 Kerberos 인증을 지원하는 기본 앱 및 웹 사이트에 사용자를 로그인하는 데 사용할 수 있습니다. **Single Sign-On**은 Apple의 Kerberos 구현이 아닙니다.
>
> - 기본 제공 Kerberos **Single Sign-On 앱 확장**은 **Single Sign-On**과 마찬가지로 웹 페이지 및 앱에 대한 Kerberos 문제를 처리합니다. 그러나 기본 제공 Kerberos 확장은 암호 변경을 지원하며 엔터프라이즈 네트워크에서 더 효율적으로 작동합니다. Kerberos **Single Sign-On 앱 확장** 및 **Single Sign-On**을 결정할 때 향상된 성능 및 기능을 위해 확장을 사용하는 것이 좋습니다.

적용 대상:

- iOS 13.0 이상
- iPadOS 13.0 이상
- macOS 10.15 이상

## <a name="wallpaper"></a>배경 무늬

감독되는 iOS/iPadOS 디바이스에 사용자 지정 .png, .jpg 또는 .jpeg 이미지를 추가합니다. 예를 들어 Intune을 사용하여 디바이스의 잠금 화면에 회사 로고를 추가합니다.

Intune에서 구성할 수 있는 설정 목록은 [iOS/iPadOS의 배경화면](ios-device-features-settings.md#wallpaper)을 참조하세요.

적용 대상:

- iOS
- iPadOS 13.0 이상

## <a name="web-content-filter"></a>웹 콘텐츠 필터

이러한 설정은 Apple의 기본 제공 자동 필터 알고리즘을 사용하여 웹 페이지를 평가하고 성인 콘텐츠 및 성인 언어를 차단할 수 있습니다. 허용된 웹 링크 및 제한된 웹 링크 목록을 만들 수도 있습니다. 예를 들어 `contoso` 웹 사이트만 열리도록 허용할 수 있습니다.

Intune에서 구성할 수 있는 설정 목록은 [iOS/iPadOS의 웹 콘텐츠 필터](ios-device-features-settings.md#web-content-filter)를 참조하세요.

적용 대상:

- iOS 7.0 이상
- iPadOS 13.0 이상

## <a name="create-a-device-profile"></a>디바이스 프로필 만들기

1. [Microsoft Endpoint Manager 관리 센터](https://go.microsoft.com/fwlink/?linkid=2109431)에 로그인합니다.
2. **디바이스 구성** > **구성 프로필** > **프로필 만들기**를 선택합니다.
3. 다음 속성을 입력합니다.

    - **이름**: 정책에 대한 설명이 포함된 이름을 입력합니다. 나중에 쉽게 식별할 수 있도록 정책 이름을 지정합니다. 예를 들어 좋은 정책 이름은 **macOS: 로그인 화면 구성**입니다.
    - **설명**: 프로필에 대한 설명을 입력합니다. 이 설정은 선택 사항이지만 권장됩니다.
    - **플랫폼**: 디바이스 플랫폼을 선택합니다. 옵션은 다음과 같습니다.  
        - **iOS/iPadOS**
        - **macOS**
    - **프로필 유형**: **디바이스 기능**을 선택합니다.

4. 선택한 플랫폼에 따라 구성할 수 있는 설정이 다릅니다. 자세한 설정을 위한 플랫폼을 선택합니다.

    - [iOS/iPadOS](ios-device-features-settings.md)
    - [macOS](macos-device-features-settings.md)

5. 작업이 완료되면 **확인** > **만들기**를 선택하여 변경 내용을 저장합니다.

프로필이 만들어지고 프로필 목록에 표시됩니다. [프로필을 할당](device-profile-assign.md)하고 [해당 상태를 모니터링](device-profile-monitor.md)합니다.

## <a name="next-steps"></a>다음 단계

프로필이 생성된 후에는 이를 할당할 수 있습니다. 다음으로, [프로필을 할당](device-profile-assign.md)하고, [해당 상태를 모니터링](device-profile-monitor.md)합니다.

[iOS/iPadOS](ios-device-features-settings.md) 및 [macOS](macos-device-features-settings.md) 디바이스에 대한 모든 디바이스 기능 설정을 봅니다.
