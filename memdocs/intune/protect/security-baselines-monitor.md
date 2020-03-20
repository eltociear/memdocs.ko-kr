---
title: Microsoft Intune에서 보안 기준의 성공 또는 실패 확인 - Azure | Microsoft Docs
description: Microsoft Intune MDM에서 사용자 및 디바이스에 보안 기준을 배포할 때 오류, 충돌 및 성공 상태를 확인합니다. Intune에서 클라이언트 로그 및 보고서 기능을 사용하여 문제를 해결하는 방법을 참조하세요.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 03/04/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: shpate
ms.suite: ems
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: e51e969abcc4e8ab1b37796df72381fa3bdbe335
ms.sourcegitcommit: 3d895be2844bda2177c2c85dc2f09612a1be5490
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79351099"
---
# <a name="monitor-security-baseline-and-profiles-in-microsoft-intune"></a>Microsoft Intune에서 보안 기준 및 프로필 모니터링

Intune은 보안 기준을 모니터링하는 여러 가지 옵션을 제공합니다. 사용자 및 디바이스에 적용되는 보안 기준 프로필을 모니터링할 수 있습니다. 또한 실제 기준 및 권장된 값과 일치(또는 일치하지 않는)하는 모든 디바이스를 모니터링할 수도 있습니다.

이 문서에서는 두 모니터링 옵션을 안내합니다.

[Intune의 보안 기준](security-baselines.md)은 Microsoft Intune의 보안 기준 기능에 대한 자세한 정보를 제공합니다.

## <a name="monitor-the-baseline-and-your-devices"></a>기준 및 디바이스 모니터링

기준을 모니터링하면 Microsoft의 추천에 따라 디바이스의 보안 상태에 대한 인사이트를 얻을 수 있습니다. Intune 콘솔에 있는 보안 기준의 개요 창에서 이러한 인사이트를 볼 수 있습니다.  기준을 처음으로 할당한 후 최대 24시간 내에 데이터가 표시됩니다. 이후에 변경하는 내용은 최대 6시간 내에 표시됩니다.

기준 및 디바이스의 모니터링 데이터를 보려면 [Microsoft Endpoint Manager 관리 센터](https://go.microsoft.com/fwlink/?linkid=2109431)에 로그인합니다. 다음으로, **엔드포인트 보안** > **보안 기준**을 선택하고, 기준을 선택하고, **개요** 창을 봅니다.

**개요** 창은 상태를 모니터링하는 두 가지 방법을 제공합니다.

- **디바이스 보기** - 기준의 각 상태 범주에 포함되는 디바이스 수에 대한 요약 정보입니다.
- **범주별** - 기준의 각 범주를 표시하고 각 기준 범주의 각 상태 그룹에 해당하는 디바이스 비율을 보여주는 보기입니다.

각 디바이스는 *디바이스* 보기와 *범주별* 보기에 모두 사용되는 다음 상태 중 하나로 표시됩니다.

- **기준과 일치** - 기준의 모든 설정이 권장 설정과 일치합니다.
- **기준과 불일치** - 기준에서 하나 이상의 설정이 원래 기준의 기본값에서 수정되었습니다. 각 보안 기준의 기본값은 해당 기준에 대한 권장 값입니다.

  > [!NOTE]
  > 기준 프로필을 만들거나 편집하는 경우 기본값 또는 구성 설정을 변경하면 *기준과 불일치* 상태가 발생합니다. 변경된 설정을 결정하는 데 도움이 필요한 경우 Microsoft 지원 팀에 문의하세요. 

- **잘못 구성됨** - 하나 이상의 설정이 잘못 구성되었습니다. 이 상태는 설정이 충돌, 오류 또는 보류 중 상태에 있음을 의미합니다.
- **적용 불가** - 하나 이상의 설정을 적용할 수 없어 적용되지 않습니다.

### <a name="device-view"></a>디바이스 보기

개요 창에는 기준과 비교하여 각 상태에 포함된 디바이스 수를 차트로 요약하는 **할당된 Windows 10 디바이스의 보안 기준 상태**가 표시됩니다.

![디바이스의 상태 확인](./media/security-baselines-monitor/overview.png)

디바이스의 상태가 기준의 다른 범주와 다른 경우 해당 디바이스는 단일 상태로 표시됩니다. 디바이스를 나타내는 상태의 우선 순위는 **잘못 구성됨**, **기준과 불일치**, **적용할 수 없음**, **기준과 일치**의 순서대로 적용됩니다.

예를 들어 디바이스에 *잘못 구성됨*으로 분류되는 설정 하나와 *기준과 불일치*로 분류되는 설정이 하나 이상 있는 경우 해당 디바이스는 *잘못 구성됨*으로 분류됩니다.

차트를 클릭하면 다양한 상태의 디바이스 목록을 드릴스루하여 살펴볼 수 있습니다. 그런 다음, 목록에서 개별 디바이스를 선택하여 개발 디바이스의 세부 정보를 볼 수 있습니다. 예를 들면 다음과 같습니다.

- **디바이스 구성**을 선택하고, 오류 상태인 프로필을 선택합니다.

  ![프로필 상태 보기](./media/security-baselines-monitor/device-configuration-profile-list.png)

- 오류 프로필을 선택합니다. 프로필의 모든 설정 목록 및 해당 상태가 표시됩니다. 이제 스크롤하여 오류를 발생시키는 설정을 확인할 수 있습니다.

  ![오류를 발생시키는 설정 확인](./media/security-baselines-monitor/profile-with-error-status.png)

이 보고를 사용하여 프로필에서 문제를 발생시키는 설정을 확인합니다. 또한 디바이스에 배포된 정책 및 프로필에 대한 자세한 정보를 가져옵니다.

> [!NOTE]
> 기준에서 속성이 **구성되지 않음**으로 설정된 경우 설정이 무시되고, 제한이 적용되지 않습니다. 속성은 보고에 표시되지 않습니다.

### <a name="per-category-view"></a>범주별 보기

개요 창에는 기준에 대한 범주별 차트인 **범주별 보안 기준 상태**가 표시됩니다.  이 보기는 기준의 각 범주를 표시하고 각 범주의 상태로 분류되는 디바이스 백분율을 보여줍니다.

![범주별 상태 보기](./media/security-baselines-monitor/monitor-baseline-per-category.png)

모든 디바이스가 기준과 일치 상태를 보고하기 전에는 **기준과 일치** 상태가 표시되지 않습니다.

열의 맨 위에서 위쪽/아래쪽 화살표 아이콘을 선택하여 각 열을 기준으로 범주별 보기를 정렬할 수 있습니다.

## <a name="monitor-the-profile"></a>프로필 모니터링

프로필을 모니터링하면 디바이스의 배포 상태에 대한 인사이트를 제공하지만 기준 권장 사항에 따른 보안 상태를 제공하지 않습니다.

1. Intune에서 **보안 기준**을 선택하고 > 기준 > **만든 프로필**을 선택합니다.

2. 프로필을 선택합니다. **개요**에서 이미지는 이 프로필이 할당된 디바이스 및 사용자의 수를 보여줍니다.

   ![보안 기준 프로필이 할당된 디바이스 및 사용자의 수 확인](./media/security-baselines-monitor/existing-profile-overview.png)

3. **관리** > **속성** 아래에 기준의 모든 설정 목록이 표시됩니다. 이러한 설정을 변경할 수도 있습니다.

   ![보안 기준 프로필에서 설정 확인 및 업데이트](./media/security-baselines-monitor/manage-settings.png)

4. **모니터**에서 개별 디바이스에 대한 프로필의 배포 상태, 각 사용자에 대한 상태 및 기준에서 각 설정에 대한 상태를 확인할 수 있습니다.

   ![보안 기준 프로필에 대한 다양한 모니터링 옵션 확인](./media/security-baselines-monitor/monitor-status-options.png)

## <a name="view-endpoint-security-configurations-per-device"></a>디바이스별 엔드포인트 보안 구성 보기

개별 디바이스에 적용되는 보안 구성의 세부 정보를 확인합니다. 이 정보를 사용하여 잘못 구성된 설정을 격리할 수 있습니다.

1. [Microsoft Endpoint Manager 관리 센터](https://go.microsoft.com/fwlink/?linkid=2109431)에 로그인합니다.

2. **디바이스** > **모든 디바이스**로 이동하고 보려는 디바이스를 선택합니다.

3. ‘모니터’ 범주에서 **엔드포인트 보안 구성**을 선택하여 해당 디바이스에 적용되는 보안 구성 목록을 확인합니다. 

4. 엔드포인트 보안 구성을 선택하여 상세히 검색하고 디바이스에서 해당 보안 구성의 평가에 대한 추가 세부 정보를 볼 수 있습니다.

## <a name="troubleshoot-using-per-setting-status"></a>설정당 상태를 사용하여 문제 해결

보안 기준을 배포했지만 배포 상태가 오류를 표시합니다. 다음 단계는 오류 문제 해결에 대한 일부 지침을 제공합니다.

1. Intune에서 **보안 기준**을 선택하고 > 기준 > **만든 프로필**을 선택합니다.

2. **모니터** > **설정당 상태**에서 프로필을 선택합니다.

3. 표는 모든 설정 및 각 설정의 상태를 보여줍니다. **오류** 열 또는 **충돌** 열을 선택하여 오류를 발생시키는 설정을 확인합니다.

### <a name="mdm-diagnostic-information"></a>MDM 진단 정보

이제 문제가 있는 설정을 알 수 있습니다. 다음 단계는 이 설정이 오류 또는 충돌을 발생시키는 이유를 확인하는 것입니다.

Windows 10 디바이스에는 기본 제공 MDM 진단 정보 보고서가 있습니다. 이 보고서는 기본값, 현재 값을 포함하고, 정책을 나열하고, 디바이스 또는 사용자에게 배포되었는지 여부를 보여줍니다. 이 보고서를 사용하면 설정이 충돌 또는 오류를 발생시키는 이유를 확인하는 데 도움이 됩니다.

1. 디바이스에서 **설정** > **계정** > **회사 또는 학교 액세스**로 이동합니다.

2. 계정 > **정보** > **고급 진단 보고서** > **보고서 만들기**를 선택합니다.

3. **내보내기**를 선택하고, 생성된 파일을 엽니다.

4. 보고서의 여러 섹션에서 오류 또는 충돌 설정을 찾습니다.

  예를 들어 **등록된 구성 원본 및 대상 리소스** 섹션 또는 **관리되지 않는 정책** 섹션을 봅니다. 오류 또는 충돌을 발생시킨 이유를 찾을 수 있습니다.

[Windows 10에서 MDM 실패 진단](https://docs.microsoft.com/windows/client-management/mdm/diagnose-mdm-failures-in-windows-10)은 이 기본 제공 보고서에 대한 자세한 정보를 제공합니다.

> [!TIP]
>
> - 또한 일부 설정은 GUID를 나열합니다. 설정 값에 대한 로컬 레지스트리(regedit)에서 이 GUID를 검색할 수 있습니다.
> - 이벤트 뷰어 로그는 문제가 있는 설정에 대한 일부 오류 정보를 포함할 수도 있습니다(**이벤트 뷰어** > **애플리케이션 및 서비스 로그** > **Microsoft** > **Windows** > **DeviceManagement-엔터프라이즈-진단-공급 기업** > **관리자**).

## <a name="next-steps"></a>다음 단계

[디바이스 프로필 모니터링](../configuration/device-profile-monitor.md) 및 [몇 가지 일반적인 문제 및 해결 방법 확인](../configuration/device-profile-troubleshoot.md)
