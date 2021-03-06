---
title: 프로젝트 설정 (형식 매핑) (DB2ToSQL) | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: cf426c69-6a8e-4d19-951d-6661d5ae2562
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 91498db5535c99c7c8afaba85efc35639510a079
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47642268"
---
# <a name="project-settings-type-mapping-db2tosql"></a>프로젝트 설정 (형식 매핑) (DB2ToSQL)
형식 매핑 페이지의 **프로젝트 설정** 대화 상자에는 SSMA DB2 데이터 형식으로 변환 하는 방법을 사용자 지정 하는 설정이 포함 되어 있습니다. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터 형식입니다.  
  
형식 매핑 페이지의 수를 **프로젝트 설정** 하 고 **기본 프로젝트 설정** 대화 상자.  
  
-   에 모든 향후 SSMA 프로젝트에 대 한 설정을 지정 하는 **도구** 메뉴 **기본 프로젝트 설정**, 설정을 보거나 에서변경하는데필요한는마이그레이션프로젝트형식을선택**마이그레이션 대상 버전** 드롭다운을 클릭 한 다음 **형식 매핑** 왼쪽 창의 맨 아래에 있습니다.  
  
-   현재 프로젝트에 대 한 설정을 지정 하는 **도구** 메뉴 **프로젝트 설정**를 클릭 하 고 **형식 매핑** 왼쪽 창의 맨 아래에.  
  
현재 개체 또는 개체의 클래스에 대 한 설정을 지정 하려면 사용 합니다 **형식 매핑** 기본 SSMA 창의 탭 합니다.  
  
## <a name="options"></a>변수  
다음 표는 **형식 매핑** 탭 옵션:  
  
**원본 형식**  
매핑된 DB2 데이터 형식입니다.  
  
**대상 유형**  
대상 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 지정된 된 DB2 데이터 형식에 대 한 데이터 형식입니다.  
  
DB2 형식 매핑에 대 한 기본 SSMA 다음 섹션의 표를 참조 하세요.  
  
**추가**  
데이터 형식 매핑 목록에 추가 하려면 클릭 합니다.  
  
**편집**  
매핑 목록에서 선택한 데이터 형식을 편집 하려면 클릭 합니다.  
  
**제거**  
매핑 목록에서 선택한 데이터 형식 매핑을 제거 하려면 클릭 합니다.  
  
**기본값으로 다시 설정**  
형식 매핑 목록 SSMA 기본값으로 다시 설정 하려면 클릭 합니다.  
  
## <a name="default-type-mappings"></a>기본 형식 매핑  
DB2 용 SSMA, 인수, 열, 지역 변수 및 반환 값에 대 한 사용자 지정 형식 매핑을 설정할 수 있습니다. 인수 및 반환 형식에 대 한 기본 매핑을 거의 동일합니다.  
  
### <a name="default-argument-type-and-return-value-type-mapping"></a>기본 인수 형식 및 반환 값 형식 매핑  
다음 표에서 인수 및 반환 값에 대 한 기본 데이터 형식 매핑을 보여 줍니다.  
  
|DB2 데이터 형식|기본 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터 형식|  
|-----------------|-------------------------------------------------------------------------|  
|bfile|varbinary(max)|  
|binary_double|float[53]|  
|binary_float|float[53]|  
|binary_integer|ssNoversion|  
|blob|varbinary(max)|  
|boolean|bit|  
|char|varchar(max)|  
|char varying|varchar(max)|  
|character|varchar(max)|  
|character varying|varchar(max)|  
|Clob|varchar(max)|  
|날짜|datetime2[0]|  
|dec|dec[38][0]|  
|Decimal|float[53]|  
|배정밀도|float[53]|  
|FLOAT|float[53]|  
|ssNoversion|ssNoversion|  
|integer|ssNoversion|  
|long|varchar(max)|  
|long raw|varbinary(max)|  
|long raw [\*... 8000]<sup>\*</sup>|varbinary [\*]|  
|long raw [8001...\*]<sup>\*</sup>|varbinary(max)|  
|national char|nvarchar(max)|  
|national char varying|nvarchar(max)|  
|국가별 문자|nvarchar(max)|  
|국가별 문자 변경<sup>\*\*</sup>|nvarchar(max)|  
|다양 한 국가별 문자<sup>\*</sup>|nvarchar(max)|  
|NCHAR|nvarchar(max)|  
|nclob|nvarchar(max)|  
|number|float[53]|  
|NUMERIC|float[53]|  
|nvarchar2|nvarchar(max)|  
|pls_integer|ssNoversion|  
|raw|varbinary(max)|  
|REAL|float[53]|  
|rowid|UNIQUEIDENTIFIER|  
|signtype|SMALLINT|  
|SMALLINT|SMALLINT|  
|string|varchar(max)|  
|TIMESTAMP|Datetime2|  
|현지 표준 시간대를 사용 하 여 타임 스탬프|datetimeoffset|  
|표준 시간대를 사용 하 여 타임 스탬프|datetimeoffset|  
|urowid|UNIQUEIDENTIFIER|  
|varchar|varchar(max)|  
|varchar2|varchar(max)|  
|xmltype|xml|  
  
<sup>\*</sup> 값 형식 매핑만 반환에 적용 됩니다.  
  
<sup>\*\*</sup> 인수 형식 매핑만 적용 됩니다.  
  
### <a name="default-column-type-mapping"></a>기본 열 형식 매핑  
다음 표에서 열에 대 한 기본 형식 매핑을 보여 줍니다.  
  
|DB2 데이터 형식|기본 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터 형식|  
|-----------------|-------------------------------------------------------------------------|  
|bfile|varbinary(max)|  
|binary_double|float[53]|  
|binary_float|float[53]|  
|blob|varbinary(max)|  
|char|char|  
|다양 한 char [\*... \*]|varchar [\*]|  
|char [\*... \*]|char [\*]|  
|character|char|  
|다양 한 문자 [\*... \*]|varchar [\*]|  
|문자 [\*... \*]|char [\*]|  
|Clob|varchar(max)|  
|날짜|datetime2[0]|  
|dec|dec[38][0]|  
|dec [\*... \*]|dec [\*] [0]|  
|dec [\*... \*][\*.. \*]|dec [\*] [\*]|  
|Decimal|decimal[38][0]|  
|decimal [\*... \*]|decimal [\*] [0]|  
|decimal [\*... \*][\*.. \*]|decimal [\*] [\*]|  
|배정밀도|float[53]|  
|FLOAT|float[53]|  
|float [\*... 53]|float [\*]|  
|float [54...\*]|float[53]|  
|ssNoversion|ssNoversion|  
|integer|ssNoversion|  
|long|varchar(max)|  
|long raw|varbinary(max)|  
|long raw [\*... 8000]|varbinary [\*]|  
|long raw [8001...\*]|varbinary(max)|  
|long varchar|varchar(max)|  
|긴 [\*... 8000]|varchar [\*]|  
|긴 [8001...\*]|varchar(max)|  
|national char|NCHAR|  
|national char varying [\*... \*]|nvarchar [\*]|  
|national char [\*... \*]|nchar [\*]|  
|국가별 문자|NCHAR|  
|다양 한 국가별 문자 [\*... \*]|nvarchar [\*]|  
|국가별 문자 [\*... \*]|nchar [\*]|  
|NCHAR|NCHAR|  
|nchar [\*]|nchar [\*]|  
|nclob|nvarchar(max)|  
|number|float[53]|  
|숫자 [\*... \*]|숫자 [\*]|  
|숫자 [\*... \*][\*.. \*]|숫자 [\*] [\*]|  
|NUMERIC|NUMERIC|  
|숫자 [\*... \*]|숫자 [\*]|  
|숫자 [\*... \*][\*.. \*]|숫자 [\*] [\*]|  
|nvarchar2 [\*... \*]|nvarchar [\*]|  
|원시 [\*... \*]|varbinary [\*]|  
|REAL|float[53]|  
|rowid|UNIQUEIDENTIFIER|  
|SMALLINT|SMALLINT|  
|TIMESTAMP|Datetime2|  
|현지 표준 시간대를 사용 하 여 타임 스탬프|datetimeoffset|  
|현지 표준 시간대를 사용 하 여 타임 스탬프 [\*... \*]|datetimeoffset [\*]|  
|표준 시간대를 사용 하 여 타임 스탬프|datetimeoffset|  
|표준 시간대를 사용 하 여 타임 스탬프 [\*... \*]|datetimeoffset [\*]|  
|타임 스탬프 [\*... \*]|datetime2 [\*]|  
|urowid|UNIQUEIDENTIFIER|  
|urowid [\*... \*]|UNIQUEIDENTIFIER|  
|varchar [\*... \*]|varchar [\*]|  
|varchar2 [\*... \*]|varchar [\*]|  
|Xmltype|xml|  
  
### <a name="default-local-variable-type-mapping"></a>기본 로컬 변수 형식 매핑  
다음 표에서 로컬 변수에 대 한 기본 형식 매핑을 보여 줍니다.  
  
|DB2 데이터 형식|기본 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터 형식|  
|-----------------|-------------------------------------------------------------------------|  
|bfile|varbinary(max)|  
|binary_double|float[53]|  
|binary_float|float[53]|  
|binary_interger|ssNoversion|  
|Blob|varbinary(max)|  
|Boolean|bit|  
|Char|char|  
|다양 한 char [\*... 8000]|varchar [\*]|  
|다양 한 char [8001...\*]|varchar(max)|  
|char [\*... 8000]|char [\*]|  
|char [8001...\*]|varchar(max)|  
|문자|char|  
|다양 한 문자 [\*... 8000]|varchar [\*]|  
|다양 한 문자 [8001...\*]|varchar(max)|  
|문자 [\*... 8000]|char [\*]|  
|문자 [8001...\*]|varchar(max)|  
|Clob|varchar(max)|  
|날짜|datetime2[0]|  
|dec|dec[38][0]|  
|dec [\*... \*]|dec [\*] [0]|  
|dec [\*... \*][\*.. \*]|dec [\*] [\*]|  
|Decimal|decimal[38][0]|  
|decimal [\*... \*]|decimal [\*] [0]|  
|decimal [\*... \*][\*.. \*]|decimal [\*] [\*]|  
|배정밀도|float[53]|  
|float|float[53]|  
|float [\*... 53]|float [\*]|  
|float [54...\*]|float[53]|  
|정수|ssNoversion|  
|정수|ssNoversion|  
|정수 [\*... \*]|숫자 [\*] [0]|  
|Long|varchar(max)|  
|long raw|varbinary(max)|  
|long raw [\*... 8000]|varbinary [\*]|  
|long raw [8001...\*]|varbinary(max)|  
|national char|NCHAR|  
|national char varying [\*... 4000]|nvarchar [\*]|  
|national char varying [4001...\*]|nvarchar(max)|  
|national char [\*... 4000]|nchar [\*]|  
|national char [4001...\*]|nvarchar(max)|  
|국가별 문자|NCHAR|  
|국가별 문자 [\*... 4000]|nvarchar [\*]|  
|국가별 문자 [4001...\*]|nvarchar(max)|  
|다양 한 국가별 문자 [\*... 4000]|nvarchar [\*]|  
|다양 한 국가별 문자 [4001...\*]|nvarchar(max)|  
|Nchar|NCHAR|  
|nchar [\*... 4000]|nchar [\*]|  
|nchar [4001...\*]|nvarchar(max)|  
|nchar 다양 한 [\*... 4000]|nvarchar [\*]|  
|nchar 다양 한 [4001...\*]|nvarchar(max)|  
|nclob|nvarchar(max)|  
|Number|float[53]|  
|숫자 [\*... \*]|숫자 [\*]|  
|숫자 [\*... \*][\*.. \*]|숫자 [\*] [\*]|  
|숫자|numeric[38][0]|  
|숫자 [\*... \*]|숫자 [\*]|  
|숫자 [\*... \*][\*.. \*]|숫자 [\*] [\*]|  
|nvarchar2 [\*... 4000]|nvarchar [\*]|  
|nvarchar2 [4001...\*]|nvarchar(max)|  
|pls_integer|ssNoversion|  
|원시 [\*... 8000]|varbinary [\*]|  
|원시 [8001...\*]|varbinary(max)|  
|Real|float[53]|  
|rowid|UNIQUEIDENTIFIER|  
|signtype|SMALLINT|  
|Smallint|SMALLINT|  
|문자열 [\*... 8000]|varchar [\*]|  
|문자열 [8001...\*]|varchar(max)|  
|TIMESTAMP|Datetime2|  
|현지 표준 시간대를 사용 하 여 타임 스탬프|datetimeoffset|  
|표준 시간대를 사용 하 여 타임 스탬프|datetimeoffset|  
|현지 표준 시간대를 사용 하 여 타임 스탬프 [\*... \*]|datetimeoffset [\*]|  
|표준 시간대를 사용 하 여 타임 스탬프 [\*... \*]|datetimeoffset [\*]|  
|타임 스탬프 [\*... \*]|datetime2 [\*]|  
|urowid|UNIQUEIDENTIFIER|  
|urowid [\*... \*]|UNIQUEIDENTIFIER|  
|varchar [\*... 8000]|varchar [\*]|  
|varchar [8001...\*]|varchar(max)|  
|varchar2 [\*... 8000]|varchar [\*]|  
|varchar2 [8001...\*]|varcha(max)|  
|Xmltype|xml|  
  
## <a name="see-also"></a>관련 항목  
[사용자 인터페이스 참조 &#40;DB2ToSQL&#41;](../../ssma/db2/user-interface-reference-db2tosql.md)  
  
