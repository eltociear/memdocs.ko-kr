---
title: 개발 중 - Microsoft Intune
titleSuffix: ''
description: 개발 중인 Microsoft Intune 기능
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 03/03/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.assetid: 25b3c26e-cf4e-4152-8306-bf4be4af2ad1
ms.reviewer: cacampbell
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 2e5c7ce18cc00934438e945933188d9634b36653
ms.sourcegitcommit: 3d895be2844bda2177c2c85dc2f09612a1be5490
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79362318"
---
# <a name="in-development-for-microsoft-intune---march-2020"></a>개발 중인 Microsoft Intune 기능 - 2020년 3월

준비 및 계획을 돕기 위해 이 페이지에는 개발 중이지만 아직 릴리스되지 않은 Intune UI 업데이트 및 기능이 나열되어 있습니다. 이 페이지의 정보 외에 다음을 참조할 수 있습니다. 

- 변경하기 전에 조치를 취해야 할 것으로 예상되면 Office 메시지 센터에 보완 게시물을 게시할 것입니다.
- 미리 보기 또는 일반적으로 사용할 수 있는 기능이 프로덕션 단계에 들어가면 기능 설명이 이 페이지에서 [새로운 기능](whats-new.md)으로 이동합니다.
- 이 페이지와 [새로운 기능](whats-new.md) 페이지는 정기적으로 업데이트됩니다. 추가 업데이트가 있는지 다시 확인하세요.
- 전략적 결과물과 타임라인은 [Microsoft 365 로드맵](https://www.microsoft.com/microsoft-365/roadmap?rtc=2&filters=EMS)을 참조하세요.

> [!NOTE]
> 이 페이지는 향후 릴리스에서 제공될 Intune 기능에 대한 Microsoft의 현재 기대를 반영합니다. 날짜 및 개별 기능이 변경될 수 있습니다. 이 페이지는 개발의 일부 기능만 설명합니다.

**RSS 피드**: URL `https://docs.microsoft.com/api/search/rss?search=%22in+development+-+microsoft+intune%22&locale=en-us`를 복사하여 피드 판독기에 붙여넣으면 이 페이지가 업데이트될 때 알 수 있습니다.

<!--
## What's coming to Intune in the Azure portal 
## What's coming to Intune apps
## Notices
-->

<!-- Common categories:  
## App management
## Device configuration
## Device enrollment
## Device management
## Intune apps
## Monitor and troubleshoot
## Role-based access control
## Security

-->
 
<!-- ***********************************************-->
## <a name="app-management"></a>앱 관리

### <a name="retarget-web-clips-to-microsoft-edge-on-iosipados-devices---5455276---"></a>iOS/iPadOS 디바이스에서 Microsoft Edge로 웹 클립의 대상 변경<!-- 5455276 -->
웹 클립은 iOS/iPadOS 디바이스에서 고정된 웹앱 역할을 하는 것으로, 업데이트가 필요합니다. 보호되는 브라우저에서 열어야 하는 경우 새로 배포된 웹 클립은 Intune Managed Browser 대신 Microsoft Edge에서 열립니다. Managed Browser 대신 Microsoft Edge에서 열리도록 기존 웹 클립의 대상을 변경해야 합니다.

### <a name="macos-and-ios-company-portal-updates---5779439-5780234----"></a>macOS 및 iOS 회사 포털 업데이트<!-- 5779439, 5780234  -->
macOS 및 iOS 회사 포털의 [프로필] 창이 [로그아웃] 단추를 포함하도록 업데이트됩니다. 또한 이 업데이트에는 macOS 회사 포털 [프로필] 창의 UI 개선 사항이 포함됩니다. 회사 포털에 대한 자세한 내용은 [Microsoft Intune 회사 포털 앱을 구성하는 방법](../apps/company-portal-app.md)을 참조하세요.

### <a name="updates-to-branding-and-customization-pane---5236032---"></a>브랜딩 및 사용자 지정 창 업데이트<!-- 5236032 -->
현재 다음을 포함한 향상된 기능으로 “브랜딩 및 사용자 지정”이라는 Intune 창을 업데이트하는 중입니다.

- 창 이름을 **사용자 지정**으로 바꿉니다.
- 설정의 구성 및 디자인을 개선합니다.
- 설정 텍스트 및 도구 설명을 개선합니다.

Intune에서 해당 설정을 찾으려면 [Microsoft Endpoint Manager 관리 센터](https://go.microsoft.com/fwlink/?linkid=2109431)로 이동하고 **테넌트 관리** > **사용자 지정** 을 선택합니다. 기존 사용자 지정에 대한 자세한 내용은 [Microsoft Intune 회사 포털 앱을 구성하는 방법](../apps/company-portal-app.md)을 참조하세요.

### <a name="configure-the-ios-microsoft-azure-ad-sso-app-extension---567534----"></a>iOS Microsoft Azure AD SSO 앱 확장 구성<!-- 567534  -->
Microsoft Azure AD 팀은 iOS 및 iPadOS 13.0 이상 사용자가 한 번의 로그온으로 Microsoft 앱 및 웹 사이트에 원활하게 액세스할 수 있도록 하는 리디렉션 SSO(Single Sign-On) 앱 확장을 개발하고 있습니다. AAD SSO 앱 확장이 릴리스되면 최소한의 클릭으로 관리 콘솔에서 **디바이스 기능** > **Single Sign-On 앱 확장** 프로필을 사용하여 SSO 확장을 구성할 수 있습니다.

iOS SSO 앱 확장 또는 디바이스 기능 구성 방법에 대한 자세한 내용은 [Single Sign-On 앱 확장](../configuration/device-features-configure.md#single-sign-on-app-extension)을 참조하세요.

### <a name="company-portal-for-ios-to-support-landscape-mode--6048329----"></a>가로 모드를 지원하기 위한 iOS용 회사 포털<!--6048329  -->
사용자는 디바이스를 등록하고, 앱을 찾고, 선택한 화면 방향을 사용하여 IT 지원을 받을 수 있습니다. 사용자가 세로 모드에서 화면을 잠그지 않으면 앱은 화면을 자동으로 검색하고 세로 또는 가로 모드에 맞게 조정합니다.

### <a name="configure-if-enrollment-is-available-in-company-portal-for-android-and-ios---4260128-idready-idstaged---"></a>Android 및 iOS용 회사 포털에서 등록을 사용할 수 있는지 여부 구성<!-- 4260128 idready idstaged -->
Android 및 iOS 디바이스에서 회사 포털의 디바이스 등록을 프롬프트를 통해 제공하거나, 프롬프트 없이 제공하거나, 사용자에게 제공하지 않을지 여부를 구성할 수 있는 새로운 설정을 사용할 수 있습니다. Intune에서 해당 설정을 찾으려면 [Microsoft Endpoint Manager 관리 센터](https://go.microsoft.com/fwlink/?linkid=2109431)로 이동하고 **테넌트 관리** > **사용자 지정**  > **편집** > **디바이스 등록**을 선택합니다. 기존 회사 포털 사용자 지정에 대한 자세한 내용은 [Microsoft Intune 회사 포털 앱을 구성하는 방법](../apps/company-portal-app.md)을 참조하세요.

### <a name="improved-sign-in-experience-in-company-portal-for-android---6103997----"></a>Android용 회사 포털의 향상된 로그인 환경<!-- 6103997  -->
사용자를 위한 더 현대적이고, 단순하고, 깔끔한 환경을 만들기 위해 Android용 회사 포털 앱에 있는 여러 로그인 화면의 레이아웃을 업데이트하고 있습니다.

<!-- ***********************************************-->
## <a name="device-configuration"></a>디바이스 구성

### <a name="wired-network-device-configuration-profiles-for-macos-devices---3508686----"></a>macOS 디바이스의 유선 네트워크 디바이스 구성 프로필<!-- 3508686  -->
유선 네트워크를 구성하는 새로운 macOS 디바이스 구성 프로필을 사용할 수 있습니다(**디바이스 구성** > **프로필** > **프로필 만들기** > **macOS**(플랫폼) > **유선 네트워크**(프로필 유형) 선택). 이 기능을 사용하여 유선 네트워크를 관리하는 802.1x 프로필을 만들고 이 유선 네트워크를 macOS 디바이스에 배포합니다.

적용 대상:
- macOS

### <a name="vpn-profiles-with-ikev2-vpn-connections-can-use-always-on-with-iosipados-devices----1947932----"></a>IKEv2 VPN 연결이 포함된 VPN 프로필이 iOS/iPadOS 디바이스에서 항상 사용할 수 있음 <!-- 1947932  -->
iOS/iPadOS 디바이스에서 IKEv2 연결을 사용하는 VPN 프로필을 만들 수 있습니다(**디바이스 구성** > **프로필** > **프로필 만들기** > **iOS/iPadOS**(플랫폼) > **VPN**(프로필 유형) 선택). 이후 업데이트에서는 IKEv2에 대해 항상 사용하도록 구성할 수 있습니다. 구성된 경우 IKEv2 VPN 프로필은 자동으로 연결되며 VPN에 연결된 상태를 유지합니다(또는 빠르게 다시 연결). 네트워크 간에 이동하거나 디바이스를 다시 시작하는 경우에도 연결된 상태를 유지합니다.

iOS/iPadOS에서 항상 사용 VPN은 IKEv2 프로필로 제한됩니다.

구성할 수 있는 최신 IKEv2 설정은 [Microsoft Intune의 iOS/iPadOS 디바이스에서 VPN 설정 추가](../configuration/vpn-settings-ios.md#ikev2-settings)를 참조하세요.

적용 대상:
- iOS

### <a name="improved-user-interface-experience-when-creating-configuration-profiles-on-iosipados-and-macos-devices---5569008-5569039-5569057-5569110-5569116-5569131-5569139-5569153-5859984----"></a>iOS/iPadOS 및 macOS 디바이스에서 구성 프로필을 만들 때 향상된 사용자 인터페이스 환경<!-- 5569008-5569039-5569057-5569110-5569116-5569131-5569139-5569153-5859984  -->
iOS/iPadOS 또는 macOS 디바이스용 프로필을 만들면 Endpoint Management 관리 센터의 환경이 업데이트됩니다. 이 변경의 영향을 받는 디바이스 구성 프로필은 다음과 같습니다(**디바이스** > **구성 프로필** > **프로필 만들기** > **iOS** 또는 **macOS**(플랫폼) 선택).

- 사용자 지정: iOS/iPadOS, macOS
- 디바이스 기능: iOS/iPadOS, macOS
- 디바이스 제한: iOS/iPadOS, macOS
- Endpoint Protection: macOS
- 확장: macOS
- 기본 설정 파일: macOS

### <a name="improved-user-interface-experience-when-creating-oemconfig-configuration-profiles-on-android-enterprise-devices---5568645-----"></a>Android Enterprise 디바이스에서 OEMConfig 구성 프로필을 만들 때 향상된 사용자 인터페이스 환경<!-- 5568645   -->
Android Enterprise 디바이스용 OEMConfig 프로필을 만들거나 편집하면 Endpoint Management 관리 센터의 환경이 업데이트됩니다. 업데이트된 환경에서는 구성한 설정을 한눈에 요약하여 제공합니다. 이 변경의 영향을 받는 OEMConfig 디바이스 구성 프로필은 다음과 같습니다(**디바이스** > **구성 프로필** > **프로필 만들기** > **Android Enterprise**(플랫폼) > **OEMConfig**(프로필 유형) 선택).

이 기능은 다음에 적용됩니다.
- Android Enterprise 

### <a name="enterprise-app-trust-settings-modification-setting-will-be-removed-from-iosipados-device-restriction-profiles---6225131----"></a>엔터프라이즈 앱 신뢰 설정 수정 설정이 iOS/iPadOS 디바이스 제한 프로필에서 제거됨<!-- 6225131  -->
iOS/iPadOS 디바이스에서 디바이스 제한 사항 프로필을 만듭니다(**디바이스** > **구성 프로필** > **프로필 만들기** > 플랫폼으로 **iOS/iPadOS** > 프로필 유형으로 **디바이스 제한** 선택). **엔터프라이즈 앱 신뢰 설정 수정** 설정은 Apple에서 제거되며 Intune에서 제거됩니다. 현재 프로필에서 이 설정을 사용하는 경우에는 아무런 영향을 주지 않으며 새 프로필을 만들 때까지 프로필을 유지합니다. 이 설정은 Intune의 보고에서도 제거됩니다.

적용 대상:
- iOS/iPadOS

제한할 수 있는 설정을 보려면 [허용하거나 제한하는 iOS 및 iPadOS 디바이스 설정](../configuration/device-restrictions-ios.md)으로 이동합니다.

### <a name="device-configuration-profile-settings-and-values-will-be-updated-for-windows-platforms---4091122---"></a>Windows 플랫폼의 디바이스 구성 프로필 설정 및 값이 업데이트됩니다.<!-- 4091122 -->
Windows 플랫폼의 디바이스 구성 프로필을 만들 경우(**디바이스** > **구성 프로필** > **프로필 만들기** > 플랫폼으로 **Windows** 옵션 선택) 일부 설정과 해당 값은 CSP와 다르며 혼동될 수 있습니다. 설정 이름과 해당 값이 더 분명하게 업데이트됩니다.

적용 대상:

- Windows 10 이상 디바이스 구성 프로필
- Windows Holographic for Business 디바이스 구성 프로필
- Windows 8.1 디바이스 구성 프로필
- Windows Phone 8.1 디바이스 구성 프로필

### <a name="improved-user-interface-experience-when-creating-device-restrictions-profiles-on-android-and-android-enterprise-devices---5841361---"></a>Android 및 Android 엔터프라이즈 디바이스에서 디바이스 제한 프로필을 만들 경우 향상된 사용자 인터페이스 환경<!-- 5841361 -->
Android 또는 Android 엔터프라이즈 디바이스의 프로필을 만들 경우 Endpoint Management 관리 센터의 환경이 업데이트됩니다. 이 변경의 영향을 받는 디바이스 구성 프로필은 다음과 같습니다(**디바이스** > **구성 프로필** > **프로필 만들기** > 플랫폼으로 **Android 디바이스 관리자** 또는 플랫폼으로 **Android 엔터프라이즈** 선택).

- 디바이스 제한: Android 디바이스 관리자
- 디바이스 제한: Android Enterprise 디바이스 소유자
- 디바이스 제한: Android Enterprise 회사 프로필

구성할 수 있는 디바이스 제한에 대한 자세한 내용은 [Android 디바이스 관리자](../configuration/device-restrictions-android.md) 및 [Android 엔터프라이즈](../configuration/device-restrictions-android-for-work.md)를 참조하세요.

### <a name="delete-bundles-and-bundle-arrays-in-oemconfig-device-configuration-profiles-on-android-enterprise-devices---5550355----"></a>Android 엔터프라이즈 디바이스에서 OEMConfig 디바이스 구성의 번들 및 번들 배열 삭제<!-- 5550355  -->
Android 엔터프라이즈 디바이스에서 OEMConfig 프로필을 만들고 업데이트합니다. 사용자는 Intune에서 **구성 디자이너**를 사용하여 번들 및 번들 배열을 삭제할 수 있습니다.

OEMConfig 프로필에 대한 자세한 내용은 [Microsoft Intune에서 OEMConfig를 사용하여 Android 엔터프라이즈 디바이스 사용 및 관리](../configuration/android-oem-configuration-overview.md)를 참조하세요.

이 기능은 다음에 적용됩니다.
- Android Enterprise

### <a name="support-for-wpa-and-wpa2-in-ios-enterprise-wi-fi-profiles--6215273-----"></a>iOS 엔터프라이즈 Wi-Fi 프로필에서 WPA 및 WPA2 지원<!--6215273   -->
[iOS용 엔터프라이즈 Wi-Fi 프로필](../configuration/wi-fi-settings-ios.md)에 ‘보안 유형’ 필드를 추가하고 있습니다(**디바이스** > **구성 프로필** > **프로필 만들기** > ‘플랫폼’으로 **iOS/iPadOS** > ‘프로필’로 **Wi-Fi** 선택).    이는 iOS용 기본 Wi-fi 프로필에 사용할 수 있는 옵션과 유사합니다. 이 변경을 통해 **WPA-Enterprise** 또는 **WPA/WPA2-Enterprise**의 보안 유형을 지정하는 새 프로필을 만든 다음, ‘EAP 형식’의 선택 영역을 지정할 수 있습니다. 

### <a name="new-user-experience-for-certificate-email-vpn-and-wi-fi-profiles---5615208-----"></a>인증서, 메일, VPN 및 Wi-Fi 프로필의 새로운 사용자 환경<!-- 5615208   -->
다음 프로필 유형을 만들고 수정하기 위해 Endpoint Management 관리 센터에서 [사용자 환경](../configuration/device-profile-create.md)을 업데이트했습니다(**디바이스** > **구성 프로필** > **프로필 만들기**). 새 환경은 이전과 동일한 설정을 제공하지만 많은 가로 스크롤이 필요하지 않은 마법사와 비슷한 환경을 사용합니다. 새 환경을 사용하여 기존 구성을 수정할 필요가 없습니다.
- 파생된 자격 증명
- 메일
- PKCS 인증서
- PKCS 가져온 인증서
- SCEP 인증서
- 신뢰할 수 있는 인증서
- VPN
- Wi-Fi

(**디바이스** > **구성 프로필** > **프로필 만들기** > ‘프로필 유형’으로 이전 프로필 선택) 

### <a name="configure-the-microsoft-defender-atp-app-for-macos-----5520115----"></a>macOS용 Microsoft Defender ATP 앱 구성  <!-- 5520115  -->
Endpoint Protection 디바이스 구성 프로필의 일부로 macOS를 실행하는 디바이스용 Microsoft Defender ATP 앱의 [설정](../protect/endpoint-protection-macos.md)을 구성할 수 있습니다(**디바이스** > **구성 프로필** > **프로필 만들기** > ‘플랫폼’으로 **macOS** > ‘프로필 유형’으로 **Endpoint Protection** 선택).   macOS 디바이스 구성을 위한 8개 설정이 있습니다. 

Defender ATP는 macOS 10.13(High Sierra) 이상에서 지원되며 [Microsoft Defender ATP](../apps/apps-advanced-threat-protection-macos.md) 앱은 해당 설정이 적용된 ‘후’ 디바이스에 배포되어야 합니다.  앱이 배포되기 전에 설정을 디바이스에 전송해야 합니다. macOS 베타 버전은 지원되지 않습니다.

### <a name="new-filevault-setting-for-macos-endpoint-protection-device-configuration-policy---5459801-----"></a>macOS Endpoint Protection 디바이스 구성 정책의 새로운 FileVault 설정<!-- 5459801   -->
[macOS Endpoint Protection](../protect/endpoint-protection-macos.md) 템플릿 내의 FileVault 범주에 새 설정을 추가하고 있습니다. 복구 키를 숨깁니다. (**디바이스** > **구성 프로필** > **프로필을 만든 후**, ‘플랫폼’으로 **macOS**를 선택하고 ‘프로필 유형’으로 **Endpoint Protection** 선택).   이 설정은 FileVault 2 암호화 중에 최종 사용자로부터 개인 키를 숨깁니다. 디바이스 사용자는 iOS 회사 포털 앱 또는 암호화된 macOS 디바이스의 회사 포털 웹 사이트에서 언제든지 개인 복구 키를 볼 수 있습니다. 개인 복구 키를 보려면 디바이스 세부 정보로 이동한 다음, ‘복구 키 가져오기’를 클릭합니다. 

이 설정은 이전에 만든 정책에서 사용할 수 없습니다. 이 설정을 사용하도록 구성하려면 FileVault 정책을 다시 만들어야 합니다. 

###  <a name="ui-update-when-configuring-compliance-policy----3961639----"></a>준수 정책을 구성할 경우 UI 업데이트 <!-- 3961639  -->
Microsoft Endpoint Manager에서 준수 정책을 구성하는 UI를 업데이트하고 있습니다(**디바이스** > **준수 정책** > **정책** > **정책 만들기** 선택). 이전에 사용한 것과 동일한 설정 및 세부 정보를 제공하는 새로운 사용자 환경이 표시됩니다. 새 환경은 마법사와 유사한 프로세스에 따라 준수 정책을 만들며, 정책에 대한 ‘할당’을 추가한 후 정책을 만들기 전에 구성을 검토할 수 있는 ‘요약’ 페이지를 포함합니다.   

### <a name="configure-delivery-optimization-agent-when-downloading-win32-app-content---5410945----"></a>Win32 앱 콘텐츠를 다운로드할 경우 전송 최적화 에이전트 구성<!-- 5410945  -->
할당에 따라 배경 또는 전경 모드에서 Win32 앱 콘텐츠를 다운로드하도록 전송 최적화 에이전트를 구성할 수 있습니다. 기존 Win32 앱의 콘텐츠는 배경 모드에서 계속 다운로드됩니다. [Microsoft Endpoint Manager 관리 센터](https://go.microsoft.com/fwlink/?linkid=2109431)에서 **앱** > **모든 앱** > ’Win32 앱 선택’ > **속성**을 선택합니다.  **할당** 옆의 **편집**을 선택합니다.  **필수** 섹션의 **모드** 아래에서 **포함**을 선택하여 할당을 편집합니다.  사용할 수 있게 되면 **앱 설정** 섹션에서 새 설정을 찾습니다. 전송 최적화에 대한 자세한 내용은 [Win32 앱 관리 - 전송 최적화](../apps/apps-win32-app-management.md#delivery-optimization)를 참조하세요.

<!-- ***********************************************-->
<!--## Device enrollment-->

<!-- ***********************************************-->
## <a name="device-management"></a>디바이스 관리

### <a name="change-primary-user-for-windows-devices----3794742---"></a>Windows 디바이스의 기본 사용자 변경 <!-- 3794742 -->
Windows 하이브리드 및 Azure AD 조인 디바이스의 기본 사용자를 변경할 수 있습니다. 이렇게 하려면 **Intune** > **디바이스** > **모든 디바이스**로 이동하고, 디바이스를 선택한 다음, **속성** > **기본 사용자**를 선택합니다.

### <a name="new-android-report-on-android-devices-overview-page---5435435---"></a>Android 디바이스 개요 페이지의 새 Android 보고서<!-- 5435435 -->
각 디바이스 관리 솔루션에 등록된 Android 디바이스 수를 표시하는 Android 디바이스 개요 페이지의 Microsoft Endpoint Manager 관리 콘솔에 보고서를 추가하고 있습니다. Azure 콘솔에 있는 동일한 차트처럼 이 차트에는 회사 프로필, 완전 관리형, 전용 및 디바이스 관리자 등록 디바이스 수가 표시됩니다. 보고서를 보려면 **디바이스** > **Android** > **개요**를 선택합니다.

### <a name="powershell-scripts-support-for-byod-devices---1862833----"></a>BYOD 디바이스의 PowerShell 스크립트 지원<!-- 1862833  -->
PowerShell 스크립트는 Intune에서 Azure AD 등록 디바이스를 지원합니다. PowerShell에 대한 자세한 내용은 [Intune에서 Windows 10 디바이스에 PowerShell 스크립트 사용](../apps/intune-management-extension.md)을 참조하세요. 이 기능은 Windows 10 Home Edition을 실행하는 디바이스를 지원하지 않습니다.

### <a name="additional-data-warehouse-device-inventory-properties---6125732----"></a>추가적인 데이터 웨어하우스 디바이스 인벤토리 속성<!-- 6125732  -->
Intune 데이터 웨어하우스를 통해 추가적인 디바이스 인벤토리 속성을 사용할 수 있습니다. 다음 속성은 [디바이스](../developer/intune-data-warehouse-collections.md#devices) 컬렉션을 통해 공개됩니다.

- 스토리지 용량
- 메모리 용량
- Office 365 버전
- 디바이스 모델

데이터 웨어하우스에 대한 자세한 내용은 [Microsoft Intune 데이터 웨어하우스 API](../developer/reports-nav-intune-data-warehouse.md)를 참조하세요.

### <a name="guide-users-from-android-device-administrator-management-to-work-profile-management--5857738--"></a>Android 디바이스 관리자 관리에서 회사 프로필 관리로 사용자 안내<!--5857738-->
Android 디바이스 관리자 플랫폼의 새 준수 설정을 릴리스하고 있습니다. 이 설정을 사용하면 디바이스 관리자를 통해 관리되는 경우 디바이스를 비규격으로 설정할 수 있습니다.

해당 비규격 디바이스의 **디바이스 설정 업데이트** 페이지에서 사용자에게 **새 디바이스 관리 설치 이동** 메시지가 표시됩니다. **해결** 단추를 탭하면 다음과 같이 안내됩니다.

1. 디바이스 관리자 관리에서 등록 취소
2. 회사 프로필 관리에 등록
3. 준수 문제 해결

Android 엔터프라이즈를 통해 최신의 더 풍부하고 더 안전한 디바이스 관리로 전환하기 위해 Google은 새로운 Android 릴리스에서 디바이스 관리자 지원을 줄이고 있습니다.  Intune은 Android 10 이상~Q2 CY2020을 실행하는 디바이스 관리자 관리형 Android 디바이스만 지원할 수 있습니다. 이 시점 이후에 Android 10 이상을 실행하는 디바이스 관리자 관리형 디바이스(Samsung 제외)는 더 이상 완전히 관리할 수는 없게 됩니다. 특히 영향을 받는 디바이스에는 새 암호 요구 사항이 없습니다. 자세한 내용은 이 [알림](#decreasing-support-for-android-device-administrator)을 참조하세요.

### <a name="retire-noncompliant-devices---1827291---"></a>비준수 디바이스 사용 중지<!-- 1827291 -->
비규격 디바이스를 사용 중지하는 새로운 선택적 준수 작업을 추가하고 있습니다(**디바이스** > **준수 정책** > **정책** > **정책** 선택 > ‘비규격에 대한 작업’ 페이지에서 사용 가능한 ‘작업’ 보기).    비규격 디바이스를 사용 중지하면 모든 회사 데이터가 제거되고 Intune에서 관리되는 디바이스도 제거됩니다. 이 작업은 구성된 값(일)에 도달할 때 실행됩니다. 최소 값은 30일입니다.  관리자가 모든 적격 디바이스를 사용 중지할 수 있는 ‘비규격 디바이스 사용 중지’ 섹션을 사용하여 디바이스를 사용 중지하려면 명시적 IT 관리자 승인이 필요합니다. 

### <a name="new-information-in-device-details---5604099---"></a>디바이스 세부 정보의 새로운 정보<!-- 5604099 -->
디바이스의 **개요** 페이지에 다음 정보가 제공됩니다.

- 스토리지 용량(디바이스의 실제 스토리지 양)
- 메모리 용량(디바이스의 실제 메모리 양)

### <a name="script-support-for-macos-devices---4280361----"></a>macOS 디바이스에 대한 스크립트 지원<!-- 4280361  -->
macOS 디바이스에 스크립트를 추가하고 배포할 수 있습니다. 이 지원은 macOS 디바이스에서 기본 MDM 기능을 사용하여 가능한 작업 이상으로 macOS 디바이스 구성 기능을 확장합니다.

<!-- ***********************************************-->
<!--## Intune apps-->
 

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
## <a name="monitor-and-troubleshoot"></a>모니터링 및 문제 해결

### <a name="help-and-support-workflow-update-to-support-additional-services---5654170---"></a>추가 서비스를 지원하기 위한 도움말 및 지원 워크플로 업데이트<!-- 5654170 -->
특정 지원을 더 잘 제공하기 위해 사용하는 관리 유형을 선택할 수 있도록 Microsoft Endpoint Manager 관리 센터에서 도움말 및 지원 페이지를 업데이트하고 있습니다(**문제 해결 + 지원** >  **도움말 및 지원** 선택). 이 변경을 통해 다음 관리 유형 중에서 선택할 수 있습니다.
- Configuration Manager(Desktop Analytics 포함)
- Intune
- 공동 관리

<!-- ***********************************************-->
<!--
## Role-based access control
-->

<!-- ***********************************************-->
## <a name="security"></a>보안

### <a name="derived-credentials-support-on-android-cobo-devices--4839592--"></a>Android COBO 디바이스에서 파생된 자격 증명 지원<!--4839592-->
Android Enterprise 완전 관리형 디바이스에서 파생된 자격 증명을 사용할 수 있습니다. Entrust Datacard, Intercede 및 DISA Purebred에 대해 파생된 자격 증명을 검색하기 위한 지원이 포함됩니다. 지원하는 앱에서 앱 인증, Wi-Fi, VPN 또는 S/MIME 서명 및/또는 암호화를 위해 파생된 자격 증명을 사용할 수 있습니다.

### <a name="use-antivirus-policy-to-manage-settings-for-microsoft-defender-antivirus-and-the-windows-security-experience--6131401---"></a>바이러스 백신 정책을 사용하여 Microsoft Defender 바이러스 백신 및 Windows 보안 환경의 설정을 관리합니다.<!--6131401 -->
‘Endpoint security’ 노드에서 **바이러스 백신**의 설정을 구성할 수 있습니다.  바이러스 백신 정책을 구성할 때 다음 두 가지 프로필 유형을 통해 Windows 10 디바이스의 설정을 정의합니다.

- Microsoft Defender 바이러스 백신: 클라우드 보호, 바이러스 백신 제외, 업데이트 관리, 검사 옵션 등의 설정을 관리합니다.
- Windows 보안 환경: 사용자가 디바이스에서 Windows 보안 설정을 사용하는 방식을 관리합니다. 최종 사용자가 Microsoft Defender 보안 센터에서 볼 수 있는 항목과 수신하는 알림을 구성할 수 있습니다.

### <a name="users-personal-encrypted-recovery-key---6273943---"></a>사용자의 암호화된 개인 복구 키<!-- 6273943 -->
사용자가 Android 회사 포털 애플리케이션 또는 Android Intune 애플리케이션을 통해 Mac 디바이스용 암호화된 **FileVault** 개인 복구 키를 검색할 수 있도록 하는 새로운 Intune 기능을 사용할 수 있습니다. 회사 포털 애플리케이션 및 Intune 애플리케이션에는 둘 다 사용자가 자신의 전체 Mac 디바이스에 액세스하는 데 필요한 **FileVault** 복구 키를 볼 수 있는 웹 회사 포털로 Chrome 브라우저가 열리는 링크가 있습니다. 암호화에 대한 자세한 내용은 [Intune에서 디바이스 암호화 사용](../protect/encrypt-devices.md)을 참조하세요.

### <a name="privacy-preferences-settings-for-macos-devices---2934232---"></a>macOS 디바이스의 프라이버시 기본 설정<!-- 2934232 --> 
macOS Catalina 10.15 릴리스를 통해 Apple은 새로운 보안 및 프라이버시 개선 사항을 추가했습니다. 기본적으로 애플리케이션 및 프로세스는 사용자 동의 없이 특정 데이터에 액세스할 수 없습니다. 사용자가 동의를 제공하지 않으면 애플리케이션 및 프로세스가 작동하지 않을 수 있습니다. Intune은 IT 관리자가 macOS 10.14 이상을 실행하는 디바이스에서 최종 사용자를 대신하여 데이터 액세스 동의를 허용하거나 거부할 수 있도록 하는 설정 지원을 추가하고 있습니다. 해당 설정을 사용하면 애플리케이션 및 프로세스가 계속 제대로 작동하며 최종 사용자에게 표시되는 프롬프트 수가 감소합니다.

### <a name="updated-ui-text-and-labels-for-windows-10-endpoint-protection-profile-settings---5983747---"></a>Windows 10 Endpoint Protection 프로필 설정의 업데이트된 UI 텍스트 및 레이블<!-- 5983747 -->
설정의 의도된 용도 및 결과를 더 쉽게 이해할 수 있도록 Windows 10 디바이스 구성 프로필로 구성하는 다양한 설정의 텍스트를 업데이트하고 있습니다.

업데이트 중인 설정에는 다음의 Windows 10 디바이스 구성 프로필이 포함됩니다.

- [디바이스 제한](../configuration/device-restrictions-windows-10.md#microsoft-defender-antivirus) > Microsoft Defender 바이러스 백신  
- [Endpoint Protection](../protect/endpoint-protection-windows-10.md) > Microsoft Defender 바이러스 백신

Intune에서 지원되는 설정은 변경되지 않습니다. 이는 Microsoft Endpoint Management 관리 센터의 UI 텍스트에 대한 업데이트일 뿐입니다.

<!-- ***********************************************-->
## <a name="notices"></a>알림

[!INCLUDE [Intune notices](../includes/intune-notices.md)]

## <a name="see-also"></a>참고 항목

최근 개발 작업에 대한 자세한 내용은 [Microsoft Intune의 새로운 기능](whats-new.md)을 참조하세요.
