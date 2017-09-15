---
title: "DENY 개체 사용 권한 (Transact SQL) | Microsoft Docs"
ms.custom: 
ms.date: 06/10/2016
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
- DENY statement, objects
- table permissions [SQL Server]
ms.assetid: 0b8d3ddc-38c0-4241-b7bb-ee654a5081aa
caps.latest.revision: 26
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 2655a796d6d097cb635576313664ea6bfa7162db
ms.contentlocale: ko-kr
ms.lasthandoff: 09/01/2017

---
# <a name="deny-object-permissions-transact-sql"></a>DENY 개체 사용 권한(Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  보안 개체의 OBJECT 클래스 멤버에 대한 사용 권한을 거부합니다. OBJECT 클래스의 멤버에는 테이블, 뷰, 테이블 반환 함수, 저장 프로시저, 확장 저장 프로시저, 스칼라 함수, 집계 함수, 서비스 큐 및 동의어에 대한 사용 권한이 있습니다.  

  
 ![항목 링크 아이콘](../../database-engine/configure-windows/media/topic-link.gif "항목 링크 아이콘") [Transact-SQL 구문 규칙](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>구문  
  
```  
DENY <permission> [ ,...n ] ON   
    [ OBJECT :: ][ schema_name ]. object_name [ ( column [ ,...n ] ) ]  
        TO <database_principal> [ ,...n ]   
    [ CASCADE ]  
        [ AS <database_principal> ]  
  
<permission> ::=  
    ALL [ PRIVILEGES ] | permission [ ( column [ ,...n ] ) ]  
  
<database_principal> ::=   
        Database_user   
    | Database_role   
    | Application_role   
    | Database_user_mapped_to_Windows_User   
    | Database_user_mapped_to_Windows_Group   
    | Database_user_mapped_to_certificate   
    | Database_user_mapped_to_asymmetric_key   
    | Database_user_with_no_login  
```  
  
## <a name="arguments"></a>인수  
 *사용 권한*  
 스키마 포함 개체에 대해 거부할 수 있는 사용 권한을 지정합니다. 사용 권한 목록은 이 항목의 뒤에 나오는 주의 섹션을 참조하세요.  
  
 ALL  
 ALL을 거부하더라도 일부 가능한 사용 권한은 거부되지 않습니다. ALL을 거부하는 것은 지정된 개체에 적용할 수 있는 모든 ANSI-92 사용 권한을 거부하는 것과 동일합니다. ALL의 의미는 다음과 같이 달라집니다.  
  
 - 스칼라 함수 사용 권한: EXECUTE, REFERENCES.  
 - 테이블 반환 함수 사용 권한: DELETE, INSERT, REFERENCES, SELECT, UPDATE.  
 - 저장 프로시저 사용 권한: EXECUTE.  
 - 테이블 사용 권한: DELETE, INSERT, REFERENCES, SELECT, UPDATE.  
 - 뷰 사용 권한: DELETE, INSERT, REFERENCES, SELECT, UPDATE.  
  
PRIVILEGES  
 ANSI-92 호환성을 위해 포함되었습니다. ALL의 동작을 변경하지 않습니다.  
  
*열*  
 사용 권한을 거부할 테이블, 뷰 또는 테이블 반환 함수의 열 이름을 지정합니다. 괄호 **()** 필요 합니다. SELECT, REFERENCES 및 UPDATE 권한만 열에 정의할 수 있습니다. *열* 보안 이름 뒤 또는 사용 권한 절에 지정할 수 있습니다.  
  
> [!CAUTION]  
>  테이블 수준의 DENY는 열 수준의 GRANT보다 우선하지 않습니다. 사용 권한 계층에서의 이러한 불일치는 이전 버전과의 호환성을 위해 유지되었습니다.  
  
 ON [개체 **::** ] [ *schema_name* ] **합니다.** *object_name*  
 사용 권한을 거부할 개체를 지정합니다. OBJECT 구가 선택 사항 경우 *schema_name* 지정 됩니다. OBJECT 구를 사용 하는 경우 범위 한정자 (**::**)가 필요 합니다. 경우 *schema_name* 를 지정 하지 않으면 기본 스키마가 사용 됩니다. 경우 *schema_name* 지정 된 스키마 범위 한정자 (**.**)가 필요 합니다.  
  
 \<데이터베이스 _ 보안 주체 >  
 사용 권한을 거부할 보안 주체를 지정합니다.  
  
 CASCADE  
 사용 권한이 거부된 보안 주체에게 사용 권한을 부여 받은 다른 보안 주체의 사용 권한도 거부됨을 나타냅니다.  
  
 AS \<데이터베이스 _ 보안 주체 >  
 이 쿼리를 실행하는 보안 주체가 사용 권한을 거부하는 권한을 부여할 수 있는 다른 보안 주체를 지정합니다.  
  
 *Database_user*  
 데이터베이스 사용자를 지정합니다.  
  
 *Database_role*  
 데이터베이스 역할을 지정합니다.  
  
 *Application_role*  
 응용 프로그램 역할을 지정합니다.  
  
 *Database_user_mapped_to_Windows_User*  
 Windows 사용자로 매핑된 데이터베이스 사용자를 지정합니다.  
  
 *Database_user_mapped_to_Windows_Group*  
 Windows 그룹으로 매핑된 데이터베이스 사용자를 지정합니다.  
  
 *Database_user_mapped_to_certificate*  
 인증서로 매핑된 데이터베이스 사용자를 지정합니다.  
  
 *Database_user_mapped_to_asymmetric_key*  
 비대칭 키로 매핑된 데이터베이스 사용자를 지정합니다.  
  
 *Database_user_with_no_login*  
 해당 서버 수준의 보안 주체가 없는 데이터베이스 사용자를 지정합니다.  
  
## <a name="remarks"></a>주의  
 개체에 대한 정보는 다양한 카탈로그 뷰에 표시됩니다. 자세한 내용은 참조 [개체 카탈로그 뷰 &#40; Transact SQL &#41; ](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md).  
  
 개체는 사용 권한 계층에서 해당 개체의 부모인 스키마에 포함된 스키마 수준 보안 개체입니다. 다음 표에는 개체에 대해 거부할 수 있는 가장 제한적인 특정 사용 권한이 의미상 이러한 사용 권한을 포함하는 보다 일반적인 사용 권한과 함께 나열되어 있습니다.  
  
|개체 사용 권한|개체 사용 권한에 포함된 사용 권한|스키마 사용 권한에 포함된 사용 권한|  
|-----------------------|----------------------------------|----------------------------------|  
|ALTER|CONTROL|ALTER|  
|CONTROL|CONTROL|CONTROL|  
|DELETE|CONTROL|DELETE|  
|CREATE 문을 실행하기 전에|CONTROL|CREATE 문을 실행하기 전에|  
|INSERT|CONTROL|INSERT|  
|RECEIVE|CONTROL|CONTROL|  
|REFERENCES|CONTROL|REFERENCES|  
|SELECT|RECEIVE|SELECT|  
|TAKE OWNERSHIP|CONTROL|CONTROL|  
|UPDATE|CONTROL|UPDATE|  
|VIEW CHANGE TRACKING|CONTROL|VIEW CHANGE TRACKING|  
|VIEW DEFINITION|CONTROL|VIEW DEFINITION|  
  
## <a name="permissions"></a>Permissions  
 개체에 대한 CONTROL 권한이 필요합니다.  
  
 AS 절을 사용하는 경우 지정된 보안 주체가 사용 권한을 거부할 개체를 소유해야 합니다.  
  
## <a name="examples"></a>예  
다음 예에서는 AdventureWorks 데이터베이스를 사용 합니다.
  
### <a name="a-denying-select-permission-on-a-table"></a>1. 테이블에 대한 SELECT 권한 거부  
 다음 예제에서는 거부 `SELECT` 사용자에 게 `RosaQdM` 테이블에 `Person.Address`합니다.  
  
```  
DENY SELECT ON OBJECT::Person.Address TO RosaQdM;  
GO  
```  
  
### <a name="b-denying-execute-permission-on-a-stored-procedure"></a>2. 저장 프로시저에 대한 EXECUTE 권한 거부  
 다음 예에서는 `EXECUTE`이라는 응용 프로그램 역할에 대해 저장 프로시저 `HumanResources.uspUpdateEmployeeHireInfo`에 대한 `Recruiting11` 권한을 거부합니다.  
  
```  
DENY EXECUTE ON OBJECT::HumanResources.uspUpdateEmployeeHireInfo  
    TO Recruiting11;  
GO   
```  
  
### <a name="c-denying-references-permission-on-a-view-with-cascade"></a>3. CASCADE를 지정하여 뷰에 대한 REFERENCES 권한 거부  
 다음 예에서는 `REFERENCES`를 지정하여 사용자 `BusinessEntityID`에 대해 `HumanResources.vEmployee` 뷰의 `Wanida` 열에 대한 `CASCADE` 권한을 거부합니다.  
  
```  
DENY REFERENCES (BusinessEntityID) ON OBJECT::HumanResources.vEmployee   
    TO Wanida CASCADE;  
GO  
```  
  
## <a name="see-also"></a>관련 항목:  
 [GRANT 개체 사용 권한&#40;Transact-SQL&#41;](../../t-sql/statements/grant-object-permissions-transact-sql.md)   
 [REVOKE 개체 사용 권한 &#40; Transact SQL &#41;](../../t-sql/statements/revoke-object-permissions-transact-sql.md)   
 [개체 카탈로그 뷰 &#40; Transact SQL &#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [사용 권한&#40;데이터베이스 엔진&#41;](../../relational-databases/security/permissions-database-engine.md)   
 [보안 주체&#40;데이터베이스 엔진&#41;](../../relational-databases/security/authentication-access/principals-database-engine.md)   
 [Securables](../../relational-databases/security/securables.md)   
 [sys.fn_builtin_permissions&#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-builtin-permissions-transact-sql.md)   
 [HAS_PERMS_BY_NAME&#40;Transact-SQL&#41;](../../t-sql/functions/has-perms-by-name-transact-sql.md)   
 [sys.fn_my_permissions &#40; Transact SQL &#41;](../../relational-databases/system-functions/sys-fn-my-permissions-transact-sql.md)  
  
  
