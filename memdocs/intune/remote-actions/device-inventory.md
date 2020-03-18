---
title: Microsoft Intune - Azure를 사용하여 디바이스 세부 정보 보기 | Microsoft Docs
description: 운영 체제, 스토리지 공간, 제조업체 및 모델을 비롯한 디바이스 세부 정보를 봅니다. Azure에서 Microsoft Intune을 사용하여 설치된 앱의 목록을 가져오고, 준수 정책을 확인하고, TeamViewer를 설정합니다. 관리하는 디바이스의 인벤토리 보기와 유사합니다.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/27/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: remote-actions
ms.localizationpriority: high
ms.technology: ''
ms.assetid: e71c6bdb-d75c-404f-8e38-24a663be81c2
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: df00db079a7e6b73ba24dc612b5cb6b2250c3898
ms.sourcegitcommit: 3d895be2844bda2177c2c85dc2f09612a1be5490
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79338190"
---
# <a name="see-device-details-in-intune"></a>Intune에서 디바이스 세부 정보 참조

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

**디바이스** 기능은 하드웨어 및 설치된 앱을 비롯하여 관리하는 디바이스에 추가 세부 정보를 제공합니다.

이 문서는 Azure Portal에서 모든 디바이스 및 해당 속성을 보는 방법을 보여줍니다.

## <a name="view-the-device-details"></a>디바이스 세부 정보 보기

1. [Microsoft Endpoint Manager 관리 센터](https://go.microsoft.com/fwlink/?linkid=2109431)에 로그인합니다.
3. **디바이스** > **모든 디바이스** 선택 &gt; 해당 세부 정보를 열려면 나열된 디바이스 중 하나를 선택합니다.

   - **개요**는 디바이스 이름을 표시하고 BYOD(bring-your-own-device) 디바이스인지 여부, 체크 인 시간 등과 같은 디바이스의 몇 가지 주요 속성을 나열합니다. 이 디바이스에서는 다음 작업을 수행할 수 있습니다.
      - [사용 중지](devices-wipe.md#retire)
      - [초기화](devices-wipe.md#wipe)
      - [삭제](devices-wipe.md#delete-devices-from-the-intune-portal)
      - [원격 잠금](device-remote-lock.md)
      - [동기화](device-sync.md)
      - [암호 초기화](device-passcode-reset.md)
      - [다시 시작](device-restart.md)(Windows만 해당)
      - [새로 시작](device-fresh-start.md)(Windows만 해당)
      - [Autopilot 다시 설정](/windows/deployment/windows-autopilot/windows-autopilot-reset#reset-devices-with-remote-windows-autopilot-reset)(Windows에만 해당)
      - [빠른 검사](../configuration/device-restrictions-windows-10.md)(Windows 10에만 해당)
      - [전체 검사](../configuration/device-restrictions-windows-10.md)(Windows 10에만 해당)
       - [디바이스 이름 바꾸기](device-rename.md)
      - 원격 지원 세션 시작
   - **속성**을 사용하여 [만든 디바이스 범주](../enrollment/device-group-mapping.md)를 할당하고, 디바이스 소유권을 개인 디바이스나 회사 디바이스로 변경합니다.
   - **하드웨어**에는 디바이스 ID, 운영 체제 및 버전, 저장소 공간, 자세한 정보 등 디바이스에 대한 많은 정보가 포함되어 있습니다.
   - **검색된 앱**은 Intune이 디바이스에 설치한 모든 앱 및 앱 버전을 표시합니다. 자세한 내용은 [Intune에서 검색된 앱](../apps/app-discovered-apps.md)을 참조하세요.
   - **디바이스 준수**는 모든 할당된 준수 정책 및 디바이스가 준수 또는 비준수인지 여부를 표시합니다.
   - **디바이스 구성**은 디바이스에 할당된 모든 디바이스 구성 정책 및 정책이 성공 또는 실패인지 여부를 표시합니다.

## <a name="hardware-device-details"></a>하드웨어 디바이스 세부 정보
디바이스별 이동 통신 사업자에 따라 일부 세부 정보를 수집하지 않을 수 있습니다.

> [!Note]  
> 하드웨어 및 소프트웨어 인벤토리는 일주일마다 Intune 서비스에서 새로 고쳐집니다.

|세부 정보|설명|플랫폼| 
|--------------|----------------------|----|  
|Name|서버의 이름입니다.|Windows, iOS|
|관리 이름|콘솔에서만 사용되는 디바이스 이름입니다. 이 이름을 변경해도 디바이스의 이름을 변경하지 않습니다.|Windows, iOS|
|UDID|디바이스의 고유한 디바이스 식별자입니다.|Windows, iOS|
|Intune 디바이스 ID|디바이스를 고유하게 식별하는 GUID입니다.|Windows, iOS|
|일련 번호|제조업체에서 디바이스의 일련 번호입니다.|Windows, iOS|
|공유 디바이스|**예**인 경우 디바이스가 둘 이상의 사용자에 의해 공유됩니다.|Windows, iOS|
|사용자 승인 등록|**예**인 경우 디바이스에는 관리자가 디바이스에서 특정 보안 설정을 관리할 수 있는 사용자 승인 등록이 있습니다.|Windows, iOS|
|운영 체제|디바이스에서 사용된 운영 체제입니다.|Windows, iOS|
|운영 체제 버전|디바이스의 운영 체제 버전입니다.|Windows, iOS|
|운영 체제 언어|디바이스의 운영 체제에 대해 설정된 언어입니다.|Windows, iOS|
|빌드 번호|운영 체제 빌드 번호입니다.|Android|
|보안 패치 수준|디바이스에 대한 보안 패치 수준입니다.|Android|
|총 스토리지 공간|디바이스의 총 스토리지 공간(기가바이트)입니다.|Windows, iOS|
|사용 가능한 스토리지 공간|디바이스에서 사용되지 않은 스토리지 공간(기가바이트)입니다.|Windows, iOS|
|IMEI|디바이스의 IMEI(International Mobile Equipment Identity)입니다.|Windows, iOS/iPadOS, Android|
|MEID|디바이스의 MEID(Mobile Equipment Identifier)입니다.|Windows, iOS/iPadOS, Android|
|제조업체|디바이스의 제조업체입니다.|Windows, iOS/iPadOS, Android|
|모델|디바이스의 모델입니다.|Windows, iOS/iPadOS, Android|
|전화 번호|디바이스에 할당된 전화 번호입니다.|Windows, iOS/iPadOS, Android*|
|구독자의 통신사|디바이스의 무선 통신사입니다.|Windows, iOS/iPadOS, Android|
|셀룰러 기술|디바이스에서 사용하는 라디오 시스템입니다.|Windows, iOS/iPadOS, Android|
|Wi-Fi MAC|디바이스의 미디어 액세스 제어 주소입니다.|Windows, iOS/iPadOS, Android|
|ICCID|집적 회로 카드 식별자, 즉, SIM 카드의 고유한 ID 번호입니다.|Windows, iOS/iPadOS, Android|
|등록된 날짜|Intune에서 디바이스를 등록한 날짜 및 시간입니다.|Windows, iOS/iPadOS, Android|
|마지막 연결|Intune에 디바이스를 마지막으로 연결한 날짜 및 시간입니다.|Windows, iOS/iPadOS, Android|
|활성화 잠금 무시 코드|활성화 잠금을 사용하지 않도록 설정하는 데 사용할 수 있는 코드입니다.|iOS|
|Azure AD 등록됨|**예**인 경우 디바이스가 Azure Active Directory에 등록되어 있습니다.|Windows, iOS/iPadOS, Android|
|Intune에 등록됨|**예**인 경우 디바이스가 Intune에 등록되어 있음|Windows, iOS/iPadOS, Android|
|준수|디바이스의 준수 상태입니다.|Windows, iOS/iPadOS, Android|
|EAS 활성화됨|**예**인 경우 디바이스는 교환 사서함과 동기화됩니다.|Windows, iOS/iPadOS, Android|
|EAS 활성화 ID|디바이스의 Exchange ActiveSync 식별자입니다.|Windows, iOS/iPadOS, Android|
|감독됨|**예**인 경우 관리자는 디바이스에 대한 제어를 강화했습니다.|Windows, iOS/iPadOS, Android|
|암호화됨|**예**인 경우 디바이스에 저장된 데이터가 암호화됩니다.|Windows, iOS/iPadOS, Android|

> [!Note]  
> Android Enterprise 전용 또는 완전 관리형 디바이스에서는 전화 번호가 인벤토리에 포함되지 않습니다.

## <a name="next-steps"></a>다음 단계
Intune을 사용하여 [디바이스를 관리](device-management.md)하기 위해 수행할 수 있는 작업을 참조하세요.
