---
title: Active Directory용 Intune Connector의 프록시 설정 구성
description: 기존 온-프레미스 프록시 서버와 함께 작동하도록 Active Directory용 Intune Connector를 구성하는 방법을 설명합니다.
keywords: ''
author: master11218
ms.author: erikje
manager: dougeby
ms.date: 4/16/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: tanvira
ms.suite: ems
search.appverid: ''
ms.custom: ''
ms.collection: M365-identity-device-management
ms.openlocfilehash: 227ed78b593ce10d47b9a1cdcc14dfbd58acdd93
ms.sourcegitcommit: 3d895be2844bda2177c2c85dc2f09612a1be5490
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79339516"
---
# <a name="work-with-existing-on-premises-proxy-servers"></a>기존 온-프레미스 프록시 서버 작업

이 문서에서는 아웃바운드 프록시 서버와 함께 작동하도록 Active Directory용 Intune Connector를 구성하는 방법을 설명합니다. 이 문서는 네트워크 환경에 기존 프록시가 있는 고객을 위해 작성되었습니다.

기본적으로 Active Directory용 Intune Connector는 WPAD(웹 프록시 자동 검색)를 사용하여 네트워크에서 프록시 서버를 자동으로 찾습니다. 네트워크에 이 기능이 구성되어 있는 경우 추가 구성이 필요하지 않을 수 있습니다.  변경이 필요한 경우 다음 섹션에서 [프록시 설정을 구성하기 위한 표준 .NET Framework 기능](https://docs.microsoft.com/dotnet/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings)을 활용하여 기본 설정을 재정의하는 방법을 설명합니다.  추가 옵션은 해당 설명서에 설명되어 있습니다.

커넥터의 작동 방식에 대한 자세한 내용은 [Azure AD 애플리케이션 프록시 커넥터의 이해](https://docs.microsoft.com/azure/active-directory/manage-apps/application-proxy-connectors)를 참조하세요.

## <a name="completely-bypass-outbound-proxies"></a>아웃바운드 프록시를 완전히 바이패스

온-프레미스 프록시를 바이패스하여 Azure 서비스에 직접 연결하도록 커넥터를 구성할 수 있습니다. 네트워크 정책에서 허용한다면 이 방법을 사용하는 것이 좋습니다. 유지 관리할 구성이 하나 줄어들기 때문입니다.

커넥터에 아웃바운드 프록시를 사용하지 않도록 설정하려면 이 코드 샘플에 표시된 섹션의 :\Program Files\Microsoft Intune\ODJConnector\ODJConnectorUI\ODJConnectorUI.exe.config 파일을 편집하고 프록시 주소 및 프록시 포트를 추가합니다.

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
    <system.net>  
        <defaultProxy>   
            <defaultProxy enabled="False" /> 
        </defaultProxy>  
    </system.net>
    <runtime>
        <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
            <dependentAssembly>
                <assemblyIdentity name="mscorlib" publicKeyToken="b77a5c561934e089" culture="neutral"/>
                <bindingRedirect oldVersion="0.0.0.0-2.0.0.0" newVersion="4.6.0.0" />
            </dependentAssembly>
        </assemblyBinding>
    </runtime>
    <startup> 
        <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.6" />
    </startup>
    <appSettings>
        <add key="SignInURL" value="https://portal.manage.microsoft.com/Home/ClientLogon"/>
        <add key="LocationServiceEndpoint" value="RestUserAuthLocationService/RestUserAuthLocationService/ServiceAddresses"/>
    </appSettings>
</configuration>
```

Connector Updater 서비스도 프록시를 바이패스하게 하려면 C:\Program Files\Microsoft Intune\ODJConnector\ODJConnectorSvc\ODJConnectorSvc.exe.config 파일을 비슷하게 변경합니다.

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
    <system.net>  
        <defaultProxy>
            <defaultProxy enabled="False" /> 
        </defaultProxy>  
    </system.net>
    <startup>
        <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.6" />
    </startup>
    <appSettings>
        <add key="BaseServiceAddress" value="https://manage.microsoft.com/" />
    </appSettings>
</configuration>
```

기본 .config 파일로 되돌려야 할 경우를 대비하여 원래 파일의 복사본을 만들어 두어야 합니다.

구성 파일을 수정한 후에는 Intune Connector 서비스를 다시 시작해야 합니다. 

1. **services.msc**를 엽니다.
2. **Intune ODJConnector 서비스**를 찾아서 선택합니다.
3. **다시 시작**을 선택합니다.

![서비스 다시 시작의 스크린샷](./media/autopilot-hybrid-connector-proxy/service-restart.png)


## <a name="specifying-an-alternative-proxy-server"></a>대체 프록시 서버 지정

다른 프록시 서버(예: 인증을 우회하는 서버)를 Active Directory용 Intune Connector와 함께 사용해야 하는 경우 비슷한 방식으로 지정할 수 있습니다. 이렇게 하려면 이 코드 샘플에 표시된 섹션의 :\Program Files\Microsoft Intune\ODJConnector\ODJConnectorUI\ODJConnectorUI.exe.config 파일을 편집하고 프록시 주소 및 프록시 포트를 추가합니다.

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
    <system.net>  
        <defaultProxy>   
            <proxy proxyaddress="<PROXY ADDRESS HERE>:<PORT HERE>" bypassonlocal="True" usesystemdefault="True"/>   
        </defaultProxy>  
    </system.net>
    <runtime>
        <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
            <dependentAssembly>
                <assemblyIdentity name="mscorlib" publicKeyToken="b77a5c561934e089" culture="neutral"/>
                <bindingRedirect oldVersion="0.0.0.0-2.0.0.0" newVersion="4.6.0.0" />
            </dependentAssembly>
        </assemblyBinding>
    </runtime>
    <startup> 
        <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.6" />
    </startup>
    <appSettings>
        <add key="SignInURL" value="https://portal.manage.microsoft.com/Home/ClientLogon"/>
        <add key="LocationServiceEndpoint" value="RestUserAuthLocationService/RestUserAuthLocationService/ServiceAddresses"/>
    </appSettings>
</configuration>
```

Connector Updater 서비스도 프록시를 바이패스하게 하려면 C:\Program Files\Microsoft Intune\ODJConnector\ODJConnectorSvc\ODJConnectorSvc.exe.config 파일을 비슷하게 변경합니다.

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
    <system.net>  
        <defaultProxy>   
            <proxy proxyaddress="<PROXY ADDRESS HERE>:<PORT HERE>" bypassonlocal="True" usesystemdefault="True"/>   
        </defaultProxy>  
    </system.net>
    <startup>
        <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.6" />
    </startup>
    <appSettings>
        <add key="BaseServiceAddress" value="https://manage.microsoft.com/" />
    </appSettings>
</configuration>
```

기본 .config 파일로 되돌려야 할 경우를 대비하여 원래 파일의 복사본을 만들어 두어야 합니다.

구성 파일을 수정한 후에는 Intune Connector 서비스를 다시 시작해야 합니다. 

1. **services.msc**를 엽니다.
2. **Intune ODJConnector 서비스**를 찾아서 선택합니다.
3. **다시 시작**을 선택합니다.

![서비스 다시 시작의 스크린샷](./media/autopilot-hybrid-connector-proxy/service-restart.png)


## <a name="next-steps"></a>다음 단계

[디바이스 관리](../remote-actions/device-management.md)
