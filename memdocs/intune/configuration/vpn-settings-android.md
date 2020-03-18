---
title: Microsoft Intune에서 Android 디바이스에 대한 VPN 설정 사용 - Azure | Microsoft Docs
description: Microsoft Intune의 Android 디바이스에서 VPN 연결을 만드는 모든 설정을 참조하세요. VPN 서버의 연결 이름, IP 주소 또는 FQDN을 입력하고, 사용자가 인증하는 방법을 선택하며 Citrix, SonicWall, Check Point 캡슐 및 Pulse Secure 연결 형식을 선택합니다.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 02/18/2020
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: d31d83aff2bc2dc6c0c62c46220bf73b430a912c
ms.sourcegitcommit: 3d895be2844bda2177c2c85dc2f09612a1be5490
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79360472"
---
# <a name="android-device-settings-to-configure-vpn-in-intune"></a>Intune에서 VPN을 구성하는 Android 디바이스 설정

이 문서에서는 Android 디바이스에서 제어할 수 있는 다양한 메일 설정을 나열하고 설명합니다. MDM(모바일 디바이스 관리) 솔루션의 일환으로 이러한 설정을 사용하여 VPN 연결을 만들고, VPN에서 인증하는 방법, VPN 서버 유형 등을 선택합니다.

Intune 관리자는 VPN 설정을 만들어 Android 디바이스에 할당할 수 있습니다. 

Intune의 VPN 프로필에 대한 자세한 내용은 [VPN 프로필](vpn-settings-configure.md)을 참조하세요.

## <a name="before-you-begin"></a>시작하기 전에

[디바이스 구성 프로필을 만들고](vpn-settings-configure.md#create-a-device-profile), **Android**를 선택합니다.

## <a name="base-vpn"></a>기본 VPN

- **연결 이름**: 이 연결의 이름을 입력합니다. 최종 사용자는 디바이스에서 사용 가능한 VPN 연결을 검색할 때 이 이름을 볼 수 있습니다. 예를 들어 다음과 같이 입력합니다. `Contoso VPN`
- **IP 주소 또는 FQDN**: 디바이스가 연결되는 VPN 서버의 IP 주소 또는 FQDN(정규화된 도메인 이름)을 입력합니다. 예를 들어 **192.168.1.1** 또는 **vpn.contoso.com**을 입력합니다.

  - **인증 방법**: 디바이스가 VPN 서버에 인증하는 방법을 선택합니다. 옵션은 다음과 같습니다.

    - **인증서**: 연결을 인증할 기존 SCEP 또는 PKCS 인증서 프로필을 선택합니다. [인증서 구성](../protect/certificates-configure.md)에는 인증서 프로필을 만드는 단계가 나열됩니다.
    - **사용자 이름 및 암호**: VPN 서버에 로그인할 때 최종 사용자에게 사용자 이름과 암호를 입력하라는 메시지가 표시됩니다.

- **연결 형식**: VPN 연결 형식을 선택합니다. 옵션은 다음과 같습니다.

  - **검사점 캡슐 VPN**
  - **Cisco AnyConnect**
  - **SonicWall Mobile Connect**
  - **F5 Access**
  - **Pulse Secure**
  - **Citrix SSO**

- **지문**(검사점 캡슐 VPN에만 해당): VPN 서버를 신뢰할 수 있는지 확인하려면 **Contoso 지문 코드**와 같은 문자열을 입력합니다. 클라이언트가 동일한 지문을 가진 서버를 신뢰하도록 지문이 클라이언트에 전송됩니다. 디바이스에 지문이 없으면, 사용자에게 지문을 보여주면서 VPN 서버를 신뢰할 것인지 묻는 메시지가 표시됩니다. 사용자는 지문을 수동으로 확인한 후 연결할 신뢰를 선택합니다.
- **Citrix VPN 특성에 대한 키 및 값 쌍 입력**(Citrix에만 해당): Citrix에서 제공하는 키 및 값 쌍을 입력합니다. 이러한 값은 VPN 연결의 속성을 구성합니다. 

  키와 값 쌍을 사용하여 쉼표로 구분된 값 파일(.csv)을 **가져올** 수도 있습니다. **내 데이터에 헤더** 및 **키** 속성이 있는지 검토해야 합니다.

  키와 값 쌍을 추가한 후에는 **내보내기**를 사용하여 데이터를 .csv 파일로 백업합니다.

## <a name="next-steps"></a>다음 단계

[프로필을 할당](device-profile-assign.md)하고, 해당 [상태를 모니터링](device-profile-monitor.md)합니다.

[Android Enterprise](vpn-settings-android-enterprise.md), [iOS/iPadOS](vpn-settings-ios.md), [macOS](vpn-settings-macos.md), [Windows 10 및 이후 버전](vpn-settings-windows-10.md), [Windows 8.1](vpn-settings-windows-8-1.md) 및 [Windows Phone 8.1](vpn-settings-windows-phone-8-1.md) 디바이스에 대한 VPN 프로필을 만들 수도 있습니다.
