---
title: Microsoft Intune - Azure에서 Android용 디바이스 제한 설정 | Microsoft Docs
description: Microsoft Intune에서 제어하고 제한할 수 있는 모든 Android 디바이스 설정 목록을 참조하세요. 이러한 설정을 사용하여 암호를 제어하고, Google Play에 액세스하고, 앱을 허용하거나 금지하고, 브라우저 설정을 제어하고, 앱을 차단하고, Google 클라우드에 백업하고, 메시지, 음성, 데이터 로밍, Wi-Fi 및 Bluetooth 연결 옵션을 제어할 수 있습니다.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 12/19/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.reviewer: ayesham, chrisbal
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: a38a7a0e191990871724e217d84c6bd8babb12dc
ms.sourcegitcommit: 3d895be2844bda2177c2c85dc2f09612a1be5490
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79361863"
---
# <a name="android-and-samsung-knox-standard-device-restriction-settings-lists-in-intune"></a>Intune의 Android 및 Samsung Knox Standard 디바이스 제한 사항 설정 목록

이 아티클에서는 Android를 실행하는 디바이스에 대해 구성할 수 있는 모든 Microsoft Intune 디바이스 제한 설정을 보여줍니다.

>[!TIP]
>원하는 설정을 사용할 수 없는 경우 [사용자 지정 프로필](custom-settings-android.md)을 사용하여 디바이스를 구성할 수 있습니다.

## <a name="general"></a>일반

- **카메라**: **차단**을 선택하면 카메라에 액세스할 수 없습니다. **구성되지 않음**을 사용하면 디바이스의 카메라에 액세스할 수 있습니다.
- **복사 및 붙여넣기(Samsung KNOX에만 해당)** : **차단**을 선택하면 복사하여 붙여넣기를 수행할 수 없습니다. **구성되지 않음**을 사용하면 디바이스에서 복사 및 붙여넣기 기능을 사용할 수 있습니다.
- **앱 간의 클립보드 공유(Samsung KNOX에만 해당)** : **차단**을 선택하면 클립보드를 사용하여 앱 간에 복사 및 붙여넣기를 수행할 수 없습니다. **구성되지 않음**을 사용하면 클립보드를 사용하여 앱 간에 복사 및 붙여넣을 수 있습니다.
- **진단 데이터 제출(Samsung KNOX에만 해당)** : **차단**을 선택하면 사용자가 디바이스에서 버그 보고서를 제출할 수 없습니다. **구성되지 않음**을 사용하면 사용자가 데이터를 제출할 수 있습니다.
- **초기화(Samsung KNOX에만 해당)** : 사용자가 디바이스에서 [초기화](../remote-actions/devices-wipe.md) 작업을 실행할 수 있습니다.
- **지리적 위치(Samsung KNOX에만 해당)** : **차단**을 선택하면 디바이스에서 위치 정보를 사용할 수 없습니다. **구성되지 않음**을 사용하면 디바이스에서 위치 정보를 사용할 수 있습니다.
- **전원 끄기(Samsung KNOX에만 해당)** : **차단**을 선택하면 사용자가 디바이스 전원을 끌 수 없습니다. 이 설정을 사용하지 않으면 **디바이스를 초기화하기 전 로그인 오류 발생 횟수** 설정이 지정되지 않으며 작동하지 않습니다. **구성되지 않음**을 사용하면 사용자가 디바이스 전원을 끌 수 있습니다.
- **화면 캡처(Samsung KNOX에만 해당)** : **차단**을 선택하면 스크린샷을 방지할 수 있습니다. **구성되지 않음**을 사용하면 사용자가 화면 콘텐츠를 이미지로 캡처할 수 있습니다.
- **음성 도우미(Samsung KNOX에만 해당)** : **차단**을 선택하면 S 음성 서비스를 사용하지 않도록 설정할 수 있습니다. **구성되지 않음**을 사용하면 디바이스에서 S 음성 서비스 및 앱을 사용할 수 있습니다. 이 설정은 Bixby 또는 화면 내용을 소리를 내어 읽는 접근성 음성 도우미에는 적용되지 않습니다.
- **YouTube(Samsung KNOX에만 해당)** : **차단**을 선택하면 사용자가 YouTube 앱을 사용할 수 없습니다. **구성되지 않음**을 사용하면 디바이스에서 YouTube 앱을 사용할 수 있습니다.
- **공유 디바이스(Samsung KNOX에만 해당)** : 관리되는 Samsung KNOX Standard 디바이스를 공유 디바이스로 구성합니다. **허용**으로 설정되면 최종 사용자가 Azure AD 자격 증명을 사용하여 디바이스 로그인/로그아웃을 수행할 수 있습니다. 디바이스는 사용 중인지 여부와 관계없이 관리되는 상태로 유지됩니다.</br>이 기능을 SCEP 인증서 프로필과 함께 사용하면 최종 사용자가 모든 사용자에 대해 동일한 앱으로 디바이스를 공유할 수 있습니다. 그러나 각 사용자에게 고유한 SCEP 사용자 인증서가 있습니다. 사용자가 로그아웃하면 모든 앱 데이터가 지워집니다. 이 기능은 LOB 앱으로만 제한됩니다. </br>**구성되지 않음**을 선택하면 여러 최종 사용자가 Azure AD 자격 증명을 사용하여 디바이스의 회사 포털 앱에 로그인할 수 없습니다.
- **날짜 및 시간 변경 차단(Samsung Knox)** : **차단**을 선택하면 사용자가 디바이스의 날짜 및 시간 설정을 변경할 수 없습니다. **구성되지 않음**을 사용하면 사용자가 날자 및 시간 설정을 변경할 수 있습니다.

## <a name="password"></a>암호

- **암호**: 최종 사용자에게 디바이스에 액세스하려면 암호를 입력하도록 **요구**합니다. **구성되지 않음**을 사용하면 사용자가 암호를 입력하지 않고 디바이스에 액세스할 수 있습니다.

    > [!NOTE]
    > 삼성 Knox 디바이스는 MDM 등록 중에 4자리 PIN을 자동으로 요구합니다. 네이티브 Android 디바이스는 조건부 액세스와의 호환을 위해 자동으로 PIN을 요구할 수 있습니다.

- **최소 암호 길이**: 사용자가 입력해야 하는 암호의 최소 길이를 입력합니다(4~16자).
- **화면이 잠기기 전까지 최대 비활성 시간(분)** : 디바이스에서 화면이 잠기기 전까지 비활성 상태로 유지될 수 있는 최대 시간(분)을 입력합니다. 디바이스의 최종 사용자는 프로필에 구성된 시간보다 큰 시간 값은 설정할 수 없습니다. 더 작은 시간 값은 설정할 수 있습니다. 예를 들어 프로필이 15분으로 설정된 경우 최종 사용자가 값을 5분으로 설정할 수 있습니다. 최종 사용자는 값을 30분으로 설정할 수 없습니다. 
- **디바이스를 초기화하기 전 로그인 오류 발생 횟수**: 디바이스를 초기화하기 전까지 허용되는 로그인 오류 횟수를 입력합니다.
- **암호 만료(일)** : 디바이스 암호를 변경해야 할 때까지의 기간(일)을 입력합니다.
- **필수 암호 유형**: 필요한 암호 복잡성 수준과 생체 인식 디바이스 사용 가능 여부를 입력합니다. 옵션은 다음과 같습니다.
  - **디바이스 기본값**
  - **낮은 보안 생체 인식**
  - **최소 숫자**
  - **복합 숫자**: “1111” 또는 “1234”와 같이 반복 또는 연속된 숫자는 허용되지 않습니다.<sup>1</sup>
  - **최소 알파벳**
  - **최소 영숫자**
  - **기호가 포함된 최소 영숫자**
- **이전 암호 다시 사용 방지**: 최종 사용자가 이전에 사용한 암호를 만드는 것을 막습니다.
- **지문 잠금 해제(Samsung KNOX에만 해당)** : **차단**을 선택하면 지문으로 디바이스 잠금을 해제할 수 없습니다. **구성되지 않음**을 사용하면 사용자가 지문을 통해 디바이스 잠금을 해제할 수 있습니다.
- **Smart Lock 및 기타 신뢰 에이전트**: **차단**을 선택하면 Smart Lock 또는 기타 신뢰 에이전트가 잠금 화면 설정을 조정할 수 없습니다(Samsung KNOX Standard 5.0 이상). 신뢰 에이전트라고도 하는 이 휴대폰 기능을 통해 디바이스가 신뢰할 수 있는 위치에 있는 경우 디바이스 잠금 화면 암호를 사용하지 않도록 설정하거나 무시할 수 있습니다. 예를 들어 디바이스가 특정 Bluetooth 디바이스에 연결되어 있거나 NFC 태그 근처에 있을 때 이 기능을 사용할 수 있습니다. 이 설정을 사용하면 사용자가 스마트 잠금 기능을 구성하는 것을 방지할 수 있습니다.
- **암호화**: **필요**를 선택하면 디바이스의 파일이 암호화됩니다. 일부 디바이스는 암호화를 지원하지 않습니다. 이 기능을 사용하려면 다음을 수행합니다. 
  1. **암호**를 **필요**로 설정합니다.
  2. **필수 암호 유형**을 **숫자 이상**으로 설정합니다.
  3. 이 설정에 대한 규정 준수를 올바르게 보고하려면 **최소 암호 길이**를 4 이상으로 설정합니다.

  > [!NOTE]
  > 암호화 정책이 적용되는 경우 삼성 Knox 디바이스는 사용자에게 디바이스 암호에 대해 6자 복합 암호를 설정하도록 요구합니다.

<sup>1</sup> 이 설정을 디바이스에 할당하기 전에 해당 디바이스에서 회사 포털 앱을 최신 버전으로 업데이트해야 합니다.

**필수 암호 유형**을 **복합 숫자**로 설정한 후 Android 5.0 이전 버전을 실행하는 디바이스에 할당하면 다음 동작이 적용됩니다.

- 회사 포털 앱에서 1704 이전 버전을 실행하는 경우 PIN 정책이 디바이스에 적용되지 않고 오류가 Microsoft Endpoint Manager 관리 센터에 표시됩니다.
- 회사 포털 앱에서 1704 버전 이상을 실행하는 경우에는 단순 PIN만 적용할 수 있습니다. Android 5.0 이전 버전에서는 이 설정이 지원되지 않습니다. Microsoft Endpoint Manager 관리 센터에는 오류가 표시되지 않습니다.

## <a name="google-play-store"></a>Google Play 스토어

- **Google Play 스토어(Samsung KNOX에만 해당)** : **차단**을 선택하면 사용자가 Google Play 스토어를 사용할 수 없습니다. **구성되지 않음**을 사용하면 사용자가 디바이스에서 Google Play 스토어에 액세스할 수 있습니다.

## <a name="restricted-apps"></a>제한된 앱

이러한 설정을 사용하여 디바이스에서 특정 앱을 허용하거나 차단합니다. 이 기능은 Android 및 Samsung Knox Standard 디바이스에서 지원됩니다.

- **금지된 앱**: 디바이스에 설치하지 않으려는 Intune에서 비관리형 앱 목록입니다. 사용자가 이 목록의 앱을 설치하면 Intune에서 알림이 표시됩니다.
- **승인된 앱**: 사용자가 설치하도록 허용된 앱 목록입니다. 계속해서 규정을 준수하려면 사용자가 다른 앱을 설치하지 않아야 합니다. Intune에서 관리되는 앱은 자동으로 허용됩니다.

이러한 목록에 앱을 추가하려면 다음을 수행할 수 있습니다.

- 원하는 앱의 Google Play 스토어 URL을 **추가**합니다. 예를 들어 Android용 Microsoft 원격 데스크톱 앱을 추가하려면 `https://play.google.com/store/apps/details?id=com.microsoft.rdc.android`를 입력합니다. 앱 URL을 찾으려면 [Google Play 스토어](https://play.google.com/store/apps)를 열고 앱을 검색합니다. 예를 들어 `Microsoft Remote Desktop Play Store` 또는 `Microsoft Planner`를 검색합니다. 앱을 선택하고 URL을 복사합니다.
- URL을 비롯하여 앱 세부 정보가 있는 CSV 파일을 가져옵니다. <’앱 URL’>, <’앱 이름’>, <’앱 게시자’> 형식을 사용합니다.    또는 제한된 앱 목록을 포함하는 기존 목록을 동일한 형식으로 **내보냅니다**.

> [!IMPORTANT]
> 제한된 앱 설정을 사용하는 디바이스 프로필을 사용자 그룹에 할당해야 합니다.

## <a name="browser"></a>브라우저

- **웹 브라우저(Samsung KNOX에만 해당)** : **차단**을 선택하면 기본 웹 브라우저가 디바이스에서 사용되지 않습니다. **구성되지 않음**을 사용하면 디바이스의 기본 웹 브라우저를 사용할 수 있습니다.
- **자동 채우기(Samsung KNOX에만 해당)** : **차단**을 선택하면 브라우저에서 텍스트 자동 채우기를 사용할 수 없습니다. **구성되지 않음**을 사용하면 웹 브라우저의 자동 채우기 기능을 사용할 수 있습니다.
- **쿠키(Samsung KNOX에만 해당)** : 디바이스에서 웹 사이트의 쿠키를 처리 할 방법을 선택합니다. 옵션은 다음과 같습니다.
  - 허용
  - 모든 쿠키 차단
  - 방문한 웹 사이트의 쿠키 허용
  - 현재 웹 사이트의 쿠키 허용
- **Javascript(Samsung KNOX에만 해당)** : **차단**을 선택하면 웹 브라우저에서 JavaScript를 실행할 수 없습니다. **구성되지 않음**을 사용하면 디바이스 웹 브라우저에서 JavaScript를 실행할 수 있습니다.
- **팝업(Samsung KNOX에만 해당)** : **차단**을 선택하면 웹 브라우저에서 팝업을 사용할 수 없습니다. **구성되지 않음**을 사용하면 웹 브라우저에서 팝업이 허용됩니다.

## <a name="allow-or-block-apps"></a>앱 허용 또는 차단

이러한 설정을 사용하여 Samsung Knox Standard 디바이스에서 특정 앱을 허용, 차단 또는 숨깁니다. 사용자가 숨겨진 앱을 열거나 실행할 수 없습니다.

옵션은 다음과 같습니다.

- **설치가 허용된 앱(Samsung Knox Standard만 해당)**
- **시작이 차단된 앱(Samsung Knox Standard만 해당)**
- **사용자에게 숨겨진 앱(Samsung Knox Standard만 해당)**

각 설정에 대한 앱 목록을 추가합니다. 옵션은 다음과 같습니다.

- **패키지 이름으로 앱 추가**: 주로 LOB(기간 업무) 앱에 사용합니다. 앱 이름과 앱 패키지 이름을 입력합니다.
- **URL로 앱 추가**: 앱 이름과 Google Play 스토어의 해당 URL을 입력합니다.
- **스토어 앱 추가**: Intune에서 관리하는 기존 앱 목록에서 앱을 선택합니다.

## <a name="cloud-and-storage"></a>클라우드 및 스토리지

- **Google 백업(Samsung KNOX에만 해당)** : **차단**을 선택하면 디바이스가 Google 백업에 동기화되지 않습니다. **구성되지 않음**을 사용하면 Google 백업을 사용할 수 있습니다.
- **Google 계정 자동 동기화(Samsung KNOX에만 해당)** : **차단**을 선택하면 디바이스에서 Google 계정 자동 동기화 기능을 사용할 수 없습니다. **구성되지 않음**을 사용하면 Google 계정 설정을 자동으로 동기화할 수 있습니다.
- **이동식 스토리지(Samsung KNOX에만 해당)** : **차단**을 선택하면 디바이스에서 이동식 스토리지를 사용할 수 없습니다. **구성되지 않음**을 사용하면 디바이스에서 SD 카드와 같은 이동식 스토리지를 사용할 수 있습니다.
- **스토리지 카드의 암호화(Samsung KNOX에만 해당)** : **필요**를 선택하면 스토리지 카드를 암호화해야 합니다. **구성되지 않음**을 사용하면 암호화되지 않은 스토리지 카드를 사용할 수 있습니다. 일부 디바이스는 스토리지 카드 암호화를 지원하지 않습니다. 확인하려면 디바이스 제조업체에 문의하세요.

## <a name="cellular-and-connectivity"></a>셀룰러 및 연결

- **데이터 로밍(Samsung KNOX에만 해당)** : **차단**을 선택하면 셀룰러 네트워크를 통한 데이터 로밍이 제한됩니다. **구성되지 않음**을 사용하면 디바이스가 셀룰러 네트워크에 있을 때 데이터 로밍이 허용됩니다.
- **SMS/MMS 메시징(Samsung KNOX에만 해당)** : **차단**을 선택하면 디바이스에서 문자 메시지를 차단할 수 있습니다. **구성되지 않음**을 사용하면 디바이스에서 SMS 및 MMS 메시징을 사용할 수 있습니다.
- **음성 전화 걸기(Samsung KNOX에만 해당)** : **차단**을 선택하면 사용자가 디바이스에서 음성 전화 걸기 기능을 사용할 수 없습니다. **구성되지 않음**을 사용하면 디바이스에서 음성 전화 걸기가 허용됩니다.
- **음성 로밍(Samsung KNOX에만 해당)** : **차단**을 선택하면 셀룰러 네트워크를 통한 음성 로밍이 제한됩니다. **구성되지 않음**을 사용하면 디바이스가 셀룰러 네트워크에 있을 때 음성 로밍이 허용됩니다.
- **Bluetooth(Samsung KNOX에만 해당)** : **차단**을 선택하면 디바이스에서 Bluetooth를 사용할 수 없습니다. **구성되지 않음**을 사용하면 디바이스에서 Bluetooth를 사용할 수 있습니다.
- **NFC(Samsung KNOX에만 해당)** : **차단**을 선택하면 NFC(근거리 통신) 기술이 중지됩니다. **구성되지 않음**을 사용하면 지원되는 디바이스에서 근거리 통신을 작업에 사용할 수 있습니다.
- **Wi-Fi(Samsung KNOX에만 해당)** : **차단**을 선택하면 디바이스에서 Wi-Fi를 사용할 수 없습니다. **구성되지 않음**을 사용하면 디바이스의 Wi-Fi 기능을 사용할 수 있습니다.
- **Wi-Fi 테더링(Samsung KNOX에만 해당)** : **차단**을 선택하면 디바이스에서 Wi-Fi 테더링을 사용할 수 없습니다. **구성되지 않음**을 사용하면 디바이스에서 Wi-Fi 테더링을 사용할 수 있습니다.

## <a name="kiosk"></a>키오스크

키오스크 설정은 Samsung Knox Standard 디바이스와 Intune을 사용하여 관리하는 앱에만 적용됩니다.

- 디바이스가 키오스크 모드일 때 실행할 앱을 추가합니다. 키오스크 모드에서는 추가하는 앱만 실행되고, 추가되지 않은 앱은 실행되지 않습니다. 미리 설치된 브라우저는 디바이스가 키오스크 모드일 때 앱으로 실행되지 않습니다. 브라우저가 필요한 경우 [Managed Browser](../apps/app-configuration-managed-browser.md)를 사용하는 것이 좋습니다.

  앱 옵션:

  - **패키지 이름으로 앱 추가**: 주로 LOB(기간 업무) 앱에 사용합니다. 앱 이름과 앱 패키지 이름을 입력합니다.
  - **URL로 앱 추가**: 앱 이름과 Google Play 스토어의 해당 URL을 입력합니다.
  - **스토어 앱 추가**: Intune에서 관리하는 기존 앱 목록에서 앱을 선택합니다.

- **화면 절전 모드 단추**: **차단**을 선택하면 차단하거나 화면 절전 모드 단추가 제한되거나 숨겨집니다. **구성되지 않음**을 사용하면 디바이스에서 화면 절전 모드 해제 단추를 사용할 수 있습니다.
- **볼륨 단추**: **차단**을 선택하면 사용자가 볼륨 단추를 표시하여 볼륨을 조정할 수 없습니다. **구성되지 않음**을 사용하면 디바이스에서 볼륨 단추를 사용할 수 있습니다.

## <a name="next-steps"></a>다음 단계

[프로필을 할당](device-profile-assign.md)하고, 해당 [상태를 모니터링](device-profile-monitor.md)합니다.

[Android 엔터프라이즈](device-restrictions-android-for-work.md#dedicated-device-settings) 및 [Windows 10](kiosk-settings.md) 디바이스에 대한 키오스크 프로필을 만들 수도 있습니다.
