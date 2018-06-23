---
title: 사용자 정의 형식을 사용 하 여 | Microsoft Docs
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
- DBPROPSET_DATASOURCEINFO property set
- UDTs [SQL Server Native Client]
- user-defined types [SQL Server], SQL Server Native Client
- SQL Server Native Client OLE DB provider, user-defined types
- DBPROPSET_SQLSERVERPARAMETER property set
- IColumnsRowset interface
- SQLNCLI, user-defined types
- SQL Server Native Client, user-defined types
- data access [SQL Server Native Client], user-defined types
- ISSCommandWithParameters interface
ms.assetid: e15d8169-3517-4323-9c9e-0f5c34aff7df
caps.latest.revision: 45
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: eaa97c4322c59c0ffc77f42cfe9e147ca7dc276b
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36181125"
---
# <a name="using-user-defined-types"></a>사용자 정의 형식 사용
  [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]부터 UDT(사용자 정의 형식)가 도입되었습니다. Udt 개체 및 사용자 지정 데이터 구조에 데이터를 저장할 수 있으므로 SQL 형식 시스템이 확장는 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 데이터베이스입니다. UDT는 여러 데이터 형식과 동작이 포함될 수 있어 단일 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 시스템 데이터 형식으로 구성된 일반적인 별칭 데이터 형식과 차별화됩니다. UDT는 검증할 수 있는 코드를 생성하는 .NET CLR(공용 언어 런타임)에서 지원하는 모든 언어를 사용하여 정의합니다. 여기에 Microsoft Visual C#<sup>®</sup> 및 Visual Basic<sup>®</sup> .NET 합니다. 데이터는 .NET 클래스 또는 구조체의 필드와 속성으로 노출되며 동작은 클래스 또는 구조체의 메서드로 정의됩니다.  
  
 UDT의 변수는 테이블의 열 정의로 사용할 수 있습니다는 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 일괄 처리 또는의 인수로 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 함수 또는 저장된 프로시저입니다.  
  
## <a name="sql-server-native-client-ole-db-provider"></a>SQL Server Native Client OLE DB 공급자  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB 공급자는 Udt를 개체로 관리할 수 있는 메타 데이터 정보를 사용 하는 이진 형식으로 Udt를 지원 합니다. UDT 열은 DBTYPE_UDT로 노출 되 고 해당 메타 데이터는 핵심 OLE DB 인터페이스를 통해 노출 되 **IColumnRowset**와 새 [ISSCommandWithParameters](../../native-client-ole-db-interfaces/isscommandwithparameters-ole-db.md) 인터페이스입니다.  
  
> [!NOTE]  
>  **irowsetfind:: Findnextrow** UDT 데이터 형식과 메서드가 작동 하지 않습니다. UDT가 검색 열 유형으로 사용되는 경우 DB_E_BADCOMPAREOP가 반환됩니다.  
  
### <a name="data-bindings-and-coercions"></a>데이터 바인딩 및 강제 변환  
 다음 표에서는 표의 데이터 형식을 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] UDT와 함께 사용할 때 발생하는 바인딩 및 강제 변환에 대해 설명합니다. UDT 열을 통해 노출 되는 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] DBTYPE_UDT로 Native Client OLE DB 공급자입니다. 적절한 스키마의 행 집합을 통해 메타데이터를 얻을 수 있으므로 사용자 정의 형식을 개체로 관리할 수 있습니다.  
  
|데이터 형식|SQL Server의<br /><br /> **UDT**|SQL Server의<br /><br /> **non-UDT**|SQL Server의<br /><br /> **UDT**|SQL Server의<br /><br /> **non-UDT**|  
|---------------|---------------------------|--------------------------------|-----------------------------|----------------------------------|  
|DBTYPE_UDT|지원<sup>6</sup>|오류<sup>1</sup>|지원<sup>6</sup>|오류<sup>5</sup>|  
|DBTYPE_BYTES|지원<sup>6</sup>|해당 없음<sup>2</sup>|지원<sup>6</sup>|해당 없음<sup>2</sup>|  
|DBTYPE_WSTR|지원<sup>3,6</sup>|해당 없음<sup>2</sup>|지원<sup>4,6</sup>|해당 없음<sup>2</sup>|  
|DBTYPE_BSTR|지원<sup>3,6</sup>|해당 없음<sup>2</sup>|지원<sup>4</sup>|해당 없음<sup>2</sup>|  
|DBTYPE_STR|지원<sup>3,6</sup>|해당 없음<sup>2</sup>|지원<sup>4,6</sup>|해당 없음<sup>2</sup>|  
|DBTYPE_IUNKNOWN|지원되지 않음|해당 없음<sup>2</sup>|지원되지 않음|해당 없음<sup>2</sup>|  
|DBTYPE_VARIANT (VT_UI1 &AMP;#124; VT_ARRAY)|지원<sup>6</sup>|해당 없음<sup>2</sup>|지원<sup>4</sup>|해당 없음<sup>2</sup>|  
|DBTYPE_VARIANT (VT_BSTR)|지원<sup>3,6</sup>|해당 없음<sup>2</sup>|해당 사항 없음|해당 없음<sup>2</sup>|  
  
 <sup>1</sup>서버 이외의 유형이 DBTYPE_UDT로 지정 **icommandwithparameters:: Setparameterinfo** 접근자 유형이 DBTYPE_UDT 인 이며 문이 실행 될 때 오류가 발생 (DB_E_ERRORSOCCURRED, 매개 변수 상태는 DBSTATUS_E_BADACCESSOR). 그렇지 않은 경우에는 데이터가 서버로 전송되지만 UDT에서 매개 변수의 데이터 형식으로의 암시적 변환이 이루어지지 않았음을 나타내는 오류가 반환됩니다.  
  
 <sup>2</sup>이 항목의 범위를 초과 합니다.  
  
 <sup>3</sup> 16 진수 문자열에서 이진 데이터에 데이터 변환이 발생 합니다.  
  
 <sup>4</sup> 16 진수 문자열로 이진 데이터에서 데이터 변환이 발생 합니다.  
  
 <sup>5</sup>접근자 생성 시간 또는 인출 시간에이 오류는 DB_E_ERRORSOCCURRED이 고 바인딩 상태는 DBBINDSTATUS_UNSUPPORTEDCONVERSION으로 설정 유효성 검사에서 발생할 수 있습니다.  
  
 <sup>6</sup>by_ref가 사용 될 수 있습니다.  
  
 DBTYPE_NULL 및 DBTYPE_EMPTY는 입력 매개 변수에 대해서는 바인딩할 수 있지만 출력 매개 변수나 결과에 대해서는 바인딩할 수 없습니다. 입력 매개 변수에 대해 바인딩할 경우 상태를 DBSTATUS_S_ISNULL 또는 DBSTATUS_S_DEFAULT로 설정해야 합니다.  
  
 DBTYPE_UDT를 DBTYPE_EMPTY와 DBTYPE_NULL로 변환할 수 있지만 DBTYPE_NULL 및 DBTYPE_EMPTY는 DBTYPE_UDT로 변환할 수 없습니다. 이는 DBTYPE_BYTES와 일치합니다.  
  
> [!NOTE]  
>  Udt 매개 변수로 처리 하기 위한 새로운 인터페이스는 **ISSCommandWithParameters**에서 상속한 **ICommandWithParameters**합니다. 응용 프로그램은 이 인터페이스를 사용하여 UDT 매개 변수에 대해 적어도 DBPROPSET_SQLSERVERPARAMETER 속성 집합의 SSPROP_PARAM_UDT_NAME을 설정해야 합니다. 이렇게 하지 않으면 **icommand:: Execute** 가 DB_E_ERRORSOCCURRED를 반환 합니다. 이 인터페이스와 속성 집합에 대해서는 이 항목의 뒷부분에서 설명합니다.  
  
 사용자 정의 형식의 모든 데이터를 보관 하기에 충분 하지 않은 열에 삽입 되 **icommand:: Execute** DB_E_ERRORSOCCURRED 상태와 함께 S_OK를 반환 합니다.  
  
 OLE DB 핵심 서비스에서 제공 하는 데이터 변환 (**IDataConvert**) DBTYPE_UDT에 적용 되지 않습니다. 다른 바인딩은 지원되지 않습니다.  
  
### <a name="ole-db-rowset-additions-and-changes"></a>OLE DB 행 집합의 추가 내용 및 변경 내용  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client는 새 값을 추가 하거나 많은 핵심 OLE DB 스키마 행 집합을 변경 합니다.  
  
#### <a name="the-procedureparameters-schema-rowset"></a>PROCEDURE_PARAMETERS 스키마 행 집합  
 PROCEDURE_PARAMETERS 스키마 행 집합에 다음이 추가되었습니다.  
  
|열 이름|형식|Description|  
|-----------------|----------|-----------------|  
|SS_UDT_CATALOGNAME|DBTYPE_WSTR|세 부분으로 구성된 이름 식별자입니다.|  
|SS_UDT_SCHEMANAME|DBTYPE_WSTR|세 부분으로 구성된 이름 식별자입니다.|  
|SS_UDT_NAME|DBTYPE_WSTR|세 부분으로 구성된 이름 식별자입니다.|  
|SS_UDT_ASSEMBLY_TYPENAME|DBTYPE_WSTR|CLR이 참조하는 데 필요한 형식 이름과 모든 어셈블리 ID를 포함하는 어셈블리의 정규화된 이름입니다.|  
  
#### <a name="the-sqlassemblies-schema-rowset"></a>SQL_ASSEMBLIES 스키마 행 집합  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB 공급자는 등록된 된 Udt를 설명 하는 새 공급자 특정 스키마 행 집합을 노출 합니다. ASSEMBLY 서버가 DBTYPE_WSTR로 지정되지만 행 집합에는 없을 수 있습니다. 이 속성이 지정되지 않은 경우 행 집합은 기본적으로 현재 서버를 사용합니다. SQL_ASSEMBLIES 스키마 행 집합은 다음 표에 정의되어 있습니다.  
  
|열 이름|형식|Description|  
|-----------------|----------|-----------------|  
|ASSEMBLY_CATALOG|DBTYPE_WSTR|형식을 포함하는 어셈블리의 카탈로그 이름입니다.|  
|ASSEMBLY_SCHEMA|DBTYPE_WSTR|형식을 포함하는 어셈블리의 스키마 이름 또는 소유자 이름입니다. 어셈블리 범위는 스키마가 아니라 데이터베이스에 의해 결정되지만 여전히 여기에서 나타내는 소유자를 가집니다.|  
|ASSEMBLY_NAME|DBTYPE_WSTR|형식을 포함하는 어셈블리의 이름입니다.|  
|ASSEMBLY_ID|DBTYPE_UI4|형식을 포함하는 어셈블리의 개체 ID입니다.|  
|PERMISSION_SET|DBTYPE_WSTR|어셈블리의 액세스 범위를 나타내는 값입니다. 값에는 "SAFE", "EXTERNAL_ACCESS" 및 "UNSAFE"가 포함됩니다.|  
|ASSEMBLY_BINARY|DBTYPE_BYTES|어셈블리의 이진 표현입니다.|  
  
#### <a name="the-sqlassemblies-dependencies-schema-rowset"></a>SQL_ASSEMBLIES_ DEPENDENCIES 스키마 행 집합  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB 공급자는 지정 된 서버의 어셈블리 종속성을 설명 하는 새 공급자별 스키마 행 집합을 노출 합니다. ASSEMBLY_SERVER가 호출자에 의해 DBTYPE_WSTR로 지정되지만 행 집합에는 없을 수 있습니다. 이 속성이 지정되지 않은 경우 행 집합은 기본적으로 현재 서버를 사용합니다. SQL_ASSEMBLY_DEPENDENCIES 스키마 행 집합은 다음 표에 정의되어 있습니다.  
  
|열 이름|형식|Description|  
|-----------------|----------|-----------------|  
|ASSEMBLY_CATALOG|DBTYPE_WSTR|형식을 포함하는 어셈블리의 카탈로그 이름입니다.|  
|ASSEMBLY_SCHEMA|DBTYPE_WSTR|형식을 포함하는 어셈블리의 스키마 이름 또는 소유자 이름입니다. 어셈블리 범위는 스키마가 아니라 데이터베이스에 의해 결정되지만 여전히 여기에서 나타내는 소유자를 가집니다.|  
|ASSEMBLY_ID|DBTYPE_UI4|어셈블리의 개체 ID입니다.|  
|REFERENCED_ASSEMBLY_ID|DBTYPE_UI4|참조된 어셈블리의 개체 ID입니다.|  
  
#### <a name="the-sqlusertypes-schema-rowset"></a>SQL_USER_TYPES 스키마 행 집합  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB 공급자 새로운 스키마 행 집합, 경우에 대해 설명 하는 SQL_USER_TYPES를 노출 합니다. 지정 된 서버의 등록된 된 Udt가 추가 됩니다. UDT_SERVER가 호출자에 의해 DBTYPE_WSTR로 지정되어야 하지만 행 집합에는 없을 수 있습니다. SQL_USER_TYPES 스키마 행 집합은 다음 표에 정의되어 있습니다.  
  
|열 이름|형식|Description|  
|-----------------|----------|-----------------|  
|UDT_CATALOGNAME|DBTYPE_WSTR|UDT 열의 경우 이 속성이 UDT가 정의되어 있는 카탈로그의 이름을 지정하는 문자열입니다.|  
|UDT_SCHEMANAME|DBTYPE_WSTR|UDT 열의 경우 이 속성이 UDT가 정의되어 있는 스키마의 이름을 지정하는 문자열입니다.|  
|UDT_NAME|DBTYPE_WSTR|UDT 클래스가 포함된 어셈블리의 이름입니다.|  
|UDT_ASSEMBLY_TYPENAME|DBTYPE_WSTR|전체 형식 이름(AQN)은 적용 가능한 경우 네임스페이스에 따른 접두사가 추가된 형식 이름을 포함합니다.|  
  
#### <a name="the-columns-schema-rowset"></a>COLUMNS 스키마 행 집합  
 COLUMNS 스키마 행 집합에 추가된 열은 다음과 같습니다.  
  
|열 이름|형식|Description|  
|-----------------|----------|-----------------|  
|SS_UDT_CATALOGNAME|DBTYPE_WSTR|UDT 열의 경우 이 속성이 UDT가 정의되어 있는 카탈로그의 이름을 지정하는 문자열입니다.|  
|SS_UDT_SCHEMANAME|DBTYPE_WSTR|UDT 열의 경우 이 속성이 UDT가 정의되어 있는 스키마의 이름을 지정하는 문자열입니다.|  
|SS_UDT_NAME|DBTYPE_WSTR|UDT의 이름입니다.|  
|SS_UDT_ASSEMBLY_TYPENAME|DBTYPE_WSTR|전체 형식 이름(AQN)은 적용 가능한 경우 네임스페이스에 따른 접두사가 추가된 형식 이름을 포함합니다.|  
  
### <a name="ole-db-property-set-additions-and-changes"></a>OLE DB 속성 집합의 추가 내용 및 변경 내용  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client에는 많은 핵심 OLE DB 속성 집합 변경 이나 새 값을 추가 합니다.  
  
#### <a name="the-dbpropsetsqlserverparameter-property-set"></a>DBPROPSET_SQLSERVERPARAMETER 속성 집합  
 OLE DB를 통해 Udt를 지원 하기 위해 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client는 다음 값을 포함 된 새로운 DBPROPSET_SQLSERVERPARAMETER 속성 집합을 구현 합니다.  
  
|속성|형식|Description|  
|----------|----------|-----------------|  
|SSPROP_PARAM_UDT_CATALOGNAME|DBTYPE_WSTR|세 부분으로 구성된 이름 식별자입니다.<br /><br /> UDT 매개 변수의 경우 이 속성이 사용자 정의 형식이 정의되어 있는 카탈로그의 이름을 지정하는 문자열입니다.|  
|SSPROP_PARAM_UDT_SCHEMANAME|DBTYPE_WSTR|세 부분으로 구성된 이름 식별자입니다.<br /><br /> UDT 매개 변수의 경우 이 속성이 사용자 정의 형식이 정의되어 있는 스키마의 이름을 지정하는 문자열입니다.|  
|SSPROP_PARAM_UDT_NAME|DBTYPE_WSTR|세 부분으로 구성된 이름 식별자입니다.<br /><br /> UDT 열의 경우 이 속성이 사용자 정의 형식의 단일 부분으로 구성된 이름을 지정하는 문자열입니다.|  
  
 SSPROP_PARAM_UDT_NAME은 필수입니다. SSPROP_PARAM_UDT_CATALOGNAME 및 SSPROP_PARAM_UDT_SCHEMANAME은 옵션입니다. 이러한 속성 중 하나가 잘못 지정되면 DB_E_ERRORSINCOMMAND가 반환됩니다. SSPROP_PARAM_UDT_CATALOGNAME 및 SSPROP_PARAM_UDT_SCHEMANAME이 모두 지정되지 않은 경우 테이블과 동일한 데이터베이스와 스키마에서 UDT를 정의해야 합니다. UDT 정의가 테이블과 동일한 데이터베이스에 속하지만 다른 스키마에 속하는 경우 SSPROP_PARAM_UDT_SCHEMANAME을 지정해야 합니다. UDT 정의가 다른 데이터베이스에 속하는 경우 SSPROP_PARAM_UDT_CATALOGNAME 및 SSPROP_PARAM_UDT_SCHEMANAME을 모두 지정해야 합니다.  
  
#### <a name="the-dbpropsetsqlservercolumn-property-set"></a>DBPROPSET_SQLSERVERCOLUMN 속성 집합  
 테이블 생성을 지원 하기 위해는 **ITableDefinition** 인터페이스 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client는 DBPROPSET_SQLSERVERCOLUMN 속성 집합을 다음과 같은 3 개의 새 열을 추가 합니다.  
  
|속성|Description|형식|Description|  
|----------|-----------------|----------|-----------------|  
|SSPROP_COL_UDT_CATALOGNAME|UDT_CATALOGNAME|VT_BSTR|DBTYPE_UDT 형식인 열의 경우 이 속성이 UDT가 정의되어 있는 카탈로그의 이름을 지정하는 문자열입니다.|  
|SSPROP_COL_UDT_SCHEMANAME|UDT_SCHEMANAME|VT_BSTR|DBTYPE_UDT 형식인 열의 경우 이 속성이 UDT가 정의되어 있는 스키마의 이름을 지정하는 문자열입니다.|  
|SSPROP_COL_UDT_NAME|UDT_NAME|VT_BSTR|DBTYPE_UDT 형식인 열의 경우 이 속성이 UDT의 단일 부분으로 구성된 이름을 지정하는 문자열입니다. 다른 열 유형에 대해서는 이 속성이 빈 문자열을 반환합니다.|  
  
> [!NOTE]  
>  PROVIDER_TYPES 스키마 행 집합에는 UDT가 나타나지 않습니다. 모든 열에 읽기 및 쓰기 액세스가 있습니다.  
  
 ADO는 설명 열의 해당 항목을 사용하여 이러한 속성을 참조합니다.  
  
 SSPROP_COL_UDTNAME은 필수입니다. SSPROP_COL_UDT_CATALOGNAME 및 SSPROP_COL_UDT_SCHEMANAME은 옵션입니다. 이러한 속성 중 하나가 잘못 지정되면 `DB_E_ERRORSINCOMMAND`가 반환됩니다.  
  
 SSPROP_COL_UDT_CATALOGNAME 및 SSPROP_COL_UDT_SCHEMANAME이 모두 지정되지 않은 경우 테이블과 동일한 데이터베이스와 스키마에서 UDT를 정의해야 합니다.  
  
 UDT 정의가 테이블과 동일한 데이터베이스에 속하지만 다른 스키마에 속하는 경우 SSPROP_COL_UDT_SCHEMANAME을 지정해야 합니다.  
  
 UDT 정의가 다른 데이터베이스에 속하는 경우 SSPROP_COL_UDT_CATALOGNAME 및 SSPROP_COL_UDT_SCHEMANAME을 모두 지정해야 합니다.  
  
### <a name="ole-db-interface-additions-and-changes"></a>OLE DB 인터페이스의 추가 내용 및 변경 내용  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client는 새 값을 추가 하거나 많은 핵심 OLE DB 인터페이스를 변경 합니다.  
  
#### <a name="the-isscommandwithparameters-interface"></a>ISSCommandWithParameters 인터페이스  
 OLE DB를 통해 Udt를 지원 하기 위해 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client의 추가 포함 하 여 변경 사항을 구현 하는 **ISSCommandWithParameters** 인터페이스입니다. 이 새 인터페이스는 핵심 OLE DB 인터페이스에서 상속 **ICommandWithParameters**합니다. 상속 되며, 세 가지 방법 외에도 **ICommandWithParameters**; **GetParameterInfo**, **MapParameterNames**, 및 **SetParameterInfo**; **ISSCommandWithParameters** 제공는 **GetParameterProperties** 및 **SetParameterProperties** 서버 특정 처리에 사용 되는 메서드 데이터 형식입니다.  
  
> [!NOTE]  
>  **ISSCommandWithParameters** 인터페이스도에서 활용 하는 새로운 SSPARAMPROPS 구조입니다.  
  
#### <a name="the-icolumnsrowset-interface"></a>IColumnsRowset 인터페이스  
 이외에 **ISSCommandWithParameters** 인터페이스 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client도 호출에서 반환 된 행 집합에 새 값을 추가 **icolumnsrowset:: Getcolumnrowset** 메서드 다음을 포함 합니다.  
  
|열 이름|형식|Description|  
|-----------------|----------|-----------------|  
|DBCOLUMN_SS_UDT_CATALOGNAME|DBTYPE_WSTR|UDT 카탈로그 이름 식별자입니다.|  
|DBCOLUMN_SS_UDT_SCHEMANAME|DBTYPE_WSTR|UDT 스키마 이름 식별자입니다.|  
|DBCOLUMN_SS_UDT_NAME|DBTYPE_WSTR|UDT 이름 식별자입니다.|  
|DBCOLUMN_SS_ASSEMBLY_TYPENAME|DBTYPE_WSTR|CLR이 참조하는 데 필요한 형식 이름과 모든 어셈블리 ID를 포함하는 어셈블리의 정규화된 이름입니다.|  
  
 DBCOLUMN_TYPE이 DBTYPE_UDT로 설정되어 있는 경우 위에 지정된 추가적인 UDT 메타데이터를 찾아 서버의 UDT 열을 다른 이진 형식과 구분할 수 있습니다. 해당 데이터가 부분적으로 완료된 경우 서버 유형은 UDT입니다. 비 UDT 서버 유형의 경우에는 이러한 열이 항상 NULL로 반환됩니다.  
  
## <a name="sql-server-native-client-odbc-driver"></a>SQL Server Native Client ODBC 드라이버  
 에 대 한 변경 사항을 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Udt를 지원 하기 위해 Native Client ODBC 드라이버. [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC 드라이버 지도 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] UDT를 SQL_SS_UDT 드라이버별 SQL 데이터 식별자를 입력 합니다. UDT 열은 SQL_SS_UDT로 표시됩니다. 사용 하 여 SQL 문의 다른 형식으로 UDT 열을 명시적으로 매핑하는 경우는 **ToString** 또는 **ToXMLString** 를 통해 또는 udt 메서드에 **CAST/CONVERT** 함수, 유형 결과의 열 집합의 열으로 변환 된 실제 형식을 반영합니다  
  
### <a name="sqlcolattribute-sqldescribeparam-sqlgetdescfield"></a>SQLColAttribute, SQLDescribeParam, SQLGetDescField  
 결과 집합의 UDT 열 또는 저장 프로시저/매개 변수가 있는 쿼리를 통해 검색 되는 UDT 매개 변수 중 하나에 대 한 추가 정보를 제공에 추가 된 4 개의 새 드라이버별 설명자 필드는 [SQLColAttribute](../../native-client-odbc-api/sqlcolattribute.md), [SQLDescribeParam](../../native-client-odbc-api/sqldescribeparam.md), 및 [SQLGetDescField](../../native-client-odbc-api/sqlgetdescfield.md) 함수입니다.  
  
 추가된 새 설명자 필드 네 개는 SQL_CA_SS_UDT_CATALOG_NAME, SQL_CA_SS_UDT_SCHEMA_NAME, SQL_CA_SS_UDT_TYPE_NAME 및 SQL_CA_SS_UDT_ASSEMBLY_TYPE_NAME입니다.  
  
### <a name="sqlcolumns-sqlprocedurecolumns"></a>SQLColumns, SQLProcedureColumns  
 또한 3 개의 새 드라이버별 열 결과에서 반환 된 집합에 추가 됩니다는 [SQLColumns](../../native-client-odbc-api/sqlcolumns.md) 및 [SQLProcedureColumns](../../native-client-odbc-api/sqlprocedurecolumns.md) UDT 결과 중 하나에 대 한 추가 정보를 제공 하는 함수 열 이나 UDT 매개 변수를 설정 합니다. 이 새로운 세 개의 열은 SS_UDT_CATALOG_NAME, SS_UDT_SCHEMA_NAME 및 SS_UDT_ASSEMBLY_TYPE_NAME입니다.  
  
### <a name="supported-conversions"></a>지원되는 변환  
 SQL에서 C 데이터 형식으로 변환할 때 SQL_C_WCHAR, SQL_C_BINARY 및 SQL_C_CHAR을 모두 SQL_SS_UDT로 변환할 수 있습니다. 하지만 SQL_C_WCHAR 및 SQL_C_CHAR SQL 데이터 형식에서 변환할 경우에는 이진 데이터가 16진수 문자열로 변환됩니다.  
  
 C에서 SQL 데이터 형식으로 변환할 때 SQL_C_WCHAR, SQL_C_BINARY 및 SQL_C_CHAR을 모두 SQL_SS_UDT로 변환할 수 있습니다. 하지만 SQL_C_WCHAR 및 SQL_C_CHAR SQL 데이터 형식에서 변환할 경우에는 이진 데이터가 16진수 문자열로 변환됩니다.  
  
## <a name="see-also"></a>관련 항목  
 [SQL Server Native Client 기능](sql-server-native-client-features.md)   
 [ISSCommandWithParameters &#40;OLE DB&#41;](../../native-client-ole-db-interfaces/isscommandwithparameters-ole-db.md)  
  
  