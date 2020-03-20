---
title: Microsoft Intune의 iOS/iPadOS 디바이스 기능 설정 - Azure | Microsoft Docs
description: Microsoft Intune에서 AirPrint, 홈 화면의 레이아웃, 앱 알림, 공유 디바이스, SSO(Single Sign-On) 및 웹 콘텐츠 필터 설정에 대한 iOS/iPadOS 디바이스를 구성하는 모든 설정을 확인합니다. 디바이스 구성 프로필에서 이러한 설정을 확인하여 조직에서 이러한 Apple 기능을 사용하도록 iOS/iPadOS 디바이스를 구성합니다.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/09/2020
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: ''
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 351c6ade59d98ce620b939c5ff6238e650390a5f
ms.sourcegitcommit: 3d895be2844bda2177c2c85dc2f09612a1be5490
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79361083"
---
# <a name="ios-and-ipados-device-settings-to-use-common-iosipados-features-in-intune"></a>Intune에서 일반적인 iOS/iPadOS 기능을 사용하는 iOS 및 iPadOS 디바이스 설정

Intune은 iOS/iPadOS 사용자가 해당 디바이스의 다른 Apple 기능을 사용하도록 허용하는 몇 가지 기본 제공 설정을 포함합니다. 예를 들어, 관리자는 iOS/iPadOS 사용자가 AirPrint 프린터를 사용하고, 홈 화면의 도킹 및 페이지에 앱 및 폴더를 추가하고, 앱 알림을 표시하고, 잠금 화면에서 자산 태그 정보를 표시하고, SSO(Single Sign-On) 인증을 사용하고, 인증서를 사용하여 사용자를 인증하는 방법을 제어할 수 있습니다.

이러한 기능을 사용하여 MDM(모바일 디바이스 관리) 솔루션의 일부로 iOS/iPadOS 디바이스를 제어합니다.

이 문서에서는 이러한 설정을 나열하고, 각 설정이 수행하는 작업을 설명합니다. 이러한 기능에 대한 자세한 내용은 [iOS/iPadOS 또는 macOS 디바이스 기능 설정 추가](device-features-configure.md)를 참조하세요.

## <a name="before-you-begin"></a>시작하기 전에

[iOS/iPadOS 디바이스 구성 프로필을 만듭니다](device-features-configure.md).

> [!NOTE]
> 이러한 설정은 여러 등록 유형에 적용되며, 일부 설정은 모든 등록 옵션에 적용됩니다. 여러 등록 유형에 대한 자세한 내용은 [iOS/iPadOS 등록](../enrollment/ios-enroll.md)을 참조하세요.

## <a name="airprint"></a>AirPrint

### <a name="settings-apply-to-all-enrollment-types"></a>설정 적용 대상: 모든 등록 유형

> [!NOTE]
> 모든 프린터를 동일한 프로필에 추가해야 합니다. Apple에서는 여러 개의 AirPrint 프로필이 동일한 디바이스를 대상으로 하는 것을 방지합니다.

- **IP 주소**: 프린터의 IPv4 또는 IPv6 주소를 입력합니다. 호스트 이름을 사용하여 프린터를 식별하는 경우 터미널에서 프린터를 ping하여 IP 주소를 가져올 수 있습니다. IP 주소 및 경로 가져오기(이 문서)에서 자세한 정보를 제공합니다.
- **경로**: 네트워크의 프린터에 대한 경로는 일반적으로 `ipp/print`입니다. IP 주소 및 경로 가져오기(이 문서)에서 자세한 정보를 제공합니다.
- **포트**: AirPrint 대상의 수신 대기 포트를 입력합니다. 이 속성을 비워두면 AirPrint는 기본 포트를 사용합니다. iOS 11.0 이상 및 iPadOS 13.0 이상에서 사용할 수 있습니다.
- **TLS**: TLS(전송 계층 보안)를 사용하여 AirPrint 연결을 보호하려면 **사용**을 선택합니다. iOS 11.0 이상 및 iPadOS 13.0 이상에서 사용할 수 있습니다.

AirPrint 서버를 추가하려면 다음을 수행합니다.

- **추가**를 선택하면 목록에 AirPrint 서버가 추가됩니다. 많은 AirPrint 서버를 추가할 수 있습니다.
- 이 정보를 사용하여 쉼표로 구분된 파일(.csv)을 **가져옵니다**. 또는 **내보내기**를 실행하여 추가한 AirPrint 서버의 목록을 만듭니다.

### <a name="get-server-ip-address-resource-path-and-port"></a>서버 IP 주소, 리소스 경로 및 포트 가져오기

AirPrinter 서버를 추가하려면 프린터의 IP 주소, 리소스 경로 및 포트가 필요합니다. 다음 단계에서는 이 정보를 가져오는 방법을 보여줍니다.

1. AirPrint 프린터와 동일한 로컬 네트워크(서브넷)에 연결된 Mac에서 **터미널**을 엽니다( **/Applications/Utilities**).
2. 터미널에서 `ippfind`을 입력하고 enter를 선택합니다.

    프린터 정보를 기록합니다. 예를 들어 `ipp://myprinter.local.:631/ipp/port1`과 유사한 항목을 반환할 수 있습니다. 첫 번째 부분은 프린터의 이름입니다. 마지막 부분(`ipp/port1`)은 리소스 경로입니다.

3. 터미널에서 `ping myprinter.local`을 입력하고 enter를 선택합니다.

   IP 주소를 기록합니다. 예를 들어 `PING myprinter.local (10.50.25.21)`과 유사한 항목을 반환할 수 있습니다.

4. IP 주소 및 리소스 경로 값을 사용합니다. 이 예제에서 IP 주소는 `10.50.25.21`이고, 리소스 경로는 `/ipp/port1`입니다.

## <a name="home-screen-layout"></a>홈 화면 레이아웃

이 기능은 다음에 적용됩니다.

- iOS 9.3 또는 이후 버전
- iPadOS 13.0 이상

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>설정 적용 대상: 자동 디바이스 등록(감독됨)

### <a name="dock"></a>도킹

**도킹** 설정을 사용하여 iOS/iPadOS 화면의 도킹에 최대 6개의 항목 또는 폴더를 추가합니다. 많은 디바이스는 적은 수의 항목을 지원합니다. 예를 들어 iPhone 디바이스는 최대 4개의 항목을 지원합니다. 이 경우 추가하는 처음 4개 항목만 디바이스에 표시됩니다.

디바이스 도킹에 최대 **6**개의 항목(결합된 앱 및 폴더)을 추가할 수 있습니다.

- **추가**: 디바이스의 도크에 앱 또는 폴더를 추가합니다.
- **형식**: **앱** 또는 **폴더** 추가를 입력합니다.

  - **앱**: 이 옵션을 선택하여 화면의 도킹에 앱을 추가합니다. 다음을 입력합니다.

    - **앱 이름**: 앱의 이름을 입력합니다. 이 이름은 Microsoft Endpoint Manager 관리 센터의 참조에 사용됩니다. iOS/iPadOS 디바이스에 표시되지 *않습니다*.
    - **앱 번들 ID**: 앱의 번들 ID를 입력합니다. 일부 예제는 [기본 제공 iOS/iPadOS 앱에 대한 번들 ID](bundle-ids-built-in-ios-apps.md)를 참조하세요.

  - **폴더**: 이 옵션을 선택하여 화면의 도킹에 폴더를 추가합니다.

    폴더에서 페이지에 추가하는 앱은 목록과 동일한 순서대로 왼쪽에서 오른쪽으로 정렬됩니다. 한 페이지에 들어가는 개수보다 많은 앱을 추가할 경우 앱이 다른 페이지로 이동합니다.

    - **폴더 이름**: 폴더의 이름을 입력합니다. 이 이름은 해당 디바이스에서 사용자에게 표시됩니다.
    - **페이지 목록**: 페이지를 **추가**하고 다음 속성을 입력합니다.

      - **페이지 이름**: 페이지의 이름을 입력합니다. 이 이름은 Microsoft Endpoint Manager 관리 센터의 참조에 사용됩니다. iOS/iPadOS 디바이스에 표시되지 *않습니다*.
      - **앱 이름**: 앱의 이름을 입력합니다. 이 이름은 Microsoft Endpoint Manager 관리 센터의 참조에 사용됩니다. iOS/iPadOS 디바이스에 표시되지 *않습니다*.
      - **앱 번들 ID**: 앱의 번들 ID를 입력합니다. 일부 예제는 [기본 제공 iOS/iPadOS 앱에 대한 번들 ID](bundle-ids-built-in-ios-apps.md)를 참조하세요.

      디바이스 도킹에 최대 **20**개의 페이지를 추가할 수 있습니다.

> [!NOTE]
> Dock 설정을 사용하여 아이콘을 추가하면 홈 화면과 페이지의 아이콘이 잠기므로 이동할 수 없습니다. 이는 iOS/iPadOS 및 Apple의 MDM 정책으로 설계된 것일 수 있습니다.

#### <a name="example"></a>예제

다음 예제에서 도킹 화면은 Safari, Mail 및 Stocks 앱만 표시합니다. 해당 속성을 표시하도록 Mail 앱이 선택되었습니다.

![샘플 iOS/iPadOS 도킹 설정](./media/ios-device-features-settings/FfFiUcP.png)

iPhone에 정책을 할당할 때 도킹은 다음 이미지와 유사합니다.

![iPhone의 샘플 iOS/iPadOS 레이아웃 도킹](./media/ios-device-features-settings/bAgCe8F.png)

### <a name="pages"></a>페이지

홈 화면에 표시할 페이지와 각 페이지에 표시할 앱을 추가합니다. 페이지에 추가하는 앱은 목록과 동일한 순서대로 왼쪽에서 오른쪽으로 정렬됩니다. 한 페이지에 들어가는 개수보다 많은 앱을 추가할 경우 앱이 다른 페이지로 이동합니다.

> [!TIP]
> 홈 화면과 페이지 목록의 항목을 다시 정렬하기 위해 항목을 끌어서 놓을 수 있습니다.

디바이스에 최대 **40**개의 페이지를 추가할 수 있습니다.

- **페이지 목록**: 페이지를 **추가**하고 다음 속성을 입력합니다.

  - **페이지 이름**: 페이지의 이름을 입력합니다. 이 이름은 Microsoft Endpoint Manager 관리 센터의 참조에 사용되며 iOS/iPadOS 디바이스에는 표시되지 *않습니다*.

  디바이스에 최대 **60**개의 항목(결합된 앱 및 폴더)을 추가할 수 있습니다.

  - **추가**: 디바이스의 페이지에 앱 또는 폴더를 추가합니다.

    - **형식**: **앱** 또는 **폴더** 추가를 입력합니다.

      - **앱**: 이 옵션을 선택하여 화면의 페이지에 앱을 추가합니다. 또한 다음을 입력합니다.

        - **앱 이름**: 앱의 이름을 입력합니다. 이 이름은 Microsoft Endpoint Manager 관리 센터의 참조에 사용됩니다. iOS/iPadOS 디바이스에 표시되지 *않습니다*.
        - **앱 번들 ID**: 앱의 번들 ID를 입력합니다. 일부 예제는 [기본 제공 iOS/iPadOS 앱에 대한 번들 ID](bundle-ids-built-in-ios-apps.md)를 참조하세요.

      - **폴더**: 이 옵션을 선택하여 화면의 도킹에 폴더를 추가합니다.

        폴더에서 페이지에 추가하는 앱은 목록과 동일한 순서대로 왼쪽에서 오른쪽으로 정렬됩니다. 한 페이지에 들어가는 개수보다 많은 앱을 추가할 경우 앱이 다른 페이지로 이동합니다.

        - **폴더 이름**: 폴더의 이름을 입력합니다. 이 이름은 디바이스의 사용자에게 표시됩니다.
        - **추가**: 폴더에 페이지를 추가합니다. 다음 속성도 입력합니다.

          - **페이지 이름**: 페이지의 이름을 입력합니다. 이 이름은 Microsoft Endpoint Manager 관리 센터의 참조에 사용됩니다. iOS/iPadOS 디바이스에 표시되지 *않습니다*.
          - **앱 이름**: 앱의 이름을 입력합니다. 이 이름은 Microsoft Endpoint Manager 관리 센터의 참조에 사용됩니다. iOS/iPadOS 디바이스에 표시되지 *않습니다*.
          - **앱 번들 ID**: 앱의 번들 ID를 입력합니다. 일부 예제는 [기본 제공 iOS/iPadOS 앱에 대한 번들 ID](bundle-ids-built-in-ios-apps.md)를 참조하세요.

#### <a name="example"></a>예제

다음 예제에서 **Contoso**라는 새 페이지가 추가됩니다. 페이지는 친구 찾기와 설정 앱을 표시합니다. 해당 속성을 표시하도록 설정 앱이 선택되었습니다.

![Intune의 iOS/iPadOS 홈 화면 설정 예제](./media/ios-device-features-settings/Jc2OxyX.png)

iPhone에 정책을 할당할 때 페이지는 다음 이미지와 유사합니다.

![Intune에서 수정된 홈 화면을 사용하는 iOS/iPadOS 디바이스](./media/ios-device-features-settings/Bd37PHa.png)

## <a name="app-notifications"></a>앱 알림

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>설정 적용 대상: 자동 디바이스 등록(감독됨)

- **추가**: 앱에 대한 알림을 추가합니다.

    ![Intune의 iOS/iPadOS 프로필에서 앱 알림 추가](./media/ios-device-features-settings/ios-macos-app-notifications.png)

  - **앱 번들 ID**: 추가할 앱의 **앱 번들 ID**를 입력합니다. 일부 예제는 [기본 제공 iOS/iPadOS 앱에 대한 번들 ID](bundle-ids-built-in-ios-apps.md)를 참조하세요.
  - **앱 이름**: 추가하려는 앱의 이름을 입력합니다. 이 이름은 Microsoft Endpoint Manager 관리 센터의 참조에 사용됩니다. 디바이스에 표시되지 *않습니다*.
  - **게시자**: 추가하는 앱의 게시자를 입력합니다. 이 이름은 Microsoft Endpoint Manager 관리 센터의 참조에 사용됩니다. 디바이스에 표시되지 *않습니다*.
  - **알림**: 앱에서 디바이스에 알림을 보내는 작업을 **사용하도록 설정**하거나, **사용하지 않도록 설정**합니다.
    - **알림 센터에 표시**: 디바이스 알림 센터에서 알림을 표시하도록 앱을 허용하려면 **사용하도록 설정**합니다. **사용하지 않도록 설정**은 앱이 알림 센터에서 알림을 표시하지 못하도록 방지합니다.
    - **잠금 화면에 표시**: 디바이스 잠금 화면에 앱의 알림을 표시하려면 **사용하도록 설정**을 선택합니다. **사용하지 않도록 설정**은 앱이 잠금 화면에 알림을 표시하지 못하도록 방지합니다.
    - **경고 유형**: 디바이스가 잠금 해제되면 알림이 표시되는 방식을 선택합니다. 옵션은 다음과 같습니다.
      - **없음**: 알림이 표시되지 않습니다.
      - **배너**: 배너는 알림과 함께 간단하게 표시됩니다.
      - **모달**: 알림이 표시되고 사용자는 디바이스를 계속 사용하기 전에 수동으로 알림을 해제해야 합니다.
    - **앱 아이콘 배지**: 앱 아이콘에 배지를 추가하려면 **사용하도록 설정**을 선택합니다. 배지는 앱이 알림을 전송했음을 의미합니다.
    - **소리**: 알림이 전달될 때 소리를 재생하려면 **사용하도록 설정**을 선택합니다.

## <a name="lock-screen-message"></a>잠금 화면 메시지

이 기능은 다음에 적용됩니다.

- iOS 9.3 이상
- iPadOS 13.0 이상

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>설정 적용 대상: 자동 디바이스 등록(감독됨)

- **자산 태그 정보**: 디바이스의 자산 태그에 대한 정보를 입력합니다. 예를 들어 `Owned by Contoso Corp` 또는 `Serial Number: {{serialnumber}}`을 입력합니다.

  입력한 텍스트는 디바이스의 로그인 창 및 잠금 화면에 표시됩니다.

- **잠금 화면 각주**: 디바이스를 분실했거나 도난당한 경우 디바이스를 되찾는 데 도움이 되는 정보를 입력합니다. 원하는 텍스트를 입력할 수 있습니다. 예를 들어 `If found, call Contoso at ...`와 같이 입력합니다.

  디바이스 토큰은 디바이스별 정보를 이러한 필드에 추가하는 데도 사용할 수 있습니다. 예를 들어 일련 번호를 표시하려면 `Serial Number: {{serialnumber}}`를 입력합니다. 잠금 화면에서 텍스트는 `Serial Number 123456789ABC`와 비슷하게 표시됩니다. 변수를 입력할 때 `{{ }}` 중괄호를 사용해야 합니다. [앱 구성 토큰](../apps/app-configuration-policies-use-ios.md#tokens-used-in-the-property-list)에는 사용할 수 있는 변수 목록이 포함됩니다. `deviceName` 또는 기타 디바이스 관련 값을 사용할 수도 있습니다.

  > [!NOTE]
  > 변수는 UI에서 유효성이 검사되지 않으며 대/소문자를 구분합니다. 따라서, 잘못된 입력으로 저장된 프로필을 볼 수 있습니다. 예를 들어 `{{deviceid}}` 대신 `{{DeviceID}}`를 입력하면 디바이스의 고유 ID 대신 리터럴 문자열이 표시될 수 있습니다. 올바른 정보를 입력해야 합니다.

## <a name="single-sign-on"></a>Single Sign-On

### <a name="settings-apply-to-device-enrollment-automated-device-enrollment-supervised"></a>설정 적용 대상: 디바이스 등록, 자동 디바이스 등록(감독됨)

- **AAD의 사용자 이름 특성**: Intune은 Azure AD에서 각 사용자에 대해 이 특성을 찾습니다. 그런 다음, Intune이 디바이스에 설치되는 XML을 생성하기 전에 해당 필드(예: UPN)를 채웁니다. 옵션은 다음과 같습니다.

  - **사용자 계정 이름**: UPN은 다음과 같은 방법으로 구문 분석됩니다.

    ![Intune의 iOS/iPadOS 사용자 이름 SSO 특성](./media/ios-device-features-settings/User-name-attribute.png)

    **영역** 텍스트 상자에 입력한 텍스트로 영역을 덮어쓸 수도 있습니다.

    예를 들어 Contoso는 유럽, 아시아 및 북아메리카를 포함하는 여러 지역이 있습니다. Contoso는 아시아 사용자가 SSO를 사용하길 원하며, 앱은 `username@asia.contoso.com` 형식의 UPN이 필요합니다. **사용자 계정 이름**을 선택하면 각 사용자의 영역이 Azure AD에서 검색되며, `contoso.com`입니다. 따라서 아시아 사용자의 경우 **사용자 계정 이름**을 선택하고, `asia.contoso.com`을 입력합니다. 최종 사용자의 UPN은 `username@contoso.com` 대신 `username@asia.contoso.com`이 됩니다.

  - **Intune 디바이스 ID**: Intune은 Intune 디바이스 ID를 자동으로 선택합니다.

    기본적으로 앱은 디바이스 ID만 사용해야 합니다. 그러나 앱이 영역 및 디바이스 ID를 사용하는 경우 영역 텍스트 상자에 영역을 입력할 수 있습니다.

    > [!NOTE]
    > 기본적으로 디바이스 ID를 사용하는 경우 영역을 비워 둡니다.

  - **Azure AD 디바이스 ID**

- **영역**: URL의 도메인 부분을 입력합니다. 예를 들어 다음과 같이 입력합니다. `contoso.com`
- **Single Sign-On을 사용할 URL 접두사**: 사용자 Single Sign-On 인증이 필요한 조직의 모든 URL을 **추가**합니다.

  예를 들어, 사용자가 이러한 사이트에 연결하는 경우, iOS/iPadOS 디바이스는 SSO(Single Sign-On) 자격 증명을 사용합니다. 사용자는 추가 자격 증명을 입력할 필요가 없습니다. 다단계 인증이 활성화된 경우 사용자는 두 번째 인증을 입력해야 합니다.

  > [!NOTE]
  > 이러한 URL은 올바른 형식의 FQDN이어야 합니다. Apple에서는 `http://<yourURL.domain>` 형식의 FQDN이어야 합니다.

  URL 일치 패턴은 `http://` 또는 `https://`로 시작해야 합니다. 단순 문자열 일치가 수행되므로 `http://www.contoso.com/` URL 접두사는 `http://www.contoso.com:80/`과 일치하지 않습니다. iOS 10.0 이상 및 iPadOS 13.0 이상의 버전에서는 단일 와일드카드 \*를 사용하여 일치하는 모든 값을 입력할 수 있습니다. 예를 들어 `http://*.contoso.com/`은 `http://store.contoso.com/` 및 `http://www.contoso.com` 둘 다와 일치합니다.

  `http://.com` 및 `https://.com` 패턴은 각각 모든 HTTP 및 HTTPS URL과 일치합니다.

- **Single Sign-On을 사용할 앱**: Single Sign-On을 사용할 수 있는 최종 사용자 디바이스에서 앱을 **추가**합니다.

  `AppIdentifierMatches` 배열에는 앱 번들 ID와 일치하는 문자열이 포함되어야 합니다. 이러한 문자열은 정확히 일치하는 항목(예: `com.contoso.myapp`)이거나, \* 와일드카드 문자를 사용하여 번들 ID의 접두사 일치를 입력할 수 있습니다. 와일드카드 문자는 마침표 문자(.) 뒤에 표시되어야 하며, 문자열의 끝에 한 번만 나타날 수 있습니다(예: `com.contoso.*`). 와일드카드가 포함되면 번들 ID가 접두사로 시작하는 모든 앱에 계정에 대한 액세스 권한이 부여됩니다.

  **앱 이름**을 사용하여 번들 ID를 식별할 수 있도록 친숙한 이름을 입력합니다.

- **자격 증명 갱신 인증서**: 인증에 인증서를 사용하는 경우(암호 아님) 인증 인증서로 기존 SCEP 또는 PFX 인증서를 선택합니다. 일반적으로 이 인증서는 VPN, Wi-Fi, 이메일 등의 다른 프로필에 대해 사용자에게 배포되는 것과 동일한 인증서입니다.

## <a name="web-content-filter"></a>웹 콘텐츠 필터

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>설정 적용 대상: 자동 디바이스 등록(감독됨)

- **필터 형식**: 특정 웹 사이트를 허용하도록 선택합니다. 옵션은 다음과 같습니다.

  - **URL 구성**: 불경한 언어 및 성적으로 노골적인 언어를 포함하는 성인 용어를 검색하는 Apple의 기본 제공 웹 필터를 사용합니다. 이 기능은 로드되는 각 웹 페이지를 평가하고, 부적절한 콘텐츠를 식별하고 차단합니다. 또한 필터로 검사하지 않으려는 URL을 추가할 수도 있습니다. 또는 Apple의 필터 설정에 관계없이 특정 URL을 차단합니다.

    - **허용된 URL**: 허용하려는 URL을 **추가**합니다. 이러한 URL은 Apple 웹 필터를 무시합니다.

        > [!NOTE]
        > 입력하는 URL은 Apple 웹 필터에서 평가하지 않으려는 URL입니다. 이러한 URL은 허용되는 웹 사이트 목록이 아닙니다. 허용되는 웹 사이트 목록을 만들려면 **필터 형식**을 **특정 웹 사이트만**으로 설정합니다.

    - **차단된 URL**: Apple 웹 필터 설정에 관계없이 열기를 중지하려는 URL을 **추가**합니다.

  - **특정 웹 사이트만**(Safari 웹 브라우저만 해당): 이러한 URL은 Safari 브라우저의 책갈피에 추가됩니다. 사용자는 이 사이트**만** 방문이 허용됩니다. 다른 사이트를 열 수 없습니다. 사용자가 액세스할 수 있는 URL의 정확한 목록을 알고 있는 경우에만 이 옵션을 사용합니다.

    - **URL**: 허용하려는 웹 사이트의 URL을 입력합니다. 예를 들어 다음과 같이 입력합니다. `https://www.contoso.com`
    - **책갈피 경로**: Apple에서 이 설정을 변경했습니다. 모든 책갈피는 **승인된 사이트** 폴더로 이동합니다. 책갈피는 입력하는 책갈피 경로로 이동하지 않습니다.
    - **제목**: 책갈피에 대한 설명이 포함된 제목을 입력합니다.

    URL을 입력하지 않는 경우 최종 사용자는 `microsoft.com`, `microsoft.net` 및 `apple.com`을 제외한 웹 사이트에 액세스할 수 없습니다. 이러한 URL은 Intune에서 자동으로 허용됩니다.

## <a name="single-sign-on-app-extension"></a>Single Sign-On 앱 확장

이 기능은 다음에 적용됩니다.

- iOS 13.0 이상
- iPadOS 13.0 이상

### <a name="settings-apply-to-all-enrollment-types"></a>설정 적용 대상: 모든 등록 유형

- **SSO 앱 확장 유형**: SSO 앱 확장의 유형을 선택합니다. 옵션은 다음과 같습니다.

  - **구성되지 않음** 앱 확장이 사용되지 않습니다. 앱 확장을 사용하지 않도록 설정하려면 SSO 앱 확장 유형을 **구성되지 않음**으로 전환합니다.
  - **리디렉션**: 최신 인증 흐름을 사용하여 SSO를 수행하기 위해 일반 사용자 지정 가능 리디렉션 앱 확장을 사용합니다. 조직의 앱 확장에 대한 확장 ID를 알고 있어야 합니다.
  - **자격 증명**: 사용자 지정 가능한 일반 자격 증명 앱 확장을 사용하여 시도 및 응답 인증 흐름으로 SSO를 수행합니다. 조직의 앱 확장에 대한 확장 ID를 알고 있어야 합니다.
  - **Kerberos**: iOS 13.0 이상 및 iPadOS 13.0 이상의 버전에 포함된 Apple의 기본 제공 Kerberos 확장을 사용합니다. 이 옵션은 **자격 증명** 앱 확장의 Kerberos 관련 버전에 속합니다.

  > [!TIP]
  > **리디렉션** 및 **자격 증명** 형식을 사용하여 확장을 통과하는 고유한 구성 값을 추가합니다. **자격 증명**을 사용하는 경우에는 **Kerberos** 유형에서 Apple이 제공하는 기본 구성 설정을 사용하는 것이 좋습니다.

- **확장 ID**(리디렉션 및 자격 증명): `com.apple.extensiblesso`과 같은 SSO 앱 확장을 식별하는 번들 식별자를 입력합니다.

- **팀 ID**(리디렉션 및 자격 증명): SSO 앱 확장의 팀 식별자를 입력합니다. 팀 식별자는 Apple에서 생성된 10자의 영숫자(숫자 및 문자) 문자열입니다(예: `ABCDE12345`). 팀 ID는 필요하지 않습니다.

  자세한 내용은 [팀 ID 찾기](https://help.apple.com/developer-account/#/dev55c3c710c)(Apple의 웹 사이트가 열림)를 참조하세요.

- **영역**(자격 증명 및 Kerberos): 인증 영역의 이름을 입력합니다. 영역 이름은 대문자여야 합니다(예: `CONTOSO.COM`). 일반적으로 영역 이름은 DNS 도메인 이름과 동일하지만 모두 대문자로 되어 있습니다.

- **도메인**(자격 증명 및 Kerberos): SSO를 통해 인증할 수 있는 사이트의 도메인 또는 호스트 이름을 입력합니다. 예를 들어, 웹 사이트가 `mysite.contoso.com`인 경우 `mysite`는 호스트 이름에 해당되며 `contoso.com`은 도메인 이름에 해당됩니다. 사용자가 이러한 사이트에 연결하면 앱 확장은 인증 질문을 처리합니다. 이 인증을 사용하면 Face ID, Touch ID 또는 Apple PIN 코드/암호를 사용하여 로그인할 수 있습니다.

  - SSO(Single Sign-On) 앱 확장 Intune 프로필의 모든 도메인은 고유해야 합니다. 다른 유형의 SSO 앱 확장을 사용 중인 경우에도 로그온 앱 확장 프로필에서 도메인을 반복할 수 없습니다.
  - 이러한 도메인은 대/소문자를 구분하지 않습니다.

- **URL**(리디렉션만 해당): 리디렉션 앱 확장이 SSO를 대신 수행하는 ID 공급자의 URL 접두사를 입력합니다. 사용자가 이러한 URL로 리디렉션되면 SSO 앱 확장이 개입하여 SSO를 요청합니다.

  - Intune SSO(Single Sign-On) 앱 확장 프로필의 모든 URL은 고유해야 합니다. 다른 유형의 SSO 앱 확장을 사용 중인 경우에도 SSO 앱 확장 프로필에서 도메인을 반복할 수 없습니다.
  - URL은 http://또는 https://로 시작해야 합니다.

- **추가 구성**(리디렉션 및 자격 증명): SSO 앱 확장에 전달할 추가 확장 관련 데이터를 입력합니다.
  - **키**: 추가하려는 항목의 이름을 입력합니다(예: `user name`).
  - **형식**: 데이터 형식을 입력합니다. 옵션은 다음과 같습니다.

    - 문자열
    - 부울: **구성 값**에 `True` 또는 `False`를 입력합니다.
    - 정수: **구성 값**에 숫자를 입력합니다.
    
  - **값**: 데이터를 입력합니다.

  - **추가**: 구성 키를 추가하려면 선택합니다.

- **키 집합 사용**(Kerberos만 해당): 암호를 키 집합에 저장 및 보관하지 못하도록 하려면 **차단**을 선택합니다. 차단된 경우 사용자에게 암호를 저장하라는 메시지가 표시되지 않으며 Kerberos 티켓이 만료되는 경우 암호를 다시 입력해야 합니다. **구성되지 않음**(기본값)을 선택하면 암호를 키 집합에 저장 및 보관할 수 있습니다. 티켓이 만료되면 사용자에게 암호를 다시 입력하라는 메시지가 표시되지 않습니다.
- **Face ID, Touch ID 또는 암호**(Kerberos만 해당): **필수**를 선택하면 Kerberos 티켓을 새로 고치기 위해 자격 증명이 필요할 때 사용자가 Face ID, Touch ID 또는 디바이스 암호를 입력해야 합니다. **구성되지 않음**(기본값)을 선택하면 사용자는 생체 인식 또는 디바이스 암호를 사용하여 Kerberos 티켓을 새로 고칠 필요가 없습니다. **키 집합 사용**이 차단되면 이 설정이 적용되지 않습니다.
- **기본 영역**(Kerberos만 해당): **사용**을 선택하여 기본 영역으로 입력한 **영역** 값을 설정합니다. **구성되지 않음**(기본값)은 기본 영역을 설정하지 않습니다.

  > [!TIP]
  > - 조직에서 여러 Kerberos SSO 앱 확장을 구성하는 경우, 이 설정을 **사용**합니다.
  > - 여러 영역을 사용하는 경우, 이 설정을 **사용**합니다. 기본 영역으로 입력한 **영역** 값을 설정합니다.
  > - 영역이 하나만 있는 경우에는 **구성되지 않음**(기본값)으로 둡니다.

- **보안 주체 이름**(Kerberos만 해당): Kerberos 보안 주체의 사용자 이름을 입력합니다. 영역 이름을 포함할 필요가 없습니다. 예를 들어, `user@contoso.com`에서 `user`는 보안 주체 이름이며 `contoso.com`은 영역 이름입니다.

  > [!TIP]
  > - 중괄호 `{{ }}`를 입력하여 보안 주체 이름에 변수를 사용할 수도 있습니다. 예를 들어, 사용자 이름을 표시하려면 `Username: {{username}}`을 입력합니다. 
  > - 그러나 변수는 UI에서 유효성이 검사되지 않으며 대/소문자를 구분하기 때문에 변수를 대체할 때에는 주의해야 합니다. 올바른 정보를 입력해야 합니다.

- **Active Directory 사이트 코드**(Kerberos만 해당): Kerberos 확장에서 사용해야 하는 Active Directory 사이트의 이름을 입력합니다. Kerberos 확장에서 Active Directory 사이트 코드를 자동으로 찾을 수 있으므로 이 값을 변경하지 않아도 됩니다.
- **캐시 이름**(Kerberos만 해당): Kerberos 캐시의 GSS(Generic Security Services) 이름을 입력합니다. 대개의 경우, 이 값은 설정하지 않아도 됩니다.
- **앱 번들 ID**(Kerberos만 해당): 디바이스에서 SSO(Single Sign-On)를 사용해야 하는 앱 번들 식별자를 **추가**합니다. 이러한 앱은 Kerberos TGT(Ticket Granting Ticket)라는 인증 티켓에 대한 액세스 권한이 부여되며, 액세스할 수 있는 서비스에 대한 사용자를 인증합니다.
- **도메인 영역 매핑**(Kerberos만 해당): 영역에 매핑해야 하는 도메인 DNS 접미사를 **추가**합니다. 호스트의 DNS 이름이 영역 이름과 일치하지 않는 경우, 이 설정을 사용합니다. 대개의 경우, 이러한 사용자 지정 도메인-영역 매핑을 만들 필요가 없습니다.
- **PKINIT 인증서**(Kerberos만 해당): Kerberos 인증에 사용할 수 있는 초기 인증용 퍼블릭 키 암호(PKINIT) 인증서를 **선택**합니다. Intune에서 추가한 [PKCS](../protect/certficates-pfx-configure.md) 또는 [SCEP](../protect/certificates-scep-configure.md) 인증서를 선택할 수 있습니다. 인증서에 대한 자세한 내용은 [Microsoft Intune의 인증에 인증서 사용](../protect/certificates-configure.md)을 참조하세요.

## <a name="wallpaper"></a>배경 무늬

이미지가 없는 프로필을 기존 이미지가 있는 디바이스에 할당하면 예기치 않은 동작이 발생할 수 있습니다. 예를 들어 이미지가 없는 프로필을 만듭니다. 이 프로필이 이미지가 이미 있는 디바이스에 할당됩니다. 이 시나리오에서는 이미지가 디바이스 기본값으로 변경되거나 원래 이미지가 디바이스에 남아있을 수 있습니다. 이런 동작은 Apple의 MDM 플랫폼에 의해 제어되고 제한됩니다.

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>설정 적용 대상: 자동 디바이스 등록(감독됨)

- **배경 무늬 표시 위치**: 이미지를 표시할 디바이스의 위치를 선택합니다. 옵션은 다음과 같습니다.
  - **구성되지 않음** 사용자 지정 이미지는 디바이스에 추가되지 않습니다. 디바이스는 운영 체제 기본값을 사용합니다.
  - **잠금 화면**: 잠금 화면에 이미지를 추가합니다.
  - **홈 화면**: 홈 화면에 이미지를 추가합니다.
  - **잠금 화면 및 홈 화면**: 잠금 화면 및 홈 화면에 동일한 이미지를 사용합니다.
- **배경 무늬 이미지**: 사용하려는 기존 .png, .jpg 또는 .jpeg 이미지를 업로드합니다. 파일 크기는 750KB 미만이어야 합니다. 추가한 이미지를 **제거**할 수도 있습니다.

> [!TIP]
> 잠금 화면 및 홈 화면에 다른 이미지를 표시하려면 잠금 화면 이미지를 사용하여 프로필을 만듭니다. 홈 화면 이미지를 사용하여 다른 프로필을 만듭니다. iOS/iPadOS 사용자 또는 디바이스 그룹에 두 프로필을 모두 할당합니다.

## <a name="next-steps"></a>다음 단계

[프로필을 할당](device-profile-assign.md)하고, 해당 [상태를 모니터링](device-profile-monitor.md)합니다.

[macOS](macos-device-features-settings.md) 디바이스에 대한 디바이스 기능 프로필을 만들 수도 있습니다.
