---
title: 데이터 원본 정보 속성 | Microsoft Docs
description: 데이터 원본 정보 속성
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
- information properties [OLE DB]
- OLE DB data source properties [OLE DB Driver for SQL Server]
author: pmasl
ms.author: Pedro.Lopes
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: d7ef43ecde303da0f0e6ba89a067ffb13069c22b
ms.sourcegitcommit: 9351e8b7b68f599a95fb8e76930ab886db737e5f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2018
---
# <a name="data-source-information-properties"></a>데이터 원본 정보 속성
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  공급자별 속성 집합 DBPROPSET_SQLSERVERDATASOURCEINFO에는 OLE DB Driver for SQL Server는 다음 데이터 원본 정보 속성을 정의합니다.  
  
|속성 ID|Description|  
|-----------------|-----------------|  
|SSPROP_COLUMNLEVELCOLLATION|형식: VT_BOOL<br /><br /> R/w: 읽기<br /><br /> 기본값: VARIANT_TRUE<br /><br /> 설명: 열 데이터 정렬이 지원 되는지 확인 하는 데 사용 합니다.<br /><br /> VARIANT_TRUE: 열 수준 데이터 정렬을 사용할 수 있습니다.<br /><br /> VARIANT_FALSE: 열 수준 데이터 정렬이 지원 되지 않습니다.|  
|SSPROP_UNICODELCID|형식: VT_I4 R/w: 읽기<br /><br /> 설명: 유니코드 로캘 id입니다.<br /><br /> 유니코드 데이터 정렬에 사용되는 로캘입니다.|  
|SSPROP_UNICODECOMPARISONSTYLE|형식: VT_I4 R/w: 읽기<br /><br /> 설명: 유니코드 비교 스타일입니다.<br /><br /> 유니코드 데이터 정렬에 사용되는 정렬 옵션입니다.|  
  
 공급자별 속성 집합 DBPROPSET_SQLSERVERSTREAM에는 OLE DB Driver for SQL Server 같은 추가 속성을 정의합니다.  
  
|속성 ID|Description|  
|-----------------|-----------------|  
|SSPROP_STREAM_XMLROOT|유형: VT_BSTR R/w: 읽기/쓰기<br /><br /> 설명: FOR XML 쿼리 결과가 올바른 형식의 문서를 수 있습니다. 이 속성을 지정한 경우, 결과 ' 선택... XML에 대 한 ' 쿼리는 올바른 형식의 XML 문서를 반환 하도록이 속성에서 제공한 루트 태그에 래핑됩니다. 쿼리가 브라우저에서 실행되는 경우에는 결과를 로드할 때 브라우저에서 파서 오류가 표시될 수 있습니다. 오류를 방지하기 위해 SQL ISAPI는 ROOT 키워드를 지원합니다. 이 키워드는 SSPROP_STREAM_XMLROOT 속성에 매핑됩니다.|  
  
## <a name="see-also"></a>관련 항목:  
 [데이터 원본 개체 & #40; OLE db& #41;](../../oledb/ole-db-data-source-objects/data-source-objects-ole-db.md)  
  
  