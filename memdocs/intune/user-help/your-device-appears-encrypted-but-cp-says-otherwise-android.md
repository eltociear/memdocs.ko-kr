---
title: Android 디바이스가 암호화된 것 같음 | Microsoft Docs
description: 회사 포털 및 Microsoft Intune 앱에서 암호화 상태 확인
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 08/14/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.subservice: end-user
ms.technology: ''
ms.assetid: ba593c08-1a78-4013-8525-b45a948772ec
searchScope:
- User help
ROBOTS: ''
ms.reviewer: arnab
ms.suite: ems
ms.custom: intune-enduser
ms.collection: ''
ms.openlocfilehash: 4fd08ba190654db5678766e34e3340330dcf3ca8
ms.sourcegitcommit: 3d895be2844bda2177c2c85dc2f09612a1be5490
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79346094"
---
# <a name="device-encrypted-but-apps-say-otherwise"></a>디바이스가 암호화되어 있지만 앱에서는 그렇지 않은 것으로 표시

회사 포털 또는 Microsoft Intune 앱에서 디바이스가 암호화되지 않은 것으로 표시되는 경우 이 문서의 단계를 수행합니다.  

## <a name="add-a-startup-pin"></a>시작 PIN 추가

특정 Android 디바이스에서는 디바이스의 보안을 유지하기 위해 시작 PIN을 만들어야 합니다. 이 설정의 위치는 디바이스의 **설정** 앱입니다. 설정의 이름 및 위치는 다를 수 있습니다. 예를 들어 Samsung Galaxy S7에서는 이 설정을 **보안 시작**이라고 합니다. 이를 사용하도록 설정하고 암호를 만들려면 **설정** > **잠금 화면 및 보안** > **보안 시작**으로 이동합니다.  

## <a name="encrypt-the-entire-device"></a>전체 디바이스 암호화

이 섹션은 회사 포털 앱에만 적용됩니다. 일부 디바이스에서는 전체 디바이스를 암호화할지 아니면 사용된 공간만을 암호화할지 선택하도록 합니다. 전체 디바이스를 암호화하는 옵션을 선택합니다. 사용된 공간만 암호화하도록 선택한 경우:

1. [회사 포털에서 이 디바이스를 제거](unenroll-your-device-from-intune-android.md)합니다.
2. 사용된 공간의 암호를 해독합니다.  
3. 전체 디바이스를 암호화합니다.  
4. 디바이스 다시 등록.  

## <a name="downgrade-your-version-of-android"></a>Android 버전 다운그레이드

이 섹션은 회사 포털 앱에만 적용됩니다. 디바이스에서 Android 6.0 이상으로 다운그레이드하는 옵션을 제공하는 경우 다운그레이드합니다. 디바이스 다운그레이드를 시도하는 경우 데이터 손실 위험이 있습니다. 그렇지 않으면 회사 지원팀에 문의하여 이 문제를 해결하는 것이 좋습니다. 회사 지원팀의 연락처 정보는 [회사 포털 웹 사이트](https://go.microsoft.com/fwlink/?linkid=2010980)에서 가져옵니다.  

## <a name="specific-manufacturer-issues"></a>특정 제조업체 문제

버전 7.0 이상의 일부 Android 디바이스에서는 특정 Android 플랫폼 표준과 일치하지 않는 방식으로 데이터를 암호화합니다. 이러한 암호화 방법은 디바이스 정보를 위험에 노출합니다. 따라서 이러한 디바이스는 지원되지 않습니다.

지원되는 Android 디바이스에 대한 목록(모든 항목이 포함된 것은 아님)은 [Intune에서 지원되는 운영 체제 및 브라우저 문서](https://docs.microsoft.com/intune/fundamentals/supported-devices-browsers#supported-samsung-knox-standard-devices)를 참조하세요. 디바이스가 나열되지 않은 경우 디바이스 제조업체를 참조하거나 지원 담당자에게 문의하세요.

> [!Note]
> Microsoft는 제조업체와 협력하여 테스트 중에 확인되거나 사용자들이 보고하는 문제를 해결합니다. 새로운 정보를 사용할 수 있을 때마다 이 문서를 업데이트합니다.

## <a name="update-devices"></a>디바이스 업데이트

디바이스를 최신 버전의 Android로 업데이트하지 않은 경우 디바이스 **설정** 앱으로 이동하고 **업데이트**를 선택합니다.  

## <a name="next-steps"></a>다음 단계

여전히 도움이 필요하세요? 회사 지원팀에 문의하거나(연락처 정보는 [회사 포털 웹 사이트](https://go.microsoft.com/fwlink/?linkid=2010980) 확인) <a href="mailto:wintunedroidfbk@microsoft.com?subject=I'm having trouble with enrolling my Android device&body=Describe the issue you're experiencing here.">Microsoft Android 팀</a>으로 메일을 보내세요.  
