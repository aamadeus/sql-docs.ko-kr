---
title: 스파스 열 지원 (OLE DB) | Microsoft Docs
description: 스파스 열 지원 (OLE DB)
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: ole-db
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: reference
author: pmasl
ms.author: Pedro.Lopes
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 327c98688395be4afd5381387be6b6675eae3981
ms.sourcegitcommit: 9351e8b7b68f599a95fb8e76930ab886db737e5f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2018
---
# <a name="sparse-columns-support-ole-db"></a>스파스 열 지원(OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  이 항목에서는 스파스 열에 대 한 SQL Server 지원에 대 한 OLE DB 드라이버에 대 한 정보를 제공 합니다. 스파스 열에 대 한 자세한 내용은 참조 [OLE DB Driver for SQL Server의에서 스파스 열 지원](../../oledb/features/sparse-columns-support-in-oledb-driver-for-sql-server.md)합니다. 샘플을 보려면 [표시 열 및 스파스 열의 카탈로그 메타 데이터 &#40;OLE DB&#41;](../../oledb/ole-db-how-to/display-column-and-catalog-metadata-for-sparse-columns-ole-db.md)합니다.  
  
## <a name="ole-db-statement-metadata"></a>OLE DB 문 메타데이터  
 [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)]부터 새 DBCOLUMNFLAGS 플래그 값인 DBCOLUMNFLAGS_SS_ISCOLUMNSET을 사용할 수 있습니다. 이 값은 열에 대 한 설정 **column_set** 값입니다. DBCOLUMNFLAGS 플래그를 통해 검색할 수 있습니다는 *dwFlags* icolumnsrowset:: Getcolumnsrowset에서 반환 된 행 집합의 DBCOLUMN_FLAGS 열과 icolumnsinfo:: Getcolumnsinfo의 매개 변수입니다.  
  
## <a name="ole-db-catalog-metadata"></a>OLE DB 카탈로그 메타데이터  
 DBSCHEMA_COLUMNS에는 다음과 같은 두 개의 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 특정 열이 새로 추가되었습니다.  
  
|열 이름|데이터 형식|값/설명|  
|-----------------|---------------|---------------------|  
|SS_IS_SPARSE|DBTYPE_BOOL|열이 스파스 열이면 VARIANT_TRUE 값을 갖고, 그렇지 않으면 VARIANT_FALSE 값을 갖습니다.|  
|SS_IS_COLUMN_SET|DBTYPE_BOOL|열이 스파스 **column_set** 열에 VARIANT_TRUE 값을 갖고, 그렇지 않으면 VARIANT_FALSE입니다.|  
  
 또한 다음과 같은 두 개의 스키마 행 집합도 새로 추가되었습니다. 이러한 행 집합은 DBSCHEMA_COLUMNS와 구조가 동일하지만 다른 내용을 반환합니다. DBSCHEMA_COLUMNS_EXTENDED에 관계 없이 모든 열을 반환 **column_set** 멤버 자격입니다. DBSCHEMA_SPARSE_COLUMN_SET은 스파스의 멤버인 열만 반환 **column_set**합니다.  
  
## <a name="ole-db-datatypecompatibility-behavior"></a>OLE DB DataTypeCompatibility 동작  
 에 대 한 동작 **DataTypeCompatibility = 80** (연결 문자열)는와 일치 한 [!INCLUDE[ssVersion2000](../../../includes/ssversion2000-md.md)] 다음과 같이 클라이언트:  
  
-   새 스키마 행 집합이 표시되지 않으며 스키마 행 집합의 행 집합에 이러한 행 집합에 대한 행이 없습니다.  
  
-   COLUMNS 행 집합의 새 열이 표시되지 않습니다.  
  
-   에 대 한 DBCOLUMNFLAGS_SS_ISCOLUMNSET이 설정 되지 않은 **column_set** 열입니다.  
  
-   DBCOMPUTEMODE_NOTCOMPUTED에 대해 설정 된 **column_set** 열입니다.  
  
## <a name="ole-db-support-for-sparse-columns"></a>스파스 열에 대한 OLE DB 지원  
 다음 OLE DB 인터페이스는 OLE DB Driver for SQL Server 스파스 열을 지원 하도록에서 수정 되었습니다.  
  
|유형 또는 멤버 함수|Description|  
|-----------------------------|-----------------|  
|IColumnsInfo::GetColumnsInfo|새 DBCOLUMNFLAGS 플래그 값인 DBCOLUMNFLAGS_SS_ISCOLUMNSET이에 대해 설정 된 **column_set** 열 *dwFlags*합니다.<br /><br /> 에 대해 설정 된 DBCOLUMNFLAGS_WRITE **column_set** 열입니다.|  
|IColumsRowset::GetColumnsRowset|에 새 DBCOLUMNFLAGS 플래그 값인 dbcolumnflags_ss_iscolumnset이 설정 되어 **column_set** DBCOLUMN_FLAGS의 열입니다.<br /><br /> DBCOLUMN_COMPUTEMODE에 DBCOMPUTEMODE_DYNAMIC로 설정 되어 **column_set** 열입니다.|  
|IDBSchemaRowset::GetSchemaRowset|Dbschema_columns는 두 개의 새 열: SS_IS_COLUMN_SET과 ss_is_sparse를 반환 합니다.<br /><br /> DBSCHEMA_COLUMNS의 멤버가 아닌 열만 반환는 **column_set**합니다.<br /><br /> 추가 된 두 개의 새로운 스키마 행 집합: DBSCHEMA_COLUMNS_EXTENDED는의 스파스 여부에 관계 없이 모든 열을 반환 **column_set** 멤버 자격입니다. DBSCHEMA_SPARSE_COLUMN_SET의 멤버인 열만 반환는 **column_set**합니다. 이러한 새 행 집합은 DBSCHEMA_COLUMNS와 동일한 열과 제한 사항을 갖습니다.|  
|IDBSchemaRowset::GetSchemas|Idbschemarowset:: Getschemas 사용 가능한 스키마 행 집합 목록에 새 행 집합, DBSCHEMA_COLUMNS_EXTENDED 및 DBSCHEMA_SPARSE_COLUMN_SET에 대 한 Guid를 포함합니다.|  
|ICommand::Execute|경우 **선택 \* 에서** *테이블* 은 스파스의 멤버가 아닌 모든 열의 반환을 사용 하는 **column_set**, 모든 값이 포함 된 XML 열 null이 아닌 열은 스파스의 구성원 인 **column_set**있을 경우.|  
|IOpenRowset::OpenRowset|Iopenrowset:: Openrowset와 icommand:: Execute, 같은 열이 있는 행 집합 반환을 **선택 \***  동일한 테이블에 대 한 쿼리 합니다.|  
|ITableDefinition|이 인터페이스 또는 스파스 열에 변경 내용이 없는지 **column_set** 열입니다. 스키마를 수정해야 하는 응용 프로그램에서는 적절한 [!INCLUDE[tsql](../../../includes/tsql-md.md)]을 직접 실행해야 합니다.|  
  
## <a name="see-also"></a>관련 항목:  
 [OLE DB Driver for SQL Server &#40;OLE DB&#41;](../../oledb/ole-db/oledb-driver-for-sql-server-ole-db.md)  
  
  