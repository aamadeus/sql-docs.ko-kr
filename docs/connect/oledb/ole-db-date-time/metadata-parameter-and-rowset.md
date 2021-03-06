---
title: 매개 변수 및 행 집합 메타 데이터 | Microsoft Docs
description: 매개 변수 및 행 집합 메타데이터
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- metadata [OLE DB]
author: pmasl
ms.author: pelopes
manager: craigg
ms.openlocfilehash: 2f25a79e503560ebf027b5bb002584b646c08783
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47834601"
---
# <a name="metadata---parameter-and-rowset"></a>메타데이터 - 매개 변수 및 행 집합
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  이 문서에서는 향상된 OLE DB 날짜 및 시간 기능과 관련하여 다음과 같은 형식 및 형식 멤버에 대한 정보를 제공합니다.  
  
-   DBBINDING 구조  
  
-   **ICommandWithParameters::GetParameterInfo**  
  
-   **ICommandWithParameters::SetParameterInfo**  
  
-   **IColumnsRowset::GetColumnsRowset**  
  
-   **IColumnsInfo::GetColumnInfo**  
  
## <a name="icommandwithparametersgetparameterinfo"></a>ICommandWithParameters::GetParameterInfo  
 다음은 *prgParamInfo*를 통해 DBPARAMINFO 구조에 반환되는 정보입니다.  
  
|매개 변수 유형|*wType*|*ulParamSize*|*bPrecision*|*bScale*|*dwFlags*<br /><br /> DBPARAMFLAGS_SS_ISVARIABLESCALE|  
|--------------------|-------------|-------------------|------------------|--------------|-----------------------------------------------------|  
|날짜|DBTYPE_DBDATE|6|10|0|지우기|  
|Time|DBTYPE_DBTIME2|10|8, 10..16|0..7|Set|  
|smalldatetime|DBTYPE_DBTIMESTAMP|16|16|0|지우기|  
|DATETIME|DBTYPE_DBTIMESTAMP|16|23|3|지우기|  
|Datetime2|DBTYPE_DBTIMESTAMP|16|19, 21..27|0..7|Set|  
|datetimeoffset|DBTYPE_DBTIMESTAMPOFFSET|20|26, 28..34|0..7|Set|  
  
 값 범위가 연속되지 않을 수도 있습니다. 이러한 경우는 소수 부분 자릿수가 0보다 커서 소수점을 추가했을 때 발생합니다.  
  
 DBPARAMFLAGS_SS_ISVARIABLESCALE은 [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)](또는 이후 버전) 서버에 연결된 경우에만 유효합니다. 하위 수준 서버에 연결된 경우에는 DBPARAMFLAGS_SS_ISVARIABLESCALE이 설정되지 않습니다.  
  
## <a name="icommandwithparameterssetparameterinfo-and-implied-parameter-types"></a>ICommandWithParameters::SetParameterInfo 및 암시적 매개 변수 유형  
 DBPARAMBINDINFO 구조에 제공된 정보는 다음을 준수해야 합니다.  
  
|*pwszDataSourceType*<br /><br /> (공급자별로 다름)|*pwszDataSourceType*<br /><br /> (OLE DB 일반)|*ulParamSize*|*bScale*|  
|----------------------------------------------------|-------------------------------------------------|-------------------|--------------|  
||DBTYPE_DATE|6|무시됨|  
|날짜|DBTYPE_DBDATE|6|무시됨|  
||DBTYPE_DBTIME|10|무시됨|  
|Time|DBTYPE_DBTIME2|10|0..7|  
|smalldatetime||16|무시됨|  
|DATETIME||16|무시됨|  
|datetime2 또는 DBTYPE_DBTIMESTAMP|DBTYPE_DBTIMESTAMP|16|0..7|  
|datetimeoffset|DBTYPE_DBTIMESTAMPOFFSET|20|0..7|  
  
 합니다 *bPrecision* 매개 변수가 무시 됩니다.  
  
 "DBPARAMFLAGS_SS_ISVARIABLESCALE"은 데이터를 서버로 보낼 때 무시됩니다. 응용 프로그램은 공급자별 유형 이름 "**datetime**" 및 "**smalldatetime**"을 사용하여 레거시 TDS(Tabular Data Stream) 유형의 사용을 강제할 수 있습니다. [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] 이상 버전의 서버에 연결된 경우 "**datetime2**" 형식이 사용되며, 유형 이름이 "**datetime2**" 또는 "DBTYPE_DBTIMESTAMP"이면 필요에 따라 암시적 서버 변환이 발생합니다. *bScale* 공급자별 이름을 입력 하는 경우 무시 됩니다 "**datetime**"또는"**smalldatetime**"는 데 사용 됩니다. 응용 프로그램 확인 해야이 고, 그렇지 *bScale* 올바르게 설정 되어 있습니다. 응용 프로그램에서 SQL Server 용 MDAC 및 OLE DB 드라이버에서 업그레이드 [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] 사용 하는 설정 하지 않을 경우 "DBTYPE_DBTIMESTAMP" 못합니다 *bScale* 올바르게 합니다. [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] 이전 버전의 서버 인스턴스에 연결된 경우 "DBTYPE_DBTIMESTAMP"가 있는 *bScale* 값이 0 또는 3이 아니면 오류이며 E_FAIL이 반환됩니다.  
  
 Icommandwithparameters:: Setparameterinfo를 호출 하지 않으면 공급자 iaccessor:: Createaccessor에 지정 된 바인딩 유형에 서 서버 유형을 다음과 같이 의미 합니다.  
  
|바인딩 유형|*pwszDataSourceType*<br /><br /> (공급자별로 다름)|  
|------------------|----------------------------------------------------|  
|DBTYPE_DATE|datetime2(0)|  
|DBTYPE_DBDATE|날짜|  
|DBTYPE_DBTIME|time(0)|  
|DBTYPE_DBTIME2|time(7)|  
|DBTYPE_DBTIMESTAMP|datetime2(7)|  
|DBTYPE_DBTIMESTAMPOFFSET|datetimeoffset(7)|  
  
## <a name="icolumnsrowsetgetcolumnsrowset"></a>IColumnsRowset::GetColumnsRowset  
 **Icolumnsrowset:: Getcolumnsrowset** 다음 열을 반환 합니다.  
  
|열 유형|DBCOLUMN_TYPE|DBCOLUM_COLUMNSIZE|DBCOLUMN_PRECISION|DBCOLUMN_SCALE, DBCOLUMN_DATETIMEPRECISION|DBCOLUMN_FLAGS, DBCOLUMNFLAGS_SS_ISVARIABLESCALE|  
|-----------------|--------------------|-------------------------|-------------------------|--------------------------------------------------|---------------------------------------------------------|  
|날짜|DBTYPE_DBDATE|6|10|0|지우기|  
|Time|DBTYPE_DBTIME2|10|8, 10..16|0..7|Set|  
|smalldatetime|DBTYPE_DBTIMESTAMP|16|16|0|지우기|  
|DATETIME|DBTYPE_DBTIMESTAMP|16|23|3|지우기|  
|Datetime2|DBTYPE_DBTIMESTAMP|16|19, 21..27|0..7|Set|  
|datetimeoffset|DBTYPE_DBTIMESTAMPOFFSET|20|26, 28..34|0..7|Set|  
  
 DBCOLUMN_FLAGS에서 날짜/시간 유형에 대해 DBCOLUMNFLAGS_ISFIXEDLENGTH는 항상 true이지만 다음과 같은 플래그는 항상 false입니다.  
  
-   DBCOLUMNFLAGS_CACHEDEFERRED  
  
-   DBCOLUMNFLAGS_ISBOOKMARK  
  
-   DBCOLUMNFLAGS_ISCHAPTER  
  
-   DBCOLUMNFLAGS_ISLONG  
  
-   DBCOLUMNFLAGS_ISROWID  
  
-   DBCOLUMNFLAGS_ISROWVER  
  
-   DBCOLUMNFLAGS_MAYDEFER  
  
 나머지 플래그(DBCOLUMNFLAGS_ISNULLABLE, DBCOLUMNFLAGS_MAYBENULL, DBCOLUMNFLAGS_WRITE 및 DBCOLUMNFLAGS_WRITEUNKNOWN)는 열이 정의된 방법 및 실제 쿼리에 따라 설정될 수 있습니다.  
  
 새 플래그 DBCOLUMNFLAGS_SS_ISVARIABLESCALE는 응용 프로그램에서 DBCOLUMN_TYPE이 DBTYPE_DBTIMESTAMP인 열의 서버 유형을 확인할 수 있도록 DBCOLUMN_FLAGS에 제공됩니다. 서버 유형을 확인하려면 DBCOLUMN_SCALE 또는 DBCOLUMN_DATETIMEPRECISION도 사용해야 합니다.  
  
 DBCOLUMNFLAGS_SS_ISVARIABLESCALE은 [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] 이상 버전의 서버에 연결된 경우에만 유효합니다. 하위 수준 서버에 연결된 경우에는 DBCOLUMNFLAGS_SS_ISVARIABLESCALE이 정의되지 않습니다.  
  
## <a name="icolumnsinfogetcolumninfo"></a>IColumnsInfo::GetColumnInfo  
 DBCOLUMNINFO 구조는 다음 정보를 반환합니다.  
  
|매개 변수 유형|*wType*|*ulColumnSize*|*bPrecision*|*bScale*|*dwFlags*<br /><br /> DBPARAMFLAGS_SS_ISVARIABLESCALE|  
|--------------------|-------------|--------------------|------------------|--------------|-----------------------------------------------------|  
|날짜|DBTYPE_DBDATE|6|10|0|지우기|  
|time(1..7)|DBTYPE_DBTIME2|10|8, 10..16|0..7|Set|  
|smalldatetime|DBTYPE_DBTIMESTAMP|16|16|0|지우기|  
|DATETIME|DBTYPE_DBTIMESTAMP|16|23|3|지우기|  
|Datetime2|DBTYPE_DBTIMESTAMP|16|19, 21..27|0..7|Set|  
|datetimeoffset|DBTYPE_DBTIMESTAMPOFFSET|20|26, 28..34|0..7|Set|  
  
 *dwFlags*에서 날짜/시간 유형에 대해 DBCOLUMNFLAGS_ISFIXEDLENGTH는 항상 true이지만 다음과 같은 플래그는 항상 false입니다.  
  
-   DBCOLUMNFLAGS_CACHEDEFERRED  
  
-   DBCOLUMNFLAGS_ISBOOKMARK  
  
-   DBCOLUMNFLAGS_ISCHAPTER  
  
-   DBCOLUMNFLAGS_ISLONG  
  
-   DBCOLUMNFLAGS_ISROWID  
  
-   DBCOLUMNFLAGS_ISROWVER, MAYDEFER  
  
 나머지 플래그(DBCOLUMNFLAGS_ISNULLABLE, DBCOLUMNFLAGS_MAYBENULL, DBCOLUMNFLAGS_WRITE 및 DBCOLUMNFLAGS_WRITEUNKNOWN)가 설정될 수 있습니다.  
  
 새 플래그 DBCOLUMNFLAGS_SS_ISVARIABLESCALE은 응용 프로그램에서 *wType*이 DBTYPE_DBTIMESTAMP인 열의 서버 유형을 확인할 수 있도록 *dwFlags*에 제공됩니다. 서버 유형을 확인하려면 *bScale*도 사용해야 합니다.  
  
## <a name="see-also"></a>참고 항목  
 [OLE DB 날짜 및 시간 기능 향상을 위한 데이터 형식 지원](../../oledb/ole-db-date-time/data-type-support-for-ole-db-date-and-time-improvements.md)  
  
  
