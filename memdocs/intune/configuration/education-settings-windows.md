---
title: Microsoft Intune의 Windows 10 교육 설정 - Azure | Microsoft Docs
description: Windows 10 디바이스에 대한 모든 교육 설정 목록을 참조하세요. 테스트 실행 앱이 있는 디바이스 구성 프로필에서 이 설정을 사용하고, 사용자 또는 학생이 로그인하는 방법을 선택하고, 테스트 중에 화면을 모니터링하는 등의 작업을 Intune에서 수행할 수 있습니다.
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 07/03/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 6f4de4bd-3dde-4a8d-8e22-46c5d06c3eea
ms.reviewer: kakyker
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 39f881b05c9698a8560fe009331fac3389b35bde
ms.sourcegitcommit: 3d895be2844bda2177c2c85dc2f09612a1be5490
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79364294"
---
# <a name="configure-the-take-a-test-app-on-windows-10-devices-using-intune"></a>Intune을 사용하여 Windows 10 디바이스에서 테스트 실행 앱 구성

시험 응시 앱을 사용하면 Windows 10 디바이스에서 진행되는 수업의 온라인 시험을 안전하게 관리할 수 있습니다. 시험 응시 앱을 설정하려면 Intune에서 디바이스 구성 프로필을 만들고 보안 평가 설정을 구성해야 합니다. 이 문서에서는 시험 응시 앱에 대해 찾을 수 있는 설정을 설명합니다. 

프로필을 구성한 후 학생에게 할당하고 배포합니다. 

[Intune의 테스트 실행 앱](education-settings-configure.md)은 이 기능에 대한 자세한 정보를 제공합니다.

## <a name="before-you-begin"></a>시작하기 전에

[디바이스 구성 프로필을 만듭니다](education-settings-configure.md#create-a-device-profile).

## <a name="take-a-test-settings"></a>테스트 설정 가져오기
디바이스 구성 프로필을 만든 후 **프로필 유형**으로 이동하여 **보안 평가(교육)** 를 선택합니다. 다음과 같은 시험 응시 앱 설정을 찾을 수 있습니다. 


- **계정 유형**: 사용자가 테스트에 로그인하는 방법을 선택합니다. 옵션은 다음과 같습니다.
  - Azure AD 계정
  - 도메인 계정
  - 로컬 계정
  - 로컬 게스트 계정: Windows 10 버전 1903 이상을 실행하는 디바이스에서만 사용할 수 있습니다.    
- **계정 사용자 이름**: 테스트 실행 앱에 사용되는 계정의 사용자 이름을 입력합니다. 다음 형식으로 계정을 입력할 수 있습니다.
  - `user@contoso.com`
  - `domain\username`
  - `user@contoso.com`
  - `computerName\username`
- **계정 이름**: 로컬 게스트 계정 유형을 설정하려면 시험 응시 앱에서 사용된 계정의 이름을 입력합니다. 계정 이름이 로그인 화면에 타일로 나타납니다. 학생은 타일을 클릭하여 시험을 시작합니다.  
- **평가 URL**: 사용자가 수행할 테스트의 URL을 입력합니다. URL을 가져오는 방법에 대한 자세한 내용은 [시험 응시 설명서](https://docs.microsoft.com/education/windows/take-tests-in-windows-10)를 참조하세요.
- **프린터 연결**: 프린터에 연결된 디바이스에서만 시험 응시 앱에 액세스하도록 허용하려면 **필수**를 선택합니다. 이 설정을 사용하면 앱의 인쇄 단추를 시험 응시자도 사용할 수 있게 됩니다. **구성되지 않음**을 사용하면 학생들이 프린터에 연결되지 않은 디바이스에서 앱에 액세스할 수 있습니다.  
- **화면 모니터링**: 사용자가 테스트를 수행하는 동안 화면 작업을 모니터링하도록 **허용**을 선택합니다. **구성되지 않음** 테스트 중에 화면을 모니터링하지 못하도록 합니다.
- **텍스트 제안**: 시험 응시자가 텍스트 제안을 볼 수 있도록 **허용**을 선택합니다. **구성되지 않음** 사용자가 테스트를 수행하는 동안 텍스트 제안을 차단합니다.

## <a name="next-steps"></a>다음 단계

[프로필을 할당](device-profile-assign.md)하고, [해당 상태를 모니터링](device-profile-monitor.md)합니다.
