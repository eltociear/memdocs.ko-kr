---
title: Microsoft Intune에서 Windows 10의 도메인 가입 프로필 설정 - Azure | Microsoft Docs
description: 하이브리드 Azure AD 가입 디바이스의 도메인 가입 디바이스 구성 프로필을 만듭니다. 이 프로필을 사용하여 온-프레미스 Active Directory 도메인 정보를 Windows Autopilot 및 Microsoft Intune으로 프로비전된 디바이스에 배포합니다.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/20/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 207b3983c214ad4e166ae58ea0ccd18ea23bf418
ms.sourcegitcommit: 3d895be2844bda2177c2c85dc2f09612a1be5490
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79364398"
---
# <a name="configuration-domain-join-settings-for-hybrid-azure-ad-joined-devices-in-microsoft-intune"></a>Microsoft Intune에서 하이브리드 Azure AD 가입 디바이스의 구성 도메인 가입 설정

많은 환경에서 온-프레미스 Active Directory(AD)를 사용합니다. Azure AD에도 가입된 AD 도메인 가입 디바이스를 하이브리드 Azure AD 가입 디바이스라고 합니다. Windows Autopilot을 사용하여 Intune에 [하이브리드 Azure AD 가입 디바이스를 등록](../enrollment/windows-autopilot-hybrid.md)할 수 있습니다. 등록하려면 **도메인 가입** 구성 프로필도 필요합니다.

**도메인 가입** 구성 프로필에는 온-프레미스 Active Directory 도메인 정보가 포함되어 있습니다. 디바이스가 프로비전되면(일반적으로 오프라인으로) 이 프로필은 디바이스가 가입할 온-프레미스 도메인을 알 수 있도록 AD 도메인 세부 정보를 배포합니다. 도메인 가입 프로필을 만들지 않으면 이러한 디바이스 배포가 실패할 수 있습니다.

이 기능은 다음에 적용됩니다.

- Windows 10 이상
- 하이브리드 Azure AD 가입 디바이스
- Autopilot + Intune을 사용한 하이브리드 배포

이 문서에서는 하이브리드 Autopilot 배포를 위해 도메인 가입 프로필을 만드는 방법을 보여 줍니다. 사용 가능한 설정도 볼 수 있습니다.

## <a name="create-the-profile"></a>프로필 만들기

1. [Microsoft Endpoint Manager 관리 센터](https://go.microsoft.com/fwlink/?linkid=2109431)에 로그인합니다.
2. **디바이스 구성** > **구성 프로필** > **프로필 만들기**를 선택합니다.
3. 다음 속성을 입력합니다.

    - **이름**: 정책에 대한 설명이 포함된 이름을 입력합니다. 나중에 쉽게 식별할 수 있도록 정책 이름을 지정합니다. 좋은 정책 이름의 예는 다음과 같습니다. **Windows 10: 하이브리드 AD 가입 디바이스를 Windows Autopilot에 등록하기 위한 온-프레미스 도메인 정보를 포함하는 도메인 가입 프로필**.
    - **설명**: 정책에 대한 설명을 입력합니다. 이 설정은 선택 사항이지만 권장됩니다.
    - **플랫폼**: **Windows 10 이상**을 선택합니다.
    - **프로필 유형**: **도메인 가입(미리 보기)** 을 선택합니다.

4. **설정**을 선택합니다. 다음 속성을 입력합니다.

    - **컴퓨터 이름 접두사**: 디바이스 이름의 접두사를 입력합니다. 컴퓨터 이름의 길이는 15자입니다. 접두사 뒤의 나머지 15자는 무작위로 생성됩니다.
    - **도메인 이름**: 디바이스가 가입할 FQDN(정규화된 도메인 이름)을 입력합니다. 예를 들어 다음과 같이 입력합니다. `americas.corp.contoso.com.`
    - **조직 구성 단위**(선택 사항): 컴퓨터 계정을 만들 조직 구성 단위(OU)의 전체 경로([고유 이름](https://docs.microsoft.com/windows/win32/ad/object-names-and-identities#distinguished-name))를 입력합니다. 예를 들어 다음과 같이 입력합니다. `"CN=Users,DC=Contoso,DC=com"` 값을 입력하지 않으면 잘 알려진 컴퓨터 개체 컨테이너가 사용됩니다.

      이 설정에 대한 자세한 내용과 조언은 [하이브리드 Azure AD 가입 디바이스 배포](../enrollment/windows-autopilot-hybrid.md)를 참조하세요.

5. 작업이 완료되면 **확인** > **만들기**를 선택하여 변경 내용을 저장합니다.

프로필이 만들어지고 프로필 목록에 표시됩니다. 이제 [Intune 및 Windows Autopilot을 사용하여 하이브리드 Azure AD 가입 디바이스를 배포](../enrollment/windows-autopilot-hybrid.md)할 준비가 되었습니다.

## <a name="next-steps"></a>다음 단계

프로필이 생성된 후에는 이를 할당할 수 있습니다. 다음으로, [프로필을 할당](device-profile-assign.md)하고, [해당 상태를 모니터링](device-profile-monitor.md)합니다.

[Intune 및 Windows Autopilot을 사용하여 하이브리드 Azure AD 가입 디바이스를 배포합니다](../enrollment/windows-autopilot-hybrid.md).
