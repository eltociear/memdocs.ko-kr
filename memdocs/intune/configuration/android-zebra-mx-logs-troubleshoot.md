---
title: Microsoft Intune에서 Android Zebra 디바이스에 StageNow 로그 사용 - Azure | Microsoft Docs
description: Microsoft Intune으로 Android 디바이스에서 StageNow를 사용하는 경우의 일반적인 문제 및 해결 방법을 참조하세요. 또한 로그를 가져오는 방법을 알아보고 성공 또는 오류에 대한 로그를 읽는 방법의 예를 확인합니다.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/26/2019
ms.topic: troubleshooting
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
ms.openlocfilehash: d8c7c60b4d9d1831aaabb9886345865234ce6351
ms.sourcegitcommit: 3d895be2844bda2177c2c85dc2f09612a1be5490
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79364619"
---
# <a name="troubleshoot-and-see-potential-issues-on-android-zebra-devices-in-microsoft-intune"></a>Microsoft Intune에서 Android Zebra 디바이스의 문제 해결 및 잠재적인 문제 확인



Microsoft Intune에서 [Zebra Mobility Extensions(MX)를 사용하여 Android Zebra 디바이스를 관리](android-zebra-mx-overview.md)합니다. Zebra 디바이스를 사용하는 경우 StageNow에서 프로필을 만들어 설정을 관리하고 Intune에 설정을 업로드합니다. Intune은 StageNow 앱을 사용하여 디바이스에서 설정을 적용합니다. 또한 StageNow 앱은 문제 해결에 사용되는 자세한 로그 파일을 디바이스에서 만듭니다.

이 기능은 다음에 적용됩니다.

- Android

예를 들어 StageNow에서 프로필을 만들어 디바이스를 구성합니다. StageNow 프로필을 만들 때 마지막 단계에서는 프로필 테스트에 사용할 파일을 생성합니다. 디바이스에서 이 파일을 StageNow 앱과 함께 사용합니다.

또 다른 예에서는 StageNow에서 프로필을 만들어 테스트합니다. Intune에서 StageNow 프로필을 추가한 다음 Zebra 디바이스에 할당합니다. 할당된 프로필의 상태를 확인할 때 프로필에는 높은 수준의 상태가 표시됩니다.

이러한 두 가지 경우 모두 StageNow 프로필이 적용될 때마다 디바이스에 저장되는 StageNow 로그 파일에서 자세한 정보를 얻을 수 있습니다.

일부 문제는 StageNow 프로필의 내용과 관련이 없으며 로그에 반영되지 않습니다.

이 문서는 StageNow 로그를 읽는 방법을 보여 주며, 로그에 반영되지 않을 수 있는 Zebra 디바이스의 다른 몇 가지 잠재적인 문제를 나열합니다.

[Zebra Mobility Extensions를 사용하여 Zebra 디바이스 사용 및 관리](android-zebra-mx-overview.md)에는 이 기능에 대한 자세한 내용이 나와 있습니다.

## <a name="get-the-logs"></a>로그 가져오기

### <a name="use-the-stagenow-app-on-the-device"></a>디바이스에서 StageNow 앱 사용
[Intune을 사용하여 프로필을 배포](android-zebra-mx-overview.md#step-4-create-a-device-management-profile-in-stagenow)하는 대신 컴퓨터에서 직접 StageNow를 사용하여 프로필을 테스트하면 디바이스의 StageNow 앱이 테스트의 로그를 저장합니다. 로그 파일을 가져오려면 디바이스의 StageNow 앱에서 **더 보기(...)** 옵션을 사용합니다.

### <a name="get-logs-using-android-debug-bridge"></a>Android Debug Bridge를 사용하여 로그 가져오기
Intune을 사용하여 프로필이 이미 배포된 후 로그를 가져오려면 [Android Debug Bridge(ADB)](https://developer.android.com/studio/command-line/adb)(Android의 웹 사이트가 열림)를 사용하여 컴퓨터에 디바이스를 연결합니다.

디바이스에서 로그는 `/sdcard/Android/data/com.microsoft.windowsintune.companyportal/files`에 저장됩니다.

### <a name="get-logs-from-email"></a>이메일에서 로그 가져오기
Intune을 사용하여 프로필이 이미 배포된 후 로그를 가져오려면 최종 사용자가 디바이스에서 이메일 앱을 사용하여 로그를 이메일로 보낼 수 있습니다. Zebra 디바이스에서 회사 포털 앱을 열고 [로그를 보냅니다](https://docs.microsoft.com/user-help/send-logs-to-your-it-admin-by-email-android). 로그 보내기 기능을 사용하면 Microsoft 지원에 문의할 때 참조할 수 있는 PowerLift 인시던트 ID도 만들어집니다.

## <a name="read-the-logs"></a>로그 읽기

로그를 볼 때 `<characteristic-error>` 태그가 표시될 때마다 오류가 발생합니다. 오류 세부 정보는 `<parm-error>`태그 > `desc` 속성에 기록됩니다.

## <a name="error-types"></a>오류 유형

Zebra 디바이스에 여러 오류 보고 수준이 포함되어 있습니다.

- CSP가 디바이스에서 지원되지 않습니다. 예를 들어 디바이스가 셀룰러 장치가 아니며 셀룰러 관리자가 없습니다.
- MX 또는 OSX 버전이 일치하지 않습니다. 각 CSP에는 버전이 지정되어 있습니다. 전체 지원 매트릭스는 [Zebra 설명서](http://techdocs.zebra.com/mx/)(Zebra 웹 사이트가 열림)를 참조하세요.
- 디바이스가 다른 문제 또는 오류를 보고합니다.

## <a name="examples"></a>예

예를 들어 다음과 같은 입력 프로필이 있다고 가정합니다.

```xml
<wap-provisioningdoc>
    <characteristic type="Clock">
        <parm name="AutoTime" value="false"/>
        <parm name="TimeZone" value="GMT-5"/>
        <parm name="Date" value="2014-12-03"/>
        <parm name="Time" value="11:11:11"/>
    </characteristic>
</wap-provisioningdoc>
```

로그에서 XML은 입력과 동일합니다. 이 일치하는 출력은 프로필이 오류 없이 디바이스에 성공적으로 적용되었음을 뜻합니다.

```xml
<wap-provisioningdoc>
    <characteristic type="Clock" version="6.0">
        <parm name="AutoTime" value="false"/>
        <parm name="TimeZone" value="GMT-5"/>
        <parm name="Date" value="2014-12-03"/>
        <parm name="Time" value="11:11:11"/>
    </characteristic>
</wap-provisioningdoc>
```

또 다른 예에는 다음과 같은 입력이 있습니다.

```xml
<wap-provisioningdoc>
    <characteristic type="XmlMgr" version="4.2" >
        <parm name="ProcessingMode" value="1"/>
    </characteristic>
    <characteristic type="AppMgr" version="4.2" >
        <parm name="Action" value="Install"/>
        <parm name="APK" value="/sdcard/test.apk"/>
    </characteristic>
</wap-provisioningdoc>
```

`<characteristic-error>` 태그가 포함되어 있으므로 로그에 오류가 표시됩니다. 이 시나리오에서 프로필은 지정된 경로에 없는 Android 패키지(APK)를 설치하려고 시도했습니다.

```xml
<wap-provisioningdoc>
    <characteristic type="XmlMgr" version="4.2">
        <parm name="ProcessingMode" value="1"/>
    </characteristic>
    <characteristic-error type="AppMgr" version="5.1" desc="missing">
        <parm-error name="Action" value="Install" desc="apk doesnot exist in the path"/>
        <parm name="APK" value="/sdcard/test.apk"/>
    </characteristic-error>
</wap-provisioningdoc>
```

## <a name="other-potential-issues-with-zebra-devices"></a>Zebra 디바이스의 다른 잠재적 문제

이 섹션에는 디바이스 관리자와 함께 Zebra 디바이스를 사용할 때 나타날 수 있는 다른 문제가 나열되어 있습니다. 이러한 문제는 StageNow 로그에 보고되지 않습니다.

### <a name="android-system-webview-is-out-of-date"></a>Android System WebView 만료됨

이전 디바이스가 회사 포털 앱을 사용하여 로그인하는 경우 System WebView 구성 요소가 최신이 아니며 업그레이드해야 한다는 메시지가 사용자에게 표시될 수 있습니다. 디바이스에 Google Play가 설치되어 있으면 인터넷에 연결하고 업데이트를 확인합니다. 디바이스에 Google Play가 설치되어 있지 않으면 업데이트된 구성 요소 버전을 가져와 디바이스에 적용합니다. 또는 Zebra에서 발급한 최신 디바이스 OS로 업데이트합니다.

### <a name="management-actions-take-a-long-time"></a>관리 작업에 시간이 오래 걸림

Google Play 서비스를 사용할 수 없는 경우 일부 작업을 완료하는 데 최대 8시간이 걸립니다. [Android용 Intune 회사 포털 앱의 제한 사항](https://support.microsoft.com/help/3211588/limitations-of-intune-company-portal-app-for-android-in-china)(다른 Microsoft 웹 사이트가 열림)이 좋은 리소스가 될 수 있습니다.

### <a name="device-spoofing-suspected-shows-in-intune"></a>Intune에 "디바이스 스푸핑이 의심됨" 표시

이 오류는 Intune이 Zebra Android가 아닌 디바이스의 해당 모델 및 제조업체를 Zebra 디바이스로 보고 하고 있다고 의심한다는 뜻입니다.

### <a name="company-portal-app-is-older-than-minimum-required-version"></a>회사 포털 앱이 필요한 최소 버전보다 이전 버전임

Intune은 회사 포털 앱의 필요한 최소 버전을 업데이트할 수 있습니다. 디바이스에 Google Play가 설치되어 있지 않으면 회사 포털 앱이 자동으로 업데이트되지 않습니다. 필요한 최소 버전이 설치된 버전보다 최신인 경우 회사 포털 앱의 작동이 중지됩니다. [Zebra 디바이스에서 테스트용 로드](android-zebra-mx-overview.md#sideload-the-company-portal-app)를 사용하여 최신 회사 포털 앱으로 업데이트합니다.

## <a name="next-steps"></a>다음 단계

[Zebra 토론 게시판](https://developer.zebra.com/community/home/discussions)(Zebra 웹 사이트가 열림)

[Intune에서 Zebra Mobility Extensions를 사용하여 Zebra 디바이스 사용 및 관리](android-zebra-mx-overview.md)
