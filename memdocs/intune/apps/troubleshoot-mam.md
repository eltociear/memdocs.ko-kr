---
title: 모바일 애플리케이션 관리 문제 해결
titleSuffix: Microsoft Intune
description: 이 항목에서는 조건부 액세스 배포의 몇 가지 문제 해결 팁을 설명합니다.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/09/2020
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: cd5a0a3b-0013-4be3-a233-ce6e9083149f
ms.reviewer: mghadial
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 8405ef9c8d83583fe2ceb5da668ccfd79d23a39a
ms.sourcegitcommit: 3d895be2844bda2177c2c85dc2f09612a1be5490
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79334095"
---
# <a name="troubleshoot-mobile-application-management"></a>모바일 애플리케이션 관리 문제 해결

이 항목에서는 Intune 앱 보호(MAM 또는 모바일 애플리케이션 관리라고도 함)를 사용할 때 발생하는 일반적인 문제에 대한 솔루션을 제공합니다.

이 정보로 문제가 해결되지 않는 경우 [Microsoft Intune에 대한 지원을 받는 방법](../fundamentals/get-support.md)을 참조하여 도움을 얻을 수 있는 다른 방법을 찾아보세요.

## <a name="common-it-administrator-issues"></a>IT 관리자에게 일반적으로 발생하는 문제

IT 관리자가 Intune 앱 보호 정책을 사용할 때 발생할 수 있는 일반적인 문제입니다.

| 문제 | 설명 | 해결 방법 |
| -- | -- | -- |
| 정책이 비즈니스용 Skype에 적용되지 않음 | Azure Portal에서 만든 디바이스 등록을 포함하지 않는 앱 보호 정책이 iOS/iPadOS 및 Android 디바이스의 비즈니스용 Skype 앱에 적용되지 않습니다. | 최신 인증을 사용하도록 비즈니스용 Skype를 설정해야 합니다.  [Enable your tenant for modern authentication](https://social.technet.microsoft.com/wiki/contents/articles/34339.skype-for-business-online-enable-your-tenant-for-modern-authentication.aspx)(최신 인증을 사용하도록 테넌트 설정)의 지침을 따라 Skype에 최신 인증을 설정합니다. |
| Office 앱 정책이 적용되지 않음 | 모든 사용자에 대해 [지원되는 Office 앱](https://www.microsoft.com/cloud-platform/microsoft-intune-partners)에 앱 보호 정책이 적용되지 않습니다. | 사용자가 Intune용 라이선스를 취득했으며, Office 앱이 배포된 앱 보호 정책의 대상인지 확인합니다. 새로 배포된 앱 보호 정책이 적용되려면 최대 8시간이 걸릴 수 있습니다. |
| 관리자가 Azure Portal에서 앱 보호 정책을 구성할 수 없음 | IT 관리자가 Azure Portal에서 앱 보호 정책을 구성할 수 없습니다. | Azure Portal에 액세스할 수 있는 사용자 역할은 다음과 같습니다. <ul><li>[Microsoft 365 관리 센터](https://admin.microsoft.com/)에서 설정할 수 있는 전역 관리자</li><li>소유자 - [Azure Portal](https://portal.azure.com/)에서 설정할 수 있습니다.</li><li>참가자 - [Azure Portal](https://portal.azure.com/)에서 설정할 수 있습니다.</li></ul> 이러한 역할 설정에 대한 도움말은 [Microsoft Intune에서 RBAC(역할 기반 관리 제어)](../fundamentals/role-based-access-control.md)를 참조하세요.|
|사용자 계정이 앱 보호 정책 보고서에서 누락됨 | 앱 보호 정책을 최근 배포한 사용자 계정이 관리 콘솔 보고서에 표시되지 않습니다. | 사용자가 앱 보호 정책 대상으로 새로 지정된 경우 대상 사용자로 보고서에 표시되는 데 최대 24시간이 걸릴 수 있습니다. |
| 정책 변경이 적용되지 않음 | 앱 보호 정책에 대한 변경 및 업데이트가 적용되는 데 최대 8시간이 걸릴 수 있습니다. | 해당하는 경우 서비스와 강제로 동기화하도록 최종 사용자가 앱에서 로그아웃했다가 다시 로그인하면 됩니다. |
| 앱 보호 정책이 DEP에서 작동되지 않음 | 앱 보호 정책이 Apple DEP 디바이스에 적용되지 않습니다. | Apple DEP(디바이스 등록 프로그램)에서 사용자 선호도를 사용 중인지 확인합니다. 사용자 선호도는 DEP에 따라 사용자 인증이 필요한 모든 앱에 필수입니다. <br><br>iOS/iPadOS DEP 등록에 대한 자세한 내용은 [Apple 디바이스 등록 프로그램을 통해 자동으로 iOS/iPadOS 디바이스 등록](../enrollment/device-enrollment-program-enroll-ios.md)을 참조하세요.|
| 데이터 전송 정책이 iOS/iPadOS에서 작동되지 않음 | **앱에서 다른 앱으로 데이터를 전송할 수 있도록 허용** 및 **앱에서 다른 앱의 데이터를 받을 수 있도록 허용** 정책이 iOS/iPadOS에서 데이터 전송을 제대로 관리하지 않습니다. | [Microsoft Intune에서 iOS/iPadOS 앱 간의 데이터 전송 관리 방법](data-transfer-between-apps-manage-ios.md)을 참조하세요. |

## <a name="common-end-user-issues"></a>최종 사용자에게 일반적으로 발생하는 문제

최종 사용자에게 일반적으로 발생하는 문제는 다음과 같은 범주로 세분화됩니다.

* **일반적인 사용 시나리오**: 최종 사용자가 Intune 앱 보호 정책을 포함하는 앱에서 이러한 시나리오를 경험할 수 있습니다. 이는 실제 문제는 아니지만, 버그 또는 오류로 간주될 수 있습니다.

* **일반적인 사용법 대화 상자**: Intune 앱 보호 정책을 포함하는 앱에서 최종 사용자에게 표시될 수 있는 사용법 대화 상자입니다. 이러한 메시지 및 대화 상자는 오류 또는 버그를 나타내지 **않습니다**.

* **오류 메시지 및 대화 상자**: Intune 앱 보호 정책을 포함하는 앱에서 최종 사용자에게 표시될 수 있는 오류 메시지 및 대화 상자입니다. 이는 흔히 Intune 앱 보호와 함께 IT 관리자 또는 버그에 의해 오류가 발생했음을 나타냅니다.

### <a name="normal-usage-scenarios"></a>일반적인 사용 시나리오

플랫폼 | 시나리오 | 설명 |
---| --- | --- |
iOS | 데이터 전송 정책이 **관리되는 앱만** 또는 **앱 없음**으로 설정된 경우에도 최종 사용자가 iOS/iPadOS 공유 확장을 사용하여 관리되지 않는 앱에서 회사 또는 학교 데이터를 열 수 있습니다. 이러면 데이터가 유출되지 않나요? | Intune 앱 보호 정책은 디바이스를 관리하지 않고는 iOS/iPadOS 공유 확장을 제어할 수 없습니다. 따라서 **Intune은 "회사" 데이터를 앱 외부에서 공유하기 전에 먼저 암호화합니다**. 관리되는 앱 외부에서 "회사" 파일을 열려고 시도하여 이를 확인할 수 있습니다. 파일이 암호화되어야 하며, 관리되는 앱 외부에서 파일을 열 수 없어야 합니다.
iOS | 최종 사용자에게 **Microsoft Authenticator 앱을 설치하라는 메시지가 표시**되는 이유는 무엇인가요? | 이 앱은 앱 기반 조건부 액세스를 적용하는 경우에 필요합니다. [승인된 클라이언트 앱 필요](https://docs.microsoft.com/azure/active-directory/conditional-access/app-based-conditional-access)를 참조하세요.
Android | 디바이스 등록 없이 MAM 앱 보호를 사용하는 경우에도 최종 사용자가 **회사 포털 앱을 설치해야 하는** 이유는 무엇인가요?  | Android에서 많은 앱 보호 기능이 회사 포털 앱에 기본 제공됩니다. **회사 포털 앱이 항상 필요한 경우에도 디바이스 등록은 필요하지 않습니다**. 등록 없이 앱 보호 기능을 사용하려면 최종 사용자가 회사 포털 앱을 디바이스에 설치해야 합니다.
iOS/Android | Outlook 앱에서 이메일 초안에 앱 보호 정책이 적용되지 않습니다. | Outlook에서는 회사 및 개인 컨텍스트를 모두 지원하므로 이메일 초안에 MAM을 적용하지 않습니다.
iOS/Android | 앱 보호 정책이 WXP의 새 문서(Word, Excel, PowerPoint)에 적용되지 않습니다. | WXP는 회사 및 개인 컨텍스트를 모두 지원하므로 OneDrive와 같이 식별된 회사 위치에 저장될 때까지 새 문서에 MAM을 적용하지 않습니다.
iOS/Android | 정책을 사용하는 경우 앱이 로컬 스토리지에 다른 이름으로 저장을 허용하지 않습니다. | 이 설정에 대한 앱 동작은 앱 개발자에 의해 제어됩니다.
Android | Android에는 MAM으로 보호된 콘텐츠에 액세스할 수 있는 "기본" 앱의 제한이 iOS/iPadOS보다 더 많습니다. | Android는 개방형 플랫폼이며, 최종 사용자는 "기본" 앱 연결을 잠재적으로 안전하지 않은 앱으로 변경할 수 있습니다. 특정 앱을 제외하려면 [데이터 전송 정책 예외](app-protection-policies-exception.md)를 적용합니다.
Android | ‘다른 이름으로 저장’이 금지된 경우, AIP(Azure Information Protection)를 PDF로 저장할 수 있습니다. | PDF로 저장하는 경우 AIP는 ‘인쇄 사용 안 함’에 대한 MAM 정책을 적용합니다.
iOS | "작업이 허용되지 않음" 오류와 함께 Outlook 앱에서 PDF 첨부 파일이 열리지 않습니다. | 이 문제는 사용자가 Intune용 Acrobat Reader를 인증하지 않았거나 지문을 사용하여 조직을 인증한 경우에 발생할 수 있습니다. 미리 Acrobat Reader를 열고 UPN 자격 증명을 사용하여 인증합니다.


### <a name="normal-usage-dialogs"></a>일반적인 사용법 대화 상자

플랫폼 | 메시지 또는 대화 상자 | 설명 |
--- | --- | --- |
iOS, Android | **로그인**: 조직 데이터를 보호하려면 이 앱을 관리해야 합니다. 이 작업을 완료하려면 회사 또는 학교 계정으로 로그인하세요. | 최종 사용자가 이 앱을 사용하려면 회사 또는 학교 계정을 사용하여 로그인해야 하며, 이는 앱 보호 정책이 필요합니다. 정책이 적용되려면 사용자가 Azure Active Directory에 대해 인증해야 합니다.
iOS, Android |**다시 시작 필요**: 조직이 이제 이 앱에서 조직 데이터를 보호합니다. 계속하려면 앱을 다시 시작해야 합니다. | 앱이 방금 Intune 앱 보호 정책을 받았으므로 정책이 적용되려면 다시 시작해야 합니다.
iOS, Android |**작업이 허용되지 않음**: 조직에서는 이 앱에서 회사 또는 학교 데이터를 여는 작업만 허용합니다. | IT 관리자가 **앱에서 다른 앱의 데이터를 받을 수 있도록 허용**을 **관리되는 앱만**으로 설정했습니다. 따라서 최종 사용자는 앱 보호 정책이 있는 다른 앱에서만 이 앱으로 데이터를 전송할 수 있습니다.
iOS, Android |**작업이 허용되지 않음**: 조직에서는 다른 관리되는 앱으로 데이터를 전송하는 작업만 허용합니다. | IT 관리자가 **앱에서 다른 앱으로 데이터를 전송할 수 있도록 허용**을 **관리되는 앱만**으로 설정했습니다. 따라서 최종 사용자는 이 앱의 데이터를 앱 보호 정책이 있는 다른 앱으로만 전송할 수 있습니다.
iOS, Android |**초기화 경고**: 조직에서 이 앱에 연결된 데이터를 제거했습니다. 계속하려면 앱을 다시 시작해야 합니다. | IT 관리자가 Intune 앱 보호를 사용하여 앱 초기화를 시작했습니다.
Android | **회사 포털 필요**: 이 앱에서 회사 또는 학교 계정을 사용하려면 Intune 회사 포털 앱을 설치해야 합니다. 계속하려면 “스토어로 이동”을 클릭합니다. | Android에서 많은 앱 보호 기능이 회사 포털 앱에 기본 제공됩니다. **회사 포털 앱이 항상 필요한 경우에도 디바이스 등록은 필요하지 않습니다**. 등록 없이 앱 보호 기능을 사용하려면 최종 사용자가 회사 포털 앱을 디바이스에 설치해야 합니다.

### <a name="error-messages-and-dialogs-on-ios"></a>iOS에서 오류 메시지 및 대화 상자

오류 메시지 또는 대화 상자 | 원인 | 수정 |
-- | --- | --- |
**앱이 설정되지 않음**: 이 앱을 사용자가 사용하도록 설정되지 않았습니다. 도움이 필요하면 IT 관리자에게 문의하세요. | 앱의 필수 앱 보호 정책을 검색하지 못했습니다. |iOS 앱 보호 정책이 사용자의 보안 그룹에 배포되어 있으며 이 앱을 대상으로 하는지 확인합니다.
**Intune Managed Browser 시작**: 이 앱은 Microsoft Intune에서 관리하는 경우에 가장 잘 작동합니다. 언제든지 이 앱을 사용하여 웹 검색을 할 수 있으며 Microsoft Intune으로 앱을 관리하는 경우 추가 데이터 보호 기능에 액세스할 수 있습니다. | Intune Managed Browser 앱의 필수 앱 보호 정책을 검색하지 못했습니다. <br><br>사용자는 계속 앱을 사용하여 웹을 검색할 수는 있지만 앱은 Intune을 통해 관리되지 않습니다. | iOS 앱 보호 정책이 사용자의 보안 그룹에 배포되어 있으며 Intune Managed Browser 앱을 대상으로 하는지 확인합니다.
**로그인 실패**: 지금은 로그인할 수 없습니다. 나중에 다시 시도하십시오. | 사용자가 회사 또는 학교 계정으로 로그인을 시도한 후 MAM 서비스에 사용자를 등록하지 못했습니다. | iOS 앱 보호 정책이 사용자의 보안 그룹에 배포되어 있으며 이 앱을 대상으로 하는지 확인합니다.
**계정이 설정되지 않음**: 조직에서 회사 또는 학교 데이터에 액세스하기 위한 계정을 설정하지 않았습니다. 도움이 필요하면 IT 관리자에게 문의하세요. | 사용자 계정에 Intune A 다이렉트 라이선스가 없습니다. | [Microsoft 365 관리 센터](https://admin.microsoft.com)에서 사용자의 계정에 Intune 라이선스가 할당되어 있는지 확인합니다.
**규정을 준수하지 않는 디바이스**: 탈옥한 디바이스를 사용 중이므로 이 앱을 사용할 수 없습니다. 도움이 필요하면 IT 관리자에게 문의하세요. | Intune에서 사용자가 탈옥한 디바이스를 사용 중임을 검색했습니다. | 디바이스를 기본 초기 설정으로 다시 설정합니다. Apple 지원 사이트의 [지침](https://support.apple.com/HT201274)을 따르세요.
**인터넷 연결 필요**: 이 앱을 사용할 수 있는지 확인하려면 인터넷에 연결되어 있어야 합니다. | 디바이스가 인터넷에 연결되어 있지 않습니다. | Wi-Fi 또는 데이터 네트워크에 디바이스를 연결합니다.
**알 수 없는 오류**: 이 앱을 다시 시작해 보세요. 문제가 계속될 경우 IT 관리자에게 문의하세요. | 알 수 없는 오류가 발생했습니다. | 잠시 기다린 후 다시 시도하세요. 오류가 계속되면 Intune [지원 티켓](../fundamentals/get-support.md#create-an-online-support-ticket)을 작성합니다.
**조직 데이터에 액세스**: 지정한 회사 또는 학교 계정은 이 앱에 액세스할 수 없습니다. 다른 계정으로 로그인해야 할 수 있습니다. 도움이 필요하면 IT 관리자에게 문의하세요. | Intune에서 사용자가 디바이스용으로 MAM에 등록된 계정이 아닌 두 번째 회사 또는 학교 계정으로 로그인을 시도했음을 발견했습니다. 디바이스당 한 번에 하나의 회사 또는 학교 계정만 MAM을 통해 관리할 수 있습니다. | 사용자가 로그인 화면에 사용자 이름이 미리 입력되어 있는 계정으로 로그인하도록 합니다. [Intune에 대한 사용자 UPN 설정을 구성](data-transfer-between-apps-manage-ios.md#configure-user-upn-setting-for-microsoft-intune-or-third-party-emm)해야 할 수 있습니다. <br> <br> 아니면 새 회사 또는 학교 계정으로 로그인하고 MAM에 등록된 기존 계정은 제거하도록 합니다.
**연결 문제**: 예기치 않은 연결 문제가 발생했습니다. 연결을 확인하고 다시 시도하세요.  |  예기치 않은 오류가 발생했습니다. | 잠시 기다린 후 다시 시도하세요. 오류가 계속되면 Intune [지원 티켓](../fundamentals/get-support.md#create-an-online-support-ticket)을 작성합니다.
**경고**: 이 앱은 더 이상 사용할 수 없습니다. 자세한 내용은 IT 관리자에게 문의하십시오. | 앱의 인증서 유효성을 검사하지 못했습니다. | 앱이 최신 버전인지 확인합니다. <br><br> 앱을 다시 설치합니다.
**오류**: 이 앱은 문제가 발생하여 닫아야 합니다. 이 오류가 계속되면 IT 관리자에게 문의하세요. | Apple iOS 키 집합에서 MAM 앱 PIN을 읽지 못했습니다. | 디바이스를 다시 시작합니다. 앱이 최신 버전인지 확인합니다. <br><br> 앱을 다시 설치합니다.

### <a name="error-messages-and-dialogs-on-android"></a>Android에서 오류 메시지 및 대화 상자

대화 상자/오류 메시지 | 원인 | 수정 |
-- | --- | --- |
**앱이 설정되지 않음**: 이 앱을 사용자가 사용하도록 설정되지 않았습니다. 도움이 필요하면 IT 관리자에게 문의하세요. | 앱의 필수 앱 보호 정책을 검색하지 못했습니다. |Android 앱 보호 정책이 사용자의 보안 그룹에 배포되어 있으며 이 앱을 대상으로 하는지 확인합니다.
**앱 시작 실패**: 앱을 시작하는 중 문제가 발생했습니다. 앱 또는 Intune 회사 포털 앱을 업데이트해 보세요. 도움이 필요하면 IT 관리자에게 문의하세요. | Intune에서 앱에 대해 유효한 앱 보호 정책을 검색했는데 MAM 초기화 중에 앱 작동이 중단됩니다. | 앱이 최신 버전인지 확인합니다. <br><br> Intune 회사 포털 앱이 디바이스에 설치되어 있으며 최신 상태인지 확인합니다. <br><br> 오류가 계속되면 회사 포털 앱을 사용하여 Intune에 로그를 보내거나 [지원 티켓](../fundamentals/get-support.md#create-an-online-support-ticket)을 작성합니다.
**앱을 찾을 수 없음**: 조직에서 이 콘텐츠를 열 수 있도록 허용한 앱이 이 디바이스에 없습니다. 도움이 필요하면 IT 관리자에게 문의하세요. | 사용자가 다른 앱에서 회사 또는 학교 데이터를 열려고 했는데 Intune이 데이터를 열도록 허용된 다른 관리되는 앱을 찾을 수 없습니다. | Android 앱 보호 정책이 사용자의 보안 그룹에 배포되어 있고, 해당하는 데이터를 열 수 있는 하나 이상의 다른 MAM 지원 앱을 대상으로 하는지 확인합니다.
**로그인 실패**: 다시 로그인해 보세요. 문제가 계속되면 IT 관리자에게 문의하세요. | 사용자가 로그인하는 데 사용한 계정을 인증하지 못했습니다. | 사용자가 Intune MAM 서비스에 이미 등록되어 있는 회사 또는 학교 계정(이 앱에 정상적으로 로그인하는 데 사용했던 첫 번째 회사 또는 학교 계정)을 사용하여 로그인하는지 확인합니다. <br><br> 앱의 데이터를 지웁니다. <br><br> 앱이 최신 버전인지 확인합니다. <br><br> 회사 포털이 최신 버전인지 확인합니다.
**인터넷 연결 필요**: 이 앱을 사용할 수 있는지 확인하려면 인터넷에 연결되어 있어야 합니다. | 디바이스가 인터넷에 연결되어 있지 않습니다. | Wi-Fi 또는 데이터 네트워크에 디바이스를 연결합니다.
**규정을 준수하지 않는 디바이스**: 루팅된 디바이스를 사용하고 있으므로 이 앱을 사용할 수 없습니다. 도움이 필요하면 IT 관리자에게 문의하세요. | Intune에서 사용자가 루팅된 디바이스를 사용 중임을 검색했습니다. | 디바이스를 기본 초기 설정으로 다시 설정합니다.
**계정이 설정되지 않음**: 이 앱은 Microsoft Intune에서 관리해야 하지만 계정이 설정되지 않았습니다. 도움이 필요하면 IT 관리자에게 문의하세요. | 사용자 계정에 Intune A 다이렉트 라이선스가 없습니다. | [Microsoft 365 관리 센터](https://admin.microsoft.com)에서 사용자의 계정에 Intune 라이선스가 할당되어 있는지 확인합니다.
**앱을 등록할 수 없음**: 이 앱은 Microsoft Intune에서 관리해야 하지만 지금은 이 앱을 등록할 수 없습니다. 도움이 필요하면 IT 관리자에게 문의하세요. | 앱 보호 정책이 필요한데 앱을 MAM 서비스에 자동으로 등록하지 못했습니다. | 앱의 데이터를 지웁니다. <br><br> 회사 포털 앱을 통해 Intune에 로그를 보내거나 지원 티켓을 등록합니다. 자세한 내용은 [Microsoft Intune에 대한 지원을 받는 방법](../fundamentals/get-support.md)을 참조하세요.

## <a name="next-steps"></a>다음 단계

- [모바일 애플리케이션 관리 설정 유효성 검사](app-protection-policies-validate.md)
- 로그 파일을 사용하여 Intune 앱 보호 정책의 문제를 해결하는 방법에 대한 자세한 내용은 [https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Support-Tip-Troubleshooting-Intune-app-protection-policy-using/ba-p/330372](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Support-Tip-Troubleshooting-Intune-app-protection-policy-using/ba-p/330372)를 참조하세요.
- 추가 Intune 문제 해결 정보는 [문제 해결 포털을 사용하여 회사 내 사용자 지원](../fundamentals/help-desk-operators.md)을 참조하세요. 
- 알려진 Microsoft Intune 문제를 알아봅니다. 자세한 내용은 [알려진 Microsoft Intune 문제](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/bg-p/IntuneCustomerSuccess)를 참조하세요.
- 추가 도움이 필요하십니까? [Microsoft Intune에 대한 지원을 받는 방법](../fundamentals/get-support.md)을 참조하십시오.
