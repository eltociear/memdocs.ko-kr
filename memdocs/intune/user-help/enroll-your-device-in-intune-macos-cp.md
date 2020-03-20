---
title: Intune 회사 포털을 사용하여 Mac 등록 | Microsoft Docs
description: 회사 포털 앱을 사용하여 Intune에 Mac을 등록하는 방법을 알아봅니다.
keywords: Mac OS X, macOS, OS X
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 12/16/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.subservice: end-user
ms.technology: ''
ms.assetid: 3bb659cc-9b57-4d19-8631-2c26749fa71c
searchScope:
- User help
ROBOTS: ''
ms.reviewer: kakyker
ms.suite: ems
ms.custom: intune-enduser
ms.collection: ''
ms.openlocfilehash: 2ef7951217b0b6df21a86ca29a8637385aa65715
ms.sourcegitcommit: 3d895be2844bda2177c2c85dc2f09612a1be5490
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79337020"
---
# <a name="enroll-your-macos-device-using-the-company-portal-app"></a>회사 포털 앱을 사용하여 macOS 디바이스 등록  

Intune 회사 포털 앱으로 macOS 디바이스를 등록하여 회사 또는 학교 전자 메일, 파일 및 앱에 대한 보안 액세스 권한을 얻습니다.

조직에서는 일반적으로 조직이 소유하는 데이터에 액세스하려면 먼저 디바이스를 등록해야 합니다. 디바이스가 등록되면 *관리*됩니다. 조직은 Intune과 같은 MDM(모바일 디바이스 관리) 공급자를 통해 디바이스에 정책과 앱을 할당할 수 있습니다. 디바이스에서 회사 또는 학교 정보에 대한 지속적인 액세스를 얻으려면 조직의 정책 설정과 일치하도록 디바이스를 구성해야 합니다.  

이 문서에서는 조직의 요구 사항을 충족하도록 macOS용 회사 포털 앱을 사용하여 디바이스를 등록, 구성 및 유지 관리하는 방법을 설명합니다.  


## <a name="what-to-expect-from-the-company-portal-app"></a>회사 포털 앱에서 예상되는 상황

초기 설정 도중 회사 포털 앱은 조직에 로그인하고 인증할 것을 요구합니다. 그런 다음 회사 포털은 조직의 요구 사항을 충족하려면 구성해야 하는 디바이스 설정을 알려 줍니다. 예를 들어 조직은 종종 사용자가 충족해야 하는 최소 또는 최대 문자 암호 요구 사항을 설정합니다.    

디바이스 등록 후 회사 포털은 항상 조직의 요구 사항에 따라 디바이스가 보호되도록 합니다. 예를 들어 신뢰할 수 없는 소스에서 앱을 설치하면 회사 포털은 사용자에게 경고하고 조직의 리소스에 대한 액세스를 제한할 수 있습니다. 이와 같은 앱 보호 정책은 일반적입니다. 액세스 권한을 다시 얻으려면 신뢰할 수 없는 앱을 제거해야 합니다. 

등록 후 조직이 다단계 인증과 같은 새 보안 요구 사항을 적용하는 경우 회사 포털은 이를 알려줍니다. 디바이스에서 작업을 계속할 수 있도록 설정을 조정할 수 있습니다.  

등록에 대해 자세히 알아보려면 [회사 포털 앱을 설치하고 디바이스를 등록하면 어떤 일이 생기나요?](what-happens-if-you-install-the-Company-Portal-app-and-enroll-your-device-in-intune-macos.md)를 참조하세요.  

## <a name="get-your-macos-device-managed"></a>macOS 디바이스 관리  
macOS 디바이스를 조직에 등록하려면 다음 단계를 사용하세요. 디바이스는 macOS 10.12 이상을 실행해야 합니다.   

> [!NOTE]
> 이 프로세스 동안 키 집합에 저장된 기밀 정보를 회사 포털이 사용하는 것을 허용해야 한다는 메시지가 표시될 수 있습니다. 이러한 프롬프트는 Apple 보안의 일부입니다. 프롬프트가 표시되면 로그인 키 집합 암호를 입력하고 **항상 허용**을 선택합니다. 키보드의 **Enter** 또는 **Return** 키를 누르면 프롬프트가 **허용**을 대신 선택하며, 추가 프롬프트가 나타날 수 있습니다.  

### <a name="install-company-portal-app"></a>회사 포털 앱 설치  
1. [내 Mac 등록](https://go.microsoft.com/fwlink/?linkid=853070)으로 이동합니다.  
2. 회사 포털 설치 관리자 .pkg 파일이 다운로드됩니다. 설치 관리자를 열고 단계를 계속 진행합니다. 
3. 소프트웨어 사용권 계약에 동의합니다. 
4. 소프트웨어를 설치하려면 디바이스 암호 또는 등록된 지문을 입력합니다.  
5. 회사 포털을 엽니다. 

> [!IMPORTANT]
> Microsoft 자동 업데이트가 열리면 Microsoft 소프트웨어를 업데이트할 수 있습니다. 모든 업데이트를 설치한 후 회사 포털 앱을 엽니다. 최상의 설치 환경을 위해서는 최신 버전의 Microsoft 자동 업데이트 및 회사 포털을 설치합니다.  


### <a name="enroll-your-mac"></a>Mac 등록  


1. 회사 또는 학교 계정을 사용하여 회사 포털에 로그인합니다.  
2. 앱이 열리면 **시작**을 선택합니다.  
3. 등록된 디바이스에서 조직이 볼 수 있는 내용과 볼 수 없는 내용을 검토합니다. 그런 다음 **계속**을 선택합니다.
4.  메시지가 표시되면 **관리 프로필 설치** 화면에서 디바이스 암호를 입력합니다.

    ![암호 프롬프트가 강조 표시된 회사 포털, 관리 포털 설치 화면의 예시 스크린샷.](./media/install-management-profile-macos-1912.PNG)   
5. **디바이스 관리 확인** 화면에서 **시스템 기본 설정 열기**를 선택합니다.  

    !["시스템 기본 설정 열기" 단추가 강조 표시된 디바이스 관리 확인 화면의 예시 스크린샷.](./media/confirm-device-management-macos-1912.PNG)  
6. 디바이스의 시스템 기본 설정이 열립니다. 디바이스 프로필 목록에서 **관리 프로필**을 선택한 다음 **승인** > **승인**을 선택합니다.  
    ![“승인” 단추가 강조 표시된 시스템 기본 설정, 관리 프로필 화면의 예시 스크린샷.](./media/management-profile-approve-macos-1912.PNG)   
1. 회사 포털로 돌아가서 **계속**을 선택합니다.    
2. 조직에서 디바이스 설정을 업데이트해야 할 수 있습니다. 설정 업데이트가 완료되면 **설정 확인**을 선택합니다.  

    ![“설정 확인” 단추가 강조 표시된 회사 포털, 디바이스 설정 업데이트 화면의 예시 스크린샷.](./media/update-settings-mac-1911.PNG)  
9. 설치가 완료되면 **완료**를 선택합니다.  


 ## <a name="troubleshooting-and-feedback"></a>문제 해결 및 피드백   

등록 도중 문제가 발생하는 경우 **도움말** > **진단 보고서 보내기**로 이동하여 Microsoft 앱 개발자에게 문제를 보고합니다. 이 정보는 앱을 개선하는 데 사용됩니다. 또한 IT 지원 담당자가 도움을 요청하는 경우 Microsoft 앱 개발자는 이 정보를 사용하여 문제를 해결합니다.  

Microsoft에 문제를 보고한 후 사용자 환경의 세부 정보를 IT 지원 담당자에게 보낼 수 있습니다. **전자 메일 세부 정보**를 선택합니다. 전자 메일의 본문에 경험한 문제를 입력합니다. 지원 담당자의 전자 메일 주소를 찾으려면 회사 포털 앱 > **연락처**로 이동합니다. 또는 [회사 포털 웹 사이트](https://go.microsoft.com/fwlink/?linkid=2010980)를 확인합니다.  
 

Microsoft Intune 회사 포털 팀은 여러분의 의견을 소중히 생각합니다. **도움말** > **피드백 보내기**로 이동하여 생각과 아이디어를 공유하세요.  

## <a name="unverified-profiles"></a>확인되지 않은 프로필  
**시스템 기본 설정** > **프로필**에서 설치된 MDM(모바일 디바이스 관리) 프로필을 보면 일부 프로필의 상태가 확인되지 않음으로 표시될 수 있습니다. 관리 프로필에 확인됨 상태가 표시되는 한, 염려할 필요가 없습니다.  

관리 프로필은 MDM 채널 연결을 정의합니다. 관리 프로필이 확인되는 한, 채널을 통해 머신에 전달되는 다른 프로필은 관리 프로필의 보안 특성을 상속합니다.  

## <a name="updating-the-company-portal-app"></a>회사 포털 앱 사용

회사 포털 앱 업데이트는 macOS용 Microsoft 자동 업데이트를 통해 다른 Office 앱과 동일한 방식으로 수행됩니다. [macOS용 Microsoft 앱 업데이트](https://support.office.com/article/Check-for-Office-for-Mac-updates-automatically-bfd1e497-c24d-4754-92ab-910a4074d7c1)에 대해 자세히 알아보세요.  

## <a name="next-steps"></a>다음 단계  
여전히 도움이 필요하세요? 회사 지원 부서에 문의하세요. 연락처 정보는 [회사 포털 웹 사이트](https://go.microsoft.com/fwlink/?linkid=2010980)를 참조하세요.  


