---
title: Intune 및 Zimperium MTD 커넥터 통합
titleSuffix: Intune on Azure
description: 회사 리소스에 대한 모바일 디바이스 액세스를 제어하기 위해 Zimperium MTD(Mobile Threat Defense)와 Intune을 통합하는 방법을 알아봅니다.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 03/09/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 975d8d84-792a-41ad-925a-4a7f1ae4dcaf
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: ed623abeb602e599866af7b7249756edd87d5a29
ms.sourcegitcommit: 3d895be2844bda2177c2c85dc2f09612a1be5490
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79349201"
---
# <a name="zimperium-mobile-threat-defense-connector-with-intune"></a>Intune 및 Zimperium MTD(Mobile Threat Defense) 커넥터 통합

Microsoft Intune과 통합되는 MTD(Mobile Threat Defense) 솔루션인 Zimperium에서 수행된 위험 평가에 따라 조건부 액세스를 사용하여 모바일 디바이스에서 회사 리소스에 대한 액세스를 제어할 수 있습니다. 위험은 Zimperium 앱을 실행하는 디바이스에서 수집된 원격 분석에 기반하여 평가됩니다.

등록된 디바이스의 Intune 디바이스 준수 정책을 통해 사용하도록 설정된 Zimperium 위험 평가에 따라 조건부 액세스 정책을 구성할 수 있습니다. 이 정책을 사용하여 감지된 위협에 따라 비규격 디바이스의 회사 리소스에 대한 액세스를 허용하거나 차단할 수 있습니다. 등록이 취소된 디바이스의 경우 앱 보호 정책을 사용하여 검색된 위협에 따라 차단 또는 선택적 초기화를 적용할 수 있습니다.

## <a name="supported-platforms"></a>지원되는 플랫폼

- **Android 4.1 이상**

- **iOS 8 이상**

## <a name="prerequisites"></a>전제 조건

- Azure Active Directory Premium

- Microsoft Intune 구독

- Zimperium Mobile Threat Defense 구독

  - 자세한 내용은 [Zimperium 웹 사이트](https://www.zimperium.com/zips-mobile-ips)를 참조하세요.

## <a name="how-do-intune-and-zimperium-help-protect-your-company-resources"></a>Intune과 Zimperium이 회사 리소스를 어떻게 보호하나요?

Android 및 iOS/iPadOS용 Zimperium 앱은 사용 가능한 경우 파일 시스템, 네트워크 스택, 디바이스 및 애플리케이션 원격 분석을 캡처한 다음, 원격 분석 데이터를 Zimperium 클라우드 서비스로 보내 모바일 위협에 대한 디바이스의 위험을 평가합니다.

- **등록된 디바이스 지원** - Intune 디바이스 준수 정책에는 Zimperium의 위험 평가 정보를 사용할 수 있는 MTD(Mobile Threat Defense) 규칙이 포함되어 있습니다. MTD 규칙을 사용하도록 설정하면 Intune은 사용하도록 설정된 정책을 디바이스가 준수하는지 평가합니다. 디바이스가 정책을 준수하지 않으면 Exchange Online, SharePoint Online 등의 회사 리소스에 대한 사용자의 액세스가 차단됩니다. 또한 사용자는 디바이스에 설치된 Zimperium 앱에서 지침을 받아 문제를 해결하고 회사 리소스에 대한 액세스 권한을 다시 얻을 수 있습니다. 등록된 디바이스에서 Zimperium 사용을 지원하려면 다음을 수행합니다.
  - [디바이스에 MTD 앱 추가](../protect/mtd-apps-ios-app-configuration-policy-add-assign.md)
  - [MTD를 지원하는 디바이스 준수 정책 만들기](../protect/mtd-device-compliance-policy-create.md)
  - [Intune에서 MTD 커넥터 사용](../protect/mtd-connector-enable.md)

- **등록되지 않은 디바이스 지원** - Intune 앱 보호 정책을 사용하면 Intune이 등록되지 않은 디바이스에서 Zimperium의 위험 평가 데이터를 사용할 수 있습니다. 관리자는 이 조합을 사용하여 [Microsoft Intune 보호 앱](../apps/apps-supported-intune-apps.md) 내에서 회사 데이터를 보호하고 이러한 등록되지 않은 디바이스에서 회사 데이터를 차단하거나 선택적으로 초기화할 수 있습니다. 등록되지 않은 디바이스에서 Zimperium 사용을 지원하려면 다음을 수행합니다.
  - [등록되지 않은 디바이스에 MTD 앱 추가](../protect/mtd-add-apps-unenrolled-devices.md)
  - [Mobile Threat Defense 앱 보호 정책 만들기](../protect/mtd-app-protection-policy.md)
  - [Intune에서 등록되지 않은 디바이스에 MTD 커넥터를 사용하도록 설정](../protect/mtd-enable-unenrolled-devices.md)
  
## <a name="sample-scenarios"></a>샘플 시나리오:

Intune과 Zimperium을 통합하는 경우 아래의 몇 가지 시나리오를 참조하세요.

### <a name="control-access-based-on-threats-from-malicious-apps"></a>악성 앱의 위협에 따라 액세스 제어

맬웨어와 같은 악성 앱이 디바이스에서 감지되면 위협이 해결될 때까지 디바이스를 차단할 수 있습니다.

- 회사 메일에 연결

- 작업용 OneDrive 앱과 회사 파일 동기화

- 회사 앱에 액세스

*악성 앱이 발견되면 액세스 차단:*

> [!div class="mx-imgBorder"]
> ![감지된 악성 앱의 개념 이미지](./media/zimperium-mobile-threat-defense-connector/Maliciousapps-blocked-zimperium.png)

*수정 시 액세스 권한 부여됨:*

> [!div class="mx-imgBorder"]
> ![업데이트 관리 후 부여된 액세스 권한의 개념 이미지](./media/zimperium-mobile-threat-defense-connector/maliciousapps-unblocked-zimperium.png)

### <a name="control-access-based-on-threat-to-network"></a>네트워크에 대한 위협에 따라 액세스 제어

네트워크에서 **메시지 가로채기(man-in-the-middle)** 와 같은 위협을 감지하고 디바이스 위험에 따라 Wi-Fi 네트워크에 대한 액세스를 보호합니다.

*Wi-Fi를 통한 네트워크 액세스 차단:*

> [!div class="mx-imgBorder"]
> ![Wi-Fi를 통한 네트워크 액세스 차단](./media/zimperium-mobile-threat-defense-connector/network-wifi-blocked-zimperium.png)

*수정 시 액세스 권한 부여됨:*

> [!div class="mx-imgBorder"]
> ![수정 시 액세스 권한 부여됨](./media/zimperium-mobile-threat-defense-connector/network-wifi-unblocked-zimperium.png)

### <a name="control-access-to-sharepoint-online-based-on-threat-to-network"></a>네트워크 위협에 따라 SharePoint Online에 대한 액세스 제어

네트워크에서 **메시지 가로채기(man-in-the-middle)** 와 같은 공격을 감지하여, 디바이스 위험에 따라 회사 파일 동기화를 금지합니다.

*네트워크 위협이 감지할 경우 SharePoint Online 차단:*

> [!div class="mx-imgBorder"]
> ![네트워크 위협이 감지되면 SharePoint Online 차단](./media/zimperium-mobile-threat-defense-connector/network-spo-blocked-zimperium.png)

*수정 시 액세스 권한 부여됨:*

> [!div class="mx-imgBorder"]
> ![SharePoint에 대해 수정 시 액세스 권한이 부여된 예](./media/zimperium-mobile-threat-defense-connector/network-spo-unblocked-zimperium.png)

### <a name="control-access-on-unenrolled-devices-based-on-threats-from-malicious-apps"></a>악성 앱의 위협에 따라 등록되지 않은 디바이스에서 액세스 제어

Zimperium Mobile Threat Defense 솔루션에서 디바이스가 감염된 것으로 간주하는 경우:

> [!div class="mx-imgBorder"]
> ![감지된 맬웨어로 인한 앱 보호 정책 차단](./media/zimperium-mobile-threat-defense-connector/zimperium-mobile-app-policy-block.png)

수정 시 액세스 권한 부여됨:

> [!div class="mx-imgBorder"]
> ![앱 보호 정책에 대한 수정 시 액세스 권한 부여됨](./media/zimperium-mobile-threat-defense-connector/zimperium-mobile-app-policy-remediated.png)

## <a name="next-steps"></a>다음 단계

- [Intune 및 Zimperium 통합](zimperium-mtd-connector-integration.md)

- [Zimperium 앱 설정](mtd-apps-ios-app-configuration-policy-add-assign.md)

- [Zimperium 디바이스 준수 정책 만들기](mtd-device-compliance-policy-create.md)

- [Zimperium MTD 커넥터 사용](mtd-connector-enable.md)

- [MTD 앱 보호 정책 만들기](../protect/mtd-app-protection-policy.md)
