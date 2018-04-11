---
title: SSVARIANT 구조 | Microsoft Docs
description: OLE DB Driver for SQL Server에에서 SSVARIANT 구조
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: ole-db-data-types
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- SSVARIANT
helpviewer_keywords:
- SSVARIANT struct
author: pmasl
ms.author: Pedro.Lopes
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 797c10dfeabd1361395c5416f65c88a0d6c82176
ms.sourcegitcommit: 9f4330a4b067deea396b8567747a6771f35e6eee
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/30/2018
---
# <a name="ssvariant-structure"></a>SSVARIANT 구조
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  **SSVARIANT** msoledbsql.h에 정의 된 구조를 SQL Server 용 OLE DB 드라이버에서 DBTYPE_SQLVARIANT 값에 해당 합니다.  
  
 **SSVARIANT** 는 판별 구조체입니다. Vt 멤버의 값에 따라 소비자는 읽을 멤버를 결정할 수 있습니다. vt 값에 해당 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 데이터 형식입니다. 따라서는 **SSVARIANT** 구조는 모든 SQL Server 형식을 보유할 수 있습니다. 표준 OLE DB 형식에 대 한 데이터 구조에 대 한 자세한 내용은 참조 [유형 표시기](http://go.microsoft.com/fwlink/?LinkId=122171)합니다.  
  
## <a name="remarks"></a>주의  
 때 DataTypeCompat = = 80, 여러 **SSVARIANT** 하위 유형이 문자열이 됩니다. 다음 vt 값에 표시 됩니다는 예를 들어 **SSVARIANT** VT_SS_WVARSTRING으로 나타납니다.  
  
-   VT_SS_DATETIMEOFFSET  
  
-   VT_SS_DATETIME2  
  
-   VT_SS_TIME2  
  
-   VT_SS_DATE  
  
 DateTypeCompat == 0인 경우, 이러한 유형은 네이티브 형식으로 나타납니다.  
  
 SSPROP_INIT_DATATYPECOMPATIBILITY에 대 한 자세한 내용은 참조 [OLE DB 드라이버와 SQL Server에 대 한 연결 문자열 키워드를 사용 하 여](../../oledb/applications/using-connection-string-keywords-with-oledb-driver-for-sql-server.md)합니다.  
  
 멤버 유형 역참조를 단순화 하는 변형 액세스 매크로가 msoledbsql.h 파일에 포함 되어는 **SSVARIANT** 구조입니다. 예로는 다음과 같이 사용 가능한 V_SS_DATETIMEOFFSET가 있습니다.  
  
```  
memcpy(&V_SS_DATETIMEOFFSET(pssVar).tsoDateTimeOffsetVal, pDTO, cbNative);  
V_SS_DATETIMEOFFSET(pssVar).bScale = bScale;  
```  
  
 각 멤버에 대 한 액세스 매크로 전체 집합에 대 한는 **SSVARIANT** 구조 msoledbsql.h 파일을 참조 하십시오.  
  
 멤버를 설명 하는 다음 표에서 **SSVARIANT** 구조:  
  
|멤버|OLE DB 유형 표시기|OLE DB C 데이터 형식|vt 값|주석|  
|------------|---------------------------|------------------------|--------------|--------------|  
|vt|SSVARTYPE|||에 포함 된 값의 형식을 지정 된 **SSVARIANT** 구조체입니다.|  
|bTinyIntVal|DBTYPE_UI1|**BYTE**|**VT_SS_UI1**|지원 된 **tinyint** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 데이터 형식입니다.|  
|sShortIntVal|DBTYPE_I2|**짧은**|**VT_SS_I2**|지원 된 **smallint** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 데이터 형식입니다.|  
|lIntVal|DBTYPE_I4|**긴**|**VT_SS_I4**|지원 된 **int** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 데이터 형식입니다.|  
|llBigIntVal|DBTYPE_I8|**LARGE_INTEGER**|**VT_SS_I8**|지원 된 **bigint** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 데이터 형식입니다.|  
|fltRealVal|DBTYPE_R4|**float**|**VT_SS_R4**|지원 된 **실제** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 데이터 형식입니다.|  
|dblFloatVal|DBTYPE_R8|**double**|**VT_SS_R8**|지원 된 **float** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 데이터 형식입니다.|  
|cyMoneyVal|DBTYPE_CY|**LARGE_INTEGER**|**VT_SS_MONEY VT_SS_SMALLMONEY**|지원 된 **money** 및 **smallmoney** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 데이터 형식입니다.|  
|fBitVal|DBTYPE_BOOL|**VARIANT_BOOL**|**VT_SS_BIT**|지원 된 **비트** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 데이터 형식입니다.|  
|rgbGuidVal|DBTYPE_GUID|**GUID**|**VT_SS_GUID**|지원 된 **uniqueidentifier** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 데이터 형식입니다.|  
|numNumericVal|DBTYPE_NUMERIC|**DB_NUMERIC**|**VT_SS_NUMERIC**|지원 된 **숫자** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 데이터 형식입니다.|  
|dDateVal|DBTYPE_DATE|**DBDATE**|**VT_SS_DATE**|지원 된 **날짜** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 데이터 형식입니다.|  
|tsDateTimeVal|DBTYPE_DBTIMESTAMP|**DBTIMESTAMP**|**VT_SS_SMALLDATETIME VT_SS_DATETIME VT_SS_DATETIME2**|지원 된 **smalldatetime**, **datetime**, 및 **datetime2** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 데이터 형식입니다.|  
|Time2Val|DBTYPE_DBTIME2|**DBTIME2**|**VT_SS_TIME2**|지원 된 **시간** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 데이터 형식입니다.<br /><br /> 포함되는 멤버는 다음과 같습니다.<br /><br /> *tTime2Val* (**DBTIME2**)<br /><br /> *bScale* (**바이트**)에 대 한 소수 자릿수를 지정 *tTime2Val* 값입니다.|  
|DateTimeVal|DBTYPE_DBTIMESTAMP|**DBTIMESTAMP**|**VT_SS_DATETIME2**|지원 된 **datetime2** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 데이터 형식입니다.<br /><br /> 포함되는 멤버는 다음과 같습니다.<br /><br /> *tsDataTimeVal* (DBTIMESTAMP)<br /><br /> *bScale* (**바이트**)에 대 한 소수 자릿수를 지정 *tsDataTimeVal* 값입니다.|  
|DateTimeOffsetVal|DBTYPE_DBTIMESTAMPOFSET|**DBTIMESTAMPOFFSET**|**VT_SS_DATETIMEOFFSET**|지원 된 **datetimeoffset** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 데이터 형식입니다.<br /><br /> 포함되는 멤버는 다음과 같습니다.<br /><br /> *tsoDateTimeOffsetVal* (**DBTIMESTAMPOFFSET**)<br /><br /> *bScale* (**바이트**)에 대 한 소수 자릿수를 지정 *tsoDateTimeOffsetVal* 값입니다.|  
|NCharVal|해당하는 OLE DB 유형 표시기 없음|**struct _NCharVal**|**VT_SS_WVARSTRING,**<br /><br /> **VT_SS_WSTRING**|지원 된 **nchar** 및 **nvarchar** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 데이터 형식입니다.<br /><br /> 포함되는 멤버는 다음과 같습니다.<br /><br /> *sActualLength* (**짧은**) 문자열에 대 한 실제 길이 지정 *pwchNCharVal* 포인트입니다. 이 값은 0으로 끝나지 않습니다.<br /><br /> *sMaxLength* (**짧은**) 문자열에 대 한 최대 길이 지정 *pwchNCharVal* 포인트입니다.<br /><br /> *pwchNCharVal* (**WCHAR** \*) 문자열에 대 한 포인터입니다.<br /><br /> 사용 되지 않은 멤버: *rgbReserved*, *dwReserved*, 및 *pwchReserved*합니다.|  
|CharVal|해당하는 OLE DB 유형 표시기 없음|**struct _CharVal**|**VT_SS_STRING,**<br /><br /> **VT_SS_VARSTRING**|지원 된 **char** 및 **varchar** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 데이터 형식입니다.<br /><br /> 포함되는 멤버는 다음과 같습니다.<br /><br /> *sActualLength* (**짧은**) 하는 문자열에 대 한 실제 길이 지정 *pchCharVal* 포인트입니다. 이 값은 0으로 끝나지 않습니다.<br /><br /> *sMaxLength* (**짧은**) 하는 문자열에 대 한 최대 길이 지정 *pchCharVal* 포인트입니다.<br /><br /> *pchCharVal* (**CHAR** \*) 문자열에 대 한 포인터입니다.<br /><br /> 사용되지 않은 멤버:<br /><br /> *rgbReserved*, *dwReserved*, 및 *pwchReserved*합니다.|  
|BinaryVal|해당하는 OLE DB 유형 표시기 없음|**struct _BinaryVal**|**VT_SS_VARBINARY,**<br /><br /> **VT_SS_BINARY**|지원 된 **이진** 및 **varbinary** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 데이터 형식입니다.<br /><br /> 포함되는 멤버는 다음과 같습니다.<br /><br /> *sActualLength* (**짧은**)를 데이터에 대 한 실제 길이 지정 *prgbBinaryVal* 포인트입니다.<br /><br /> *sMaxLength* (**짧은**)를 데이터에 대 한 최대 길이 지정 *prgbBinaryVal* 포인트입니다.<br /><br /> *prgbBinaryVal* (**바이트** \*) 이진 데이터에 대 한 포인터입니다.<br /><br /> 사용 되지 않은 멤버: *dwReserved*합니다.|  
|알려지지 않은 유형|UNUSED|UNUSED|UNUSED|UNUSED|  
|BLOBType|UNUSED|UNUSED|UNUSED|UNUSED|  
  
## <a name="see-also"></a>참고 항목  
 [데이터 형식 &#40; OLE db&#41;](../../oledb/ole-db-data-types/data-types-ole-db.md)  
  
  