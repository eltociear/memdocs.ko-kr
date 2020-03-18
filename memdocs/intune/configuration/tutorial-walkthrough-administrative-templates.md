---
title: 연습 - Microsoft Intune에서 관리 템플릿 만들기 - Azure | Microsoft Docs
description: 이 자습서 또는 연습에서는 Microsoft Intune을 사용하여 Windows 10 이상 디바이스에서 Office, Windows 및 Microsoft Edge ADMX 템플릿을 구성합니다.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 02/18/2020
ms.topic: tutorial
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: ''
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 936634a26dee315c7ad452ac408f9cc0eac00dfe
ms.sourcegitcommit: 3d895be2844bda2177c2c85dc2f09612a1be5490
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79343273"
---
# <a name="tutorial-use-the-cloud-to-configure-group-policy-on-windows-10-devices-with-admx-templates-and-microsoft-intune"></a>자습서: 클라우드를 사용해 ADMX 템플릿과 Microsoft Intune으로 Windows 10 디바이스에서 그룹 정책 구성

> [!NOTE]
> 이 자습서는 Microsoft Ignite를 위한 기술 워크샵으로 만들어졌습니다. Intune 및 온-프레미스에서 ADMX 정책을 사용 및 구성하는 것과 비교해볼 때 이 자습서에는 일반적인 자습서보다 많은 필수 구성 요소가 포함됩니다.

ADMX 템플릿이라고도 하는 그룹 정책 관리 템플릿에는 PC를 비롯하여 Windows 10 디바이스에서 구성할 수 있는 설정이 포함됩니다. ADMX 템플릿 설정은 다양한 서비스에서 사용할 수 있습니다. 해당 설정은 Microsoft Intune을 포함한 MDM(모바일 디바이스 관리) 공급자에서 사용됩니다. 예를 들어 PowerPoint에서 디자인 아이디어를 켜고, Microsoft Edge에서 홈페이지를 설정하고, Internet Explorer에서 ActiveX 컨트롤을 차단할 수 있습니다.

ADMX 템플릿은 다음 서비스에 사용할 수 있습니다.

- **Microsoft Edge**: [Microsoft Edge 정책 파일](https://www.microsoftedgeinsider.com/en-us/enterprise)에서 다운로드합니다.
- **Office**: [Office 365 ProPlus, Office 2019 및 Office 2016](https://www.microsoft.com/download/details.aspx?id=49030)에서 다운로드합니다.
- **Windows**: Windows 10 OS에 기본 제공됩니다.

ADMX 정책에 대한 자세한 내용은 [ADMX 지원 정책 이해](https://docs.microsoft.com/windows/client-management/mdm/understanding-admx-backed-policies)를 참조하세요.

Microsoft Intune에서 해당 템플릿은 Intune 서비스에 기본 제공되며 **관리 템플릿** 프로필로 사용할 수 있습니다. 이 프로필에서 포함하려는 설정을 구성한 다음, 이 프로필을 디바이스에 “할당”합니다.

이 자습서에서는 다음 작업을 수행하게 됩니다.

> [!div class="checklist"]
> * [Microsoft Endpoint Manager 관리 센터](https://go.microsoft.com/fwlink/?linkid=2109431)의 기본 개념을 알아봅니다.
> * 사용자 그룹을 만들고 디바이스 그룹을 만듭니다.
> * Intune의 설정을 온-프레미스 ADMX 설정과 비교합니다.
> * 다양한 관리 템플릿을 만들고 다양한 그룹을 대상으로 하는 설정을 구성합니다.

이 랩을 마치면 Intune 및 Microsoft 365를 사용하여 사용자를 관리하고 관리 템플릿을 배포하기 시작할 기술을 습득하게 됩니다.

이 기능은 다음에 적용됩니다.

- Windows 10 버전 1703 이상

## <a name="prerequisites"></a>전제 조건

- Intune 및 Azure AD(Active Directory) Premium을 포함하는 Microsoft 365 E3 또는 E5 구독. E3 또는 E5 구독이 없는 경우 [체험해 보세요](https://docs.microsoft.com/office365/admin/try-or-buy-microsoft-365?view=o365-worldwide).

  여러 가지 Microsoft 365 라이선스에서 제공되는 혜택에 대한 자세한 내용은 [Microsoft 365를 사용하여 엔터프라이즈 혁신](https://www.microsoft.com/microsoft-365/compare-all-microsoft-365-plans)을 참조하세요.

- Microsoft Intune은 **Intune MDM 기관**으로 구성됩니다. 자세한 내용은 [모바일 디바이스 관리 기관 설정](../fundamentals/mdm-authority-set.md)을 참조하세요.

  > [!div class="mx-imgBorder"]
  > ![테넌트 상태에서 MDM 기관을 Microsoft Intune으로 설정](./media/tutorial-walkthrough-administrative-templates/tenant-status.png)

- 온-프레미스 Active Directory DC(도메인 컨트롤러)에서:

  1. 다음 Office 및 Microsoft Edge 템플릿을 [중앙 저장소(SYSVOL 폴더)](https://support.microsoft.com/help/3087759/how-to-create-and-manage-the-central-store-for-group-policy-administra)에 복사합니다.

      - [Office 관리 템플릿](https://www.microsoft.com/download/details.aspx?id=49030)
      - [Microsoft Edge 관리 템플릿 > 정책 파일](https://www.microsoftedgeinsider.com/en-us/enterprise)

  2. DC와 동일한 도메인의 Windows 10 Enterprise 관리자 컴퓨터에 해당 템플릿을 푸시하는 그룹 정책을 만듭니다. 이 자습서의 내용

      - 해당 템플릿을 사용하여 만든 그룹 정책을 **OfficeandEdge**라고 합니다. 이미지에 이 이름이 표시됩니다.
      - 사용하는 Windows 10 Enterprise 관리자 컴퓨터를 **관리자 컴퓨터**라고 합니다.

      일부 조직에서 도메인 관리자는 두 가지 계정인 일반적인 도메인 회사 계정 및 그룹 정책과 같은 도메인 관리자 작업에만 사용되는 다른 도메인 관리자 계정을 사용합니다.

      **관리자 컴퓨터**는 관리자가 도메인 관리자 계정으로 로그인하고 그룹 정책 관리용으로 디자인된 도구에 액세스하는 데 사용됩니다.

- **관리자 컴퓨터**에서:

  - 도메인 관리자 계정으로 로그인합니다.

  - **RSAT: 그룹 정책 관리 도구**를 설치합니다.

    1. **설정** 앱 > **앱** > **선택적 기능** > **기능 추가**를 엽니다.
    2. **RSAT: 그룹 정책 관리 도구** > **설치**를 선택합니다.

        Windows에서 기능을 설치하는 동안 잠시 기다려 주세요. 완료되면 **Windows 관리 도구** 앱에 표시됩니다.

        > [!div class="mx-imgBorder"]
        > ![그룹 정책 관리 앱을 포함하는 Windows 관리 도구 앱](./media/tutorial-walkthrough-administrative-templates/windows-administrative-tools-app.png)

  - Endpoint Manager 관리 센터를 포함하는 Microsoft 365 구독에 대한 인터넷 액세스 및 관리자 권한이 있어야 합니다.

## <a name="open-the-endpoint-manager-admin-center"></a>Endpoint Manager 관리 센터 열기

1. Microsoft Edge 버전 77 이상과 같은 Chromium 웹 브라우저를 엽니다.
2. [Microsoft Endpoint Manager 관리 센터](https://go.microsoft.com/fwlink/?linkid=2109431)(https://devicemanagement.microsoft.com) )로 이동합니다. 다음 계정으로 로그인합니다.

    **사용자**: Microsoft 365 테넌트 구독의 관리자 계정을 입력합니다.  
    **암호**: 해당 암호를 입력합니다.

이 관리 센터는 디바이스 관리에 중점을 두며 Azure AD 및 Intune과 같은 Azure 서비스를 포함합니다. **Azure Active Directory** 및 **Intune** 브랜딩이 표시되지 않을 수 있지만 사용하고 있는 것입니다.

[Microsoft 365 관리 센터](https://admin.microsoft.com)에서 Endpoint Manager 관리 센터를 열 수도 있습니다.

1. [https://admin.microsoft.com](https://admin.microsoft.com)으로 이동합니다.
2. Microsoft 365 테넌트 구독의 관리자 계정으로 로그인합니다.
3. **관리 센터**에서 **모든 관리 센터** > **Endpoint Management**를 선택합니다. Endpoint Manager 관리 센터가 열립니다.

    > [!div class="mx-imgBorder"]
    > ![Microsoft 365 관리 센터의 모든 관리 센터 참조](./media/tutorial-walkthrough-administrative-templates/microsoft365-admin-centers.png)

## <a name="create-groups-and-add-users"></a>그룹 만들기 및 사용자 추가

온-프레미스 정책은 로컬, 사이트, 도메인 및 OU(조직 구성 단위)의 LSDOU 순서로 적용됩니다. 이 계층 구조에서 OU 정책은 로컬 정책을 덮어쓰고 도메인 정책은 사이트 정책을 덮어씁니다.

Intune에서 정책은 직접 만든 사용자 및 그룹에 적용됩니다. 계층 구조가 없습니다. 두 정책이 동일한 설정을 업데이트하는 경우 설정은 충돌로 표시됩니다. 두 준수 정책이 충돌하는 경우 가장 제한적인 정책이 적용됩니다. 두 구성 프로필이 충돌하는 경우 설정이 적용되지 않습니다. 자세한 내용은 [디바이스 정책 및 프로필과 관련된 일반적인 질문, 문제 및 해결 방법](device-profile-troubleshoot.md#if-multiple-policies-are-assigned-to-the-same-user-or-device-how-do-i-know-which-settings-gets-applied)을 참조하세요.

다음 단계에서는 보안 그룹을 만들고 그룹에 사용자를 추가합니다. 사용자를 여러 그룹에 추가할 수 있습니다. 예를 들어 사용자는 일반적으로 업무용 Surface Pro 및 개인용 Android 모바일 디바이스와 같은 여러 디바이스를 사용하게 됩니다. 또한 개인 사용자는 일반적으로 여러 디바이스에서 조직 리소스에 액세스하게 됩니다.

1. Endpoint Manager 관리 센터에서 **그룹** > **새 그룹**을 선택합니다.

2. 다음 설정을 입력합니다.

    - **그룹 유형**: **보안**을 선택합니다.
    - **그룹 이름**: **모든 Windows 10 학생 디바이스**를 입력합니다.
    - **멤버 자격 유형**: **할당됨**을 선택합니다.

3. **구성원**을 선택하고 일부 디바이스를 추가합니다.

    디바이스 추가는 선택 사항입니다. 목표는 그룹 만들기를 연습하고 디바이스 추가 방법을 알아보는 것입니다. 프로덕션 환경에서 이 자습서를 사용하는 경우 수행 중인 작업을 알고 있어야 합니다.

4. **선택** > **만들기**로 이동하여 변경 내용을 저장합니다.

    그룹이 표시되지 않습니까? **새로 고침**을 선택합니다.

5. **새 그룹**을 선택하고 다음 설정을 입력합니다.

    - **그룹 유형**: **보안**을 선택합니다.
    - **그룹 이름**: **모든 Windows 디바이스**를 입력합니다.
    - **멤버 자격 유형**: **동적 디바이스**를 선택합니다.
    - **동적 디바이스 구성원**: 쿼리를 구성합니다.

        - **속성**: **deviceOSType**을 선택합니다.
        - **연산자**: **Equals**를 선택합니다.
        - **값**: **Windows**를 입력합니다.

        1. **식 추가**를 선택합니다. 식은 **규칙 구문**에 표시됩니다.

            > [!div class="mx-imgBorder"]
            > ![동적 쿼리를 만들고 Microsoft Intune 관리 템플릿에서 식 추가](./media/tutorial-walkthrough-administrative-templates/dynamic-group-query.png)

            사용자 또는 디바이스가 입력한 조건을 충족하면 동적 그룹에 자동으로 추가됩니다. 이 예제에서 운영 체제가 Windows인 경우 디바이스는 이 그룹에 자동으로 추가됩니다. 이 자습서를 프로덕션 환경에서 사용하는 경우에는 주의하세요. 목표는 동적 그룹 만들기를 연습하는 것입니다.

        2. **저장** > **만들기**로 이동하여 변경 내용을 저장합니다.

6. 다음 설정을 사용하여 **모든 교사** 그룹을 만듭니다.

    - **그룹 유형**: **보안**을 선택합니다.
    - **그룹 이름**: **모든 교사**를 입력합니다.
    - **멤버 자격 유형**: **동적 사용자**를 선택합니다.
    - **동적 사용자 구성원**: 쿼리를 구성합니다.

      - **속성**: **부서**를 선택합니다.
      - **연산자**: **Equals**를 선택합니다.
      - **값**: **교사**를 입력합니다.

        1. **식 추가**를 선택합니다. 식은 **규칙 구문**에 표시됩니다.

            사용자 또는 디바이스가 입력한 조건을 충족하면 동적 그룹에 자동으로 추가됩니다. 이 예제에서 해당 부서가 교사인 경우 사용자는 이 그룹에 자동으로 추가됩니다. 사용자가 조직에 추가되면 부서 및 기타 속성을 입력할 수 있습니다. 이 자습서를 프로덕션 환경에서 사용하는 경우에는 주의하세요. 목표는 동적 그룹 만들기를 연습하는 것입니다.

        2. **저장** > **만들기**로 이동하여 변경 내용을 저장합니다.

### <a name="talking-points"></a>요점

- 동적 그룹은 Azure AD Premium의 기능입니다. Azure AD Premium이 없는 경우 할당된 그룹만 만들 수 있습니다. 동적 그룹에 대한 자세한 내용은 다음을 참조하세요.

  - [Azure Active Directory의 동적 그룹 멤버 자격(1부)](https://blogs.technet.microsoft.com/pauljones/2017/08/28/dynamic-group-membership-in-azure-active-directory-part-1/)
  - [Azure Active Directory의 동적 그룹 멤버 자격(2부)](https://blogs.technet.microsoft.com/pauljones/2017/08/29/dynamic-group-membership-in-azure-active-directory-part-2/)

- Azure AD Premium에는 [MFA(Multi-Factor Authentication)](https://docs.microsoft.com/azure/active-directory/authentication/concept-mfa-howitworks) 및 [조건부 액세스](https://docs.microsoft.com/azure/active-directory/conditional-access/overview)를 포함하여 앱과 디바이스를 관리할 때 일반적으로 사용되는 기타 서비스가 포함됩니다.

- 많은 관리자가 사용자 그룹을 사용하는 시기와 디바이스 그룹을 사용하는 시기를 궁금해합니다. 일부 지침은 [사용자 그룹 및 디바이스 그룹](device-profile-assign.md#user-groups-vs-device-groups)을 참조하세요.

- 사용자는 여러 그룹에 속할 수 있습니다. 다음과 같이 만들 수 있는 다른 동적 사용자 및 디바이스 그룹 중 일부를 고려해 보세요.

  - 모든 학생
  - 모든 Android 디바이스
  - 모든 iOS/iPadOS 디바이스
  - Marketing
  - 인적 자원
  - 모든 Charlotte 직원
  - 모든 Redmond 직원
  - 서부 IT 관리자
  - 동부 IT 관리자

만든 사용자 및 그룹은 [Microsoft 365 관리 센터](https://admin.microsoft.com), Azure Portal의 Azure AD 및 [Azure Portal의 Microsoft Intune](https://go.microsoft.com/fwlink/?linkid=2090973)에도 표시됩니다. 테넌트 구독을 위해 이 모든 영역에서 그룹을 만들고 관리할 수 있습니다. **목표가 디바이스 관리인 경우 [Microsoft Endpoint Manager 관리 센터](https://go.microsoft.com/fwlink/?linkid=2109431)를 사용합니다**.

### <a name="review-group-membership"></a>그룹 멤버 자격 검토

1. Endpoint Manager 관리 센터에서 **사용자**를 선택한 다음, 기존 사용자의 이름을 선택합니다.

    > [!div class="mx-imgBorder"]
    > ![Endpoint Manager 관리 센터에서 사용자 선택](./media/tutorial-walkthrough-administrative-templates/select-users-endpoint-manager-admin-center.png)

2. 추가하거나 변경할 수 있는 일부 정보를 검토합니다. 예를 들어 직위, 부서, 도시, 사무실 위치 등 구성할 수 있는 속성을 확인합니다. 동적 그룹을 만들 때 동적 쿼리에서 해당 속성을 사용할 수 있습니다.
3. **그룹**을 선택하여 이 사용자의 멤버 자격을 확인합니다. 그룹에서 사용자를 제거할 수도 있습니다.
4. 다른 옵션 중 일부를 선택하여 자세한 정보 및 수행할 수 있는 작업을 선택합니다. 예를 들어 할당된 라이선스, 사용자의 디바이스 등을 확인합니다.

### <a name="what-did-i-just-do"></a>이 단계에서 수행한 작업

Endpoint Manager 관리 센터에서 새 보안 그룹을 만들고 기존 사용자와 디바이스를 해당 그룹에 추가했습니다. 이 자습서의 이후 단계에서 해당 그룹을 사용합니다.

## <a name="create-a-template-in-intune"></a>Intune에서 템플릿 만들기

이 섹션에서는 Intune에서 관리 템플릿을 만들고, **그룹 정책 관리**의 일부 설정을 확인하고, Intune에서 동일한 설정을 비교합니다. 목표는 그룹 정책에 설정을 표시하고 Intune에 동일한 설정을 표시하는 것입니다.

1. Endpoint Manager 관리 센터에서 **디바이스** > **구성 프로필** > **프로필 만들기**를 선택합니다.
2. 다음 속성을 입력합니다.

    - **이름**: 프로필에 대한 설명이 포함된 이름을 입력합니다. 나중에 쉽게 식별할 수 있도록 프로필 이름을 지정합니다. 예를 들어 **관리 템플릿 - Windows 10 학생 디바이스**를 입력합니다.
    - **설명**: 프로필에 대한 설명을 입력합니다. 이 설정은 선택 사항이지만 권장됩니다.
    - **플랫폼**: **Windows 10 이상**을 선택합니다.
    - **프로필 유형**: **관리 템플릿**을 선택합니다.

3. **만들기**를 선택합니다. **범주 선택** 드롭다운 목록에서 **모든 제품**을 선택합니다. 모든 설정이 표시됩니다. 해당 설정에서 다음 속성을 확인합니다.

    - 정책의 **경로**는 그룹 정책 관리 또는 GPEdit과 동일합니다.
    - 설정은 사용자 또는 디바이스에 적용됩니다.

### <a name="open-group-policy-management"></a>그룹 정책 관리 열기

이 섹션에서는 Intune의 정책 및 그룹 정책 관리 편집기의 일치 정책을 보여 줍니다.

#### <a name="compare-a-device-policy"></a>디바이스 정책 비교

1. **관리자 컴퓨터**에서 **그룹 정책 관리** 앱을 엽니다.

    이 앱은 **RSAT: 그룹 정책 관리 도구**와 함께 설치되며, 이 도구는 Windows에 설치하는 선택적 기능입니다. 이 문서의 [필수 구성 요소](#prerequisites)에는 설치하는 단계가 나열됩니다.

2. **도메인**을 확장한 다음, 도메인을 선택합니다. 예를 들어 **contoso.net**을 선택합니다.
3. **OfficeandEdge** 정책을 마우스 오른쪽 단추로 클릭한 다음, **편집**을 선택합니다. 그러면 그룹 정책 관리 편집기 앱이 열립니다.

    > [!div class="mx-imgBorder"]
    > ![Office 및 Edge ADMX 그룹 정책을 마우스 오른쪽 단추로 클릭하고 편집 선택](./media/tutorial-walkthrough-administrative-templates/open-group-policy-management.png)

    **OfficeandEdge**는 Office 및 Microsoft Edge ADMX 템플릿을 포함하는 그룹 정책입니다. 이 정책은 이 문서의 [필수 구성 요소](#prerequisites)에서 설명합니다.

4. **컴퓨터 구성** > **정책** > **관리 템플릿** > **제어판** > **개인 설정**을 확장합니다. 사용 가능한 설정을 확인합니다.

    > [!div class="mx-imgBorder"]
    > ![그룹 정책 관리 편집기에서 컴퓨터 구성을 확장하고 개인 설정으로 이동](./media/tutorial-walkthrough-administrative-templates/open-group-policy-management-editor-admx-policy.png)

    **Prevent enabling lock screen camera**(잠금 화면 카메라 사용 금지)를 두 번 클릭하고 사용 가능한 옵션을 확인합니다.

    > [!div class="mx-imgBorder"]
    > ![그룹 정책에서 컴퓨터 구성 설정 옵션 확인](./media/tutorial-walkthrough-administrative-templates/prevent-enabling-lock-screen-camera-admx-policy.png)

5. 디바이스 관리의 관리 센터에서 **관리 템플릿 - Windows 10 학생 디바이스** 템플릿으로 이동합니다.
6. 드롭다운 목록에서 **모든 제품**을 선택하고 **개인 설정**을 검색합니다.

    > [!div class="mx-imgBorder"]
    > ![Microsoft Intune의 관리 템플릿에서 개인 설정 검색](./media/tutorial-walkthrough-administrative-templates/search-personalization-administrative-template.png)

    사용 가능한 설정을 확인합니다.

    설정 형식은 **디바이스**이며 경로는 **\Control Panel\Personalization**입니다. 이 경로는 그룹 정책 관리 편집기에서 방금 본 것과 비슷합니다. 설정을 열면 그룹 정책 관리 편집기에 표시된 것과 동일한 **구성되지 않음**, **사용** **사용 안 함** 옵션이 표시됩니다.

#### <a name="compare-a-user-policy"></a>사용자 정책 비교

1. 관리 템플릿에서 **InPrivate 브라우징**을 검색합니다. 경로를 확인하고 설정이 사용자 및 디바이스에 적용되는지 확인합니다.

2. **그룹 정책 관리 편집기**에서 일치하는 사용자 및 디바이스 설정을 찾습니다.

    - 디바이스: **컴퓨터 구성** > **정책** > **관리 템플릿** > **Windows 구성 요소** > **Internet Explorer** > **개인 정보** > **InPrivate 브라우징 끄기**를 확장합니다.
    - 사용자: **사용자 구성** > **정책** > **관리 템플릿** > **Windows 구성 요소** > **Internet Explorer** > **개인 정보** > **InPrivate 브라우징 끄기**를 확장합니다.

    > [!div class="mx-imgBorder"]
    > ![ADMX 템플릿을 사용하여 Internet Explorer에서 InPrivate 브라우징 끄기](./media/tutorial-walkthrough-administrative-templates/group-policy-turn-off-inprivate-browsing.png)

> [!TIP]
> 기본 제공 Windows 정책을 보려면 GPEdit(**그룹 정책 편집** 앱)을 사용할 수도 있습니다.

#### <a name="compare-an-edge-policy"></a>Edge 정책 비교

1. 디바이스 관리의 관리 센터에서 **관리 템플릿 - Windows 10 학생 디바이스** 템플릿으로 이동합니다.
2. 드롭다운 목록에서 **Edge 버전 77 이상**을 선택합니다.
3. **시작**을 검색합니다. 사용 가능한 설정을 확인합니다.
4. 그룹 정책 관리 편집기에서 다음 설정을 찾습니다.

    - 디바이스: **컴퓨터 구성** > **정책** > **관리 템플릿** > **Microsoft Edge** > **시작, 홈페이지 및 새 탭 페이지**를 확장합니다.
    - 사용자: **사용자 구성** > **정책** > **관리 템플릿** > **Microsoft Edge** > **시작, 홈페이지 및 새 탭 페이지**를 확장합니다.

### <a name="what-did-i-just-do"></a>이 단계에서 수행한 작업

Intune에서 관리 템플릿을 만들었습니다. 이 템플릿에서는 일부 ADMX 설정을 살펴보고 그룹 정책 관리에서 동일한 ADMX 설정을 살펴보았습니다.

## <a name="add-settings-to-the-students-admin-template"></a>학생 관리 템플릿에 설정 추가

이 템플릿에서는 여러 학생이 공유하는 디바이스를 잠그도록 일부 Internet Explorer 설정을 구성합니다.

1. **관리 템플릿 - Windows 10 학생 디바이스**에서 **InPrivate 브라우징 끄기**를 검색하고 디바이스 정책을 선택합니다.

    > [!div class="mx-imgBorder"]
    > ![Microsoft Intune의 관리 템플릿에서 InPrivate 브라우징 디바이스 정책 끄기](./media/tutorial-walkthrough-administrative-templates/turn-off-inprivate-browsing-administrative-template.png)

2. 이 창에서 설정할 수 있는 설명과 값을 확인합니다. 해당 옵션은 그룹 정책에 표시된 것과 비슷합니다.
3. **사용** > **확인**을 선택하여 변경 내용을 저장합니다.
4. 또한 다음과 Internet Explorer 설정을 구성합니다. **확인**을 선택하여 변경 내용을 저장해야 합니다.

    - **파일 끌어서 놓기 또는 파일 복사 및 붙여넣기 허용**
      - **형식**: 디바이스
      - **경로**: \Windows Components\Internet Explorer\Internet Control Panel\Security Page\Internet Zone
      - **값**: Disabled

    - **인증서 오류 무시할 수 없음**
      - **형식**: 디바이스
      - **경로**: \Windows Components\Internet Explorer\Internet Control Panel
      - **값**: 사용

    - **홈페이지 설정 변경할 수 없음**
      - **형식**: 사용자
      - **경로**: \Windows Components\Internet Explorer
      - **값**: 사용
      - **홈페이지**: URL(예: `contoso.com`)을 입력합니다.

5. 검색 필터의 선택을 취소합니다. 구성한 설정이 맨 위에 나열됩니다.

    > [!div class="mx-imgBorder"]
    > ![구성된 설정은 Microsoft Intune의 맨 위에 나열됨](./media/tutorial-walkthrough-administrative-templates/configured-settings-administrative-template.png)

### <a name="assign-your-template"></a>템플릿 할당

1. 템플릿에서 **할당**을 선택합니다. 템플릿을 닫은 후 **디바이스 - 구성 프로필** 목록에서 해당 템플릿을 선택해야 할 수 있습니다.

    > [!div class="mx-imgBorder"]
    > ![Microsoft Intune의 디바이스 구성 프로필 목록에서 관리 템플릿 프로필 선택](./media/tutorial-walkthrough-administrative-templates/filter-administrative-template-device-configuration-profiles-list.png)

2. **포함할 그룹 선택**을 선택합니다. 기존 사용자 및 그룹 목록이 표시됩니다.
3. 앞에서 만든 **모든 Windows 10 학생 디바이스** 그룹을 선택한 다음, **선택**을 선택합니다.

    이 자습서를 프로덕션 환경에서 사용하는 경우 비어 있는 그룹을 추가하는 것이 좋습니다. 목표는 템플릿 할당을 연습하는 것입니다.

4. 변경 내용을 **저장**합니다.

프로필은 저장되는 즉시 디바이스가 Intune에 체크 인될 때 디바이스에 적용됩니다. 디바이스가 인터넷에 연결되어 있으면 즉시 프로필이 적용될 수 있습니다. 정책 새로 고침 시간에 대한 자세한 내용은 [정책, 프로필 또는 앱을 할당한 후 디바이스에서 해당 정책, 프로필 또는 앱을 수신할 때까지 걸리는 시간](device-profile-troubleshoot.md#how-long-does-it-take-for-devices-to-get-a-policy-profile-or-app-after-they-are-assigned)을 참조하세요.

엄격하거나 제한적인 정책 및 프로필을 할당하는 경우에는 계정이 잠기지 않도록 주의하세요. 정책 및 프로필에서 제외되는 그룹을 만드는 것이 좋습니다. 문제를 해결하는 방법은 액세스 권한을 가지는 것입니다. 이 그룹을 모니터링하여 의도한 대로 사용 중인지 확인합니다.

### <a name="what-did-i-just-do"></a>이 단계에서 수행한 작업

Endpoint Manager 관리 센터에서 관리 템플릿 디바이스 구성 프로필을 만들고 직접 만든 그룹에 이 프로필을 할당했습니다.

## <a name="create-a-onedrive-template"></a>OneDrive 템플릿 만들기

이 섹션에서는 Intune에서 OneDrive 관리 템플릿을 만들어 일부 설정을 제어합니다. 이 특정 설정은 조직에서 일반적으로 사용되기 때문에 선택됩니다.

1. 다른 프로필을 만듭니다(**디바이스** > **구성 프로필을** > **프로필 만들기**).

2. 다음 속성을 입력합니다.

    - **이름**: **관리 템플릿 - 모든 Windows 10 사용자에게 적용되는 OneDrive 정책**을 입력합니다.
    - **설명**: 프로필에 대한 설명을 입력합니다. 이 설정은 선택 사항이지만 권장됩니다.
    - **플랫폼**: **Windows 10 이상**을 선택합니다.
    - **프로필 유형**: **관리 템플릿**을 선택합니다.

3. **만들기**를 선택합니다.
4. 드롭다운 목록에서 **Office**를 선택합니다.
5. 다음 설정을 **사용**합니다. **확인**을 선택하여 변경 내용을 저장해야 합니다.

    - **Windows 자격 증명을 사용하여 OneDrive 동기화 클라이언트에 자동으로 사용자 로그인**
    - **OneDrive 요청 기반 파일 관리 사용**
    - **사용자가 개인 OneDrive 계정을 동기화하지 못하도록 방지**

설정이 다음 설정과 유사하게 표시됩니다.

> [!div class="mx-imgBorder"]
> ![Microsoft Intune에서 OneDrive 관리 템플릿 만들기](./media/tutorial-walkthrough-administrative-templates/one-drive-administrative-template.png)

OneDrive 클라이언트 설정에 대한 자세한 내용은 [그룹 정책을 사용하여 OneDrive 동기화 클라이언트 설정 제어](https://docs.microsoft.com/onedrive/use-group-policy)를 참조하세요.

### <a name="assign-your-template"></a>템플릿 할당

1. 템플릿에서 **할당**을 선택합니다.
2. **포함할 그룹 선택**을 선택합니다. 기존 사용자 및 그룹 목록이 표시됩니다.
3. 앞에서 만든 **모든 Windows 디바이스** 그룹을 선택한 다음, **선택**을 선택합니다.

    이 자습서를 프로덕션 환경에서 사용하는 경우 비어 있는 그룹을 추가하는 것이 좋습니다. 목표는 템플릿 할당을 연습하는 것입니다.

4. 변경 내용을 **저장**합니다.

이제 일부 관리 템플릿을 만들고 직접 만든 그룹에 할당했습니다. 다음 단계는 Intune용 Microsoft Graph API 및 Windows PowerShell을 사용하여 관리 템플릿을 만드는 것입니다.

## <a name="optional-create-a-policy-using-powershell-and-graph-api"></a>선택 사항: PowerShell 및 Graph API를 사용하여 정책 만들기

이 섹션에서는 다음 리소스를 사용합니다. 이 섹션에서 이 리소스를 설치합니다.

- [Intune PowerShell SDK](https://github.com/microsoft/Intune-PowerShell-SDK)
- [Intune용 Microsoft Graph API](https://docs.microsoft.com/graph/api/resources/intune-graph-overview?view=graph-rest-1.0)

1. **관리자 컴퓨터**에서 관리자 권한으로 **Windows PowerShell**을 엽니다.

    1. 검색 창에 **powershell**을 입력합니다.
    2. **Windows PowerShell**을 마우스 오른쪽 단추로 클릭하고  > **관리자 권한으로 실행**을 선택합니다.

    > [!div class="mx-imgBorder"]
    > ![관리자 권한으로 Windows PowerShell 실행](./media/tutorial-walkthrough-administrative-templates/run-windows-powershell-administrator.png)

2. 실행 정책을 가져오고 설정합니다.

    1. 입력: `get-ExecutionPolicy`

        설정되어 있는 항목을 기록해 둡니다(**제한됨**일 수 있음). 자습서를 완료하면 원래 값으로 다시 설정합니다.

    2. 입력: `Set-ExecutionPolicy -ExecutionPolicy Unrestricted`

    3. `Y`를 입력하여 변경합니다.

    PowerShell의 실행 정책은 악의적인 스크립트 실행을 방지하는 데 도움이 됩니다. 자세한 내용은 [실행 정책 정보](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_execution_policies)를 참조하세요.

3. 입력: `Install-Module -Name Microsoft.Graph.Intune`

    다음과 같은 경우 `Y`를 입력합니다.

    - NuGet 공급자를 설치하도록 요청된 경우
    - 신뢰할 수 없는 리포지토리의 모듈을 설치하도록 요청된 경우

    완료하는 데 몇 분 정도 걸릴 수 있습니다. 완료되면 다음과 같은 프롬프트가 표시됩니다.

    > [!div class="mx-imgBorder"]
    > ![모듈을 설치한 후 Windows PowerShell 프롬프트](./media/tutorial-walkthrough-administrative-templates/powershell-prompt.png)

4. 웹 브라우저에서 [https://github.com/Microsoft/Intune-PowerShell-SDK/releases](https://github.com/Microsoft/Intune-PowerShell-SDK/releases)로 이동하고 **Intune-PowerShell-SDK_v6.1907.00921.0001.zip** 파일을 선택합니다.

    1. **다른 이름으로 저장**을 선택하고 기억할 폴더를 선택합니다. `c:\psscripts`를 선택하는 것이 좋습니다.
    2. 폴더를 열고, .zip 파일을 마우스 오른쪽 단추로 클릭한 다음, **모두 추출** > **추출**을 선택합니다. 폴더 구조는 다음 폴더와 유사하게 표시됩니다.

        > [!div class="mx-imgBorder"]
        > ![추출된 후 Intune PowerShell SDK 폴더 구조](./media/tutorial-walkthrough-administrative-templates/psscripts-directory.png)

5. **보기** 탭에서 **파일 이름 확장명**을 확인합니다.

    > [!div class="mx-imgBorder"]
    > ![탐색기의 보기 탭에서 파일 이름 확장명 선택](./media/tutorial-walkthrough-administrative-templates/file-names-extension.png)

6. 폴더에서 `c:\psscripts\Intune-PowerShell-SDK_v6.1907.00921.0001\drop\outputs\build\Release\net471`로 이동합니다. 모든 .dll을 마우스 오른쪽 단추로 클릭한 다음, **속성** > **차단 해제**를 선택합니다.

    > [!div class="mx-imgBorder"]
    > ![DLL 차단 해제](./media/tutorial-walkthrough-administrative-templates/unblock-dll.png)

7. **Windows PowerShell** 앱에서 다음을 입력합니다.

    ```powershell
    Import-Module c:\psscripts\Intune-PowerShell-SDK_v6.1907.00921.0001\drop\outputs\build\Release\net471\Microsoft.Graph.Intune.psd1
    ```

    신뢰할 수 없는 게시자에서 실행할지 묻는 메시지가 표시되면 `R`을 입력합니다.

8. Intune 관리 템플릿은 Graph의 베타 버전을 사용합니다.

    1. 입력: `Update-MSGraphEnvironment -SchemaVersion 'beta'`

    2. 입력: `Connect-MSGraph -AdminConsent`

    3. 메시지가 표시되면 동일한 Microsoft 365 관리자 계정으로 로그인합니다. 이 cmdlet은 테넌트 조직에 정책을 만듭니다.

        **사용자**: Microsoft 365 테넌트 구독의 관리자 계정을 입력합니다.  
        **암호**: 해당 암호를 입력합니다.

    4. **수락**을 선택합니다.

9. **테스트 구성** 구성 프로필을 만듭니다. 다음을 입력합니다.

    ```powershell
    $configuration = Invoke-MSGraphRequest -Url https://graph.microsoft.com/beta/deviceManagement/groupPolicyConfigurations -Content '{"displayName":"Test Configuration","description":"A test configuration created through PS"}' -HttpMethod POST
    ```

    이 cmdlet이 성공하면 프로필이 생성됩니다. 확인하려면 Endpoint Manager 관리 센터 > **구성 프로필**로 이동합니다. **테스트 구성** 프로필이 나열됩니다.

10. 모든 SettingDefinitions를 가져옵니다. 다음을 입력합니다.

    ```powershell
    $settingDefinitions = Invoke-MSGraphRequest -Url https://graph.microsoft.com/beta/deviceManagement/groupPolicyDefinitions -HttpMethod GET
    ```

11. 설정 표시 이름을 사용하여 정의 ID를 찾습니다. 다음을 입력합니다.

    ```powershell
    $desiredSettingDefinition = $settingDefinitions.value | ? {$_.DisplayName -Match "Silently sign in users to the OneDrive sync client with their Windows credentials"}
    ```

12. 설정을 구성합니다. 다음을 입력합니다.

    ```powershell
    $configuredSetting = Invoke-MSGraphRequest -Url "https://graph.microsoft.com/beta/deviceManagement/groupPolicyConfigurations('$($configuration.id)')/definitionValues" -Content ("{""enabled"":""true"",""configurationType"":""policy"",""definition@odata.bind"":""https://graph.microsoft.com/beta/deviceManagement/groupPolicyDefinitions('$($desiredSettingDefinition.id)')""}") -HttpMethod POST
    ```

    ```powershell
    Invoke-MSGraphRequest -Url "https://graph.microsoft.com/beta/deviceManagement/groupPolicyConfigurations('$($configuration.id)')/definitionValues('$($configuredSetting.id)')" -Content ("{""enabled"":""false""}") -HttpMethod PATCH
    ```

    ```powershell
    $configuredSetting = Invoke-MSGraphRequest -Url "https://graph.microsoft.com/beta/deviceManagement/groupPolicyConfigurations('$($configuration.id)')/definitionValues('$($configuredSetting.id)')" -HttpMethod GET
    ```

### <a name="see-your-policy"></a>정책 이름 확인

1. Endpoint Manager 관리 센터에서 **구성 프로필** > **새로 고침**을 선택합니다.
2. **테스트 구성** 프로필 > **설정**을 선택합니다.
3. 드롭다운 목록에서 **모든 제품**을 선택합니다.

**Windows 자격 증명을 사용하여 OneDrive 동기화 클라이언트에 자동으로 사용자 로그인** 설정이 구성되어 있음을 알 수 있습니다.

## <a name="policy-best-practices"></a>정책 모범 사례

Intune에서 정책 및 프로필을 만들 때 고려해야 할 몇 가지 권장 사항 및 모범 사례가 있습니다. 자세한 내용은 [정책 및 프로필 모범 사례](device-profile-create.md#recommendations)를 참조하세요.

## <a name="clean-up-resources"></a>리소스 정리

더 이상 필요하지 않은 경우 다음을 수행할 수 있습니다.

- 만든 그룹을 삭제합니다.

  - **모든 Windows 10 학생 디바이스**
  - **모든 Windows 디바이스**
  - **모든 교사**

- 만든 관리 템플릿을 삭제합니다.

  - **관리 템플릿 - Windows 10 학생 디바이스**
  - **관리 템플릿 - 모든 Windows 10 사용자에게 적용되는 OneDrive 정책**
  - **테스트 구성**

- Windows PowerShell 실행 정책을 다시 원래 값으로 설정합니다. 다음 예제에서는 실행 정책을 제한됨으로 설정합니다.

  ```powershell
  Set-ExecutionPolicy -ExecutionPolicy Restricted
  ```

## <a name="next-steps"></a>다음 단계

이 자습서에서는 [Microsoft Endpoint Manager 관리 센터](https://go.microsoft.com/fwlink/?linkid=2109431)에 더 익숙해지고, 쿼리 작성기를 사용하여 동적 그룹을 만들고, [ADMX 설정](https://docs.microsoft.com/windows/client-management/mdm/understanding-admx-backed-policies)을 구성하기 위해 Intune에서 관리 템플릿을 만들었습니다. 또한 Intune을 사용하여 온-프레미스 및 클라우드에서 ADMX 템플릿을 사용을 비교했습니다. 이와 함께 PowerShell cmdlet을 사용하여 관리 템플릿을 만들었습니다.

Intune의 관리 템플릿에 대한 자세한 내용은 다음을 참조하세요.

> [!div class="nextstepaction"]
> [Intune에서 Windows 10 템플릿을 사용하여 그룹 정책 설정 구성](administrative-templates-windows.md)
