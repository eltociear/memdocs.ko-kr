---
title: 빠른 시작 - iOS/iPadOS 디바이스용 메일 디바이스 프로필 만들기
titleSuffix: Microsoft Intune
description: iOS/iPadOS 디바이스가 회사 메일에 안전하게 연결할 수 있도록 Microsoft Intune을 사용하여 메일 디바이스 프로필을 만드는 방법을 알아봅니다.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 02/18/2020
ms.topic: quickstart
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 7a6345afe4258ff7141228a7284932f083791c70
ms.sourcegitcommit: 3d895be2844bda2177c2c85dc2f09612a1be5490
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79361486"
---
# <a name="quickstart-create-an-email-device-profile-for-iosipados"></a>빠른 시작: iOS/iPadOS용 이메일 디바이스 프로필 만들기

이 빠른 시작에서는 iOS/iPadOS 디바이스용 메일 디바이스 프로필을 만드는 방법을 알아봅니다. 이 프로필은 회사 메일에 연결하기 위해 iOS/iPadOS 디바이스의 기본 제공 메일 앱에 필요한 설정을 지정합니다. 이메일 디바이스 프로필을 사용하면 디바이스 설정을 표준화할 수 있으며, 최종 사용자가 설정 작업을 수행할 필요 없이 자신의 개인용 디바이스에서 회사 이메일에 액세스할 수 있습니다. 메일을 더욱 안전하게 보호하려면 메일 프로필을 사용하여 디바이스가 규정을 준수하는지 확인한 다음, 규정을 준수하는 디바이스만 메일에 액세스할 수 있도록 조건부 액세스를 설정하면 됩니다. 이메일 프로필에 대한 자세한 내용은 [Microsoft Intune에서 이메일 설정을 구성하는 방법](email-settings-configure.md)을 참조하세요.

Intune 구독이 없으면 [평가판 계정에 등록](../fundamentals/free-trial-sign-up.md)하세요.

## <a name="sign-in-to-intune"></a>Intune에 로그인

전역 관리자 또는 Intune 서비스 관리자로 [Microsoft Endpoint Manager 관리 센터](https://go.microsoft.com/fwlink/?linkid=2109431)에 로그인합니다. Intune 평가판 구독을 만든 경우 구독을 만든 계정은 글로벌 관리자입니다.

## <a name="create-an-iosipados-email-profile"></a>iOS/iPadOS 메일 프로필 만들기

1. **디바이스 구성** > **구성 프로필** > **프로필 만들기**를 선택합니다.

   ![Intune에서 iOS/iPadOS용 메일 프로필 만들기](./media/quickstart-email-profile/ios-create-profile.png)

2. **이름** 아래에 새 프로필에 대해 설명하는 이름을 입력합니다. 이 예에서는 **iOS에서 회사 이메일 요구**를 입력합니다.
3. 다음 프로필 정보를 입력합니다.
    - **설명**에 **iOS/iPadOS 디바이스에 회사 메일을 사용하도록 요구**를 입력합니다.
    - **플랫폼**에서 **iOS/iPadOS**를 선택합니다.
    - **프로필 유형**으로 **이메일**을 선택합니다.

        ![Intune의 iOS/iPadOS 디바이스에서 사용할 메일 프로필 만들기](./media/quickstart-email-profile/ios-email-profile-name.png)

4. **설정**을 선택하고 다음 설정을 입력합니다(그 외의 설정은 기본값 유지).
   - **메일 서버**: 이 빠른 시작에서는 **outlook.office365.com**을 입력합니다. 이 설정은 iOS/iPadOS 메일 앱이 메일에 연결하는 데 사용할 메일 서버의 Exchange 위치(URL)를 지정합니다.
   - **계정 이름**: **회사 이메일**을 입력합니다.
   - **AAD의 사용자 이름 특성**: 이 이름은 Intune이 Azure AD(Azure Active Directory)에서 가져오는 특성입니다. Intune은 이 이름을 사용하여 이 프로필의 사용자 이름을 동적으로 생성합니다. 이 빠른 시작에서는 **사용자 계정 이름**을 프로필의 사용자 이름으로 사용할 것입니다(예: user1@contoso.com).
   - **AAD의 메일 주소 특성**: 이 설정은 Exchange에 로그인하는 데 사용되는 Azure AD의 이메일 주소입니다. 이 빠른 시작에서는 **사용자 계정 이름**을 선택합니다.
   - **인증 방법**: 이 빠른 시작에서는 **사용자 이름 및 암호**를 선택합니다. (Intune에 대한 인증서를 이미 설정한 경우 **인증서**를 선택해도 됩니다.)

        ![iOS/iPadOS용 메일 프로필 만들기](./media/quickstart-email-profile/ios-email-profile.png)

5. **확인** > **만들기**를 선택합니다. 프로필 목록에 새 프로필이 나타나고 대시보드가 표시되므로 프로필이 iOS/iPadOS 디바이스 및 iOS/iPadOS 사용자에게 어떻게 할당되었는지 모니터링할 수 있습니다.
6. **할당**을 선택합니다.
7. **포함** 탭을 선택하고 **모든 사용자 및 모든 디바이스**를 선택합니다. 
8. **저장**을 선택합니다.

## <a name="clean-up-resources"></a>리소스 정리

여기서 만든 프로필을 다른 자습서 또는 테스트에 더 이상 사용하지 않으려는 경우 지금 삭제할 수 있습니다.

1. Intune에서 **디바이스 구성**을 선택하고 **프로필**을 선택합니다.
2. 여기서 만든 테스트 프로필 **iOS/iPadOS에서 회사 메일 요구**를 선택합니다.
3. 프로필 옆에서 줄임표( **...** )를 선택하고 **삭제**를 선택합니다.

## <a name="next-steps"></a>다음 단계

이 빠른 시작에서는 iOS/iPadOS 디바이스용 메일 프로필을 만들었습니다. 이제 이 프로필을 사용하여 프로필과 일치하지 않는 iOS/iPadOS 디바이스를 비준수로 표시하는 규정 준수 정책을 만들어서 iOS/iPadOS 디바이스의 규정 준수 여부를 확인할 수 있습니다. 보다 강력한 보호를 원하는 경우 비준수 iOS/iPadOS 디바이스의 메일 액세스를 차단하는 조건부 액세스 정책을 만들면 됩니다. 디바이스 준수 정책에 대한 자세한 내용은 [Intune에서 디바이스 준수 정책 시작](../protect/device-compliance-get-started.md)을 참조하세요.

> [!div class="nextstepaction"]
> [자습서: 관리 디바이스에서 Exchange Online 이메일 보호](../protect/tutorial-protect-email-on-enrolled-devices.md)
