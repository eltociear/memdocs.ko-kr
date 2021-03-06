---
title: Microsoft Intune에서 디바이스 프로필 확인 - Azure | Microsoft Docs
description: Microsoft Intune에서 디바이스 구성 프로필 세부 정보를 보고 관리하며, 프로필에 할당된 디바이스 수의 그래픽 차트를 보고, 프로필이 할당되거나 배포된 디바이스를 확인합니다. 충돌 설정이 있는 프로필의 문제를 해결할 수도 있습니다.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/21/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 9deaed87-fb4b-4689-ba88-067bc61686d7
ms.reviewer: karthib
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 23594bd1e728e20deba6d978fc2a1f678d692ff3
ms.sourcegitcommit: 3d895be2844bda2177c2c85dc2f09612a1be5490
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79364476"
---
# <a name="monitor-device-profiles-in-microsoft-intune"></a>Microsoft Intune에서 디바이스 프로필 모니터링



Intune에는 디바이스 구성 프로필을 모니터링하고 관리하는 데 도움이 되는 일부 기능이 포함되어 있습니다. 예를 들어, 프로필의 상태를 확인하고, 할당된 디바이스를 확인하고, 프로필 속성을 업데이트할 수 있습니다.

## <a name="view-existing-profiles"></a>기존 프로필 보기

1. [Microsoft Endpoint Manager 관리 센터](https://go.microsoft.com/fwlink/?linkid=2109431)에 로그인합니다.
2. **디바이스** > **구성 프로필**을 선택합니다.

모든 기존 프로필이 나열되고 이러한 프로필은 플랫폼과 같은 세부 정보가 포함되며 프로필이 모든 디바이스에 할당되었는지 여부가 표시됩니다.

## <a name="view-details-on-a-profile"></a>프로필에 대한 세부 정보 보기

디바이스 프로필을 만든 후 Intune에서 그래픽 차트를 제공합니다. 이러한 차트에는 프로필이 디바이스에 성공적으로 할당되어 있는 상태 또는 프로필에 충돌이 표시되는지 여부 등의 프로필 상태가 표시됩니다.

1. 기존 프로필을 선택합니다. 예를 들어, macOS 프로필을 선택합니다.
2. **개요** 탭을 선택합니다.

    위쪽 그래픽 차트에는 디바이스 프로필에 할당된 디바이스 수가 표시됩니다. 예를 들어, 구성 디바이스 프로필이 macOS 디바이스에 적용되는 경우 차트는 macOS 디바이스의 개수가 나열됩니다.

    또한 동일한 디바이스 프로필이 할당된 기타 플랫폼의 디바이스 수도 표시됩니다. 예를 들어, macOS 이외의 디바이스 수가 표시됩니다.

    ![디바이스 프로필에 할당된 디바이스 수 보기](./media/device-profile-monitor/device-configuration-profile-graphical-chart.png)

    아래쪽 그래픽 차트에는 디바이스 프로필에 할당된 사용자 수가 표시됩니다. 예를 들어 구성 디바이스 프로필이 macOS 사용자에게 적용되는 경우 차트에는 macOS 사용자 수가 나열됩니다.

3. 위쪽 그래픽 차트에서 원을 선택합니다. **디바이스 상태**가 열립니다.

    프로필에 할당된 디바이스가 나열되고 프로필이 성공적으로 배포되었는지 여부가 표시됩니다. 또한 특정 플랫폼(예: macOS)이 있는 디바이스만 나열됩니다.

    **디바이스 상태** 세부 정보를 닫습니다.

4. 아래쪽 그래픽 차트에서 원을 선택합니다. **사용자 상태**가 열립니다. 

    프로필에 할당된 사용자가 나열되고 프로필이 성공적으로 배포되었는지 여부가 표시됩니다. 또한 특정 플랫폼(예: macOS)이 있는 사용자만 나열됩니다.

    **사용자 상태** 세부 정보를 닫습니다.

5. **프로필** 목록으로 돌아가서 특정 프로필을 선택합니다. 또한 다음과 같은 기존 속성을 변경할 수도 있습니다.
    - **속성**: 이름을 변경하거나 기존 설정을 업데이트합니다.
    - **할당**: 정책을 적용해야 하는 디바이스를 포함하거나 제외합니다. **선택된 그룹**을 선택하여 특정 그룹을 선택합니다.
    - **디바이스 상태**: 프로필에 할당된 디바이스가 나열되고 프로필이 성공적으로 배포되었는지 여부가 표시됩니다. 특정 디바이스를 선택하여 설치된 앱을 비롯한 더 많은 세부 정보를 얻을 수 있습니다.
    - **사용자 상태**: 이 프로필의 영향을 받는 디바이스를 가진 사용자 이름 및 프로필이 성공적으로 배포되었는지 여부를 나열합니다. 특정 사용자를 선택하여 더 많은 세부 정보를 얻을 수 있습니다.
    - **설정별 상태**: 프로필 내의 개별 설정을 표시하여 출력을 필터링하고 설정이 성공적으로 적용되었는지 여부를 표시합니다.

## <a name="view-conflicts"></a>충돌 보기

**디바이스** > **모든 디바이스**에서 충돌을 유발시키는 모든 설정을 볼 수 있습니다. 충돌이 발생하면 이 설정을 포함하는 모든 구성 프로필도 표시됩니다. 관리자는 이 기능을 사용하여 문제를 해결하고 프로필과의 불일치를 해결할 수 있습니다.

1. Intune에서 **디바이스** > **모든 디바이스** 선택 &gt; 목록에서 기존 디바이스를 선택합니다. 최종 사용자는 회사 포털 앱에서 디바이스 이름을 가져올 수 있습니다.
2. **디바이스 구성**을 선택합니다. 디바이스에 적용되는 모든 구성 정책이 나열됩니다.
3. 정책을 선택합니다. 디바이스에 적용되는 해당 정책의 모든 설정이 표시됩니다. 디바이스에 **충돌** 상태가 있는 경우 해당 행을 선택합니다. 새 창에서 모든 프로필과 충돌을 일으키는 설정이 있는 프로필 이름이 표시됩니다.

충돌하는 설정과 해당 설정을 포함하는 정책을 파악했으므로 충돌을 쉽게 해결할 수 있습니다. 

## <a name="device-firmware-configuration-interface-profile-reporting"></a>디바이스 펌웨어 구성 인터페이스 프로필 보고

> [!WARNING]
> DFCI 프로필을 모니터링하는 기능은 현재 만드는 중입니다. DFCI는 공개 미리 보기로 제공되지만, 모니터링 데이터가 없거나 불완전할 수 있습니다.

DFCI 프로필은 다른 디바이스 구성 프로필과 마찬가지로 설정별로 보고됩니다. 제조업체의 DFCI 지원 여부에 따라 일부 설정이 적용되지 않을 수 있습니다.

DFCI 프로필 설정을 사용하면 다음 상태가 표시될 수 있습니다.

- **규격**: 이 상태는 프로필의 설정 값이 디바이스의 설정과 일치하는 경우를 표시합니다. 이 상태는 다음 시나리오에서 발생할 수 있습니다.

  - DFCI 프로필은 프로필의 설정을 구성했습니다.
  - 디바이스에 설정으로 제어되는 하드웨어 기능이 없으며 프로필 설정은 **사용 안 함**입니다.
  - UEFI에서 DFCI가 기능을 사용 안 함으로 설정하도록 허용하지 않으며 프로필 설정은 **사용**입니다.
  - 디바이스에 기능을 사용하지 않도록 설정할 하드웨어가 없으며 프로필 설정은 **사용**입니다.

- **해당 없음**: 이 상태는 프로필의 설정 값이 **사용**이고 디바이스에서 일치하는 설정을 찾을 수 없는 경우를 표시합니다. 이 상태는 디바이스 하드웨어에 기능이 없는 경우 발생할 수 있습니다.

- **비준수**: 이 상태는 프로필의 설정 값이 디바이스의 설정과 일치하지 않는 경우를 표시합니다. 이 상태는 다음 시나리오에서 발생할 수 있습니다.

  - UEFI에서 DFCI가 설정을 사용 안 함으로 설정하도록 허용하지 않으며 프로필 설정은 **사용 안 함**입니다.
  - 디바이스에 기능을 사용하지 않도록 설정할 하드웨어가 없으며 프로필 설정은 **사용 안 함**입니다.
  - 디바이스에 최신 DFCI 펌웨어 버전이 없습니다.
  - DFCI가 UEFI 메뉴에서 로컬 “옵트아웃” 컨트롤을 사용하여 Intune에 등록되기 전에 사용하지 않도록 설정되었습니다.
  - 디바이스가 Autopilot 등록 외부에서 Intune에 등록되었습니다.
  - 디바이스가 Microsoft CSP에 의해 Autopilot에 등록되지 않았거나 OEM에 의해 직접 등록되었습니다.

## <a name="next-steps"></a>다음 단계

[디바이스 프로필을 통한 일반적인 질문, 이슈 및 해결 방법](device-profile-troubleshoot.md)  
[Intune의 문제 해결 정책 및 프로필](troubleshoot-policies-in-microsoft-intune.md)
