---
title: "Windows 인증에 대한 데이터베이스 미러링 끝점 만들기(Transact-SQL) | Microsoft Docs"
ms.custom: ""
ms.date: "05/17/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-high-availability"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "데이터베이스 미러링 [SQL Server], 배포"
  - "데이터베이스 미러링 [SQL Server], 끝점"
  - "끝점 [SQL Server], 데이터베이스 미러링"
  - "Windows 인증 [SQL Server]"
  - "데이터베이스 미러링 [SQL Server], 보안"
ms.assetid: baf1a4b1-6790-4275-b261-490bca33bdb9
caps.latest.revision: 61
author: "MikeRayMSFT"
ms.author: "mikeray"
manager: "jhubbard"
caps.handback.revision: 61
---
# Windows 인증에 대한 데이터베이스 미러링 끝점 만들기(Transact-SQL)
  이 항목에서는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 을 사용하여 [!INCLUDE[tsql](../../includes/tsql-md.md)]에서 Windows 인증을 사용하는 데이터베이스 미러링 끝점을 만드는 방법에 대해 설명합니다. 데이터베이스 미러링 또는 [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] 을 지원하려면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 의 각 인스턴스에 데이터베이스 미러링 끝점이 필요합니다. 서버 인스턴스는 하나의 포트가 있는 데이터베이스 미러링 끝점을 하나만 가질 수 있습니다. 데이터베이스 미러링 끝점은 끝점이 생성될 때 로컬 시스템에서 사용 가능한 모든 포트를 사용할 수 있습니다. 서버 인스턴스의 모든 데이터베이스 미러링 세션이 이 포트에서 수신하고 데이터베이스 미러링에 대해 들어오는 모든 연결에 이 포트가 사용됩니다.  
  
> [!IMPORTANT]  
>  데이터베이스 미러링 끝점이 있고 이미 사용 중인 경우 해당 끝점을 사용하는 것이 좋습니다. 사용 중인 끝점을 삭제하면 기존 세션이 중단됩니다.  
  
 **항목 내용**  
  
-   **시작하기 전 주의 사항:**  [보안](#Security)  
  
-   **데이터베이스 미러링 끝점을 만들려면:** [Transact-SQL](#TsqlProcedure) 사용  
  
##  <a name="BeforeYouBegin"></a> 시작하기 전에  
  
###  <a name="Security"></a> 보안  
 서버 인스턴스의 인증 및 암호화 방법은 시스템 관리자가 설정합니다.  
  
> [!IMPORTANT]  
>  RC4 알고리즘은 더 이상 사용되지 않습니다. [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] AES를 사용하는 것이 좋습니다.  
  
####  <a name="Permissions"></a> 사용 권한  
 CREATE ENDPOINT 권한 또는 sysadmin 고정 서버 역할의 멤버 자격이 필요합니다. 자세한 내용은 [GRANT 끝점 사용 권한&#40;Transact-SQL&#41;](../../t-sql/statements/grant-endpoint-permissions-transact-sql.md)을 참조하세요.  
  
##  <a name="TsqlProcedure"></a> Transact-SQL 사용  
  
#### Windows 인증을 사용하는 데이터베이스 미러링 끝점을 만들려면  
  
1.  데이터베이스 미러링 끝점을 만들 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스에 연결합니다.  
  
2.  표준 도구 모음에서 **새 쿼리**를 클릭합니다.  
  
3.  다음 문을 사용하여 데이터베이스 미러링 끝점이 이미 존재하는지 확인합니다.  
  
    ```  
    SELECT name, role_desc, state_desc FROM sys.database_mirroring_endpoints;   
    ```  
  
    > [!IMPORTANT]  
    >  서버 인스턴스에 대한 데이터베이스 미러링 끝점이 이미 존재하는 경우 서버 인스턴스에서 설정한 다른 세션에 대한 끝점을 사용하세요.  
  
4.  Transact-SQL로 Windows 인증을 사용하는 끝점을 만들려면 CREATE ENDPOINT 문을 사용합니다. 이 문은 일반적으로 다음과 같은 형식으로 되어 있습니다.  
  
     CREATE ENDPOINT *\<endpointName>*  
  
     STATE=STARTED  
  
     AS TCP ( LISTENER_PORT = *\<listenerPortList>* )  
  
     FOR DATABASE_MIRRORING  
  
     (  
  
     [ AUTHENTICATION = **WINDOWS** [ *\<authorizationMethod>* ]  
  
     ]  
  
     [ [**,**] ENCRYPTION = **REQUIRED**  
  
     [ ALGORITHM { *\<algorithm>* } ]  
  
     ]  
  
     [**,**] ROLE = *\<role>*  
  
     ).  
  
     여기서  
  
    -   *\<endpointName>*은 서버 인스턴스의 데이터베이스 미러링 끝점에 대한 고유 이름입니다.  
  
    -   STARTED는 끝점이 시작되어 연결에 대한 수신을 시작하도록 지정합니다. 데이터베이스 미러링 끝점은 일반적으로 STARTED 상태로 생성됩니다. STOPPED 상태(기본값)나 DISABLED 상태로 세션을 시작할 수도 있습니다.  
  
    -   *\<listenerPortList>*는 서버에서 데이터베이스 미러링 메시지를 수신할 하나의 포트 번호(*nnnn*)입니다. TCP만 허용되기 때문에 다른 프로토콜을 지정하면 오류가 발생합니다.  
  
         하나의 포트 번호는 컴퓨터 시스템당 한 번만 사용할 수 있습니다. 데이터베이스 미러링 끝점은 끝점이 생성될 때 로컬 시스템에서 사용 가능한 모든 포트를 사용할 수 있습니다. 시스템의 TCP 끝점에서 현재 사용 중인 포트를 식별하려면 다음 Transact-SQL 문을 사용합니다.  
  
        ```  
        SELECT name, port FROM sys.tcp_endpoints;  
        ```  
  
        > [!IMPORTANT]  
        >  각 서버 인스턴스에는 하나의 고유 수신기 포트만 필요합니다.  
  
    -   끝점에서 연결을 인증하는 데 NTLM이나 Kerberos만을 사용하려는 경우가 아니라면 Windows 인증에서 AUTHENTICATION 옵션은 선택 사항입니다. *\<authorizationMethod>*는 연결 인증 방법을 NTLM, KERBEROS 또는 NEGOTIATE 중 하나로 지정합니다. 기본값인 NEGOTIATE를 적용하면 끝점이 Windows 협상 프로토콜을 사용하여 NTLM이나 Kerberos를 선택합니다. 협상을 사용하면 반대쪽 끝점의 인증 수준에 따라 인증을 사용하여 연결을 설정하거나 인증을 사용하지 않고 연결을 설정할 수 있습니다.  
  
    -   ENCRYPTION은 기본적으로 REQUIRED로 설정되어 있으며 이는 끝점에 대한 모든 연결에 암호화를 사용해야 함을 의미합니다. 그러나 다음과 같이 끝점에 대해 암호화를 해제하거나 선택적으로 사용할 수 있습니다. 대체 방법은 다음과 같습니다.  
  
        |값|정의|  
        |-----------|----------------|  
        |DISABLED|연결을 통해 전송되는 데이터를 암호화하지 않도록 지정합니다.|  
        |SUPPORTED|반대쪽 끝점이 SUPPORTED나 REQUIRED로 지정된 경우에만 데이터를 암호화하도록 지정합니다.|  
        |REQUIRED|연결을 통해 전송되는 데이터를 반드시 암호화하도록 지정합니다.|  
  
         한 끝점에 암호화가 필요한 경우 다른 끝점의 ENCRYPTION은 SUPPORTED나 REQUIRED로 설정해야 합니다.  
  
    -   *\<algorithm>*은 끝점의 암호화 표준을 지정하는 옵션을 제공합니다. *\<algorithm>* 값은 RC4, AES, AES RC4 또는 RC4 AES 중 하나이거나 이들 알고리즘의 조합일 수 있습니다.  
  
         AES RC4는 끝점이 AES 알고리즘에 우선 순위를 두어 암호화 알고리즘을 협상하도록 지정합니다. RC4 AES는 끝점이 RC4 알고리즘에 우선 순위를 두어 암호화 알고리즘을 협상하도록 지정합니다. 양쪽 끝점이 두 알고리즘을 모두 지정하지만 순서가 다른 경우 연결을 수락하는 끝점의 알고리즘이 적용됩니다.  
  
        > [!NOTE]  
        >  RC4 알고리즘은 더 이상 사용되지 않습니다. [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] AES를 사용하는 것이 좋습니다.  
  
    -   *\<role>*은 서버가 수행할 수 있는 역할을 정의합니다. ROLE은 반드시 지정해야 합니다. 그러나 끝점의 역할은 데이터베이스 미러링과만 관련이 있습니다. [!INCLUDE[ssHADR](../../includes/sshadr-md.md)]에 대해서는 끝점의 역할이 무시됩니다.  
  
         서버 인스턴스가 데이터베이스 미러링 세션에 따라 각기 다른 역할을 하도록 하려면 ROLE=ALL을 지정합니다. 서버 인스턴스가 파트너 또는 미러링 모니터 서버가 되도록 제한하려면 ROLE=PARTNER와 ROLE=WITNESS를 각각 지정합니다.  
  
        > [!NOTE]  
        >  다양한 버전의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서 제공하는 데이터베이스 미러링 옵션에 대한 자세한 내용은 [SQL Server 2016 버전에서 지원하는 기능](../Topic/Features%20Supported%20by%20the%20Editions%20of%20SQL%20Server%202016.md)을 참조하세요.  
  
     CREATE ENDPOINT 구문에 대한 자세한 내용은 [CREATE ENDPOINT&#40;Transact-SQL&#41;](../../t-sql/statements/create-endpoint-transact-sql.md)를 참조하세요.  
  
    > [!NOTE]  
    >  기존 끝점을 변경하려면 [ALTER ENDPOINT&#40;Transact-SQL&#41;](../../t-sql/statements/alter-endpoint-transact-sql.md)를 사용합니다.  
  
###  <a name="TsqlExample"></a> 예: 데이터베이스 미러링 지원을 위한 끝점 만들기(Transact-SQL)  
 다음 예에서는 세 대의 다른 컴퓨터 시스템에 있는 기본 서버 인스턴스에 대한 데이터베이스 미러링 끝점을 만듭니다.  
  
|서버 인스턴스의 역할|호스트 컴퓨터 이름|  
|-----------------------------|---------------------------|  
|파트너(처음에는 주 역할임)|`SQLHOST01\.`|  
|파트너(처음에는 미러 역할임)|`SQLHOST02\.`|  
|미러링 모니터|`SQLHOST03\.`|  
  
 이 예에서 세 끝점은 모든 사용 가능한 포트 번호를 사용할 수 있지만 모두 포트 번호 7022를 사용합니다. 세 끝점에서 기본 유형인 Windows 인증을 사용하므로 AUTHENTICATION 옵션이 필요하지 않습니다. 세 끝점은 모두 Windows 인증의 기본 동작에 따라 연결 인증 방법을 협상하도록 되어 있으므로 ENCRYPTION 옵션도 필요하지 않습니다. 또한 세 끝점에는 모두 기본 동작에 따라 암호화가 필요합니다.  
  
 각 서버 인스턴스는 파트너나 미러링 모니터 서버로 역할이 제한되며 각 서버의 끝점은 ROLE=PARTNER 또는 ROLE=WITNESS와 같이 해당 역할을 명시적으로 지정합니다.  
  
> [!IMPORTANT]  
>  각 서버 인스턴스는 끝점을 하나만 가질 수 있습니다. 따라서 서버 인스턴스가 세션에 따라 파트너 역할을 하거나 미러링 모니터 서버 역할을 하도록 하려면 ROLE=ALL을 지정하세요.  
  
```  
--Endpoint for initial principal server instance, which  
--is the only server instance running on SQLHOST01.  
CREATE ENDPOINT endpoint_mirroring  
    STATE = STARTED  
    AS TCP ( LISTENER_PORT = 7022 )  
    FOR DATABASE_MIRRORING (ROLE=PARTNER);  
GO  
--Endpoint for initial mirror server instance, which  
--is the only server instance running on SQLHOST02.  
CREATE ENDPOINT endpoint_mirroring  
    STATE = STARTED  
    AS TCP ( LISTENER_PORT = 7022 )  
    FOR DATABASE_MIRRORING (ROLE=PARTNER);  
GO  
--Endpoint for witness server instance, which  
--is the only server instance running on SQLHOST03.  
CREATE ENDPOINT endpoint_mirroring  
    STATE = STARTED  
    AS TCP ( LISTENER_PORT = 7022 )  
    FOR DATABASE_MIRRORING (ROLE=WITNESS);  
GO  
```  
  
##  <a name="RelatedTasks"></a> 관련 태스크  
 **데이터베이스 미러링 끝점을 구성하려면**  
  
-   [Always On 가용성 그룹에 대한 데이터베이스 미러링 끝점 만들기&#40;SQL Server PowerShell&#41;](../../database-engine/availability-groups/windows/database mirroring - always on availability groups- powershell.md)  
  
-   [데이터베이스 미러링 끝점에 대한 인증서 사용&#40;Transact-SQL&#41;](../../database-engine/database-mirroring/use-certificates-for-a-database-mirroring-endpoint-transact-sql.md)  
  
    -   [데이터베이스 미러링 끝점의 아웃바운드 연결에 대한 인증서 사용 허용&#40;Transact-SQL&#41;](../../database-engine/database-mirroring/database mirroring - use certificates for outbound connections.md)  
  
    -   [데이터베이스 미러링 끝점의 인바운드 연결에 대한 인증서 사용 허용&#40;Transact-SQL&#41;](../../database-engine/database-mirroring/database mirroring - use certificates for inbound connections.md)  
  
-   [서버 네트워크 주소 지정&#40;데이터베이스 미러링&#41;](../../database-engine/database-mirroring/specify-a-server-network-address-database-mirroring.md)  
  
-   [가용성 복제본 추가 또는 수정 시 끝점 URL 지정&#40;SQL Server&#41;](../../database-engine/availability-groups/windows/specify endpoint url - adding or modifying availability replica.md)  
  
 **데이터베이스 미러링 끝점에 대한 정보를 보려면**  
  
-   [sys.database_mirroring_endpoints&#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-mirroring-endpoints-transact-sql.md)  
  
## 참고 항목  
 [ALTER ENDPOINT&#40;Transact-SQL&#41;](../../t-sql/statements/alter-endpoint-transact-sql.md)   
 [암호화 알고리즘 선택](../../relational-databases/security/encryption/choose-an-encryption-algorithm.md)   
 [CREATE ENDPOINT&#40;Transact-SQL&#41;](../../t-sql/statements/create-endpoint-transact-sql.md)   
 [서버 네트워크 주소 지정&#40;데이터베이스 미러링&#41;](../../database-engine/database-mirroring/specify-a-server-network-address-database-mirroring.md)   
 [예제: Windows 인증을 사용하여 데이터베이스 미러링 설정&#40;Transact-SQL&#41;](../../database-engine/database-mirroring/example-setting-up-database-mirroring-using-windows-authentication-transact-sql.md)   
 [데이터베이스 미러링 끝점&#40;SQL Server&#41;](../../database-engine/database-mirroring/the-database-mirroring-endpoint-sql-server.md)  
  
  