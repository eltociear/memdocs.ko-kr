---
title: 등록 상태 페이지 설정
titleSuffix: Microsoft Intune
description: Windows 10 디바이스를 등록하는 사용자를 위한 인사말 페이지를 설정합니다.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 11/26/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 8518d8fa-a0de-449d-89b6-8a33fad7b3eb
ms.reviewer: ericor
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure;seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9bbb8738acbfdfa2317d754797dbb171c6a5d8ac
ms.sourcegitcommit: 3d895be2844bda2177c2c85dc2f09612a1be5490
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79344391"
---
# <a name="set-up-an-enrollment-status-page"></a>등록 상태 페이지 설정
 
[!INCLUDE [azure_portal](../includes/azure_portal.md)]
 
ESP(등록 상태 페이지)는 초기 디바이스를 등록하는 동안 Windows 10 디바이스(버전 1803 이상)에 대한 설치 정보를 표시합니다. 예를 들면 다음과 같습니다.
- [Windows Autopilot](https://docs.microsoft.com/windows/deployment/windows-autopilot/)을 사용하는 경우 
- 또는 등록 상태 페이지 정책이 적용된 후에 관리되는 디바이스가 처음으로 시작될 때마다 

등록 상태 페이지는 사용자가 디바이스 설정 중에 디바이스 상태를 이해하는 데 도움이 됩니다. 여러 등록 상태 페이지 프로필을 만들어 사용자가 포함된 여러 그룹에 적용할 수 있습니다. 프로필은 다음과 같이 설정할 수 있습니다.
- 설치 진행률 표시.
- 설치가 완료될 때까지 사용 차단.
- 디바이스 설정에 실패한 경우 사용자가 수행할 수 있는 작업 지정.

또한 동일한 사용자의 충돌하는 프로필 할당을 고려하기 위해 각 프로필의 우선순위를 설정할 수도 있습니다.

> [!NOTE]
> 등록 상태 페이지는 할당된 그룹에 속한 사용자만 대상으로 지정할 수 있으며 해당 디바이스를 사용하는 모든 사용자를 등록할 때 디바이스에 해당 정책이 설정됩니다.  

## <a name="available-settings"></a>사용 가능한 설정

 등록 상태 페이지의 동작을 사용자 지정하도록 다음 설정을 구성할 수 있습니다.

<table>
<th align="left">Setting<th align="left">예<th align="left">아니요
<tr><td>앱 및 프로필 설치 진행률 표시<td>등록 상태 페이지가 표시됩니다.<td>등록 상태 페이지가 표시되지 않습니다.
<tr><td>모든 앱 및 프로필이 설치될 때까지 디바이스 차단<td>이 테이블의 설정은 사용자가 잠재적인 설치 문제를 해결할 수 있도록 등록 상태 페이지의 동작을 사용자 지정하는 데 사용할 수 있습니다.
<td>등록 상태 페이지에는 설치 오류를 해결하는 추가 옵션이 표시되지 않습니다.
<tr><td>설치 오류 발생 시 사용자가 디바이스를 재설정하도록 허용<td>설치에 실패한 경우 <b>디바이스 재설정</b> 단추가 표시됩니다.<td>설치에 실패한 경우 <b>디바이스 재설정</b> 단추가 표시되지 않습니다.
<tr><td>설치 오류 발생 시 사용자가 디바이스를 사용하도록 허용<td>설치에 실패한 경우 <b>계속</b> 단추가 표시됩니다.<td>설치에 실패한 경우 <b>계속</b> 단추가 표시되지 않습니다.
<tr><td>설치가 지정된 시간(분)보다 오래 걸리면 시간 초과 오류 표시<td colspan="2">설치가 완료될 때까지 대기할 시간(분)을 지정합니다. 기본값은 60분으로 입력됩니다.
<tr><td>오류가 발생하는 경우 사용자 지정 메시지 표시<td>설치 오류가 발생하는 경우 표시할 사용자 지정 메시지를 지정할 수 있는 텍스트 상자가 제공됩니다.<td>다음과 같은 기본 메시지가 표시됩니다. <br><b>조직에서 설정한 설치 제한 시간을 초과했습니다. 다시 시도하거나 IT 지원 담당자에게 문의하여 도움을 요청하세요.<b>
<tr><td>사용자가 설치 오류에 대한 로그를 수집하는 것을 허용<td>설치 오류가 발생하는 경우 <b>로그 수집</b> 단추가 표시됩니다. <br>사용자가 이 단추를 클릭하면 로그 파일 <b>MDMDiagReport.cab</b>을 저장할 위치를 선택하라는 메시지가 표시됩니다.<td>설치에 실패한 경우 <b>로그 수집</b> 단추가 표시되지 않습니다.
<tr><td>이러한 필수 앱이 사용자/디바이스에 할당된 경우 이러한 필수 앱이 설치될 때까지 디바이스 사용 차단<td colspan="2"><b>모두</b> 또는 <b>선택됨</b>을 선택합니다. <br><br><b>선택됨</b>을 선택하는 경우 디바이스를 사용하도록 설정하기 전에 설치해야 하는 앱을 선택할 수 있는 <b>앱 선택</b> 단추가 표시됩니다.
</table>

## <a name="turn-on-default-enrollment-status-page-for-all-users"></a>모든 사용자의 기본 등록 상태 페이지 켜기

등록 상태 페이지를 켜려면 아래 단계에 따릅니다.
 
1. [Microsoft Endpoint Manager 관리 센터](https://go.microsoft.com/fwlink/?linkid=2109431)에서 **디바이스** > **Windows** > **Windows 등록** > **등록 상태 페이지**를 선택합니다.
2. **등록 상태 페이지** 블레이드에서 **기본값** > **설정**을 선택합니다.
3. **프로필 및 앱 설치 진행률 표시**에서 **예**를 선택합니다.
4. 사용하려는 다른 설정을 선택한 다음, **저장**을 선택합니다.

## <a name="create-enrollment-status-page-profile-and-assign-to-a-group"></a>등록 상태 페이지 프로필을 만들고 그룹에 할당

1. [Microsoft Endpoint Manager 관리 센터](https://go.microsoft.com/fwlink/?linkid=2109431)에서 **디바이스** > **Windows** > **Windows 등록** > **등록 상태 페이지** > **프로필 만들기**를 선택합니다.
2. **이름** 및 **설명**을 제공합니다.
3. **만들기**를 선택합니다.
4. **등록 상태 페이지** 목록에서 새 프로필을 선택합니다.
5. **할당** > **그룹 선택**을 선택하고 이 프로필을 채택하려는 그룹을 선택한 후 **선택** > **저장**을 선택합니다.
6. **설정** > 이 프로필에 적용할 설정 선택 > **저장**을 선택합니다.

## <a name="set-the-enrollment-status-page-priority"></a>등록 상태 페이지 우선순위 설정

사용자는 여러 그룹에 속할 수 있으며 등록 상태 페이지 프로필을 여러 개 사용할 수 있습니다. 이러한 충돌을 해결하려면 각 프로필의 우선 순위를 설정하면 됩니다. 등록 중에 누군가 등록 상태 페이지 프로필을 두 개 이상 보유하고 있다면 우선 순위가 가장 높은 프로필만 등록하는 디바이스에 적용됩니다.

1. [Microsoft Endpoint Manager 관리 센터](https://go.microsoft.com/fwlink/?linkid=2109431)에서 **디바이스** > **Windows** > **Windows 등록** > **등록 상태 페이지**를 선택합니다.
2. 목록의 프로필을 마우스로 가리키세요.
3. 세로 점 세 개를 사용하여 목록의 원하는 위치로 프로필을 끕니다.

## <a name="block-access-to-a-device-until-a-specific-application-is-installed"></a>특정 애플리케이션이 설치될 때까지 디바이스 액세스 차단

사용자가 바탕 화면에 액세스하기 전에 설치해야 하는 앱을 지정할 수 있습니다.

1. [Microsoft Endpoint Manager 관리 센터](https://go.microsoft.com/fwlink/?linkid=2109431)에서 **디바이스** > **Windows** > **Windows 등록** > **등록 상태 페이지**를 선택합니다.
2. 프로필 > **설정**을 선택합니다.
3. **프로필 및 앱 설치 진행률 표시**에서 **예**를 선택합니다.
4. **모든 앱 및 프로필이 설치될 때까지 디바이스 차단**에서 **예**를 선택합니다.
5. **이러한 필수 앱이 사용자/디바이스에 할당된 경우 이러한 필수 앱이 설치될 때까지 디바이스 사용 차단**에서 **선택됨**을 선택합니다.
6. **앱 선택**을 선택하고, 앱을 선택한 다음, **선택** > **저장**을 선택합니다.

## <a name="enrollment-status-page-tracking-information"></a>등록 상태 페이지 추적 정보

등록 상태 페이지에서 디바이스 준비, 디바이스 설정 및 계정 설정에 대한 정보를 추적하는 세 가지 단계가 있습니다.

### <a name="device-preparation"></a>디바이스 준비

디바이스 준비를 위해 등록 상태 페이지는 다음을 추적합니다.
- TPM(신뢰할 수 있는 플랫폼 모듈) 키 증명(해당하는 경우)
- Azure Active Directory 조인 진행률
- Intune 등록 상태
- Intune 관리 확장 설치

### <a name="device-setup"></a>디바이스 설정

등록 상태 페이지는 다음 디바이스 설정 항목을 추적합니다(모든 디바이스 또는 등록하는 디바이스가 구성원인 디바이스 그룹에 할당된 경우).
- 보안 정책
  - 모든 등록에 대한 하나의 구성 서비스 공급자(CSP)입니다.
  - Intune에서 구성된 실제 CSP는 여기서 추적하지 않습니다.
- 애플리케이션
  - 컴퓨터별 LoB(기간 업무) MSI 앱입니다.
  - 설치 컨텍스트 = 디바이스인 LoB 저장소 앱입니다.
  - 설치 컨텍스트 = 디바이스인 오프라인 저장소 및 LoB 저장소 앱입니다.
  - Win32 응용 프로그램(Windows 10 버전 1903 이상에만 해당) 
- 연결 프로필
  - **모든 디바이스** 또는 등록 디바이스가 멤버로 속한 Autopilot 디바이스의 디바이스 그룹에 할당된 VPN 또는 Wi-Fi 프로필
- **모든 디바이스** 또는 등록 디바이스가 멤버로 속한 Autopilot 디바이스의 디바이스 그룹에 할당된 인증서

### <a name="account-setup"></a>계정 설정
계정 설정을 위해 등록 상태 페이지는 다음 항목을 추적합니다(현재 로그인된 사용자에게 할당된 경우).
- 보안 정책
  - 모든 등록에 대해 하나의 CSP입니다.
  - Intune에서 구성된 실제 CSP는 여기서 추적하지 않습니다.
- 애플리케이션
  - 모든 디바이스, 모든 사용자 또는 디바이스를 등록하는 사용자가 구성원인 사용자 그룹에 할당된 사용자별 LoB MSI 앱입니다.
  - 모든 사용자 또는 디바이스를 등록하는 사용자가 구성원인 사용자 그룹에 할당된 컴퓨터별 LoB MSI 앱입니다.
  - 다음 개체 중 하나에 할당된 LoB 스토어 앱, 온라인 스토어 앱 및 오프라인 스토어 앱입니다.
    - All Devices
    - 모든 사용자
    - 디바이스를 등록하는 사용자가 사용자로 설정된 설치 컨텍스트의 구성원인 사용자 그룹입니다.
  - Win32 애플리케이션(Windows 10 버전 1903 이상에만 해당) 
- 연결 프로필
  - 모든 사용자 또는 디바이스를 등록하는 사용자가 구성원인 사용자 그룹에 할당된 VPN 또는 Wi-Fi 프로필입니다.
- 인증서
  - 모든 사용자 또는 디바이스를 등록하는 사용자가 구성원인 사용자 그룹에 할당된 인증서 프로필입니다.

### <a name="troubleshooting"></a>문제 해결
문제 해결을 위해 자주 묻는 질문

- 등록 상태 페이지를 사용하는 Autopilot 배포 중에 디바이스 설정 단계에서 내 애플리케이션이 설치되지 않는 이유는 무엇인가요?
  - Autopilot 디바이스 설정 단계에서 애플리케이션이 설치되도록 하려면 다음을 확인하세요. 
        1. 선택한 앱 목록에서 애플리케이션이 액세스를 차단하도록 선택되어 있는지 여부
        2. Autopilot 프로필이 할당된 동일한 Azure AD 디바이스 그룹을 애플리케이션 대상으로 지정했는지 여부 

- Autopilot 배포가 아님에도 등록 상태 페이지가 표시되는 이유는 무엇인가요(예: 사용자가 Configuration Manager 공동 관리 등록 디바이스에 처음으로 로그인 하는 경우)?  
  - 등록 상태 페이지에는 다음을 포함한 모든 등록 방법의 설치 상태가 나열됩니다.
      - Autopilot
      - Configuration Manager 공동 관리
      - 새 사용자가 등록 상태 페이지 정책이 처음 적용된 디바이스에 로그인하는 경우
      - **OOBE(Out of Box Experience)에 의해 프로비전된 디바이스에만 페이지 표시** 설정이 켜져 있고 정책이 설정된 경우, 디바이스에 로그인하는 첫 번째 사용자에게만 등록 상태 페이지가 표시됩니다.

- 디바이스에서 등록 상태 페이지가 구성된 경우 이 페이지를 사용하지 않도록 설정하려면 어떻게 해야 하나요?
  - 등록 시 등록 상태 페이지 정책이 디바이스에 설정됩니다. 등록 상태 페이지를 사용하지 않도록 설정하려면 사용자 및 디바이스 등록 상태 페이지 섹션을 사용하지 않도록 설정해야 합니다. 다음 구성으로 사용자 지정 OMA-URI 설정을 만들어 섹션을 사용하지 않도록 설정합니다.

      사용자 등록 상태 페이지 사용 안 함:

      ```
      Name:  Disable User ESP (choose a name you desire)
      Description:  (enter a description)
      OMA-URI:  ./Vendor/MSFT/DMClient/Provider/MS DM Server/FirstSyncStatus/SkipUserStatusPage
      Data type:  Boolean
      Value:  True 
      ```
      디바이스 등록 상태 페이지 사용 안 함:

      ```
      Name:  Disable Device ESP (choose a name you desire)
      Description:  (enter a description)
      OMA-URI:  ./Vendor/MSFT/DMClient/Provider/MS DM Server/FirstSyncStatus/SkipDeviceStatusPage
      Data type:  Boolean
      Value:  True 
      ```
- 로그 파일을 수집하려면 어떻게 해야 하나요?
  - 등록 상태 페이지 로그 파일을 수집하는 방법에는 다음과 같은 두 가지가 있습니다.
      - 사용자가 ESP 정책에서 로그를 수집할 수 있도록 합니다. 등록 상태 페이지에서 시간 초과가 발생하면 최종 사용자가 **로그 수집** 옵션을 선택할 수 있습니다. USB 드라이브를 삽입하여 로그 파일을 드라이브에 복사할 수 있습니다.
      - Shift-F10 키 시퀀스를 입력하여 명령 프롬프트를 열고 다음 명령줄을 입력하여 로그 파일을 생성합니다. 

      ```
      mdmdiagnosticstool.exe -area Autopilot -cab <pathToOutputCabFile>.cab 
      ```

### <a name="known-issues"></a>알려진 문제
다음은 알려진 문제입니다. 
- ESP 프로필을 사용하지 않도록 설정해도 디바이스에서 ESP 정책이 제거되지 않으며 사용자가 처음으로 디바이스에 로그인하면 ESP를 계속 가져옵니다. 이 정책은 ESP 프로필을 사용하지 않도록 설정한 경우에도 제거되지 않습니다. ESP를 사용하지 않도록 설정하려면 OMA-URI를 배포해야 합니다. OMA-URI를 사용하여 ESP를 사용하지 않도록 설정하는 방법에 대한 지침은 위 내용을 참조하세요. 
- 재부팅을 보류하면 항상 시간 초과가 발생합니다. 디바이스를 재부팅해야 하기 때문에 시간 초과가 발생합니다. 등록 상태 페이지에서 추적한 항목이 완료되는 시간이 필요하기 때문에 재부팅해야 합니다. 재부팅하면 등록 상태 페이지가 종료되고 재부팅 후 계정 설정 중에는 디바이스를 사용할 수 없습니다.  애플리케이션 설치 시에는 재부팅을 하지 않는 것이 좋습니다. 
- 디바이스를 설정하는 동안 재부팅하면 계정 설정 단계로 전환되기 전에 사용자가 자격 증명을 입력해야 합니다. 재부팅 중에는 사용자 자격 증명이 유지되지 않습니다. 사용자에게 자격 증명을 입력하도록 한 다음, 등록 상태 페이지를 계속 진행할 수 있습니다. 
- Windows 10 버전 1903 미만에서 회사 및 학교 계정 등록을 추가하는 동안 등록 상태 페이지가 항상 시간 초과됩니다. 등록 상태 페이지는 Azure AD 등록이 완료될 때까지 기다립니다. 이 문제는 Windows 10 버전 1903 이상에서 해결되었습니다.  
- ESP를 사용하는 하이브리드 Azure AD Autopilot 배포는 ESP 프로필에 정의된 시간 제한보다 오래 걸립니다. 하이브리드 Azure AD Autopilot 배포에서 ESP는 ESP 프로필에 설정된 값보다 40분 이상 더 소요됩니다. 이러한 지연은 온-프레미스 AD 커넥터에서 Azure AD에 대한 새 디바이스 레코드를 만들 시간을 제공합니다. 
- Windows 로그온 페이지가 Autopilot 사용자 기반 모드의 사용자 이름으로 미리 채워져 있지 않습니다. ESP의 디바이스 설정 단계에서 재부팅하는 경우:
    - 사용자 자격 증명이 유지되지 않습니다.
    - 사용자가 디바이스 설정 단계에서 계정 설정 단계로 진행하기 전에 자격 증명을 다시 입력해야 합니다.
- ESP가 오랫동안 중지되었거나 "식별 중" 단계가 완료되지 않습니다. Intune은 식별 단계 중에 ESP 정책을 평가합니다. 현재 사용자에게 Intune 라이선스가 할당되지 않은 경우 디바이스에서 ESP 정책 평가를 완료하지 못할 수 있습니다.  
- Microsoft Defender 애플리케이션 제어를 구성하면 Autopilot 중에 재부팅하라는 메시지가 표시됩니다. Microsoft Defender 애플리케이션(AppLocker CSP)을 구성하려면 재부팅해야 합니다. 이 정책이 구성되면 디바이스가 Autopilot 중에 재부팅될 수 있습니다. 현재는 재부팅을 억제하거나 연기할 수 있는 방법이 없습니다.
- DeviceLock 정책(https://docs.microsoft.com/windows/client-management/mdm/policy-csp-devicelock) 을 ESP 프로필의 일부로 사용하도록 설정된 경우 두 가지 이유 때문에 OOBE 또는 사용자 데스크톱 자동 로그온이 예기치 않게 실패할 수 있습니다.
  - ESP 디바이스 설정 단계를 종료하기 전에 디바이스를 재부팅하지 않으면 사용자에게 Azure AD 자격 증명을 입력하라는 메시지가 표시될 수 있습니다. 사용자에게 Windows 첫 번째 로그인 애니메이션이 표시되는 자동 로그온 성공 메시지 대신 이 메시지가 표시됩니다.
  - 사용자가 Azure AD 자격 증명을 입력했지만 ESP 디바이스 설정 단계를 종료하기 전에 디바이스를 재부팅하면 자동 로그온에 실패합니다. 이 오류는 ESP 디바이스 설정 단계가 완료되지 않았기 때문에 발생합니다. 해결 방법은 디바이스를 재설정하는 것입니다.

## <a name="next-steps"></a>다음 단계
Windows 등록 페이지를 설정한 후 Windows 디바이스를 관리하는 방법을 알아봅니다. 자세한 내용은 [Microsoft Intune 디바이스 관리란?](../remote-actions/device-management.md)을 참조하세요.
