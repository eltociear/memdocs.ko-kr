---
title: Microsoft Intune에서 SCEP 또는 PKCS 인증 제거 - Azure | Microsoft Docs
titleSuffix: ''
description: 관리자는 초기화 또는 사용 중지 조치를 사용하여 Microsoft Intune에서 인증서를 제거할 수 있습니다 디바이스 등록 취소 또는 준수 정책 제거 등 인증서가 자동으로 제거되는 시나리오가 있습니다. Intune 라이선스를 분실하거나 제거한 경우와 같이 인증서가 디바이스에 자동으로 남아 있는 시나리오도 있습니다. Android, Android 엔터프라이즈, iOS/iPadOS, macOS 및 Windows 디바이스에 대한 다양한 방법을 참조하세요.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 11/21/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.reviewer: lacranda
ms.openlocfilehash: cba46d5b4b203cdbb67fb5f6b6b116a21ebacb32
ms.sourcegitcommit: 3d895be2844bda2177c2c85dc2f09612a1be5490
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79338931"
---
# <a name="remove-scep-and-pkcs-certificates-in-microsoft-intune"></a>Microsoft Intune에서 SCEP 및 PKCS 인증서 제거

Microsoft Intune에서 SCEP(단순 인증서 등록 프로토콜) 및 PKCS(공개 키 암호화 표준) 인증서 프로필을 사용하여 디바이스에 인증서를 추가할 수 있습니다.

이 인증서는 디바이스를 [초기화](../remote-actions/devices-wipe.md#wipe)하거나 [사용 중지](../remote-actions/devices-wipe.md#retire)하는 경우 제거할 수 있습니다. 인증서가 자동으로 제거되는 시나리오와 인증서가 디바이스에 남아 있는 시나리오도 있습니다. 이 문서에서는 몇 가지 일반적인 시나리오와 PKCS 및 SCEP 인증서에 미치는 영향을 나열합니다.

> [!NOTE]
> 온-프레미스 Active Directory 또는 Azure AD(Active Directory)에서 제거되는 사용자의 인증서를 제거하고 해지하려면 다음 단계를 순서대로 따릅니다.
>
> 1. 사용자의 디바이스 초기화하거나 사용 중지합니다.
> 2. 온-프레미스 Active Directory 또는 Azure AD에서 사용자를 제거합니다.

## <a name="manually-deleted-certificates"></a>인증서를 수동으로 삭제

인증서 수동 삭제는 SCEP 또는 PKCS 인증서 프로필로 프로비저닝된 플랫폼 및 인증서 전반에 적용되는 시나리오입니다. 예를 들어 사용자가 디바이스에서 인증서를 삭제하는 데 디바이스는 인증서 정책의 대상으로 으로 유지될 수 있습니다.

이 시나리오에서는 인증서를 삭제한 후 다음에 디바이스가 Intune에 체크 인할 때 필요한 인증서가 없으므로 준수하지 않음으로 확인됩니다. 그러면 Intune에서 새 인증서를 발급하여 디바이스를 준수 상태로 복원합니다. 인증서 복원에는 추가 작업이 필요하지 않습니다.

## <a name="windows-devices"></a>Windows 디바이스

### <a name="scep-certificates"></a>SCEP 인증서

다음과 같은 경우 SCEP 인증서가 해지 *및* 제거됩니다.

- 사용자가 등록을 취소합니다.
- 관리자가 [초기화](../remote-actions/devices-wipe.md#wipe) 작업을 실행합니다.
- 관리자가 [사용 중지](../remote-actions/devices-wipe.md#retire) 작업을 실행합니다.
- 디바이스가 Azure AD 그룹에서 제거됩니다.
- 인증서 프로필이 그룹 할당에서 제거됩니다.

다음과 같은 경우 SCEP 인증서가 해지됩니다.

- 관리자가 SCEP 프로필을 변경하거나 업데이트합니다.

다음과 같은 경우 루트 인증서가 제거됩니다.

- 사용자가 등록을 취소합니다.
- 관리자가 [초기화](../remote-actions/devices-wipe.md#wipe) 작업을 실행합니다.
- 관리자가 [사용 중지](../remote-actions/devices-wipe.md#retire) 작업을 실행합니다.

다음과 같은 경우 SCEP 인증서가 디바이스에 *남아 있습니다*(인증서는 해지되거나 제거되지 않음).

- 사용자가 Intune 라이선스를 상실합니다.
- 관리자가 Intune 라이선스를 철회합니다.
- 관리자가 Azure AD에서 사용자 또는 그룹을 제거합니다.

### <a name="pkcs-certificates"></a>PKCS 인증서

다음과 같은 경우 PKCS 인증서가 해지 *및* 제거됩니다.

- 사용자가 등록을 취소합니다.
- 관리자가 [초기화](../remote-actions/devices-wipe.md#wipe) 작업을 실행합니다.
- 관리자가 [사용 중지](../remote-actions/devices-wipe.md#retire) 작업을 실행합니다.

다음과 같은 경우 루트 인증서가 제거됩니다.

- 사용자가 등록을 취소합니다.
- 관리자가 [초기화](../remote-actions/devices-wipe.md#wipe) 작업을 실행합니다.
- 관리자가 [사용 중지](../remote-actions/devices-wipe.md#retire) 작업을 실행합니다.

다음과 같은 경우 PKCS 인증서가 디바이스에 *남아 있습니다*(인증서는 해지되거나 제거되지 않음).

- 사용자가 Intune 라이선스를 상실합니다.
- 관리자가 Intune 라이선스를 철회합니다.
- 관리자가 Azure AD에서 사용자 또는 그룹을 제거합니다.
- 관리자가 PKCS 프로필을 변경하거나 업데이트합니다.
- 인증서 프로필이 그룹 할당에서 제거됩니다.


## <a name="ios-devices"></a>iOS 디바이스

### <a name="scep-certificates"></a>SCEP 인증서

다음과 같은 경우 SCEP 인증서가 해지 *및* 제거됩니다.

- 사용자가 등록을 취소합니다.
- 관리자가 [초기화](../remote-actions/devices-wipe.md#wipe) 작업을 실행합니다.
- 관리자가 [사용 중지](../remote-actions/devices-wipe.md#retire) 작업을 실행합니다.
- 디바이스가 Azure AD 그룹에서 제거됩니다.
- 인증서 프로필이 그룹 할당에서 제거됩니다.

다음과 같은 경우 SCEP 인증서가 해지됩니다.

- 관리자가 SCEP 프로필을 변경하거나 업데이트합니다.

다음과 같은 경우 루트 인증서가 제거됩니다.

- 사용자가 등록을 취소합니다.
- 관리자가 [초기화](../remote-actions/devices-wipe.md#wipe) 작업을 실행합니다.
- 관리자가 [사용 중지](../remote-actions/devices-wipe.md#retire) 작업을 실행합니다.

다음과 같은 경우 SCEP 인증서가 디바이스에 *남아 있습니다*(인증서는 해지되거나 제거되지 않음).

- 사용자가 Intune 라이선스를 상실합니다.
- 관리자가 Intune 라이선스를 철회합니다.
- 관리자가 Azure AD에서 사용자 또는 그룹을 제거합니다.

### <a name="pkcs-certificates"></a>PKCS 인증서

다음과 같은 경우 PKCS 인증서가 해지 *및* 제거됩니다.

- 사용자가 등록을 취소합니다.
- 관리자가 [초기화](../remote-actions/devices-wipe.md#wipe) 작업을 실행합니다.
- 관리자가 [사용 중지](../remote-actions/devices-wipe.md#retire) 작업을 실행합니다.

다음과 같은 경우 PKCS 인증서가 제거됩니다.

- 인증서 프로필이 그룹 할당에서 제거됩니다.

다음과 같은 경우 루트 인증서가 제거됩니다.

- 사용자가 등록을 취소합니다.
- 관리자가 [초기화](../remote-actions/devices-wipe.md#wipe) 작업을 실행합니다.
- 관리자가 [사용 중지](../remote-actions/devices-wipe.md#retire) 작업을 실행합니다.

다음과 같은 경우 PKCS 인증서가 디바이스에 *남아 있습니다*(인증서는 해지되거나 제거되지 않음).

- 사용자가 Intune 라이선스를 상실합니다.
- 관리자가 Intune 라이선스를 철회합니다.
- 관리자가 Azure AD에서 사용자 또는 그룹을 제거합니다.
- 관리자가 PKCS 프로필을 변경하거나 업데이트합니다.

## <a name="android-knox-devices"></a>Android KNOX 디바이스

### <a name="scep-certificates"></a>SCEP 인증서

다음과 같은 경우 SCEP 인증서가 해지 *및* 제거됩니다.

- 사용자가 등록을 취소합니다.
- 관리자가 [초기화](../remote-actions/devices-wipe.md#wipe) 작업을 실행합니다.

다음과 같은 경우 SCEP 인증서가 해지됩니다.

- 관리자가 [사용 중지](../remote-actions/devices-wipe.md#retire) 작업을 실행합니다.
- 디바이스가 Azure AD 그룹에서 제거됩니다.
- 인증서 프로필이 그룹 할당에서 제거됩니다.
- 관리자가 Azure AD에서 사용자 또는 그룹을 제거합니다.
- 관리자가 SCEP 프로필을 변경하거나 업데이트합니다.

다음과 같은 경우 루트 인증서가 제거됩니다.

- 사용자가 등록을 취소합니다.
- 관리자가 [초기화](../remote-actions/devices-wipe.md#wipe) 작업을 실행합니다.
- 관리자가 [사용 중지](../remote-actions/devices-wipe.md#retire) 작업을 실행합니다.

다음과 같은 경우 SCEP 인증서가 디바이스에 *남아 있습니다*(인증서는 해지되거나 제거되지 않음).

- 사용자가 Intune 라이선스를 상실합니다.
- 관리자가 Intune 라이선스를 철회합니다.
- 관리자가 Azure AD에서 사용자 또는 그룹을 제거합니다.

### <a name="pkcs-certificates"></a>PKCS 인증서

다음과 같은 경우 PKCS 인증서가 해지 *및* 제거됩니다.

- 사용자가 등록을 취소합니다.
- 관리자가 [초기화](../remote-actions/devices-wipe.md#wipe) 작업을 실행합니다.
- 관리자가 [사용 중지](../remote-actions/devices-wipe.md#retire) 작업을 실행합니다.

다음과 같은 경우 루트 인증서가 제거됩니다.

- 사용자가 등록을 취소합니다.
- 관리자가 [초기화](../remote-actions/devices-wipe.md#wipe) 작업을 실행합니다.
- 관리자가 [사용 중지](../remote-actions/devices-wipe.md#retire) 작업을 실행합니다.

다음과 같은 경우 PKCS 인증서가 디바이스에 *남아 있습니다*(인증서는 해지되거나 제거되지 않음).
- 사용자가 Intune 라이선스를 상실합니다.

- 관리자가 Intune 라이선스를 철회합니다.
- 관리자가 Azure AD에서 사용자 또는 그룹을 제거합니다.
- 관리자가 PKCS 프로필을 변경하거나 업데이트합니다.
- 인증서 프로필이 그룹 할당에서 제거됩니다.


> [!NOTE]
> Android for Work 디바이스는 이전 시나리오에 대해 유효성이 검사되지 않습니다.
> Android 레거시 디바이스(삼성이 아닌 모든 비작업 프로필 디바이스)는 인증서를 제거할 수 없습니다.

## <a name="macos-certificates"></a>macOS 인증서

### <a name="scep-certificates"></a>SCEP 인증서

다음과 같은 경우 SCEP 인증서가 해지 *및* 제거됩니다.

- 사용자가 등록을 취소합니다.
- 관리자가 [사용 중지](../remote-actions/devices-wipe.md#retire) 작업을 실행합니다.
- 디바이스가 Azure AD 그룹에서 제거됩니다.
- 인증서 프로필이 그룹 할당에서 제거됩니다.

다음과 같은 경우 SCEP 인증서가 해지됩니다.

- 관리자가 SCEP 프로필을 변경하거나 업데이트합니다.

다음과 같은 경우 SCEP 인증서가 디바이스에 *남아 있습니다*(인증서는 해지되거나 제거되지 않음).

- 사용자가 Intune 라이선스를 상실합니다.
- 관리자가 Intune 라이선스를 철회합니다.
- 관리자가 Azure AD에서 사용자 또는 그룹을 제거합니다.

> [!NOTE]
> [초기화](../remote-actions/devices-wipe.md#wipe) 작업을 사용하여 macOS 디바이스를 초기화하는 기능은 지원되지 않습니다.

### <a name="pkcs-certificates"></a>PKCS 인증서

PKCS 인증서는 macOS에서 지원되지 않습니다.

## <a name="next-steps"></a>다음 단계

[인증에 인증서 사용](certificates-configure.md)