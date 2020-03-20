---
title: 출시대상 그룹 및 시간 결정
titleSuffix: Microsoft Intune
description: 이 문서에서는 Microsoft Intune을 출시할 그룹과 해당 배포의 시간을 결정하는 데 도움이 되는 정보를 제공합니다.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 01/02/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 3a63f78f-a7e7-4f44-9288-16b28d5d58ca
ms.reviewer: jeffbu, cgerth
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 7aa18316ad1b4473ac70399e1370bfececadbfaf
ms.sourcegitcommit: 3d895be2844bda2177c2c85dc2f09612a1be5490
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79357443"
---
# <a name="develop-a-rollout-plan"></a>출시 계획 개발

출시 계획을 개발하면 Intune 출시 대상으로 지정할 조직 그룹, 각 그룹에 대한 출시 시간 및 사용할 등록 방식을 파악할 수 있습니다.

## <a name="targeted-groups-and-timeframes"></a>대상 그룹 및 시간

먼저 [사용 사례 시나리오](planning-guide-scenarios.md)에서 파악했으며 Intune 출시 대상으로 지정한 그룹을 검토합니다.

둘째로, 각 대상 그룹에 대한 출시 시간을 결정합니다. 이 작업을 수행할 때는 보통 Intune 배포 팀과 대상 그룹이 논의를 거쳐 각 그룹에 가장 적합한 출시 시간을 결정해야 합니다. 이러한 논의에서 다루어야 할 요점은 다음과 같습니다.
* 그룹의 변경 의지
* 사용자 및 디바이스 수
* 디바이스 플랫폼의 유형
* 요구 사항
* 지리적 위치
* 업무상의 위험

## <a name="rollout-phases"></a>출시 단계
조직에서는 일반적으로 IT 부서의 소규모 사용자 그룹을 대상으로 하는 초기 파일럿 그룹부터 Intune 출시를 시작하도록 선택합니다. 이 파일럿 그룹은 보다 광범위한 IT 사용자 집합을 포함하도록 확장할 수 있으며, 다른 조직 그룹 구성원도 포함할 수 있습니다.

### <a name="pilot"></a>파일럿
출시의 첫 단계는 파일럿 사용자를 대상으로 진행해야 합니다. 파일럿 사용자는 새 솔루션을 처음으로 사용하게 됨을 이해해야 합니다. 또한 구성, 설명서, 알림을 개선하고 이후 출시 단계에서 다른 모든 사용자를 위해 용이한 방법을 마련하는 데 도움이 되는 피드백을 적극 제공해야 합니다. 이러한 사용자는 임원 또는 VIP여서는 안 됩니다.

파일럿 단계는 [과제](planning-guide-deployment-goals.md)를 테스트하고 이전 단계에서 수집한 [요구 사항](planning-guide-requirements.md)을 세분화할 수 있는 좋은 기회입니다.

사용자에 대한 영향은 최소화하면서 문제를 해결할 수 있도록 [통신](planning-guide-communication-plan.md) 계획, [지원](planning-guide-support-plan.md) 계획, [테스트 및 유효성 검사](planning-guide-test-validation.md)를 포함하세요.

### <a name="production-rollout"></a>프로덕션 출시
파일럿을 효율적으로 완료한 후에는 조직의 나머지 그룹을 대상으로 전체 프로덕션 출시를 시작할 수 있습니다. 다양한 출시 그룹과 단계의 몇 가지 예는 다음과 같습니다.

- **부서** <br/>각 부서가 출시 단계일 수 있습니다. 한 번에 한 부서 전체를 대상으로 지정합니다. 이러한 유형의 출시에서 각 부서의 사용자는 대개 같은 방식으로 모바일 디바이스를 사용하고 같은 애플리케이션에 액세스합니다. 그리고 적용되는 정책 유형도 동일할 가능성이 높습니다.

- **지리적 위치** <br/>이 방식을 사용하는 경우에는 동일한 대륙, 국가/지역 또는 동일한 회사의 건물과 같은 특정 지리적 위치의 모든 사용자에게 솔루션을 배포합니다. 이 유형의 단계적 배포를 통해 사용자의 특정 위치에 솔루션을 중점적으로 배포할 수 있습니다. 따라서 동시에 Intune을 배포하는 위치의 수가 줄어들므로 더 많은 [화이트 글러브](#user-assisted-enrollment) 접근 방식을 제공할 수 있습니다. 동일한 위치에 다양한 부서 또는 사용 사례가 있을 수 있으므로 동시에 다양한 사용 사례를 배포하게 될 수 있습니다.

- **플랫폼** <br/>이 유형의 배포에서는 동시에 비슷한 플랫폼을 배포하게 됩니다. 첫 달에 모든 iOS/iPadOS 디바이스를 배포하고 다음 달에 Android, Windows 디바이스를 차례로 배포하는 경우를 예로 들 수 있습니다. 이 유형의 단계별 배포를 진행하면 기술 지원팀이 한 번에 하나의 플랫폼만 지원하면 되므로 지원을 손쉽게 제공할 수 있습니다.

다음은 대상 그룹 및 타임라인이 포함된 Intune 출시 계획의 예입니다.

| **출시 단계** | **7월** | **8월** | **9월** | **10월** |
|:---:|:---:|:---:|:---:|:---:|
| 제한된 파일럿 | IT(50명의 사용자) |  |  |  |                                                         
| 확장된 파일럿 | IT(200명의 사용자), IT 임원(10명의 사용자) |  |  |  |                                                         
| 프로덕션 출시 단계 1 |  | 영업 및 마케팅(2,000명의 사용자) |  |  |
| 프로덕션 출시 단계 2 |  |  | 소매(1,000명의 사용자) |  |
| 프로덕션 출시 단계 3 |  |  |  | HR(50명의 사용자), 재무(40명의 사용자), 임원(30명의 사용자) |

[위 표의 템플릿을 다운로드](https://gallery.technet.microsoft.com/Intune-deployment-planning-fae156c2?redir=0)하여 조직의 출시 단계를 입력할 수 있습니다.
## <a name="match-rollout-groups-to-enrollment-approaches"></a>출시 그룹과 일치하는 등록 방식 선택

Intune 출시에 대한 대상 그룹 및 시간을 결정했으므로 다음 단계에서는 각 그룹에 대해 가장 적절한 Intune 등록 방식을 선택합니다. 다음과 같은 여러 가지 등록 방식을 사용할 수 있습니다.
* 사용자 셀프 서비스
* 사용자 지원 등록
* IT 기술 박람회

### <a name="user-self-service"></a>사용자 셀프 서비스

이 경우에는 사용자가 일반적으로 IT 조직에서 제공하는 등록 지침에 따라 자신의 디바이스를 직접 등록합니다. 이 방식은 조직에서 가장 일반적으로 사용되며, 사용자 지원 등록보다 더 확장성이 큽니다.

### <a name="user-assisted-enrollment"></a>사용자 지원 등록

"화이트 글러브"라고도 하는 이 방식에서는 IT 팀 구성원이 직접 대면 방식이나 Skype를 통해 사용자의 등록 프로세스를 지원합니다. 이 방식은 일반적으로 임원진 및 등록 프로세스 중에 더 많은 도움을 필요로 할 수 있는 기타 그룹에서 사용됩니다.

### <a name="it-tech-fair"></a>IT 기술 박람회

Intune 사용자 등록을 위한 또 다른 옵션은 IT 기술 박람회를 개최하는 것입니다. 이 이벤트에서 IT 그룹이 설치하는 Intune 등록 지원 부스를 통해 사용자는 Intune 등록 관련 정보를 얻고, 질문을 하고, 등록 프로세스 관련 지원을 받을 수 있습니다. 이 옵션은 특히 Intune 출시의 초기 단계에서 IT 그룹과 사용자에게 모두 유익할 수 있습니다.

등록 방식이 포함된 위의 Intune 출시 계획의 업데이트된 예는 다음과 같습니다.

| **출시 단계** | **7월** | **8월** | **9월** | **10월** |
|:---:|:---:|:---:|:---:|:---:|
| 제한된 파일럿 |  |  |  |  |
| 셀프 서비스 | IT |  |  |  |
| 확장된 파일럿 |  |  |  |  |
| 셀프 서비스 | IT |  |  |  |
| 화이트 글러브 | IT 임원 |  |  |  |
| 프로덕션 출시 단계 1 |  | 영업, 마케팅 |  |  |
| 셀프 서비스 |  | 영업 및 마케팅 |  |  |
| 프로덕션 출시 단계 2 |  |  | 소매 |  |
| 셀프 서비스 |  |  | 소매 |  |
| 프로덕션 출시 단계 3 |  |  |  | 임원, HR, 재무 |
| 셀프 서비스 |  |  |  | HR, 재무 |
| 화이트 글러브 |  |  |  | 임원 |

## <a name="next-steps"></a>다음 단계

다음 섹션에서는 [Intune 출시 통신 계획 개발](planning-guide-communication-plan.md)에 대한 지침을 제공합니다.
