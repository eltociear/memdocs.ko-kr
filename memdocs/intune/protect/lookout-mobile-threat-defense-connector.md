---
title: Microsoft Intune을 사용한 Lookout MTD 커넥터
titleSuffix: Microsoft Intune
description: 회사 리소스에 대한 모바일 디바이스 액세스를 제어하기 위해 Lookout MTD(모바일 위협 방어)를 사용하여 Intune을 통합하는 방법을 알아봅니다.
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
ms.assetid: 3a730a5d-2a90-42b0-aa28-aadfc7a18788
ms.reviewer: davera
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 1b3927f09bb74f9058b19dad7f2f3b72f21a0d43
ms.sourcegitcommit: 3d895be2844bda2177c2c85dc2f09612a1be5490
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79351931"
---
# <a name="lookout-mobile-endpoint-security-connector-with-intune"></a>Intune을 사용한 Lookout Mobile Endpoint Security 커넥터

Microsoft Intune과 통합된 Mobile Threat Defense 솔루션인 Lookout에서 수행한 위험 평가에 따라 회사 리소스에 대한 모바일 디바이스의 액세스를 제어할 수 있습니다. 위험은 다음을 비롯하여 Lookout 서비스를 통해 디바이스에서 수집된 원격 분석에 따라 평가됩니다.

- 운영 체제 취약점
- 설치된 악성 앱
- 악성 네트워크 프로필

등록된 디바이스의 Intune 준수 정책을 통해 사용하도록 설정된 Lookout 위험 평가에 따라 조건부 액세스 정책을 구성할 수 있습니다. 이 정책을 사용하여 회사 리소스에 액세스하는 비규격 디바이스를 감지된 위협에 따라 허용하거나 차단할 수 있습니다. 등록이 취소된 디바이스의 경우 앱 보호 정책을 사용하여 검색된 위협에 따라 차단 또는 선택적 초기화를 적용할 수 있습니다.

## <a name="how-do-intune-and-lookout-mobile-endpoint-security-help-protect-company-resources"></a>Intune과 Lookout Mobile Endpoint Security가 회사 리소스를 보호하는 데 어떤 도움이 되나요?

Lookout의 모바일 앱인 **Lookout for Work**가 모바일 디바이스에서 설치되어 실행됩니다. 이 앱은 파일 시스템, 네트워크 스택, 디바이스 및 앱 원격 분석(사용 가능한 경우)을 캡처한 다음, Lookout 클라우드 서비스로 보내 모바일 위협에 대한 디바이스의 위험을 평가합니다. 요구 사항에 맞게 Lookout 콘솔에서 위협에 대한 위험 수준 분류를 변경할 수 있습니다.

- **등록된 디바이스 지원** - Intune 디바이스 준수 정책에는 Lookout for Work의 위험 평가 정보를 사용할 수 있는 MTD(Mobile Threat Defense) 규칙이 포함되어 있습니다. MTD 규칙을 사용하도록 설정하면 Intune은 사용하도록 설정된 정책을 디바이스가 준수하는지 평가합니다. 디바이스가 정책을 준수하지 않으면 Exchange Online, SharePoint Online 등의 회사 리소스에 대한 사용자의 액세스가 차단됩니다. 또한 사용자는 디바이스에 설치된 Lookout for Work 앱에서 지침을 받아 문제를 해결하고 회사 리소스에 대한 액세스 권한을 다시 얻을 수 있습니다. 등록된 디바이스를 Lookout for Work를 사용하여 지원하려면 다음을 수행합니다.
  - [디바이스에 MTD 앱 추가](../protect/mtd-apps-ios-app-configuration-policy-add-assign.md)
  - [MTD를 지원하는 디바이스 준수 정책 만들기](../protect/mtd-device-compliance-policy-create.md)
  - [Intune에서 MTD 커넥터 사용 설정](../protect/mtd-connector-enable.md)

- **등록되지 않은 디바이스 지원** - Intune 앱 보호 정책을 사용하면 Intune이 등록되지 않은 디바이스에서 Lookout for Work의 위험 평가 데이터를 사용할 수 있습니다. 관리자는 이 조합을 사용하여 [Microsoft Intune 보호 앱](../apps/apps-supported-intune-apps.md) 내에서 회사 데이터를 보호하고 이러한 등록되지 않은 디바이스에서 회사 데이터를 차단하거나 선택적으로 초기화할 수 있습니다. 등록되지 않은 디바이스에서 Lookout for Work를 사용하여 지원하려면 다음을 수행합니다.
  - [등록되지 않은 디바이스에 MTD 앱 추가](../protect/mtd-add-apps-unenrolled-devices.md)
  - [Mobile Threat Defense 앱 보호 정책 만들기](../protect/mtd-app-protection-policy.md)
  - [Intune에서 등록되지 않은 디바이스에 MTD 커넥터를 사용하도록 설정](../protect/mtd-enable-unenrolled-devices.md)

## <a name="supported-platforms"></a>지원되는 플랫폼

Intune에 등록한 경우 다음과 같은 플랫폼에서 Lookout이 지원됩니다.

- **Android 4.1 이상**  
- **iOS 8 이상**  

플랫폼 및 언어 지원에 대한 자세한 내용은 [Lookout 웹 사이트](https://personal.support.lookout.com/hc/articles/114094140253)를 참조하세요.  

## <a name="prerequisites"></a>전제 조건

- Lookout Mobile EndPoint Security 엔터프라이즈 구독  
- Microsoft Intune 구독
- Azure Active Directory Premium
- 사용자에게 라이선스가 할당된 EMS(Enterprise Mobility + Security) E3 또는 E5  

자세한 내용은 [Lookout Mobile Endpoint Security](https://www.lookout.com/products/mobile-endpoint-security)를 참조하세요.

## <a name="sample-scenarios"></a>샘플 시나리오:

Intune과 함께 Mobile Endpoint Security를 사용할 때의 일반적인 시나리오는 다음과 같습니다.

### <a name="control-access-based-on-threats-from-malicious-apps"></a>악성 앱의 위협에 따라 액세스 제어

맬웨어와 같은 악성 앱이 디바이스에서 감지되면 위협이 해결될 때까지 다음으로부터 디바이스를 차단할 수 있습니다.

- 회사 메일에 연결
- 작업용 OneDrive 앱과 회사 파일 동기화
- 회사 앱에 액세스

*악성 앱이 발견되면 액세스 차단:*

> [!div class="mx-imgBorder"]
> ![악성 앱으로 인한 액세스 차단 정책의 개념 이미지](./media/lookout-mobile-threat-defense-connector/malicious-apps-blocked.png)

*수정 시 액세스 권한 부여됨:*

> [!div class="mx-imgBorder"]
> ![수정 후 디바이스에 부여된 액세스 권한을 보여 주는 개념 이미지](./media/lookout-mobile-threat-defense-connector/malicious-apps-unblocked.png)

### <a name="control-access-based-on-threat-to-network"></a>네트워크에 대한 위협에 따라 액세스 제어

메시지 가로채기(man-in-the-middle) 공격과 같은 사용자 네트워크 위협을 검색하고 디바이스 위험에 따라 Wi-Fi 네트워크에 대한 액세스를 보호합니다.

*Wi-Fi를 통한 네트워크 액세스 차단:*

> [!div class="mx-imgBorder"]
> ![네트워크 위협에 따른 WiFi 액세스 차단을 보여 주는 이미지](./media/lookout-mobile-threat-defense-connector/network-wifi-blocked.png)

*수정 시 액세스 권한 부여됨:*

> [!div class="mx-imgBorder"]
> ![수정 후 액세스를 허용하는 조건부 액세스의 개념 이미지](./media/lookout-mobile-threat-defense-connector/network-wifi-unblocked.png)

### <a name="control-access-to-sharepoint-online-based-on-threat-to-network"></a>네트워크 위협에 따라 SharePoint Online에 대한 액세스 제어

메시지 가로채기(man-in-the-middle) 공격 같은 네트워크에 대한 위협을 감지하여, 디바이스 위험에 따라 회사 파일 동기화를 금지합니다.

*네트워크 위협이 감지할 경우 SharePoint Online 차단:*

> [!div class="mx-imgBorder"]
> ![SharePoint Online에 대한 액세스 차단의 개념 이미지](./media/lookout-mobile-threat-defense-connector/network-spo-blocked.png)

*수정 시 액세스 권한 부여됨:*

> [!div class="mx-imgBorder"]
> ![네트워크 위협이 해결된 후 액세스를 허용하는 개념 이미지](./media/lookout-mobile-threat-defense-connector/network-spo-unblocked.png)

### <a name="control-access-on-unenrolled-devices-based-on-threats-from-malicious-apps"></a>악성 앱의 위협에 따라 등록되지 않은 디바이스에서 액세스 제어

Lookout Mobile Threat Defense 솔루션에서 디바이스가 감염된 것으로 간주하는 경우:
> [!div class="mx-imgBorder"]
> ![검색된 맬웨어로 인한 앱 보호 정책 차단](./media/lookout-mobile-threat-defense-connector/lookout-app-policy-block.png)

수정 시 액세스 권한 부여됨.

> [!div class="mx-imgBorder"]
> ![앱 보호 정책에 대한 수정 시 액세스 권한 부여됨](./media/lookout-mobile-threat-defense-connector/lookout-app-policy-remediated.png)

## <a name="next-steps"></a>다음 단계

이 솔루션을 구현하기 위해 수행해야 하는 주요 단계는 다음과 같습니다.

- [Lookout 통합 설정](lookout-mtd-connector-integration.md)
- [Intune에서 Mobile Endpoint Security를 사용하도록 설정](mtd-connector-enable.md)
- [Lookout for Work 앱 추가 및 할당](mtd-apps-ios-app-configuration-policy-add-assign.md)
- [Lookout 디바이스 준수 정책 구성](mtd-device-compliance-policy-create.md)
- [MTD 앱 보호 정책 만들기](mtd-app-protection-policy.md)