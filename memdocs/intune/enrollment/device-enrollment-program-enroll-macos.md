---
title: macOS 디바이스 등록 - Apple Business Manager 또는 Apple School Manager
titleSuffix: ''
description: 회사 소유 macOS 디바이스를 등록하는 방법을 알아봅니다.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 12/06/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: tisilver
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 427907b3b24556be15958707bf55f4dc9b190d94
ms.sourcegitcommit: 3d895be2844bda2177c2c85dc2f09612a1be5490
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79363826"
---
# <a name="automatically-enroll-macos-devices-with-the-apple-business-manager-or-apple-school-manager"></a>Apple Business Manager 또는 Apple School Manager를 사용하여 macOS 디바이스를 자동으로 등록

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Apple의 [Apple Business Manager](https://business.apple.com/) 또는 [Apple School Manager](https://school.apple.com/)를 통해 구매한 macOS 디바이스에 대한 Intune 등록을 설정할 수 있습니다. 디바이스를 건드리지 않고 다수의 디바이스에서 이러한 등록 중 하나를 사용할 수 있습니다. macOS 디바이스를 직접 사용자에게 제공할 수 있습니다. 사용자가 디바이스를 켜면 설정 도우미가 미리 구성된 설정을 사용하여 실행되고 디바이스가 Intune 관리용으로 등록됩니다.

등록을 설정하려면 Intune과 Apple 포털을 둘 다 사용합니다. 등록 중에 디바이스에 적용된 설정을 포함하는 등록 프로필을 만듭니다.

Apple Business Manager 등록 및 Apple School Manager는 [디바이스 등록 관리자](device-enrollment-manager-enroll.md)와 함께 사용할 수 없습니다.

<!--
**Steps to enable enrollment programs from Apple**
1. [Get an Apple DEP token and assign devices](#get-the-apple-dep-token)
2. [Create an enrollment profile](#create-an-apple-enrollment-profile)
3. [Synchronize DEP-managed devices](#sync-managed-device)
4. [Assign DEP profile to devices](#assign-an-enrollment-profile-to-devices)
5. [Distribute devices to users](#end-user-experience-with-managed-devices)
-->
## <a name="prerequisites"></a>전제 조건

- [Apple School Manager](https://school.apple.com/) 또는 [Apple의 장비 등록 프로그램](http://deploy.apple.com)에서 구매한 디바이스
- 일련 번호 또는 구매 주문 번호 목록입니다.
- [MDM 기관](../fundamentals/mdm-authority-set.md)
- [Apple MDM Push certificate](../enrollment/apple-mdm-push-certificate-get.md)

## <a name="get-an-apple-dep-token"></a>Apple DEP 토큰 가져오기

macOS 디바이스를 DEP 또는 Apple School Manager를 통해 등록하려면 Apple의 DEP 토큰(.p7m) 파일이 필요합니다. Intune에서는 이 토큰을 통해 조직에서 소유한 디바이스의 정보를 동기화할 수 있습니다. 또한 Intune에서 등록 프로필을 Apple에 업로드하고 해당 프로필을 디바이스에 업로드할 수 있게 합니다.

Apple 포털을 사용하여 토큰을 만듭니다. 관리용으로 Intune에 디바이스를 할당하는 데도 Apple 포털을 사용할 수 있습니다.

> [!NOTE]
> Azure로 마이그레이션하기 전에 Intune 클래식 포털에서 토큰을 삭제하면 Intune이 삭제된 Apple 토큰을 복원할 수 있습니다. Azure Portal에서 토큰을 다시 삭제할 수 있습니다.

### <a name="step-1-download-the-intune-public-key-certificate-required-to-create-the-token"></a>1단계. 토큰을 만드는 데 필요한 Intune 공개 키 인증서 다운로드

1. [Microsoft Endpoint Manager 관리 센터](https://go.microsoft.com/fwlink/?linkid=2109431)에서 **디바이스** > **macOS** > **macOS 등록** > **등록 프로그램 토큰** > **추가**를 선택합니다.

    ![등록 프로그램 토큰을 가져옵니다.](./media/device-enrollment-program-enroll-macos/image01.png)

2. **동의**를 선택하여 Microsoft에서 Apple에 사용자 및 디바이스 정보를 보낼 수 있도록 권한을 부여합니다.

   ![공개 키를 다운로드하기 위한 Apple 인증서 작업 영역의 등록 프로그램 토큰 창 스크린샷](./media/device-enrollment-program-enroll-macos/add-enrollment-program-token-pane.png)

3. **공개 키 다운로드**를 선택하여 암호화 키(.pem) 파일을 다운로드하고 로컬로 저장합니다. .pem 파일은 Apple 포털에서 트러스트 관계 인증서를 요청하는 데 사용됩니다.

### <a name="step-2-use-your-key-to-download-a-token-from-apple"></a>2단계. 키를 사용하여 Apple에서 토큰 다운로드

1. **Apple 장비 등록 프로그램에 대한 토큰 만들기** 또는 **Apple School Manager를 통해 토큰 만들기**를 선택하여 해당 Apple 포털을 열고 회사 Apple ID로 로그인합니다. 이 Apple ID를 사용하여 토큰을 갱신할 수 있습니다.
2. DEP의 경우 Apple 포털에서 **장비 등록 프로그램**에 대해 **시작**을 선택한 후  > **서버 관리** > **MDM 서버 추가**를 선택합니다.
3. Apple School Manager의 경우 Apple 포털에서 **MDM 서버** > **MDM 서버 추가**를 선택합니다.
4. **MDM 서버 이름**을 입력하고 **다음**을 선택합니다. 서버 이름은 참조용으로 MDM(모바일 디바이스 관리) 서버를 식별하기 위한 것으로, Microsoft Intune 서버의 이름 또는 URL이 아닙니다.

5. **&lt;ServerName&gt; 추가** 대화 상자가 열리고 **공개 키 업로드**가 표시됩니다. **파일 선택...** 을 선택하여 .pem 파일을 업로드하고 **다음**을 선택합니다.

6. **배포 프로그램** &gt; **디바이스 등록 프로그램** &gt; **디바이스 관리**로 이동합니다.
7. **디바이스 선택 기준**에서 디바이스를 식별하는 방법을 지정합니다.
    - **일련 번호**
    - **주문 번호**
    - **CSV 파일 업로드**

   ![일련 번호로 디바이스 선택을 지정하고 작업 선택을 서버에 할당으로 설정한 다음 서버 이름을 선택하는 스크린샷](./media/device-enrollment-program-enroll-macos/enrollment-program-token-specify-serial.png)

8. **작업 선택**에서 **서버에 할당**, Microsoft Intune에 지정된 &lt;ServerName&gt; 및 **확인**을 순서대로 선택합니다. Apple Portal에서 관리를 위해 지정된 디바이스를 Intune 서버에 할당한 다음 **할당 완료**를 표시합니다.

### <a name="step-3-save-the-apple-id-used-to-create-this-token"></a>3단계: 이 토큰을 만드는 데 사용되는 Apple ID 저장

[Microsoft Endpoint Manager 관리 센터](https://go.microsoft.com/fwlink/?linkid=2109431)에서 나중에 참조하기 위해 Apple ID를 제공합니다.

![등록 프로그램 토큰을 만드는 데 사용되는 Apple ID를 지정하고 등록 프로그램 토큰을 찾는 스크린샷](./media/device-enrollment-program-enroll-macos/image03.png)

### <a name="step-4-upload-your-token"></a>4단계. 토큰 업로드
**Apple 토큰** 상자에서 인증서(.pem) 파일을 찾은 다음 **열기**, **만들기**를 차례로 선택합니다. Push Certificate가 있으면 Intune에서 등록된 디바이스에 정책을 푸시하여 macOS 디바이스를 등록하고 관리할 수 있습니다. Intune이 Apple과 자동으로 동기화되어 등록 프로그램 계정을 확인합니다.

## <a name="create-an-apple-enrollment-profile"></a>Apple 등록 프로필 만들기

이제 토큰을 설치했으므로 디바이스의 등록 프로필을 만들 수 있습니다. 디바이스 등록 프로필은 등록 중에 디바이스 그룹에 적용되는 설정을 정의합니다.

1. [Microsoft Endpoint Manager 관리 센터](https://go.microsoft.com/fwlink/?linkid=2109431)에서 **디바이스** > **macOS** > **macOS 등록** > **등록 프로그램 토큰**을 선택합니다.
2. 토큰을 선택하고 **프로필**을 선택한 다음 **프로필 만들기**를 선택합니다.

    ![프로필 스크린샷을 만듭니다.](./media/device-enrollment-program-enroll-macos/image04.png)

3. **프로필 만들기**에서 관리 목적으로 프로필의 **이름** 및 **설명**을 입력합니다. 사용자는 이러한 세부 정보를 볼 수 없습니다. 이 **이름** 필드를 사용하여 Azure Active Directory에 동적 그룹을 만들 수 있습니다. 이 등록 프로필로 디바이스를 할당하기 위해 프로필 이름을 사용하여 enrollmentProfileName 매개 변수를 정의합니다. [Azure Active Directory 동적 그룹](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-dynamic-membership#rules-for-devices)에 대해 자세히 알아보세요.

    ![프로필 이름 및 설명](./media/device-enrollment-program-enroll-macos/createprofile.png)

4. **플랫폼**에서 **macOS**를 선택합니다.

5. **사용자 선호도**에서 이 프로필이 있는 디바이스가 할당된 사용자로 등록되어야 하는지, 할당된 사용자 없이 등록되어야 하는지 선택합니다.
    - **사용자 선호도를 사용하여 등록** - 사용자에게 속하고 앱 설치 같은 서비스에 회사 포털 앱을 사용하려는 디바이스의 경우 이 옵션을 선택합니다. ADFS를 사용하는 경우 사용자 선호도에는 [WS-Trust 1.3 사용자 이름/혼합 엔드포인트](https://technet.microsoft.com/library/adfs2-help-endpoints)가 필요합니다. [자세한 정보](https://technet.microsoft.com/itpro/powershell/windows/adfs/get-adfsendpoint). 사용자 선호도를 사용하는 macOS DEP 디바이스에는 다단계 인증이 지원되지 않습니다.

    - **사용자 선호도를 사용하지 않고 등록** - 단일 사용자로 등록되지 않은 디바이스의 경우 이 옵션을 선택합니다. 로컬 사용자 데이터에 액세스하지 않고 작업을 수행하는 디바이스에 이 옵션을 사용합니다. 회사 포털 앱과 같은 앱이 작동하지 않습니다.

6. **디바이스 관리 설정**을 선택한 다음 이 프로필을 사용하는 디바이스에 대해 잠긴 환경을 사용할 것인지 선택합니다. **잠긴 환경**을 사용하면 **시스템 기본 설정** 메뉴 또는 **터미널**에서 관리 프로필을 제거할 수 있는 iOS 설정을 사용할 수 없습니다. 디바이스를 등록한 후에 이 설정을 변경하려면 디바이스를 초기화해야 합니다.

    ![디바이스 관리 설정 스크린샷](./media/device-enrollment-program-enroll-macos/devicemanagementsettingsblade-macos.png)

7. **확인**을 선택합니다.

8. **설정 도우미 설정**을 선택하여 다음 프로필 설정을 구성합니다.  ![설정 도우미 사용자 지정.](./media/device-enrollment-program-enroll-macos/setupassistantcustom-macos.png)

    | 부서 설정 | 설명 |
    |---|---|
    | <strong>부서 이름</strong> | 정품 인증을 하는 동안 사용자가 <strong>구성 정보</strong>를 탭하면 표시됩니다. |
    | <strong>부서 전화</strong> | 정품 인증을 하는 동안 사용자가 <strong>도움이 필요하세요?</strong> 단추를 클릭하면 표시됩니다. |

    사용자가 설정할 때 디바이스에 다양한 설치 도우미 화면을 표시하거나 숨기도록 선택할 수 있습니다.
    - **숨기기**를 선택하면 설정 중에 화면이 표시되지 않습니다. 디바이스를 설정한 후에도 사용자는 여전히 **설정** 메뉴로 이동하여 기능을 설정할 수 있습니다.
    - **표시**를 선택하면 설정 중에 화면이 표시됩니다. 사용자는 경우에 따라 작업을 수행하지 않고 화면을 건너뛸 수 있습니다. 그러나 나중에 디바이스의 **설정** 메뉴로 이동하여 기능을 설정할 수 있습니다. 

    | 설치 도우미 화면 설정 | **표시**를 선택하면 설정 중에 디바이스는... |
    |------------------------------------------|------------------------------------------|
    | <strong>암호</strong> | 사용자에게 암호를 묻는 메시지를 표시합니다. 디바이스가 보안된 상태가 아니거나 다른 방식으로 액세스가 제어된 상태(즉, 하나의 앱만 사용할 수 있도록 디바이스를 제한하는 키오스크 모드)가 아니면 항상 암호를 요구합니다. |
    | <strong>위치 서비스</strong> | 사용자에게 해당 위치를 묻는 메시지를 표시합니다. |
    | <strong>복원</strong> | 앱 및 데이터 화면을 표시합니다. 이 화면은 디바이스를 설치할 때 iCloud Backup에서 데이터를 복원하거나 전송하는 옵션을 제공합니다. |
    | <strong>iCloud 및 Apple ID</strong> | 사용자에게 **Apple ID**로 로그인하고 **iCloud**를 사용할 수 있는 옵션을 제공합니다.                         |
    | <strong>계약조건</strong> | 사용자가 Apple의 사용 약관에 동의해야 합니다. |
    | <strong>터치 ID</strong> | 사용자에게 디바이스에 대한 지문 식별을 설정하는 옵션을 제공합니다. |
    | <strong>Apple Pay</strong> | 사용자에게 디바이스에서 Apple Pay를 설정하는 옵션을 제공합니다. |
    | <strong>확대/축소</strong> | 디바이스를 설정할 때 디스플레이를 확대/축소하는 옵션을 사용자에게 제공합니다. |
    | <strong>Siri</strong> | 사용자에게 Siri를 설정할 수 있는 옵션을 제공합니다. |
    | <strong>진단 데이터</strong> | 사용자에게 진단 화면을 표시합니다. 이 화면은 사용자에게 진단 데이터를 Apple에 전송하는 옵션을 제공합니다. |
    | <strong>FileVault</strong> | 사용자에게 FileVault 암호화를 설정할 수 있는 옵션을 제공합니다. |
    | <strong>iCloud 진단</strong> | 사용자에게 iCloud 진단 데이터를 Apple에 전송하는 옵션을 제공합니다. |
    | <strong>iCloud Storage</strong> | 사용자에게 iCloud Storage를 설정할 수 있는 옵션을 제공합니다. |    
    | <strong>표시 색상</strong> | 사용자에게 표시 색상을 설정할 수 있는 옵션을 제공합니다. |
    | <strong>모양</strong> | 사용자에게 모양 화면을 표시합니다. |
    | <strong>등록</strong>| 사용자에게 디바이스를 등록하라고 요구합니다. |
    | <strong>개인 정보 보호</strong>| 사용자에게 개인 정보 화면을 표시합니다. |
    | <strong>화면 시간</strong>| 사용자에게 화면 시간 화면을 표시합니다. |

9. **확인**을 선택합니다.

10. 프로필을 저장하려면 **만들기**를 선택합니다.

## <a name="sync-managed-devices"></a>관리되는 디바이스 동기화

이제 Intune에 디바이스 관리 권한이 있으므로 Intune을 Apple과 동기화하여 Azure 포털의 Intune에서 관리되는 디바이스를 확인할 수 있습니다.

1. [Microsoft Endpoint Manager 관리 센터](https://go.microsoft.com/fwlink/?linkid=2109431)에서 **디바이스** > **macOS** > **macOS 등록** > **등록 프로그램 토큰** > 목록에서 토큰 선택 > **디바이스** > **동기화**를 선택합니다. ![등록 프로그램 디바이스 노드가 선택되고 동기화 링크를 선택하는 스크린샷](./media/device-enrollment-program-enroll-macos/image06.png)

   허용되는 등록 프로그램 트래픽에 대한 Apple 약관을 준수하기 위해 Intune에서는 다음과 같은 제한 사항을 적용합니다.
   - 전체 동기화는 7일마다 한 번씩만 실행할 수 있습니다. 전체 동기화 중에 Intune은 Intune에 연결된 Apple MDM 서버에 할당된 일련 번호의 전체 업데이트된 목록을 가져옵니다. DEP 포털의 Apple MDM 서버에서 할당을 취소하지 않고 등록 프로그램 디바이스를 Intune 포털에서 삭제하면 전체 동기화가 실행될 때까지 Intune으로 다시 가져오지 않습니다.   
   - 동기화는 24시간마다 자동으로 실행됩니다. **동기화** 단추를 클릭하여 동기화할 수도 있습니다(15분마다 한 번만). 모든 동기화 요청은 완료하는 데 15분이 주어집니다. **동기화** 단추는 동기화가 완료될 때까지 사용할 수 없습니다. 이 동기화는 기존 디바이스 상태를 새로 고치고 Apple MDM 서버에 할당된 새 디바이스를 가져옵니다.

## <a name="assign-an-enrollment-profile-to-devices"></a>디바이스에 등록 프로필 할당

먼저 등록 프로그램 프로필을 디바이스에 할당해야 디바이스를 등록할 수 있습니다.

1. [Microsoft Endpoint Manager 관리 센터](https://go.microsoft.com/fwlink/?linkid=2109431)에서 **디바이스** > **macOS** > **macOS 등록** > **등록 프로그램 토큰**을 선택하고 목록에서 토큰을 선택합니다.
2. **디바이스**를 선택하고 목록에서 디바이스를 선택한 다음 **프로필 할당**을 선택합니다.
3. **프로필 할당** 아래에서 디바이스의 프로필 &gt; **할당**을 선택합니다.

### <a name="assign-a-default-profile"></a>기본 프로필 할당

특정 토큰을 사용하여 등록하는 모든 디바이스에 적용할 기본 macOS 및 iOS/iPadOS 프로필을 선택할 수 있습니다. 

1. [Microsoft Endpoint Manager 관리 센터](https://go.microsoft.com/fwlink/?linkid=2109431)에서 **디바이스** > **macOS** > **macOS 등록** > **등록 프로그램 토큰**을 선택하고 목록에서 토큰을 선택합니다.
2. **기본 프로필 설정**을 선택하고 드롭다운 목록에서 프로필을 선택한 다음 **저장**을 선택합니다. 이 프로필은 토큰에 등록하는 모든 디바이스에 적용됩니다.

## <a name="distribute-devices"></a>디바이스 배포

Apple과 Intune 간의 동기화 및 관리를 사용하도록 설정했으며 디바이스를 등록할 수 있는 프로필을 할당했습니다. 이제 사용자에게 디바이스를 배포할 수 있습니다. 사용자 선호도가 있는 디바이스의 경우 각 사용자에게 Intune 라이선스를 할당해야 합니다. 사용자 선호도를 사용하지 않는 디바이스에는 디바이스 라이선스가 필요합니다. 활성화된 디바이스는 디바이스를 초기화할 때까지 등록 프로필을 적용할 수 없습니다.

## <a name="renew-a-dep-token"></a>DEP 토큰 갱신

1. deploy.apple.com으로 이동합니다.  
2. **서버 관리**에서 갱신할 토큰 파일과 연결된 MDM 서버를 선택합니다.
3. **새 토큰 생성**을 선택합니다.

    ![새 토큰 생성의 스크린샷입니다.](./media/device-enrollment-program-enroll-macos/generatenewtoken.png)

4. **서버 토큰**을 선택합니다.  
5. [Microsoft Endpoint Manager 관리 센터](https://go.microsoft.com/fwlink/?linkid=2109431)에서 **디바이스 등록** > **Apple 등록** > **등록 프로그램 토큰**을 선택하고 토큰을 선택합니다.
    ![등록 프로그램 토큰의 스크린샷입니다.](./media/device-enrollment-program-enroll-macos/enrollmentprogramtokens.png)

6. **토큰 갱신**을 선택하고 원래 토큰을 만드는 데 사용되는 Apple ID를 입력합니다.  
    ![새 토큰 생성의 스크린샷입니다.](./media/device-enrollment-program-enroll-macos/renewtoken.png)

7. 새로 다운로드된 토큰을 업로드합니다.  
8. **토큰 갱신**을 선택합니다. 토큰이 갱신되었다는 확인 메시지가 표시됩니다.
    ![확인의 스크린샷입니다.](./media/device-enrollment-program-enroll-macos/confirmation.png)

## <a name="next-steps"></a>다음 단계

macOS 디바이스가 등록되면 [디바이스 관리](../remote-actions/device-management.md)를 시작할 수 있습니다.
