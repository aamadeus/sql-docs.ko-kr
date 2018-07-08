---
title: DBSCHEMA_CATALOGS 행 집합 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- DBSCHEMA_CATALOGS
topic_type:
- apiref
helpviewer_keywords:
- DBSCHEMA_CATALOGS rowset
ms.assetid: f02dc75d-5442-4eea-b33a-567dc816be7a
caps.latest.revision: 31
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: df3b146d3e1015fd4a78254be0d8a7a6083991d8
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36079856"
---
# <a name="dbschemacatalogs-rowset"></a>DBSCHEMA_CATALOGS 행 집합
  DBMS(데이터베이스 관리 시스템)에서 액세스 가능한 카탈로그에 연결된 실제 특성을 식별합니다.  
  
## <a name="rowset-columns"></a>행 집합 열  
 `DBSCHEMA_CATALOGS` 행 집합에는 다음과 같은 열을 포함 합니다.  
  
|열 이름|유형 표시기|길이|Description|  
|-----------------|--------------------|------------|-----------------|  
|`CATALOG_NAME`|`DBTYPE_WSTR`|255|카탈로그 이름입니다. null일 수 없습니다.|  
|`DESCRIPTION`|`DBTYPE_WSTR`||사람이 읽을 수 있는 테이블 설명입니다.|  
|`ROLES`|`DBTYPE_WSTR`||현재 사용자가 속해 있는 쉼표로 구분된 역할 목록입니다.<br /><br /> 별표 (\*) 경우에 서버 또는 데이터베이스 관리자는 현재 사용자가 역할이 포함 됩니다.<br /><br /> 역할 중 하나가 동적 보안을 사용하는 경우 `Username`이 `ROLES`에 추가됩니다.|  
|`DATE_MODIFIED`|`DBTYPE_DBTIMESTAMP`||카탈로그가 마지막으로 수정된 날짜입니다.|  
  
 행 집합은 `CATALOG_NAME`을 기준으로 정렬됩니다.  
  
## <a name="restriction-columns"></a>제한 열  
 `DBSCHEMA_CATALOGS` 행 집합은 다음 표의 열을 기준으로 제한될 수 있습니다.  
  
|열 이름|유형 표시기|제한 상태|  
|-----------------|--------------------|-----------------------|  
|`CATALOG_NAME`|`DBTYPE_WSTR`|선택 사항|  
  
## <a name="see-also"></a>관련 항목  
 [OLE DB 스키마 행 집합](ole-db-schema-rowsets.md)  
  
  