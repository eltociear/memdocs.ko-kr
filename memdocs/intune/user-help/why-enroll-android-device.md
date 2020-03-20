---
title: Android 디바이스를 등록하는 이유
description: Intune에 디바이스를 등록하는 것이 왜 중요한지 알아봅니다.
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
ms.assetid: d22f5aea-7be4-419b-b51b-a522ca037b69
searchScope:
- User help
ROBOTS: ''
ms.reviewer: esmich
ms.suite: ems
ms.custom: intune-enduser
ms.collection: ''
ms.openlocfilehash: ea760ef125ce2d6d7d0446564be3b2b27a6038ce
ms.sourcegitcommit: 3d895be2844bda2177c2c85dc2f09612a1be5490
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79335135"
---
# <a name="why-enroll-your-android-device"></a>Android 디바이스를 등록하는 이유  

학교 및 회사에서는 사용자가 안전하고 신뢰할 수 있는 디바이스를 사용하여 내부 리소스에 액세스하기를 원합니다. 회사 포털 및 Microsoft Intune 앱은 이러한 리소스에 액세스하는 동안 Android 디바이스와 데이터를 안전하게 유지합니다. 사용자의 위치 또는 사용하는 디바이스와 관계없이 리소스에 안전하게 액세스할 수 있도록 합니다. 

조직에서 이러한 앱 중 하나를 설치하고 등록하도록 요구하는 경우 디바이스에서 회사 리소스에 액세스하려면 그렇게 해야 합니다. 이 문서에서는 이러한 앱에 디바이스를 등록하는 목적과 이점에 대해 설명합니다.  

## <a name="gets-your-device-managed"></a>디바이스 관리  
 회사 포털 및 Microsoft Intune 앱은 Intune에서 디바이스를 등록합니다.  Intune은 조직에서 보안 및 디바이스 정책을 통해 모바일 디바이스 및 앱을 관리하는 데 도움이 되는 모바일 장치 관리 공급자입니다. 

앱은 각 등록 단계를 안내하고 조직의 정책에 맞게 디바이스 설정을 구성합니다. 또한 회사 액세스를 얻기 전에 해결해야 하는 문제나 설정에 대해 경고할 수 있습니다.  

예를 들어 조직에서 다음과 같은 정책을 요구할 수 있습니다.  
* 암호 또는 PIN 설정
* 설정된 로그인 시도 횟수 이후 액세스 제한
* 무단 해제 또는 루팅된 디바이스 사용 금지
* 작업에 필요한 앱 설치  

## <a name="gives-you-access-to-work-and-school-apps-work-files-and-email"></a>회사 및 학교 앱, 작업 파일, 이메일에 대한 액세스 권한을 제공합니다.  
등록하는 동안 회사 포털 및 Microsoft Intune 앱을 사용하려면 회사 또는 학교 계정에 연결해야 합니다.  디바이스를 인증하고 조직의 정책에 맞게 디바이스 설정을 구성한 후에 조직의 이메일 계정, 네트워크, 파일 및 앱에 대한 액세스 권한을 얻을 수 있습니다.  

조직에서 가끔 Microsoft Office나 Mobile Threat Defense 같은 작업 또는 보안 앱을 설치하라고 요구합니다. 이러한 앱이 필요하거나 사용자가 사용할 수 있게 되면 회사 포털 또는 Microsoft Intune 앱에서 찾을 수 있습니다.

## <a name="lets-you-remotely-reset-a-lost-or-stolen-device-if-device-supports-it"></a>분실 또는 도난당한 디바이스를 원격으로 다시 설정해 봅시다(디바이스에서 지원하는 경우).
디바이스를 분실하거나 도난당한 경우 다른 디바이스에서 회사 포털 앱 또는 회사 포털 웹 사이트에 로그인하여 전화기를 공장 설정으로 다시 설정할 수 있습니다. 이 기능은 잃어버린 디바이스에 다른 사람이 액세스하면 안 되는 회사 데이터가 포함된 경우에 유용합니다. 디바이스가 관리에 등록되었기 때문에 회사 지원팀 또는 IT 관리자도 디바이스를 다시 설정할 수 있습니다.  

초기화 기능은 Microsoft Intune 앱에서 사용할 수 없습니다.  

## <a name="notifies-you-of-policy-updates-and-requirements"></a>정책 업데이트 및 요구 사항 공지
회사 포털 또는 Microsoft Intune 앱은 8시간마다 Intune과 자동으로 체크 인 또는 동기화됩니다. 회사 포털을 사용할 때 더 자주 체크 인하려면 사용자 또는 회사 지원팀이 수동 동기화를 시작할 수 있습니다. 체크 인하는 동안 앱이 다음 작업을 수행합니다.  

* 회사 지원팀이 제공하는 정책 또는 앱 업데이트를 다운로드합니다.  
* 하드웨어 인벤토리 업데이트를 보냅니다. 이러한 업데이트에는 개인 정보가 포함되지 않습니다.  
* 회사 앱 인벤토리 업데이트를 보냅니다. 이러한 업데이트에는 개인 정보가 포함되지 않습니다.  

디바이스가 동기화되지 않았거나 더 이상 요구 사항을 충족하지 않는 경우 해당 상태는 *비준수*로 표시됩니다. 디바이스가 다시 요구 사항을 충족할 때까지 회사 및 학교 관련 리소스에 대한 액세스가 철회될 수 있습니다. 회사 포털 앱은 이러한 문제 및 문제를 해결하기 위해 수행해야 하는 단계를 알려줍니다.  


## <a name="permits-company-support-access-to-your-device"></a>회사 지원팀의 디바이스 액세스 허용
디바이스를 등록하면 회사 지원팀 또는 IT 관리자가 합당한 이유가 있을 때 제한적으로 디바이스에 액세스할 수 있도록 액세스 권한이 부여됩니다. 최종 사용자는 다음과 같이 할 수 있습니다.  

* 사용자 디바이스를 디바이스 제조업체의 기본 설정으로 복원합니다. 위에서 언급했듯이, 관리자도 디바이스를 다시 설정할 수 있습니다. 그러나 관리자가 회사 포털 앱에 바로 액세스할 수 없는 경우에는 회사에서 관리자 대신 디바이스를 다시 설정해야 합니다.  

* 모든 회사 관련 데이터를 제거합니다. 관리자가 퇴사하거나 디바이스가 더 이상 관리되지 않는 경우 조직에서 디바이스의 회사 관련 데이터를 제거할 수 있습니다. 개인 데이터 및 설정은 제거되지 않고 디바이스에 유지됩니다.  

* 디바이스 암호나 PIN을 요구하도록 디바이스의 요구 사항을 설정하세요. 이 예에서는 디바이스가 규정을 준수하지 않을 때 앱 알림을 받습니다. 회사 지원팀이 디바이스의 암호 입력 오류 횟수를 제한할 수도 있습니다. 입력 오류 횟수가 너무 많으면 디바이스가 잠길 수 있습니다.  

* 사용 약관에 조건에 동의해야 합니다.  

* 카메라를 사용하지 않도록 설정합니다. 이 정책의 목적은 소유권이 있는 정보를 찍지 못하게 차단하고, 학습 환경에 방해가 되는 요인을 제거하는 것입니다. 학교에서는 학생들이 테스트 자료를 공유할 수 없도록 교실 디바이스에서 카메라를 해제할 수 있습니다.  

* 디바이스의 모든 데이터를 암호화하도록 요구합니다. 디바이스를 분실하거나 도난당한 경우 이 정책은 디바이스의 데이터를 보호하는 데 도움이 됩니다. 또한 디바이스와 앱 간에 공유되는 데이터를 보호합니다. 

## <a name="next-steps"></a>다음 단계  

도움이 필요하십니까? 회사 지원팀에 문의하거나(연락처 정보는 [회사 포털 웹 사이트](https://go.microsoft.com/fwlink/?linkid=2010980) 확인) <a href="mailto:wintunedroidfbk@microsoft.com?subject=I'm having trouble installing the Company Portal app on my Android device&body=Describe the issue you're experiencing here.">Microsoft Android 팀</a>으로 메일을 보내세요.
