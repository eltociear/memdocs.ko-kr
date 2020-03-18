---
title: Microsoft Intune을 사용하여 macOS 디바이스에 Office 365 설치
titleSuffix: ''
description: Microsoft Intune을 사용하여 macOS 디바이스에 Office 365 앱을 설치하는 방법을 알아봅니다.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/23/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 2372332a-7e3a-4a9c-91a9-86654e0fabe2
ms.reviewer: aiwang
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 1633900e77eedce0bcca477173e647f5d35b1ee8
ms.sourcegitcommit: 3d895be2844bda2177c2c85dc2f09612a1be5490
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79341375"
---
# <a name="assign-office-365-to-macos-devices-with-microsoft-intune"></a>Microsoft Intune을 사용하여 macOS 디바이스에 Office 365 할당

이 앱 유형을 사용하면 macOS 디바이스에 Office 365 2016 앱을 쉽게 할당할 수 있습니다. 이 앱 유형을 사용하면 Word, Excel, PowerPoint, Outlook 및 OneNote를 설치할 수 있습니다. 앱을 더 안전하게 최신 상태로 유지하기 위해 앱과 함께 MAU(Microsoft 자동 업데이트)가 제공됩니다. 원하는 앱이 Intune 콘솔의 앱 목록에 하나의 앱으로 표시됩니다.


## <a name="before-you-start"></a>시작하기 전에

macOS 디바이스에 Office 365를 추가하기 전에 다음 세부 정보를 파악합니다.

- 이 앱을 배포할 디바이스에서 macOS 10.10 이상을 실행하고 있어야 합니다.
- Intune은 Mac용 Office 2016 제품군에 포함된 Office 앱 추가만 지원합니다.
- Intune에서 앱 패키지를 설치할 때 Office 앱이 열리면 저장되지 않은 파일에서 사용자 데이터가 손실될 수 있습니다.

## <a name="select-the-office-365-suite-app-type"></a>Office 365 제품군 앱 유형 선택

1. [Microsoft Endpoint Manager 관리 센터](https://go.microsoft.com/fwlink/?linkid=2109431)에 로그인합니다.
2. **앱** > **모든 앱** > **추가**를 선택합니다.
3. **앱 유형 선택** 창의 **Office 365 제품군** 섹션에서 **macOS**를 선택합니다.
4. **선택**을 클릭합니다. **Office 365 제품군 추가** 단계가 표시됩니다.

## <a name="step-1---app-suite-information"></a>1단계 - 앱 제품군 정보

이 단계에서는 앱 제품군에 대한 정보를 제공합니다. 이 정보를 사용하여 Intune에서 앱 제품군을 식별할 수 있으며, 사용자가 회사 포털에서 앱 제품군을 찾을 수도 있습니다.

1. **앱 제품군 정보** 페이지에서 기본값을 확인하거나 수정할 수 있습니다.
    - **제품군 이름**: 회사 포털에 표시되는 앱 제품군의 이름을 입력합니다. 사용하는 모든 제품군 이름이 고유한지 확인합니다. 같은 앱 패키지 이름이 두 번 나타나는 경우 앱 중 하나만 회사 포털에서 사용자에게 표시됩니다.
    - **제품군 설명**: 앱 제품군에 대한 설명을 입력합니다. 예를 들어 포함하도록 선택한 앱을 나열할 수 있습니다.
    - **게시자**: Microsoft가 게시자로 표시됩니다.
    - **범주**: 필요한 경우, 기본 제공 앱 범주 중 하나 이상 또는 사용자가 만든 범주를 선택합니다. 이 설정을 통해 사용자가 회사 포털을 찾아볼 때 앱 패키지를 더 쉽게 찾을 수 있습니다.
    - **회사 포털에서 이 항목을 추천 앱으로 표시**: 사용자가 앱을 찾아볼 때 회사 포털의 기본 페이지에 앱 제품군을 눈에 띄게 표시하려면 이 옵션을 선택합니다.
    - **정보 URL**: 필요에 따라 이 앱에 대한 정보를 포함하는 웹 사이트의 URL을 입력합니다. URL은 회사 포털에서 사용자에게 표시됩니다.
    - **개인정보취급방침 URL**: 필요에 따라 이 앱에 대한 개인정보 관련 정보를 포함하는 웹 사이트의 URL을 입력합니다. URL은 회사 포털에서 사용자에게 표시됩니다.
    - **개발자**: Microsoft가 개발자로 표시됩니다.
    - **소유자**: Microsoft가 소유자로 표시됩니다.
    - **메모**: 이 앱과 연결할 모든 메모를 입력합니다.
    - **로고**: Office 365 로고는 사용자가 회사 포털을 찾을 때 앱과 함께 표시되는 로고입니다.
2. **다음**을 클릭하여 **범위 태그** 페이지를 표시합니다.

## <a name="step-2---select-scope-tags-optional"></a>2단계 - 범위 태그 선택(선택 사항)
범위 태그를 사용하여 Intune에서 클라이언트 앱 정보를 볼 수 있는 사용자를 결정할 수 있습니다. 범위 태그에 대한 자세한 내용은 [분산형 IT에 역할 기반 액세스 제어 및 범위 태그 사용](../fundamentals/scope-tags.md)을 참조하세요.

1. **범위 태그 선택**을 클릭하여 앱 제품군의 범위 태그를 선택적으로 추가합니다. 
2. **다음**을 클릭하여 **할당** 페이지를 표시합니다.

## <a name="step-3---assignments"></a>3단계 - 할당

1. 앱 제품군에 대해 **필수** 또는 **등록된 디바이스에 사용 가능** 그룹 할당을 선택합니다. 자세한 내용은 [그룹을 추가하여 사용자 및 디바이스 구성](../fundamentals/groups-add.md) 및 [Microsoft Intune을 사용하여 그룹에 앱 할당](apps-deploy.md)을 참조하세요.

    >[!Note]
    > Intune을 통해 macOS용 Office 365 앱 제품군을 제거할 수는 없습니다.

2. **다음**를 클릭하여 **검토 + 만들기** 페이지를 표시합니다. 

## <a name="step-4---review--create"></a>4단계 - 검토 + 만들기

1. 앱 제품군에 대해 입력한 값과 설정을 검토합니다.
2. 완료되면 **만들기**를 클릭하여 Intune에 앱을 추가합니다.

    만든 Office 365 Windows 10 앱 제품군의 **개요 블레이드**가 표시됩니다. 패키지가 앱 목록에 단일 항목으로 표시됩니다.

## <a name="next-steps"></a>다음 단계

- Windows 10 디바이스에 Office 365 앱을 추가하는 방법에 대한 자세한 내용은 [Microsoft Intune을 사용하여 Windows 10 디바이스에 Office 365 ProPlus 2016 앱 할당](apps-add-office365.md)을 참조하세요.
- 사용자 그룹에 앱 할당을 포함하고 제외하는 방법에 대한 자세한 내용은 [앱 할당 포함 및 제외](apps-inc-exl-assignments.md)를 참조하세요.
