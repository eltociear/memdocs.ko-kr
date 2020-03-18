---
title: 앱 보호 정책을 모니터링하는 방법
titleSuffix: Microsoft Intune
description: 이 항목에서는 Intune에서 앱 보호 정책을 모니터링하는 방법에 대해 설명합니다.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 02/28/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 9b0afb7d-cd4e-4fc6-83e2-3fc0da461d02
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 39551ec60e41a7bc3d6c7f63e16f622b64a5669c
ms.sourcegitcommit: 3d895be2844bda2177c2c85dc2f09612a1be5490
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79342142"
---
# <a name="how-to-monitor-app-protection-policies"></a>앱 보호 정책을 모니터링하는 방법
[!INCLUDE [azure_portal](../includes/azure_portal.md)]

[Azure Portal](https://portal.azure.com)의 Intune 앱 보호 창에서 사용자에게 적용한 앱 보호 정책의 상태를 모니터링할 수 있습니다. 또한 앱 보호 정책, 정책 준수 상태, 사용자에게 발생할 수 있는 문제에 따라 영향을 받는 사용자 정보를 확인할 수 있습니다.

앱 보호 정책을 모니터링 하는 세 가지 방법이 있습니다.
- 요약 보기
- 상세 보기
- 보고 보기

앱 보호 데이터의 보존 기간은 90일입니다. 최근 90일 내에 Intune 서비스에 체크인한 앱 인스턴스는 앱 보호 상태 보고서에 포함됩니다. *앱 인스턴스*는 고유한 사용자 + 앱 + 디바이스입니다. 

> [!NOTE]
> 자세한 내용은 [앱 보호 정책을 만들고 할당하는 방법](app-protection-policies.md)을 참조하세요.

## <a name="summary-view"></a>요약 보기

1. [Microsoft Endpoint Manager 관리 센터](https://go.microsoft.com/fwlink/?linkid=2109431)에 로그인합니다.
3. **앱** > **모니터링** > **앱 보호 상태**를 선택합니다.

   ![Intune 모바일 애플리케이션 관리 창의 요약 타일 스크린샷](./media/app-protection-policies-monitor/app-protection-user-status-summary.png)

- **할당된 사용자**: 업무 환경의 정책에 연결된 앱을 사용하고 보호되고 라이선스가 부여된 회사의 할당된 사용자 및 보호되지 않고 라이선스가 부여되지 않은 할당된 사용자의 총 수입니다.
- **플래그가 지정된 사용자**: 디바이스에 문제가 발생하는 사용자 수입니다. 무단 해제된(iOS/iPadOS) 디바이스와 루팅된(Android) 디바이스는 **플래그가 지정된 사용자**로 보고됩니다. 또한 Google SafetyNet 디바이스 증명 검사(IT 관리자가 켜는 경우)를 통해 플래그가 지정되는 디바이스를 가진 사용자는 여기에서 보고됩니다. 
- **잠재적으로 유해한 앱이 있는 사용자**: Google Play 보호를 통해 검색된 Android 디바이스에 유해한 앱이 있을 수 있는 사용자 수입니다. 
- **iOS 사용자 상태** 및 **Android 사용자 상태**: 관련된 플랫폼에 대한 업무 환경에서 할당된 정책이 있는 앱을 사용한 사용자 수입니다. 이 정보는 정책에서 관리되는 사용자 수뿐만 아니라 업무 환경에서 정책에 의해 지정되지 않은 앱을 사용하는 사용자의 수를 보여줍니다. 정책에 이러한 사용자를 추가하는 것이 좋습니다.
- **상위 보호된 iOS/iPadOS 앱** 및 **상위 보호된 Android 앱**: 이 정보는 가장 많이 사용하는 iOS/iPadOS 및 Android 앱을 기반으로 플랫폼별 보호된/보호되지 않은 앱 수를 보여줍니다.
- **등록 없이 구성된 상위 iOS/iPadOS 앱** 및 **등록 없이 구성된 상위 Android 앱**: 이 정보는 등록되지 않은 디바이스의 가장 많이 사용하는 iOS/iPadOS 및 Android 앱을 기반으로 구성된(즉, 앱 구성 정책을 사용한) 앱의 수를 플랫폼별로 보여 줍니다.

    > [!NOTE]
    > 플랫폼당 정책이 여러 개 있는 경우 사용자에게 하나 이상의 정책이 할당되면 정책을 통해 사용자를 관리하는 것으로 간주됩니다.

## <a name="detailed-view"></a>상세 보기
**플래그가 지정된 사용자** 타일과 **잠재적으로 유해한 앱이 있는 사용자** 타일을 선택해 요약의 자세한 보기를 볼 수 있습니다.

### <a name="flagged-users"></a>플래그가 지정된 사용자
상세 보기는 오류 메시지, 오류가 발생했을 때 액세스된 앱, 영향을 받는 디바이스 OS 플랫폼 및 타임스탬프를 표시합니다. 오류는 일반적으로 무단 해제(iOS/iPadOS) 또는 루팅(Android)된 디바이스에 대한 것입니다. 또한 ‘SafetyNet 디바이스 증명’ 조건부 시작 검사로 플래그가 지정되는 디바이스를 가진 사용자는 Google에서 보고한 이유와 함께 여기에서 보고됩니다. 사용자를 보고서에서 제거하려면 결과를 보고해야 하는 다음 루트 검색 검사(또는 탈옥 검사/SafetyNet 검사 발생) 이후에 발생하는 디바이스 자체의 상태를 변경해야 합니다. 디바이스가 실제로 재구성된 경우 창이 다시 로드될 때 플래그가 지정된 사용자 보고서에서 새로 고침이 수행됩니다.

### <a name="users-with-potentially-harmful-apps"></a>잠재적으로 유해한 앱이 있는 사용자
**앱에서 위협 검색 필요** 조건부 시작 검사로 플래그가 지정되는 디바이스를 가진 사용자는 Google에서 보고한 위협 범주와 함께 여기에서 보고됩니다. 이 보고서에 Intune을 통해 배포되는 앱이 나열되는 경우, 앱의 앱 개발자에게 문의하거나 사용자에게 할당되지 않도록 앱을 제거합니다. 자세히 보기에는 다음이 표시됩니다.

- **사용자**: 사용자의 이름입니다.
- **앱 패키지 ID**: Android OS가 앱의 고유성을 확인하는 방식입니다.
- **앱이 MAM을 지원하는지 여부**: 앱이 Microsoft Intune으로 배포되었는지 확인합니다. 
- **위협 범주**: Google이 분류한 앱 위협 범주입니다. 
- **이메일**: 사용자의 이메일입니다.
- **디바이스 이름**: 사용자 계정에 연결된 디바이스의 이름입니다.
- **타임스탬프**: Google이 잠재적으로 위험한 앱에 대해 Microsoft Intune에 최종 동기화한 날짜입니다.

## <a name="reporting-view"></a>보고 보기

**앱 보호 상태** 창 위쪽에서 동일한 보고서를 찾을 수 있습니다. 이러한 보고서를 보려면 **앱** > **앱 보호 상태** > **보고서**를 선택합니다. **보고서** 창은 다음을 비롯한 사용자와 앱을 기반으로 하는 여러 보고서를 제공합니다.

### <a name="user-report"></a>사용자 보고서

단일 사용자를 검색하고 해당 사용자에 대한 준수 상태를 확인할 수 있습니다. **앱 보고** 창은 선택한 사용자에 대한 다음 정보를 표시합니다.

- **아이콘**: 해당 앱 상태가 최신 상태인지 여부를 표시합니다.
- **앱 이름**: 앱의 이름입니다.
- **디바이스 이름**: 사용자 계정에 연결된 디바이스입니다.
- **디바이스 유형**: 디바이스가 실행 중인 디바이스 또는 운영 체제 유형입니다.
- **정책**: 앱과 연결된 정책입니다.
- **상태:**
  - **체크 인**: 정책이 사용자에게 배포되었고, 앱이 회사 컨텍스트에서 적어도 한 번 사용되었습니다.
  - **체크 인 안 됨**: 정책이 사용자에게 배포되었지만 그 후 회사 컨텍스트에서 앱이 사용되지 않았습니다.
- **마지막 동기화**: 앱이 Intune과 마지막으로 동기화된 시간입니다.

>[!NOTE]
> **마지막 동기화** 열은 콘솔 내 사용자 상태 보고서와 앱 보호 정책의 [내보낼 수 있는 .csv 보고서](https://docs.microsoft.com/intune/app-protection-policies-monitor#export-app-protection-activities)에서 동일한 값을 나타냅니다. 차이점은 두 보고서의 값 사이에 동기화가 약간 지연된다는 것입니다.
>
> 마지막 동기화에서 참조된 시간은 Intune에서 앱 인스턴스를 마지막으로 본 시점입니다. 사용자가 앱을 시작하면 마지막으로 체크 인된 시간에 따라 해당 시작 시간에 Intune 앱 보호 서비스에게 알릴 수 있습니다. [앱 보호 정책 체크 인 재시도 간격 시간](app-protection-policy-delivery.md)을 참조하세요. 사용자가 마지막 체크 인 간격(활성 사용일 경우 일반적으로 30분)에서 특정 앱을 사용한 적이 없는 상태로 앱을 시작한 경우 다음을 수행합니다.
>
> - 앱 보호 정책을 내보낼 수 있는 .csv 보고서는 최신 시간이 최소 1분에서 최대 30분 사이입니다.
> - 사용자 상태 보고서에 최신 시간이 즉시 적용됩니다.
>
> 예를 들어 오후 12시에 보호된 앱을 시작하는 사용이 허가된 대상 최종 사용자가 있다고 가정합니다.
>
> - 처음 로그인하는 경우 사용자가 이전에 로그아웃되었으며 Intune을 사용하여 앱 인스턴스를 등록하지 않았음을 의미합니다. 사용자가 로그인하면 사용자는 새 앱 인스턴스 등록을 가져오고 즉시 체크 인할 수 있습니다(향후 체크 인에 대해 이전에 나열된 동일한 시간 지연을 사용). 따라서 마지막 동기화 시간은 사용자 상태 보고서에서 오후 12시로 보고되고, 앱 보호 정책 보고서에는 오후 12시 1분(또는 늦어도 오후 12시 30분)으로 보고됩니다.
> - 사용자가 앱을 시작하는 경우 마지막으로 보고된 동기화 시간은 사용자가 마지막으로 체크 인한 시간에 따라 달라집니다.

사용자에 대한 보고를 확인하려면 다음 단계를 수행합니다.

1. 사용자를 선택하려면 **사용자 상태** 요약 타일을 선택합니다.

    ![Intune 모바일 애플리케이션 관리의 요약 타일 스크린샷](./media/app-protection-policies-monitor/MAM-reporting-6.png)

2. **앱 보고** 창에서 **사용자 선택**을 선택하여 Azure Active Directory 사용자를 검색합니다.

    ![앱 보고 창에서 사용자 선택 옵션의 스크린샷](./media/app-protection-policies-monitor/MAM-reporting-2.png)

3. 목록에서 사용자를 선택합니다. 해당 사용자에 대한 준수 상태의 세부 정보를 확인할 수 있습니다.

>[!NOTE]
> 검색한 사용자에게 배포된 MAM 정책이 없으면 해당 사용자가 MAM 정책의 대상이 아니라는 메시지가 표시됩니다.

### <a name="app-report"></a>앱 보고서
플랫폼 및 앱으로 검색할 수 있으며 이 보고서는 보고서를 생성하기 전에 선택할 수 있는 두 개의 서로 다른 앱 보호 상태를 제공합니다. 상태는 **보호됨** 또는 **보호되지 않음**일 수 있습니다.

  - 관리형 MAM 작업의 사용자 상태(**보호됨**): 이 보고서에서는 사용자 단위로 관리되는 각 MAM 앱의 작업에 대해 간략하게 설명합니다. 각 사용자에 대한 MAM 정책에서 대상으로 지정된 모든 앱과 MAM 정책으로 체크 인한 각 앱의 상태가 표시됩니다. 또한 보고서에는 MAM 정책의 대상으로 지정되었지만 체크 인되지 않은 각 앱의 상태도 포함됩니다.
  - 관리되는 않는 MAM 작업의 사용자 상태(**보호되지 않음**): 이 보고서에서는 사용자 단위로 현재 관리되지 않는 MAM 지원 앱 작업에 대해 간략하게 설명합니다. 이 문제는 다음과 같은 경우에 발생할 수 있습니다.
    - 해당 앱을 한 명의 사용자가 사용하거나, 현재 MAM 정책에서 대상으로 지정되지 않은 앱에서 사용
    - 모든 앱이 체크 인되었으나 MAM 정책을 가져오지 않음

    ![3개의 앱에 대한 세부 정보가 포함된 사용자 앱 보고 창 스크린샷](./media/app-protection-policies-monitor/MAM-reporting-4.png)

### <a name="user-configuration-report"></a>**사용자 구성 보고서**
선택한 사용자에 따라 이 보고서는 사용자가 받은 모든 앱 구성의 세부 정보를 제공합니다.

### <a name="app-configuration-report"></a>**앱 구성 보고서**
이 보고서는 선택한 플랫폼 및 앱을 기반으로 선택한 앱의 구성을 받은 사용자에 대한 세부 정보를 제공합니다.

### <a name="app-learning-report-for-windows-information-protection"></a>Windows Information Protection에 대한 앱 학습 보고서
이 보고서는 정책 경계를 넘으려고 시도하는 앱을 보여 줍니다.

### <a name="website-learning-for-windows-information-protection"></a>Windows Information Protection에 대한 웹 사이트 학습
이 보고서는 정책 경계를 넘으려고 시도하는 웹 사이트를 보여 줍니다.

## <a name="export-app-protection-activities"></a>앱 보호 활동 내보내기
모든 앱 보호 정책 활동을 단일 .csv 파일로 내보낼 수 있습니다. 이를 통해 사용자로부터 보고된 모든 앱 보호 상태를 분석할 수 있습니다. **App Protection .csv 파일 표시**:
- **사용자**: 사용자의 이름입니다.
- **이메일**: 사용자의 이메일입니다.
- **앱**: 앱의 이름입니다.
- **앱 버전**: 애플리케이션 버전입니다.
- **디바이스 이름**: 사용자 계정에 연결된 디바이스의 이름입니다.
- **디바이스 제조업체**: 디바이스를 제조한 업체를 표시합니다(Android 한정). 
- **디바이스 모델**: 디바이스를 제조한 업체를 표시합니다(Android 한정). 
- **Android 패치 버전**: 최신 Andorid 보안 패치 날짜입니다.
- **AAD 디바이스 ID**: 디바이스가 AAD에 가입된 경우 생성되는 열입니다.
- **MDM 디바이스 ID**: 디바이스가 Microsoft Intune MDM에 등록된 경우 생성되는 열입니다.
- **플랫폼**: 운영 체제입니다.
- **플랫폼 버전**: 운영 체제 버전입니다.
- **관리 유형**: 디바이스 관리 유형입니다. Android 엔터프라이즈, 관리되지 않는, MDM이 있습니다.  
- **앱 보호 상태**: 보호되지 않음, 보호자 지도 권장이 있습니다.
- **정책**: 앱과 연결된 앱 보호 정책입니다.
- **마지막 동기화**: 앱이 Microsoft Intune과 마지막으로 동기화된 시간입니다. 
- **준수 상태**: 사용자 디바이스의 앱이 앱 기반 조건부 액세스 정책을 준수하는지 여부입니다.  

다음 단계에 따라 앱 보호 .csv 파일 또는 앱 구성 .csv 파일을 생성합니다.

1. Intune 모바일 애플리케이션 관리 창에서 **앱 보호 보고서**를 선택합니다.

    ![앱 보호 다운로드 링크의 스크린샷](./media/app-protection-policies-monitor/app-protection-report-csv-2.png)

2. **예**를 선택하여 보고서를 저장한 다음 **다른 이름으로 저장**을 선택합니다. 보고서를 저장하려는 폴더를 선택합니다.

    ![보고서 저장 확인 상자 스크린 샷](./media/app-protection-policies-monitor/app-protection-report-csv-1.png)
   
> [!NOTE]
> Intune은 앱 등록 ID, Android 제조업체, 모델 및 보안 패치 버전을 포함한 추가 디바이스 보고 필드와 iOS/iPadOS 모델을 제공합니다. Intune에서 **앱** > **앱 보호 상태** > **앱 보호 보고서: iOS/iPadOS, Android**를 선택하여 이러한 필드에 액세스합니다. 또한 이러한 매개 변수를 사용하여 디바이스 제조업체(Android)의 **허용** 목록, 디바이스 모델(Android 및 iOS/iPadOS)의 **허용** 목록 및 **최소 Android 보안 패치 버전** 설정을 구성할 수 있습니다.   
 
## <a name="see-also"></a>참고 항목
- [iOS/iPadOS 앱 간의 데이터 전송 관리](data-transfer-between-apps-manage-ios.md)
- [Android 앱이 앱 보호 정책으로 관리될 때 예상되는 상황](../fundamentals/end-user-mam-apps-android.md)
- [iOS/iPadOS 앱이 앱 보호 정책으로 관리될 때 예상되는 상황](../fundamentals/end-user-mam-apps-ios.md)
