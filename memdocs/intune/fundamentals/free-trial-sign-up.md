---
title: 빠른 시작 - Microsoft Intune 평가판 체험
titleSuffix: ''
description: 이 빠른 시작에서는 평가판 구독을 만들고, 지원되는 구성 및 네트워킹 요구 사항을 이해하고, 필요에 따라 도메인 이름을 구성해 보겠습니다.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/16/2020
ms.topic: quickstart
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 195931c0-8208-43bd-b0af-b1f8e469a32c
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 83107121b05b2126e4c6b2b377baf57ee069f917
ms.sourcegitcommit: 3d895be2844bda2177c2c85dc2f09612a1be5490
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79343988"
---
# <a name="quickstart-try-microsoft-intune-for-free"></a>빠른 시작: Microsoft Intune 평가판 체험

Microsoft Intune을 사용하면 디바이스 및 앱을 관리하여 직원의 회사 데이터를 보호할 수 있습니다. 이 빠른 시작에서는 평가판 구독을 만들고 테스트 환경에서 Intune을 사용해 봅니다.

Intune은 Microsoft Endpoint Manager 관리 센터를 통해 관리되는 안전한 클라우드 기반 서비스에서 MDM(모바일 장치 관리) 및 MAM(모바일 응용 프로그램 관리)을 제공합니다. Intune을 사용하면 직원의 회사 리소스(데이터, 디바이스 및 앱)가 올바르게 구성, 액세스 및 업데이트되고 회사의 준수 정책 및 요구 사항을 충족합니다.

## <a name="prerequisites"></a>전제 조건
Microsoft Intune을 설정하기 전에, 다음 요구 사항을 검토하세요.

- [지원되는 운영 체제 및 브라우저](supported-devices-browsers.md)
- [네트워크 구성 요구 사항 및 대역폭](network-bandwidth-use.md)

## <a name="sign-up-for-a-microsoft-intune-free-trial"></a>Microsoft Intune 무료 평가판 등록

Intune 평가판은 30일 동안 무료로 사용할 수 있습니다. 회사 또는 학교 계정이 이미 있는 경우 해당 계정으로 **로그인**하고 구독에 Intune을 추가합니다. 그렇지 않은 경우 조직에서 Intune을 사용하기 위한 새 계정을 **등록**해야 합니다.

> [!IMPORTANT]
> 새 계정을 등록한 후에는 기존 회사 또는 학교 계정을 결합할 수 없습니다.

1. [Microsoft Intune 평가판](https://go.microsoft.com/fwlink/?linkid=2019088) 페이지로 이동하여 양식을 작성합니다.

    ![Microsoft Intune 평가판 계정 등록 웹 페이지의 스크린샷](./media/free-trial-sign-up/account-sign-up-site-full-browser.png)

    대부분의 IT 작업 및 사용자가 여러분과 다른 로캘에 있는 경우 **국가 또는 지역**에서 해당 로캘을 선택할 수 있습니다. Azure는 지역 정보를 사용하여 적절한 서비스를 제공합니다. 이 설정은 나중에 변경할 수 없습니다.

2. 회사 이름 뒤에 **.onmicrosoft.com**을 붙여서 계정을 만듭니다. 

    ![Intune 평가판 계정 새 자격 증명 프로세스 스크린샷](./media/free-trial-sign-up/account-sign-up-site-user-id.png)

    **.onmicrosoft.com** 없이 사용할 조직의 고유한 사용자 지정 도메인이 있는 경우 이 문서의 뒷부분에 설명된 Microsoft 365 관리 센터에서 변경할 수 있습니다.

3. 등록 프로세스가 끝나면 새 계정 정보를 확인합니다.

    ![계정 정보 이미지](./media/free-trial-sign-up/intune-end-of-sign-up-process.png) 

## <a name="sign-in-to-intune-in-the-microsoft-endpoint-manager"></a>Microsoft Endpoint Manager의 Intune에 로그인

아직 포털에 로그인하지 않았다면 다음 단계를 완료하세요.

1. 새 브라우저 창을 열고 주소 표시줄에 **https://devicemanagement.microsoft.com** 을 입력합니다. 
2. 위 단계에서 제공된 사용자 ID를 사용하여 로그인합니다( *yourID@yourdomain* .onmicrosoft.com).

    ![포털 로그인 페이지의 이미지](./media/free-trial-sign-up/azure-portal-signin.png)

평가판에 등록하는 경우 등록 과정 중에 입력한 이메일 주소로 계정 정보가 포함된 이메일 메시지가 전송됩니다. 이 전자 메일을 통해 평가판이 활성화된 것을 확인합니다.

> [!TIP]
> Microsoft Endpoint Manager를 사용하는 경우 비공개 모드가 아닌 일반 모드에서 브라우저를 사용하면 더 나은 결과를 얻을 수 있습니다.

## <a name="confirm-the-mdm-authority-in-intune"></a>Intune에서 MDM 기관 확인

기본적으로 무료 평가판을 만들 때 MDM 기관이 설정됩니다. 다음 단계를 사용하면 MDM 기관이 설정되었는지 확인할 수 있습니다.

1. 아직 로그인하지 않았다면 Microsoft Endpoint Manager에 로그인합니다.
2. **테넌트 관리**를 클릭합니다.
3. 테넌트 세부 정보를 확인합니다. **MDM 기관**이 **Microsoft Intune**으로 설정되어야 합니다.

Microsoft Endpoint Manager에 로그인한 후 MDM 기관이 설정되지 않았다고 표시하는 주황색 배너가 보이면 지금 활성화시킬 수 있습니다. MDM(모바일 디바이스 관리) 기관 설정에 따라 디바이스를 관리하는 방법이 결정됩니다. 사용자가 관리를 위해 디바이스를 등록하려면 먼저 MDM 권한을 설정해야 합니다.

### <a name="to-set-the-mdm-authority-to-intune-follow-these-steps"></a>MDM 기관을 Intune으로 설정하려면 다음 단계를 수행합니다.

1. 새 브라우저 창을 열고 주소 표시줄에 **https://portal.azure.com** 을 입력합니다. 
2. **모든 서비스** > **Microsoft Intune**을 선택합니다.
3. 디바이스 관리를 사용하도록 설정하지 않았음을 나타내는 배너를 선택하거나, 배너가 즉시 표시되지 않으면 **디바이스 등록**을 선택합니다. 아직 디바이스 관리를 사용하도록 설정하지 않은 경우 **MDM 기관 선택** 블레이드가 표시됩니다.

    > [!NOTE]
    > MDM 기관을 설정한 경우 **디바이스 등록** 블레이드에 MDM 기관 값이 표시됩니다. 주황색 배너는 MDM 기관을 아직 설정하지 않은 경우만 표시됩니다. 

    ![MDM 기관 선택 블레이드의 이미지](./media/free-trial-sign-up/choose-mdm-authority.png) 

4. MDM 기관을 설정하지 않으면 **MDM 기관 선택** 아래에서 MDM 기관을 **Intune MDM 기관**으로 설정합니다.

MDM 기관에 대한 자세한 내용은 [모바일 디바이스 관리 권한 설정](mdm-authority-set.md)을 참조하세요.

## <a name="configure-your-custom-domain-name-optional"></a>사용자 지정 도메인 이름 구성(선택 사항)

위에서 언급했듯이, **.onmicrosoft.com** 없이 사용하고 싶은 조직의 고유한 사용자 지정 도메인이 있는 경우 Microsoft 365 관리 센터에서 변경할 수 있습니다. 다음 단계를 사용하여 사용자 지정 도메인 이름을 추가하고, 확인하고, 구성할 수 있습니다.  

> [!IMPORTANT]
> 도메인 이름의 *초기* **onmicrosoft.com** 부분을 변경하거나 제거할 수 없습니다. 하지만 비즈니스 ID가 명확히 유지되도록 Intune에서 사용된 *사용자 지정* 도메인 이름을 추가하거나, 확인하거나, 제거할 수 있습니다. 자세한 내용은 [사용자 지정 도메인 이름 구성](custom-domain-name-configure.md)을 참조하세요.

1. [Microsoft 365 관리 센터](https://admin.microsoft.com)로 이동하고, 관리자 계정을 사용하여 로그인합니다.

2. 탐색 창에서 **설치** > **도메인** > **도메인 추가**를 선택합니다.

3. 사용자 지정 도메인 이름을 입력합니다. **다음**을 선택합니다.

   ![Microsoft 365 관리 센터 - 도메인 추가 스크린샷](./media/free-trial-sign-up/domain-custom-add.png)

4. 이전 단계에서 입력한 도메인의 소유자인지 확인합니다. 
    
    **이메일을 통해 코드 전송**을 선택하면 도메인의 등록된 연락처로 이메일이 전송됩니다. 이메일을 받은 후, 코드를 복사하여 **여기에 확인 코드 입력** 필드에 입력합니다. 확인 코드가 일치하면 도메인이 테넌트에 추가됩니다. 익숙하지 않은 이메일이 표시될 수 있습니다. 일부 등록 기관에서는 실제 이메일 주소를 숨깁니다. 이메일 주소는 도메인 등록 시 입력된 것과 다를 수도 있습니다.

   ![Microsoft 365 관리 센터 - 도메인 확인 스크린샷](./media/free-trial-sign-up/domain-custom-verify.png)

   > [!NOTE]
   > TXT 레코드 확인 세부 정보는 [Office 365에 대한 DNS 호스팅 공급자에서 DNS 레코드 만들기](https://support.office.com/article/Create-DNS-records-at-any-DNS-hosting-provider-for-Office-365-7B7B075D-79F9-4E37-8A9E-FB60C1D95166)를 참조하세요.

## <a name="admin-experiences"></a>관리자 환경

가장 자주 사용하게 될 포털이 두 개 있습니다.
- Microsoft Endpoint Manager 관리 센터([https://devicemanagement.microsoft.com/](https://devicemanagement.microsoft.com/))에서 [Intune의 기능](what-is-intune.md)을 탐색할 수 있습니다. 관리자는 여기서 Intune 작업을 합니다.
- Azure Active Directory를 사용하지 않는 경우 Microsoft 365 관리 센터([https://admin.microsoft.com](https://admin.microsoft.com))에서 사용자를 추가하고 관리할 수 있습니다. 또한 대금 청구 및 지원을 포함하여 계정의 다른 측면을 관리할 수 있습니다.

## <a name="next-steps"></a>다음 단계

이 빠른 시작에서는 테스트 환경에서 Intune을 사용해 볼 수 있는 평가판 구독을 만들었습니다. Intune 설정에 대한 자세한 내용은 [Intune 설정](setup-steps.md)을 참조하세요.

다음 Intune 빠른 시작을 진행하기 위해서는 아래 빠른 시작 링크를 클릭하세요.

> [!div class="nextstepaction"]
> [빠른 시작: 사용자를 만들고 라이선스 할당](quickstart-create-user.md)
