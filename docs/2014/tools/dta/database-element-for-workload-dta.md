---
title: Database 요소 (DTA) 작업에 대 한 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- XML
helpviewer_keywords:
- Database element
ms.assetid: 112fca2a-37e5-4162-b2e7-b56eb8ab0c6f
caps.latest.revision: 12
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 6380708319286a984ef54ef3820fab22821047bf
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36088489"
---
# <a name="database-element-for-workload-dta"></a>Workload의 Database 요소(DTA)
  작업 추적 테이블이 위치하는 데이터베이스를 지정합니다.  
  
## <a name="syntax"></a>구문  
  
```  
  
<Workload>  
  <Database>  
   ...code removed here...  
  </Database>  
```  
  
## <a name="element-characteristics"></a>요소 특징  
  
|특징|Description|  
|--------------------|-----------------|  
|**데이터 형식 및 길이**|없음|  
|**기본값**|없음|  
|**발생 빈도**|다른 작업 유형이 지정되지 않은 경우 한 번만 지정해야 합니다. 지정 해야 합니다는 `EventString`, `File`, 또는 `Database` 에 대 한 자식 요소는 `Workload` 부모 하지만 한 유형만 사용할 수 있습니다. 예를 들어 `Database` 요소로 작업을 지정할 경우 동일한 XML 입력 파일에서 `File` 요소로 작업을 지정할 수 없습니다.|  
  
## <a name="element-relationships"></a>요소 관계  
  
|관계|요소|  
|------------------|--------------|  
|**부모 요소**|[Workload 요소 &#40;DTA&#41;](workload-element-dta.md)|  
|**자식 요소**|[데이터베이스에 대 한 요소 이름을 &#40;DTA&#41;](name-element-for-database-dta.md)<br /><br /> [Database의 schema 요소 &#40;DTA&#41;](schema-element-for-database-dta.md)|  
  
## <a name="remarks"></a>Remarks  
 데이터베이스 엔진 튜닝 관리자 XML 스키마에서 이 요소의 이름은 **DatabaseDetailsTypecomplexType** 입니다. 이 `Database` 요소와 `Configuration` 요소가 루트 부모인 요소를 혼동하지 마십시오. [Configuration의 Database 요소&#40;DTA&#41;](database-element-for-configuration-dta.md)를 참조하세요.  
  
## <a name="example"></a>예제  
 사용 예제를 보려면이에 대 한 `Database` 요소에서 코드 예제를 보려면 [Workload 요소 &#40;DTA&#41;](workload-element-dta.md)합니다.  
  
## <a name="see-also"></a>관련 항목  
 [XML 입력 파일 참조&#40;데이터베이스 엔진 튜닝 관리자&#41;](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  