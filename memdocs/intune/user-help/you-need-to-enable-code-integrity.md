---
title: 코드 무결성을 사용하도록 설정해야 함 | Microsoft 문서
description: ''
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 11/14/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.subservice: end-user
ms.technology: ''
ms.assetid: 84892bbc-f888-417b-bbeb-978cc7e10028
searchScope:
- User help
ROBOTS: ''
ms.reviewer: scottduf
ms.suite: ems
ms.custom: intune-enduser
ms.collection: ''
ms.openlocfilehash: b6fc5fbc3a657eeabd8771e02e20aa168987ea5e
ms.sourcegitcommit: 3d895be2844bda2177c2c85dc2f09612a1be5490
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79346445"
---
# <a name="enable-code-integrity"></a>코드 무결성 사용

조직이 PC에서 *코드 무결성*이라는 위협 방지 기능을 사용하도록 요구할 수 있습니다. 코드 무결성은 디바이스의 드라이버 및 시스템 파일에서 손상 또는 악성 소프트웨어의 징후를 확인합니다. 디바이스에서 코드 무결성이 작동하려면 [*보안 부팅*](https://docs.microsoft.com/windows/security/information-protection/secure-the-windows-10-boot-process#secure-boot)이라는 또 다른 보안 기능을 사용하도록 설정해야 합니다.

코드 무결성이 사용하지 않도록 설정되어 PC가 규정을 준수하지 않는 경우 조직의 IT 지원 담당자에게 문의하세요. 지원 담당자가 다음에 디바이스를 시작할 때 코드 무결성을 트리거하는 보안 부팅을 사용하도록 설정하는 과정을 도와줍니다. 

스스로 고급 디바이스 사용자라고 생각한다면 [보안 부팅을 다시 사용하도록 설정](https://docs.microsoft.com/windows-hardware/manufacture/desktop/disabling-secure-boot#re-enable-secure-boot)을 참조하여 해당 단계를 직접 시도할 수 있습니다.

## <a name="additional-resources-for-it-administrators"></a>IT 관리자를 위한 추가 리소스

Intune 관리자가 Intune의 디바이스 상태 준수 설정에 대한 자세한 내용을 알아보려면 [Intune에서 Windows 10 디바이스에 대한 디바이스 준수 정책 추가](https://docs.microsoft.com/intune/protect/compliance-policy-create-windows)를 참조하세요. Intune에서 수행할 수 있는 준수 작업을 자세히 알아보려면 [HealthAttestation CSP](https://docs.microsoft.com/windows/client-management/mdm/healthattestation-csp#step-8-take-appropriate-policy-action-based-on-evaluation-results)를 참조하세요.  

## <a name="next-steps"></a>다음 단계

여전히 도움이 필요하세요? 회사 지원 부서에 문의하세요. 연락처 정보는 [회사 포털 웹 사이트](https://go.microsoft.com/fwlink/?linkid=2010980)를 참조하세요.
