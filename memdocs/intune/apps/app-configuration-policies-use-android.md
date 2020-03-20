---
title: 관리되는 Android 엔터프라이즈 디바이스용 앱 구성 정책 추가
titleSuffix: Microsoft Intune
description: Microsoft Intune에서 앱 구성 정책을 사용하여 사용자가 관리되는 Google Play 앱을 실행할 때 설정을 제공할 수 있습니다.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 02/28/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: d0b6f3fe-2bd4-4518-a6fe-b9fd115ed5e0
ms.reviewer: chrisbal
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: f49d1e419eb7199d2a7cf20f03959689a5f5fa44
ms.sourcegitcommit: 3d895be2844bda2177c2c85dc2f09612a1be5490
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79342493"
---
# <a name="add-app-configuration-policies-for-managed-android-enterprise-devices"></a>관리되는 Android 엔터프라이즈 디바이스용 앱 구성 정책 추가

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Microsoft Intune의 앱 구성 정책은 관리되는 Android 엔터프라이즈 디바이스에서 관리되는 Google Play 앱에 대한 설정을 제공합니다. 앱 개발자는 Android에서 관리되는 앱 구성 설정을 노출합니다. Intune은 이러한 노출된 설정을 사용하여 관리자가 앱에 대한 기능을 구성할 수 있도록 합니다. 앱 구성 정책은 사용자 그룹에 할당됩니다. 정책 설정은 앱에서 해당 설정을 확인할 때(일반적으로는 앱을 처음 실행할 때) 사용됩니다.

> [!NOTE]  
> 모든 앱이 앱 구성을 지원하지는 않습니다. 앱에서 앱 구성 정책을 지원하는지 앱 개발자와 함께 확인하세요.

1. [Microsoft Endpoint Manager 관리 센터](https://go.microsoft.com/fwlink/?linkid=2109431)에 로그인합니다.
2. **앱** > **앱 구성 정책** > **추가** > **관리 디바이스**를 선택합니다. **관리되는 디바이스**와 **관리되는 앱** 중에서 선택할 수 있습니다. 자세한 내용은 [앱 구성을 지원하는 애플리케이션](app-configuration-policies-overview.md#apps-that-support-app-configuration)을 참조하세요.
3. **기본 사항** 페이지에서 다음 세부 정보를 설정합니다.
    - **이름** - Azure Portal에 표시되는 프로필의 이름입니다.
    - **설명** - Azure Portal에 표시되는 프로필의 설명입니다.
    - **디바이스 등록 유형** - 설정이 **관리 디바이스**여야 합니다.
4. **Android Enterprise**를 **플랫폼**으로 선택합니다.
5. **대상 앱** 옆의 **앱 선택**을 클릭합니다. **연결된 앱** 창이 표시됩니다. 
6. **연결된 앱** 창에서 구성 정책에 연결할 관리되는 앱을 선택하고 **확인**을 클릭합니다.
7. **다음**을 클릭하여 **설정** 페이지를 표시합니다.
8. **추가**를 클릭하여 **권한 추가** 창을 표시합니다.
9. 재정의하려는 권한을 클릭합니다. 부여되는 권한은 선택한 앱의 "기본 앱 권한" 정책을 재정의합니다.
10. 각 권한의 **권한 상태**를 설정합니다. **프롬프트**, **자동 부여** 또는 **자동 거부** 중에서 선택할 수 있습니다. 권한에 대한 자세한 내용은 [Intune을 사용하여 디바이스를 규격 또는 비규격으로 표시하는 Android Enterprise 설정](../protect/compliance-policy-create-android-for-work.md)을 참조하세요.
11. 드롭다운 상자에서 **구성 설정 형식**을 선택합니다. 다음 방법 중 하나를 선택하여 구성 정보를 추가합니다.
    - **구성 디자이너 사용**
    - **JSON 데이터 입력**<br><br>
    구성 디자이너 사용에 대한 자세한 내용은 [구성 디자이너 사용](#use-the-configuration-designer)을 참조하세요. XML 데이터 입력에 대한 자세한 내용은 [JSON 데이터 입력](#enter-json-data)을 참조하세요.
12. **다음**을 클릭하여 **할당** 페이지를 표시합니다.
13. **할당 대상** 옆의 드롭다운 상자에서 **선택한 그룹**, **모든 사용자**, **모든 디바이스** 또는 **모든 사용자 및 모든 디바이스** 중 앱 구성 정책을 할당할 대상을 선택합니다.

    ![정책 할당 포함 탭의 스크린샷](./media/app-configuration-policies-use-ios/app-config-policy01.png)

14. 드롭다운 상자에서 **모든 사용자**를 선택합니다.

    ![정책 할당의 스크린샷 - 모든 사용자 드롭다운 옵션](./media/app-configuration-policies-use-ios/app-config-policy02.png)

15. **제외할 그룹 선택**을 클릭하여 관련 창을 표시합니다.

    ![정책 할당의 스크린샷 - 제외할 그룹 선택 창](./media/app-configuration-policies-use-ios/app-config-policy03.png)

16. 제외하려는 그룹을 클릭한 다음, **선택**을 클릭합니다.

    >[!NOTE]
    >그룹을 추가할 때 주어진 할당 유형에 이미 다른 그룹이 포함되어 있으면 다른 포함 할당 유형에 대해 사전 선택되며 변경할 수 없습니다. 따라서 사용된 해당 그룹은 제외된 그룹으로 사용할 수 없습니다.

17. **다음**를 클릭하여 **검토 + 만들기** 페이지를 표시합니다.
18. **만들기**를 클릭하여 앱 구성 정책을 Intune에 추가합니다.

## <a name="use-the-configuration-designer"></a>구성 디자이너 사용

앱이 구성 설정을 지원하도록 디자인된 경우 관리되는 Google Play 앱에 구성 디자이너를 사용할 수 있습니다. 구성은 Intune에 등록된 디바이스에 적용됩니다. 디자이너를 사용하면 앱이 공개하는 설정에 대한 특정 구성 값을 구성할 수 있습니다.

1. **추가**를 선택합니다. 앱에 대해 입력하려는 구성 설정 목록을 선택합니다.

    이메일 앱에 GMail 또는 Nine Work을 사용하는 경우 이러한 설정에 대한 자세한 내용은 [이메일 구성을 위한 Android 엔터프라이즈 디바이스 설정](../configuration/email-settings-android-enterprise.md)을 참조하세요.

2. 구성의 각 키 및 값의 경우 다음을 설정합니다.

    - **값 형식**: 구성 값의 데이터 형식입니다. 문자열 값 형식의 경우 값 형식으로 변수 또는 인증서 프로필을 필요에 따라 선택할 수 있습니다.
    - **구성 값** 구성의 값입니다. **값 형식**에 대해 변수 또는 인증서를 선택하는 경우 변수 또는 인증서 프로필 목록에서 선택할 수 있습니다. 인증서를 선택하면 디바이스에 배포되는 인증서 별칭이 런타임 시 채워집니다.

### <a name="supported-variables-for-configuration-values"></a>구성 값에 대해 지원되는 변수

값 형식으로 변수를 선택하는 경우 다음 옵션을 선택할 수 있습니다.

| 옵션 | 예제 |
|----|----|
| AAD 디바이스 ID | dc0dc142-11d8-4b12-bfea-cae2a8514c82 |
| 계정 ID | fc0dc142-71d8-4b12-bbea-bae2a8514c81 |
| Intune 디바이스 ID | b9841cd9-9843-405f-be28-b2265c59ef97 |
| 도메인 | contoso.com |
| Mail | john@contoso.com |
| 부분 UPN | john |
| 사용자 ID | 3ec2c00f-b125-4519-acf0-302ac3761822 |
| 사용자 이름 | John Doe |
| 사용자 계정 이름 | john@contoso.com |

### <a name="allow-only-configured-organization-accounts-in-multi-identity-apps"></a>다중 ID 앱에서 구성된 조직 계정만 허용 

Android 디바이스의 경우 다음 키/값 쌍을 사용합니다.

| **Key** | com.microsoft.intune.mam.AllowedAccountUPNs |
|---|---|
| **값** | <ul><li>하나 이상의 <code>;</code>으로 구분된 UPN입니다.</li><li>허용된 계정만 이 키로 정의된 관리되는 사용자 계정입니다.</li><li> Intune 등록 디바이스의 경우 <code>{{userprincipalname}}</code> 토큰을 사용하여 등록된 사용자 계정을 나타낼 수 있습니다.</li></ul> |

   > [!NOTE]
   > 다중 ID로 구성된 조직 계정만 허용하는 경우에는 Android용 Outlook 2.2.222 이상, Android용 Word, Excel, PowerPoint 16.0.9327.1000 이상 또는 Android용 OneDrive 5.28 이상을 사용해야 합니다.<p></p>
   > Microsoft Intune 관리자는 관리되는 디바이스에서 Microsoft Office 애플리케이션에 추가할 사용자 계정을 제어할 수 있습니다. 허용되는 조직 사용자 계정만 액세스하도록 제한하고 등록된 디바이스에서 개인 계정을 차단할 수 있습니다. 지원 애플리케이션이 앱 구성을 처리하고 승인되지 않은 계정을 제거 및 차단합니다.<p></p>

## <a name="enter-json-data"></a>JSON 데이터 입력

앱의 일부 구성 설정(예: 번들 유형 관련 설정)은 구성 디자이너를 사용하여 구성할 수 없습니다. 이러한 값에는 JSON 편집기를 사용합니다. 설정은 앱을 설치하면 앱에 자동으로 제공됩니다.

1. **구성 설정 형식**으로 **JSON 편집기 입력**을 선택합니다.
2. 편집기에서 구성 설정에 대한 JSON 값을 정의할 수 있습니다. **JSON 템플릿 다운로드**를 선택하여 샘플 파일을 다운로드한 다음 구성할 수 있습니다.
3. **확인**을 선택한 다음 **추가**를 선택합니다.

정책이 만들어지고 목록에 표시됩니다.

할당된 앱은 디바이스에서 실행될 때 앱 구성 정책에서 구성한 설정을 사용하여 실행됩니다.

## <a name="preconfigure-the-permissions-grant-state-for-apps"></a>앱에 대한 사용 권한 부여 상태 미리 구성

Android 디바이스 기능에 액세스하기 위한 앱의 권한을 미리 구성할 수도 있습니다. 기본적으로 위치 또는 디바이스 카메라에 대한 액세스와 같이 디바이스 권한이 필요한 Android 앱에서는 권한을 허용할 것인지 거부할 것인지 묻는 메시지를 사용자에게 표시합니다.

예를 들어 앱에서 디바이스의 마이크를 사용합니다. 앱에 마이크 사용 권한을 부여하라는 메시지가 사용자에게 표시됩니다.

1. [Microsoft Endpoint Manager 관리 센터](https://go.microsoft.com/fwlink/?linkid=2109431)에서 **앱** > **앱 구성 정책** >  **추가** > **관리 디바이스**를 선택합니다.
2. 다음 속성을 추가합니다.

    - **이름**: 정책에 대한 설명이 포함된 이름을 입력합니다. 나중에 쉽게 식별할 수 있도록 정책 이름을 지정합니다. 예를 들어 올바른 정책 이름은 **전체 회사에 대한 Android Enterprise 프롬프트 권한 앱 정책**입니다.
    - **설명**. 프로필에 대한 설명을 입력합니다. 이 설정은 선택 사항이지만 권장됩니다.
    - **디바이스 등록 유형**: 이 설정은 **관리 디바이스**로 설정됩니다.
    - **플랫폼**: **Android**를 선택합니다.

3. **연결된 앱**을 선택합니다. 구성 정책을 정의하려는 앱을 선택합니다. 승인했으며 Intune과 동기화한 앱을 Android 회사 프로필 앱 목록에서 선택합니다.
4. **권한** > **추가**를 선택합니다. 목록에서 사용 가능한 앱 권한 > **확인**을 선택합니다.
5. 이 정책을 통해 부여하려는 각 권한에 대한 옵션을 선택합니다.
    - **프롬프트**. 사용자에게 허용할 것인지 거부할 것인지 묻는 메시지 표시
    - **자동 허용**. 사용자에게 알리지 않고 자동으로 승인합니다.
    - **자동 거부**. 사용자에게 알리지 않고 자동으로 거부합니다.
6. 앱 구성 정책을 할당하려면 앱 구성 정책을 선택하고 **할당** > 을 선택한 후에**그룹 선택**을 선택합니다. 할당할 사용자 그룹 > **선택**을 선택합니다.
7. **저장**을 선택하여 정책을 할당합니다.

## <a name="additional-information"></a>추가 정보

- [Android 엔터프라이즈 디바이스에 관리되는 Google Play 앱 할당](apps-add-android-for-work.md#assigning-a-managed-google-play-app-to-android-enterprise-work-profile-devices)
- [iOS/iPadOS 및 Android용 Outlook 앱 구성 설정 배포](https://docs.microsoft.com/exchange/clients-and-mobile-in-exchange-online/outlook-for-ios-and-android/outlook-for-ios-and-android-configuration-with-microsoft-intune)

## <a name="next-steps"></a>다음 단계

앱을 계속 [할당](apps-deploy.md) 및 [모니터링](apps-monitor.md)합니다.
