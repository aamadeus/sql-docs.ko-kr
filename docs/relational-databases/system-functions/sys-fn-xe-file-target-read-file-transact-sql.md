---
title: sys.fn_xe_file_target_read_file (TRANSACT-SQL) | Microsoft Docs
ms.custom: 
ms.date: 06/22/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: system-functions
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- fn_xe_file_target_read_file_TSQL
- fn_xe_file_target_read_file
- sys.fn_xe_file_target_read_file_TSQL
- sys.fn_xe_file_target_read_file
dev_langs: TSQL
helpviewer_keywords:
- extended events [SQL Server], functions
- fn_xe_file_target_read_file function
- sys.fn_xe_file_target_read_file function
ms.assetid: cc0351ae-4882-4b67-b0d8-bd235d20c901
caps.latest.revision: "20"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 603253fffd3d3ea6d5a42b37f9d7f4fc8a3edccd
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2017
---
# <a name="sysfnxefiletargetreadfile-transact-sql"></a>sys.fn_xe_file_target_read_file(Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  확장 이벤트 비동기 파일 대상에서 만든 파일을 읽습니다. 행당 하나의 이벤트가 XML 형식으로 반환됩니다.  
  
> [!WARNING]  
>  [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]및 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] XEL 및 XEM 형식으로 생성 된 추적 결과 허용 합니다. [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]XEL 형식의 추적 결과를 지원만 이벤트를 확장 합니다. XEL 형식의 추적 결과를 읽으려면 SQL Server Management Studio를 사용하는 것이 좋습니다.    
  
 ![항목 링크 아이콘](../../database-engine/configure-windows/media/topic-link.gif "항목 링크 아이콘") [Transact-SQL 구문 규칙](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>구문  
  
```  
  
sys.fn_xe_file_target_read_file ( path, mdpath, initial_file_name, initial_offset )  
```  
  
## <a name="arguments"></a>인수  
 *경로*  
 읽을 파일 파일의 경로입니다. *경로* 파일의 이름을 포함 하 고 와일드 카드를 포함할 수 있습니다. *경로* 은 **nvarchar (260)**합니다. 기본값은 없습니다. Azure SQL 데이터베이스 환경에서이 값은 Azure 저장소에서 파일에 HTTP URL입니다.
  
 *mdpath*  
 파일 또는 지정 된 파일에 해당 하는 메타 데이터 파일의 경로를 *경로* 인수입니다. *mdpath* 은 **nvarchar (260)**합니다. 기본값은 없습니다. SQL Server 2016 부터는이 매개 변수를 null로 지정할 수 있습니다.
  
> [!NOTE]  
>  [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]필요 하지 않습니다는 *mdpath* 매개 변수입니다. 그러나 이전 버전의 SQL Server에서 생성된 로그 파일의 경우 이전 버전과의 호환성을 위해 이 매개 변수가 유지됩니다.  
  
 *initial_file_name*  
 읽을 첫 번째 파일 *경로*합니다. *initial_file_name* 은 **nvarchar (260)**합니다. 기본값은 없습니다. 경우 **null** 에서 모든 파일을 찾을 인수로 지정 *경로* 읽혀집니다.  
  
> [!NOTE]  
>  *initial_file_name* 및 *initial_offset* 는 쌍을 이루는 인수입니다. 둘 중 한 인수의 값을 지정하는 경우 다른 한 인수의 값도 지정해야 합니다.  
  
 *initial_offset*  
 이전에 읽은 마지막 오프셋을 지정하는데 사용되고 오프셋(포함)까지 모든 이벤트를 건너뜁니다. 이벤트 열거는 오프셋이 지정된 후에 시작됩니다. *initial_offset* 은 **bigint**합니다. 경우 **null** 인수는 전체 파일을 읽을 때 지정 됩니다.  
  
## <a name="table-returned"></a>반환된 테이블  
  
|열 이름|데이터 형식|Description|  
|-----------------|---------------|-----------------|  
|module_guid|**uniqueidentifier**|이벤트 모듈 GUID입니다. Null을 허용하지 않습니다.|  
|package_guid|**uniqueidentifier**|이벤트 패키지 GUID입니다. Null을 허용하지 않습니다.|  
|object_name|**nvarchar(256)**|이벤트의 이름입니다. Null을 허용하지 않습니다.|  
|event_data|**nvarchar(max)**|XML 형식의 이벤트 내용입니다. Null을 허용하지 않습니다.|  
|file_name|**nvarchar (260)**|이벤트가 포함된 파일의 이름입니다. Null을 허용하지 않습니다.|  
|file_offset|**bigint**|이벤트가 포함된 파일에 있는 블록의 오프셋입니다. Null을 허용하지 않습니다.|  
|timestamp_utc|**datetime2**|**적용 대상**: [!INCLUDE[ssSQLv14](../../includes/sssqlv14-md.md)] 통해 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 및 [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]합니다.<br /><br />날짜 및 이벤트의 시간 (UTC 표준 시간대)입니다. Null을 허용하지 않습니다.|  

  
## <a name="remarks"></a>주의  
 실행 하 여 설정 하는 큰 결과 읽는 **sys.fn_xe_file_target_read_file** 에 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 오류가 발생할 수 있습니다. 사용 하 여는 **파일로 결과 저장** 모드 (**Ctrl + Shift + F**) 많은 결과 집합을 파일로 내보내고 대신 다른 도구로 파일을 읽을 합니다.  
  
## <a name="permissions"></a>Permissions  
 을 실행하려면 서버에 대해 VIEW SERVER STATE 권한이 필요합니다.  
  
## <a name="examples"></a>예  
  
### <a name="a-retrieving-data-from-file-targets"></a>1. 파일 대상에서 데이터 가져오기  
 다음 예에서는 모든 파일의 행을 모두 가져옵니다. 이 예에서 파일 대상과 메타파일은 C:\ 드라이브의 추적 폴더에 있습니다.  
  
```  
SELECT * FROM sys.fn_xe_file_target_read_file('C:\traces\*.xel', 'C:\traces\metafile.xem', null, null);  
```  
  
## <a name="see-also"></a>관련 항목:  
 [확장 이벤트 동적 관리 뷰](../../relational-databases/system-dynamic-management-views/extended-events-dynamic-management-views.md)   
 [확장 이벤트 카탈로그 뷰&#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/extended-events-catalog-views-transact-sql.md)   
 [확장 이벤트](../../relational-databases/extended-events/extended-events.md)  
  
  