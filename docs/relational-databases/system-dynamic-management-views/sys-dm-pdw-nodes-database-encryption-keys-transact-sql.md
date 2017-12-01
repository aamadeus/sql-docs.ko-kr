---
title: sys.dm_pdw_nodes_database_encryption_keys (Transact SQL) | Microsoft Docs
ms.custom: 
ms.date: 03/07/2017
ms.prod: 
ms.prod_service: sql-data-warehouse, pdw
ms.service: sql-data-warehouse
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: TSQL
ms.assetid: e7fd02b2-5d7e-4816-a0af-b58ae2ac3f7a
caps.latest.revision: "9"
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 1fdfeeccb7bbf0ffae44566b46e589c3f90e9c75
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2017
---
# <a name="sysdmpdwnodesdatabaseencryptionkeys-transact-sql"></a>sys.dm_pdw_nodes_database_encryption_keys (Transact SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  연결된 데이터베이스 암호화 키 및 데이터베이스의 암호화 상태에 대한 정보를 반환합니다. **sys.dm_pdw_nodes_database_encryption_keys** 각 노드에 대 한이 정보를 제공 합니다. 데이터베이스 암호화에 대 한 자세한 내용은 참조 [투명 한 데이터 암호화 (SQL Server PDW)](http://msdn.microsoft.com/en-us/b82ad21d-09dd-43dd-8fab-bcf2c8c3ac6d)합니다.  
  
|열 이름|데이터 형식|Description|  
|-----------------|---------------|-----------------|  
|database_id|**int**|각 노드의 실제 데이터베이스 ID입니다.|  
|encryption_state|**int**|이 노드에서 데이터베이스 암호화 되지 않으므로 암호화 여부를 나타냅니다.<br /><br /> 0 = 데이터베이스 암호화 키가 없고 암호화되지 않음<br /><br /> 1 = 암호화되지 않음<br /><br /> 2 = 암호화 진행 중<br /><br /> 3 = 암호화됨<br /><br /> 4 = 키 변경 진행 중<br /><br /> 5 = 해독 진행 중<br /><br /> 6 = 보호 변경 진행 중 (데이터베이스 암호화 키를 암호화 하는 인증서가 변경 됩니다.)|  
|create_date|**datetime**|암호화 키를 만든 날짜를 표시합니다.|  
|regenerate_date|**datetime**|암호화 키를 다시 생성한 날짜를 표시합니다.|  
|modify_date|**datetime**|암호화 키를 수정한 날짜를 표시합니다.|  
|set_date|**datetime**|암호화 키가 데이터베이스에 적용된 날짜를 표시합니다.|  
|opened_date|**datetime**|데이터베이스 키가 마지막으로 열린 시간을 표시합니다.|  
|key_algorithm|**varchar(?)**|키에 사용된 알고리즘을 표시합니다.|  
|key_length|**int**|키의 길이를 표시합니다.|  
|encryptor_thumbprint|**varbin**|암호기의 손도장을 표시합니다.|  
|percent_complete|**real**|데이터베이스 암호화 상태 변경의 완료 비율입니다. 상태 변경이 없으면 0이 됩니다.|  
|node_id|**int**|노드와 연결 된 고유 숫자 id입니다.|  
  
## <a name="permissions"></a>Permissions  
 서버에 대한 VIEW SERVER STATE 권한이 필요합니다.  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>예: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] 및[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 다음 예제에서는 조인을 `sys.dm_pdw_nodes_database_encryption_keys` TDE의 각 노드에 보호 되는 데이터베이스에 대 한 암호화 상태를 나타내는 다른 시스템 테이블에 있습니다.  
  
```  
SELECT D.database_id AS DBIDinMaster, D.name AS UserDatabaseName,   
PD.pdw_node_id AS NodeID, DM.physical_name AS PhysDBName,   
keys.encryption_state  
FROM sys.dm_pdw_nodes_database_encryption_keys AS keys  
JOIN sys.pdw_nodes_pdw_physical_databases AS PD  
    ON keys.database_id = PD.database_id AND keys.pdw_node_id = PD.pdw_node_id  
JOIN sys.pdw_database_mappings AS DM  
    ON DM.physical_name = PD.physical_name  
JOIN sys.databases AS D  
    ON D.database_id = DM.database_id  
ORDER BY D.database_id, PD.pdw_node_ID;  
```  
  
## <a name="see-also"></a>관련 항목:  
 [SQL 데이터 웨어하우스 및 병렬 데이터 웨어하우스 동적 관리 뷰 &#40; Transact SQL &#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)   
 [데이터베이스 암호화 키 &#40; 만들기 Transact SQL &#41;](../../t-sql/statements/create-database-encryption-key-transact-sql.md)   
 [ALTER DATABASE ENCRYPTION key&#40; Transact SQL &#41;](../../t-sql/statements/alter-database-encryption-key-transact-sql.md)   
 [DROP DATABASE ENCRYPTION KEY&#40;Transact-SQL&#41;](../../t-sql/statements/drop-database-encryption-key-transact-sql.md)  
  
  
