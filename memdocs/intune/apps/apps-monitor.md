---
title: 앱 정보 및 할당 모니터링
titleSuffix: Microsoft Intune
description: 사용자 또는 디바이스에 앱을 할당한 후, 이 정보를 사용하여 해당 앱의 상태를 모니터링할 수 있습니다.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 02/27/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 64e5133d-1e23-4ee6-b556-f5d32c0e95da
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 8e6d06bade82dcebd170d7594ce25033382a2634
ms.sourcegitcommit: 3d895be2844bda2177c2c85dc2f09612a1be5490
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79340582"
---
# <a name="monitor-app-information-and-assignments-with-microsoft-intune"></a>Microsoft Intune으로 앱 정보 및 할당 모니터링

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Intune에서는 관리하는 앱 속성을 모니터링하고 앱 할당 상태를 관리하는 몇 가지 방법을 제공합니다.

1. [Microsoft Endpoint Manager 관리 센터](https://go.microsoft.com/fwlink/?linkid=2109431)에 로그인합니다.
2. **앱** > **모든 앱**을 선택합니다.
3. 앱 목록에서 모니터링할 앱을 선택합니다. 그러면 디바이스 상태 및 사용자 상태에 대한 개요를 포함한 앱 창이 표시됩니다.

> [!NOTE]
> **사용 가능** 상태로 배포되는 Android 스토어 앱은 설치 상태를 보고하지 않습니다.
>
> Android Enterprise 회사 프로필 디바이스에 배포된 관리형 Google Play 앱의 경우 Intune을 사용하여 디바이스에 설치된 앱의 상태 및 버전 번호를 볼 수 있습니다. 

## <a name="app-overview-pane"></a>앱 개요 창

앱 창에서는 환경에 있는 앱의 상태에 대한 세부 정보를 검토할 수 있습니다.

### <a name="essentials"></a>Essentials
**필수** 섹션은 앱에 대한 다음 정보를 포함합니다.

 | **앱 세부 정보**            | **설명**                                                      |
|------------------------|------------------------------------------------------------------|
| **게시자**          | 앱의 게시자                                            |
| **운영 체제**   | 앱 운영 체제(Windows, iOS/iPadOS, Android 등) |
| **만든 날짜**             | 해당 수정 버전을 만든 날짜 및 시간 <b>**참고**: IT 관리자가 앱 범주 또는 앱 설명을 변경하는 것과 같이 앱 메타데이터를 변경하면 이 날짜 값이 업데이트됩니다.                        |
| **할당됨**           | 앱이 할당되었는지 여부(**예** 또는 **아니요**).                  |

### <a name="device-and-user-status-graphs"></a>디바이스 및 사용자 상태 그래프
그래프는 다음과 같은 상태의 앱 수를 보여줍니다.

| **디바이스 상태**       | **설명**                                       |
|-----------------------|-------------------------------------------------------|
| **설치됨**         | 설치된 앱의 수입니다.                         |
| **설치 안 됨**     | 설치되지 않은 앱의 수입니다.                     |
| **실패**            | 실패한 설치의 수입니다.                   |
| **설치 보류 중**   | 설치 과정에 있는 앱의 수입니다. |
| **해당 없음**           | 상태를 적용할 수 없는 앱의 수입니다.            |

> [!NOTE]
> **등록 여부와 관계없이 사용 가능**으로 배포된 Android LOB(기간 업무) 앱(.APK)은 등록된 디바이스의 앱 설치 상태만 보고합니다. Intune에 등록되지 않은 디바이스에는 앱 설치 상태를 사용할 수 없습니다.

### <a name="device-install-status"></a>디바이스 설치 상태

메뉴의 **모니터링** 섹션에서 **디바이스 설치 상태**를 선택하면 디바이스 상태 목록이 표시됩니다. 세부 정보 테이블에는 다음 열이 포함되어 있습니다.

| **디바이스 열**      | **설명**                                                                                                                                                                                                                                            |
|----------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **디바이스 이름**      | 디바이스 이름 지정을 허용하는 플랫폼에서 디바이스의 이름입니다. 다른 플랫폼에서 Intune은 다른 속성으로부터 이름을 만듭니다. 이 특성은 다른 디바이스에서 사용할 수 없습니다.                                                                       |
| **사용자 이름**        | 사용자의 이름입니다.                                                                                                                                                                                                                                      |
| **플랫폼**         | 디바이스의 운영 체제(Windows, iOS/iPadOS, Android 등)                                                                                                                                                                                           |
| **버전**          | 앱의 버전 번호입니다. LOB(기간 업무) 앱 및 비즈니스용 Microsoft 스토어 앱의 경우 앱의 전체 버전 번호가 표시됩니다. 전체 버전 번호는 앱의 특정 릴리스를 식별합니다. 번호는 _버전_(_빌드_)으로 표시됩니다. 예: 2.2(2.2.17560800). 표준 스토어 앱의 경우 버전이 표시되지 않습니다. |
| **상태**           | 앱의 상태입니다.                                                                                                                                                                                                                                     |
| **상태 정보**   | 상태의 세부 정보입니다.                                                                                                                                                                                                                                     |
| **마지막 체크 인**    | 디바이스가 Intune과 마지막으로 동기화된 날짜입니다.                                                                                                                                                                                                                  |


### <a name="user-install-status"></a>사용자 설치 상태

메뉴의 **모니터링** 섹션에서 **사용자 설치 상태**를 선택하면 사용자 상태 목록이 표시됩니다. 세부 정보 테이블에는 다음 열이 포함되어 있습니다.

| **사용자 열**     | **설명**                           |
|---------------------|-------------------------------------------|
| **Name**            | Azure Active Directory의 사용자 이름입니다.         |
| **사용자 이름**       | 사용자의 고유한 이름입니다.              |
| **설치**   | 사용자가 설치한 앱의 수입니다. |
| **실패**        | 사용자에 대한 실패한 앱 설치 수입니다.     |
| **설치 안 됨**   | 사용자가 설치하지 않은 앱의 수입니다. |


## <a name="next-steps"></a>다음 단계

- Intune 데이터 작업에 대해 자세히 알아보려면 [Intune 데이터 웨어하우스 사용](../developer/reports-nav-create-intune-reports.md)을 참조하세요.
- 앱 구성 정책에 대한 자세한 내용은 [Intune용 앱 구성 정책](app-configuration-policies-overview.md)을 참조하세요.
