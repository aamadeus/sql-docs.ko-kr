---
title: 매개 변수 및 행 집합 메타 데이터 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- metadata [OLE DB]
ms.assetid: 31b318a4-20e7-4db0-b367-eb9938859029
caps.latest.revision: 32
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: a8b3365cdf3a2773b6627dfd49edd20b839ef9a8
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36187610"
---
# <a name="parameter-and-rowset-metadata"></a>매개 변수 및 행 집합 메타데이터
  이 항목에서는 향상된 OLE DB 날짜 및 시간 기능과 관련하여 다음과 같은 형식 및 형식 멤버에 대한 정보를 제공합니다.  
  
-   DBBINDING 구조  
  
-   `ICommandWithParameters::GetParameterInfo`  
  
-   `ICommandWithParameters::SetParameterInfo`  
  
-   `IColumnsRowset::GetColumnsRowset`  
  
-   `IColumnsInfo::GetColumnInfo`  
  
## <a name="icommandwithparametersgetparameterinfo"></a>ICommandWithParameters::GetParameterInfo  
 다음 정보를 통해 DBPARAMINFO 구조에 반환 됩니다 *prgParamInfo*:  
  
|매개 변수 유형|*wType*|*ulParamSize*|*bPrecision*|*bScale*|*dwFlags*<br /><br /> DBPARAMFLAGS_SS_ISVARIABLESCALE|  
|--------------------|-------------|-------------------|------------------|--------------|-----------------------------------------------------|  
|날짜|DBTYPE_DBDATE|6|10|0|지우기|  
|Time|DBTYPE_DBTIME2|10|8, 10..16|0..7|Set|  
|smalldatetime|DBTYPE_DBTIMESTAMP|16|16|0|지우기|  
|DATETIME|DBTYPE_DBTIMESTAMP|16|23|3|지우기|  
|Datetime2|DBTYPE_DBTIMESTAMP|16|19,21..27|0..7|Set|  
|datetimeoffset|DBTYPE_DBTIMESTAMPOFFSET|20|26,28..34|0..7|Set|  
  
 값 범위가 연속되지 않을 수도 있습니다. 이러한 경우는 소수 부분 자릿수가 0보다 커서 소수점을 추가했을 때 발생합니다.  
  
 DBPARAMFLAGS_SS_ISVARIABLESCALE은만에 연결 된 경우 유효는 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] (또는 이후 버전) 서버. DBPARAMFLAGS_SS_ISVARIABLESCALE은 하위 수준 서버에 연결 된 경우에 설정 하지 마십시오.  
  
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
  
 *bPrecision* 매개 변수가 무시 됩니다.  
  
 "DBPARAMFLAGS_SS_ISVARIABLESCALE"은 데이터를 서버로 보낼 때 무시됩니다. 응용 프로그램은 공급자별 유형 이름 "`datetime`" 및 "`smalldatetime`"을 사용하여 레거시 TDS(Tabular Data Stream) 유형의 사용을 강제할 수 있습니다. 에 연결 된 경우 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] (또는 이후 버전) 서버 "`datetime2`"형식이 사용 되도록 및 암시적 서버 변환이 발생 합니다, 필요한 경우 형식 이름이"`datetime2`" 또는 "DBTYPE_DBTIMESTAMP"입니다. *bScale* 는 공급자별 이름을 입력 하는 경우 무시 됩니다. "`datetime`"또는"`smalldatetime`" 사용 됩니다. 그렇지 않으면 응용 프로그램에서 되도록 해야 *bScale* 올바르게 설정 되어 있습니다. MDAC에서 업그레이드 된 응용 프로그램 및 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client에서 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 설정 하지 않은 경우 "DBTYPE_DBTIMESTAMP" 못합니다 사용 하는 *bScale* 정확 합니다. 에 서버 인스턴스에 연결 되어 있을 때 이전의 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], *bScale* 0 또는 "dbtype_dbtimestamp" 3이 아닌 값이는 오류 이며 E_FAIL이 반환 됩니다.  
  
 Icommandwithparameters:: Setparameterinfo를 호출 하지 않으면 iaccessor:: Createaccessor에 지정 된 바인딩 유형에 서 서버 공급자 유추 다음과 같이 입력 합니다.  
  
|바인딩 유형|*pwszDataSourceType*<br /><br /> (공급자별로 다름)|  
|------------------|----------------------------------------------------|  
|DBTYPE_DATE|datetime2(0)|  
|DBTYPE_DBDATE|날짜|  
|DBTYPE_DBTIME|time(0)|  
|DBTYPE_DBTIME2|time(7)|  
|DBTYPE_DBTIMESTAMP|datetime2(7)|  
|DBTYPE_DBTIMESTAMPOFFSET|datetimeoffset(7)|  
  
## <a name="icolumnsrowsetgetcolumnsrowset"></a>IColumnsRowset::GetColumnsRowset  
 `IColumnsRowset::GetColumnsRowset`은 다음 열을 반환합니다.  
  
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
  
 DBCOLUMNFLAGS_SS_ISVARIABLESCALE은만에 연결 된 경우 유효는 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] (또는 이후 버전) 서버. 하위 수준 서버에 연결된 경우에는 DBCOLUMNFLAGS_SS_ISVARIABLESCALE이 정의되지 않습니다.  
  
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
  
 *dwFlags*, DBCOLUMNFLAGS_ISFIXEDLENGTH는 항상 날짜/시간 형식에 대 한 true 및 다음과 같은 플래그는 항상 false:  
  
-   DBCOLUMNFLAGS_CACHEDEFERRED  
  
-   DBCOLUMNFLAGS_ISBOOKMARK  
  
-   DBCOLUMNFLAGS_ISCHAPTER  
  
-   DBCOLUMNFLAGS_ISLONG  
  
-   DBCOLUMNFLAGS_ISROWID  
  
-   DBCOLUMNFLAGS_ISROWVER, MAYDEFER  
  
 나머지 플래그(DBCOLUMNFLAGS_ISNULLABLE, DBCOLUMNFLAGS_MAYBENULL, DBCOLUMNFLAGS_WRITE 및 DBCOLUMNFLAGS_WRITEUNKNOWN)가 설정될 수 있습니다.  
  
 새 플래그 DBCOLUMNFLAGS_SS_ISVARIABLESCALE에 제공 된 *dwFlags* 응용 프로그램을 하는 열의 서버 유형을 확인할 수 있도록 여기서 *wType* 이 dbtype_dbtimestamp 인 합니다. *bScale* 서버 유형을 확인을 사용 해야 합니다.  
  
## <a name="see-also"></a>관련 항목  
 [메타 데이터 &#40;OLE DB&#41;](../../database-engine/dev-guide/metadata-ole-db.md)  
  
  