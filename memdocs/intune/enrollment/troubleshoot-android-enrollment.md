---
title: Microsoft Intune에서 Android 엔터프라이즈 디바이스 문제 해결
description: Intune에서 Android 디바이스를 등록할 때 가장 일반적인 문제 중 일부에 대한 문제를 해결하기 위한 제안입니다.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/25/2020
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: ''
ms.reviewer: mghadial
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: bcc524a69d0fb41da84a2e882b81a205fe7192cc
ms.sourcegitcommit: 3d895be2844bda2177c2c85dc2f09612a1be5490
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79363332"
---
# <a name="troubleshoot-android-enterprise-device-problems-in-microsoft-intune"></a>Microsoft Intune에서 Android 엔터프라이즈 디바이스 문제 해결

이 문서는 Intune 관리자가 Intune에서 Android 엔터프라이즈 디바이스를 등록할 때 나타나는 문제를 이해하고 해결하는 데 도움이 됩니다.

## <a name="apps-on-android-enterprise-devices"></a>Android 엔터프라이즈 디바이스의 앱

### <a name="managed-google-play-apps-that-arent-deployed-through-intune-are-displayed-in-the-work-profile"></a>Intune을 통해 배포되지 않는 관리형 Google Play 앱이 회사 프로필에 표시됨
회사 프로필을 만들 때 디바이스 OEM이 회사 프로필에서 시스템 앱을 사용하도록 설정할 수 있습니다. 이 기능은 MDM 공급자가 제어하지 않습니다.

문제를 해결하려면 다음 단계를 수행합니다.

  1. 회사 포털 로그를 수집합니다.
  2. 회사 프로필에 예기치 않게 표시되는 앱을 확인합니다.
  3. Intune에서 디바이스 등록을 취소하고 회사 포털을 제거합니다.
  4. 테스트를 위해 EMM 없이 회사 프로필 만들기를 허용하는 [Test DPC](https://play.google.com/store/apps/details?id=com.afwsamples.testdpc) 앱을 설치합니다.
  5. [Test DPC](https://play.google.com/store/apps/details?id=com.afwsamples.testdpc)의 지침에 따라 디바이스에 회사 프로필을 만듭니다.
  6. 회사 프로필에 표시되는 앱을 검토합니다. 
  7. 동일한 애플리케이션이 Test DPC 앱에 표시되는 경우 해당 앱은 해당 디바이스의 OEM이 예상한 것입니다.

### <a name="unapproved-managed-google-play-for-work-store-apps-arent-being-removed-from-the-client-apps-page-in-intune"></a>승인되지 않은 관리형 Google Play for Work 스토어 앱이 Intune의 클라이언트 앱 페이지에서 제거되지 않음
이는 예상된 동작입니다.

### <a name="managed-google-play-apps-arent-being-reported-under-the-discovered-apps-blade-in-the-intune-portal"></a>관리형 Google Play 앱이 Intune 포털의 검색된 앱 블레이드 아래에 보고되지 않음
이는 예상된 동작입니다. 회사 프로필에 설치된 시스템 앱만 검색된 앱 블레이드에서 인벤토리에 포함됩니다. 설치된 관리형 Google Play 애플리케이션을 보려면 **관리형 앱** 블레이드를 사용합니다.

### <a name="are-web-applications-supported-for-work-profile-enrolled-devices"></a>회사 프로필에 등록된 디바이스에서 웹 애플리케이션이 지원되나요?
예. 자세한 내용은 [관리형 Google Play 웹 링크](../apps/apps-add-android-for-work.md#managed-google-play-web-links)를 참조하세요.

## <a name="device-management"></a>디바이스 관리

### <a name="file-path-internal-storageandroiddatacommicrosoftwindowsintunecompanyportalfiles-missing-on-work-profile-enrolled-devices"></a>파일 경로 Internal storage/Android/Data.com.microsoft.windowsintune.companyportal/files가 회사 프로필 등록 디바이스에 없음

  **대답**: 이는 예상된 동작입니다. 이 경로는 디바이스 관리자(레거시 Android 등록) 시나리오의 경우에만 생성됩니다.

  회사 포털 로그를 수집하려면 다음 단계를 수행합니다.

  1. 배지가 있는 회사 포털 앱에서 **메뉴** > **도움말** > **메일 지원**을 탭한 다음, **메일 보내기 및 로그 업로드**를 탭합니다. 
  2. **다음과 관련된 도움 요청 보내기**라는 메시지가 표시되면 메일 앱 중 하나를 선택합니다.
  3. Microsoft 기술 지원에 제공할 수 있는 인시던트 ID가 포함된 IT 관리자에 대한 메일이 생성됩니다.

### <a name="managed-google-play-last-sync-time--hasnt-been-updated-in-days"></a>관리형 Google Play 마지막 동기화 시간이 업데이트되지 않음
이는 예상된 동작입니다. 동기화는 수동으로 수행하는 경우에만 트리거됩니다.

### <a name="encryption-is-required-when-a-device-is-enrolled-can-it-be-turned-off"></a>디바이스가 등록되면 암호화가 필요합니다. 기능을 끌 수 있나요?
아니요. Google에서는 회사 프로필을 만들려면 디바이스를 암호화하도록 요구합니다. 

### <a name="samsung-devices-are-blocking-the-use-of-third-party-keyboards-like-swiftkey"></a>Samsung 디바이스가 SwiftKey 같은 타사 키보드의 사용을 차단함
Samsung은 Android 8.0 이상 디바이스에서 이 제한을 적용하기 시작했습니다. Microsoft는 현재 이 문제를 해결하기 위해 Samsung과 협력하고 있으며 새 정보를 사용할 수 있는 경우 게시할 예정입니다.

## <a name="remote-actions"></a>원격 작업

### <a name="wipe-factory-reset-option-isnt-available-for-work-profile-enrolled-device"></a>초기화 옵션은 회사 프로필 등록 디바이스에 사용할 수 없음
이는 예상된 동작입니다. 회사 프로필 시나리오에서 MDM 공급자는 디바이스를 완전히 제어할 수 없습니다. 사용할 수 있는 유일한 옵션은 전체 회사 프로필과 모든 관련 콘텐츠를 제거하는 사용 중지(회사 데이터 제거)입니다.

### <a name="is-device-passcode-reset-supported"></a>디바이스 암호 다시 설정이 지원되나요?
회사 프로필 등록 디바이스의 경우 Android 8.0 이상 디바이스에서 회사 프로필 암호를 다시 설정할 수 있는 경우는 다음과 같습니다.
- 회사 프로필 암호가 관리되는 경우
- 최종 사용자가 암호 다시 설정을 허용한 경우

전용 디바이스(COSU) 및 완전 관리형의 경우 디바이스 암호 다시 설정이 지원됩니다.


## <a name="next-steps"></a>다음 단계

- [Intune에서 디바이스 등록 문제 해결](troubleshoot-device-enrollment-in-intune.md)
- [Intune 포럼에서 질문하기](https://social.technet.microsoft.com/Forums/%7Blang-locale%7D/home?category=microsoftintune&filter=alltypes&sort=lastpostdesc)
- [Microsoft Intune 지원 팀 블로그 보기](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/bg-p/IntuneCustomerSuccess)
- [Microsoft Enterprise Mobility + Security 블로그 보기](https://techcommunity.microsoft.com/t5/Azure-Active-Directory-Identity/Announcing-the-public-preview-of-Azure-AD-group-based-license/ba-p/245210)