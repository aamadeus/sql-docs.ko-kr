---
title: sp_sproc_columns (TRANSACT-SQL) | Microsoft Docs
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_sproc_columns
- sp_sproc_columns_TSQL
dev_langs: TSQL
helpviewer_keywords: sp_sproc_columns
ms.assetid: 62c18c21-35c5-4772-be0d-ffdcc19c97ab
caps.latest.revision: "26"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 9488e94ffa0d3532ce72e421f5deadaf1acbed77
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/21/2017
---
# <a name="spsproccolumns-transact-sql"></a>sp_sproc_columns(Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  현재 환경 내의 저장 프로시저 또는 사용자 정의 함수에 대한 열 정보를 반환합니다.  
  
 ![항목 링크 아이콘](../../database-engine/configure-windows/media/topic-link.gif "항목 링크 아이콘") [Transact-SQL 구문 규칙](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>구문  
  
```  
-- Syntax for SQL Server, Azure SQL Database, Azure SQL Data Warehouse, Parallel Data Warehouse  
  
sp_sproc_columns [[@procedure_name = ] 'name']   
    [ , [@procedure_owner = ] 'owner']   
    [ , [@procedure_qualifier = ] 'qualifier']   
    [ , [@column_name = ] 'column_name']  
    [ , [@ODBCVer = ] 'ODBCVer']  
    [ , [@fUsePattern = ] 'fUsePattern']  
```  
  
## <a name="arguments"></a>인수  
 [  **@procedure_name =** ] **'***이름***'**  
 카탈로그 정보를 반환하는 데 사용되는 프로시저의 이름입니다. *이름* 은 **nvarchar (**390**)**, 기본값은 % 현재 데이터베이스의 모든 테이블을 의미입니다. 와일드카드 패턴 일치가 지원됩니다.  
  
 [  **@procedure_owner =**] **'***소유자***'**  
 프로시저의 소유자 이름입니다. *소유자*은 **nvarchar (**384**)**, 기본값은 NULL입니다. 와일드카드 패턴 일치가 지원됩니다. 경우 *소유자* 을 지정 하지 않으면 기본 DBMS의 기본 프로시저 표시 규칙이 적용 됩니다.  
  
 지정한 이름의 프로시저를 현재 사용자가 갖고 있을 경우 해당 프로시저에 대한 정보가 반환됩니다. 경우 *소유자*지정 하지 않으면 현재 사용자가 지정한 이름의 프로시저를 소유 하지 및 **sp_sproc_columns** 데이터베이스 소유자가 소유 하 고 있는 지정한 이름의 프로시저를 찾습니다. 프로시저가 있으면 해당 열에 대한 정보가 반환됩니다.  
  
 [  **@procedure_qualifier =**] **'***한정자***'**  
 프로시저 한정자의 이름입니다. *한정자* 은 **sysname**, 기본값은 NULL입니다. 다양 한 DBMS 제품에서는 테이블에 대 한 세 부분으로 구성 된 이름 (*qualifier.owner.name*). [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서 이 매개 변수는 데이터베이스 이름을 나타냅니다. 일부 제품에서는 테이블 데이터베이스 환경의 서버 이름을 나타냅니다.  
  
 [  **@column_name =**] **'***column_name***'**  
 카탈로그 정보 중 한 열만을 사용하고자 할 때 지정하는 단일 열입니다. *column_name* 은 **nvarchar (**384**)**, 기본값은 NULL입니다. 경우 *column_name* 은 생략 하면 모든 열의 반환 됩니다. 와일드카드 패턴 일치가 지원됩니다. 상호 운용성을 극대화하려면 게이트웨이 클라이언트에서 ISO 표준 패턴 일치(% 및 _ 와일드카드 문자)만 사용해야 합니다.  
  
 [  **@ODBCVer =**] **'***ODBCVer***'**  
 사용하고 있는 ODBC의 버전입니다. *ODBCVer* 은 **int**, 기본값은 2 이며 ODBC 버전 2.0 나타내는입니다. ODBC 버전 2.0과 ODBC 버전 3.0의 차이 대 한 자세한 내용은 odbc 참조 **SQLProcedureColumns** odbc 버전 3.0 사양  
  
 [  **@fUsePattern =**] **'***fUsePattern***'**  
 밑줄(_), 백분율(%) 및 대괄호([ ]) 문자를 와일드카드 문자로 해석할지 여부를 결정합니다. 유효한 값은 0(패턴 일치 해제)과 1(패턴 일치 설정)입니다. *fUsePattern* 은 **비트**, 기본값은 1입니다.  
  
## <a name="return-code-values"></a>반환 코드 값  
 없음  
  
## <a name="result-sets"></a>결과 집합  
  
|열 이름|데이터 형식|Description|  
|-----------------|---------------|-----------------|  
|**PROCEDURE_QUALIFIER**|**sysname**|프로시저 한정자 이름입니다. 이 열은 NULL이 될 수 있습니다.|  
|**PROCEDURE_OWNER**|**sysname**|프로시저 소유자 이름입니다. 이 열은 항상 값을 반환합니다.|  
|**PROCEDURE_NAME**|**nvarchar (**134**)**|프로시저 이름입니다. 이 열은 항상 값을 반환합니다.|  
|**COLUMN_NAME**|**sysname**|각 열에 대 한 열 이름에서 **TABLE_NAME** 반환 합니다. 이 열은 항상 값을 반환합니다.|  
|**COLUMN_TYPE**|**smallint**|이 필드는 항상 값을 반환합니다.<br /><br /> 0 = SQL_PARAM_TYPE_UNKNOWN<br /><br /> 1 = SQL_PARAM_TYPE_INPUT<br /><br /> 2 = SQL_PARAM_TYPE_OUTPUT<br /><br /> 3 = SQL_RESULT_COL<br /><br /> 4 = SQL_PARAM_OUTPUT<br /><br /> 5 = SQL_RETURN_VALUE|  
|**DATA_TYPE**|**smallint**|ODBC 데이터 형식에 대한 정수 코드입니다. 이 데이터 형식을 ISO 형식에 매핑할 수 없는 경우 값은 NULL입니다. 네이티브 데이터 형식 이름이 반환 됩니다는 **TYPE_NAME** 열입니다.|  
|**TYPE_NAME**|**sysname**|데이터 형식의 문자열 표시입니다. 이것은 원본으로 사용되는 DBMS에 의해 제시된 데이터 형식 이름입니다.|  
|**전체 자릿수**|**int**|유효 자릿수입니다. 에 대 한 반환 값은 **정밀도** 열이 정수는 10에서입니다.|  
|**LENGTH**|**int**|데이터의 전송 크기입니다.|  
|**크기 조정**|**smallint**|소수점 오른쪽 자릿수입니다.|  
|**기 수**|**smallint**|숫자 유형에 대한 기준입니다.|  
|**NULL 허용**|**smallint**|Null 허용 여부를 지정합니다.<br /><br /> 1 = Null 값을 허용하는 데이터 형식을 만들 수 있습니다.<br /><br /> 0 = Null 값이 허용되지 않습니다.|  
|**설명**|**varchar (**254**)**|프로시저 열에 대한 설명입니다. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]는 이 열의 값을 반환하지 않습니다.|  
|**COLUMN_DEF**|**nvarchar (**4000**)**|열의 기본값입니다.|  
|**SQL_DATA_TYPE**|**smallint**|에 표시 된 대로 SQL 데이터 형식의 값은 **형식** 설명자 필드입니다. 이 열은 동일는 **DATA_TYPE** 열을 제외 하 고는 **datetime** 및 ISO **간격** 데이터 형식입니다. 이 열은 항상 값을 반환합니다.|  
|**SQL_DATETIME_SUB**|**smallint**|**datetime** ISO **간격** 하위 코드의 값 **SQL_DATA_TYPE** 은 **SQL_DATETIME** 또는 **SQL_INTERVAL**. 이외의 다른 데이터 형식의 **datetime** 및 ISO **간격**,이 필드는 NULL입니다.|  
|**CHAR_OCTET_LENGTH**|**int**|바이트의 최대 길이 **문자** 또는 **이진** 데이터 형식 열입니다. 다른 모든 데이터 형식의 경우에는 이 열이 NULL을 반환합니다.|  
|**ORDINAL_POSITION**|**int**|테이블에 있는 열의 순서 위치입니다. 테이블의 첫 번째 열은 1입니다. 이 열은 항상 값을 반환합니다.|  
|**IS_NULLABLE**|**varchar(254)**|테이블에 있는 열의 Null 허용 여부입니다. ISO 규칙을 따라서 null 허용 여부를 결정합니다. ISO 호환 DBMS에서는 빈 문자열을 반환할 수 없습니다.<br /><br /> 열이 NULL을 포함할 수 있으면 YES를 표시하고 NULL을 포함할 수 없으면 NO를 표시합니다.<br /><br /> Null 허용 여부를 알 수 없으면 이 열에서는 길이가 0인 문자열을 반환합니다.<br /><br /> 이 열에 반환되는 값은 NULLABLE 열에 반환되는 값과 다릅니다.|  
|**SS_DATA_TYPE**|**tinyint**|확장 저장 프로시저에 사용되는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터 형식입니다. 자세한 내용은 [데이터 형식&#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)을 참조하세요.|  
  
## <a name="remarks"></a>주의  
 **sp_sproc_columns** 같습니다 **SQLProcedureColumns** ODBC의 합니다. 반환 결과으로 정렬 **PROCEDURE_QUALIFIER**, **PROCEDURE_OWNER**, **PROCEDURE_NAME**, 및 프로시저에 매개 변수가 나타나는 순서 정의 합니다.  
  
## <a name="permissions"></a>Permissions  
 스키마에 대한 SELECT 권한이 필요합니다.  
  
## <a name="see-also"></a>관련 항목:  
 [카탈로그 저장 프로시저 &#40; Transact SQL &#41;](../../relational-databases/system-stored-procedures/catalog-stored-procedures-transact-sql.md)   
 [시스템 저장 프로시저&#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  