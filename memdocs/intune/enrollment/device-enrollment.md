---
title: Microsoft Intune 디바이스 등록이란?
titleSuffix: Microsoft Intune
description: iOS/iPadOS, Android 및 Windows 디바이스에 대한 등록을 알아봅니다.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 4/24/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 6f67fcd2-5682-4f9c-8d74-d4ab69dc978c
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: 8a81d0cad6e7fa985733675912ada6f446eb501d
ms.sourcegitcommit: 3d895be2844bda2177c2c85dc2f09612a1be5490
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79359406"
---
# <a name="what-is-device-enrollment"></a>디바이스 등록이란?
[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Intune을 사용하여 직원의 디바이스 및 앱을 관리하고 회사 데이터에 액세스하는 방법을 관리할 수 있습니다. 이 모바일 디바이스 관리(MDM)를 사용하려면 먼저 디바이스를 Intune 서비스에 등록해야 합니다. 디바이스가 등록되면 MDM 인증서가 발급됩니다. 이 인증서는 Intune 서비스와 통신하는 데 사용됩니다.

다음 표에서 볼 수 있듯이 직원의 디바이스를 등록하는 몇 가지 방법이 있습니다. 각 방법은 디바이스의 소유권(개인 또는 회사), 기기 유형(iOS, Windows, Android) 및 관리 요구 사항(재설정, 선호도, 잠금)에 따라 다릅니다.

기본적으로 모든 플랫폼의 디바이스를 Intune에서 등록할 수 있습니다. 그러나 [플랫폼별로 디바이스를 제한](enrollment-restrictions-set.md#create-a-device-type-restriction)할 수 있습니다.

## <a name="iosipados-enrollment-methods"></a>iOS/iPadOS 등록 방법

| **방법** | **초기화 필요** | [**사용자 선호도**](device-enrollment-program-enroll-ios.md#create-an-apple-enrollment-profile) | **Locked** | **세부 정보** |
|:---:|:---:|:---:|:---:|:---:|
| | 디바이스는 등록 중 초기화됩니다. | 각 디바이스를 사용자와 연결합니다.| '예'인 경우 사용자는 디바이스 등록을 해제할 수 없습니다. | |
|**[BYOD](#bring-your-own-device)** | 아니요| 예 | 아니요 | [추가 정보](apple-mdm-push-certificate-get.md)|
|**[DEM](#device-enrollment-manager)**| 아니요 |아니요 |아니요 | [추가 정보](device-enrollment-program-enroll-ios.md)|
|**[DEP](#apple-device-enrollment-program)**| 예 | 선택 사항 | 선택 사항|[추가 정보](device-enrollment-program-enroll-ios.md)|
|**[USB-SA](#usb-sa)**| 예 | 선택 사항 | 아니요| [추가 정보](apple-configurator-enroll-ios.md)|
|**[USB-Direct](#usb-direct)**| 아니요 | 아니요 | 아니요|[추가 정보](apple-configurator-enroll-ios.md)|

## <a name="macos-enrollment-methods"></a>macOS 등록 방법
| **방법** |  **초기화 필요** |  **사용자 선호도** | **잠김** | **세부 정보**|
|:---:|:---:|:---:|:---:|:---:|
|**[BYOD](#bring-your-own-device)** | 아니요| 예 | 아니요 | [추가 정보](macos-enroll.md)|
|**[DEM](#device-enrollment-manager)**| 아니요 |아니요 |아니요  | [추가 정보](device-enrollment-manager-enroll.md)|
|**[DEP](#apple-device-enrollment-program)**| 예 | 선택 사항 | 선택 사항|[추가 정보](device-enrollment-program-enroll-macos.md)|

## <a name="windows-enrollment-methods"></a>Windows 등록 방법

| **방법** | **초기화 필요** | **사용자 선호도** | **잠김** | **세부 정보**|
|:---:|:---:|:---:|:---:|:---:|:---:|
|**[BYOD](#bring-your-own-device)** | 아니요 | 예 | 아니요 | [추가 정보](windows-enroll.md)|
|**[DEM](#device-enrollment-manager)**| 아니요 |아니요 |아니요 |[추가 정보](device-enrollment-manager-enroll.md)|
|**자동 등록** | 아니요 |예 |아니요 | [추가 정보](windows-enroll.md#enable-windows-10-automatic-enrollment)|
|**Autopilot** |예 |예 |아니요 | [추가 정보](enrollment-autopilot.md)
|**대량 등록** |아니요 |아니요 |아니요 | [추가 정보](windows-bulk-enroll.md) |
|**공동 관리** |아니요 |예 |아니요 | [추가 정보](https://docs.microsoft.com/configmgr/core/clients/manage/co-management-overview)
|**GPO** |아니요 |예 |아니요 | [추가 정보](https://docs.microsoft.com/windows/client-management/mdm/enroll-a-windows-10-device-automatically-using-group-policy)

## <a name="android-enrollment-methods"></a>Android 등록 방법

| **개인** | **등록 방법** | **초기화 필요** | **사용자 선호도** | **잠김** | **세부 정보**|
|:---:|:---:|:---:|:---:|:---:|:---:|
|**Android 디바이스 관리자**|**회사 포털을 통해 사용자 시작** | 아니요 | 예 | 아니요 | [추가 정보](https://docs.microsoft.com/user-help/enroll-device-android-company-portal)|
|**Android Enterprise 회사 프로필**|**회사 포털을 통해 사용자 시작**| 아니요 | 예 | 아니요 | [추가 정보](android-work-profile-enroll.md)|


| **회사** | **등록 방법** | **초기화 필요** | **사용자 선호도** | **잠김** | **세부 정보**|
|:---:|:---:|:---:|:---:|:---:|:---:|
|**Android 디바이스 관리자**|**회사 포털을 통해 [DEM](#device-enrollment-manager) 시작**| 아니요 | 아니요 | 아니요 |[추가 정보](device-enrollment-manager-enroll.md)|
|**Android 디바이스 관리자**|**(미리 선언된 IMEI 또는 SN) 회사 포털을 통해 사용자 시작**| 아니요 | 예 | 아니요 | [추가 정보](corporate-identifiers-add.md)|
|**Zebra Mobility 확장을 사용하는 Android 디바이스 관리자**|**회사 포털을 통해 사용자 또는 [DEM](#device-enrollment-manager) 시작**| 아니요 | 사용자 시작이면 예, [DEM](#device-enrollment-manager) 시작이면 아니요 | 아니요 | [추가 정보](../configuration/android-zebra-mx-overview.md)|
|**Android Enterprise 전용**|**NFC, 토큰, QR 코드, Zero Touch**| 예 | 아니요 | 정책을 통해 구성 가능 | [추가 정보](android-kiosk-enroll.md)|
|**Android 엔터프라이즈 완전 관리형**|**NFC, 토큰, QR 코드, Zero Touch**| 예 | 예 | 정책을 통해 구성 가능 | [추가 정보](android-dedicated-devices-fully-managed-enroll.md)|


## <a name="bring-your-own-device"></a>Bring Your Own Device
BYOD(Bring Your Own Device)에는 개인적으로 소유한 전화, 태블릿, PC 등이 있습니다. 사용자는 회사 포털 앱을 설치 및 실행하여 BYOD를 등록합니다. 사용자는 이 프로그램을 통해 전자 메일 등의 회사 리소스에 액세스할 수 있습니다.

## <a name="corporate-owned-device"></a>회사 소유 디바이스
[COD(회사 소유 디바이스)](corporate-identifiers-add.md)에는 회사가 직원에게 배포한 전화, 태블릿, PC가 있습니다. COD 등록은 자동 등록, 공유 디바이스 또는 사전 승인된 등록 요구 사항과 같은 관리 시나리오를 지원합니다. COD를 등록하는 일반적인 방법은 관리자가 디바이스 등록 관리자(DEM)를 사용하는 것입니다. Apple에서 제공한 장비 등록 프로그램(DEP) 도구를 통해 iOS/iPadOS 디바이스를 직접 등록할 수 있습니다. IMEI 번호가 있는 디바이스도 회사 소유로 식별되고 태그가 지정됩니다.

### <a name="device-enrollment-manager"></a>디바이스 등록 관리자
DEM(디바이스 등록 관리자)은 회사 소유 디바이스를 여러 개 등록하여 관리할 수 있는 특수 사용자 계정입니다. 관리자는 회사 포털을 설치하고 사용자 정보가 없는 디바이스를 여러 대 등록할 수 있습니다. 이러한 디바이스 유형은 예를 들어 POS(Point-Of-Sale) 또는 유틸리티 앱에는 유용하지만 이메일 또는 회사 리소스에 액세스해야 하는 사용자에게는 유용하지 않습니다. [DEM](device-enrollment-manager-enroll.md)에 대해 자세히 알아보세요.

### <a name="apple-device-enrollment-program"></a>Apple 장비 등록 프로그램
Apple DEP(장비 등록 프로그램) 관리를 통해 정책을 만들고 구입 후 DEP로 관리하는 iOS/iPadOS 및 macOS 디바이스에 "무선으로" 정책을 배포할 수 있습니다. 사용자가 처음으로 디바이스를 켜고 설치 도우미를 실행하면 디바이스가 등록됩니다. 이 방법은 iOS/iPadOS 감독 모드를 지원하며, 이 모드에서는 특정 기능을 사용하여 디바이스를 구성할 수 있습니다.

iOS/iPadOS DEP 등록에 대한 자세한 내용은 다음을 참조하세요.

- [iOS/iPadOS 디바이스를 등록하는 방법 선택](ios-enroll.md)
- [디바이스 등록 프로그램을 사용하여 iOS/iPadOS 디바이스 등록](device-enrollment-program-enroll-ios.md)

### <a name="usb-sa"></a>USB-SA
IT 관리자는 USB를 통해 Apple Configurator를 사용하여 등록할 각 회사 소유 디바이스를 설정 도우미를 사용하여 수동으로 준비합니다. IT 관리자는 등록 프로필을 만들어 Apple Configurator로 내보냅니다. 사용자가 디바이스를 받으면 설정 도우미를 실행하여 디바이스를 등록하라는 메시지가 표시됩니다. 이 방법은 **iOS 감독** 모드를 지원하며, 이 모드에서는 다음 기능을 사용할 수 있습니다.
- 잠긴 등록
- 키오스크 모드와 다른 고급 구성 및 제한 사항

설정 도우미를 사용한 iOS/iPadOS Apple Configurator 등록에 대한 자세한 내용은 다음을 참조하세요.

- [iOS/iPadOS 디바이스를 등록하는 방법 결정](ios-enroll.md)
- [Configurator 및 설정 도우미를 사용하여 iOS/iPadOS 디바이스 등록](apple-configurator-enroll-ios.md)

### <a name="usb-direct"></a>USB-Direct
직접 등록의 경우 관리자가 등록 정책을 만들고 Apple Configurator로 내보내어 각 디바이스를 수동으로 등록해야 합니다. USB로 연결된 회사 소유의 디바이스는 직접 등록되고 초기화할 필요가 없습니다. 디바이스는 사용자가 지정되지 않은 디바이스로 관리됩니다. 디바이스는 잠기거나 감독되지 않으며 조건부 액세스, 탈옥 검색, 모바일 애플리케이션 관리를 지원할 수 없습니다.

iOS/iPadOS 등록에 대한 자세한 내용은 다음을 참조하세요.

- [iOS/iPadOS 디바이스를 등록하는 방법 결정](ios-enroll.md)
- [Configurator 및 직접 등록을 사용하여 iOS/iPadOS 디바이스 등록](apple-configurator-enroll-ios.md)

## <a name="mobile-device-cleanup-after-mdm-certificate-expiration"></a>MDM 인증서 만료 후 모바일 디바이스 정리

MDM 인증서는 모바일 디바이스가 Intune 서비스와 통신할 때 자동으로 갱신됩니다. 모바일 디바이스가 초기화되거나 일정 기간 동안 Intune 서비스와 통신하지 못한 경우에는 MDM 인증서가 갱신되지 않습니다. MDM 인증서가 만료되고 180일 후 Azure Portal에서 디바이스가 제거됩니다.
