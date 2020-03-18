---
title: Microsoft Intune에서 iOS/iPadOS 디바이스에 사용자 지정 설정 추가 - Azure | Microsoft Docs
titleSuffix: ''
description: Apple Configurator 또는 Apple Profile Manager 도구에서 iOS 및 iPadOS 설정을 내보낸 다음, 이 설정을 Microsoft Intune으로 가져옵니다. 이 설정은 iOS/iPadOS 디바이스에서 사용자 지정 설정과 기능을 만들고 사용하고 제어할 수 있습니다. 그런 다음, 이 사용자 지정 프로필을 조직의 iOS/iPadOS 디바이스에 할당하거나 배포하여 기준 또는 표준을 만들 수 있습니다.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 02/18/2020
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 3cec45dae7e0596428b2d7ab5c925889c183d465
ms.sourcegitcommit: 3d895be2844bda2177c2c85dc2f09612a1be5490
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79364593"
---
# <a name="use-custom-settings-for-ios-and-ipados-devices-in-microsoft-intune"></a>Microsoft Intune에서 iOS 및 iPadOS 디바이스의 사용자 지정 설정 추가

Microsoft Intune을 사용하면 "사용자 지정 프로필"을 사용하여 iOS/iPadOS 디바이스에 대한 사용자 지정 설정을 추가하거나 만들 수 있습니다. 사용자 지정 프로필은 Intune의 기능입니다. Intune에 기본 제공되지 않은 디바이스 설정 및 기능을 추가하도록 설계되었습니다.

iOS/iPadOS 디바이스를 사용하는 경우, 사용자 지정을 Intune으로 가져오는 방법은 다음의 두 가지가 있습니다.

- [Apple Configurator](https://itunes.apple.com/app/apple-configurator-2/id1037126344?mt=12)
- [Apple Profile Manager](https://support.apple.com/profile-manager)

이 도구를 사용하여 설정을 구성 프로필로 내보낼 수 있습니다. Intune에서 이 파일을 가져온 다음, iOS/iPadOS 사용자 및 디바이스에 프로필을 할당합니다. 일단 할당되면 설정이 배포됩니다. 또한 설정은 조직 내에서 iOS/iPadOS에 대한 기준 또는 표준도 만듭니다.

이 문서에서는 Apple Configurator 및 Apple Profile Manager 사용에 대한 몇 가지 지침을 제공하며 구성 가능한 속성에 대해 설명합니다.

## <a name="before-you-begin"></a>시작하기 전에

[프로필을 만듭니다](device-profile-create.md).

## <a name="what-you-need-to-know"></a>기억해야 하는 사항

- **Apple Configurator**를 사용하여 구성 프로필을 만들 때, 내보내는 설정이 디바이스의 iOS/iPadOS 버전과 호환되는지 확인합니다. 호환되지 않는 설정 해결에 대한 정보를 보려면 [Apple 개발자](https://developer.apple.com/) 웹 사이트에서 **구성 프로필 참조** 및 **모바일 디바이스 관리 프로토콜 참조**를 검색하세요.

- **Apple Profile Manager**를 사용하는 경우 다음을 확인해야 합니다.

  - Profile Manager에서 [모바일 디바이스 관리](https://help.apple.com/serverapp/mac/5.7/#/apd05B9B761-D390-4A75-9251-E9AD29A61D0C)를 사용합니다.
  - Profile Manager에서 [iOS/iPadOS 디바이스](https://help.apple.com/profilemanager/mac/5.7/#/pm9onzap1984)를 추가합니다.
  - Profile Manager에서 디바이스를 추가한 후 **라이브러리에서** > **디바이스** &gt;디바이스 선택 &gt; **설정**으로 이동합니다. 디바이스에 대한 일반 설정을 입력합니다.

    이 파일을 다운로드하고 저장합니다. Intune 프로필에서 이 파일을 입력합니다.

  - Apple Profile Manager에서 내보내는 설정이 디바이스의 iOS/iPadOS 버전과 호환되는지 확인합니다. 호환되지 않는 설정 해결에 대한 정보를 보려면 [Apple 개발자](https://developer.apple.com/) 웹 사이트에서 **구성 프로필 참조** 및 **모바일 디바이스 관리 프로토콜 참조**를 검색하세요.

## <a name="custom-configuration-profile-settings"></a>사용자 지정 구성 프로필 설정

- **사용자 지정 구성 프로필 이름**: 정책의 이름을 입력합니다. 이 이름은 디바이스 및 Intune 상태에서 표시됩니다.
- **구성 프로필 파일**: Apple Configurator 또는 Apple Profile Manager를 사용하여 만든 구성 프로필을 찾아봅니다. 최대 파일 크기는 100만 바이트(1MB 미만)입니다. 가져온 파일은 **파일 내용** 영역에 표시됩니다.

  사용자 지정 구성 파일에 디바이스 토큰을 추가할 수도 있습니다. 디바이스 토큰은 디바이스별 정보를 추가하는 데 사용됩니다. 예를 들어 일련 번호를 표시하려면 `{{serialnumber}}`를 입력합니다. 디바이스에서 텍스트는 각 디바이스에 고유한 `123456789ABC`와 유사하게 표시됩니다. 변수를 입력할 때 `{{ }}` 중괄호를 사용해야 합니다. [앱 구성 토큰](../apps/app-configuration-policies-use-ios.md#tokens-used-in-the-property-list)에는 사용할 수 있는 변수 목록이 포함됩니다. `deviceid` 또는 기타 디바이스 관련 값을 사용할 수도 있습니다.

  > [!NOTE]
  > 변수는 UI에서 유효성이 검사되지 않으며 대/소문자를 구분합니다. 따라서, 잘못된 입력으로 저장된 프로필을 볼 수 있습니다. 예를 들어 `{{deviceid}}` 대신 `{{DeviceID}}`을 입력하면 디바이스의 고유 ID 대신 리터럴 문자열이 표시될 수 있습니다. 올바른 정보를 입력해야 합니다.

**확인** > **만들기**를 선택하여 변경 내용을 저장합니다. 프로필이 만들어지고 프로필 목록에 표시됩니다.

## <a name="next-steps"></a>다음 단계

프로필이 만들어지지만 아직 아무것도 하지 않습니다. 그런 다음, [프로필을 할당합니다](device-profile-assign.md).

[macOS 디바이스에서 프로필을 만드는](custom-settings-macos.md) 방법을 참조하세요. 
