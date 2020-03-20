---
title: Microsoft Intune-Azure를 사용하여 디바이스 관리 | Micrososft Docs
description: 디바이스 목록을 csv 형식으로 내보내는 것을 포함하여 Microsoft intune으로 관리하는 디바이스를 검토하고, Azure Active Directory-조인된 디바이스를 보고, 디바이스에서 동작의 변경 로그를 검토하고, IT 관리자가 원격으로 Android 디바이스의 문제를 해결할 수 있게 TeamViewer 커넥터를 사용하고 디바이스에서 실행할 수 있는 모든 작업을 봅니다.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 11/14/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: remote-actions
ms.localizationpriority: high
ms.technology: ''
ms.assetid: d2412418-d91a-4767-a3d6-bc88bb29caa2
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: 4acb2317ea2147f25ef5b19c7d92ae795df36629
ms.sourcegitcommit: 3d895be2844bda2177c2c85dc2f09612a1be5490
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79338112"
---
# <a name="what-is-microsoft-intune-device-management"></a>Microsoft Intune 디바이스 관리란?

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

IT 관리자의 경우 관리되는 디바이스가 위험으로부터 해당 데이터를 보호하는 동안 사용자가 해당 작업을 수행해야 하는 리소스를 제공하도록 해야 합니다.

**디바이스** 워크로드는 관리하는 디바이스에 대한 정보를 제공하고, 이러한 디바이스에 대해 원격 작업을 활성화할 수 있도록 합니다.

## <a name="get-to-your-devices"></a>디바이스로 가져오기

1. [Microsoft Endpoint Manager 관리 센터](https://go.microsoft.com/fwlink/?linkid=2109431)에 로그인합니다.
3. **디바이스**를 선택합니다. 이 보기는 개별 디바이스에 대한 자세한 정보 및 다음을 포함해 이 정보로 할 수 있는 작업을 표시합니다.

   - **개요**는 등록된 디바이스의 시각적 스냅샷, 다양한 플랫폼을 사용하고 있는 디바이스 수 등을 표시합니다.
   - **모든 디바이스** - 관리하는 등록된 디바이스의 목록을 표시합니다.

     **내보내기** 기능을 사용하여 10,000개(Internet Explorer) 또는 30,000개(Microsoft Edge, Chrome)씩 늘어나도록 모든 디바이스의 .zip 목록을 만듭니다.

     디바이스를 선택하여 하드웨어 세부 정보, 설치된 앱, 정책 같은 [해당 디바이스의 추가 세부 정보를 확인](device-inventory.md)합니다.

   - **Azure AD 디바이스**는 Azure AD(Active Directory)로 등록되거나 조인된 디바이스 목록을 표시합니다. [Azure AD 디바이스 관리](https://docs.microsoft.com/azure/active-directory/device-management-introduction)에 대해 자세히 알아봅니다.
   - **디바이스 작업**은 작업, 해당 상태, 작업을 시작한 사용자 및 시간을 비롯한 다른 디바이스에서 실행된 원격 작업의 기록을 포함합니다.

     ![디바이스 작업 모니터링 스크린샷](./media/device-management/monitor-device-actions.png)

   - **감사 로그**는 Intune에서 변경을 생성하는 활동 레코드입니다. [감사 로그](../fundamentals/monitor-audit-logs.md)는 자세한 세부 정보를 제공합니다.
   - **TeamViewer 커넥터**는 Intune에서 관리되는 Android 디바이스의 사용자가 IT 관리자의 원격 지원을 받을 수 있는 서비스입니다. [TeamViewer](teamviewer-support.md)에 대해 자세히 알아봅니다.
   - **도움말 및 지원**은 문제 해결 팁, 지원 요청 또는 Intune 상태 확인에 대한 바로 가기를 제공합니다.

## <a name="available-device-actions"></a>사용 가능한 디바이스 작업
사용 가능한 작업은 디바이스 플랫폼 및 디바이스 구성에 따라 다릅니다.

- [디바이스 인벤토리 보기](device-inventory.md)
- 다음의 원격 디바이스 작업을 실행합니다.
  - [Autopilot 재설정](https://docs.microsoft.com/windows/deployment/windows-autopilot/windows-autopilot-reset#reset-devices-with-remote-windows-autopilot-reset)
  - [BitLocker 키 순환](../protect/encrypt-devices.md#rotate-bitlocker-recovery-keys)(Windows에만 해당)
  - [삭제](devices-wipe.md#delete-devices-from-the-intune-portal)
  - [활성화 잠금 사용 안 함](device-activation-lock-disable.md)(iOS만 해당)
  - [새로 시작](device-fresh-start.md)(Windows만 해당)
  - [전체 검사](../configuration/device-restrictions-windows-10.md#microsoft-defender-antivirus)(Windows 10에만 해당)
  - [디바이스 찾기](device-locate.md)(iOS만 해당)
  - [분실 모드](device-lost-mode.md)(iOS만 해당)
  - [빠른 검사](../configuration/device-restrictions-windows-10.md#microsoft-defender-antivirus)(Windows 10에만 해당)
  - [Android 원격 제어](teamviewer-support.md)
  - [원격 잠금](device-remote-lock.md)
  - [디바이스 이름 바꾸기](device-rename.md)
  - [암호 초기화](device-passcode-reset.md)
  - [다시 시작](device-restart.md)(Windows만 해당)
  - [사용 중지](devices-wipe.md#retire)
  - [Windows Defender 보안 인텔리전스 업데이트](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-antivirus/manage-protection-updates-windows-defender-antivirus)
  - [Windows 10 PIN 재설정](device-windows-pin-reset.md)
  - [초기화](devices-wipe.md#wipe)
  - [사용자 지정 알림 보내기](custom-notifications.md#send-a-custom-notification-to-a-single-device)(Android, iOS/iPadOS)
  - [디바이스 동기화](device-sync.md)
- [대량 디바이스 작업](bulk-device-actions.md)

## <a name="next-steps"></a>다음 단계

- 특정 디바이스에 대한 자세한 정보를 보려면 **모든 디바이스**에서 디바이스를 선택 합니다.
- **디바이스 작업**을 선택하여 관리하는 디바이스에서 수행된 작업의 상태를 확인합니다.
