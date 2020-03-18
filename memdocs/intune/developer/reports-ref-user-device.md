---
title: 사용자 디바이스 연결 - Intune 데이터 웨어하우스
titleSuffix: Microsoft Intune
description: UserDeviceAssociation 엔터티에는 조직의 사용자 디바이스 연결이 포함되어 있습니다.
keywords: Intune 데이터 웨어하우스
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 12/04/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: developer
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 777484A7-09CE-4409-987F-76B3F87DFE93
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 6127b365a04ad48a9cbaa98bdef821c4d1334181
ms.sourcegitcommit: 3d895be2844bda2177c2c85dc2f09612a1be5490
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79339893"
---
# <a name="reference-for-user-device-association-entity"></a>사용자 디바이스 연결 엔터티에 대한 참조

**userDeviceAssociation** 엔터티에는 조직의 사용자 디바이스 연결이 포함되어 있습니다.

## <a name="userdeviceassociations"></a>userDeviceAssociations


|        Name        |                                           설명                                            |        예제         |
|--------------------|--------------------------------------------------------------------------------------------------|------------------------|
|      userKey       |              데이터 웨어하우스에서 사용자의 고유 식별자입니다. (서로게이트 키입니다.)               |          123           |
|     deviceKey      |                      데이터 웨어하우스의 디바이스에 대한 고유 식별자                      |          123           |
| createdDateTimeUTC |           사용자 디바이스 연결을 만든 날짜 및 시간. UTC 형식을 사용합니다.           | 11/23/2016 12:00:00 AM |
|     isDeleted      | 사용자가 해당 디바이스를 등록 취소했으며 연결이 현재 더 이상 존재하지 않음을 나타냅니다. |       True/False       |
|  endedDateTimeUTC  |              IsDeleted를 <strong>True</strong>로 변경한 UTC 날짜 및 시간               | 06/23/2017 12:00:00 AM |

## <a name="next-steps"></a>다음 단계

- [Intune 데이터 웨어하우스](reports-nav-create-intune-reports.md)에 대해 자세히 알아봅니다.
