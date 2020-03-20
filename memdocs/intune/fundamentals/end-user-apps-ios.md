---
title: iOS/iPadOS 사용자가 앱을 얻는 방법
description: 최종 사용자에게 iOS/iPadOS 앱을 제공하기 위한 방법
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 03/11/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 7e3135c1-df26-48c9-aa4c-cdab6168897a
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 957c63c760dcc576ab30bb85440d52833307818d
ms.sourcegitcommit: 3d895be2844bda2177c2c85dc2f09612a1be5490
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79344092"
---
# <a name="how-your-iosipados-users-get-their-apps"></a>iOS/iPadOS 사용자가 앱을 얻는 방법

이 정보를 사용하여 최종 사용자가 Microsoft Intune을 통해 배포하는 앱을 얻는 방법과 위치를 이해합니다.

**필요한 앱**--플랫폼에 따라 최소한의 사용자 작업으로 디바이스에 설치되며, 관리자에게 필요한 앱입니다.

**사용 가능한 앱**--회사 포털 앱 목록에 제공되며, 사용자가 필요에 따라 선택하여 설치할 수 있는 앱입니다.

**관리되는 앱**--정책을 통해 관리할 수 있고 Intune에서 "래핑"했거나 Intune 앱 SDK(소프트웨어 개발 키트)로 빌드된 앱입니다. 이러한 앱은 Intune에서 관리할 수 있고, 앱 보호 정책을 적용할 수 있습니다.

**관리되지 않는 앱**--사용자가 Intune 앱 SDK와 연결되지 않은 iOS/iPadOS App Store에서 다운로드할 수 있는 앱입니다. Intune은 이러한 앱의 배포, 관리 또는 선택적 초기화를 제어하지 않습니다.  

등록된 사용자는 회사 포털 앱의 앱 화면에서 다음 타일을 탭하여 앱을 얻습니다.

- **모든 앱**은 [회사 포털 웹 사이트](https://portal.manage.microsoft.com)의 모두 탭에 있는 모든 앱 목록을 가리킵니다.

- **추천 앱**을 선택하면 회사 포털 웹 사이트의 추천 탭으로 이동합니다.

- **범주**는 회사 포털 웹 사이트의 범주 탭을 가리킵니다.

![iOS 회사 포털 앱 화면](./media/end-user-apps-ios/ios-cp-app-main-apps-screen.png)

앱을 추가하는 방법에 대한 자세한 내용은 [Microsoft Intune에 앱을 추가하는 방법](../apps/apps-add.md)을 참조하세요.

## <a name="app-management-takeover"></a>앱 관리 인수
앱이 최종 사용자의 디바이스에 이미 설치된 경우 iOS/iPadOS 디바이스는 조직에서 앱을 관리할 수 있도록 경고를 표시합니다. 최종 사용자는 조직이 앱 관리를 수행하도록 허용해야 관리되는 디바이스에 앱 구성을 적용할 수 있습니다. 사용자가 경고를 취소하면 디바이스가 관리되고 앱이 할당되는 동안 주기적으로 경고가 표시됩니다.  


![취소 및 관리 옵션을 보여 주는 앱 관리 변경 경고의 이미지.](./media/end-user-apps-ios/intune-app-management-confirmation-2002.png)

## <a name="see-also"></a>참고 항목  

[Android 사용자가 앱을 얻는 방법](end-user-apps-android.md)

[Windows 사용자가 앱을 얻는 방법](end-user-apps-windows.md)
