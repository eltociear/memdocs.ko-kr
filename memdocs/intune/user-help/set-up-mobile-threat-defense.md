---
title: 모바일 디바이스에 Mobile Threat Defense 설치
description: 모바일 디바이스에 Mobile Threat Defense 설치하는 방법을 알아봅니다.
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 10/25/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.subservice: end-user
ms.technology: ''
ms.assetid: ''
searchScope:
- User help
ROBOTS: ''
ms.custom: intune-enduser
ms.collection: ''
ms.openlocfilehash: 889c7ef6d45a51a4aed86bf1a76842feb6f6251a
ms.sourcegitcommit: 3d895be2844bda2177c2c85dc2f09612a1be5490
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79336110"
---
# <a name="install-mobile-threat-defense"></a>Mobile Threat Defense 설치   

조직의 보안 요구 사항에 따라 MTD(모바일 위협 방어) 공급업체 앱을 설치해야 할 수 있습니다. 이 유형의 앱은 의심스러운 앱, 네트워크, OS 취약성 등 디바이스에 대한 위협을 감지하고 경고합니다.  

필수 MTD 앱이 없으면 회사 또는 학교 계정을 사용한 보호된 앱 로그인이 차단됩니다. 이 문서에서는 차단을 해제하기 위해 [MTD 앱을 설치하는 방법](set-up-mobile-threat-defense.md#install-app)을 알아봅니다.  

설치할 수 있는 MTD 공급업체 앱은 다양하며, 조직에서 어느 앱을 사용할지 알려줄 것입니다. 


## <a name="information-your-organization-can-see"></a>조직에서 볼 수 있는 정보   

조직에서는 개인 앱에서 텍스트, 이메일, 사진 등의 데이터를 볼 수 없습니다. MTD 앱은 이름 및 버전과 같은 앱 정보를 조직에 보고합니다. 실제로 보고되는 정보는 회사에서 사용하는 MTD 공급업체에 따라 다릅니다. 조직에서 다음 정보를 볼 수 있습니다.   

* 앱 이름  
* 앱 ID: Google Play에서 앱을 식별하는 고유한 이름입니다.  
* 앱 버전 및 짧은 버전 번호: 앱의 특정 릴리스 번호입니다.  
* 앱 번들 및 동적 크기: 디바이스에서 앱이 사용하는 공간의 크기입니다. 


## <a name="install-app"></a>앱 설치    
보호된 앱에 로그인할 때 MTD 앱을 설치하라는 메시지가 자동으로 표시됩니다. 화면의 단계를 따라 설치를 완료합니다. 추가 도움말을 보려면 이 섹션의 단계를 사용합니다.  
 
디바이스를 등록하라는 메시지가 표시될 수도 있습니다. ID를 확인하고 학교 또는 회사 계정을 디바이스에 연결하려면 등록이 필요합니다. 등록되지 않은 경우 MTD 앱을 설치하기 전에 해당 설치 프로그램이 자동으로 안내합니다. **등록** 화면으로 이동하면 설치 단계를 시작할 수 있습니다.  

디바이스 등록에 대한 자세한 내용은 [조직의 네트워크에서 개인 디바이스 등록](https://docs.microsoft.com/azure/active-directory/user-help/user-help-register-device-on-network)을 참조하세요.  

### <a name="ios-setup"></a>iOS 설정  

1. **등록** 화면에서 지침에 따라 조직에서 요구하는 MTD 앱을 설치합니다.   
2. **등록** 화면으로 돌아가서 **열기**를 선택합니다.  
3. MTD 앱이 Microsoft Authenticator를 열 수 있는 권한을 요청합니다. **열기**를 선택합니다. 
4. 로그인 할 회사 계정을 선택합니다. 
5. MTD 앱이 디바이스에서 보안 위협을 검색하는 동안 기다립니다. 
6. 처음에 액세스하려던 학교 또는 회사 앱으로 돌아갑니다. 이 시점에서 PIN 만들기와 같은 기타 앱 보안 요구 사항을 구성하라는 메시지가 표시될 수 있습니다.   
7. 이제 앱에 액세스할 수 있을 것입니다. 여전히 차단된 경우:  
    * **등록** 화면에서 **다시 확인**을 선택합니다.  
    * MTD 앱으로 이동하여 기존 위협이 있는지 확인합니다. 권장 단계를 완료하여 위협을 해결하고 액세스 권한을 다시 받을 수 있습니다.    

### <a name="android-setup"></a>Android 설정 

1. **등록** 화면에서 지침에 따라 조직에서 요구하는 MTD 앱을 설치합니다.  
2. **등록** 화면으로 돌아가서 **열기**를 선택합니다.  
3. MTD 앱은 필요한 경우 디바이스의 특정 영역에 액세스할 수 있는 권한을 요청합니다. 이 앱이 제대로 작동하려면 연락처에 대한 액세스를 **허용**해야 합니다. 요청되는 권한은 MTD 공급업체에 따라 다릅니다.  
4. 로그인 할 회사 계정을 선택합니다.  
5. MTD 앱이 디바이스에서 보안 위협을 검색하는 동안 기다립니다.  
6. 처음에 액세스하려던 학교 또는 회사 앱으로 돌아갑니다. 이 시점에서 PIN 만들기와 같은 기타 앱 보안 요구 사항을 구성하라는 메시지가 표시될 수 있습니다.  
7. 이제 앱에 액세스할 수 있을 것입니다. 여전히 차단된 경우:  
    * **등록** 화면에서 **다시 확인**을 선택합니다.  
    * MTD 앱으로 이동하여 기존 위협이 있는지 확인합니다. 권장 단계를 완료하여 위협을 해결하고 액세스 권한을 다시 받을 수 있습니다.  

### <a name="installation-failed"></a>설치 실패  

설치가 실패하면 IT 지원 담당자에게 문의하세요. [회사 포털 웹 사이트](https://go.microsoft.com/fwlink/?linkid=2010980)로 이동하면 귀사의 연락처 정보를 찾을 수 있습니다.  

또한 IT 지원 담당자에게 앱 로그를 보내 설치에 대한 추가 컨텍스트를 제공할 수 있습니다.  
* Android 사용자: 회사 포털에서 [로그를 업로드하고 이메일로 보냅니다](https://docs.microsoft.com/user-help/send-logs-to-your-it-admin-by-email-android).   

* iOS 디바이스 사용자: iOS용 Microsoft Edge에서 [로그를 검색하고 전송](https://docs.microsoft.com/intune/apps/manage-microsoft-edge#use-microsoft-edge-on-ios-to-access-managed-app-logs)합니다.  

## <a name="resolve-a-threat"></a>위협 해결  
위협이 조직의 정의된 위협 수준을 초과하는 경우 조직에서 다음 작업을 수행합니다.  
   
* 액세스 차단: 사용자가 회사 또는 학교 계정에 로그인한 상태에서 조직의 보호된 앱을 사용하는 것을 차단합니다.  
* 데이터 초기화: 하나 이상의 조직의 보호된 앱에서 사용자의 회사 또는 학교 데이터를 삭제합니다.  

위협을 해결하고 액세스 권한을 다시 얻으려면 디바이스에서 MTD 앱을 엽니다. 제공된 정보를 읽고 위협이 디바이스에 어떤 영향을 미치는지, 해결 방법은 무엇인지 확인합니다. 위협을 해결하는 단계를 수행한 후 MTD 앱으로 돌아가서 새 검색을 시작합니다. 조직에 다시 액세스하는 데 몇 분 정도 걸릴 수 있습니다.  

## <a name="next-steps"></a>다음 단계  

여전히 도움이 필요하세요? 회사 지원 부서에 문의하세요. 연락처 정보는 [회사 포털 웹 사이트](https://go.microsoft.com/fwlink/?linkid=2010980)를 참조하세요.

