---
title: OLE DB 테이블 반환 매개 변수 형식 지원(메서드) | Microsoft Docs
description: OLE DB 테이블 반환 매개 변수 형식 지원(메서드)
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- table-valued parameters (OLE DB), API support (methods)
author: pmasl
ms.author: pelopes
manager: craigg
ms.openlocfilehash: 5607767674565c510fb10215b46b51a930d8a231
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47599112"
---
# <a name="ole-db-table-valued-parameter-type-support-methods"></a>OLE DB 테이블 반환 매개 변수 형식 지원(메서드)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  다음 표준 OLE DB 메서드는 테이블 반환 매개 변수를 지원합니다.  
  
|메서드|테이블 반환 매개 변수 지원|  
|------------|-------------------------------------|  
|ITableDefinitionWithConstraints::CreateTableWithConstraints|테이블 반환 매개 변수의 형식 정보를 알고 있으며 해당 형식 정보를 기반으로 테이블 반환 매개 변수 행 집합 개체를 인스턴스화하려는 경우 사용합니다.<br /><br /> 자세한 내용은 "정적 시나리오"를 참조 하세요 [테이블 반환 매개 변수 행 집합을 만들지](../../oledb/ole-db-table-valued-parameters/table-valued-parameter-rowset-creation.md)합니다.|  
|IOpenRowset::OpenRowset|테이블 반환 매개 변수의 형식 정보를 알지 못하며 서버에서 검색된 메타데이터 정보를 기반으로 테이블 반환 매개 변수 행 집합 개체를 인스턴스화하려는 경우 사용합니다.<br /><br /> 자세한 내용은 "동적 시나리오"를 참조 [테이블 반환 매개 변수 행 집합을 만들지](../../oledb/ole-db-table-valued-parameters/table-valued-parameter-rowset-creation.md)합니다.|  
|ISSCommandWithParameters::SetParameterInfo|테이블 반환 매개 변수의 명령 매개 변수를 지정하려면 소비자가 DBPARAMBINDINFO 구조체의 *pwszName* 멤버에서 매개 변수 형식을 "table" 또는 "DBTYPE_TABLE"로 지정합니다. 합니다 *ulParamSize* 로 ~ 0입니다. 자세한 내용은 "테이블 반환 매개 변수 사양"를 참조 하세요 [Executing Commands Containing Table-Valued 매개 변수](../../oledb/ole-db-table-valued-parameters/executing-commands-containing-table-valued-parameters.md)합니다.|  
|ISSCommandWithParameters::SetParameterProperties|스키마 이름, 유형 이름, 열 순서, 기본 열과 같은 테이블 반환 매개 변수와 관련된 속성을 설정합니다.<br /><br /> 소비자가 SSPARAMPROPS 구조체의 *iOrdinal*에서 매개 변수의 서수를 지정합니다. 요청되는 속성 집합은 DBPROPSET_SQLSERVERPARAMETER입니다.|  
|ISSCommandWithParameters::GetParameterInfo|모든 매개 변수 형식을 지정된 명령으로 가져옵니다.<br /><br /> 테이블 반환 매개 변수의 경우 DBPARAMINFO 구조체의 *wType* 필드는 DBTYPE_TABLE 형식이 됩니다. *ulParamSize* 필드는 알 수 없는 길이를 나타내는 ~0으로 설정됩니다.|  
|ISSCommandWithParameters::GetParameterProperties|DBTYPE_TABLE 형식의 매개 변수에 대한 추가적인 형식 정보를 가져옵니다.<br /><br /> 소비자가 SSPARAMPROPS 구조체의 *iOrdinal* 멤버에서 매개 변수의 서수를 지정합니다. 소비자는 isscommandwithparameters:: Setparameterproperties 아래 나열 되어 있는 DBPROPSET_SQLSERVERPARAMETER 속성 집합의 속성 중 하나를 요청할 수 있습니다.<br /><br /> 소비자가 테이블 반환 매개 변수 형식을 알 수 없기 때문에 공급자가 SSPROP_PARAM_TYPE_TYPENAME, SSPROP_PARAM_TYPE_SCHEMANAME 및 SSPROP_PARAM_TYPE_CATALOGNAME을 올바른 값으로 설정해야 합니다. 나머지 SSPROP_PARAM_TABLE_DEFAULT_COLUMNS 및 SSPROP_PARAM_TABLE_COLUMN_SORT_ORDER 속성에는 기본값이 사용됩니다. 소비자는 테이블 반환 매개 변수 형식 이름을 검색한 후 IOpenRowset::OpenRowset을 사용하여 테이블 반환 매개 변수 형식을 지정함으로써 이 테이블 반환 매개 변수의 인스턴스를 생성합니다. 자세한 내용은 [테이블 반환 매개 변수 형식 검색](../../oledb/ole-db-table-valued-parameters/table-valued-parameter-type-discovery.md)합니다.|  
|Irowsetinfo:: Getproperties|테이블 반환 매개 변수 행 집합 속성을 가져옵니다. 소비자는 이 속성을 사용하여 최적의 바인딩을 설정할 수 있습니다.|  
|IColumnsRowset::GetColumnsRowset|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 테이블에 대한 메타데이터 정보를 검색합니다. 테이블 반환 매개 변수의 경우에는 동일한 인터페이스에서 다음과 같은 각 열에 대한 자세한 메타데이터 정보를 제공합니다.<br /><br /> DBCOLUMN_FLAGS는 DBCOLUMNFLAGS_ISNULLABLE 비트를 통해 Null 허용 여부를 나타냅니다.<br /><br /> DBCOLUMN_ISUNIQUE는 열이 ID 열인지 여부를 나타냅니다.<br /><br /> DBCOLUMN_COMPUTEMODE는 열이 계산되는지 여부를 나타냅니다.|  
|Iaccessor:: Createaccessor|테이블 반환 매개 변수 행 집합 개체를 명령 매개 변수에 바인딩하려면 해당 *wType* 멤버를 DBTYPE_TABLE로 설정하여 접근자를 만듭니다. DBOBJECT 구조체에는 IID_IRowset 또는 *iid* 멤버의 기타 유효한 행 집합 개체 인터페이스가 포함됩니다. 나머지 필드는 DBTYPE_IUNKNOWN과 유사하게 처리됩니다.|  
  
## <a name="see-also"></a>참고 항목  
 [OLE DB 테이블 반환 매개 변수 형식 지원](../../oledb/ole-db-table-valued-parameters/ole-db-table-valued-parameter-type-support.md)   
 [테이블 반환 매개 변수 행 집합 만들기](../../oledb/ole-db-table-valued-parameters/table-valued-parameter-rowset-creation.md)   
 [테이블 반환 매개 변수&#40;OLE DB&#41; 사용](../../oledb/ole-db-how-to/use-table-valued-parameters-ole-db.md)  
  
  
