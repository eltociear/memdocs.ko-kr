---
title: Microsoft Intune에 웹앱 추가
titleSuffix: ''
description: Microsoft Intune에 웹앱(클라이언트-서버 애플리케이션)을 추가하는 방법을 알아봅니다.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/22/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 5f08752f-0e87-4ad9-a34c-4991b3150775
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 3fc6b9fc427ab6e0dc0488061378e78060527676
ms.sourcegitcommit: 3d895be2844bda2177c2c85dc2f09612a1be5490
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79361980"
---
# <a name="add-web-apps-to-microsoft-intune"></a>Microsoft Intune에 웹앱 추가

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Intune은 웹앱을 포함하여 다양한 앱 유형을 지원합니다. 웹앱은 클라이언트-서버 애플리케이션입니다. 서버는 UI, 콘텐츠 및 기능을 포함하는 웹앱을 제공합니다. 또한 플랫폼을 호스팅하는 현대식 웹은 일반적으로 보안, 부하 분산 및 기타 이점을 제공합니다. 웹앱은 웹에서 별도로 유지 관리됩니다. Microsoft Intune을 사용하여 이 앱 유형을 가리킵니다. 또한 이 앱에 액세스할 수 있는 사용자 그룹을 할당합니다. 

사용자의 앱을 관리하고 할당하려면 먼저 Intune에 앱을 추가합니다. 

Intune이 사용자의 디바이스에 웹앱 바로 가기를 만듭니다. iOS/iPadOS 디바이스의 경우 웹앱에 대한 바로 가기가 홈 화면에 추가됩니다. Android 디바이스 관리자 디바이스의 경우 웹앱에 대한 바로 가기가 Intune 회사 포털 위젯에 추가되고 사용자가 위젯을 수동으로 고정해야 합니다. Windows 디바이스의 경우 웹앱에 대한 바로 가기가 시작 메뉴에 배치됩니다.

> [!Note]
> 웹앱을 시작하려면 사용자의 디바이스에 브라우저가 설치되어 있어야 합니다. 

> [!Note]
> Android Enterprise 디바이스에 대해서는 [관리형 Google Play 웹 링크](apps-add-android-for-work.md#managed-google-play-web-links)를 참조하세요.

## <a name="add-a-web-app-to-intune"></a>Intune에 웹앱 추가
Intune에 앱을 웹용 앱의 바로 가기로 추가하려면 다음 작업을 수행하세요.

1. [Microsoft Endpoint Manager 관리 센터](https://go.microsoft.com/fwlink/?linkid=2109431)에 로그인합니다.
2. **앱** > **모든 앱** > **추가**를 선택합니다.
3. **앱 유형 선택** 창의 사용 가능한 **기타** 유형 아래에서 **웹 링크**를 선택합니다.
4. **선택**을 클릭합니다. **앱 추가** 단계가 표시됩니다.
5. **앱 정보** 페이지에서 다음 정보를 추가합니다.
    - **이름**:  회사 포털에 표시하려는 앱 이름을 입력합니다. 

        > [!NOTE]
        > 앱을 배포하고 설치한 뒤에 Intune Azure Portal에서 앱의 이름을 변경하면 더 이상 명령을 사용하여 앱을 대상으로 지정할 수 없습니다.

    - **설명**: 앱에 대한 설명을 입력합니다. 이 설명은 회사 포털에서 사용자에게 표시됩니다.
    - **게시자**: 이 앱 게시자의 이름을 입력합니다.
    - **앱 URL**: 할당할 앱을 호스트하는 웹 사이트의 URL을 입력합니다.
    - **범주**: 필요한 경우, 기본 제공 앱 범주 중 하나 이상 또는 사용자가 만든 범주를 선택합니다. 이렇게 하면 사용자가 회사 포털을 찾아볼 때 앱을 더 쉽게 찾을 수 있습니다.
    - **회사 포털에서 이 항목을 추천 앱으로 표시**: 사용자가 앱을 찾아볼 때 회사 포털의 기본 페이지에 앱 제품군을 눈에 띄게 표시하려면 이 옵션을 선택합니다.
    - **이 링크를 열려면 Managed Browser가 필요**: Intune Managed Browser에서 열 수 있는 웹 사이트 또는 웹앱 링크를 사용자에게 할당하려면 이 옵션을 선택합니다. 이 브라우저는 디바이스에 설치되어 있어야 합니다.
    - **로고**: 앱과 연결할 아이콘을 업로드합니다. 사용자가 회사 포털을 찾아볼 때 이 아이콘이 앱과 함께 표시됩니다.
6. **다음**을 클릭하여 **범위 태그** 페이지를 표시합니다.
7. **범위 태그 선택**을 클릭하여 앱의 범위 태그를 선택적으로 추가합니다. 자세한 내용은 [분산형 IT에 RBAC(역할 기반 액세스 제어) 및 범위 태그 사용](../fundamentals/scope-tags.md)을 참조하세요.
8. **다음**을 클릭하여 **할당** 페이지를 표시합니다.
9. 앱의 그룹 할당을 선택합니다. 자세한 내용은 [그룹을 추가하여 사용자 및 디바이스 구성](../fundamentals/groups-add.md)을 참조하세요. 
10. **다음**를 클릭하여 **검토 + 만들기** 페이지를 표시합니다. 앱에 대해 입력한 값과 설정을 검토합니다.
11. 완료되면 **만들기**를 클릭하여 Intune에 앱을 추가합니다.

    만든 앱의 **개요 블레이드**가 표시됩니다.

> [!Note]
> 현재 iOS/iPadOS 디바이스로 Intune 웹앱 배포는 관리 프로필과 연결되어 있어 수동으로 제거할 수 없습니다. Intune 포털에서 배포 유형을 **제거**로 변경하면 웹앱을 자동으로 제거할 수 있습니다. 그러나 앱 할당 의도를 **제거**로 변경하기 전에 배포를 제거하면 디바이스가 Intune에서 등록 취소될 때까지 웹앱은 영구히 남아 있습니다.

최종 사용자는 웹앱을 선택한 다음 **브라우저에서 열기** 옵션을 선택하여 Windows 회사 포털 앱에서 직접 웹앱을 시작할 수 있습니다. 게시된 웹 URL이 웹 브라우저에서 직접 열립니다. 

## <a name="next-steps"></a>다음 단계

만든 앱이 앱 목록에 표시되며, 여기서 이 앱을 선택한 그룹에 할당할 수 있습니다. 도움말은 [그룹에 앱 할당](apps-deploy.md)을 참조하세요. 
