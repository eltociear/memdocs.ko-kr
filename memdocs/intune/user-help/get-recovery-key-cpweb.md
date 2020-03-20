---
title: Intune 회사 포털 웹 사이트에서 macOS 디바이스 복구 키 가져오기
description: 등록된 관리되는 macOS 디바이스에 대한 복구 키를 확인합니다.
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 12/04/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.subservice: end-user
ms.technology: ''
ms.assetid: ''
searchScope:
- User help
ROBOTS: ''
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-enduser
ms.collection: ''
ms.openlocfilehash: 5a15f3a05f96333eba19cf69c5778e6c8bd04f59
ms.sourcegitcommit: 3d895be2844bda2177c2c85dc2f09612a1be5490
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79336760"
---
# <a name="get-a-recovery-key-for-a-macos-device"></a>macOS 디바이스 복구 키 가져오기

회사 포털 웹 사이트를 사용하여 잠긴 macOS 디바이스에 대한 복구 키를 가져올 수 있습니다. 디바이스 암호를 잊은 경우 다른 디바이스에서 회사 포털에 로그인하여 키를 검색할 수 있습니다.  

## <a name="get-recovery-key-from-company-portal-website"></a>회사 포털 웹 사이트에서 복구 키 가져오기

이 옵션은 FileVault를 사용하는 조직에서 암호화한 디바이스에 사용할 수 있습니다. 개인적으로 암호화한 디바이스에는 사용할 수 없습니다.

1. 임의의 디바이스에서 [회사 포털 웹 사이트](https://portal.manage.microsoft.com)에 로그인하고 **메뉴** 단추 > **디바이스**를 선택합니다.  
2. 암호화된 macOS 디바이스를 선택합니다.  
3. **복구 키 가져오기**를 선택합니다.  

    ![회사 포털 웹 사이트의 복구 키 가져오기 섹션이 강조 표시된 스크린샷.](./media/1907-recovery2-cpweb-intune.PNG)  

4. 복구 키가 표시됩니다.

    ![복구 키를 보여 주는 회사 포털 웹 사이트의 스크린샷.](./media/1907-recovery-cpweb-intune.PNG)  

    보안상의 이유로 5분 후에 키가 사라집니다. 키를 다시 표시하려면 **복구 키 가져오기**를 선택합니다.

디바이스가 올바르게 암호화되었지만 키를 찾을 수 없는 경우 조직의 지원 담당자에게 문의하세요. 연락처 정보는 [회사 포털 웹 사이트](https://go.microsoft.com/fwlink/?linkid=2010980)를 참조하세요.  

## <a name="get-recovery-key-from-company-portal-app-for-ios"></a>iOS용 회사 포털 앱에서 복구 키 가져오기

iOS용 회사 포털 앱을 사용하여 개인 복구 키(FileVault 키)를 검색할 수 있습니다. 개인 복구 키를 포함하는 디바이스는 Intune에 등록되고 Intune을 통해 FileVault로 암호화되어야 합니다. 개인적으로 암호화한 디바이스에는 이 옵션을 사용할 수 없습니다. 

회사 포털 앱을 사용하여 Safari 웹 보기를 열고 개인 복구 키를 검색할 수 있습니다. 

1. 회사 포털을 엽니다.
2. **복구 키 가져오기**를 클릭합니다.

    ![복구 키가 표시된 iOS용 회사 포털 앱의 스크린샷](./media/get-recovery-key-cpweb-02.png)  

Safari 웹 보기에서 회사 포털 웹 사이트가 열리고 키가 표시됩니다. 

## <a name="it-pro-support"></a>IT 전문가 지원

IT 지원 담당자이고 macOS 디바이스에 대해 FileVault 암호화를 구성하고 관리하려면 [Intune에서 디바이스 암호화 사용](/intune/protect/encrypt-devices)을 참조하세요.

## <a name="next-steps"></a>다음 단계

회사 포털 웹 사이트에서 수행할 수 있는 다른 작업에 대해 알아봅니다. 작업 목록은 [Intune 회사 포털 웹 사이트 사용](using-the-intune-company-portal-website.md)을 참조하세요.  

여전히 도움이 필요하세요? IT 지원 담당자에게 문의하세요. 연락처 정보는 [회사 포털 웹 사이트](https://go.microsoft.com/fwlink/?linkid=2010980)를 참조하세요.  
