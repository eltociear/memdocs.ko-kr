---
title: IntuneManagementExtension 엔터티
titleSuffix: Microsoft Intune
description: Intune 데이터 웨어하우스 API에서 엔터티 컬렉션의 IntuneManagementExtension 엔터티 범주에 대한 참조 항목입니다.
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
ms.assetid: 73DF3B90-6D52-4EF6-AFFD-1873A18C7421
ms.reviewer: dariusz
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: f8152eb12779376e1885d0a2b2898cd602aa825d
ms.sourcegitcommit: 3d895be2844bda2177c2c85dc2f09612a1be5490
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79359770"
---
# <a name="reference-for-intune-management-extensions"></a>Intune 관리 확장에 대한 참조

**intuneManagementExtensions** 범주는 다음과 같은 정보를 추적하는 모바일 디바이스에 대한 엔터티를 포함합니다.

- IntuneManagementExtension의 버전
- IntuneManagementExtension의 설치 상태

## <a name="intunemanagementextensionversions"></a>intuneManagementExtensionVersions

**intuneManagementExtensionVersion** 엔터티는 intuneManagementExtensions에서 사용하는 모든 버전을 나열합니다.

| 속성  | 설명 | 예제 |
|---------|------------|--------|
| extensionVersionKey |intuneManagementExtensions 버전의 고유 식별자입니다. | 1 |
| extensionVersion |4 자리 버전 번호입니다. |1.0.2.0 |

## <a name="intunemanagementextensionhealthstates"></a>intuneManagementExtensionHealthStates

**intuneManagementExtensionHealthState**는 intuneManagementExtensions의 가능한 상태를 모두 나열합니다.

| 속성  | 설명 | 예제 |
|---------|------------|--------|
| extensionStateKey |상태의 고유 식별자입니다. | 2 |
| extensionState |IntuneManagementExtension의 상태입니다. | 정상 |

## <a name="intunemanagementextensions"></a>intuneManagementExtensions

**intuneManagementExtension**은 각 Windows 10 디바이스의 IntuneManagementExtensions 상태를 일별로 나열합니다.
데이터는 최근 60일 동안 보존됩니다. 


|      속성       |                         설명                         | 예제 |
|---------------------|-------------------------------------------------------------|---------|
|       dateKey       |               날짜의 고유 식별자입니다.                |   123   |
|      tenantKey      |              테넌트의 고유 식별자입니다.               |   456   |
|      deviceKey      |              디바이스의 고유 식별자입니다.               |   789   |
| extensionVersionKey | intuneManagementExtension 버전의 고유 식별자입니다. |    1    |
|  extensionStateKey  |             상태의 고유 식별자입니다.              |    2    |

