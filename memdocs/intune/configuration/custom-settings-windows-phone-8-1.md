---
title: Microsoft Intune에서 Windows Phone 8.1 디바이스에 사용자 지정 설정 추가- Azure | Microsoft Docs
titleSuffix: ''
description: Microsoft Intune에서 Windows Phone 8.1을 실행하는 디바이스에 OMA-URI 설정을 사용하려면 사용자 지정 프로필을 추가하거나 만듭니다.
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
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: b1bea9047d65faf449c77e1a677000d32e883a76
ms.sourcegitcommit: 3d895be2844bda2177c2c85dc2f09612a1be5490
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79364528"
---
# <a name="use-custom-settings-for-windows-phone-81-devices-in-intune"></a>Intune에서 Windows Phone 8.1 디바이스에 대한 사용자 지정 설정 사용

Microsoft Intune을 사용하면 "사용자 지정 프로필"을 사용하여 Windows Phone 8.1 디바이스에 대한 사용자 지정 설정을 추가하거나 만들 수 있습니다. 사용자 지정 프로필은 Intune의 기능입니다. Intune에 기본 제공되지 않은 디바이스 설정 및 기능을 추가하도록 설계되었습니다.

Windows Phone 8.1 사용자 지정 프로필은 OMA-URI(Open Mobile Alliance Uniform Resource Identifier) 설정을 사용하여 다른 기능을 구성합니다. 이러한 설정은 일반적으로 모바일 디바이스 제조업체에서 디바이스에서 기능을 제어하기 위해 사용합니다. [Windows Phone 8.1 MDM 프로토콜 설명서](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-phone/dn499787(v=technet.10))에 설정이 나열됩니다.

이 문서는 Windows Phone 8.1 디바이스의 사용자 지정 프로필을 만드는 방법을 보여줍니다. 

## <a name="create-the-profile"></a>프로필 만들기

1. [Microsoft Endpoint Manager 관리 센터](https://go.microsoft.com/fwlink/?linkid=2109431)에 로그인합니다.
2. **디바이스 구성** > **구성 프로필** > **프로필 만들기**를 선택합니다.
3. 다음 설정을 입력합니다.

    - **이름**: 프로필에 대한 설명이 포함된 이름을 입력합니다. 나중에 쉽게 식별할 수 있도록 프로필 이름을 지정합니다. 예를 들어 좋은 프로필 이름은 **Windows Phone 사용자 지정 프로필**입니다.
    - **설명**: 설정에 대한 개요와 기타 중요한 모든 세부 정보를 제공하는 설명을 입력합니다.
    - **플랫폼**: **Windows Phone 8.1**을 선택합니다.
    - **프로필 유형**: **사용자 지정**을 선택합니다.

4. **사용자 지정 OMA-URI 설정**에서 **추가**를 선택합니다. 다음 설정을 입력합니다.

    - **이름**: 설정 목록에서 쉽게 식별할 수 있도록 OMA-URI 설정에 대한 고유한 이름을 입력합니다.
    - **설명**: 설정 개요를 제공하는 설명과 프로필을 찾는 데 도움이 되는 기타 관련 정보를 입력합니다.
    - **OMA-URI**(대/소문자 구분): 설정으로 사용하려는 OMA-URI를 입력합니다.
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

다음 예에서 Windows 8.1 Phone 디바이스는 이동 통신 사업자 커버리지 영역 밖으로 이동할 경우 셀룰러 네트워크를 변경할 수 없습니다.

- **이름**: 셀룰러 데이터 로밍 허용
- **설명**: 셀룰러 데이터 로밍 허용 또는 허용 안 함
- **OMA-URI**(대/소문자 구분): ./Vendor/MSFT/PolicyManager/My/Connectivity/AllowCellularDataRoaming
- **데이터 형식**: 정수
- **값**: 0

## <a name="next-steps"></a>다음 단계

프로필이 만들어지지만 아직 아무것도 하지 않습니다. 다음으로, [프로필을 할당](device-profile-assign.md)하고, [해당 상태를 모니터링](device-profile-monitor.md)합니다.

[Windows 10 디바이스에 대한 사용자 지정 프로필](custom-settings-windows-10.md)을 만듭니다.
