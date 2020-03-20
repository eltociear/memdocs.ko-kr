---
title: Intune 회사 포털 및 DISA Purebred를 사용하여 iOS 또는 iPadOS 디바이스 등록
description: DISA Purebred를 사용하여 iOS 또는 iPadOS 디바이스를 등록하고 파생 자격 증명 인증을 설정하는 방법을 알아봅니다.
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 10/31/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
searchScope:
- User help
ROBOTS: ''
ms.reviewer: tisilver
ms.suite: ems
ms.custom: intune-enduser
ms.collection: ''
ms.openlocfilehash: 38d1b40ecdeee5bfd872297a5fd4f0229cb48dcf
ms.sourcegitcommit: 3d895be2844bda2177c2c85dc2f09612a1be5490
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79337592"
---
# <a name="set-up-ios-or-ipados-device-with-company-portal-and-disa-purebred"></a>회사 포털 및 DISA Purebred를 사용하여 iOS 또는 iPadOS 디바이스 설정  

Intune 회사 포털 앱으로 디바이스를 등록하여 조직의 메일, 파일 및 앱에 대한 보안 모바일 액세스 권한을 얻습니다. 디바이스가 등록되면 *관리*됩니다. 조직은 Intune과 같은 MDM(모바일 디바이스 관리) 공급자를 통해 디바이스에 정책과 앱을 할당할 수 있습니다.  

등록 도중 파생 자격 증명을 디바이스에 설치합니다. 조직에서는 리소스에 액세스하거나 메일을 서명하고 암호화할 때 파생 자격 증명을 인증 방법으로 사용하도록 요구할 수 있습니다. 

스마트 카드를 사용하여 다음을 수행하는 경우 파생 자격 증명을 설정해야 할 수 있습니다.

* 학교 또는 회사 앱, Wi-Fi 및 VPN(가상 사설망)에 로그인
* S/MIME 인증서를 사용하여 학교 또는 회사 이메일 서명 및 암호화  

이 문서에서는 다음을 수행합니다.  

   * Intune 회사 포털을 사용하여 모바일 iOS 또는 iPadOS 디바이스를 등록합니다.  
   * 조직의 파생 자격 증명 공급자 [DISA Purebred](https://cyber.mil/pki-pke/purebred/)에서 파생 자격 증명을 가져옵니다.  

## <a name="what-are-derived-credentials"></a>파생 자격 증명이란?  
파생 자격 증명은 스마트 카드 자격 증명에서 파생되고 디바이스에 설치된 인증서입니다. 회사 리소스에 대한 원격 액세스 권한을 부여하는 동시에 권한 없는 사용자가 중요한 정보에 액세스하지 못하도록 합니다.  

파생 자격 증명은 다음에 사용됩니다. 
* 학교 또는 회사 앱, Wi-Fi, VPN에 로그인하는 학생 및 직원 인증
* S/MIME 인증서를 사용하여 학교 또는 회사 이메일 서명 및 암호화

파생 자격 증명은 SP(Special Publication) 800-157의 일부로 PIV(Personal Identity Verification) 파생 자격 증명에 관한 NIST(미국 국립표준기술원) 지침을 구현한 것입니다.  

## <a name="prerequisites"></a>전제 조건

 등록을 완료하려면 다음이 있어야 합니다.

* 학교 또는 회사에서 제공하는 스마트 카드
* 스마트 카드로 로그인할 수 있는 컴퓨터 또는 키오스크에 대한 액세스 권한
* 모바일 디바이스
* 디바이스에 설치된 iOS 및 iPadOS용 Intune 회사 포털 앱   

또한 설치하는 동안 Purebred 에이전트 또는 담당자에게 문의해야 합니다.      

## <a name="enroll-device"></a>디바이스 등록  
1. 모바일 디바이스에서 iOS/iPadOS용 회사 포털 앱을 열고 회사 계정으로 로그인합니다.  

2. 화면의 코드를 적어 둡니다.  

    ![화면 메시지 및 코드가 있는 회사 포털 앱의 예시 이미지.](./media/copy-code-intercede.png)  
3. 스마트 카드 지원 디바이스로 전환하고 https://microsoft.com/devicelogin 으로 이동합니다. 
4. 이전에 적어 둔 코드를 입력합니다.  

    ![회사 포털 웹 사이트 “코드 입력” 프롬프트 예시 스크린샷.](./media/enter-code-intercede.png)   

5. 스마트 카드를 삽입하여 로그인합니다.  
6. 모바일 디바이스에서 회사 포털 앱으로 돌아와 화면의 지시에 따라 디바이스를 등록합니다.  
7. 등록이 완료된 후 회사 포털이 스마트 카드를 설정하라고 알립니다. 알림을 탭합니다. 알림을 받지 못한 경우 이메일을 확인합니다.   

    ![디바이스 홈 화면의 회사 포털 푸시 알림 예시 스크린샷.](./media/action-required-in-app-intercede.png)  
8. **모바일 스마트 카드 액세스 설정** 화면에서  
    a. 조직의 설치 지침에 대한 링크를 탭합니다. 조직에서 추가 지침을 제공하지 않으면 이 문서로 리디렉션됩니다.  
    b. **열기**를 클릭하여 Purebred 앱을 엽니다.  

    ![회사 포털 모바일 스마트 카드 액세스 설정 화면의 예시 스크린샷.](./media/smart-card-open-disa-purebred.png)  
9. 회사 포털이 Purebred 등록 앱을 열도록 허용할지 묻는 메시지가 표시되면 **열기**를 선택합니다.   

    ![회사 포털의 DISA Purebred 앱을 열기 프롬프트의 예시 스크린샷.](./media/open-app-prompt-disa-purbred.png)  
10. 앱이 작동하면 조직의 Purebred 에이전트를 사용하여 Purebred 등록 전 구성 프로필을 구성하고 다운로드합니다.   
11. 설정 앱 > **일반** > **프로필 및 디바이스 관리** > **프로필 설치**로 이동하고 **설치**를 탭합니다.  
12. 디바이스 암호를 입력합니다.  
13. 프로필을 설치합니다. 설치를 시작하려면 **설치**를 두 번 이상 눌러야 할 수 있습니다. 
14. Purebred 등록 앱으로 돌아갑니다. Purebred 에이전트의 지침에 따라 계속 진행합니다.  
 
15. 구성 프로필을 다운로드한 후 설정 앱 > **일반** > **프로필 및 디바이스 관리** > **프로필 설치**로 이동하고 **설치**를 탭합니다.   
16.  디바이스 암호를 입력합니다.
17. 프로필을 설치합니다. 설치를 시작하려면 **설치**를 두 번 이상 눌러야 할 수 있습니다. 
18. 설치가 완료되면 회사 포털 앱으로 돌아갑니다.  
19.  **모바일 스마트 카드 액세스 설정** 화면에서 **계속**을 탭합니다.  

20. **인증서 가져오기** 화면에서 DISA Purebred로부터 얻은 파생 자격 증명을 검색하고 가져옵니다.  

    a. **계속**을 탭합니다.   

    ![회사 포털 인증서 가져오기 설정 화면의 예시 스크린샷](./media/import-certificate-disa-purebred.png)  
    b. iCloud 드라이브 **찾아보기** > **위치**로 이동하고 **기타 위치**를 탭합니다.  

    ![iCloud 드라이브 찾아보기 메뉴의 기타 위치 옵션이 강조 표시된 예시 스크린샷.](./media/icloud-drive-more-locations.png)  
    c. 스위치를 탭하여 **Purebred 키 체인**을 사용하도록 설정합니다.  

    ![iCloud 드라이브의 찾아보기 보기에서 Purebred 키 체인 스위치가 사용하도록 설정된 것을 보여 주는 예시 스크린샷.](./media/icloud-drive-enable-purebred-keychain.png)   

    d. **Purebred 자격 증명 패키지**를 탭합니다.  

    ![선택 가능한 Purebred 자격 증명 패키지 옵션이 있는 iOS 화면의 예시 스크린샷.](./media/purebred-credential-package.png)  
    f. 인증서 목록이 표시됩니다. 하나를 선택한 다음 **키 가져오기**를 탭합니다.  

    ![선택 가능한 인증서 목록에서 인증서 하나가 이미 선택된 예시 스크린샷.](./media/import-purebred-keychain.png) 
21. 회사 포털 앱으로 돌아가서 회사 포털이 디바이스 설정을 마칠 때까지 기다립니다.   

## <a name="next-steps"></a>다음 단계  
등록이 완료되면 전자 메일, Wi-Fi 및 조직에서 제공하는 앱 등 회사 리소스에 액세스할 수 있습니다. 회사 포털에서 앱을 가져오고, 검색하고, 설치 및 제거하는 방법에 대한 자세한 내용은 다음을 참조하세요.

* [회사 포털 웹 사이트에서 앱 관리](manage-apps-cpweb.md)  
* [디바이스에서 관리되는 앱 사용](use-managed-apps-on-your-device-ios.md)  

여전히 도움이 필요하세요? 회사 지원 부서에 문의하세요. 연락처 정보는 [회사 포털 웹 사이트](https://go.microsoft.com/fwlink/?linkid=2010980)를 참조하세요.
