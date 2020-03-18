---
title: macOS 디바이스 지우기
titleSuffix: Microsoft Intune
description: macOS 디바이스에서 운영 체제를 비롯한 모든 데이터를 지우는 방법을 알아봅니다.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/27/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: remote-actions
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ab396092-907a-44b7-a157-aabee62176a9
ms.reviewer: coferro
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 650ba81c9e92ce03b67e90cf188435b7dc0800fb
ms.sourcegitcommit: 3d895be2844bda2177c2c85dc2f09612a1be5490
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79338216"
---
# <a name="erase-all-data-from-a-macos-device"></a>macOS 디바이스에서 모든 데이터 지우기

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

운영 체제를 포함하여 macOS 디바이스에서 모든 데이터를 지울 수 있습니다. Intune 관리에서 디바이스도 제거됩니다. 최종 사용자에게 아무런 경고도 표시되지 않습니다.

1. [Microsoft Endpoint Manager 관리 센터](https://go.microsoft.com/fwlink/?linkid=2109431)에서 **디바이스** > **모든 디바이스**를 차례로 선택하고 지우려는 디바이스를 선택합니다.
2. **자세히** > **지우기**를 클릭하고 >**복구 PIN**에 6자리 숫자를 제공합니다. 이것은 사용자가 운영 체제를 디바이스에 재설치할 수 있도록 사용자에게 제공해야 하는 PIN입니다. 지우기 작업이 완료된 후에는 이 PIN이 보이지 않기 때문에 기록해두어야 합니다.
![스크린샷](./media/device-erase/providepin.png)
3. **확인**을 클릭하여 디바이스를 지웁니다.
