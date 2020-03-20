---
title: Microsoft Intune과 Zimperium MTD 통합
titleSuffix: Microsoft Intune
description: 회사 리소스에 대한 모바일 디바이스 액세스를 제어하기 위해 Microsoft Intune을 사용하여 Zimperium MTD(Mobile Threat Defense) 솔루션을 설정하는 방법입니다.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/21/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 363fd280-1865-4a61-855b-eb75c3c62753
ms.reviewer: davidra
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 5bb106e482beb7894c84f11d0994b43ba43eb302
ms.sourcegitcommit: 3d895be2844bda2177c2c85dc2f09612a1be5490
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79338385"
---
# <a name="integrate-zimperium-with-intune"></a>Intune 및 Zimperium 통합

Intune과 Zuneperium Mobile Threat Defense 솔루션을 통합하려면 다음 단계를 완료하세요.

## <a name="before-you-begin"></a>시작하기 전에

다음 단계는 [Zimperium MTD 콘솔](https://www.zimperium.com/platform)에서 완료되며, Intune 등록된 디바이스(디바이스 준수 사용)와 등록되지 않은 디바이스(앱 보호 정책 사용) 모두에 대해 Zimperium 서비스에 연결할 수 있습니다.

Intune과 Zimperium을 통합하는 과정을 시작하기 전에 다음의 구독과 자격 증명이 있는지 확인합니다.

- Microsoft Intune 구독

- 다음 권한을 부여할 Azure Active Directory 전역 관리자의 관리자 자격 증명:

  - 로그인 및 사용자 프로필 읽기

  - 로그인한 사용자로 디렉터리에 액세스

  - 디렉터리 데이터 읽기

  - Intune에 디바이스 정보 보내기

- Zimperium MTD 콘솔에 액세스하기 위한 관리자 자격 증명

### <a name="zimperium-app-authorization"></a>Zimperium 앱 권한 부여

Zimperium 앱 권한 부여 프로세스는 다음과 같습니다.

- Zimperium 서비스에 디바이스 상태와 관련된 정보를 Intune으로 다시 전달하기 위한 권한을 부여합니다. 이러한 권한을 부여하려면 전역 관리자 자격 증명을 사용해야 합니다. 권한 부여는 일회성 작업입니다. 권한이 부여된 후에는 일별 작업을 위해 전역 관리자 자격 증명이 필요하지 않습니다.

- Zimperium이 Azure Active Directory(AD) 등록 그룹 멤버 자격과 동기화하여 해당 디바이스의 데이터베이스를 채웁니다.

- Zimperium 관리 콘솔에서 Azure AD SSO(Single Sign-On)를 사용하도록 허용합니다.

- Zimperium 앱에서 Azure AD SSO를 사용하여 로그인하도록 허용합니다.

동의 및 Azure Active Directory 애플리케이션에 대한 자세한 내용은 Azure Active Directory 문서 ‘Azure Active Directory v2.0 엔드포인트의 권한 및 동의’에 나오는 [디렉터리 관리자로부터 권한 요청](https://docs.microsoft.com/azure/active-directory/develop/v2-permissions-and-consent#request-the-permissions-from-a-directory-admin)을 참조하세요. 


## <a name="to-set-up-zimperium-integration"></a>Zimperium 통합 설정

1. [Zimperium MTD 콘솔](https://www.zimperium.com/platform)로 이동하여 자격 증명으로 로그인합니다. Zimperium 통합 설정 프로세스를 수행하려면 전역 관리자 역할이 있는 Azure Active Directory 사용자 권한으로 로그인해야 합니다. 이 일회성 설정 작업은 전역 관리자 권한을 사용하여 조직에 Zimperium 앱으로 Intune과 통신할 수 있는 권한을 부여합니다. 

2. 왼쪽 메뉴에서 **관리**를 선택합니다.

3. **MDM 설정** 탭을 선택합니다.

4. **MDM 추가**를 선택한 다음 **MDM 공급자** 목록에서 **Microsoft Intune**을 선택합니다.

5. Microsoft Intune을 MDM 서비스로 설정하면 **Microsoft Intune 구성** 창이 팝업됩니다. 그러면 각 옵션에 대해 **Azure Active Directory 추가**를 선택합니다. **zIPS iOS 및 Android 앱**에 대해 **Azure Active Directory 추가**를 선택하여 Zimperium에 Azure AD Single Sign-On을 통해 Intune 및 Azure AD와 통신할 수 있는 권한을 부여합니다.

    > [!IMPORTANT]  
    > Intune과의 통합 프로세스를 완료하려면 Zimperium zConsole, zIPS iOS 및 Android 앱을 추가해야 합니다.

6. **동의**를 선택하여 Intune 및 Azure Active Directory와 통신할 수 있는 권한을 Zimperium 앱에 부여합니다.

7. Azure AD에 **Zimperium zConsole** 및 **zIPS iOS 및 Android** 앱을 추가한 후 Azure AD 보안 그룹을 추가합니다. 그럼으로써 Zimperium에서 Azure AD 보안 그룹과 해당 서비스를 동기화할 수 있습니다.

8. **마침**을 선택하여 구성을 저장하고 첫 번째 Azure AD 보안 그룹 동기화를 시작합니다.

9. Zimperium MTD 콘솔에서 로그아웃합니다.

## <a name="next-steps"></a>다음 단계

- [등록된 디바이스에 대해 Zimperium 앱 설정](mtd-apps-ios-app-configuration-policy-add-assign.md)
- [등록되지 않은 디바이스에 대해 Zimperium 앱 설정](mtd-add-apps-unenrolled-devices.md)
