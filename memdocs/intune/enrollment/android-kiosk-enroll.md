---
title: Android 엔터프라이즈 전용 디바이스의 Intune 등록 설정
titleSuffix: Microsoft Intune
description: Intune에서 Android 엔터프라이즈 전용 디바이스를 등록하는 방법에 대해 알아봅니다.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 1/15/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: chmaguir
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure;seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: b3ceb5c08e443bad42a0983b2b8257b997ca537c
ms.sourcegitcommit: 3d895be2844bda2177c2c85dc2f09612a1be5490
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79359705"
---
# <a name="set-up-intune-enrollment-of-android-enterprise-dedicated-devices"></a>Android 엔터프라이즈 전용 디바이스의 Intune 등록 설정

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Android 엔터프라이즈는 전용 디바이스 솔루션 집합을 통해 회사 소유의 일회용 키오스크 스타일 디바이스를 지원합니다. 이러한 디바이스는 몇 가지 예로서 디지털 간판, 티켓 인쇄, 재고 관리와 같은 단일 용도로 사용됩니다. 관리자는 제한된 앱 및 웹 링크 집합에 대한 디바이스 사용을 잠급니다. 또한 사용자가 다른 앱을 추가하거나 디바이스에서 다른 작업을 수행하는 것을 방지합니다.

Intune을 통해 Android 엔터프라이즈 전용 디바이스에 앱 및 설정을 배포할 수 있습니다. Android 엔터프라이즈에 대한 자세한 내용은 [Android 엔터프라이즈 요구 사항](https://support.google.com/work/android/answer/6174145?hl=en&ref_topic=6151012)을 참조하세요.

이러한 방식으로 관리하는 디바이스는 사용자 계정 없이 Intune에 등록되며 어떠한 최종 사용자와도 연결되지 않습니다. 개인용 애플리케이션이나 Outlook 또는 Gmail과 같은 사용자별 계정 데이터에 대한 강력한 요구 사항이 있는 앱을 대상으로 만들어진 것은 아닙니다.

## <a name="device-requirements"></a>디바이스 요구 사항

Android 엔터프라이즈 전용 디바이스로 관리하려면 디바이스가 다음 요구 사항을 충족해야 합니다.

- Android OS 버전 5.1 이상.
- 디바이스는 GMS(Google 모바일 서비스) 연결성을 갖춘 Android의 배포를 실행해야 합니다. 디바이스는 GMS를 사용할 수 있어야 하며 GMS에 연결할 수 있어야 합니다.

## <a name="set-up-android-enterprise-dedicated-device-management"></a>Android 엔터프라이즈 전용 디바이스 관리 설정

Android 엔터프라이즈 전용 디바이스 관리를 설정하려면 다음 단계를 따릅니다.

1. 모바일 디바이스 관리를 준비하려면 지침에 따라 [MDM(모바일 디바이스 관리) 기관을 **Microsoft Intune**](../fundamentals/mdm-authority-set.md)으로 설정해야 합니다. 이 항목은 모바일 디바이스 관리에 대해 Intune을 처음 설정할 때 한 번만 설정하면 됩니다.
2. [Intune 테넌트 계정을 관리형 Google Play 계정에 연결](connect-intune-android-enterprise.md)합니다.
3. [등록 프로필을 만듭니다.](#create-an-enrollment-profile)
4. [디바이스 그룹을 만듭니다](#create-a-device-group).
5. [전용 디바이스를 등록합니다](#enroll-the-dedicated-devices).

### <a name="create-an-enrollment-profile"></a>등록 프로필 만들기

> [!NOTE]
> 토큰이 만료된 경우 토큰에 연결된 프로필은 **디바이스 등록** > **Android 등록** > **회사 소유 전용 디바이스**에 표시되지 않습니다. 활성 토큰과 비활성 토큰 모두에 연결된 모든 프로필을 보려면 **필터**를 클릭하고 "활성" 및 "비활성" 정책 상태의 확인란을 모두 선택합니다. 

전용 디바이스를 등록할 수 있도록 등록 프로필을 만들어야 합니다. 프로필이 만들어지면 등록 토큰(임의 문자열) 및 QR 코드를 제공합니다. Android OS 및 디바이스 버전에 따라 토큰 또는 QR 코드를 사용하여 [전용 디바이스를 등록](#enroll-the-dedicated-devices)할 수 있습니다.

1. [Microsoft Endpoint Manager 관리 센터](https://go.microsoft.com/fwlink/?linkid=2109431)에 로그인하여 **디바이스** > **Android** > **Android 등록** > **회사 소유의 전용 디바이스**를 선택합니다.
2. **만들기**를 선택하고 필수 필드를 작성합니다.
    - **이름**: 프로필을 동적 디바이스 그룹에 할당할 때 사용할 이름을 입력합니다.
    - **토큰 만료 날짜**: 토큰이 만료되는 날짜입니다. Google은 최대 90일을 적용합니다.
3. **만들기**를 선택하여 프로필을 저장합니다.

### <a name="create-a-device-group"></a>디바이스 그룹 만들기

앱 및 정책의 대상을 할당된 디바이스 그룹이나 동적 디바이스 그룹으로 지정할 수 있습니다. 다음 단계에 따라 특정 등록 프로필에 등록된 디바이스를 자동으로 채우도록 동적 AAD 디바이스 그룹을 구성할 수 있습니다.

1. [Microsoft Endpoint Manager 관리 센터](https://go.microsoft.com/fwlink/?linkid=2109431)에 로그인한 후 에서 **그룹** > **모든 그룹** > **새 그룹**을 선택합니다.
2. **그룹** 블레이드에서 다음과 같은 필수 필드를 입력합니다.
    - **그룹 유형**: 보안
    - **그룹 이름**: 직관적인 이름(예: 팩터리 1 디바이스)
    - **멤버 자격 유형**: 동적 디바이스
3. **동적 쿼리 추가**를 선택합니다.
4. **동적 멤버 관리 규칙** 블레이드에서 다음과 같은 필드를 입력합니다.
    - **동적 멤버 관리 규칙 추가**: 단순 규칙
    - **다음 위치에 디바이스 추가**: enrollmentProfileName
    - 가운데 상자에서 **같음**을 선택합니다.
    - 마지막 필드에 이전에 만든 등록 프로필 이름을 입력합니다.
    동적 멤버 관리 규칙에 대한 자세한 내용은 [AAD에서 그룹에 대한 동적 멤버 관리 규칙](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-dynamic-membership)을 참조하세요. 
5. **쿼리 추가** > **만들기**를 선택합니다.

### <a name="replace-or-remove-tokens"></a>토큰 교체 또는 제거

- **토큰 바꾸기**: 토큰 바꾸기를 사용하여 만료일이 임박했을 때 새 토큰/QR 코드를 생성할 수 있습니다.
- **토큰 해지**: 토큰/QR 코드를 즉시 만료시킬 수 있습니다. 이 시점부터 토큰/QR 코드를 더 이상 사용할 수 없습니다. 다음과 같은 경우 이 옵션을 사용할 수 있습니다.
  - 토큰/QR 코드를 권한이 없는 사람과 실수로 공유
  - 모든 등록을 완료하고 더 이상 토큰/QR 코드가 필요하지 않음

토큰/QR 코드를 교체하거나 취소해도 이미 등록된 디바이스에는 영향을 주지 않습니다.

1. [Microsoft Endpoint Manager 관리 센터](https://go.microsoft.com/fwlink/?linkid=2109431)에 로그인하여 **디바이스** > **Android** > **Android 등록** > **회사 소유의 전용 디바이스**를 선택합니다.
2. 사용하려는 프로필을 선택합니다.
3. **토큰**을 선택합니다.
4. 토큰을 바꾸려면 **토큰 바꾸기**를 선택합니다.
5. 토큰을 해지하려면 **토큰 해지**를 선택합니다.

## <a name="enroll-the-dedicated-devices"></a>전용 디바이스 등록

이제 [전용 디바이스를 등록](android-dedicated-devices-fully-managed-enroll.md)할 수 있습니다.

> [!NOTE]
> 전용 디바이스를 등록하는 동안 **Microsoft Intune** 앱이 자동으로 설치됩니다.  이 앱은 등록에 필요하며 제거할 수 없습니다. 

## <a name="managing-apps-on-android-enterprise-dedicated-devices"></a>Android 엔터프라이즈 전용 디바이스에서 앱 관리

할당 유형이 [필수로 설정](../apps/apps-deploy.md#assign-an-app)된 앱만 Android 엔터프라이즈 전용 디바이스에 설치할 수 있습니다. 앱은 Android 엔터프라이즈 회사 프로필 디바이스와 동일한 방식으로 관리형 Google Play 스토어에서 설치됩니다.

앱 개발자가 Google Play에 대한 업데이트를 게시하면 관리되는 디바이스에서 앱이 자동으로 업데이트됩니다.

Android 엔터프라이즈 전용 디바이스에서 앱을 제거하려면 다음 중 하나를 수행합니다.
- 필수 앱 배포를 삭제합니다.
- 앱에 대한 제거 배포를 만듭니다.

## <a name="next-steps"></a>다음 단계
- [Android 앱 배포](../apps/apps-deploy.md)
- [Android 구성 정책 추가](../configuration/device-profiles.md)
