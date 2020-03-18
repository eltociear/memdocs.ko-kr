---
title: 검색된 앱
titleSuffix: Microsoft Intune
description: Intune이 디바이스에서 발견한 검색된 앱에 대해 자세히 이해합니다.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 02/28/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 07dd262f-13e7-4cb2-9cc2-b755d1c276cf
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: ''
ms.collection: M365-identity-device-management
ms.openlocfilehash: 1e0115fcdf823e3881ef80edbe44c1762ac6cbf1
ms.sourcegitcommit: 3d895be2844bda2177c2c85dc2f09612a1be5490
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79342389"
---
# <a name="intune-discovered-apps"></a>Intune 검색된 앱

Intune **검색된 앱**은 테넌트의 Intune 등록 디바이스에서 검색된 앱의 목록입니다. 이 목록은 테넌트의 소프트웨어 인벤토리로 사용됩니다. **검색된 앱**은 [앱 설치](apps-monitor.md) 보고서와는 별개의 보고서입니다. 개인 디바이스의 경우 Intune은 관리되지 않는 애플리케이션에 관한 정보를 수집하지 않습니다. 회사 디바이스에서는 관리형 앱인지 여부와 관계없이 모든 앱이 이 보고서에서 수집됩니다. 다음은 예상되는 동작을 매핑하는 표입니다. 일반적으로 보고서는 등록 시부터 7일마다 새로 고쳐집니다(전체 테넌트는 매주 새로 고쳐지지 않음). 이 새로 고침 기간의 유일한 예외로 Win32 앱용 Intune 관리 확장을 통해 수집되는 애플리케이션 정보는 24시간마다 수집됩니다.

## <a name="monitor-discovered-apps-with-intune"></a>Intune을 사용하여 검색된 앱 모니터링

Intune은 테넌트의 Intune 등록 디바이스에서 검색된 앱의 집계된 목록을 제공합니다.

1. [Microsoft Endpoint Manager 관리 센터](https://go.microsoft.com/fwlink/?linkid=2109431)에 로그인합니다.
2. **앱** > **모니터링** > **검색된 앱**을 선택합니다.

>[!NOTE]
>**검색된 앱** 창에서 **내보내기**를 선택하여 검색된 앱 목록을 .csv 파일로 내보낼 수 있습니다.
>
>검색된 Win32 앱의 경우 현재 집계 개수가 없습니다. 이러한 유형의 데이터는 디바이스별로만 볼 수 있습니다.

또한 Intune은 테넌트의 개별 디바이스에 대해 검색된 앱 목록을 제공합니다.

1. [Microsoft Endpoint Manager 관리 센터](https://go.microsoft.com/fwlink/?linkid=2109431)에 로그인합니다.
2. **디바이스** > **모든 디바이스**를 선택합니다.
3. 디바이스를 선택합니다.
4. 이 디바이스에 대해 검색된 앱을 보려면 **모니터** 섹션에서 **검색된 앱**을 선택합니다.

## <a name="details-of-discovered-apps"></a>검색된 앱의 세부 정보

다음 목록에서는 앱 플랫폼 유형, 개인 디바이스에서 모니터링되는 앱, 회사 소유 디바이스에서 모니터링되는 앱 및 새로 고침 주기를 제공합니다. Intune에서 지원하는 앱 유형에 대한 자세한 내용은 Microsoft Intune [Microsoft Intune의 앱 형식](apps-add.md#app-types-in-microsoft-intune)을 참조하세요.

| 플랫폼 | 개인 소유 디바이스 | 회사 소유 디바이스 | 새로 고침 주기 |
|------------------------------------------------------------------------|----------------------------------|--------------------------------------------------|---------------------------------------|
| Windows 10(Win32 앱) 참고: 디바이스에 [Intune 관리 확장 필요](intune-management-extension.md) | 해당 없음 | 관리되는 앱만 | 디바이스 등록 시부터 24시간마다 |
| Windows 10(최신 앱) | 최신 관리형 앱만 | 디바이스에 설치된 모든 최신 앱 | 디바이스 등록 시부터 7일마다 |
| Windows 8.1 | 관리되는 앱만 | 관리되는 앱만 | 디바이스 등록 시부터 7일마다 |
| Windows Phone 8 | 관리되는 앱만 | 관리되는 앱만 | 디바이스 등록 시부터 7일마다 |
| Windows RT | 관리되는 앱만 | 관리되는 앱만 | 디바이스 등록 시부터 7일마다 |
| iOS/iPadOS | 관리되는 앱만 | 디바이스에 설치되는 모든 앱 | 디바이스 등록 시부터 7일마다 |
| macOS | 관리되는 앱만 | 디바이스에 설치되는 모든 앱 | 디바이스 등록 시부터 7일마다 |
| Android | 관리되는 앱만 | 디바이스에 설치되는 모든 앱 | 디바이스 등록 시부터 7일마다 |
| Android Enterprise | 관리되는 앱만 | 작업 프로필에 설치된 앱만 | 디바이스 등록 시부터 7일마다 |

> [!NOTE]
> - Configuration Manager의 앱 관리 워크로드에 표시된 Windows 10 하이브리드 Azure AD 가입 디바이스는 현재 위의 일정에 따라 Intune Management Extension(IME)을 통해 앱 인벤토리를 수집하지 않습니다. 이 문제를 완화하기 위해 IME를 디바이스에 설치할 수 있도록 Configuration Manager의 앱 관리 워크로드를 Intune으로 전환해야 합니다(IME는 Win32 인벤토리 및 PowerShell 배포에 필요합니다). 이 동작에 대한 변경 사항 또는 업데이트는 [개발 중](../fundamentals/in-development.md) 및/또는 [새로운 기능](../fundamentals/whats-new.md)에서 발표됩니다.
> - 2019년 11월 이전에 등록된 개인 소유의 macOS 디바이스는 해당 디바이스를 다시 등록할 때까지 설치된 모든 앱을 계속 표시할 수 있습니다.
> - Android Enterprise 완전 관리형 및 전용에는 검색된 앱이 표시되지 않습니다.

검색된 앱의 수는 앱 설치 상태 수와 일치하지 않을 수 있습니다. 일치하지 않는 경우는 다음과 같습니다.

- 설치된 관리 앱의 대상 지정이 변경되면 상태 창의 설치 수는 감속하지만 감지된 앱에는 보고된 상태로 남아 있을 수 있습니다.
- 하나의 테넌트에 있는 동일한 앱의 여러 인스턴스를 대상으로 지정하면 사용자 또는 디바이스가 중복될 가능성이 있으므로 수가 달라집니다. 앱의 각 인스턴스는 중복 사용자를 계산하지만 검색된 앱은 중복된 수를 갖습니다.
- 검색된 앱과 앱 상태가 서로 다른 시간 간격으로 수집되어 앱 수가 달라지게 됩니다.

## <a name="next-steps"></a>다음 단계

- [Microsoft Intune의 앱 형식](apps-add.md#app-types-in-microsoft-intune)
- [Microsoft Intune으로 앱 정보 및 할당 모니터링](apps-monitor.md)
