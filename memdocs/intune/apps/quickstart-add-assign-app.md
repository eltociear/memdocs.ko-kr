---
title: 빠른 시작 - 클라이언트 앱 추가 및 할당
titleSuffix: Microsoft Intune
description: 이 빠른 시작에서는 Microsoft Intune을 사용하여 클라이언트 앱을 추가하고 할당합니다.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/26/2019
ms.topic: quickstart
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: dab6f5c8-1ebb-42c4-a7a7-7af001f94e15
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: c5b6762669e4d816010982c63a119bffdec2f055
ms.sourcegitcommit: 3d895be2844bda2177c2c85dc2f09612a1be5490
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79334277"
---
# <a name="quickstart-add-and-assign-a-client-app"></a>빠른 시작: 클라이언트 앱 추가 및 할당

이 빠른 시작에서는 Intune을 사용하여 클라이언트 앱을 회사의 직원에 추가하고 할당합니다. 관리자의 우선 순위 중 하나는 최종 사용자가 업무 수행에 필요한 앱을 액세스할 수 있게 하는 것입니다.

Intune 구독이 없으면 [평가판 계정에 등록](../fundamentals/free-trial-sign-up.md)하세요.

## <a name="prerequisites"></a>전제 조건

- 이 빠른 시작을 완료하려면 [사용자 만들기](../fundamentals/quickstart-create-user.md), [그룹 만들기](../fundamentals/quickstart-create-group.md) 및 [디바이스 등록](../enrollment/quickstart-setup-auto-enrollment.md)을 해야 합니다.

## <a name="sign-in-to-intune"></a>Intune에 로그인

[Intune](https://aka.ms/intuneportal)에 [전역 관리자 또는 Intune 서비스 관리자](../fundamentals/users-add.md#types-of-administrators)로 로그인합니다. Intune 평가판 구독을 만든 경우 구독을 만든 계정은 글로벌 관리자입니다.

## <a name="add-the-client-app-to-intune"></a>Intune에 클라이언트 앱 추가

Intune이 앱의 측면을 관리할 수 있도록 앱을 포함할 수 있습니다. 

다음 단계에 따라 Intune에 앱을 추가할 수 있습니다.

1. [Intune](https://aka.ms/intuneportal)에서 **앱** > **모든 앱** > **추가**를 선택합니다. 
2. **앱 유형 선택** 창의 **Office 365 제품군** 섹션에서 **Windows 10**을 선택합니다.
3. **선택**을 클릭합니다. **앱 추가** 단계가 표시됩니다.
4. **앱 제품군 정보** 페이지에서 기본 세부 정보를 확인합니다.
5. **다음**을 클릭하여 **앱 제품군 구성** 페이지를 표시합니다.
6. **채널 업데이트** 옆 드롭다운 상자에서 **매월**을 선택합니다.
7. ***앱 제품군 구성** 페이지의 나머지 기본 정보를 확인합니다.
8. **다음**을 클릭하여 **범위 태그** 페이지를 표시합니다.
9. **범위 태그 선택**을 클릭하여 앱의 범위 태그를 선택적으로 추가합니다. 자세한 내용은 [분산형 IT에 RBAC(역할 기반 액세스 제어) 및 범위 태그 사용](../fundamentals/scope-tags.md)을 참조하세요.
10. **다음**을 클릭하여 **할당** 페이지를 표시합니다.
11. 앱의 그룹 할당을 선택합니다. 자세한 내용은 [그룹을 추가하여 사용자 및 디바이스 구성](../fundamentals/groups-add.md)을 참조하세요.
12. **다음**를 클릭하여 **검토 + 만들기** 페이지를 표시합니다. 앱에 대해 입력한 값과 설정을 검토합니다.
13. 완료되면 **만들기**를 클릭하여 Intune에 앱을 추가합니다.

## <a name="assign-the-app-to-a-group"></a>그룹에 앱 할당

Microsoft Intune에 앱을 추가한 후 사용자와 다바이스 그룹에 해당 앱을 할당할 수 있습니다.

> [!NOTE]
> 이 빠른 시작은 이 시리즈의 이전 빠른 시작에서 빌드합니다. 자세한 정보는 이 빠른 시작의 [필수 구성 요소](quickstart-add-assign-app.md#prerequisites)를 참조하세요.

다음 단계에 따라 그룹에 앱을 할당합니다.

1. [Intune](https://aka.ms/intuneportal)에서 **앱** > **모든 앱**을 선택합니다. 
2. 그룹에 할당하려는 앱을 선택합니다.
3. **할당** > **그룹 추가**를 클릭하여 **그룹 추가** 창을 표시합니다.
4. **할당 유형** 드롭다운 상자에서 **등록된 디바이스에 사용 가능**을 선택합니다. 
5. **포함된 그룹** > **포함할 그룹 선택** > **Contoso 테스터**를 클릭합니다.
6. **선택** > **확인** > **확인** > **저장**을 클릭하여 그룹을 할당합니다.

이제 앱을 **Contoso 테스터** 그룹에 할당했습니다.

## <a name="install-the-app-on-the-enrolled-device"></a>등록된 디바이스에 앱 설치

회사 포털 앱을 설치하고 사용하여 Intune에서 사용할 수 있도록 만든 **Contoso의 할 일(To-Do)** 앱을 설치해야 합니다. 다음 단계에 따라 등록된 디바이스의 사용자가 앱을 사용할 수 있는지 확인합니다.

1. 등록된 Windows 10 Desktop 디바이스에 로그인합니다.

    > [!IMPORTANT]
    > 디바이스는 [Intune에 등록](../enrollment/quickstart-enroll-windows-device.md)되어 있어야 합니다. 또한 앱에 할당한 그룹에 포함된 계정을 사용하여 디바이스에 로그인해야 합니다.

2. **시작** 메뉴에서 **Microsoft Store**를 엽니다. 그런 다음, **회사 포털** 앱을 찾아서 설치합니다.
3. **회사 포털** 앱을 시작합니다.
4. Intune을 사용하여 추가한 앱을 클릭합니다. 이 빠른 시작에서는 **Microsoft Office 365 앱 도구 모음** 앱을 추가했습니다.

    > [!NOTE]
    > Intune 사용자에게 앱을 성공적으로 할당하지 않은 경우 다음과 같은 메시지가 표시됩니다. *IT 관리자가 사용 가능한 앱을 만들지 않았습니다.*

5. **설치**를 클릭합니다.

비즈니스 요구 사항에 따라 회사 포털 앱을 직원에게 할당해야 하는 경우에는 Intune에서 바로 Windows 10 회사 포털 앱을 수동으로 할당할 수 있습니다. 자세한 내용은 [Microsoft Intune을 사용하여 Windows 10 회사 포털 앱 수동으로 추가](company-portal-app.md)를 참조하세요.

## <a name="next-steps"></a>다음 단계

이 빠른 시작에서는 intune에 앱을 추가하고 Windows 10 Desktop 디바이스에 앱을 설치합니다. Intune에서 앱을 관리하는 방법에 대한 자세한 내용은 [Microsoft Intune 앱 관리란?](app-management.md)을 참조하세요.

다음 Intune 빠른 시작을 진행하기 위해서는 아래 빠른 시작 링크를 클릭하세요.

> [!div class="nextstepaction"]
> [빠른 시작: 앱 보호 정책 만들기 및 할당](quickstart-create-assign-app-policy.md)
