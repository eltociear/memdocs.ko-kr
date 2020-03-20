---
title: Microsoft Intune과 Jamf Pro 통합 문제 해결
titleSuffix: Microsoft Intune
description: Microsoft Intune과 Mac 디바이스용 Jamf Pro를 통합할 때 가장 일반적인 문제 중 일부를 해결하기 위한 제안입니다.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/02/2019
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 335841a8642429e36c277673fd8a238d486366c9
ms.sourcegitcommit: 3d895be2844bda2177c2c85dc2f09612a1be5490
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79350618"
---
# <a name="troubleshoot-integration-of-jamf-pro-with-microsoft-intune"></a>Microsoft Intune과 Jamf Pro 통합 문제 해결

이 문서는 Intune 관리자가 Intune과 macOS용 Jamf Pro 통합에 관련된 문제를 이해하고 해결하는 데 도움이 됩니다.

> [!TIP]  
> 이 문서의 많은 정보는 원래 support.microsoft.com의 [Microsoft Intune과 Jamf 통합 시 문제 해결](https://support.microsoft.com/help/4519171/troubleshoot-problems-when-integrating-jamf-with-microsoft-intune)에 나와 있었습니다.

## <a name="prerequisites"></a>전제 조건

문제 해결을 시작하기 전에 몇 가지 기본 정보를 수집하여 문제를 명확하게 파악하고 해결 시간을 단축합니다. 예를 들어 Jamf-Intune 통합 관련 문제가 발생하는 경우 항상 필수 구성 요소가 모두 충족되었는지 확인합니다. 문제 해결을 시작하기 전에 다음 고려 사항을 검토합니다.

- [Intune과 Jamf Pro 통합](conditional-access-integrate-jamf.md#prerequisites)의 필수 구성 요소를 검토합니다.
- 모든 사용자에게 Microsoft Intune 및 Microsoft AAD Premium P1 라이선스가 있어야 합니다. 
- Jamf Pro 콘솔에서 Microsoft Intune 통합 권한이 있는 사용자 계정이 있어야 합니다.
- Azure에서 전역 관리자 권한이 있는 사용자 계정이 있어야 합니다.


Intune과 Jamf Pro 통합을 조사할 경우 다음 정보를 고려합니다. 
- 정확한 오류 메시지가 무엇입니까?
- 오류 메시지는 어디에 있습니까?
- 문제가 언제 시작되었습니까?  Intune과 Jamf Pro 통합이 작동했습니까?
- 얼마나 많은 사용자가 영향을 받습니까? 영향을 받는 사용자는 전체입니까, 아니면 일부입니까?
- 영향을 받은 디바이스는 얼마나 됩니까? 영향을 받는 디바이스는 전체입니까, 아니면 일부입니까?
 

## <a name="common-problems"></a>일반적인 문제 

다음 정보는 Intune 및 Jamf Pro 통합을 설정한 후 디바이스의 일반적인 문제를 식별하고 해결하는 데 도움이 될 수 있습니다.  

| 문제   | 추가 정보                  |
|-----------------|--------------------------|
| **디바이스가 Jamf Pro에서 응답하지 않는 것으로 표시됨**  | [디바이스가 Jamf Pro 또는 Azure AD을 사용하여 체크 인하지 못함](#devices-are-marked-as-unresponsive-in-jamf-pro) |
| **디바이스를 등록하지 못한 앱을 열 때 Mac 디바이스가 키 집합 로그인에 대한 메시지를 표시함**  | [Azure AD에 앱을 등록할 수 있도록 암호에 대한 메시지가 사용자에게 표시됨](#mac-devices-prompt-for-keychain-sign-in-when-you-open-an-app). |
| **디바이스 등록 실패**  | 다음 원인이 적용될 수 있습니다. <br> **-** [***원인 1*** - Azure의 Jamf Pro 앱에 잘못된 권한이 있음](#cause-1) <br> **-** [***원인 2*** - Azure AD에 *Jamf Native macOS Connector* 문제가 있음](#cause-2) <br> **-** [***원인 3*** - 사용자에게 유효한 Intune 또는 Jamf 라이선스가 없음](#cause-3) <br> **-** [***원인 4*** - 사용자가 회사 포털 앱을 시작하는 데 Jamf 셀프 서비스를 사용하지 않음](#cause-4) <br> **-** [***원인 5*** - Intune 통합이 꺼짐](#cause-5) <br> **-** [***원인 6*** - 디바이스가 이전에 Intune에 등록되었거나 사용자가 디바이스를 여러 번 등록하려고 시도함](#cause-6) <br> **-** [***원인 7*** - JamfAAD에서 사용자의 키 집합에서 “Microsoft Workplace Join 키”에 대한 액세스를 요청함](#cause-7) |
|  **Mac 디바이스가 Intune에서 호환되지만 Azure에서 호환되지 않는 것으로 표시됨** | [디바이스 등록 문제](#mac-device-shows-compliant-in-intune-but-noncompliant-in-azure) |
| **Jamf를 사용하여 등록된 Mac 디바이스의 중복 항목이 Intune 콘솔에 표시됨** | [동일한 디바이스의 여러 번 등록](#duplicate-entries-appear-in-the-intune-console-for-mac-devices-enrolled-by-using-jamf) |
| **준수 정책에서 디바이스를 평가하지 못함** | [정책이 디바이스 그룹을 대상으로 함](#compliance-policy-fails-to-evaluate-the-device) |
| **Microsoft Graph API의 액세스 토큰을 검색할 수 없음** | 다음 원인이 적용될 수 있습니다. <br> -[Azure의 Jamf Pro 앱에 대한 권한](#theres-a-permission-issue-with-the-jamf-pro-application-in-azure) <br> - [Jamf 또는 Intune의 만료된 라이선스](#a-license-required-for-jamf-intune-integration-has-expired) <br> **-** [포트가 열려 있지 않음](#the-required-ports-arent-open-on-your-network)|
 

### <a name="devices-are-marked-as-unresponsive-in-jamf-pro"></a>디바이스가 Jamf Pro에서 응답하지 않는 것으로 표시됨  

**원인**: 다음은 디바이스가 Jamf Pro에서 ‘응답하지 않는’ 것으로 표시되는 일반적인 원인입니다. 

- 디바이스가 Jamf Pro를 사용하여 체크 인하지 못합니다.  
  Jamf Pro는 디바이스가 15분마다 체크 인할 것으로 예상합니다. 24시간 동안 체크 인하지 못할 경우 디바이스가 Jamf에서 응답하지 않는 것으로 표시됩니다.  

- 디바이스가 Azure AD를 사용하여 체크 인하지 못합니다.  
  Azure AD에 등록된 macOS 디바이스는 Azure 토큰을 수신합니다.
  - 이 토큰은 12시간마다 새로 고쳐집니다.   
  - 24시간 이상 토큰이 새로 고쳐지지 않으면 Jamf Pro는 디바이스를 응답하지 않는 것으로 표시합니다.  
  - Azure 토큰이 만료되면 Azure에 로그인하여 새 토큰을 가져올지 묻는 메시지가 사용자에게 표시됩니다. Azure 액세스를 위한 새로 고침 토큰은 7일마다 생성됩니다.

**해결 방법**  
디바이스가 Jamf Pro에서 ‘응답하지 않는’ 것으로 표시된 후 디바이스의 등록된 사용자는 로그인하여 응답하지 않는 상태를 수정해야 합니다.  로그인 키 집합에 Intune의 ID가 있기 때문에 작업 공간에 연결된 계정이 있는 사용자여야 합니다.



### <a name="mac-devices-prompt-for-keychain-sign-in-when-you-open-an-app"></a>앱을 열 때 Mac 디바이스가 키 집합 로그인에 대한 메시지를 표시함  

Intune 및 Jamf Pro 통합을 구성하고 조건부 액세스 정책을 배포한 후 Jamf Pro를 사용하여 관리되는 디바이스의 사용자에게는 Teams, Outlook 같은 Microsoft Office 365 애플리케이션 및 Azure AD 인증이 필요한 기타 앱을 열 때 암호를 묻는 메시지가 표시됩니다. 

예를 들어 Microsoft Teams를 열 때 다음 예제와 유사한 텍스트가 있는 메시지가 표시됩니다.

``` 
  Microsoft Teams wants to sign using key “Microsoft Workplace Join Key” in your keychain.  
  To allow this, enter the “login” keychain password 
```

**원인**: Azure AD 등록이 필요한 각 앱에 대해 Jamf Pro에서 이 메시지를 생성합니다. 

**해결 방법**   
메시지에서 사용자는 Azure AD에 로그인하려면 디바이스 암호를 제공해야 합니다. 다음 옵션을 사용할 수 있습니다.
- **거부** - 로그인하지 않고 앱을 사용하지 않습니다.
- **허용** - 일회성 로그인입니다. 다음에 앱을 열 때 로그인하라는 메시지가 다시 표시됩니다.
- **항상 허용** - 애플리케이션에 대해 로그인 자격 증명이 캐시됩니다. 다음에 앱을 열 때 로그인하라는 메시지가 표시되지 않습니다.  

한 앱에 대해 ‘항상 허용’을 선택하면 이후 로그인할 때 해당 앱만 승인됩니다.  추가 앱은 ‘항상 허용’으로 설정될 때까지 인증하라는 메시지가 표시됩니다.  한 앱에 대해 캐시된 자격 증명은 다른 앱에서 사용할 수 없습니다.  

### <a name="devices-fail-to-register"></a>디바이스 등록 실패  

Mac 디바이스를 등록하지 못하는 일반적인 원인에는 여러 가지가 있습니다.  

#### <a name="cause-1"></a>원인 1  

**Azure의 Jamf Pro 엔터프라이즈 애플리케이션에 잘못된 권한이 있거나 둘 이상의 권한이 있음**  

  Azure에서 앱을 만들 경우 모든 기본 API 권한을 제거한 다음, Intune에 *update_device_attributes*의 단일 권한을 할당해야 합니다. 

  **해결 방법**  
  Azure AD에서 만든 Jamf 앱에 대한 권한을 검토하고 필요한 경우 수정합니다. [Azure AD에서 Jamf용 애플리케이션을 만드는](conditional-access-integrate-jamf.md#create-an-application-in-azure-active-directory) 절차를 참조하세요. 

#### <a name="cause-2"></a>원인 2  

****Jamf Native macOS Connector** 앱이 Azure AD 테넌트에서 만들어지지 않았거나, 커넥터에 대한 동의가 전역 관리자 권한이 없는 계정에 의해 서명됨**  

  **해결 방법**  
  docs.jamf.com의 [Microsoft Intune과 통합](https://docs.jamf.com/10.13.0/jamf-pro/administrator-guide/Integrating_with_Microsoft_Intune.html)에서 ‘macOS Intune 통합 구성’ 섹션을 참조하세요.  

#### <a name="cause-3"></a>원인 3

**사용자에게 유효한 Intune 또는 Jamf 라이선스가 없음**  

  유효한 라이선스가 없으면 Jamf 라이선스가 만료되었음을 나타내는 다음 오류가 발생할 수 있습니다.  
  ```
    Unable to connect to Microsoft Intune.  
    
    Check your Microsoft Intune Integration configuration.
  ```  

  **해결 방법**
  - Jamf 라이선스: Jamf의 새 라이선스를 얻으려면 Jamf에 문의하세요.  
  - Intune 라이선스: 사용자에게 유효한 라이선스를 할당하거나 Microsoft 또는 파트너에게 문의하여 현재 라이선스를 얻는 방법에 관한 정보를 확인하세요.

#### <a name="cause-4"></a>원인 4  

**사용자가 회사 포털 앱을 시작하는 데 ‘Jamf 셀프 서비스’를 사용하지 않음** 

Jamf를 통해 Intune에 디바이스를 등록하려면 사용자가 Jamf 셀프 서비스를 사용하여 Intune 회사 포털을 열어야 합니다. 사용자가 회사 포털을 수동으로 열면 디바이스는 Jamf에 연결되지 않고 등록됩니다.  

디바이스가 등록에 사용한 서비스를 확인하려면 디바이스에서 회사 포털 앱을 확인합니다. Jamf를 통해 등록된 경우 변경하려면 셀프 서비스 앱을 열라는 알림을 받게 됩니다.

회사 포털 앱에서 사용자에게 **`Not registered`** 가 표시될 수 있으며 다음 예제와 유사한 항목이 회사 포털 로그에 나타날 수 있습니다.  

```
   Line 7783: <DATE> <IP ADDRESS> INFO com.microsoft.ssp.application TID=1  
 
   WelcomeViewController.swift: 253 (startLogin()) Portal launched without WPJ only arg while account is under partner management
```

**해결 방법**  
Intune에서 Jamf로 등록 원본을 변경하려면 다음을 수행합니다.
1. [Intune에서 macOS 디바이스 등록을 취소합니다](https://docs.microsoft.com/user-help/unenroll-your-device-from-intune-macos). Intune에서 완전히 제거되지 않는 디바이스에 관련된 더 복잡한 문제를 방지하려면 이 원인 목록에서 [‘원인 6’](#cause-6)을 참조하세요.   

2. 디바이스에서 Jamf 셀프 서비스를 사용하여 회사 포털 앱을 열고 Intune에 디바이스를 등록합니다. 이 작업을 수행하려면 [Jamf를 사용하여 macOS용 회사 포털 앱을 배포](conditional-access-assign-jamf.md#deploy-the-company-portal-app-for-macos-in-jamf-pro)하고 [Azure AD에 사용자 디바이스를 등록하는 Jamf Pro의 정책을 만들어야](conditional-access-assign-jamf.md#create-a-policy-in-jamf-pro-to-have-users-register-their-devices-with-azure-active-directory) 합니다.  

3. 포털이 열리면 첫 번째 화면에 로그인하라는 메시지가 표시됩니다. 회사 또는 학교 계정을 사용합니다.  

4. 회사 포털에서 사용자의 계정 정보를 확인하고, 디바이스 등록 및 디바이스 준수 상태를 표시합니다. 노란색 삼각형은 학교 또는 회사의 macOS 디바이스를 보호하기 위해 수행해야 하는 작업을 강조 표시합니다. 시작을 클릭하여 등록을 시작합니다.  

5. 메시지가 표시되면 컴퓨터의 로그인 정보를 입력합니다.  
     
관리에서 디바이스를 등록하는 데 몇 분 정도 걸릴 수 있습니다. 그 동안 디바이스에서 다른 작업을 수행할 수 있습니다. 회사 액세스 설정이 완료되면 알려드리겠다는 메시지를 받게 됩니다.

#### <a name="cause-5"></a>원인 5  

**Intune 통합이 꺼짐**

Intune 통합이 꺼져 있으면 사용자가 디바이스를 등록하려고 할 때 다음 메시지가 포함된 팝업 창이 회사 포털에 표시됩니다.  

```
   Invalid command line input
   
   Registration-only command line flag (-r) can only be used when partner management is enabled in Intune. Please contact your IT admin.
```  

Jamf Pro 서버는 통합이 꺼져 있는 경우 통합이 사용되지 않음을 Intune에 알리는 펄스를 Intune 서버에 보냅니다. 

**해결 방법**  
Jamf Pro 내에서 Intune 통합을 다시 사용하도록 설정합니다. [Jamf Pro에서 Microsoft Intune 통합 구성](conditional-access-integrate-jamf.md#enable-intune-to-integrate-with-jamf-pro)을 참조하세요.


#### <a name="cause-6"></a><a name="cause-6"></a>원인 6  

**디바이스가 이전에 Intune에 등록되었거나 사용자가 디바이스를 여러 번 등록하려고 시도함**

디바이스가 Jamf에서 등록 취소되었지만 Intune에서 제대로 제거되지 않았거나, 등록이 여러 번 시도된 경우 포털에는 동일한 디바이스의 여러 인스턴스가 표시될 수 있습니다. 이로 인해 Jamf 등록이 실패합니다.

**해결 방법**  
1. Mac에서 **터미널**을 시작합니다.
2. **sudo JAMF removemdmprofile**을 실행합니다.
3. **sudo JAMF removeFramework**를 실행합니다.
4. JAMF Pro 서버에서 컴퓨터의 인벤토리 레코드를 삭제합니다.
5. AzureAD에서 디바이스를 삭제합니다.
6. 디바이스에서 다음 파일을 삭제합니다(있는 경우).
   - /Library/Application Support/com.microsoft.CompanyPortal.usercontext.info
   - /Library/Application Support/com.microsoft.CompanyPortal
   - /Library/Application Support/com.jamfsoftware.selfservice.mac
   - /Library/Saved Application
   - State/com.jamfsoftware.selfservice.mac.savedState
   - /Library/Saved Application State/com.microsoft.CompanyPortal.savedState
   - /Library/Preferences/com.microsoft.CompanyPortal.plist
   - /Library/Preferences/com.jamfsoftware.selfservice.mac.plist
   - /Library/Preferences/com.jamfsoftware.management.jamfAAD.plist
   - /Users/<username>/Library/Cookies/com.microsoft.CompanyPortal.binarycookies
   - /Users/<username>/Library/Cookies/com.jamf.management.jamfAAD.binarycookies
   - com.microsoft.CompanyPortal
   - com.microsoft.CompanyPortal.HockeySDK
   - enterpriseregistration.windows.net
   - https://device.login.microsoftonline.com
   - https://device.login.microsoftonline.com/
   - Microsoft 세션 전송 키(퍼블릭 및 프라이빗 키)
   - Microsoft Workplace Join 키(퍼블릭 및 프라이빗 키)
7. *Microsoft*, *Intune* 또는 ‘회사 포털’을 참조하는 디바이스의 키 집합에서 DeviceLogin.microsoft.com 인증서를 포함한 모든 것을 제거합니다.  JAMF 퍼블릭 키 및 프라이빗 키를 제외하고 *JAMF* 참조를 제거합니다. 
   > [!IMPORTANT]  
   > 퍼블릭 키 및 프라이빗 키를 제거하면 디바이스 등록이 중단됩니다.

8. 다음 항목을 찾아서 삭제합니다.  
   - Kind: Application password ; Account: com.microsoft.workplacejoin.thumbprint
   - Kind: Application password ; Account: com.microsoft.workplacejoin.registeredUserPrincipalName
   - Kind: Certificate ; Issued by: MS-Organization-Access
   - Kind: Identity preference ; Name(ADFS STS URL if present): https://adfs\<DNSName>.com/adfs/ls
   - Kind: Identity preference ; Name: https://enterpriseregistration.windows.net
   - Kind: Identity preference ; Name: https://enterpriseregistration.windows.net/  
9. Mac 디바이스를 다시 시작합니다.
10. 디바이스에서 회사 포털을 제거합니다.
11. portal.manage.microsoft.com으로 이동하고 Mac 디바이스 인스턴스를 모두 삭제합니다. 다음 단계로 이동하기 전에 30분 이상 기다립니다.
12. JAMF Pro에서 디바이스를 다시 등록합니다.
13. 셀프 서비스를 다시 열고 등록 정책을 시작합니다.


#### <a name="cause-7"></a>원인 7  

**JamfAAD에서 사용자의 키 집합에서 “Microsoft Workplace Join 키”에 대한 액세스를 요청함**

등록하는 동안 macOS 디바이스의 사용자에게 키 집합의 키에 대한 JamfAAD 액세스를 허용하라는 다음 메시지가 표시됩니다. 

```
   JamfAAD wants to access key “Microsoft Workplace Join Key" in your keychain. 
    
   To allow this, enter the “login” keychain password
```

**해결 방법**  
Azure AD에 디바이스를 등록하려면 Jamf에서 사용자가 계정 암호를 입력하고 **허용**을 선택해야 합니다.

이 요청은 이 문서의 앞부분에 나오는 [앱을 열 때 Mac 디바이스가 키 집합 로그인에 대한 메시지를 표시함](#mac-devices-prompt-for-keychain-sign-in-when-you-open-an-app)에 대한 요청과 비슷합니다.  

 
### <a name="mac-device-shows-compliant-in-intune-but-noncompliant-in-azure"></a>Mac 디바이스가 Intune에서 호환되지만 Azure에서 호환되지 않는 것으로 표시됨  

**원인**: 다음 조건에 해당하는 경우 디바이스가 Intune에서 호환되지만 Azure에서 호환되지 않는 것으로 표시될 수 있습니다.  
- 디바이스가 제대로 등록되지 않았습니다.  
- 디바이스가 필요한 정리 없이 여러 번 등록되었습니다.

**해결 방법**  
이 문제를 해결하려면 이 문서의 앞부분에 나오는 ‘디바이스 등록 실패’에 대한 [‘원인 6’](#cause-6)의 해결 방법을 따릅니다.   


### <a name="duplicate-entries-appear-in-the-intune-console-for-mac-devices-enrolled-by-using-jamf"></a>Jamf를 사용하여 등록된 Mac 디바이스의 중복 항목이 Intune 콘솔에 표시됨  
 
**원인**: 디바이스는 Intune에 여러 번 등록되며, 일반적으로 Intune에서 제거된 후 다시 등록됩니다.  

디바이스가 Intune 및 Jamf Pro 통합에서 제거되면 일부 데이터가 남게 되어 이후 등록할 때 중복 항목이 생성될 수 있습니다.  

**해결 방법**  
이 문제를 해결하려면 이 문서의 앞부분에 나오는 ‘디바이스 등록 실패’에 대한 [‘원인 6’](#cause-6)의 해결 방법을 따릅니다.   

### <a name="compliance-policy-fails-to-evaluate-the-device"></a>준수 정책에서 디바이스를 평가하지 못함  

**원인**: Jamf를 Intune과 통합해도 디바이스 그룹을 대상으로 하는 규정 준수 정책은 지원되지 않습니다. 

**해결 방법**  
사용자 그룹에 할당할 macOS 디바이스에 대한 준수 정책을 수정합니다. 


### <a name="could-not-retrieve-the-access-token-for-microsoft-graph-api"></a>Microsoft Graph API의 액세스 토큰을 검색할 수 없음

이 경우 다음과 같은 오류가 발생합니다.

```
   Could not retrieve the access token for Microsoft Graph API. Check the configuration for Microsoft Intune Integration.
```   

이 오류의 원인은 다음 중 하나일 수 있습니다. 

#### <a name="theres-a-permission-issue-with-the-jamf-pro-application-in-azure"></a>Azure에서 Jamf Pro 애플리케이션에 관련된 권한 문제가 있음

Azure에서 Jamf Pro 앱을 등록하는 동안 다음 조건 중 하나가 발생했습니다.  
- 앱이 둘 이상의 권한을 받았습니다.
- **‘\<회사>’에 대한 관리자 동의 권한 부여** 옵션이 선택되지 않았습니다.   

**해결 방법**  
이 문서의 앞부분에 나오는 [디바이스 등록 실패](#devices-fail-to-register)에 대한 원인 1의 해결 방법을 참조하세요.

#### <a name="a-license-required-for-jamf-intune-integration-has-expired"></a>Jamf-Intune 통합에 필요한 라이선스가 만료됨

**해결 방법**: [디바이스 등록 실패](#devices-fail-to-register)에 대한 원인 3의 해결 방법을 참조하세요. 

#### <a name="the-required-ports-arent-open-on-your-network"></a>네트워크에서 필요한 포트가 열려 있지 않음

**해결 방법**: Intune과 Jamf Pro 통합에 대한 [필수 구성 요소](conditional-access-integrate-jamf.md#prerequisites)에서 네트워크 포트 정보를 검토합니다.


## <a name="next-steps"></a>다음 단계
[Intune과 Jamf Pro 통합](conditional-access-integrate-jamf.md)에 대한 자세한 정보