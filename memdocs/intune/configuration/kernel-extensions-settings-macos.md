---
title: Microsoft Intune의 macOS 커널 확장 설정 - Azure | Microsoft Docs
titleSuffix: ''
description: macOS 디바이스에서 커널 확장을 사용하도록 설정을 추가하거나, 구성하거나 만듭니다. 또한 사용자가 승인된 확장을 재정의하도록 허용하거나, 팀 식별자에서 모든 확장을 허용하거나, Microsoft Intune에서 특정 확장 또는 앱을 허용할 수 있습니다.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 09/10/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: aa471beb5929a6c5b39267871518f560fe6978f6
ms.sourcegitcommit: 3d895be2844bda2177c2c85dc2f09612a1be5490
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79343429"
---
# <a name="macos-device-settings-to-configure-and-use-kernel-extensions-in-intune"></a>Intune에서 커널 확장을 구성 및 사용하는 macOS 디바이스 설정



이 문서에서는 macOS 디바이스에서 제어할 수 있는 다양한 커널 확장 설정을 나열하고 설명합니다. MDM(모바일 장치 관리) 솔루션의 일부로, 이러한 설정을 사용하여 디바이스에서 커널 확장을 추가하고 관리합니다.

Intune의 커널 확장 및 모든 필수 구성 요소에 대해 자세히 알아보려면 [macOS 커널 확장 추가](kernel-extensions-overview-macos.md)를 참조하세요.

이러한 설정은 Intune에서 디바이스 구성 프로필에 추가된 다음, macOS 디바이스에 할당되거나 배포됩니다.

## <a name="before-you-begin"></a>시작하기 전에

[디바이스 커널 확장 구성 프로필을 만듭니다](kernel-extensions-overview-macos.md).

> [!NOTE]
> 이러한 설정은 다른 등록 유형에 적용됩니다. 여러 등록 유형에 대한 자세한 내용은 [macOS 등록](../enrollment/macos-enroll.md)을 참조하세요.

## <a name="kernel-extensions"></a>커널 확장

### <a name="settings-apply-to-user-approved-automated-device-enrollment"></a>설정 적용 대상: 사용자가 승인한 자동화된 디바이스 등록

- **사용자 재정의 허용**: **허용**하면 사용자가 구성 프로필에 포함되지 않은 커널 확장을 승인할 수 있습니다. **구성 되지 않음**(기본값)은 사용자가 구성 프로필에 포함되지 않은 확장을 허용할 수 없게 합니다. 즉, 구성 프로필에 포함된 확장만 허용됩니다.

  이 기능에 대한 자세한 내용은 [사용자 승인 커널 확장 로드](https://developer.apple.com/library/archive/technotes/tn2459/_index.html)(Apple의 웹 사이트가 열림)를 참조하세요.

- **허용된 팀 식별자**: 하나 이상의 팀 ID를 허용하려면 이 설정을 사용합니다. 입력한 팀 ID로 서명된 모든 커널 확장이 허용되고 신뢰됩니다. 즉, 이 옵션을 사용하여 동일한 팀 ID 내에 있는 모든 커널 확장을 허용할 수 있습니다. 이는 특정 개발자나 파트너가 될 수 있습니다.

  로드하려는 유효한 서명된 커널 확장의 팀 식별자를 **추가**합니다. 팀 식별자를 여러 개 추가할 수 있습니다. 팀 식별자는 영숫자(문자 및 숫자)이고 10자여야 합니다. 예를 들어 다음과 같이 입력합니다. `ABCDE12345`

  추가한 팀 식별자는 삭제할 수도 있습니다.

  자세한 내용은 [팀 ID 찾기](https://help.apple.com/developer-account/#/dev55c3c710c)(Apple의 웹 사이트가 열림)를 참조하세요.

- **허용된 커널 확장**: 특정 커널 확장을 허용하려면 이 설정을 사용합니다. 입력한 커널 확장만 허용되거나 신뢰됩니다.

  로드하려는 커널 확장의 번들 식별자 및 팀 식별자를 **추가**합니다. 서명되지 않은 레거시 커널 확장의 경우 빈 팀 식별자를 사용합니다. 커널 확장을 여러 개 추가할 수 있습니다. 팀 식별자는 영숫자(문자 및 숫자)이고 10자여야 합니다. 예를 들어 **번들 ID**에는 `com.contoso.appname.macos`를 입력하고 **팀 식별자**에는 `ABCDE12345`를 입력합니다.

  > [!TIP]
  > macOS 디바이스에서 Kext(커널 확장)의 번들 ID를 가져오려면 다음을 수행할 수 있습니다.
  >
  > 1. 터미널에서 `kextstat | grep -v com.apple`을 실행하고 출력을 확인합니다. 원하는 소프트웨어 또는 Kext를 설치합니다. `kextstat | grep -v com.apple`을 다시 실행하고 변경 내용을 확인합니다.
  >
  >    터미널에서 `kextstat`는 OS의 모든 커널 확장을 나열합니다. 
  >
  > 2. 디바이스에서 Kext에 대한 정보 속성 목록 파일(info.plist)을 엽니다. 번들 ID가 표시됩니다. 각 Kext에는 info.plist 파일이 저장되어 있습니다.

> [!NOTE]
> 팀 식별자 및 커널 확장을 추가할 필요가 없습니다. 이들을 구성할 수 있습니다.

## <a name="next-steps"></a>다음 단계

[프로필을 할당](device-profile-assign.md)하고, 해당 [상태를 모니터링](device-profile-monitor.md)합니다.
