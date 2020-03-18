---
title: Microsoft Intune에서 SCEP와 함께 타사 CA(인증 기관) 사용 - Azure | Microsoft Docs
description: Microsoft Intune에서 공급업체 또는 타사 CA(인증 기관)를 추가하여 SCEP 프로토콜을 통해 모바일 디바이스에 인증서를 발급할 수 있습니다. 이 개요에서 Azure AD(Active Directory) 애플리케이션은 Microsoft Intune에 인증서 유효성 검사 권한을 부여합니다. 그런 다음, SCEP 서버 설정에서 AAD 애플리케이션의 애플리케이션 ID, 인증 키 및 테넌트 ID를 사용하여 인증서를 발급합니다.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 07/03/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 1dfac34615c208328cab06a3fd047d3a9b99c794
ms.sourcegitcommit: 3d895be2844bda2177c2c85dc2f09612a1be5490
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79353894"
---
# <a name="add-partner-certification-authority-in-intune-using-scep"></a>SCEP를 사용하여 Intune에 파트너 인증 기관 추가

Intune에서 타사 CA(인증 기관)를 사용합니다. 타사 CA는 SCEP(단순 인증서 등록 프로토콜)를 사용하여 새 인증서나 갱신된 인증서로 모바일 디바이스를 프로비저닝할 수 있고 Windows, iOS/iPadOS, Android 및 macOS 디바이스를 지원할 수 있습니다.

이 기능의 사용법은 오픈 소스 API와 Intune 관리자 작업이라는 두 가지 부분으로 나뉘어 있습니다.

**1부 - 오픈 소스 API 사용**  
Microsoft는 Intune과 통합하기 위한 API를 만들었습니다. API를 통해 인증서를 확인하고 성공 또는 실패 알림을 보내고 SSL 특히, SSL 소켓 팩터리를 사용하여 Intune과 통신할 수 있습니다.

API는 [Intune SCEP API 공개 GitHub 리포지토리](https://github.com/Microsoft/Intune-Resource-Access/tree/develop/src/CsrValidation)에서 다운로드하여 솔루션에서 사용할 수 있습니다. 타사 SCEP 서버에서 이 API를 사용하여 SCEP가 인증서를 디바이스에 프로비저닝하기 전에 Intune에 사용자 지정 인증 질문 유효성 검사를 실행합니다.

[Intune SCEP 관리 솔루션과 통합](scep-libraries-apis.md)에서는 API 사용, 메서드 및 빌드한 솔루션 테스트에 대한 자세한 정보를 제공합니다.

**2부 - 애플리케이션 및 프로필 만들기**  
Azure AD(Active Directory) 애플리케이션을 사용하면 Intune에 권한을 위임하여 디바이스에서 발생하는 SCEP 요청을 처리할 수 있습니다. Azure AD 애플리케이션은 개발자가 만든 API 솔루션 내에서 사용되는 애플리케이션 ID 및 인증 키 값을 포함합니다. 그러면 관리자는 Intune을 사용하여 SCEP 인증서 프로필을 만들고 배포하며 디바이스에서 배포 상태에 관한 보고서를 볼 수 있습니다.

이 문서에서는 관리자 관점에서 Azure AD 애플리케이션 생성 등을 살펴보며 이 기능에 대한 개요를 제공합니다.

## <a name="overview"></a>개요

다음 단계는 Intune에서 인증서에 SCEP를 사용하는 방법에 대한 개요를 제공합니다.

1. Intune에서 관리자는 SCEP 인증서 프로필을 만든 다음, 프로필 대상을 사용자 또는 디바이스로 지정합니다.
2. 디바이스가 Intune에 체크 인합니다.
3. Intune은 고유한 SCEP 인증 질문을 만듭니다. 또한 올바른 주체 및 SAN과 같은 추가 무결성 검사 정보를 추가합니다.
4. Intune은 인증 질문 및 무결성 검사 정보를 암호화하고 서명한 다음, SCEP 요청을 통해 디바이스에 이 정보를 보냅니다.
5. 디바이스는 Intune에서 푸시되는 SCEP 인증서 프로필을 기반으로 디바이스에 CSR(인증서 서명 요청) 및 퍼블릭/프라이빗 키 쌍을 생성합니다.
6. CSR 및 암호화/서명된 인증 질문이 타사 SCEP 서버 엔드포인트로 전송됩니다.
7. SCEP 서버는 CSR과 인증 질문을 Intune에 보냅니다. 그런 다음, Intune은 서명의 유효성을 검사하고 페이로드의 암호를 해독하며 CSR을 무결성 검사 정보와 비교합니다.
8. Intune은 SCEP 서버에 응답을 보내고 인증 질문 유효성 검사가 성공했는지 여부를 명시합니다.  
9. 인증 질문이 성공적으로 확인되면 SCEP 서버는 디바이스에 인증서를 발급합니다.

다음 다이어그램에서는 Intune과 타사 SCEP 통합의 자세한 흐름을 보여 줍니다.

> [!div class="mx-imgBorder"]
> ![타사 인증 기관 SCEP를 Microsoft Intune과 통합하는 방법](./media/certificate-authority-add-scep-overview/scep-certificate-vendor-integration.png)

## <a name="set-up-third-party-ca-integration"></a>타사 CA 통합 설정

### <a name="validate-third-party-certification-authority"></a>타사 인증 기관 유효성 검사

타사 인증 기관을 Intune과 통합하기 전에 사용 중인 CA가 Intune을 지원하는지 확인합니다. (이 문서에서) [타사 CA 파트너](#third-party-certification-authority-partners)는 목록을 포함합니다. 인증 기관의 지침에서 자세한 내용을 확인할 수도 있습니다. CA는 해당 구현과 관련된 설치 지침을 포함할 수 있습니다.

### <a name="authorize-communication-between-ca-and-intune"></a>CA와 Intune 간의 통신 승인

Intune을 사용하여 타사 SCEP 서버가 사용자 지정 인증 질문 유효성 검사를 실행할 수 있도록 Azure AD에 앱을 만듭니다. 이 앱은 Intune에 위임된 권한을 부여하여 SCEP 요청의 유효성을 검사합니다.

Azure AD 앱을 등록하는 데 필요한 권한이 있는지 확인합니다. Azure AD 설명서의 [필요한 사용 권한](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-create-service-principal-portal#required-permissions)을 참조하세요.

#### <a name="create-an-application-in-azure-active-directory"></a>Azure Active Directory에서 애플리케이션 만들기  

1. [Azure Portal](https://portal.azure.com)에서 **Azure Active Directory** > **앱 등록**으로 이동한 후 **새 등록**을 선택합니다.  

2. **애플리케이션 등록** 페이지에서 다음 세부 정보를 지정합니다.  
   - **이름** 섹션에서 의미 있는 애플리케이션 이름을 입력합니다.  
   - **지원되는 계정 유형** 섹션에서 **모든 조직 디렉터리의 계정**을 선택합니다.  
   - **리디렉션 URI**에서 기본값인 웹을 그대로 사용한 후 타사 SCEP 서버의 로그인 URL을 지정합니다.  

3. **등록**을 선택하여 애플리케이션을 만들고 새 앱의 개요 페이지를 엽니다.  

4. 앱 **개요** 페이지에서 **애플리케이션(클라이언트) ID** 값을 복사하고 나중에 사용할 수 있도록 기록합니다. 나중에 이 값이 필요합니다.  

5. 앱 탐색 창에서 **관리** 아래에 있는 **인증서 및 비밀**로 이동합니다. **새 클라이언트 암호** 단추를 선택합니다. [설명]에 값을 입력하고, **만료** 옵션을 선택한 후, **추가**를 선택하여 클라이언트 암호 ‘값’을 생성합니다.  
   > [!IMPORTANT]  
   > 이 페이지를 나가기 전에 클라이언트 암호 값을 복사하고 나중에 타사 CA 구현에서 사용할 수 있도록 기록합니다. 이 값은 다시 표시되지 않습니다. 애플리케이션 ID, 인증 키 및 테넌트 ID를 구성하는 방법에 대한 타사 CA 지침을 검토해야 합니다.  

6. **테넌트 ID**를 기록합니다. 테넌트 ID는 계정의 @ 기호 다음에 오는 도메인 텍스트입니다. 예를 들어 계정이 *admin@name.onmicrosoft.com* 이면 테넌트 ID는 **name.onmicrosoft.com**입니다.  

7. 앱 탐색 창에서 **관리** 아래에 있는 **API 사용 권한**으로 이동한 후 **권한 추가**를 선택합니다.  

8. **API 사용 권한 요청** 페이지에서 **Intune**을 선택한 후 **애플리케이션 권한**을 선택합니다. **scep_challenge_provider**(SCEP 챌린지 유효성 검사) 확인란을 선택합니다.  

   **권한 추가**를 선택하여 이 구성을 저장합니다.  

9. **API 사용 권한** 페이지에서 **Microsoft에 대한 관리자 동의 허용**을 선택한 후 **예**를 선택합니다.  
   
   Azure AD에서 앱 등록 프로세스가 완료되었습니다.





### <a name="configure-and-deploy-a-scep-certificate-profile"></a>SCEP 인증서 프로필 구성 및 배포
관리자는 사용자 또는 디바이스를 대상으로 SCEP 인증서 프로필을 만듭니다. 그런 다음, 프로필을 할당합니다.

- [SCEP 인증서 프로필 만들기](certificates-profile-scep.md#create-a-scep-certificate-profile)

- [인증서 프로필 할당](certificates-profile-scep.md#assign-the-certificate-profile)

## <a name="removing-certificates"></a>인증서 제거

디바이스의 등록을 취소하거나 초기화할 때 인증서가 제거됩니다. 인증서는 해지되지 않습니다.

## <a name="third-party-certification-authority-partners"></a>타사 인증 기관 파트너
다음 타사 인증 기관은 Intune을 지원합니다.

- [Entrust Datacard](https://go.entrustdatacard.com/pki/intune/)
- [EJBCA GitHub 오픈 소스 버전](https://github.com/agerbergt/intune-ejbca-connector)
- [EverTrust](https://evertrust.fr/en/products/)
- [GlobalSign](https://downloads.globalsign.com/acton/attachment/2674/f-6903f60b-9111-432d-b283-77823cc65500/1/-/-/-/-/globalsign-aeg-microsoft-intune-integration-guide.pdf)
- [IDnomic](https://www.idnomic.com/)
- [Sectigo](https://sectigo.com/products)
- [DigiCert](https://knowledge.digicert.com/tutorials/microsoft-intune.html)
- [Venafi](https://www.venafi.com/platform/enterprise-mobility)
- [SCEPman](https://azuremarketplace.microsoft.com/marketplace/apps/gluckkanja.scepman)

Intune과 제품을 통합하는 데 관심이 있는 타사 CA인 경우 API 지침을 검토합니다.

- [Intune SCEP API GitHub 리포지토리](https://github.com/Microsoft/Intune-Resource-Access/tree/develop/src/CsrValidation)
- [타사 CA에 대한 Intune SCEP API 지침](scep-libraries-apis.md)

## <a name="see-also"></a>참고 항목

- [인증서 프로필 구성](certificates-scep-configure.md)
- [Intune SCEP API GitHub 리포지토리](https://github.com/Microsoft/Intune-Resource-Access/tree/develop/src/CsrValidation)
- [타사 CA에 대한 Intune SCEP API 지침](scep-libraries-apis.md)
