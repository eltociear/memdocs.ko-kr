---
title: Exchange Connector 문제 해결
titleSuffix: Microsoft Intune
description: Intune 온-프레미스 Exchange Connector와 관련된 문제를 해결합니다.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/02/2019
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: a7e3c742-295b-40bb-9afa-17f243062500
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: af44b09f5e539306a24ae0e0294b3ad674f7cb74
ms.sourcegitcommit: 3d895be2844bda2177c2c85dc2f09612a1be5490
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79338554"
---
# <a name="troubleshoot-the-intune-exchange-connector"></a>Intune Exchange Connector 문제 해결

이 문서에서는 Intune Exchange Connector와 관련된 문제를 해결하는 방법을 설명합니다.

## <a name="before-you-start"></a>시작하기 전에

Intune에서 Exchange Connector 문제 해결을 시작하기 전에 탄탄한 기반 작업을 수행할 수 있도록 몇 가지 기본적인 정보를 수집합니다. 이러한 접근 방식은 문제의 본질을 더 잘 파악하고 더 빠르게 해결하는 데 도움이 됩니다.

- 프로세스가 설치 요구 사항을 충족하는지 확인합니다. [온-프레미스 Intune Exchange 커넥터 설정](exchange-connector-install.md)을 참조하세요.
- 계정에 Exchange와 Intune 관리자 권한이 모두 있는지 확인합니다.
- 완전하고 정확한 오류 메시지 텍스트, 세부 정보, 메시지가 표시되는 위치를 확인합니다.
- 문제가 시작된 시기를 확인합니다. 
  - 커넥터를 처음 설정하고 있습니까? 
  - 커넥터가 제대로 작동하지 않고 실패했습니까?
  - 작동하는 경우 Intune 환경, Exchange 환경 또는 커넥터 소프트웨어를 실행하는 컴퓨터에 어떤 변화가 있었습니까?
- MDM 기관이란 무엇입니까?
- 어떤 Exchange 버전을 사용하고 있습니까?

### <a name="use-powershell-to-get-more-data-on-exchange-connector-issues"></a>Powershell을 사용하여 Exchange 커넥터에 더 많은 데이터를 가져오는 문제

- 사서함에 대한 모든 모바일 디바이스 목록을 가져오려면 `Get-ActiveSyncDeviceStatistics -mailbox mbx`를 사용합니다.
- 사서함에 대한 SMTP 주소 목록을 가져오려면 `Get-Mailbox -Identity user | select emailaddresses | fl`을 사용합니다.
- 디바이스의 액세스 상태에 대한 상세 정보를 가져오려면 다음을 사용합니다. `Get-CASMailbox <upn> | fl`

## <a name="review-the-connector-configuration"></a>커넥터 구성 검토

환경과 커넥터가 올바르게 구성되어 있는지 확인하려면 [온-프레미스 Exchange 커넥터 요구 사항](exchange-connector-install.md#intune-exchange-connector-requirements)을 검토합니다. 

### <a name="general-considerations-for-the-connector"></a>커넥터에 대한 일반적인 고려 사항

- 방화벽 및 프록시 서버에서 Exchange Connector를 호스팅하는 서버와 Intune 서비스 사이의 커뮤니케이션을 허용하는지 확인합니다.

- Intune Exchange Connector를 호스팅하는 컴퓨터와 Exchange 클라이언트 액세스 서버(CAS)는 도메인으로 조인되고 동일한 LAN상에 있어야 합니다. Intune Exchange 커넥터에서 사용되는 계정에 대해 필요한 권한이 추가되어 있는지 확인합니다.

- 알림 계정은 *Autodiscover* 설정을 검색하는 데 사용됩니다. Exchange의 Autodisover에 대한 자세한 정보는 [Exchange Server의 Autodiscover 서비스](https://docs.microsoft.com/exchange/architecture/client-access/autodiscover?view=exchserver-2016)를 참조하세요.

- Intune Exchange Connector는 알림 계정 자격 증명으로 *시작* 링크(Intune 등록용)와 함께 알림 이메일 메시지를 전송하여 EWS URL에 요청을 보냅니다. 등록용 *시작* 링크의 사용은 Android 비Knox 디바이스의 요구 사항입니다. 그렇지 않으면 이 디바이스는 조건부 액세스에 의해 차단됩니다.

### <a name="common-issues-for-connector-configurations"></a>커넥터 구성의 일반적인 문제

- **계정 권한**: Microsoft Intune Exchange Connector 대화 상자에서 [필수 Windows PowerShell Exchange cmdlet](exchange-connector-install.md#exchange-cmdlet-requirements)을 실행할 수 있는 적절한 사용 권한이 있는 사용자 계정을 지정했는지 확인합니다.
- **알림 이메일 메시지**: 알림을 사용하도록 설정하고 알림 계정을 지정합니다.
- **클라이언트 액세스 서버 동기화**: Exchange Connector를 구성할 경우 Exchange 커넥터를 호스팅하는 서버에서 네트워크 대기 시간이 가장 짧은 CAS를 지정합니다. CAS와 Exchange 커넥터 간의 통신 대기 시간은 특히 Exchange Online Dedicated를 사용할 때 디바이스 검색을 지연시킬 수 있습니다.
- **동기화 일정**: 디바이스를 새로 등록한 사용자는 Exchange Connector가 Exchange CAS와 동기화될 때까지 액세스가 지연될 수 있습니다. 전체 동기화는 하루에 한 번 수행되며 델타(빠른) 동기화는 하루에 여러 번 수행됩니다. [수동으로 빠른 동기화 또는 전체 동기화를 강제 수행](exchange-connector-install.md#manually-force-a-quick-sync-or-full-sync)하여 지연을 최소화할 수 있습니다.

## <a name="next-steps"></a>다음 단계
다음 문서는 일반적인 문제와 특정 오류를 해결하는 데 도움이 될 수 있습니다.

- [Intune Exchange Connector의 일반적인 문제 해결](troubleshoot-exchange-connector-common-problems.md).
- [Intune Exchange Connector의 일반적인 오류 해결](troubleshoot-exchange-connector-common-errors.md).

지원 또는 Intune 커뮤니티에서 지원을 요청합니다.

- [지원 받기](../fundamentals/get-support.md)를 참조하여 Intune 콘솔로 문제를 해결하거나 Microsoft를 통한 지원 사례를 엽니다. 
- [Microsoft Intune 포럼](https://social.technet.microsoft.com/Forums/en-US/home?forum=microsoftintuneprod)에 문제를 게시합니다.  
