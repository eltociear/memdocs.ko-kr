---
title: Microsoft Intune에서 Android 엔터프라이즈 디바이스에 사용자 지정 설정 추가 - Azure | Microsoft Docs
description: Microsoft Intune에서 만들 Android 엔터프라이즈 디바이스에 대한 사용자 지정 프로필을 추가하거나 만듭니다.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 12/18/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 4724d6e5-05e5-496c-9af3-b74f083141f8
ms.reviewer: chrisbal
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 827b5eb8b65aa59212b9ef990def3c5f191baf7c
ms.sourcegitcommit: 3d895be2844bda2177c2c85dc2f09612a1be5490
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79334433"
---
# <a name="use-custom-settings-for-android-enterprise-devices-in-microsoft-intune"></a>Microsoft Intune의 Android 엔터프라이즈 디바이스에 대한 사용자 지정 설정 사용

Microsoft Intune을 사용하면 "사용자 지정 프로필"을 사용하여 Android 엔터프라이즈 회사 프로필에 대한 사용자 지정 설정을 추가하거나 만들 수 있습니다. 사용자 지정 프로필은 Intune의 기능입니다. Intune에 기본 제공되지 않은 디바이스 설정 및 기능을 추가하도록 설계되었습니다.

Android 엔터프라이즈 사용자 지정 프로필은 OMA-URI(Open Mobile Alliance Uniform Resource Identifier) 설정을 사용하여 Android 엔터프라이즈에서 기능을 제어합니다. 이러한 설정은 일반적으로 모바일 디바이스 제조업체에서 이러한 기능을 제어하기 위해 사용합니다.

Intune은 다음과 같은 제한된 수의 Android Enterprise 사용자 지정 프로필을 지원합니다.

- ./Vendor/MSFT/WiFi/Profile/SSID/Settings: [미리 공유한 키를 사용하여 Wi-Fi 프로필 만들기](wi-fi-profile-shared-key.md)에는 몇 가지 예제가 있습니다.
- ./Vendor/MSFT/VPN/Profile/Name/PackageList: [앱별 VPN 프로필 만들기](android-pulse-secure-per-app-vpn.md)에는 몇 가지 예제가 있습니다.
- ./Vendor/MSFT/WorkProfile/DisallowCrossProfileCopyPaste: 이 문서의 [예제](#example)를 참조하세요. 이 설정은 사용자 인터페이스에서도 사용할 수 있습니다. 자세한 내용은 [기능을 허용하거나 제한하는 Android 엔터프라이즈 디바이스 설정](device-restrictions-android-for-work.md)을 참조하세요.

추가 설정이 필요한 경우 [Android Enterprise용 OEMConfig](android-oem-configuration-overview.md)를 참조하세요.

이 문서는 Android 엔터프라이즈 디바이스의 사용자 지정 프로필을 만드는 방법을 보여줍니다. 또한 복사 및 붙여넣기 기능을 차단하는 사용자 지정 프로필의 예를 제공합니다.

## <a name="create-the-profile"></a>프로필 만들기

1. [Microsoft Endpoint Manager 관리 센터](https://go.microsoft.com/fwlink/?linkid=2109431)에 로그인합니다.
2. **디바이스 구성** > **구성 프로필** > **프로필 만들기**를 선택합니다.
3. 다음 설정을 입력합니다.

    - **이름**: 프로필에 대한 설명이 포함된 이름을 입력합니다. 나중에 쉽게 식별할 수 있도록 프로필 이름을 지정합니다. 예를 들어 좋은 프로필 이름은 **Android Enterprise custom profile**입니다.
    - **설명**: 프로필에 대한 설명을 입력합니다. 이 설정은 선택 사항이지만 권장됩니다.
    - **플랫폼**: **Android Enterprise**를 선택합니다.
    - **프로필 유형**: **사용자 지정**을 선택합니다.

4. **사용자 지정 OMA-URI 설정**에서 **추가**를 선택합니다. 다음 설정을 입력합니다.

    - **이름**: 쉽게 찾을 수 있도록 OMA-URI 설정에 대한 고유 이름을 입력합니다.
    - **설명**: 설정에 대한 개요와 기타 중요한 모든 세부 정보를 제공하는 설명을 입력합니다.
    - **OMA URI** 설정으로 사용하려는 OMA-URI를 입력합니다.
    - **데이터 형식**: 이 OMA-URI 설정에 사용할 데이터 형식을 선택합니다. 옵션은 다음과 같습니다.

      - 문자열
      - 문자열(XML 파일)
      - 날짜 및 시간
      - 정수
      - 부동 소수점
      - 부울
      - Base64(파일)

    - **값**: 입력한 OMA-URI와 연결할 데이터를 입력합니다. 값은 선택한 데이터 형식에 따라 달라집니다. 예를 들어, **날짜 및 시간**을 선택한 경우 날짜 선택에서 값을 선택합니다.

    일부 설정을 추가한 후 **내보내기**를 선택할 수 있습니다. **내보내기**는 쉼표로 구분된 값(.csv) 파일에서 추가한 모든 값의 목록을 만듭니다.

5. **확인**을 선택하여 변경 내용을 저장합니다. 필요에 따라 더 많은 설정을 계속 추가합니다.
6. 완료되면 **확인** > **만들기**를 선택하여 Intune 프로필을 만듭니다. 완료되면 프로필이 **디바이스 - 구성 프로필** 목록에 표시됩니다.

## <a name="example"></a>예제

이 예에서는 Android 엔터프라이즈 디바이스에서 회사와 개인 앱 간에 복사 및 붙여넣기 작업을 제한하는 사용자 지정 프로필을 만듭니다.

1. [Microsoft Endpoint Manager 관리 센터](https://go.microsoft.com/fwlink/?linkid=2109431)에 로그인합니다.
2. **디바이스 구성** > **구성 프로필** > **프로필 만들기**를 선택합니다.
3. 다음 설정을 입력합니다.

    - **이름**: 프로필에 대한 설명이 포함된 이름을 입력합니다. 나중에 쉽게 식별할 수 있도록 프로필 이름을 지정합니다. 예를 들어 **android ent block copy paste custom profile**을 입력합니다.
    - **설명**: 프로필에 대한 설명을 입력합니다. 이 설정은 선택 사항이지만 권장됩니다.
    - **플랫폼**: **Android Enterprise**를 선택합니다.
    - **프로필 유형**: **사용자 지정**을 선택합니다.

4. **사용자 지정 OMA-URI 설정**에서 **추가**를 선택합니다. 다음 설정을 입력합니다.

    - **이름**: `Block copy and paste` 등을 입력합니다.
    - **설명**: `Blocks copy/paste between work and personal apps` 등을 입력합니다.
    - **OMA URI** `./Vendor/MSFT/WorkProfile/DisallowCrossProfileCopyPaste`를 입력합니다.
    - **데이터 형식**: 이 OMA-URI의 값이 **True** 또는 **False**가 되도록 **부울**을 선택합니다.
    - **값**: **True**를 선택합니다.

5. 설정을 입력하면, 환경은 다음 이미지와 비슷해야 합니다.

    ![Android 회사 프로필에 대한 복사 및 붙여넣기 기능 차단](./media/custom-settings-android-for-work/custom-policy-afw-copy-paste.png)

관리하는 Android 엔터프라이즈 디바이스에 이 프로필을 할당하면 회사 프로필과 개인 프로필에 있는 앱 간의 복사 및 붙여넣기 기능이 차단됩니다.

## <a name="next-steps"></a>다음 단계

프로필이 만들어지지만 아직 아무것도 하지 않습니다. 다음으로, [프로필을 할당](device-profile-assign.md)하고, [해당 상태를 모니터링](device-profile-monitor.md)합니다.

[Android 디바이스에 대한 사용자 지정 프로필](custom-settings-android.md)을 만듭니다.
