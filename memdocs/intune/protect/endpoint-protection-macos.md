---
title: Microsoft Intune - Azure의 macOS에서 엔드포인트 보호 추가 | Microsoft Docs
description: MacOS 디바이스에서 게이트키퍼를 사용하여 mac 앱 스토어를 포함해 앱을 설치할 수 있는 위치를 결정합니다. 또한 Microsoft Intune을 사용하여 방화벽이 특정 앱을 허용하도록 구성하거나 사용하도록 설정하고, 특정 앱을 차단하고, 은폐 모드를 사용하고 특정 유형의 들어오는 연결을 차단합니다.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/02/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 8ef60333b53e03b3a6a8d736817ef27df9a182f1
ms.sourcegitcommit: 3d895be2844bda2177c2c85dc2f09612a1be5490
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79352074"
---
# <a name="macos-endpoint-protection-settings-in-intune"></a>Intune에서 macOS 엔드포인트 보호 설정  

이 문서에서는 macOS를 실행하는 디바이스에 대해 구성할 수 있는 엔드포인트 보호 설정을 보여줍니다. Intune에서 [엔드포인트 보호](endpoint-protection-configure.md)에 macOS 디바이스 구성 프로필을 사용하여 해당 설정을 구성합니다.  

## <a name="gatekeeper"></a>게이트키퍼  

- **다음 위치에서 다운로드된 앱 허용**  
  앱이 다운로드된 원본 위치에 따라 디바이스에서 시작할 수 있는 앱을 제한합니다. 맬웨어에서 디바이스를 보호하고 신뢰하는 소스로부터만 앱을 허용하기 위함입니다.  

  - **구성되지 않음**  
  - **Mac 앱 스토어**  
  - **Mac 앱 스토어 및 확인된 개발자**  
  - **Anywhere**  

  **기본값**: 구성되지 않음  

- **사용자가 게이트키퍼를 재정의할 수 있음**  
  사용자가 게이트키퍼 설정을 재정의하는 것을 금지하고 앱을 설치하기 위해 컨트롤 클릭을 금지합니다. 사용하도록 설정되면 사용자가 앱을 컨트롤 클릭하여 설치할 수 있습니다.  
 
  - **구성되지 않음** - 사용자가 Control 키를 클릭하여 앱을 설치할 수 있습니다.  
  - **차단** - 사용자가 Control 키를 클릭하여 앱을 설치할 수 없도록 합니다.  

  **기본값**: 구성되지 않음  

## <a name="firewall"></a>방화벽  

방화벽을 사용하여 포트별이 아닌 애플리케이션별 연결을 제어합니다. 애플리케이션별 설정을 사용하면 방화벽 보호의 이점을 더욱 쉽게 얻을 수 있습니다. 또한 합법적인 앱에 대해 열려있는 네트워크 포트를 원하지 않는 앱이 제어하는 것을 방지해줍니다.  

**일반**
- **방화벽**  
  들어오는 연결을 사용자 환경에서 처리하는 방법을 구성하려면 방화벽을 사용하도록 설정합니다.  
  - **구성되지 않음**  
  - **사용**  

  **기본값**: 구성되지 않음  

- **들어오는 연결**  
  DHCP, Bonjour, IPSec 등의 기본 인터넷 서비스에 필요한 연결을 제외하고 들어오는 모든 연결을 차단합니다. 또한 이 기능은 모든 공유 서비스(예: 파일 공유, 화면 공유)를 차단합니다. 공유 서비스를 사용하는 경우 이 설정을 *구성되지 않음*으로 유지합니다.  
  - **구성되지 않음**  
  - **차단**  

  **기본값**: 구성되지 않음  

**특정 앱에 대한 들어오는 연결을 허용하거나 차단합니다.**  

  - **허용된 앱**  
    들어오는 연결을 수신하도록 명시적으로 허용된 앱을 선택합니다.  

  - **차단된 앱**  
    들어오는 연결을 차단해야 하는 앱을 선택합니다.  

  - **은폐 모드**  
    컴퓨터가 검색 요청에 응답하지 않게 하려면 은폐 모드를 사용하도록 설정합니다. 디바이스는 권한이 부여된 앱에 대해 들어오는 요청에 계속 응답합니다. ICMP(ping)와 같은 예기치 않은 요청은 무시합니다.  
    - **구성되지 않음**  
    - **사용**  

    **기본값**: 구성되지 않음  

## <a name="filevault"></a>FileVault  
Apple FileVault 설정에 대한 자세한 내용은 Apple Developer 콘텐츠에서 [FDEFileVault](https://developer.apple.com/documentation/devicemanagement/fdefilevault)를 참조하세요. 

> [!IMPORTANT]  
> macOS 10.15부터 FileVault 구성에는 사용자 승인 MDM 등록이 필요합니다. 

- **FileVault**  
  macOS 10.13 이상을 실행하는 디바이스의 FileVault에서 XTS-AES 128을 사용하여 전체 디스크 암호화를 ‘사용하도록 설정’할 수 있습니다.   
  - **구성되지 않음**  
  - **사용**  

  **기본값**: 구성되지 않음  

  - **복구 키 유형**  
    디바이스의 ‘개인 키’ 복구 키가 생성됩니다.  개인 키의 다음 설정을 구성합니다.  

    - **개인 복구 키의 위치** - 개인 복구 키를 검색하는 방법 및 위치를 설명하는 사용자에게 표시할 짧은 메시지를 지정합니다. 이 텍스트는 암호를 잊어버린 경우 개인 복구 키를 입력하라는 메시지가 표시될 때 로그인 화면에서 사용자가 볼 수 있는 메시지에 삽입됩니다.  
      
    - **개인 복구 키 회전** - 디바이스의 개인 복구 키를 회전하는 빈도를 지정합니다. 기본값인 **구성되지 않음** 또는 **1**~**12**개월 값을 선택할 수 있습니다.  

  - **로그아웃 시 프롬프트 사용 안 함**  
    로그아웃할 때 FileVault 사용을 요청하는 프롬프트가 사용자에게 표시되지 않도록 합니다.  사용 안 함으로 설정하면 로그아웃 시 프롬프트가 사용되지 않으며, 대신 사용자가 로그인할 때 메시지가 표시됩니다.  
    - **구성되지 않음**  
    - **사용 안 함** - 로그아웃 시 프롬프트를 사용하지 않도록 설정합니다.

    **기본값**: 구성되지 않음  

  - **무시 허용 횟수**  
  FileVault에서 사용자 로그인을 요구하기 전에 사용자가 FileVault 사용을 묻는 프롬프트를 무시할 수 있는 횟수를 설정합니다. 

    - **구성되지 않음** - 다음 로그인이 허용되기 전에 디바이스에서 암호화가 필요합니다.  
    - **1**~**10** - 디바이스에서 암호화를 요구하기 전에 사용자가 프롬프트를 1~10번 무시할 수 있습니다.  
    - **무제한, 항상 묻기** - 사용자에게 FileVault 사용을 묻는 메시지가 표시되지만 암호화가 필요하지 않습니다.  
 
    **기본값**: ‘상황에 따라 다름’ - ‘로그아웃 시 프롬프트 사용 안 함’이 **구성되지 않음**으로 설정된 경우 이 설정은 기본적으로 **구성되지 않음**으로 설정됩니다.   ‘로그아웃 시 프롬프트 사용 안 함’이 **사용 안 함**으로 설정된 경우 이 설정은 기본적으로 **1**로 설정되며 **구성되지 않음** 값은 옵션이 아닙니다. 

Intune을 통한 FileVault 사용에 대한 자세한 내용은 [FileVault 복구 키](encryption-monitor.md#filevault-recovery-keys)를 참조하세요.
