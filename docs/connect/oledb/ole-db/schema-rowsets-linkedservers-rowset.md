---
title: LINKEDSERVERS 행 집합 (OLE DB) | Microsoft Docs
description: LINKEDSERVERS 행 집합(OLE DB)
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
helpviewer_keywords:
- LINKEDSERVERS rowset
- enumerating data sources [OLE DB]
author: pmasl
ms.author: Pedro.Lopes
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: b00a600f2690981f152c75c92dc467c1d6d13aed
ms.sourcegitcommit: 9351e8b7b68f599a95fb8e76930ab886db737e5f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2018
---
# <a name="schema-rowsets---linkedservers-rowset"></a>스키마 행 집합-LINKEDSERVERS 행 집합
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  **LINKEDSERVERS** 행 집합에 참여할 수 있는 조직 데이터 원본을 열거 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 분산 쿼리 합니다.  
  
 **LINKEDSERVERS** 행 집합에는 다음 열이 포함되어 있습니다.  
  
|열 이름|유형 표시기|Description|  
|-----------------|--------------------|-----------------|  
|SVR_NAME|DBTYPE_WSTR|연결된 서버의 이름입니다.|  
|SVR_PRODUCT|DBTYPE_WSTR|연결된 서버 이름이 나타내는 데이터 저장소 유형을 식별하는 제조업체 또는 기타 이름입니다.|  
|SVR_PROVIDERNAME|DBTYPE_WSTR|서버 데이터를 이용할 때 사용되는 OLE DB 공급자의 이름입니다.|  
|SVR_DATASOURCE|DBTYPE_WSTR|공급자의 데이터 원본을 가져올 때 사용되는 OLE DB DBPROP_INIT_DATASOURCE 문자열입니다.|  
|SVR_PROVIDERSTRING|DBTYPE_WSTR|공급자의 데이터 원본을 가져올 때 사용되는 OLE DB DBPROP_INIT_PROVIDERSTRING 값입니다.|  
|SVR_LOCATION|DBTYPE_WSTR|공급자의 데이터 원본을 가져올 때 사용되는 OLE DB DBPROP_INIT_LOCATION 문자열입니다.|  
  
 행 집합은 SRV_NAME을 기준으로 정렬되며 SRV_NAME에서 하나의 제한이 지원됩니다.  
  
## <a name="see-also"></a>관련 항목:  
 [스키마 행 집합 지원 &#40;OLE DB&#41;](../../oledb/ole-db/schema-rowset-support-ole-db.md)  
  
  