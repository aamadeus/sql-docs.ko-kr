---
title: 요소 (DTA) 스키마에 대 한 테이블 | Microsoft Docs
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
- Table element [DTA]
ms.assetid: a59e8319-05d1-47f3-af39-7d970ab8e7dc
caps.latest.revision: 13
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 44df363381b2811b422f29671fe4902c1dd7c23e
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36173005"
---
# <a name="table-element-for-schema-dta"></a>Schema의 Table 요소(DTA)
  튜닝에 사용할 테이블을 지정합니다.  
  
## <a name="syntax"></a>구문  
  
```  
  
<Schema>  
...code removed here...  
    <Table>...</Table>  
```  
  
## <a name="element-attributes"></a>요소 특성  
  
|attribute|Description|  
|---------------|-----------------|  
|`NumberOfRows`|(선택 사항) 여러 다른 크기의 테이블을 시뮬레이트할 수 있게 하는 정수입니다.|  
  
## <a name="element-characteristics"></a>요소 특징  
  
|특징|Description|  
|--------------------|-----------------|  
|**데이터 형식 및 길이**|**string**, 1에서 255자 사이|  
|**기본값**|없음|  
|**발생 빈도**|(선택 사항) 작업에 적합한 수만큼 테이블을 나열합니다.|  
  
## <a name="element-relationships"></a>요소 관계  
  
|관계|요소|  
|------------------|--------------|  
|**부모 요소**|[Database의 schema 요소 &#40;DTA&#41;](schema-element-for-database-dta.md)|  
|**자식 요소**|[테이블에 대 한 요소 이름을 &#40;DTA&#41;](name-element-for-table-dta.md)|  
  
## <a name="remarks"></a>Remarks  
 `Table` 요소를 지정하지 않을 경우 데이터베이스 엔진 튜닝 관리자는 지정된 데이터베이스의 모든 테이블을 튜닝할 수 있다고 가정합니다.  
  
## <a name="example"></a>예제  
 사용 예를 보려면 [Server 요소&#40;DTA&#41;](server-element-dta.md)를 참조하세요.  
  
## <a name="see-also"></a>관련 항목  
 [XML 입력 파일 참조&#40;데이터베이스 엔진 튜닝 관리자&#41;](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  