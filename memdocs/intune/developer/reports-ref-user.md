---
title: 사용자 - Intune 데이터 웨어하우스
titleSuffix: Microsoft Intune
description: Intune 데이터 웨어하우스 API에서 엔터티 컬렉션의 사용자 범주에 대한 항목을 참조하세요.
keywords: Intune 데이터 웨어하우스
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/03/2020
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: developer
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: C29A6EEA-72B7-427E-9601-E05B408F3BB0
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: b2bb18415cbebcef98ba6a7015872467c13eb231
ms.sourcegitcommit: 3d895be2844bda2177c2c85dc2f09612a1be5490
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79339880"
---
# <a name="reference-for-user-entity"></a>사용자 엔터티 참조

**사용자** 범주에는 데이터 모델의 사용자 속성을 정의하는 **사용자** 엔터티가 포함됩니다.

## <a name="users"></a>사용자

**사용자** 엔터티는 회사 내 할당된 라이선스가 있는 모든 Azure Active Directory(Azure AD) 사용자를 나열합니다.

**사용자** 엔터티 컬렉션에는 사용자 데이터가 포함됩니다. 이러한 레코드에는 사용자가 제거된 경우에도 데이터 컬렉션 기간의 사용자 상태가 포함됩니다. 예를 들어, 사용자가 Intune에 추가된 다음 지난달 중에 제거되었을 수 있습니다. 보고 시점에는 이 사용자가 없지만 이전 달의 데이터에는 사용자와 상태가 있습니다. 데이터에 있는 사용자의 현재 상태 기록에 대한 기간을 보여 주는 보고서를 만들 수 있습니다.

|          속성          |                                                                                                           설명                                                                                                          |                예제               |
|:--------------------------:|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|:------------------------------------:|
| userKey                    | 데이터 웨어하우스의 사용자의 고유 식별자 - 서로게이트 키                                                                                                                                                         | 123                                  |
| userId                     | 사용자의 고유 식별자는 UserKey와 비슷하지만 자연 키입니다.                                                                                                                                                    | b66bc706-ffff-7437-0340-032819502773 |
| userEmail                  | 사용자의 이메일 주소                                                                                                                                                                                                     | John@constoso.com                    |
| userPrincipalName                        | 사용자의 사용자 계정 이름입니다.                                                                                                                                                                                               | John@constoso.com                    |
| displayName                | 사용자의 표시 이름                                                                                                                                                                                                      | John                                 |
| intuneLicensed             | 이 사용자의 Intune 라이선스 여부를 나타냅니다.                                                                                                                                                                              | True/False                           |
| isDeleted                  | 사용자의 모든 라이선스가 만료되었는지 여부와 이에 따라 사용자가 Intune에서 제거되었는지 여부를 나타냅니다. 단일 레코드의 경우 이 플래그는 변경되지 않습니다. 대신 새 사용자 상태의 새 레코드가 만들어집니다. | True/False                           |
| RowLastModifiedDateTimeUTC | 데이터 웨어하우스에서 레코드를 마지막으로 수정한 UTC 날짜 및 시간                                                                                                                                                 | 2016/11/23 0:00                      |


## <a name="next-steps"></a>다음 단계
- **현재 사용자** 엔터티 컬렉션을 사용하여 사용자 데이터를 현재 활성 상태인 사용자로 제한할 수 있습니다. 자세한 내용은 [현재 사용자 엔터티에 대한 참조](reports-ref-data-model.md)를 참조하세요.
- 데이터 웨어하우스가 Intune에서 사용자의 수명을 추적하는 방법에 대한 자세한 내용은 [Intune 데이터 웨어하우스의 사용자 수명 표시](reports-ref-user-timeline.md)를 참조하세요.
