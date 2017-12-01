---
title: sys.syscolumns (Transact SQL) | Microsoft Docs
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-non-specified
ms.prod_service: database-enginel, sql-data-warehouse, pdw
ms.service: 
ms.component: system-compatibility-views
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.syscolumns
- sys.syscolumns_TSQL
- syscolumns_TSQL
- syscolumns
dev_langs: TSQL
helpviewer_keywords:
- syscolumns system table
- sys.syscolumns compatibility view
ms.assetid: 863fd87b-ff33-4ac5-9aa9-df21140681da
caps.latest.revision: "32"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 94f43de0bf804d366b599c053d8dddadf51d809f
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2017
---
# <a name="syssyscolumns-transact-sql"></a>sys.syscolumns(Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-xxxx-asdw-pdw-md.md)]

  데이터베이스에 있는 모든 테이블 및 뷰의 모든 열에 대한 행, 그리고 저장 프로시저의 각 매개 변수당 한 개의 행을 반환합니다.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssnoteCompView](../../includes/ssnotecompview-md.md)]  
  
|열 이름|데이터 형식|Description|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|열 또는 프로시저 매개 변수의 이름입니다.|  
|**id**|**int**|이 열이 속한 테이블의 개체 ID 또는 이 매개 변수와 연관된 저장 프로시저의 ID입니다.|  
|**xtype**|**tinyint**|물리적 저장소 유형 **sys.types**합니다.|  
|**typestat**|**tinyint**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**xusertype**|**smallint**|확장 사용자 정의 데이터 형식의 ID입니다. 데이터 형식 수가 32,767을 초과하면 오버플로되거나 NULL을 반환합니다.|  
|**길이**|**smallint**|최대 물리적 저장 길이 **sys**. **형식**합니다.|  
|**xprec**|**tinyint**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**xscale**|**tinyint**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**열 id**|**smallint**|열 또는 매개 변수 ID입니다.|  
|**사분면**|**smallint**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**bitpos**|**tinyint**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**예약**|**tinyint**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**colstat**|**smallint**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**cdefault**|**int**|이 열에 대한 기본값의 ID입니다.|  
|**도메인**|**int**|이 열에 대한 CHECK 제약 조건 또는 규칙의 ID입니다.|  
|**번호**|**smallint**|프로시저가 그룹화될 때의 하위 프로시저 번호입니다.<br /><br /> 0 = 프로시저가 아닌 항목|  
|**colorder**|**smallint**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**autoval**|**varbinary (8000)**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**오프셋**|**smallint**|이 열이 나타나는 행의 오프셋입니다.|  
|**collationid**|**int**|열 데이터 정렬의 ID입니다. 문자를 기반으로 하지 않는 열의 경우 NULL입니다.|  
|**상태**|**tinyint**|열 또는 매개 변수의 속성을 설명하는 데 사용되는 비트맵입니다.<br /><br /> 0x08 = 열에 Null 값이 허용됩니다.<br /><br /> 0x10 = ANSI 패딩을 설정할 때 적용 된 **varchar** 또는 **varbinary** 열이 추가 되었습니다. 에 대 한 후행 공백을 유지 하며 **varchar** 후행 0을 유지 하 고 **varbinary** 열입니다.<br /><br /> 0x40 = 매개 변수가 OUTPUT 매개 변수입니다.<br /><br /> 0x80 = 열이 ID 열입니다.|  
|**유형**|**tinyint**|물리적 저장소 유형 **sys**. **형식**합니다.|  
|**usertype**|**smallint**|사용자 정의 데이터 형식의 ID **sys.types**합니다. 데이터 형식 수가 32,767을 초과하면 오버플로되거나 NULL을 반환합니다.|  
|**printfmt**|**varchar (255)**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**prec**|**smallint**|이 열의 전체 자릿수 수준입니다.<br /><br /> -1 = **xml** 또는 큰 값 유형입니다.|  
|**크기 조정**|**int**|이 열의 소수 자릿수입니다.<br /><br /> NULL = 데이터 형식이 숫자가 아닙니다.|  
|**계산 됨**|**int**|열이 계산되었는지 여부를 나타내는 플래그입니다.<br /><br /> 0 = 계산되지 않았음<br /><br /> 1 = 계산됨|  
|**isoutparam**|**int**|프로시저 매개 변수가 출력 매개 변수인지 여부를 나타냅니다.<br /><br /> 1 = True<br /><br /> 0 = False|  
|**isnullable**|**int**|열에 Null 값이 허용되는지 여부를 나타냅니다.<br /><br /> 1 = True<br /><br /> 0 = False|  
|**데이터 정렬**|**sysname**|열의 데이터 정렬 이름입니다. 문자 기반 열이 아닌 경우 NULL입니다.|  
  
## <a name="see-also"></a>관련 항목:  
 [시스템 뷰 &#40; 시스템 테이블 매핑 Transact SQL &#41;](../../relational-databases/system-tables/mapping-system-tables-to-system-views-transact-sql.md)   
 [호환성 뷰&#40;Transact-SQL&#41;](~/relational-databases/system-compatibility-views/system-compatibility-views-transact-sql.md)  
  
  