---
title: Intune과 Better Mobile Threat Defense 커넥터 사용
titleSuffix: Intune on Azure
description: Intune과 Better Mobile Threat Defense 커넥터를 설정합니다.
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
ms.assetid: ''
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: 05dec05cdc5a16078328d736d2f622cea1b2aa00
ms.sourcegitcommit: 3d895be2844bda2177c2c85dc2f09612a1be5490
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79353985"
---
# <a name="better-mobile-threat-defense-connector-with-intune"></a>Intune과 Better Mobile Threat Defense 커넥터 사용

Microsoft Intune과 통합된 MTD(Mobile Threat Defense) 솔루션인 Better Mobile에서 수행된 위험 평가에 따라 조건부 액세스를 사용하여 모바일 디바이스에서 회사 리소스에 대한 액세스를 제어할 수 있습니다. 위험은 Better Mobile 앱을 실행하는 디바이스에서 수집된 원격 분석에 기반하여 평가됩니다.

등록된 디바이스의 Intune 디바이스 준수 정책을 통해 사용하도록 설정된 Better Mobile 위험 평가에 따라 조건부 액세스 정책을 구성할 수 있습니다. 이 정책을 사용하여 회사 리소스에 액세스하는 비규격 디바이스를 감지된 위협에 따라 허용하거나 차단할 수 있습니다. 등록이 취소된 디바이스의 경우 앱 보호 정책을 사용하여 검색된 위협에 따라 차단 또는 선택적 초기화를 적용할 수 있습니다.

## <a name="how-do-intune-and-better-mobile-help-protect-your-company-resources"></a>Intune과 Better Mobile이 회사 리소스를 보호하는 데 어떤 도움이 되나요?

Better Mobile 모바일 앱은 모바일 디바이스에서 설치되어 실행됩니다. 이 앱은 파일 시스템, 네트워크 스택, 디바이스 및 앱 원격 분석(사용 가능한 경우)을 캡처한 다음, Better Mobile 클라우드 서비스로 보내 모바일 위협에 대한 디바이스의 위험을 평가합니다.

- **등록된 디바이스 지원** - Intune 디바이스 준수 정책에는 Better Mobile의 위험 평가 정보를 사용할 수 있는 MTD(Mobile Threat Defense) 규칙이 포함되어 있습니다. MTD 규칙을 사용하도록 설정하면 Intune은 사용하도록 설정된 정책을 디바이스가 준수하는지 평가합니다. 디바이스가 정책을 준수하지 않으면 Exchange Online, SharePoint Online 등의 회사 리소스에 대한 사용자의 액세스가 차단됩니다. 또한 사용자는 디바이스에 설치된 Better Mobile 앱에서 지침을 받아 문제를 해결하고 회사 리소스에 대한 액세스 권한을 다시 얻을 수 있습니다. 등록된 장치에서 Better Mobile 사용을 지원하려면 다음을 수행합니다.
  - [디바이스에 MTD 앱 추가](../protect/mtd-apps-ios-app-configuration-policy-add-assign.md)
  - [MTD를 지원하는 디바이스 준수 정책 만들기](../protect/mtd-device-compliance-policy-create.md)
  - [Intune에서 MTD 커넥터 사용](../protect/mtd-connector-enable.md)

- **등록되지 않은 디바이스 지원** - Intune 앱 보호 정책을 사용하면 Intune이 등록되지 않은 디바이스에서 Better Mobile의 위험 평가 데이터를 사용할 수 있습니다. 관리자는 이 조합을 사용하여 [Microsoft Intune 보호 앱](../apps/apps-supported-intune-apps.md) 내에서 회사 데이터를 보호하고 이러한 등록되지 않은 디바이스에서 회사 데이터를 차단하거나 선택적으로 초기화할 수 있습니다. 등록되지 않은 장치에서 Better Mobile 사용을 지원하려면 다음을 수행합니다.
  - [등록되지 않은 디바이스에 MTD 앱 추가](../protect/mtd-add-apps-unenrolled-devices.md)
  - [Mobile Threat Defense 앱 보호 정책 만들기](../protect/mtd-app-protection-policy.md)
  - [Intune에서 등록되지 않은 디바이스에 MTD 커넥터를 사용하도록 설정](../protect/mtd-enable-unenrolled-devices.md)

## <a name="supported-platforms"></a>지원되는 플랫폼

- **Android 4.1 이상**

- **iOS 8.0 이상**

## <a name="prerequisites"></a>전제 조건

- Azure Active Directory Premium

- Microsoft Intune 구독

- Better Mobile Threat Defense 구독

  - 자세한 내용은 [Better Mobile 웹 사이트](https://www.better.mobi/)를 참조하세요.

## <a name="sample-scenarios"></a>샘플 시나리오:

다음은 몇 가지 일반적인 시나리오입니다.

### <a name="control-access-based-on-threats-from-malicious-apps"></a>악성 앱의 위협에 따라 액세스 제어

맬웨어와 같은 악성 앱이 디바이스에서 감지되면 위협이 해결될 때까지 디바이스에서 다음 작업을 차단할 수 있습니다.

- 회사 메일에 연결

- 작업용 OneDrive 앱과 회사 파일 동기화

- 회사 앱에 액세스

악성 앱이 발견되면 액세스 차단:

![감지된 악성 앱을 보여주는 이미지](./media/better-mobile-threat-defense-connector/better-mobile-maliciousapps-blocked.png)

수정 시 액세스 권한 부여됨:

![감지된 악성 앱에 액세스 권한 부여됨](./media/better-mobile-threat-defense-connector/better-mobile-maliciousapps-unblocked.png)

### <a name="control-access-based-on-threat-to-network"></a>네트워크에 대한 위협에 따라 액세스 제어

**메시지 가로채기(man-in-the-middle)** 공격과 같은 사용자 네트워크 위협을 검색하고 디바이스 위험에 따라 Wi-Fi 네트워크에 대한 액세스를 보호합니다.

Wi-Fi를 통한 네트워크 액세스 차단:

![Wi-Fi를 통한 네트워크 액세스 차단](./media/better-mobile-threat-defense-connector/better-mobile-network-wifi-blocked.png)

수정 시 액세스 권한 부여됨:

![수정 시 부여된 액세스 권한을 보여주는 이미지](./media/better-mobile-threat-defense-connector/better-mobile-network-wifi-unblocked.png)

### <a name="control-access-to-sharepoint-online-based-on-threat-to-network"></a>네트워크 위협에 따라 SharePoint Online에 대한 액세스 제어

**메시지 가로채기(man-in-the-middle)** 공격 같은 네트워크에 대한 위협을 감지하여, 디바이스 위험에 따라 회사 파일 동기화를 금지합니다.

네트워크 위협이 감지되면 SharePoint Online 차단:

![네트워크 위협이 감지되면 SharePoint Online 차단](./media/better-mobile-threat-defense-connector/better-mobile-network-spo-blocked.png)

해결 시 액세스 허용:

![SharePoint에 대해 수정 시 액세스 권한이 부여된 예](./media/better-mobile-threat-defense-connector/better-mobile-network-spo-unblocked.png)

### <a name="control--access-on-unenrolled-devices-based-on-threats-from-malicious-apps"></a>악성 앱의 위협에 따라 등록되지 않은 디바이스에서 액세스 제어

BETTER Mobile Threat Defense 솔루션에서 디바이스가 감염된 것으로 간주하는 경우: ![감지된 맬웨어로 인한 앱 보호 정책 차단](./media/better-mobile-threat-defense-connector/better-mobile-app-policy-block.png)

수정 시 액세스 권한 부여됨:

![앱 보호 정책에 대한 수정 시 액세스 권한 부여됨](./media/better-mobile-threat-defense-connector/better-mobile-app-policy-remediated.png)

## <a name="next-steps"></a>다음 단계

- [Intune과 Better Mobile 통합](better-mobile-mtd-connector-integration.md)

- [Better Mobile 앱 설정](mtd-apps-ios-app-configuration-policy-add-assign.md)

- [Better Mobile 디바이스 준수 정책 만들기](mtd-device-compliance-policy-create.md)

- [Better Mobile MTD 커넥터 사용 설정](mtd-connector-enable.md)

- [MTD 앱 보호 정책 만들기](mtd-app-protection-policy.md) 
