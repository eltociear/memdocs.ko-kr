---
title: Microsoft Intune - Azure와 네트워크 액세스 제어 통합 | Microsoft Docs
description: NAC(네트워크 액세스 제어) 솔루션은 Intune을 사용하여 디바이스에 대한 준수 및 등록을 확인합니다. NAC는 조건부 액세스를 사용한 특정 동작 및 작업을 포함합니다. 등록된 단계를 참조하고 파트너 솔루션 목록을 가져옵니다.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 02/18/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: aa7ecff7-8579-4009-8fd6-e17074df67de
ms.reviewer: tycast
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: e1fe46894a9905cba4267e8ff9baa949dde5709a
ms.sourcegitcommit: 3d895be2844bda2177c2c85dc2f09612a1be5490
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79351489"
---
# <a name="network-access-control-nac-integration-with-intune"></a>Intune과 NAC(네트워크 액세스 제어) 통합

Intune은 디바이스가 온-프레미스 리소스에 액세스하려고 할 때 조직이 회사 데이터를 보호할 수 있도록 네트워크 액세스 제어 파트너와 통합됩니다.

>[!IMPORTANT]
> NAC는 현재 Android 엔터프라이즈 완전 관리형 또는 Android 엔터프라이즈 전용 디바이스를 지원하지 않습니다.

## <a name="how-do-intune-and-nac-solutions-help-protect-your-organization-resources"></a>Intune 및 NAC 솔루션은 조직 리소스를 어떻게 보호하나요?

NAC 솔루션은 액세스 제어 결정을 내리기 위해 Intune에서 디바이스 등록 및 규정 준수 상태를 확인합니다. 디바이스가 등록되지 않았거나 등록되었으나 Intune 디바이스 준수 정책을 준수하지 않을 경우 등록 또는 디바이스 준수 확인을 위해 Intune에 리디렉션되어야 합니다.

### <a name="example"></a>예제

디바이스가 등록되었으며 Intune 규격인 경우 NAC 솔루션에서 회사 리소스에 대한 디바이스 액세스를 허용해야 합니다. 예를 들어 사용자가 회사 Wi-Fi 또는 VPN 리소스에 액세스하려고 할 때 액세스가 허용되거나 거부될 수 있습니다.

## <a name="feature-behaviors"></a>기능 동작

Intune에 능동적으로 동기화하는 디바이스는 **준수** / **비준수**에서 **동기화되지 않음**(또는 **알 수 없음**)으로 이동할 수 없습니다. **알 수 없음** 상태는 아직 준수 여부가 평가되지 않은 새로 등록된 디바이스에 예약되었습니다.

리소스에 대한 액세스가 차단된 디바이스의 경우, 차단 서비스가 모든 사용자를 [관리 포털](https://portal.manage.microsoft.com)로 리디렉션하여 디바이스가 차단된 이유를 확인할 수 있도록 해야 합니다.  사용자가 이 페이지를 방문하면 해당 디바이스의 준수 여부가 동기적으로 재평가됩니다.

## <a name="nac-and-conditional-access"></a>NAC 및 조건부 액세스

NAC는 조건부 액세스와 연동하여 액세스 제어 결정을 제공합니다. 자세한 내용은 [Intune에서 조건부 액세스를 사용하는 일반적인 방법](conditional-access-intune-common-ways-use.md)을 참조하세요.

## <a name="how-the-nac-integration-works"></a>NAC 통합의 작동 방식

다음 목록은 Intune과 통합된 경우 NAC 통합의 작동 방식에 대한 개요입니다. 처음 세 단계인 1-3단계에서는 온보딩 프로세스에 대해 설명합니다. NAC 솔루션이 Intune과 통합된 후 4-9단계에서는 지속적인 작업을 설명합니다.

![Intune과 NAC 작동 방식의 개념 이미지](./media/network-access-control-integrate/ca-intune-common-ways-2.png)

1. NAC 파트너 솔루션을 AAD(Azure Active Directory)에 등록하고 Intune NAC API에 위임된 사용 권한을 부여합니다.
2. Intune 검색 URL을 포함한 적절한 설정으로 NAC 파트너 솔루션을 구성합니다.
3. 인증서 인증을 위해 NAC 파트너 솔루션을 구성합니다.
4. 사용자가 회사 Wi-Fi 액세스 지점에 연결하거나 VPN 연결 요청을 수행합니다.
5. NAC 파트너 솔루션이 디바이스 정보를 Intune에 전달하고 디바이스 등록 및 준수 상태를 Intune에 요청합니다.
6. 디바이스가 규격이 아니거나 등록되지 않은 경우 NAC 파트너 솔루션이 사용자에게 등록하거나 디바이스 준수를 수정하도록 알립니다.
7. 해당하는 경우 디바이스가 규정 준수 및 등록 상태를 재확인하려고 합니다.
8. 디바이스가 등록되고 규격이면 NAC 파트너 솔루션이 Intune에서 상태를 가져옵니다.
9. 성공적으로 연결되어 디바이스가 회사 리소스에 액세스할 수 있게 됩니다.

## <a name="use-nac-for-vpn-on-your-iosipados-devices"></a>iOS/iPadOS 디바이스에서 VPN에 NAC 사용  

NAC는 VPN 프로필에서 NAC를 사용하도록 설정하지 않고도 다음 VPN에서 사용할 수 있습니다.

  - Cisco Legacy AnyConnect용 NAC
  - F5 Access Legacy
  - Citrix VPN

NAC는 Cisco AnyConnect, Citrix SSO 및 F5 액세스에도 지원됩니다. 

### <a name="to-enable-nac-for-cisco-anyconnect-for-ios"></a>iOS용 Cisco AnyConnect에 대해 NAC를 사용하도록 설정하려면:

  - 아래 링크에 설명된 대로 NAC를 위해 Intune에 ISE를 통합합니다.
  - VPN 프로필에서 **NAC(네트워크 액세스 제어) 사용** 설정을 **예**로 지정합니다.

### <a name="to-enable-nac-for-citrix-sso"></a>Citrix SSO에 대해 NAC을 사용하도록 설정하려면

  - Citrix Gateway 12.0.59 이상을 사용합니다.  
  - Citrix SSO 1.1.6 이상을 설치해야 합니다.
  - Citrix 제품 설명서에 설명된 대로 [NAC를 위해 Intune에 NetScaler를 통합](https://docs.citrix.com/en-us/netscaler-gateway/12/microsoft-intune-integration/configuring-network-access-control-device-check-for-netscaler-gateway-virtual-server-for-single-factor-authentication-deployment.html)합니다.
  - VPN 프로필에서 **기본 설정** > **NAC(네트워크 액세스 제어) 사용** > **동의**를 선택합니다.


### <a name="to-enable-nac-for-f5-access"></a>F5 Access에 대해 NAC을 사용하도록 설정하려면

  - F5 BIG-IP 13.1.1.5를 사용합니다. BIG-IP 14는 지원되지 않습니다.
  - BIG-IP와 NAC용 Intune을 통합하세요. [개요: 엔드포인트 관리 시스템을 사용하여 디바이스 상태 검사를 위한 APM 구성](https://support.f5.com/kb/en-us/products/big-ip_apm/manuals/product/apm-client-configuration-7-1-6/6.html#guid-0bd12e12-8107-40ec-979d-c44779a8cc89) F5 가이드에 단계가 나열됩니다.
  - VPN 프로필에서 **기본 설정** > **NAC(네트워크 액세스 제어) 사용** > **동의**를 선택합니다.

  보안상의 이유로 24시간마다 VPN 연결이 끊어집니다. VPN을 즉시 다시 연결할 수 있습니다.

Microsoft는 이러한 최신 클라이언트를 위한 NAC 솔루션을 출시하기 위해 파트너와 협업하고 있습니다. 솔루션이 준비되면 이 문서가 추가 정보를 통해 업데이트될 것입니다.

## <a name="next-steps"></a>다음 단계

- [Intune과 Cisco ISE 통합](https://www.cisco.com/c/en/us/td/docs/security/ise/2-1/admin_guide/b_ise_admin_guide_21/b_ise_admin_guide_20_chapter_01000.html)
- [Intune과 Citrix NetScaler 통합](https://docs.citrix.com/en-us/netscaler-gateway/12/microsoft-intune-integration/configuring-network-access-control-device-check-for-netscaler-gateway-virtual-server-for-single-factor-authentication-deployment.html)
- [Intune과 F5 BIG-IP Access Policy Manager 통합](https://support.f5.com/kb/en-us/products/big-ip_apm/manuals/product/apm-client-configuration-13-0-0/6.html)
- [Intune과 HP Aruba ClearPass 통합](https://support.arubanetworks.com/Documentation/tabid/77/DMXModule/512/Command/Core_Download/Default.aspx?EntryId=31271)
- [Intune을 사용한 Squadra 보안 이동식 미디어 관리자(secRMM) 통합](http://www.squadratechnologies.com/StaticContent/ProductDownload/secRMM/9.9.0.0/secRMMIntuneAccessControlSetupGuide.pdf)
