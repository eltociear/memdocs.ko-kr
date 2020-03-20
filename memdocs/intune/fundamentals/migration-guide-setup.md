---
title: Microsoft Intune 기본 설정
description: 이 문서는 Microsoft Intune을 설정하는 데 필요한 단계를 제공합니다.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 03/04/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 60cfa440-0723-4ea0-bacf-3c5d26f9a1d3
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: 3b7784d4ad86e3418259f85ca1c4577d2289dc86
ms.sourcegitcommit: 3d895be2844bda2177c2c85dc2f09612a1be5490
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79358158"
---
# <a name="basic-setup"></a>기본 설정

환경을 평가했으면 Microsoft Intune을 설정할 차례입니다.

## <a name="external-dependencies-for-an-intune-deployment"></a>Intune 배포에 대한 외부 종속성

### <a name="identity"></a>ID

Intune은 ID 및 사용자 그룹화 공급자로 AAD(Azure Active Directory)가 필요합니다. 다음에 대해 자세히 알아보세요.

- [ID 요구 사항](https://docs.microsoft.com/azure/active-directory/active-directory-hybrid-identity-design-considerations-overview#design-considerations-overview)

- [디렉터리 동기화 요구 사항](https://docs.microsoft.com/azure/active-directory/active-directory-hybrid-identity-design-considerations-directory-sync-requirements)

- [MFA(다단계 인증)](https://docs.microsoft.com/azure/active-directory/authentication/concept-mfa-howitworks)

- [사용자 및 디바이스 그룹 계획](users-add.md)

- [사용자 및 디바이스 그룹을 만드는 방법](groups-get-started.md)

조직이 이미 Office 365를 사용하고 있는 경우 Intune에서 동일한 Azure Active Directory 환경을 사용해야 합니다.

### <a name="pki-optional"></a>PKI(선택 사항)

Intune에서 VPN, Wi-Fi 또는 메일 프로필에 인증서 기반 인증을 사용할 계획인 경우 지원되는 [PKI 인프라를 구축](../protect/certificates-configure.md)하고, 인증서 프로필을 만들어 배포할 준비가 되었는지 확인해야 합니다. Intune에서 인증서를 구성하는 방법에 대해 자세히 알아보세요.

- [SCEP 인증서 인프라 구성 방법](/intune/certificates-scep-configure)

- [PFX 인증서 인프라 구성](/intune/certficates-pfx-configure)

## <a name="task-list-for-an-intune-setup"></a>Intune 설정에 대한 작업 목록

### <a name="task-1-intune-subscription"></a>태스크 1: Intune 구독

Intune으로 마이그레이션하려면 먼저, [Intune 구독](account-sign-up.md)이 필요합니다.

### <a name="task-2-assign-intune-user-licenses"></a>태스크 2: Intune 사용자 라이선스 할당

- [Intune 사용자 라이선스를 할당하는 방법](licenses-assign.md)에 대해 알아보세요.

- 새 Azure Active Directory 테넌트를 만든 경우 [새 사용자를 생성하거나 온-프레미스 AD(Active Directory)에서 사용자를 동기화하는 방법](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect)에 대해 알아보세요.

### <a name="task-3-set-your-mdm-authority-to-intune"></a>태스크 3: MDM 기관을 Intune으로 설정

Intune은 [Microsoft Endpoint Manager 관리 센터](https://go.microsoft.com/fwlink/?linkid=2109431)를 사용하여 관리하는 것이 좋습니다.

MDM 기관을 **Intune**으로 설정하세요. 다른 MDM 기관을 사용하면 Intune에서 MDM 관리를 대체 Microsoft 관리 콘솔로 전송할 수 있습니다. 이러한 경우는 일반적이지 않습니다.

> [!IMPORTANT]
> 모바일 디바이스 관리를 Intune에 처음으로 전송할 경우 MDM 기관을 Intune으로 설정해야 합니다.

[모바일 관리 기관을 설정하는 방법](mdm-authority-set.md)에 대해 알아보세요.

## <a name="next-step"></a>다음 단계

[디바이스 및 앱 관리 정책](migration-guide-configure-policies.md)을 구성합니다.
