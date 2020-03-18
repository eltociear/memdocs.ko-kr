---
title: Microsoft Intune에서 Android 디바이스 관리자 등록
titleSuffix: ''
description: 디바이스 관리자 등록을 사용하여 Intune에 Android 디바이스를 등록합니다.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 07/23/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: chmaguir
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: ebe011c5549762c865eacdc2719e5ec28fdbed8c
ms.sourcegitcommit: 3d895be2844bda2177c2c85dc2f09612a1be5490
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79339711"
---
# <a name="android-device-administrator-enrollment"></a>Android 디바이스 관리자 등록

Android 디바이스 관리자("레거시" Android 관리라고도 하며 Android 2.2를 통해 출시됨)는 Android 디바이스를 관리하는 방법입니다. 그러나 이제 향상된 관리 기능을 [Android Enterprise](https://www.android.com/enterprise/management/)(Android 5.0을 통해 출시)에서 사용할 수 있습니다. 최신의 풍부하고 보다 안전한 디바이스 관리로 전환하기 위해 Google은 새로운 Android 릴리스에서 디바이스 관리자 지원을 줄이고 있습니다.

따라서 이러한 기능 제한을 방지하기 위해서는 아래에 설명된 디바이스 관리자 프로세스를 사용하여 새 디바이스를 등록하지 않는 것이 좋습니다.

같은 이유로, 디바이스가 Android 10으로 업데이트되는 경우 디바이스 관리자 관리와는 다른 방식으로 디바이스를 마이그레이션하는 것이 좋습니다. 

Android 디바이스 관리자 지원과 관련된 Intune 지원에 대한 자세한 내용은 [알림 섹션](../fundamentals/whats-new.md#decreasing-support-for-android-device-administrator)을 참조하세요.

계속해서 사용자가 디바이스 관리자 관리를 사용하여 Android 디바이스를 등록하도록 하려는 경우 다음 섹션을 계속 진행합니다.  

Google의 Android Enterprise 기능에 대한 자세한 내용은 다음 문서를 참조하세요.
- [디바이스 관리자에서 Android Enterprise로 마이그레이션하기 위한 Google 지침](http://static.googleusercontent.com/media/android.com/en/enterprise/static/2016/pdfs/enterprise/Android-Enterprise-Migration-Bluebook_2019.pdf)
- [디바이스 관리자 API 사용 중단 계획에 대한 Google 설명서](https://developers.google.com/android/work/device-admin-deprecation)

## <a name="set-up-device-administrator-enrollment"></a>디바이스 관리자 등록 설정

1. 모바일 디바이스 관리를 준비하려면 MDM 기관을 **Microsoft Intune**으로 설정해야 합니다. 지침은 [MDM 기관 설정](../fundamentals/mdm-authority-set.md)을 참조하세요. 이 항목은 모바일 디바이스 관리에 대해 Intune을 처음 설정할 때 한 번만 설정하면 됩니다.
2. [Microsoft Endpoint Manager 관리 센터](https://go.microsoft.com/fwlink/?linkid=2109431)에 로그인하고 **디바이스** > **Android** > **Android 등록** > **디바이스 관리 권한이 있는 개인 및 회사 소유 디바이스** > **디바이스 관리자를 사용하여 디바이스를 관리합니다.** 로 이동합니다.
3. [사용자에게 디바이스를 등록하는 방법을 알려 줍니다](../user-help/enroll-device-android-company-portal.md).  

사용자가 등록한 후 [규정 준수 정책 할당](../protect/compliance-policy-create-android.md), [앱 관리](../apps/app-management.md) 등을 포함한 Intune에서 디바이스 관리를 시작할 수 있습니다.

다른 사용자 작업에 대한 정보는 다음 문서를 참조하세요.
- [Microsoft Intune에서 최종 사용자 환경 관련 리소스](../fundamentals/end-user-educate.md)
- [Intune에서 Android 디바이스 사용](https://docs.microsoft.com/user-help/using-your-android-device-with-intune)


## <a name="block-device-administrator-enrollment"></a>디바이스 관리자 등록 차단
Android 디바이스 관리자 디바이스를 차단하거나 등록에서 개인적으로 소유한 Android 디바이스 관리자 디바이스를 차단하려면 [디바이스 유형 제한 설정](enrollment-restrictions-set.md)을 참조하세요.


## <a name="next-steps"></a>다음 단계
- [준수 정책 할당](../protect/compliance-policy-create-android.md)
- [앱 관리](../apps/app-management.md)
