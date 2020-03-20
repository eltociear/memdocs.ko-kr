---
title: Intune Exchange Connector의 일반적인 오류 해결
titleSuffix: Microsoft Intune
description: 온-프레미스 Microsoft Intune Exchange Connector의 일반적인 오류 해결
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
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: cb35fdc400c89c64b689f4695a48d201e50fc617
ms.sourcegitcommit: 3d895be2844bda2177c2c85dc2f09612a1be5490
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79350657"
---
# <a name="resolve-common-errors-for-the-intune-exchange-connector"></a>Intune Exchange Connector의 일반적인 오류 해결

이 문서는 Intune 관리자가 Intune Exchange Connector의 작동에 관련된 특정 오류 및 메시지를 해결하는 데 도움이 될 수 있습니다.  

## <a name="configuration-failed-and-returned-error-code-0x0000001"></a>구성에 실패하고 오류 코드 0x0000001이 반환됨

**문제**:  
Microsoft Intune Exchange Connector를 구성하려고 시도할 때 다음 오류 메시지가 표시됩니다.

```
   The Microsoft Intune Exchange Connector cannot connect to the Microsoft Exchange server.  
   The following Microsoft Exchange Server address could not be reached <Exchange server Name FQDN>  
   Verify that the FQDN of the exchange server address and credentials that you entered is correct and the server is running. The Microsoft Intune Exchange Connector does not support Exchange server arrays.  
   Error code: 0x0000001  
```

인터넷 프록시 설정이 잘못 구성된 경우 이 문제가 발생할 수 있습니다.

**해결 방법**:  
프록시 설정 구성:
1. 로컬 네트워크 관리자에게 문의하여 프록시 설정이 제대로 구성되어 있는지 확인합니다. 
2. **Netsh winhttp** 명령을 사용하여 프록시 서버를 구성하고 필요한 제외 목록을 추가합니다. 예를 들면 다음과 같습니다.  

   ```
   Netsh winhttp set proxy proxy-server="http=proxy.corp.domain.com" bypass-list"34*.*;134.132.*.*;10.*.*;localhost;*.corp.domain.com;*.staging.domain.com"
   ```

## <a name="configuration-failed-and-returned-error-code-0x000000b"></a>구성에 실패하고 오류 코드 0x000000b가 반환됨   

**문제**:  
Microsoft Intune Exchange Connector를 구성하려고 시도할 때 다음 오류 메시지가 표시됩니다.  

```
   The Microsoft Intune Exchange Connector experienced an error:  
   CertEnroll::CX509PrivateKey::Create: The system cannot find the file specified. 0x80070002 (WIN32: 2  
   ERROR_FILE_NOT_FOUND  
   Error code: 0x000000b  
```
Intune에 로그인하는 데 사용한 계정이 Intune 전역 관리자 계정이 아닌 경우 이 문제가 발생할 수 있습니다.

**해결 방법**:  
전역 관리자 계정으로 Intune에 로그인하거나 전역 관리자 그룹에 계정을 추가합니다. 자세한 내용은 [Microsoft Intune을 통한 RBAC(역할 기반 관리 제어)](../fundamentals/role-based-access-control.md)를 참조하세요.

## <a name="configuration-failed-and-returned-error-code-0x0000006"></a>구성에 실패하고 오류 코드 0x0000006이 반환됨

**문제**:  
Microsoft Intune Exchange Connector를 구성하려고 시도할 때 다음 오류 메시지가 표시됩니다.  

```  
   The Microsoft Intune Exchange Connector cannot connect to Microsoft Intune  
   Verify that you are connected to the Internet, check the Microsoft Intune Service Status, and try to connect again.  
   Error code: 0x00000006  
```  
프록시 서버가 인터넷에 연결하는 데 사용되고 Intune 서비스에 대한 트래픽을 차단하는 경우 이 오류가 발생할 수 있습니다. 프록시가 사용 중인지 확인하려면 **제어판** ** > 인터넷 옵션**으로 이동하고, **연결** 탭을 선택한 다음, **LAN 설정**을 클릭합니다.

**해결 방법**:  

- **옵션 1** - 프록시를 거치지 않고 컴퓨터에서 인터넷에 연결할 수 있도록 프록시 설정을 제거합니다.  

- **옵션 2** - [Intune Exchange Connector 요구 사항](exchange-connector-install.md#intune-exchange-connector-requirements)에 설명된 대로 Intune 서비스에 대한 통신을 허용하도록 프록시 서버를 구성합니다.



## <a name="event-7000-or-7041-microsoft-intune-exchange-connector-service-wont-start"></a>이벤트 7000 또는 7041: Microsoft Intune Exchange Connector 서비스가 시작되지 않음

**문제**:  
iOS 디바이스가 Intune에 등록되지 않았고 다음 오류 메시지 중 하나를 생성합니다.  

```  
   Log Name:      System
   Source:            Service Control Manager
   Date:               <time>
   Task Category: None
   Level:               Error
   Keywords:        Classic
   User:                N/A
   Computer:      <computer>
   Description:
   The Microsoft Intune Exchange Connector Service service failed to start because of the following error:  
   The service did not start because of a logon failure.
```  

```  
   Log Name:      System
   Source:            Service Control Manager
   Date:               <time>
   Event ID:          7041
   Task Category: None
   Level:               Error   
   Keywords:        Classic
   User:                N/A
   Computer:       <computer>
   Description:
   The WIEC service was unable to log on as .\WIEC_USER with the currently configured password because of the following error:
   Logon failure: the user has not been granted the requested logon type at this computer.
   Service: WIEC
   Domain and account: .\WIEC_USER
   This service account does not have the required user right "Log on as a service."  
```
**WIEC_User** 계정에 로컬 정책의 **서비스로 로그온** 사용자 권한이 없는 경우 이 문제가 발생할 수 있습니다.

**해결 방법**:  
Intune Exchange Connector를 실행하는 컴퓨터에서 **WIEC_User** 서비스 계정에 **서비스로 로그온** 사용자 권한을 할당합니다. 컴퓨터가 클러스터의 노드인 경우 클러스터의 모든 노드에 있는 클러스터 서비스 계정에 ‘서비스로 로그온’ 사용자 권한을 할당해야 합니다.   

컴퓨터의 **WIEC_User** 서비스 계정에 **Log on as a service** 사용자 권한을 할당하려면 다음 단계를 수행합니다.

1. 관리자 또는 관리자 그룹의 구성원으로 컴퓨터에 로그온합니다.
2. **secpol.msc**를 실행하여 로컬 보안 정책을 엽니다.
3. **보안 설정** > **로컬 정책**으로 이동한 다음, **사용자 권한 할당**을 선택합니다.
4. 올바른 창에서 **서비스로 로그온**을 두 번 클릭합니다.
5. **사용자 또는 그룹 추가**를 선택하고, 정책에 **WIEC_USER**을 추가한 다음, **확인**을 두 번 선택합니다.

**서비스로 로그온** 사용자 권한이 **WIEC_User**에 할당되었지만 나중에 제거된 경우 도메인 관리자에게 문의하여 그룹 정책 설정이 해당 할당을 덮어쓰는지 여부를 확인합니다.  

## <a name="next-steps"></a>다음 단계  

다음 문서는 특정 오류를 해결하는 데 도움이 될 수 있습니다.
- [Intune Exchange Connector의 일반적인 문제 해결](troubleshoot-exchange-connector-common-problems.md).git 

지원 또는 Intune 커뮤니티에서 지원을 요청합니다.
- [지원 받기](../fundamentals/get-support.md)를 참조하여 Intune 콘솔을 통해 문제를 해결하거나 Microsoft에 지원 사례를 엽니다. 
- [Microsoft Intune 포럼](https://social.technet.microsoft.com/Forums/en-US/home?forum=microsoftintuneprod)에 문제를 게시합니다.  
