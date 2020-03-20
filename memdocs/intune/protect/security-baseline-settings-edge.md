---
title: Microsoft Edge에 대한 Intune 보안 기준 설정
titleSuffix: Microsoft Intune
description: Microsoft Edge 브라우저 관리를 위해 Intune에서 지원하는 보안 기준 설정
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/30/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: ''
ms.reviewer: shpate
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 623752d0eaf2742e21a78c688d58cd062f87ed52
ms.sourcegitcommit: 3d895be2844bda2177c2c85dc2f09612a1be5490
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79351216"
---
# <a name="microsoft-edge-baseline-settings-for-intune"></a>Intune의 Microsoft Edge 기준 설정

Microsoft Intune이 지원하는 Microsoft Edge 웹 브라우저 기준 설정을 확인합니다. Microsoft Edge 기준 기본값은 Microsoft Edge 브라우저의 권장 구성을 나타내며, 다른 보안 기준의 기준 기본값과 일치하지 않을 수 있습니다.

> [!NOTE]
> Microsoft Edge 기준은 공개 미리 보기로 제공됩니다. 

## <a name="microsoft-edge"></a>Microsoft Edge

- **사이트에 대한 Microsoft Defender SmartScreen 프롬프트 우회 방지**  
  **기본값**: 사용  
  Microsoft Edge CSP: [Browser/PreventSmartScreenPromptOverride](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser#browser-preventsmartscreenpromptoverride)

  이 정책 설정을 통해 잠재적 악성 웹 사이트에 대한 Microsoft Defender SmartScreen 필터 경고를 사용자가 재정의할 수 있는지 여부를 결정할 수 있습니다. 
  - 이 설정을 사용하도록 설정하면 사용자는 Microsoft Defender SmartScreen 경고를 무시할 수 없고 사이트로 이동하는 것이 차단됩니다. 
  - 이 설정을 사용하지 않도록 설정하거나 구성하지 않으면 사용자는 Microsoft Defender SmartScreen 경고를 무시하고 사이트로 이동할 수 있습니다.

- **최소 SSL 버전 사용**  
  **기본값**: 사용  

  지원되는 SSL 최소 버전을 설정합니다. 이 정책을 *구성되지 않음*으로 설정하면 Microsoft Edge는 기본 최소 버전인 *TLS 1.0*을 사용합니다. *사용*으로 설정하면 다음 값 중 최소 버전을 선택할 수 있습니다.

  - TLS 1.0
  - TLS 1.1
  - TLS 1.2

  - **최소 SSL 버전 사용**  
    **기본값**: TLS 1.2

- **다운로드에 대한 Microsoft Defender SmartScreen 경고 우회 방지**  
  **기본값**: 사용  
  Microsoft Edge CSP: [Browser/PreventSmartScreenPromptOverrideForFiles](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser#browser-preventsmartscreenpromptoverrideforfiles)  

  이 정책을 통해 확인되지 않은 다운로드에 대한 Microsoft Defender SmartScreen 경고를 사용자가 재정의할 수 있는지 여부를 결정할 수 있습니다.
  - 이 정책을 사용하도록 설정하면 조직의 사용자는 Microsoft Defender SmartScreen 경고를 무시할 수 없으며 확인되지 않은 다운로드를 완료할 수 없습니다.
  - 이 설정을 사용하지 않도록 설정하거나 구성하지 않으면 사용자는 Microsoft Defender SmartScreen 경고를 무시하고 확인되지 않은 다운로드를 완료할 수 있습니다.

- **사용자가 SSL 경고 페이지에서 계속 진행하도록 허용**  
  **기본값**: Disabled  
  Microsoft Edge CSP: [Browser/PreventCertErrorOverrides](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser#browser-preventcerterroroverrides)  

  SSL 오류가 있는 사이트를 사용자가 방문하면 Microsoft Edge가 경고 페이지를 표시합니다. 이 정책을 *사용* 또는 *구성되지 않음*으로 설정하면 사용자는 이러한 경고 페이지를 클릭하여 연결할 수 있습니다. 이 정책을 *사용하지 않음*으로 설정하면 사용자는 경고 페이지를 클릭하지 못하도록 차단됩니다. 

- **기본 Adobe Flash 설정**  
  **기본값**: 사용  
  Microsoft Edge CSP: [Browser/AllowFlash](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser#browser-allowflash) 및 [Browser/AllowFlashClickToRun](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser#browser-allowflashclicktorun)  

  'PluginsAllowedForUrls' 또는 'PluginsBlockedForUrls'가 적용되지 않는 웹 사이트가 자동으로 Adobe Flash 플러그인을 실행할 수 있는지 여부를 결정합니다. 

  - 모든 사이트에서 Adobe Flash를 차단하려면 'BlockPlugins'를 선택합니다.
  - Adobe Flash가 실행되도록 하되 시작하려면 사용자가 개체 틀을 클릭해야 하도록 하려면 ‘ClickToPlay’를 선택합니다.
  
   어느 경우든 'PluginsAllowedForUrls' 및 'PluginsBlockedForUrls' 정책은 'DefaultPluginsSetting'보다 우선적으로 적용됩니다. 자동 재생은 'PluginsAllowedForUrls' 정책에 명시적으로 나열된 도메인에서만 허용됩니다. 
   모든 사이트에서 자동 재생을 사용하려면 http://* 및 https://*를 이 목록에 추가하는 것이 좋습니다. 
   
   - 이 정책을 *구성되지 않음*으로 설정하면 사용자가 이 설정을 수동으로 변경할 수 있습니다. * 2 = Adobe Flash 플러그인 차단 * 3 = 클릭하여 재생 이전의 '1' 옵션은 모두 허용을 설정하지만 이 기능은 이제 'PluginsAllowedForUrls' 정책에 의해서만 처리됩니다. '1'을 사용하는 기존 정책은 클릭하여 재생 모드로 작동합니다.  
 
  - **기본 Adobe Flash 설정**  
    **기본값**: Adobe Flash 플러그인 차단

- **모든 사이트에 대해 사이트 격리 사용**  
  **기본값**: 사용  

  'SitePerProcess' 정책을 사용하면 사용자가 모든 사이트 격리의 기본 동작을 옵트아웃하지 못하도록 할 수 있습니다. 또한 IsolateOrigins 정책을 사용하여 추가적인 보다 세분화된 원본을 격리할 수 있습니다.

  - 이 정책이 *사용*으로 설정되면 사용자는 각 사이트가 자체 프로세스에서 실행하는 기본 동작을 옵트아웃할 수 없습니다. 
  - *사용하지 않음* 또는 *구성되지 않음*을 사용하는 경우 사용자는 사이트 격리를 옵트아웃할 수 있습니다. (예를 들어 edge://flags에서 “사이트 격리 사용 안 함” 항목을 사용하여) 정책을 사용하지 않도록 설정하거나 정책을 구성하지 않으면 사이트 격리가 해제되지 않습니다.

- **지원되는 인증 체계**  
  **기본값**: 사용  

  지원되는 HTTP 인증 체계를 지정합니다. 'basic', 'digest', 'ntlm', 'negotiate' 값을 사용하여 정책을 구성할 수 있습니다. 여러 값은 쉼표로 구분합니다. 이 정책을 구성하지 않으면 네 가지 체계가 모두 사용됩니다.
 
  - **지원되는 인증 체계**  
    다음 옵션 중에서 선택합니다. 
    - 기본
    - 다이제스트
    - NTLM *(기본적으로 선택됨)*
    - Negotiate *(기본적으로 선택됨)*

- **암호 관리자에 암호 저장 사용**  
  **기본값**: Disabled  
  Microsoft Edge CSP: [Browser/AllowPasswordManager](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser#browser-allowpasswordmanager)  

  Microsoft Edge가 사용자 암호를 저장할 수 있도록 설정합니다. 
  - 이 정책을 사용하도록 설정하면 사용자가 Microsoft Edge에 암호를 저장할 수 있습니다. 사용자가 다음 번에 사이트를 방문할 때 Microsoft Edge가 자동으로 암호를 입력합니다. 
  - 이 정책을 사용하지 않도록 설정하면 사용자는 새 암호를 저장할 수 없지만 이전에 저장된 암호는 사용할 수 있습니다. 
  
  이 정책을 *사용* 또는 *사용 안 함*으로 설정하면 사용자는 Microsoft Edge에서 이 정책을 변경하거나 재정의할 수 없습니다. 
  
  이 정책을 *구성되지 않음*으로 설정하면 사용자는 암호를 저장하고 이 기능을 해제할 수도 있습니다.

- **설치할 수 없는 확장 제어**  
  **기본값**: 사용  

  사용자가 Microsoft Edge에서 설치할 수 없는 특정 확장을 나열합니다. 이 정책을 배포하면 이전에 설치된 이 목록의 모든 확장을 사용할 수 없게 되며 사용자는 이를 사용 하도록 설정할 수 없습니다. 차단된 확장 목록에서 항목을 제거하는 경우 해당 확장은 이전에 설치된 모든 위치에서 자동으로 다시 사용하도록 설정됩니다.
  
  허용 목록에 명시적으로 나열되지 않은 모든 확장을 차단하려면 **\*** 를 사용합니다. 이 정책이 *구성되지 않음*으로 설정되면 사용자는 Microsoft Edge에 어떤 확장도 설치할 수 있습니다. 
  
  예시 값: extension_id1 extension_id2.  
  <br>
  - **사용자가 설치하지 못하도록 할 확장 ID(모든 사용자의 경우 *)**  
    **추가**를 선택하고 추가 확장을 지정합니다. **\*** 이(가) 기본적으로 선택됩니다.

- **Microsoft Defender SmartScreen 구성**  
  **기본값**: 사용  
  Microsoft Edge CSP: [Browser/AllowSmartScreen](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser#browser-allowsmartscreen)  
  
  이 정책 설정을 통해 Microsoft Defender SmartScreen을 켤지 여부를 구성할 수 있습니다. Microsoft Defender SmartScreen은 잠재적 피싱 사기 및 악성 소프트웨어로부터 사용자를 보호하는 데 도움이 되는 경고 메시지를 제공합니다. 
  
  - Microsoft Defender SmartScreen은 기본적으로 켜져 있습니다. 이 설정을 사용하도록 설정하면 Microsoft Defender SmartScreen이 켜지며 사용자가 끌 수 없습니다.
  - 이 설정을 사용하지 않도록 설정하면 Microsoft Defender SmartScreen이 꺼지며 사용자가 켤 수 없습니다. 
  - *구성되지 않음*으로 설정하면 사용자가 Microsoft Defender SmartScreen을 사용할지 여부를 선택할 수 있습니다. 
  
  이 정책은 Microsoft Active Directory 도메인에 가입된 Windows 인스턴스나 디바이스 관리에 등록된 Windows 10 Pro 또는 Enterprise 인스턴스에서만 사용할 수 있습니다.

- **사용자 수준 네이티브 메시징 호스트 허용(관리자 권한 없이 설치됨)**  
  **기본값**: Disabled  

  네이티브 메시징 호스트의 사용자 수준 설치를 사용하도록 설정합니다. 
  - 이 정책을 사용하지 않도록 설정하면 Microsoft Edge는 시스템 수준에 설치된 네이티브 메시징 호스트만 사용합니다. 기본적으로 이 정책을 구성하지 않으면 Microsoft Edge는 사용자 수준 네이티브 메시징 호스트의 사용을 허용합니다.

## <a name="next-steps"></a>다음 단계

[Intune에서 보안 기준 사용](security-baselines.md)
