---
title: Intune에서 최신 인증을 사용하지 않는 앱 차단
titleSuffix: Microsoft Intune
description: Microsoft Intune을 사용하는 애플리케이션 및 최신 인증(ADAL)에 대해 알아봅니다.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/06/2020
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.topic: conceptual
ms.technology: ''
ms.assetid: 73db3070-d033-40fb-a8f1-58b9d198021e
ms.reviewer: chrisgre
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: f529a80403d27cf9d12c03c6090670095bf569fa
ms.sourcegitcommit: 3d895be2844bda2177c2c85dc2f09612a1be5490
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79354180"
---
# <a name="block-apps-that-dont-use-modern-authentication-adal"></a>최신 인증(ADAL)을 사용하지 않는 앱 차단

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

앱 보호 정책을 사용한 앱 기반 조건부 액세스의 경우 애플리케이션에서 OAuth2 구현인 [최신 인증](https://support.office.com/article/Using-Office-365-modern-authentication-with-Office-clients-776c0036-66fd-41cb-8928-5495c0f9168a)을 사용해야 합니다. 최신 Office 모바일 및 데스크톱 애플리케이션은 최신 인증을 사용합니다. 그러나 기본 인증 및 양식 기반 인증과 같은 다른 인증 방법을 사용하는 타사 앱과 이전 Office 앱이 있습니다.

## <a name="block-access-to-apps"></a>앱 액세스 차단

최신 인증을 사용하지 않는 앱에 대한 액세스를 차단하려면 Intune 앱 보호 정책을 사용하여 조건 액세스를 구현합니다. 자세한 내용은 [Intune을 사용한 앱 기반 조건부 액세스](app-based-conditional-access-intune.md)를 참조하세요.

## <a name="additional-information"></a>추가 정보

Azure AD 조건부 액세스에 대한 자세한 내용은 다음 항목을 참조하세요.
- [Azure Active Directory에서 조건부 액세스란 무엇을 말하나요?](https://docs.microsoft.com/azure/active-directory/conditional-access/overview)
- [앱 기반 조건부 액세스의 작동 방식](app-based-conditional-access-intune.md#how-app-based-conditional-access-works)
- [Azure Active Directory 조건부 액세스를 위해 SharePoint Online 및 Exchange Online 설정](https://docs.microsoft.com/azure/active-directory/conditional-access/conditional-access-for-exo-and-spo)

## <a name="next-steps"></a>다음 단계

- [Intune을 사용하는 앱 기반 조건부 액세스](app-based-conditional-access-intune.md)
