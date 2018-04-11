---
title: 데이터 원본 속성 (OLE DB) | Microsoft Docs
description: 데이터 원본 속성 (OLE DB)
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: ole-db-data-source-objects
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- OLE DB Driver for SQL Server, data source properties
- properties [OLE DB]
- data source properties [OLE DB]
- OLE DB data source properties [OLE DB Driver for SQL Server]
author: pmasl
ms.author: Pedro.Lopes
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: fcde39742d23c9cf29bd22c7c384c8ea7e615ec1
ms.sourcegitcommit: 9351e8b7b68f599a95fb8e76930ab886db737e5f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2018
---
# <a name="data-source-properties-ole-db"></a>데이터 원본 속성(OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  OLE DB Driver for SQL Server 데이터 원본 속성을 다음과 같이 구현합니다.  
  
|속성 ID|설명|  
|-----------------|-----------------|  
|DBPROP_CURRENTCATALOG|R/w: 읽기/쓰기 기본값: 없음<br /><br /> 설명: DBPROP_CURRENTCATALOG 값 보고 현재 데이터베이스는 OLE DB Driver에 대 한 SQL Server 세션에 대 한 합니다. 사용 하 여 현재 데이터베이스를 설정 하는 것과 동일한 결과가 속성 값을 설정는 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 사용 *데이터베이스* 문.<br /><br /> 부터는 [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]호출 하는 경우, [sp_defaultdb](../../../relational-databases/system-stored-procedures/sp-defaultdb-transact-sql.md) 데이터베이스 이름을 지정 하 고 소문자로 혼합 사례 이름의 데이터베이스가 원래 만들어진 경우에 DBPROP_CURRENTCATALOG 이름을 반환 하는 소문자로 합니다. 이전 버전의 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]에서는 DBPROP_CURRENTCATALOG가 대/소문자가 섞인 이름을 반환했습니다.|  
|DBPROP_MULTIPLECONNECTIONS|R/w: 읽기/쓰기 기본값: VARIANT_FALSE<br /><br /> 설명: 연결이 행 집합을 생성 하지 않으므로 또는 서버 커서를 하지 않은 행 집합을 생성 하는 명령을 실행 하는 경우 다른 명령을 실행할 경우 DBPROP_MULTIPLECONNECTIONS가 VARIANT_TRUE 이면 새 명령을 실행 하 여 새 연결 생성 됩니다.<br /><br /> OLE DB Driver for SQL Server DBPROP_MULTIPLECONNECTION이 VARIANT_FALSE 또는 연결에는 트랜잭션이 활성화 된 경우 다른 연결을 생성 되지 않습니다. OLE DB Driver for SQL Server DB_E_OBJECTOPEN을 반환 하는 경우 DBPROP_MULTIPLECONNECTIONS가 VARIANT_FALSE 고 활성 트랜잭션이 있으면 E_FAIL을 반환 합니다. 트랜잭션 및 잠금은 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]가 연결별로 관리합니다. 두 번째 연결이 생성되면 분리된 연결에 대한 명령은 잠금을 공유하지 않습니다. 한 명령이 다른 명령을 차단하지 않도록 다른 명령이 요청한 행의 잠금은 유지됩니다. 여러 세션을 만들 때도 마찬가지입니다.<br /><br /> 각 세션이 별도의 연결을 가집니다.|  
  
 공급자별 속성 집합 DBPROPSET_SQLSERVERDATASOURCE에는 OLE DB Driver for SQL Server는 다음과 같은 추가 데이터 원본 속성을 정의합니다.  
  
|속성 ID|설명|  
|-----------------|-----------------|  
|SSPROP_ENABLEFASTLOAD|R/w: 읽기/쓰기 기본값: VARIANT_FALSE<br /><br /> 설명: 메모리에서 대량 복사를 사용 하도록 설정 SSPROP_ENABLEFASTLOAD 속성을 variant_true로 설정 해야 합니다. 이 속성을 데이터 원본에 대해 설정 새로 만들어진된 세션에 대 한 소비자 액세스 허용 하는 [IRowsetFastLoad](../../oledb/ole-db-interfaces/irowsetfastload-ole-db.md) 인터페이스입니다.<br /><br /> 속성이 variant_true로 설정 되어 있으면 **IRowsetFastLoad** 인터페이스를 통해 사용할 수는 **iopenrowset:: Openrowset** 요청 하 여는 **IID_IRowsetFastLoad** 인터페이스 또는 설정 **SSPROP_IRowsetFastLoad** 를 variant_true로 설정 합니다.|  
|SSPROP_ENABLEBULKCOPY|R/w: 읽기/쓰기 기본값: VARIANT_FALSE<br /><br /> 설명: 파일에서 대량 복사를 사용 하도록 설정 SSPROP_ENABLEBULKCOPY 속성을 variant_true로 설정 해야 합니다. 데이터 원본에서 이 속성을 설정하면 소비자가 세션과 동일한 수준에서 IBCPSession 인터페이스에 액세스할 수 있습니다.<br /><br /> SSPROP_IRowsetFastLoad도 VARIANT_TRUE로 설정해야 합니다.|  
  
## <a name="see-also"></a>관련 항목:  
 [데이터 원본 개체 & #40; OLE db& #41;](../../oledb/ole-db-data-source-objects/data-source-objects-ole-db.md)  
  
  