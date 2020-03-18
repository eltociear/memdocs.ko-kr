---
title: Microsoft Intune에 iOS 스토어 앱 추가
titleSuffix: ''
description: Microsoft Intune에 iOS 스토어 앱을 추가하는 방법을 알아봅니다. App Store에서 무료로 제공되는 앱은 이 방법을 사용하여 할당할 수 있습니다.
keywords: Intune
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/22/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: c59514d7-1256-4576-9380-e7a0b85a0378
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 10df5802483a89de2fb82e2a29ca43fb542c9ae8
ms.sourcegitcommit: 3d895be2844bda2177c2c85dc2f09612a1be5490
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79343832"
---
# <a name="add-ios-store-apps-to-microsoft-intune"></a>Microsoft Intune에 iOS 스토어 앱 추가

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

이 아티클의 정보를 사용하면 Microsoft Intune에 iOS 스토어 앱을 추가하는 데 도움이 됩니다. iOS 스토어 앱은 Intune이 사용자 디바이스에 설치하는 앱입니다. 사용자는 회사의 직원입니다. iOS 스토어 앱은 자동으로 업데이트됩니다.

>[!NOTE]
>iOS/iPadOS 디바이스 사용자는 주식, 지도 같은 일부 기본 제공 iOS/iPadOS 앱을 제거할 수 있으나 Intune을 사용하여 해당 앱을 다시 배포할 수는 없습니다. 사용자가 이러한 앱을 삭제하는 경우 앱 스토어로 이동해서 수동으로 다시 설치해야 합니다.

## <a name="before-you-start"></a>시작하기 전에

앱 스토어에서 무료인 경우에만 이 방법으로 앱을 할당할 수 있습니다. Intune을 사용하여 유료 앱을 할당하려면 [iOS/iPadOS Volume-Purchase Program](vpp-apps-ios.md)을 사용하는 것이 좋습니다.

>[!NOTE]
>Microsoft Intune에서 작업하는 경우 Microsoft Edge 또는 Google Chrome 브라우저를 사용하는 것이 좋습니다.

1. [Microsoft Endpoint Manager 관리 센터](https://go.microsoft.com/fwlink/?linkid=2109431)에 로그인합니다.
2. **앱** > **모든 앱** > **추가**를 선택합니다.
3. **앱 유형 선택** 창의 사용 가능한 **스토어 앱** 유형 아래에서 **iOS 스토어 앱**을 선택합니다.
4. **선택**을 클릭합니다.<br>
   **앱 추가** 단계가 표시됩니다.
5. **앱 스토어 검색**을 선택합니다.
6. **앱 스토어 검색** 창에서 앱 스토어 국가/지역 로캘을 선택합니다.
7. **검색** 상자에서 앱 이름(또는 이름의 일부)을 입력합니다.  
    Intune에서 스토어를 검색하고 관련 결과의 목록을 반환합니다.
8. 결과 목록에서 원하는 앱을 선택한 다음, **선택**을 선택합니다.<br>

   **앱 정보** 페이지가 **앱 추가** 창에 표시됩니다. 가능한 경우 스토어에서 선택한 앱에 따라 앱 정보가 추가됩니다.

9. **앱 정보** 페이지에서 앱 세부 정보를 추가합니다. 선택한 앱에 따라 이 창의 일부 값이 자동으로 채워질 수 있습니다.
    - **이름**: 회사 포털에 표시하려는 앱 이름을 입력합니다. 사용하는 모든 앱 이름이 고유한지 확인합니다. 앱 이름이 중복될 경우 한 이름만 회사 포털에서 사용자에게 표시됩니다.
    - **설명**: 앱에 대한 설명을 입력합니다. 이 설명은 회사 포털에서 사용자에게 표시됩니다.
    - **게시자**: 앱 게시자의 이름을 입력합니다.
    - **앱 스토어 URL**: 만들려는 앱의 App Store URL을 입력합니다.
    - **최소 운영 체제**: 목록에서 앱을 설치할 수 있는 가장 오래된 운영 체제 버전을 선택합니다. 이전 버전의 운영 체제를 사용하는 디바이스에 앱을 할당할 경우 앱이 설치되지 않습니다.
    - **적용 가능한 디바이스 유형**: 목록에서 앱에서 사용하는 디바이스를 선택합니다.
    - **범주**: 필요한 경우, 기본 제공 앱 범주 중 하나 이상 또는 사용자가 만든 범주를 선택합니다. 이렇게 하면 사용자가 회사 포털을 찾아볼 때 앱을 더 쉽게 찾을 수 있습니다.
    - **회사 포털에서 이 항목을 추천 앱으로 표시**: 사용자가 앱을 찾아볼 때 회사 포털의 기본 페이지에 앱 제품군을 눈에 띄게 표시하려면 이 옵션을 선택합니다.
    - **정보 URL**: 필요에 따라 이 앱에 대한 정보를 포함하는 웹 사이트의 URL을 입력합니다. URL은 회사 포털에서 사용자에게 표시됩니다.
    - **개인정보취급방침 URL**: 필요에 따라 이 앱에 대한 개인정보 관련 정보를 포함하는 웹 사이트의 URL을 입력합니다. URL은 회사 포털에서 사용자에게 표시됩니다.
    - **개발자**: 선택적으로, 앱 개발자의 이름을 입력합니다. 이 필드는 관리자에게만 표시되며 사용자에게 표시되지 않습니다.
    - **소유자**: 필요한 경우 이 앱의 소유자 이름을 입력합니다(예: *HR 부서*). 이 필드는 관리자에게만 표시되며 사용자에게 표시되지 않습니다.
    - **메모**: 선택 사항으로, 이 앱과 연결할 모든 메모를 입력합니다. 이 필드는 관리자에게만 표시되며, 최종 사용자에게는 표시되지 않습니다.
    - **로고**: 필요한 경우 앱과 연결할 아이콘을 업로드합니다. 사용자가 회사 포털을 찾아볼 때 이 아이콘이 앱과 함께 표시됩니다.
10. **다음**을 클릭하여 **범위 태그** 페이지를 표시합니다.
11. **범위 태그 선택**을 클릭하여 앱의 범위 태그를 선택적으로 추가합니다. 자세한 내용은 [분산형 IT에 RBAC(역할 기반 액세스 제어) 및 범위 태그 사용](../fundamentals/scope-tags.md)을 참조하세요.
12. **다음**을 클릭하여 **할당** 페이지를 표시합니다.
13. 앱의 그룹 할당을 선택합니다. 자세한 내용은 [그룹을 추가하여 사용자 및 디바이스 구성](../fundamentals/groups-add.md)을 참조하세요. 
14. **다음**를 클릭하여 **검토 + 만들기** 페이지를 표시합니다. 앱에 대해 입력한 값과 설정을 검토합니다.
15. 완료되면 **만들기**를 클릭하여 Intune에 앱을 추가합니다.

만든 앱의 **개요 블레이드**가 표시됩니다.

## <a name="next-steps"></a>다음 단계

- [그룹에 앱 할당](apps-deploy.md)
