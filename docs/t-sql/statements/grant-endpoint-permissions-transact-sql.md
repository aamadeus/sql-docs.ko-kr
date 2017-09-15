---
title: "GRANT 끝점 사용 권한 (Transact SQL) | Microsoft Docs"
ms.custom: 
ms.date: 06/17/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- endpoints [SQL Server], permissions
- granting permissions [SQL Server], endpoints
- GRANT statement, endpoints
- permissions [SQL Server], endpoints
ms.assetid: 9eda885c-fc3a-4c9d-8de6-ce07fb35a934
caps.latest.revision: 16
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 6f89febc7d63bcf36c947aacd90337e7f9478c96
ms.contentlocale: ko-kr
ms.lasthandoff: 09/01/2017

---
# <a name="grant-endpoint-permissions-transact-sql"></a>GRANT 끝점 사용 권한(Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  끝점에 대한 사용 권한을 부여합니다.  

  
 ![항목 링크 아이콘](../../database-engine/configure-windows/media/topic-link.gif "항목 링크 아이콘") [Transact-SQL 구문 규칙](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>구문  
  
```  
GRANT permission  [ ,...n ] ON ENDPOINT :: endpoint_name  
        TO < server_principal >  [ ,...n ]  
    [ WITH GRANT OPTION ]  
    [ AS SQL_Server_login ]   
  
<server_principal> ::=   
        SQL_Server_login  
    | SQL_Server_login_from_Windows_login   
    | SQL_Server_login_from_certificate   
    | SQL_Server_login_from_AsymKey  
```  
  
## <a name="arguments"></a>인수  
 *사용 권한*  
 끝점에 대해 부여할 수 있는 사용 권한을 지정합니다. 사용 권한 목록은 이 항목의 뒤에 나오는 주의 섹션을 참조하세요.  
  
 끝점에서 **::***endpoint_name*  
 사용 권한을 부여할 끝점을 지정합니다. 범위 한정자 (**::**)가 필요 합니다.  
  
 \<server_principal >  
 사용 권한을 부여할 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 로그인을 지정합니다.  
  
 *SQL_Server_login*  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 로그인의 이름을 지정합니다.  
  
 *SQL_Server_login_from_Windows_login*  
 Windows 로그인에서 생성된 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 로그인의 이름을 지정합니다.  
  
 *SQL_Server_login_from_certificate*  
 인증서로 매핑된 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 로그인의 이름을 지정합니다.  
  
 *SQL_Server_login_from_AsymKey*  
 비대칭 키에 매핑된 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 로그인의 이름을 지정합니다.  
  
 WITH GRANT OPTION  
 지정된 사용 권한을 다른 보안 주체에게 부여할 수 있는 권한도 이 보안 주체에 제공됨을 나타냅니다.  
  
 AS *SQL_Server_login*  
 이 쿼리를 실행하는 보안 주체가 사용 권한을 부여하는 권한을 부여할 수 있는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 로그인을 지정합니다.  
  
## <a name="remarks"></a>주의  
 현재 데이터베이스는 경우에 서버 범위의 사용 권한은 부여할 수 **마스터**합니다.  
  
 끝점에 대 한 정보는 [sys.endpoints](../../relational-databases/system-catalog-views/sys-endpoints-transact-sql.md) 카탈로그 뷰에 있습니다. 서버 사용 권한 정보에 표시 됩니다는 [sys.server_permissions](../../relational-databases/system-catalog-views/sys-server-permissions-transact-sql.md) 카탈로그 뷰 및 서버 보안 주체에 대 한 정보에 표시 되는 [sys.server_principals](../../relational-databases/system-catalog-views/sys-server-principals-transact-sql.md) 카탈로그 뷰.  
  
 끝점은 서버 수준 보안 개체입니다. 다음 표에는 끝점에 대해 부여할 수 있는 가장 제한적인 특정 사용 권한이 의미상 이러한 사용 권한을 포함하는 보다 일반적인 사용 권한과 함께 나열되어 있습니다.  
  
|끝점 사용 권한|끝점 사용 권한에 포함된 사용 권한|서버 사용 권한에 포함된 사용 권한|  
|-------------------------|------------------------------------|----------------------------------|  
|ALTER|CONTROL|ALTER ANY ENDPOINT|  
|CONNECT|CONTROL|CONTROL SERVER|  
|CONTROL|CONTROL|CONTROL SERVER|  
|TAKE OWNERSHIP|CONTROL|CONTROL SERVER|  
|VIEW DEFINITION|CONTROL|VIEW ANY DEFINITION|  
  
## <a name="permissions"></a>Permissions  
 끝점에 대한 CONTROL 권한 또는 서버에 대한 ALTER ANY ENDPOINT 권한이 필요합니다.  
  
## <a name="examples"></a>예  
  
### <a name="a-granting-view-definition-permission-on-an-endpoint"></a>1. 끝점에 대한 VIEW DEFINITION 권한 부여  
 다음 예에서는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 로그인 `VIEW DEFINITION`에 대해 끝점 `Mirror7`에 대한 `ZArifin` 권한을 부여합니다.  
  
```  
USE master;  
GRANT VIEW DEFINITION ON ENDPOINT::Mirror7 TO ZArifin;  
GO  
```  
  
### <a name="b-granting-take-ownership-permission-with-the-grant-option"></a>2. GRANT OPTION을 지정하여 TAKE OWNERSHIP 권한 부여  
 다음 예에서는 `TAKE OWNERSHIP`으로 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 사용자 `Shipping83`에 대해 끝점 `PKomosinski`에 대한 `GRANT OPTION` 권한을 부여합니다.  
  
```  
USE master;  
GRANT TAKE OWNERSHIP ON ENDPOINT::Shipping83 TO PKomosinski   
    WITH GRANT OPTION;  
GO  
```  
  
## <a name="see-also"></a>관련 항목:  
 [끝점 사용 권한 &#40; 거부 Transact SQL &#41;](../../t-sql/statements/deny-endpoint-permissions-transact-sql.md)   
 [REVOKE 끝점 사용 권한 &#40; Transact SQL &#41;](../../t-sql/statements/revoke-endpoint-permissions-transact-sql.md)   
 [CREATE ENDPOINT&#40;Transact-SQL&#41;](../../t-sql/statements/create-endpoint-transact-sql.md)   
 [끝점 카탈로그 뷰 &#40; Transact SQL &#41;](../../relational-databases/system-catalog-views/endpoints-catalog-views-transact-sql.md)   
 [sys.endpoints &#40; Transact SQL &#41;](../../relational-databases/system-catalog-views/sys-endpoints-transact-sql.md)   
 [사용 권한&#40;데이터베이스 엔진&#41;](../../relational-databases/security/permissions-database-engine.md)   
 [보안 주체&#40;데이터베이스 엔진&#41;](../../relational-databases/security/authentication-access/principals-database-engine.md)  
  
  
