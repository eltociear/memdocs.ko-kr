---
title: Intune 회사 포털 및 Intercede를 사용하여 iOS 또는 iPadOS 디바이스 등록
description: Intercede를 사용하여 iOS 또는 iPadOS 디바이스를 등록하고 파생 자격 증명 인증을 설정하는 방법을 알아봅니다.
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
ms.openlocfilehash: 1bd216049c5dbda7c044949f9fa39c3b7bd56f9d
ms.sourcegitcommit: 3d895be2844bda2177c2c85dc2f09612a1be5490
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79337241"
---
# <a name="set-up-ios-or-ipados-device-with-company-portal-and-intercede"></a>회사 포털 및 Intercede를 사용하여 iOS 또는 iPadOS 디바이스 설정

Intune 회사 포털 앱으로 디바이스를 등록하여 조직의 메일, 파일 및 앱에 대한 보안 모바일 액세스 권한을 얻습니다.  디바이스가 등록되면 *관리*됩니다. 조직은 Intune과 같은 MDM(모바일 디바이스 관리) 공급자를 통해 디바이스에 정책과 앱을 할당할 수 있습니다.  

등록 도중 파생 자격 증명을 디바이스에 설치합니다. 조직에서는 리소스에 액세스하거나 메일을 서명하고 암호화할 때 파생 자격 증명을 인증 방법으로 사용하도록 요구할 수 있습니다. 

스마트 카드를 사용하여 다음을 수행하는 경우 파생 자격 증명을 설정해야 할 수 있습니다.

* 학교 또는 회사 앱, Wi-Fi 및 VPN(가상 사설망)에 로그인
* S/MIME 인증서를 사용하여 학교 또는 회사 이메일 서명 및 암호화  

이 문서에서는 다음을 수행합니다.  

* Intune 회사 포털을 사용하여 모바일 iOS 또는 iPadOS 디바이스를 등록합니다.  
* 조직의 파생 자격 증명 공급자 [Intercede](https://www.intercede.com/)에서 파생 자격 증명을 가져옵니다.   


## <a name="what-are-derived-credentials"></a>파생 자격 증명이란?  
파생 자격 증명은 스마트 카드 자격 증명에서 파생되고 디바이스에 설치된 인증서입니다. 회사 리소스에 대한 원격 액세스 권한을 부여하는 동시에 권한 없는 사용자가 중요한 정보에 액세스하지 못하도록 합니다.  

파생 자격 증명은 다음에 사용됩니다. 
* 학교 또는 회사 앱, Wi-Fi, VPN에 로그인하는 학생 및 직원 인증
* S/MIME 인증서를 사용하여 학교 또는 회사 이메일 서명 및 암호화  

파생 자격 증명은 SP(Special Publication) 800-157의 일부로 PIV(Personal Identity Verification) 파생 자격 증명에 관한 NIST(미국 국립표준기술원) 지침을 구현한 것입니다.  

## <a name="prerequisites"></a>전제 조건

 등록을 완료하려면 다음이 있어야 합니다.

* 학교 또는 회사에서 제공하는 스마트 카드
* 스마트 카드로 로그인할 수 있는 컴퓨터 또는 셀프 서비스 키오스크에 대한 액세스 권한
* 모바일 디바이스
* 디바이스에 설치된 iOS 및 iPadOS용 Intune 회사 포털 앱


## <a name="enroll-device"></a>디바이스 등록  
1. 모바일 디바이스에서 iOS/iPadOS용 회사 포털 앱을 열고 회사 계정으로 로그인합니다.  
2. 화면에 표시되는 코드를 적어 둡니다.  

    ![화면 메시지 및 코드가 있는 회사 포털 앱의 예시 이미지.](./media/copy-code-intercede.png)  
1. 스마트 카드 지원 디바이스로 전환하고 https://microsoft.com/devicelogin 으로 이동합니다. 

1. 앞서 적어 둔 코드를 입력합니다.
 
2. 스마트 카드를 삽입하여 로그인합니다.   

3. 모바일 디바이스에서 회사 포털 앱으로 돌아와 화면의 지시에 따라 디바이스를 등록합니다.  
4. 등록이 완료된 후 회사 포털이 스마트 카드를 설정하라고 알립니다. 알림을 탭합니다. 알림을 받지 못한 경우 이메일을 확인합니다.   

    ![디바이스 홈 화면의 회사 포털 푸시 알림 예시 스크린샷.](./media/action-required-in-app-intercede.png)  

5. **모바일 스마트 카드 액세스 설정** 화면에서  
    a. 조직의 설치 지침에 대한 링크를 탭합니다. 조직에서 추가 지침을 제공하지 않으면 이 문서로 리디렉션됩니다.  
    b. **시작**을 탭합니다.  

    ![회사 포털 모바일 스마트 카드 액세스 설정 화면의 예시 스크린샷.](./media/smart-card-info-intercede.png)  

6. 스마트 카드 지원 디바이스 또는 셀프 서비스 키오스크로 전환하고 MyID 앱을 엽니다. 회사 자격 증명을 사용하여 로그인합니다.  
7. ID를 요청하는 옵션을 선택합니다. 
8. 사용할 프로필을 묻는 메시지가 표시되면 모바일 자격 증명을 사용하여 활성화하는 옵션을 선택합니다. QR 코드가 표시됩니다.  
9. 모바일 디바이스로 돌아갑니다. 회사 포털 > **QR 코드 가져오기** 화면에서 **계속**을 탭합니다.  

    ![회사 포털 QR 코드 가져오기의 예시 스크린샷.](./media/get-qr-code-intercede.png) 
 
10. **카메라 사용** > **확인**을 탭합니다.  

    ![카메라 액세스 허용 권한을 요청하는 회사 포털 프롬프트의 예시 스크린샷.](./media/allow-cp-camera-access-intercede.png)  

11. 스마트 카드 지원 디바이스에 있는 QR 코드 이미지를 스캔합니다. 
12. 회사 포털이 디바이스 설정을 마칠 때까지 기다립니다.  

## <a name="next-steps"></a>다음 단계  
등록이 완료되면 전자 메일, Wi-Fi 및 조직에서 제공하는 앱 등 회사 리소스에 액세스할 수 있습니다. 회사 포털에서 앱을 가져오고, 검색하고, 설치 및 제거하는 방법에 대한 자세한 내용은 다음을 참조하세요.

* [회사 포털 웹 사이트에서 앱 관리](manage-apps-cpweb.md)  
* [디바이스에서 관리되는 앱 사용](use-managed-apps-on-your-device-ios.md)  

여전히 도움이 필요하세요? 회사 지원 부서에 문의하세요. 연락처 정보는 [회사 포털 웹 사이트](https://go.microsoft.com/fwlink/?linkid=2010980)를 참조하세요.
