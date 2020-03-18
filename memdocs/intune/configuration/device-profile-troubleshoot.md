---
title: Microsoft Intune - Azure에서 디바이스 프로필 문제 해결 | Microsoft Docs
description: Microsoft Intune을 사용하는 경우 사용자나 디바이스에 적용되지 않은 프로필 변경, 새 정책이 디바이스에 적용되는 데 얼마나 걸리는지, 여러 정책이 있을 때 어떤 설정을 적용하는지, 프로필이 삭제되거나 제거되면 어떻게 되는지 등을 포함한 디바이스 정책 및 프로필의 일반적인 질문과 답변입니다.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 02/18/2020
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 67d0d271b5befc65ad286a8da6e00f647973d73d
ms.sourcegitcommit: 3d895be2844bda2177c2c85dc2f09612a1be5490
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79364463"
---
# <a name="common-questions-issues-and-resolutions-with-device-policies-and-profiles-in-microsoft-intune"></a>Microsoft Intune의 디바이스 정책 및 프로필을 통한 일반적인 질문, 이슈 및 해결 방법

Intune의 디바이스 프로필 및 정책을 사용하는 경우 일반적인 질문에 대한 답변을 얻을 수 있습니다. 이 문서에서는 체크 인 시간 간격을 나열하고, 충돌에 대한 추가적인 세부 정보 등도 제공합니다.

## <a name="why-doesnt-a-user-get-a-new-profile-when-changing-a-password-or-passphrase-on-an-existing-wi-fi-profile"></a>기존 Wi-Fi 프로필에서 암호를 변경할 때 사용자가 새 프로필을 받지 못하는 이유는 무엇인가요?

회사 Wi-Fi 프로필을 만들고, 프로필을 그룹에 배포하고, 암호를 변경하고, 프로필을 저장합니다. 프로필을 변경할 때 일부 사용자는 새 프로필을 가져올 수 없습니다.

이 문제를 완화하려면 게스트 Wi-Fi를 설정 합니다. 회사 Wi-Fi가 실패하는 경우 사용자는 게스트 Wi-Fi에 연결할 수 있습니다. 자동으로 연결 설정을 사용할 수 있도록 합니다. 모든 사용자에게 게스트 Wi-Fi 프로필을 배포 합니다.

일부 추가 권장 사항.  

- 연결하려는 Wi-Fi 네트워크에 암호가 사용되는 경우 Wi-Fi 라우터에 직접 연결할 수 있는지 확인합니다. iOS/iPadOS 디바이스로 테스트할 수 있습니다.
- Wi-Fi 엔드포인트(Wi-Fi 라우터)에 연결을 완료한 후 사용한 SSID와 자격 증명(이 값은 암호)을 기록해 둡니다.
- 미리 공유한 키 필드에 SSID와 자격 증명(암호)을 입력합니다. 
- 사용자 수가 제한된 테스트 그룹(가급적 IT 팀)에 배포합니다. 
- iOS/iPadOS 디바이스를 Intune에 동기화합니다. 아직 등록하지 않은 경우 등록합니다. 
- 동일한 Wi-Fi 엔드포인트에 다시 연결을 테스트합니다(첫 번째 단계 참조).
- 더 큰 그룹에 롤아웃하고 최종적으로 조직의 모든 예상 사용자에게 롤아웃합니다. 

## <a name="how-long-does-it-take-for-devices-to-get-a-policy-profile-or-app-after-they-are-assigned"></a>정책, 프로필 또는 앱을 할당한 후 디바이스에서 해당 정책, 프로필 또는 앱을 수신할 때까지 걸리는 시간

Intune 서비스에서 디바이스에 체크 인을 알립니다. 알림 시간은 즉시에서 몇 시간까지 다양합니다. 이러한 알림 시간은 플랫폼에 따라서도 다릅니다.

첫 번째 알림 이후 디바이스가 정책 또는 프로필을 수신하기 위해 체크 인하지 않으면 알림을 3번 더 보냅니다. 꺼져 있거나 네트워크에 연결되지 않은 오프라인 디바이스는 알림을 받지 못할 수 있습니다. 이 경우 디바이스는 Intune 서비스를 사용하여 예약된 다음 체크 인에서 정책 또는 프로필을 가져옵니다. 규정을 준수하지 않는 상태로 전환하는 디바이스를 포함하여 비준수에 대해 확인하는 경우에도 마찬가지입니다.

**예상** 빈도:

| 플랫폼 | 새로 고침 주기|
| --- | --- |
| iOS/iPadOS | 약 8시간마다 |
| macOS | 약 8시간마다 |
| Android | 약 8시간마다 |
| 디바이스로 등록된 Windows 10 PC | 약 8시간마다 |
| Windows Phone | 약 8시간마다 |
| Windows 8.1 | 약 8시간마다 |

최근 등록된 디바이스의 경우 다음과 같이 준수, 비준수 및 구성 체크 인이 더 자주 실행됩니다. **예상 시간**은 다음과 같습니다.

| 플랫폼 | 빈도 |
| --- | --- |
| iOS/iPadOS | 1시간 동안 15분마다/그 이후에는 8시간마다 |  
| macOS | 1시간 동안 15분마다/그 이후에는 8시간마다 | 
| Android | 15분 동안 3분마다/그 이후 2시간 동안은 15분마다/그 이후에는 약 8시간마다 | 
| 디바이스로 등록된 Windows 10 PC | 15분 동안 3분마다/그 이후 2시간 동안은 15분마다/그 이후에는 약 8시간마다 | 
| Windows Phone | 15분 동안 5분마다/그 이후 2시간 동안은 15분마다/그 이후에는 약 8시간마다 | 
| Windows 8.1 | 15분 동안 5분마다/그 이후 2시간 동안은 15분마다/그 이후에는 약 8시간마다 | 

언제든 사용자는 회사 포털 앱을 열고 **설정** > **동기화**로 정책 또는 프로필 업데이트를 즉시 확인할 수 있습니다.

## <a name="what-actions-cause-intune-to-immediately-send-a-notification-to-a-device"></a>Intune에서 디바이스에 알림을 즉시 보내도록 하는 작업

정책, 프로필 또는 앱이 할당되거나(또는 할당되지 않거나) 업데이트되거나, 삭제되는 등과 같이 알림을 트리거하는 다양한 작업이 있습니다. 이러한 작업 시간은 플랫폼마다 다릅니다.

디바이스는 체크 인하라는 알림을 받거나 예약된 체크 인 시간 동안 Intune에 체크 인합니다. 잠금, 암호 재설정, 앱, 프로필 또는 정책 할당과 같은 작업을 통해 디바이스 또는 사용자를 대상으로 지정하면, Intune에서 이러한 업데이트를 받으려면 체크 인해야 한다는 알림을 디바이스에 즉시 보냅니다.

회사 포털 앱에서 연락처 정보를 수정하는 등의 기타 변경 작업을 수행하는 경우에는 디바이스에 알림이 즉시 전송되지 않습니다.

정책 또는 프로필의 설정은 모든 체크 인에 적용됩니다. [Windows 10 MDM 정책 새로 고침 블로그 게시물](https://www.petervanderwoude.nl/post/windows-10-mdm-policy-refresh/)이 좋은 리소스가 될 수 있습니다.

## <a name="if-multiple-policies-are-assigned-to-the-same-user-or-device-how-do-i-know-which-settings-gets-applied"></a>여러 정책을 같은 사용자 또는 디바이스에 할당하는 경우 적용되는 설정은 어떻게 확인할 수 있는가요?

둘 이상의 정책을 같은 사용자 또는 디바이스에 할당하면 적용되는 설정이 개별 설정 수준에서 적용됩니다.

- 준수 정책 설정은 항상 구성 프로필 설정보다 우선적으로 적용됩니다.

- 준수 정책이 다른 준수 정책의 동일 설정과 대조해 평가되는 경우 가장 제한적인 준수 정책 설정이 적용됩니다.

- 구성 정책 설정이 다른 구성 정책의 설정과 충돌하는 경우 이 충돌은 Intune에 표시됩니다. 수동으로 이러한 충돌을 해결합니다.

## <a name="what-happens-when-app-protection-policies-conflict-with-each-other-which-one-is-applied-to-the-app"></a>앱 보호 정책이 서로 충돌하는 경우 어떤 정책을 앱에 적용해야 할까요?

다시 설정 전까지의 PIN 입력 시도와 같이 숫자 입력 필드에 대한 설정을 ‘제외’하면, 충돌하는 값은 앱 보호 정책에서 사용 가능한 가장 제한적인 설정으로 지정됩니다.  권장 설정 옵션을 사용하여 MAM 정책을 만든 것처럼 숫자 입력 필드는 값과 동일하게 설정됩니다.

두 프로필 설정이 동일하면 충돌이 발생합니다. 복사/붙여넣기 설정을 제외하면 동일한 두 MAM 정책을 구성한 경우를 예로 들 수 있습니다. 이 시나리오에서는 복사/붙여넣기 설정이 가장 제한적인 값으로 설정되지만, 나머지 설정은 구성된 대로 적용됩니다.

정책이 앱에 배포되고 적용됩니다. 두 번째 정책이 배포됩니다. 이 시나리오에서는 첫 번째 정책이 우선 적용되어 계속 적용됩니다. 두 번째 정책은 충돌을 보여 줍니다. 둘 다 동시에 적용되면 이전 정책이 없으므로 두 정책이 충돌하게 됩니다. 충돌하는 설정은 가장 제한적인 값으로 설정됩니다.

## <a name="what-happens-when-iosipados-custom-policies-conflict"></a>iOS/iPadOS 사용자 지정 정책 충돌 시의 결과

Intune은 Apple 구성 파일 또는 사용자 지정 OMA-URI(Open Mobile Alliance Uniform Resource Identifier) 정책 페이로드를 평가하지 않으며 전달 메커니즘으로만 작동합니다.

사용자 지정 정책을 할당할 때는 구성된 설정이 준수, 구성 또는 기타 사용자 지정 정책과 충돌하지 않는지 확인해야 합니다. 사용자 지정 정책과 그 설정이 충돌하는 경우 설정은 임의로 적용됩니다.

## <a name="what-happens-when-a-profile-is-deleted-or-no-longer-applicable"></a>프로필이 삭제되거나 더 이상 적용할 수 없는 경우 어떻게 되나요?

프로필을 삭제하거나 프로필이 있는 그룹에서 디바이스를 제거하면, 다음과 같이 설명된 대로 디바이스에서 프로필 및 설정이 제거됩니다.

- Wi-Fi, VPN, 인증서 및 이메일 프로필: 이러한 프로필은 지원되는 모든 등록된 디바이스에서 제거됩니다.
- 모든 기타 프로필 유형:  

  - **Windows 및 Android 디바이스**: 설정이 디바이스에서 제거되지 않습니다.
  - **Windows Phone 8.1 디바이스**: 다음 설정이 제거됩니다.  
  
    - 모바일 디바이스의 잠금을 해제하는 데 암호 필요
    - 단순 암호 허용
    - 최소 암호 길이
    - 필수 암호 유형
    - 암호 만료(일)
    - 암호 기록 기억
    - 디바이스를 초기화하기 전까지 허용되는 로그인 반복 오류 횟수
    - 암호를 요구하기 전까지 비활성 시간(분)
    - 필수 암호 유형 - 최소 문자 집합 수
    - 카메라 허용
    - 모바일 디바이스 암호화 필요
    - 이동식 스토리지 허용
    - 웹 브라우저 허용
    - 앱 스토어 허용
    - 화면 캡처 허용
    - 지리적 위치 허용
    - Microsoft 계정 허용
    - 복사 및 붙여넣기 허용
    - Wi-Fi 테더링 허용
    - 무료 Wi-Fi 핫스팟에 자동 연결 허용
    - Wi-Fi 핫스팟 보고 허용
    - 초기화 허용
    - Bluetooth 허용
    - NFC 허용
    - Wi-Fi 허용

  - **iOS/iPadOS**: 다음을 제외한 모든 설정이 제거됩니다.
  
    - 음성 로밍 허용
    - 데이터 로밍 허용
    - 로밍하는 동안 자동 동기화 허용

## <a name="i-changed-a-device-restriction-profile-but-the-changes-havent-taken-effect"></a>디바이스 제한 프로필을 변경했지만 변경 내용이 적용되지 않습니다.

설정된 후 Windows Phone 디바이스에서는 MDM 또는 EAS를 사용하여 설정된 보안 정책의 보안이 저하되는 것을 허용하지 않습니다. 예를 들어 **문자 암호의 최소 수**를 8로 설정합니다. 이 수를 4로 줄이려고 합니다. 더 제한적인 프로필이 이미 디바이스에 적용되었습니다.

프로필을 덜 안전한 값으로 변경하려면 보안 정책을 다시 설정합니다. 예를 들어 Windows 8.1의 데스크톱에서 오른쪽에서 안쪽으로 살짝 민 후 **설정** > **제어판**을 선택합니다. **사용자 계정** 애플릿을 선택합니다. 왼쪽 탐색 메뉴에서 **보안 정책 재설정** 링크가 있습니다(아래쪽 방향). 이를 선택한 다음, **정책 다시 설정**을 선택합니다.

Android, Windows Phone 8.1 이상, iOS/iPadOS 및 Windows 10과 같은 기타 MDM 디바이스의 경우 제한적이지 않은 프로필을 적용할 수 있도록 사용을 중지하고 Intune에 다시 등록해야 합니다.

## <a name="some-settings-in-a-windows-10-profile-return-not-applicable"></a>Windows 10 프로필의 일부 설정은 "해당 없음"을 반환합니다.

Windows 10 디바이스의 일부 설정은 "해당 없음"으로 표시될 수 있습니다. 이 경우 해당 특정 설정은 디바이스에서 실행되는 Windows 버전에서 지원되지 않습니다. 이 메시지는 다음과 같은 이유로 발생할 수 있습니다.

- 설정은 디바이스의 현재 OS(운영 체제) 버전이 아닌 최신 버전의 Windows에서만 제공됩니다.
- 설정은 Home, Professional, Enterprise 및 Education과 같은 특정 Windows 버전 또는 특정 SKU에 대해서만 제공됩니다.

다양한 설정에 대한 버전 및 SKU 요구 사항에 대해 자세히 알아보려면 [CSP(구성 서비스 공급 기업) 참조](https://docs.microsoft.com/windows/client-management/mdm/configuration-service-provider-reference)를 참조하세요.

## <a name="next-steps"></a>다음 단계

추가 도움이 필요하십니까? [Microsoft Intune에 대한 지원을 받는 방법](../fundamentals/get-support.md)을 참조하십시오.
