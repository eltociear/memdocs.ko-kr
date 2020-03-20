---
title: Microsoft Intune에 macOS 사업 부문 앱을 추가하는 방법
titleSuffix: ''
description: Microsoft Intune에 macOS LOB(기간 업무) 앱을 추가하는 방법을 알아봅니다.
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
ms.assetid: ef8008ac-8b85-4bfc-86ac-1f9fcbd3db76
ms.reviewer: aiwang
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 5d8b0093267ca62094a846a50ae9b9a02c2ef9d8
ms.sourcegitcommit: 3d895be2844bda2177c2c85dc2f09612a1be5490
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79361304"
---
# <a name="how-to-add-macos-line-of-business-lob-apps-to-microsoft-intune"></a>Microsoft Intune에 macOS LOB(사업 부문) 앱을 추가하는 방법

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

이 문서의 정보를 사용하면 Microsoft Intune에 macOS 사업 부문 앱을 추가하는 데 도움이 됩니다. 사업 부문 파일을 Microsoft Intune에 업로드하기 전에 *.pkg* 파일을 전처리하려면 외부 도구를 다운로드해야 합니다. *.pkg* 파일의 전처리는 macOS 디바이스에서 수행해야 합니다.

> [!NOTE]
> macOS Catalina 10.15 릴리스부터 앱을 Intune에 추가하기 전에 macOS LOB 앱이 공증되었는지 확인해야 합니다. LOB 앱 개발자가 앱을 공증하지 않은 경우 사용자의 macOS 디바이스에서 앱이 실행되지 않습니다. 앱이 공증되었는지 확인하는 방법에 대한 자세한 내용은 [macOS 앱을 공증하여 macOS Catalina 준비](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Support-Tip-Notarizing-your-macOS-apps-to-prepare-for-macOS/ba-p/808579)를 참조하세요.

> [!NOTE]
> macOS 디바이스 사용자는 주식, 지도 같은 기본 제공 macOS 앱 중 일부를 제거할 수 있으나 Intune을 사용하여 해당 앱을 다시 배포할 수는 없습니다. 최종 사용자가 이러한 앱을 삭제하는 경우 앱 스토어로 이동하여 수동으로 다시 설치해야 합니다.

## <a name="before-your-start"></a>시작하기 전에

사업 부문 파일을 Microsoft Intune에 업로드하기 전에 외부 도구를 다운로드하여 다운로드한 도구를 실행 파일로 표시한 다음 *.pkg* 파일을 전처리해야 합니다. *.pkg* 파일의 전처리는 macOS 디바이스에서 수행해야 합니다. Mac용 Intune 앱 래핑 도구를 사용하여 Microsoft Intune에서 Mac 앱을 관리할 수 있도록 합니다.

> [!IMPORTANT]
> Apple Developer 계정에서 가져온 “Developer ID 설치 프로그램” 인증서를 사용하여 *.pkg* 파일에 서명해야 합니다. macOS LOB 앱을 Microsoft Intune에 업로드하는 데는 *.pkg* 파일만 사용할 수 있습니다. *.dmg*와 다른 형식의 *.pkg*로의 변환은 지원되지 않습니다.
>

1. [Mac용 Intune 앱 래핑 도구](https://github.com/msintuneappsdk/intune-app-wrapping-tool-mac)를 다운로드합니다.

    > [!NOTE]
    > **Mac용 Intune 앱 래핑 도구**는 macOS 머신에서 실행되어야 합니다. 

2. 다음과 같이 다운로드한 도구를 실행 파일로 표시합니다.
   - 터미널 앱을 시작합니다.
   - `IntuneAppUtil`이 있는 위치로 디렉터리를 변경합니다.
   - 다음 명령을 실행하여 도구 실행 파일을 만듭니다.<br> 
       `chmod +x IntuneAppUtil`

3. **Mac용 Intune 앱 래핑 도구** 내에서 `IntuneAppUtil` 명령을 사용하여 *.intunemac* 파일에서 *.pkg* LOB 앱 파일을 래핑합니다.<br>

    macOS용 Microsoft Intune 앱 래핑 도구에 사용할 샘플 명령:
    > [!IMPORTANT]
    > `IntuneAppUtil` 명령을 실행하기 전에 `<source_file>` 인수에 공백이 포함 되지 않았는지 확인합니다.

    - `IntuneAppUtil -h`<br>
    이 명령은 도구에 대한 사용 정보를 보여줍니다.
    
    - `IntuneAppUtil -c <source_file> -o <output_file> [-v]`<br>
    이 명령은 *.pkg* LOB 앱 파일을 *.intunemac* 파일로 래핑합니다.
    
    - `IntuneAppUtil -r <filename.intunemac> [-v]`<br>
    이 명령은 생성된 *.intunemac* 파일에 대해 발견된 매개 변수 및 버전을 추출합니다.

## <a name="select-the-app-type"></a>앱 유형을 선택합니다.

1. [Microsoft Endpoint Manager 관리 센터](https://go.microsoft.com/fwlink/?linkid=2109431)에 로그인합니다.
2. **앱** > **모든 앱** > **추가**를 선택합니다.
3. **앱 유형 선택** 창의 **기타** 앱 유형에서 **LOB(기간 업무) 앱**을 선택합니다.
4. **선택**을 클릭합니다. **앱 추가** 단계가 표시됩니다.

## <a name="step-1---app-information"></a>1단계 - 앱 정보

### <a name="select-the-app-package-file"></a>앱 패키지 파일 선택

1. **앱 추가** 창에서 **앱 패키지 파일 선택**을 클릭합니다. 
2. **앱 패키지 파일** 창에서 찾아보기 단추를 선택합니다. 그런 다음 확장명이 *.intunemac*인 macOS 설치 파일을 선택합니다.
   앱 세부 정보가 표시됩니다.
3. 완료되면 **앱 패키지 파일** 창에서 **확인**을 선택하여 앱을 추가합니다.

### <a name="set-app-information"></a>앱 정보 설정

1. **앱 정보** 페이지에서 앱의 세부 정보를 추가합니다. 선택한 앱에 따라 이 창의 일부 값이 자동으로 채워질 수 있습니다.
    - **이름**: 회사 포털에 표시되는 앱 이름을 입력합니다. 사용하는 모든 앱 이름이 고유한지 확인합니다. 동일한 앱 이름을 두 번 사용하는 경우 앱 중 하나만 회사 포털에 표시됩니다.
    - **설명**: 앱에 대한 설명을 입력합니다. 설명은 회사 포털에 표시됩니다.
    - **게시자**: 앱 게시자의 이름을 입력합니다.
    - **최소 운영 체제**: 목록에서 앱을 설치할 수 있는 최소 운영 체제 버전을 선택합니다. 이전 버전의 운영 체제를 사용하는 디바이스에 앱을 할당할 경우 앱이 설치되지 않습니다.
    - **범주**: 기본 제공 앱 범주를 하나 이상 선택하거나 직접 만든 범주를 선택합니다. 범주를 사용하면 사용자가 회사 포털을 탐색할 때 앱을 더 쉽게 찾을 수 있습니다.
    - **회사 포털에서 이 항목을 추천 앱으로 표시**: 사용자가 앱을 찾아볼 때 회사 포털의 기본 페이지에 앱을 쉽게 확인할 수 있도록 표시합니다.
    - **정보 URL**: 필요에 따라 이 앱에 대한 정보를 포함하는 웹 사이트의 URL을 입력합니다. URL은 회사 포털에 표시됩니다.
    - **개인정보취급방침 URL**: 필요에 따라 이 앱에 대한 개인정보 관련 정보를 포함하는 웹 사이트의 URL을 입력합니다. URL은 회사 포털에 표시됩니다.
    - **개발자**: 선택적으로, 앱 개발자의 이름을 입력합니다.
    - **소유자**: 선택적으로, 이 앱의 소유자 이름을 입력합니다. 예를 들어 **HR 부서** 등을 입력합니다.
    - **메모**: 이 앱과 연결할 모든 메모를 입력합니다.
    - **로고**: 앱과 연결된 아이콘을 업로드합니다. 사용자가 회사 포털을 탐색할 때 이 아이콘이 앱과 함께 표시됩니다.
2. **다음**을 클릭하여 **범위 태그** 페이지를 표시합니다.

## <a name="step-2---select-scope-tags-optional"></a>2단계 - 범위 태그 선택(선택 사항)

범위 태그를 사용하여 Intune에서 클라이언트 앱 정보를 볼 수 있는 사용자를 결정할 수 있습니다. 범위 태그에 대한 자세한 내용은 [분산형 IT에 역할 기반 액세스 제어 및 범위 태그 사용](../fundamentals/scope-tags.md)을 참조하세요.

1. **범위 태그 선택**을 클릭하여 앱의 범위 태그를 선택적으로 추가합니다. 
2. **다음**을 클릭하여 **할당** 페이지를 표시합니다.

## <a name="step-3---assignments"></a>3단계 - 할당

1. 앱에 대해 **필수**, **등록된 디바이스에 사용 가능** 또는 **제거** 그룹 할당을 선택합니다. 자세한 내용은 [그룹을 추가하여 사용자 및 디바이스 구성](../fundamentals/groups-add.md) 및 [Microsoft Intune을 사용하여 그룹에 앱 할당](apps-deploy.md)을 참조하세요.
2. **다음**를 클릭하여 **검토 + 만들기** 페이지를 표시합니다. 

## <a name="step-4---review--create"></a>4단계 - 검토 + 만들기

1. 앱에 대해 입력한 값과 설정을 검토합니다.
2. 완료되면 **만들기**를 클릭하여 Intune에 앱을 추가합니다.

    LOB(기간 업무) 앱의 **개요** 블레이드가 표시됩니다.

만든 앱이 앱 목록에 표시됩니다. 이 목록에서 선택한 그룹에 앱을 할당할 수 있습니다. 도움말은 [그룹에 앱을 할당하는 방법](apps-deploy.md)을 참조하세요.

> [!NOTE]
> *.pkg* 파일에 여러 앱 또는 앱 설치 관리자가 포함되어 있는 경우 Microsoft Intune은 설치된 모든 앱이 디바이스에서 발견될 경우에만 ‘앱’이 성공적으로 설치되어 있다고 보고합니다. 

## <a name="update-a-line-of-business-app"></a>기간 업무 앱 업데이트

[!INCLUDE [shared-proc-lob-updateapp](../includes/shared-proc-lob-updateapp.md)]

> [!NOTE]
> Intune 서비스에서 새 *.pkg* 파일을 디바이스에 성공적으로 배포하려면 *.pkg* 패키지의 *packageinfo* 파일에 있는 `version` 및 `CFBundleVersion` 문자열을 증분해야 합니다.

## <a name="next-steps"></a>다음 단계

- 만든 앱은 앱 목록에 표시됩니다. 이제 선택한 그룹에 앱을 할당할 수 있습니다. 도움말은 [그룹에 앱을 할당하는 방법](apps-deploy.md)을 참조하세요.

- 앱의 속성 및 할당을 모니터링할 수 있는 방법에 대해 자세히 알아봅니다. 자세한 내용은 [앱 정보 및 할당을 모니터링하는 방법](apps-monitor.md)을 참조하세요.

- Intune에서 앱의 컨텍스트에 대해 자세히 알아봅니다. 자세한 내용은 [디바이스 및 앱 수명 주기 개요](../fundamentals/device-lifecycle.md)를 참조하세요.
