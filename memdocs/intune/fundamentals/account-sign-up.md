---
title: Microsoft Intune에 등록 또는 로그인
description: Microsoft Intune 구독에 등록하거나 로그인하여 구독을 시작하는 방법입니다.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 01/02/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 0f3ce07a-b718-42a9-bace-f99a8b8abd94
ms.reviewer: angerobe
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: ad73f89ff4dccd3151bd3123cd4bb54483aaae30
ms.sourcegitcommit: 3d895be2844bda2177c2c85dc2f09612a1be5490
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79363176"
---
# <a name="sign-up-or-sign-in-to-microsoft-intune"></a>Microsoft Intune에 등록 또는 로그인

이 항목에서는 시스템 관리자가 Intune 계정을 등록하는 방법을 알려줍니다.

Intune에 등록하기 전에 Microsoft Online Services 계정, 기업계약 또는 동등한 볼륨 라이선싱 계약이 이미 있는지 확인합니다. Microsoft 볼륨 라이선싱 계약 또는 Office 365 같은 다른 Microsoft 클라우드 서비스 구독에는 일반적으로 회사 또는 학교 계정이 포함되어 있습니다.

회사 또는 학교 계정이 이미 있는 경우 해당 계정으로 **로그인**하고 구독에 Intune을 추가합니다. 그렇지 않은 경우 조직에서 Intune을 사용하기 위한 새 계정을 **등록**해야 합니다.

>[!WARNING]
>새 계정을 등록한 후에는 기존 회사 또는 학교 계정을 결합할 수 없습니다.

## <a name="how-to-sign-up-for-intune"></a>Intune에 등록하는 방법

1. [Intune 등록 페이지](https://admin.microsoft.com/Signup/Signup.aspx?OfferId=40BE278A-DFD1-470a-9EF7-9F2596EA7FF9&dl=INTUNE_A&ali=1#0%20)를 방문합니다.

   ![Microsoft Intune 평가판 계정 등록 웹 페이지의 스크린샷](./media/account-sign-up/account-sign-up-site.png)

2. 등록 페이지에서 로그인 또는 등록하여 Intune의 새로운 구독을 관리합니다.

## <a name="post-sign-up-considerations"></a>등록 후 고려 사항

새 구독을 등록하면 등록 과정 중에 제공한 메일 주소로 계정 정보가 포함된 메일 메시지를 받게 됩니다. 이 전자 메일을 통해 구독이 활성화된 것을 확인합니다.

등록 과정을 완료하면 사용자를 추가하고 사용자에게 라이선스를 할당하는 데 사용되는 Microsoft 365 관리 센터로 이동됩니다. 기본 onmicrosoft.com 도메인 이름을 사용하는 클라우드 기반 계정만 사용하려면, 그대로 진행하여 이 곳에서 사용자를 추가하고 라이선스를 할당할 수 있습니다. 하지만, 조직의 [사용자 지정 도메인 이름](custom-domain-name-configure.md)을 사용하거나 온-프레미스 Active Directory의 [사용자 계정 정보를 동기화](users-add.md#sync-active-directory-and-add-users-to-intune)하려는 경우 브라우저 창을 닫을 수 있습니다.

## <a name="sign-in-to-microsoft-intune"></a>Microsoft Intune에 로그인

Intune에 등록한 후에는 [지원 브라우저](supported-devices-browsers.md#intune-supported-web-browsers)에서 디바이스를 사용하여 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)에 로그인한 후 서비스를 등록할 수 있습니다.

기본적으로 계정에 Azure AD의 다음 사용 권한 중 하나가 있어야 합니다.

- 전역 관리자
- Intune 서비스 관리자(Intune 관리자라고도 함)

다른 권한을 가진 사용자에 대해 서비스를 관리할 수 있는 액세스 권한을 부여하려면 [역할 기반 액세스 제어](role-based-access-control.md)를 참조하세요.

### <a name="intune-admin-portal-url"></a>Intune 관리 포털 URL

Microsoft 365 관리 센터: https://devicemanagement.microsoft.com

Intune Azure Portal: https://portal.azure.com/#blade/Microsoft_Intune_DeviceSettings/ExtensionLandingBlade

교육용 Intune: https://intuneeducation.portal.azure.com

Intune 클래식 포털: https://manage.microsoft.com Intune 클래식 포털은 Intune PC 소프트웨어 클라이언트에 등록된 디바이스를 관리하는 데만 사용됩니다.

### <a name="urls-for-intune-services-provided-by-office-365"></a>Office 365에서 제공하는 Intune 서비스의 URL

Microsoft 365 Business: https://portal.microsoft.com/adminportal

Office 365 모바일 디바이스 관리: https://portal.office.com/adminportal/home#/MifoDevices

## <a name="see-also"></a>참고 항목

[Office 365, Azure 또는 Intune에 로그인 할 수 없음](https://support.microsoft.com/help/2412085)
