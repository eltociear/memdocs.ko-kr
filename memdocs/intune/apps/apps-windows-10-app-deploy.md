---
title: Microsoft Intune을 사용하여 Windows 10 앱 배포
titleSuffix: ''
description: Microsoft Intune으로 사용할 수 있는 Windows 10 앱 배포 시나리오에 대해 알아봅니다.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 02/25/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: abebfb5e-054b-435a-903d-d1c31767bcf2
ms.reviewer: priyar
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 2168833715bb1148adcb3e158e58c9f54bcd3fc4
ms.sourcegitcommit: 3d895be2844bda2177c2c85dc2f09612a1be5490
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79340153"
---
# <a name="windows-10-app-deployment-by-using-microsoft-intune"></a>Microsoft Intune을 사용하여 Windows 10 앱 배포 

Microsoft Intune은 Windows 10 디바이스에서 다양한 앱 형식 및 배포 시나리오를 지원합니다. Intune에 앱이 추가되면 사용자와 디바이스에 해당 앱을 할당할 수 있습니다. 이 문서에서는 지원되는 Windows 10 시나리오에 대한 자세한 내용을 제공하고 Windows에 앱을 배포할 때 유의해야 하는 주요 세부 정보를 다룹니다. 

기간 업무(LOB) 앱 및 비즈니스용 Microsoft 스토어 앱은 Windows 10 디바이스에서 지원되는 앱 형식입니다. Windows 앱의 파일 확장명에는 .msi, .appx 및 .appxbundle이 포함됩니다.  

> [!Note]
> 최신 앱을 배포하려면 다음 이상이 필요합니다.
> - Windows 10 1803의 경우, [2018년 5월 23일—KB4100403(OS 빌드 17134.81)](https://support.microsoft.com/help/4100403/windows-10-update-kb4100403)입니다.
> - Windows 10 1709의 경우, [2018년 6월 21일—KB4284822(OS 빌드 16299.522)](https://support.microsoft.com/help/4284822)입니다.
>
> 연결된 기본 사용자가 없는 경우 Windows 10 1803 이상에서만 앱 설치를 지원합니다.
>
> Windows 10 Home 버전을 실행 중인 디바이스에서는 LOB 앱 배포를 지원하지 않습니다.

## <a name="supported-windows-10-app-types"></a>지원되는 Windows 10 앱 유형

사용자가 실행하는 Windows 10 버전에 따라 지원되는 구체적인 앱 유형이 달라집니다. 다음 표에는 앱 유형 및 Windows 10 지원 가능성이 나와 있습니다.

| 앱 유형 | 홈 | Pro | 비즈니스 | Enterprise | 교육 | S-모드 | HoloLens<sup>1 | Surface Hub | WCOS | 휴대폰 |
|----------------|------|-----|----------|------------|-----------|--------|-----------|------------|------|--------|
|  .MSI | 아니요 | 예 | 예 | 예 | 예 | 아니요 | 아니요 | 아니요 | 아니요 | 아니요 |
| .IntuneWin | 아니요 | 예 | 예 | 예 | 예 | 19H2+ | 아니요 | 아니요 | 아니요 | 아니요 |
| Office C2R | 아니요 | 예 | 예 | 예 | 예 | RS4+ | 아니요 | 아니요 | 아니요 | 아니요 |
| LOB: APPX/MSIX | 예 | 예 | 예 | 예 | 예 | 예 | 예 | 예 | 예 | 예 |
| MSFB 오프라인 | 예 | 예 | 예 | 예 | 예 | 예 | 예 | 예 | 예 | 예 |
| MSFB 온라인 | 예 | 예 | 예 | 예 | 예 | 예 | RS4+ | 아니요 | 예 | 예 |
| Web Apps | 예 | 예 | 예 | 예 | 예 | 예 | 예<sup>2 | 예<sup>2 | 예 | 예<sup>2 |
| Store 링크 | 예 | 예 | 예 | 예 | 예 | 예 | 예 | 예 | 예 | 예 |
| Microsoft Edge | 아니요 | 예 | 예 | 예 | 예 | 19H2+<sup>3 | 아니요 | 아니요 | 아니요 | 아니요 |

<sup>1</sup> 앱 관리의 잠금을 해제하려면 HoloLens 디바이스를 [Holographic for Business](../fundamentals/windows-holographic-for-business.md)로 업그레이드합니다.<br />
<sup>2</sup> 회사 포털에서만 시작합니다.<br />
<sup>3</sup> Edge 앱이 성공적으로 설치되면 디바이스에도 S 모드 정책이 할당되어야 합니다.

> [!NOTE]
> 모든 Windows 앱 유형은 등록이 필요합니다.

## <a name="windows-10-lob-apps"></a>Windows 10 LOB 앱

Windows 10 LOB 앱을 서명하고 Intune 관리 콘솔에 업로드할 수 있습니다. 여기에는 유니버설 Windows 플랫폼(UWP) 앱 및 Windows 앱 패키지(AppX)와 같은 최신 앱뿐만 아니라 간단한 Microsoft Installer 패키지 파일(MSI)과 같은 Win 32 앱이 포함될 수 있습니다. 관리자는 LOB 앱의 업데이트를 수동으로 업로드하고 배포해야 합니다. 이러한 업데이트는 앱이 설치된 사용자 디바이스에 자동으로 설치됩니다. 사용자 개입이 필요하지 않으며 사용자가 업데이트를 제어할 수 없습니다. 

## <a name="microsoft-store-for-business-apps"></a>비즈니스용 Microsoft 스토어 앱

비즈니스용 Microsoft Store 앱은 비즈니스용 Microsoft Store 관리 포털에서 구매하는 최신 앱입니다. 그런 다음 관리를 위해 Microsoft Intune으로 동기화됩니다. 이 앱은 온라인에서 라이선스되거나 오프라인에서 라이선스될 수 있습니다. Microsoft Store는 관리자에 의한 추가 작업 없이 업데이트를 직접 관리합니다. 사용자 지정 URI(Uniform Resource Identifier)를 사용하여 특정 앱에 대한 업데이트를 방지할 수도 있습니다. 자세한 내용은 [엔터프라이즈 앱 관리 - 앱의 자동 업데이트 방지](https://docs.microsoft.com/windows/client-management/mdm/enterprise-app-management#prevent-app-from-automatic-updates)를 참조합니다. 사용자는 모든 비즈니스용 Microsoft Store 앱에 대한 업데이트를 사용하지 못하도록 설정할 수도 있습니다. 

### <a name="categorize-microsoft-store-for-business-apps"></a>비즈니스용 Microsoft Store 앱 범주화 
비즈니스용 Microsoft Store 앱을 범주화하려면 

1. [Microsoft Endpoint Manager 관리 센터](https://go.microsoft.com/fwlink/?linkid=2109431)에 로그인합니다.
2. **앱** > **모든 앱**을 선택합니다. 
3. 비즈니스용 Microsoft Store 앱을 선택합니다. 그런 다음, **속성** > **앱 정보** > **범주**를 선택합니다. 
4. 범주를 선택합니다.

## <a name="install-apps-on-windows-10-devices"></a>Windows 10 디바이스에서 앱 설치
앱 유형에 따라 두 가지 방법 중 하나로 Windows 10 디바이스에 앱을 설치할 수 있습니다.

- **사용자 컨텍스트**: 사용자 컨텍스트에서 앱을 배포할 경우 관리되는 앱은 사용자가 디바이스에 로그인할 때 해당 사용자를 위해 디바이스에 설치됩니다. 사용자가 디바이스에 로그인할 때까지 앱 설치는 성공할 수 없습니다. 
  - 최신 LOB 앱 및 비즈니스용 Microsoft Store 앱(온라인 및 오프라인 모두)은 사용자 컨텍스트에서 배포할 수 있습니다. 앱은 필수 및 사용 가능 의도를 모두 지원합니다.
  - 사용자 모드 또는 이중 모드로 빌드된 Win32 앱은 사용자 컨텍스트에서 배포할 수 있으며 필수 및 사용 가능 의도를 모두 지원합니다. 
- **디바이스 컨텍스트**: 디바이스 컨텍스트에서 앱을 배포하면 Intune에서 관리되는 앱을 디바이스에 직접 설치합니다.
  - 최신 LOB 앱 및 오프라인 사용 허가된 비즈니스용 Microsoft Store 앱은 디바이스 컨텍스트에서 배포할 수 있습니다. 이러한 앱은 필수 의도만 지원합니다.
  - 컴퓨터 모드 또는 이중 모드로 빌드된 Win32 앱은 디바이스 컨텍스트에서 배포할 수 있으며 필수 의도만 지원합니다.

> [!NOTE]
> 이중 모드 앱으로 빌드된 Win32 앱의 경우 관리자는 해당 인스턴스와 연결된 모든 할당에 대해 앱이 사용자 모드 또는 컴퓨터 모드 중 어떤 모드로 작동할지 선택해야 합니다. 배포 컨텍스트를 할당마다 변경할 수는 없습니다.  

앱은 디바이스 및 Intune 앱 유형에서 지원되는 경우에만 디바이스 컨텍스트에서 설치할 수 있습니다. 디바이스 컨텍스트에서 다음 앱 유형을 설치하고 이러한 앱을 디바이스 그룹에 할당할 수 있습니다.

- Win32 앱
- 오프라인 라이선스가 부여된 비즈니스용 Microsoft Store 앱
- LOB 앱(MSI, APPX 및 MSIX)
- Office 365 ProPlus

디바이스 컨텍스트에서 설치하기로 선택한 Windows LOB 앱(구체적으로 APPX 및 MSIX) 및 비즈니스용 Microsoft Store 앱(오프라인 앱)은 디바이스 그룹에 할당되어야 합니다. 이러한 앱 중 하나가 사용자 컨텍스트에 배포되는 경우 설치가 실패합니다. 관리 콘솔에 표시되는 상태 및 오류는 다음과 같습니다.
  - 상태: 실패
  - 오류: 사용자는 디바이스 컨텍스트 설치를 대상으로 할 수 없습니다.

> [!IMPORTANT]
> Autopilot white glove 프로비전 시나리오와 함께 사용하는 경우 디바이스 그룹을 대상으로 하는 디바이스 컨텍스트에 배포된 비즈니스용 Microsoft Store 앱 및 LOB 앱에 대한 요구 사항은 없습니다. 자세한 내용은 [Windows Autopilot white glove 배포](https://docs.microsoft.com/windows/deployment/windows-autopilot/white-glove)를 참조하세요.

> [!Note]
> 특정 배포를 사용하여 앱 할당을 저장한 후에는 최신 앱을 제외하고 해당 할당에 대한 컨텍스트를 변경할 수 없습니다. 최신 앱의 경우 컨텍스트를 사용자 컨텍스트에서 디바이스 컨텍스트로 변경할 수 있습니다. 

단일 사용자 또는 디바이스에 대한 정책에 충돌이 있는 경우 다음 우선 순위가 적용됩니다.
- 디바이스 컨텍스트 정책은 사용자 컨텍스트 정책보다 우선 순위가 높습니다. 
- 설치 정책이 제거 정책보다 우선 순위가 높습니다.

자세한 내용은 [Microsoft Intune에서 앱 할당 포함 및 제외](apps-inc-exl-assignments.md)를 참조하세요. Intune의 앱 형식에 대한 자세한 내용은 [Microsoft Intune에 앱 추가](apps-add.md)를 참조하세요.

## <a name="next-steps"></a>다음 단계

- [Microsoft Intune을 사용하여 그룹에 앱 할당](apps-deploy.md)
- [앱을 모니터링하는 방법](apps-monitor.md)
