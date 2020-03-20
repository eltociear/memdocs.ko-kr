---
title: Intune용 Android 디바이스 암호화 | Microsoft Docs
description: Intune에서 필요한 경우 Android 디바이스 암호화를 설정하는 단계
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 04/19/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.subservice: end-user
ms.technology: ''
ms.assetid: d4430e92-04cc-48e9-a77a-81b95a90b6b3
searchScope:
- User help
ROBOTS: ''
ms.reviewer: arnab
ms.suite: ems
ms.custom: intune-enduser
ms.collection: ''
ms.openlocfilehash: ee2d220e308b406251f049e1c17422f89ee36534
ms.sourcegitcommit: 3d895be2844bda2177c2c85dc2f09612a1be5490
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79348785"
---
# <a name="encrypting-your-android-device"></a>Android 디바이스 암호화

디바이스 암호화는 디바이스를 분실하거나 도난 당했을 때 무단 액세스로부터 파일과 폴더를 보호해 줍니다. 디바이스 암호화를 설정하면 정확한 암호 또는 PIN을 입력하는 사용자만 디바이스에 로그인할 수 있습니다. 

학교 또는 직장 리소스에 액세스하기 전에 조직에서 Android 디바이스 암호화를 요구할 수 있습니다. 최신 Android 디바이스 중에는 기본적으로 암호화되어 있는 경우가 있습니다.  

## <a name="turn-on-encryption"></a>암호화 설정

회사 포털 또는 Microsoft Intune 앱에 디바이스를 암호화하라는 메시지가 표시되면 다음 단계를 완료합니다. 

> [!Note]
> Huawei, Vivo, OPPO의 특정 Android 디바이스는 암호화할 수 없습니다. 자세한 내용은 [여기](your-device-appears-encrypted-but-cp-says-otherwise-android.md)를 참조하세요.  

1. 디바이스 화면 잠금을 설정합니다.  
    a. **설정** > **잠금 화면 및 보안** > **화면 잠금**으로 이동합니다.  
    b. **PIN**, **암호** 또는 **패턴** 중 하나를 선택합니다.  
    c. 화면의 지시에 따라 화면 잠금을 구성합니다.  

2. **잠금 화면 및 보안**으로 돌아가서 **보안 시작**을 선택합니다.
3. **디바이스 켤 때 PIN 필요** > **확인**을 선택합니다.
4. PIN을 입력하여 확인하고 디바이스를 암호화합니다.
5. 회사 포털 또는 Microsoft Intune 앱을 엽니다.
    * 회사 포털 사용자: 디바이스를 선택하고 **디바이스 설정 확인**을 탭합니다. 
    * Microsoft Intune 사용자: 페이지가 업데이트될 때까지 기다려야 하며, 업데이트되면 암호화 상태를 준수로 변경해야 합니다.  

Android 4.4 이전 버전을 실행하는 디바이스에는 **보안 시작** 옵션이 없을 수 있습니다. 이 경우, 다음 단계를 완료하여 디바이스를 암호화합니다.

1. **설정** > **보안** > **디바이스 암호화**로 이동합니다. 화면 라벨은 Android 디바이스마다 다릅니다. **디바이스 암호화** 옵션이 표시되지 않을 경우 다음에서 확인해 봅니다.
    * **스토리지** > **스토리지 암호화**
    * **스토리지** > **잠금 화면 및 보안** > **기타 보안 설정** 

2. 화면의 지시를 따릅니다. 암호화가 진행되는 동안 디바이스가 여러 번 다시 시작될 수 있습니다.
3. 회사 포털 또는 Microsoft Intune 앱을 엽니다.
    * 회사 포털 사용자: 디바이스를 선택하고 **디바이스 설정 확인**을 탭합니다.  
    * Microsoft Intune 사용자: 페이지가 업데이트될 때까지 기다려야 하며, 업데이트되면 암호화 상태를 준수로 변경해야 합니다.

## <a name="troubleshoot"></a>문제 해결  
**문제**: 디바이스를 이미 암호화했습니다.

- 암호화 단추를 사용할 수 없습니다.
- 여전히 암호화해야 한다는 메시지가 표시됩니다.
- 회사 포털 또는 Microsoft Intune 앱을 사용하려고 할 때 오류가 발생합니다.

**시도할 작업**

- 디바이스가 충전되었고 전원에 연결되어 있는지 확인합니다.  
- 디바이스에서 PIN 또는 암호를 설정했는지 확인합니다.  

여전히 도움이 필요하세요? 회사 지원팀에 문의하거나(연락처 정보는 [회사 포털 웹 사이트](https://go.microsoft.com/fwlink/?linkid=2010980) 확인) <a href="mailto:wintunedroidfbk@microsoft.com?subject=I'm having trouble with encryption on my Android device&body=Describe the issue you're experiencing here.">Microsoft Android 팀</a>으로 메일을 보내세요.  
