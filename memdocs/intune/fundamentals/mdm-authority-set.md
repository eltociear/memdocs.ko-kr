---
title: 모바일 디바이스 관리 기관을 설정합니다.
titleSuffix: Microsoft Intune
description: Intune으로 모바일 디바이스 관리 기관을 설정합니다.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 08/16/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.assetid: 8deff871-5dff-4767-9484-647428998d82
ms.reviewer: damionw
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 651ab8488503594a9e6cf82af1731ca31c8035ed
ms.sourcegitcommit: 3d895be2844bda2177c2c85dc2f09612a1be5490
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79362188"
---
# <a name="set-the-mobile-device-management-authority"></a>모바일 디바이스 관리 기관을 설정합니다.

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

MDM(모바일 디바이스 관리) 기관 설정에 따라 디바이스를 관리하는 방법이 결정됩니다. IT 관리자가 MDM 기관을 설정해야 사용자가 관리를 위해 디바이스를 등록할 수 있습니다.

가능한 구성은 다음과 같습니다.

- **Intune 독립 실행형** - Azure Portal을 사용하여 구성하는 클라우드 전용 관리입니다. Intune에서 제공하는 모든 기능 집합을 포함합니다. [Intune 콘솔에서 MDM 기관을 설정합니다](#set-mdm-authority-to-intune).

- **Intune 공동 관리** - Windows 10 디바이스를 위한 Intune 클라우드 솔루션과 Configuration Manager의 통합입니다. Configuration Manager 콘솔을 사용하여 Intune을 구성합니다. [Intune에 대한 디바이스 자동 등록을 구성합니다](https://docs.microsoft.com/configmgr/comanage/tutorial-co-manage-clients#configure-auto-enrollment-of-devices-to-intune). 

- **Office 365용 모바일 디바이스 관리**  - Office 365와 Intune 클라우드 솔루션의 통합입니다. Microsoft 365 관리 센터에서 Intune을 구성합니다. Intune 독립 실행형에서 제공되는 기능 중 일부를 포함합니다. Microsoft 365 관리 센터에서 MDM 기관을 설정합니다.

- **Office 365 MDM 동시 사용** 테넌트에서 Office 365용 MDM과 Intune을 동시에 활성화하고 사용할 수 있으며, 각 사용자가 모바일 디바이스를 관리하는 데 사용되는 서비스를 결정할 수 있도록 관리 기관을 Intune 또는 Office 365용 MDM으로 설정할 수 있습니다. 사용자의 관리 기관은 사용자에게 할당된 라이선스에 따라 정의됩니다. 자세한 내용은 [Office 365용 MDM과 함께 Microsoft Intune 동시 사용](https://blogs.technet.microsoft.com/configmgrdogs/2016/01/04/microsoft-intune-co-existence-with-mdm-for-office-365)을 참조하세요.

## <a name="set-mdm-authority-to-intune"></a>MDM 기관을 Intune으로 설정

MDM 기관을 아직 설정하지 않은 경우 다음 단계를 수행합니다.

1. [Microsoft Endpoint Manager 관리 센터](https://go.microsoft.com/fwlink/?linkid=2109431)에서 주황색 배너를 선택하여 **모바일 디바이스 관리 기관** 설정을 엽니다. 주황색 배너는 MDM 기관을 아직 설정하지 않은 경우만 표시됩니다.
2. **모바일 디바이스 관리 기관** 아래에서, 다음 옵션 중에서 MDM 기관을 선택합니다.
   - **Intune MDM 기관**
   - **없음**

   ![Intune의 모바일 디바이스 관리 기관 설정 화면 스크린샷](./media/mdm-authority-set/set-mdm-auth.png)

   MDM 기관을 Intune으로 설정했음을 나타내는 메시지가 표시됩니다.

### <a name="workflow-of-intune-administration-ui"></a>Intune 관리 UI의 워크플로
Android 또는 Apple 디바이스 관리를 사용하는 경우 Intune은 이러한 타사 서비스와 통합하는 디바이스 및 사용자 정보를 보내 해당 디바이스를 관리합니다.

데이터 공유 동의를 추가하는 시나리오는 다음과 같습니다.
- Android 회사 프로필을 사용합니다.
- Apple MDM 푸시 인증서를 사용하고 업로드.
- DEP(장비 등록 프로그램), School Manager, Volume Purchasing Program 등의 Apple 서비스 중 하나를 사용.

각 경우에 동의는 모바일 디바이스 관리 서비스의 실행과 관련하여 엄격히 적용됩니다. 예를 들어 IT 관리자는 등록을 위해 Google 또는 Apple 디바이스를 인증했는지 확인합니다. 새 워크플로가 가동될 때 어떤 정보가 공유되는지 알려주는 설명서는 다음 위치에 있습니다.
- [Intune이 Google에 보내는 데이터](https://aka.ms/Data-intune-sends-to-google)
- [Intune이 Apple에 보내는 데이터](https://aka.ms/data-intune-sends-to-apple)

## <a name="key-considerations"></a>핵심 고려 사항
새 MDM 기관으로 변경하면 디바이스가 서비스에 체크 인되어 동기화되기 전에 전환 시간(최대 8시간)이 필요할 수 있습니다. 등록된 디바이스가 변경 후에도 계속 관리되고 보호되도록 하려면 새 MDM 기관에서 설정을 구성해야 합니다. 
- 디바이스는 새 MDM 기관(Intune 독립 실행형)의 설정이 디바이스의 기존 설정을 대체하도록 변경 후에도 서비스에 연결되어야 합니다.
- MDM 기관을 변경한 후 이전 MDM 기관의 일부 기본 설정(예: 프로필)이 최대 7일 동안 또는 디바이스가 서비스에 처음 연결될 때까지 디바이스에 남아 있습니다. 새 MDM 기관에서 최대한 신속하게 앱 및 설정(정책, 프로필, 앱 등)을 구성하고, 기존의 등록된 디바이스를 가진 사용자가 포함된 사용자 그룹에 해당 설정을 배포하는 것이 좋습니다. MDM 기관에서 변경이 수행되고 디바이스가 서비스에 연결되는 즉시, 새 MDM 기관에서 새 설정을 수신되므로 관리 및 보호의 부재가 나타나지 않습니다.
- 연결된 사용자가 없는 디바이스(일반적으로 iOS/iPadOS 장비 등록 프로그램 또는 대량 등록 시나리오가 있는 경우)는 새 MDM 기관으로 마이그레이션되지 않습니다. 이러한 디바이스의 경우 새 MDM 기관으로 이동하려면 지원 서비스에 문의해야 합니다.

## <a name="change-mdm-authority-to-office-365"></a>MDM 기관을 Office 365로 변경

Office 365 MDM을 활성화(또는 기존 Intune 서비스 외에 MDM 공동 사용을 사용하도록 설정)하려면 [https://protection.office.com](https://protection.office.com)으로 이동하여 **데이터 손실 방지** > **디바이스 보안 정책** > **관리되는 디바이스 목록 보기** > **시작하기**를 선택합니다.

자세한 내용은 [Office 365에서 MDM(모바일 디바이스 관리) 설정](https://support.office.com/en-us/article/Set-up-Mobile-Device-Management-MDM-in-Office-365-dd892318-bc44-4eb1-af00-9db5430be3cd)을 참조하세요.

Office 365 MDM에서만 최종 사용자를 관리하려면 Office 365 MDM을 활성화한 후 할당된 Intune 및/또는 EMS 라이선스를 모두 제거합니다.

## <a name="mobile-device-cleanup-after-mdm-certificate-expiration"></a>MDM 인증서 만료 후 모바일 디바이스 정리

MDM 인증서는 모바일 디바이스가 Intune 서비스와 통신할 때 자동으로 갱신됩니다. 모바일 디바이스가 초기화되거나 일정 기간에 Intune 서비스와 통신하지 못한 경우에는 MDM 인증서가 갱신되지 않습니다. MDM 인증서가 만료되고 180일 후 Azure Portal에서 디바이스가 제거됩니다.

## <a name="remove-mdm-authority"></a>MDM 기관 제거

MDM 기관을 Unknown으로 다시 변경할 수 없습니다. MDM 기관은 등록된 디바이스가 보고하는 포털(Microsoft Intune 또는 Office 365 MDM)을 서비스가 확인하는 데 사용됩니다.

## <a name="what-to-expect-after-changing-the-mdm-authority"></a>MDM 기관 변경 후 예상되는 상황

- Intune 서비스에서 테넌트의 MDM 기관이 변경되었음을 감지하면 서비스에 체크 인하고 동기화하기 위해 등록된 모든 디바이스에 알림 메시지를 보냅니다(이 알림은 정기적으로 예약된 체크 인을 벗어남). 따라서 테넌트의 MDM 기관이 Intune 독립 실행형에서 변경된 후에 전원이 켜져 있고 온라인 상태인 모든 디바이스는 서비스에 연결되고, 새 MDM 기관을 수신하고, 새 MDM 기관에서 관리되게 됩니다. 이러한 서비스의 관리 및 보호가 중단되는 일은 없습니다.
- MDM 기관을 변경하는 동안(또는 직후에) 전원이 켜져 있고 온라인 상태인 디바이스의 경우에도 디바이스가 새 MDM 기관의 서비스에 등록되기까지 최대 8시간의 지연이 있습니다(예약된 다음 정기 체크 인 타이밍에 따라).    

  > [!IMPORTANT]    
  > MDM 기관을 변경하는 시간과 갱신된 APN 인증서를 새 기관으로 업로드하는 시간 사이의 iOS/iPadOS 디바이스에 대한 새 디바이스 등록 및 디바이스 체크 인에 실패합니다. 따라서 MDM 기관을 변경한 후 가능한 한 빨리 APNs 인증서를 갱신하고 새 인증 기관에 업로드하는 것이 중요합니다.

- 사용자는 디바이스에서 서비스로의 체크 인을 수동으로 시작하여 새 MDM 기관을 빠르게 변경할 수 있습니다. 사용자는 회사 포털 앱을 사용하고 디바이스 준수 검사를 시작하여 이 변경을 쉽게 수행할 수 있습니다.
- 디바이스가 MDM 기관을 변경한 다음 서비스에 체크 인되고 동기화된 후에 작업이 제대로 작동하는지 확인하려면 새 MDM 기관에서 디바이스를 찾습니다.
- MDM 기관 변경 동안 디바이스가 오프라인 상태일 때와 디바이스가 서비스로 체크 인될 때까지의 중간 기간이 있습니다. 이 중간 기간 동안 디바이스가 보호되고 제대로 작동되도록 하기 위해 최대 7일 동안(또는 디바이스가 새 MDM 기관에 연결되고 기존 설정을 덮어쓰는 새 설정을 받을 때까지) 디바이스에서 다음 프로필이 그대로 유지됩니다.
  - 전자 메일 프로필
  - VPN 프로필
  - 인증서 프로필
  - Wi-Fi 프로필
  - 구성 프로필
- 새 MDM 기관으로 변경한 후 Microsoft Intune 관리 콘솔의 준수 데이터가 정확히 보고될 때가지 최대 1주가 걸릴 수 있습니다. 그러나 Azure Active Directory 및 디바이스의 준수 상태는 정확하게 유지되므로 디바이스는 계속 보호됩니다.
- 기존 설정을 덮어쓰고 새로 사용하려는 설정은 이전 이름과 같은 이름이어야 합니다. 그렇지 않으면 디바이스에서 프로필 및 정책이 중복될 수 있습니다.    

  > [!TIP]    
  > 모범 사례는 MDM 기관 변경이 완료된 즉시, 모든 배포 뿐만 아니라 모든 관리 설정과 구성을 만드는 것입니다. 이렇게 하면 중간 기간 동안에도 디바이스가 보호되고 능동적으로 관리될 수 있습니다.

- MDM 기관을 변경한 후 다음 단계를 수행하여 새 디바이스가 새 기관에 성공적으로 등록되었는지 확인합니다.   
  - 새 디바이스 등록
  - 새로 등록된 디바이스가 새 MDM 기관에 표시되는지 확인합니다.
  - 디바이스의 관리 콘솔에서 원격 잠금 등의 작업을 수행합니다. 성공한 경우 디바이스가 새 MDM 기관에서 관리되는 것입니다.
- 특정 디바이스에 문제가 있는 경우 등록을 취소했다가 다시 등록하여 가능한 한 빠른 시일 내에 디바이스가 새 기관에 연결되고 관리될 수 있도록 합니다.

## <a name="next-steps"></a>다음 단계

MDM 기관을 설정하면 [디바이스 등록](../enrollment/device-enrollment.md)을 시작할 수 있습니다.
