---
title: Column 요소 (DTA) 인덱스에 대 한 | Microsoft Docs
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
- Column element
ms.assetid: ba9fac20-26bd-4333-940e-842c15241b46
caps.latest.revision: 14
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 58d8827fe160ef1acb300e7501fd9faeaa369efd
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36079881"
---
# <a name="column-element-for-index-dta"></a>Index의 Column 요소(DTA)
  사용자 지정 구성에서 인덱스가 만들어지는 열을 지정합니다.  
  
## <a name="syntax"></a>구문  
  
```  
  
<Create>  
  <Index>  
    <Name>...</Name>  
    <Column [Type | SortOrder]>  
     ...code removed here...  
     </Column>  
```  
  
## <a name="element-attributes"></a>요소 특성  
  
|Column 특성|Description|  
|----------------------|-----------------|  
|`Type`|(선택 사항) 인덱스 열 유형을 지정합니다. **string** 데이터 형식을 사용하여 허용된 다음 값 중 하나로 이 특성을 지정할 수 있습니다.<br /><br /> `KeyColumn`:<br />                  인덱스 키에서 열을 참조하도록 지정합니다. 다음 구문을 사용하여 이 특성을 설정합니다.<br />`<Column Type="KeyColumn">`<br />자세한 내용은 [클러스터형 및 비클러스터형 인덱스 소개](../../relational-databases/indexes/clustered-and-nonclustered-indexes-described.md)를 참조하세요.<br /><br /> `IncludedColumn`: 열 (키 열) 대신 포괄된 열 임을 지정 합니다. 다음 구문을 사용하여 이 특성을 설정합니다.<br />`<Column Type="IncludedColumn">`<br />키가 아닌 열 포함에 대한 자세한 내용은 [포괄 열을 사용하여 인덱스 만들기](../../relational-databases/indexes/create-indexes-with-included-columns.md)를 참조하세요.|  
|`SortOrder`|(선택 사항) 열의 정렬 순서를 지정합니다. 다음과 같이 **string** 데이터 형식을 사용하여 **"Ascending"** 또는 **"Descending"** 정렬 순서를 지정할 수 있습니다.<br /><br /> `<Column SortOrder="Ascending">`|  
  
## <a name="element-characteristics"></a>요소 특징  
  
|특징|Description|  
|--------------------|-----------------|  
|**데이터 형식 및 길이**|없음|  
|**기본값**|없음|  
|**발생 빈도**|`Index` 요소에 최대 1024개의 열을 지정할 수 있습니다.|  
  
## <a name="element-relationships"></a>요소 관계  
  
|관계|요소|  
|------------------|--------------|  
|**부모 요소**|[요소 인덱스 &#40;DTA&#41;](index-element-dta.md)|  
|**자식 요소**|[Name 요소 열에 대 한 &#40;DTA&#41;](name-element-for-column-dta.md)|  
  
## <a name="example"></a>예제  
 이 요소의 사용 예를 보려면 [사용자 정의 구성이 포함된 XML 입력 파일 샘플&#40;DTA&#41;](xml-input-file-sample-with-user-specified-configuration-dta.md)을 참조하세요.  
  
## <a name="see-also"></a>관련 항목  
 [XML 입력 파일 참조&#40;데이터베이스 엔진 튜닝 관리자&#41;](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  