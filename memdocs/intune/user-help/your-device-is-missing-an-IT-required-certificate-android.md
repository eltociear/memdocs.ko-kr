---
title: 디바이스에 인증서가 없는 경우 | Microsoft Docs
description: ''
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 07/29/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.subservice: end-user
ms.technology: ''
ms.assetid: f0ba4cbb-ef0a-4335-86bf-f1d006867fa2
searchScope:
- User help
ROBOTS: ''
ms.reviewer: arnab
ms.suite: ems
ms.custom: intune-enduser
ms.collection: ''
ms.openlocfilehash: b4a16204afc99169183e02eb269ab24d7f63cc49
ms.sourcegitcommit: 3d895be2844bda2177c2c85dc2f09612a1be5490
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79346055"
---
# <a name="install-missing-certificate-required-by-your-organization"></a>조직에 필요한 누락된 인증서 설치  

디바이스가 Intune에 등록되어 있지 않고 필요한 인증서가 없는 경우 회사 포털 앱에 로그인할 수 없습니다. 로그인하려고 시도하면 다음과 같은 메시지가 표시됩니다.

![screenshot-error-message-about-missing-certificate](./media/andr-cert_install-1-cert_missing.png)

필요한 인증서를 다운로드하고 디바이스를 등록하기 위해 두 가지 방법을 시도할 수 있습니다. 

- 회사 포털 앱에서 브라우저 액세스를 사용하도록 설정합니다.
- 회사 또는 학교 PC에서 누락된 인증서를 식별합니다. 그런 다음 인터넷을 검색하여 누락된 인증서를 다운로드합니다. 

먼저 브라우저 액세스를 사용하도록 설정하는 단계를 완료합니다. 그런 후에도 디바이스를 등록할 수 없는 경우 단계에 따라 인터넷에서 인증서를 찾습니다. 

## <a name="enable-browser-access"></a>브라우저 액세스 사용
브라우저 액세스를 사용하도록 설정하려면 다음 단계를 완료합니다. 액세스를 사용하도록 설정하고 나면 회사 포털이 적절한 인증서를 설치하고 등록을 계속합니다.    

1. 회사 포털 앱에서 오른쪽 모서리로 이동하여 메뉴를 선택합니다.  
2. **설정**을 선택합니다.  
3. **브라우저 액세스 사용** 옆에서 **사용**을 선택합니다.  
4. 디바이스 관리자 화면에서 **활성화**를 탭합니다. 

## <a name="identify-and-download-the-missing-certificate-through-web-search"></a>웹 검색을 통해 누락된 인증서 식별 및 다운로드
디바이스에서 인증서를 수동으로 식별하고 설치하려면 다음 단계를 완료하세요.  

1. PC에서 Internet Explorer를 엽니다. 이 용도로 사용할 PC가 없으면 회사 지원팀에 문의하세요. 회사 지원팀의 연락처 정보는 [회사 포털 웹 사이트](https://go.microsoft.com/fwlink/?linkid=2010980)를 확인하세요.

2. [회사 포털 웹 사이트](https://go.microsoft.com/fwlink/?linkid=2010980)로 이동한 후 회사 또는 학교 자격 증명으로 로그인합니다.

3. 브라우저의 주소 표시줄 맨 오른쪽에서 다음 스크린샷과 같이 자물쇠 모양의 기호를 선택합니다.

    ![screenshot-internet-explorer-address-bar-padlock-symbol](./media/andr-missing-cert-ie-padlock-symbol.png)

    자물쇠 기호가 보이지 않으면 중지하고 회사 지원팀에 문의하세요. 잠금은 안전하게 로그인되어 있음을 의미하므로 해당 기호가 표시되지 않으면 계속 진행하지 않아야 합니다.

4. **인증서 보기**를 선택합니다.

    ![screenshot-internet-explorer-view-certificates-button-on-website-identification-dialog](./media/andr-missg-cert-ie-view-cert-button.png)

5. **인증 경로** 탭을 선택한 다음 인터넷에서 가져와야 하는 인증서를 식별합니다. 필요한 인증서의 이름은 앞의 예제 스크린샷에 강조 표시된 것과 같은 위치에 있습니다.

6. Bing이나 Google 같은 검색 엔진을 사용하여 이전 섹션에서 식별한 누락된 인증서의 이름을 검색합니다. 인증서는 ".crt" 또는 ".pem" 등의 다른 "확장명"으로 끝날 수 있습니다.

7. 웹 사이트에서 루트 인증서를 다운로드합니다.

8. 인증서 다운로드 후 디바이스 맨 위에서 아래로 끌어 알림을 열고, 알림 목록에서 인증서 이름을 누릅니다.

4. 다음 스크린샷에 표시된 **인증서 이름 지정** 대화 상자에서 기본 인증서 이름을 그대로 적용합니다.

5. **자격 증명 용도**가 **VPN 및 앱용**으로 설정되어 있는지 확인한 후 **확인**을 탭합니다.

    ![screenshot-certificate-name-dialog-showing-certificate-name](./media/andr-missing-cert-cert-name.png)

6. 회사 포털 앱을 닫습니다.

7. 회사 포털 앱을 다시 엽니다. 이제 회사 포털 앱에 로그인할 수 있습니다. 도움이 필요하면 회사 지원팀에 문의하세요.

앞서 표시된 것과 동일한 "인증서 없음" 메시지가 표시되고 해당 절차를 이미 진행했다면 회사 지원팀에서 설치하기 위해 필요한 다른 인증서가 있을 수 있습니다. 도움이 필요하면 [회사 포털 웹 사이트](https://go.microsoft.com/fwlink/?linkid=2010980)에 제공되는 연락처 정보를 사용하여 회사 지원팀에 문의하세요.

## <a name="next-steps"></a>다음 단계  

여전히 도움이 필요하세요? 회사 지원 부서에 문의하세요. 연락처 정보는 [회사 포털 웹 사이트](https://go.microsoft.com/fwlink/?linkid=2010980)를 참조하세요.  
