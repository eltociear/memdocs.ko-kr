---
title: Microsoft Intune에서 macOS 디바이스에 기본 설정 파일 설정 추가 - Azure | Microsoft Docs
titleSuffix: ''
description: 앱에 대한 키 정보를 포함하는 xml 또는 plist 파일을 추가합니다. 기본 설정 파일 디바이스 구성 프로필을 사용하여 속성 목록 파일에서 키 정보를 변경하고 macOS 디바이스에 할당합니다.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/09/2020
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: d226888c3d710a7b80357ebb92130b34ab2fef94
ms.sourcegitcommit: 3d895be2844bda2177c2c85dc2f09612a1be5490
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79360758"
---
# <a name="add-a-property-list-file-to-macos-devices-using-microsoft-intune"></a>Microsoft Intune을 사용하여 macOS 디바이스에 속성 목록 파일 추가

Microsoft Intune을 사용하여 macOS 디바이스 또는 macOS에 설치된 앱에 대한 속성 목록 파일(.plist)을 추가할 수 있습니다.

이 기능은 다음에 적용됩니다.

- 10.7 이상 버전을 실행하는 macOS 디바이스

일반적으로 속성 목록 파일에는 macOS 애플리케이션에 대한 정보가 포함됩니다. 자세한 내용은 [정보 속성 목록 파일 정보](https://developer.apple.com/library/archive/documentation/General/Reference/InfoPlistKeyReference/Articles/AboutInformationPropertyListFiles.html)(Apple 웹 사이트) 및 [사용자 지정 페이로드 설정](https://support.apple.com/guide/mdm/custom-mdm9abbdbe7/1/web/1)을 참조하세요.

이 문서에서는 macOS 디바이스에 추가할 수 있는 다양한 속성 목록 파일 설정을 나열하고 설명합니다. MDM(모바일 장치 관리) 솔루션의 일부로 이러한 설정을 사용하여 앱 번들 ID(`com.company.application`)를 추가하고 해당 .plist 파일을 추가합니다.

이러한 설정은 Intune에서 디바이스 구성 프로필에 추가된 다음, macOS 디바이스에 할당되거나 배포됩니다.

## <a name="before-you-begin"></a>시작하기 전에

[프로필을 만듭니다](device-profile-create.md).

## <a name="what-you-need-to-know"></a>기억해야 하는 사항

- 이러한 설정은 유효성이 검사되지 않습니다. 디바이스에 프로필을 할당하기 전에 변경 내용을 테스트해야 합니다.
- 앱 키를 입력하는 방법을 잘 모르겠으면 앱 내부에서 설정을 변경합니다. 그런 다음 [Xcode](https://developer.apple.com/xcode/)를 사용하여 앱의 기본 설정 파일을 검토해 설정이 어떻게 구성되었는지 확인합니다. Apple에서는 파일을 가져오기 전에 Xcode를 사용하여 관리할 수 없는 설정을 제거할 것을 권장합니다.
- 일부 앱은 관리되는 기본 설정에서 작동하므로 사용자가 모든 설정을 관리할 수는 없습니다.
- 사용자 채널 설정이 아니라 디바이스 채널 설정을 대상으로 하는 속성 목록 파일을 업로드해야 합니다. 속성 목록 파일은 전체 디바이스를 대상으로 합니다.

## <a name="preference-file"></a>기본 설정 파일

- **기본 설정 도메인 이름**: 속성 목록 파일은 일반적으로 웹 브라우저(Microsoft Edge), [Microsoft Defender Advanced Threat Protection](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-atp-mac) 및 사용자 지정 앱에 사용됩니다. 기본 설정 도메인을 만들면 번들 ID도 만들어집니다. `com.company.application`와 같은 번들 ID를 입력합니다. 예를 들어 `com.Contoso.applicationName`, `com.Microsoft.Edge` 또는 `com.microsoft.wdav`를 입력합니다.
- **속성 목록 파일**: 앱과 연결된 속성 목록 파일을 선택합니다. `.plist` 또는 `.xml` 파일이어야 합니다. 예를 들어 `YourApp-Manifest.plist` 또는 `YourApp-Manifest.xml` 파일을 업로드합니다.
- **파일 내용**: 속성 목록 파일의 키 정보가 표시됩니다. 키 정보를 변경해야 하는 경우에는 다른 편집기에서 목록 파일을 열고 Intune에서 해당 파일을 다시 업로드합니다.

파일이 올바르게 서식 지정되어야 합니다. 파일은 키 값 쌍만 있어야 하고 `<dict>`, `<plist>`또는 `<xml>` 태그로 래핑되지 않아야 합니다. 예를 들어 속성 목록 파일은 다음 파일과 비슷해야 합니다.

```xml
<key>SomeKey</key>
<string>someString</string>
<key>AnotherKey</key>
<false/>
...
```

**확인** > **만들기**를 선택하여 변경 내용을 저장합니다. 프로필이 만들어지고 프로필 목록에 표시됩니다.

## <a name="next-steps"></a>다음 단계

프로필이 만들어지지만 아직 아무것도 하지 않습니다. 다음으로, [프로필을 할당](device-profile-assign.md)하고, [해당 상태를 모니터링](device-profile-monitor.md)합니다.

Microsoft Edge의 기본 설정 파일에 대한 자세한 내용은 [macOS에서 Microsoft Edge 정책 설정 구성](https://docs.microsoft.com/deployedge/configure-microsoft-edge-on-mac)을 참조하세요.
