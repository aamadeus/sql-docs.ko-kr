---
title: KeepExisting 요소 (DTA) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- KeepExisting element
ms.assetid: e67aae61-d06d-4a03-85ba-6516c3502dce
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 8691e57b9750447b1740c79337b75500febd9549
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48070743"
---
# <a name="keepexisting-element-dta"></a>KeepExisting 요소(DTA)
  데이터베이스 엔진 튜닝 관리자가 권장 구성을 생성할 때 유지해야 하는 물리적인 디자인 구조(인덱스, 인덱싱된 뷰 또는 분할)를 지정합니다.  
  
## <a name="syntax"></a>구문  
  
```  
  
<DTAInput>  
...code removed...  
    <TuningOptions>  
      <KeepExisting>...</KeepExisting>  
```  
  
## <a name="element-characteristics"></a>요소 특징  
  
|특징|Description|  
|--------------------|-----------------|  
|**데이터 형식 및 길이**|`string`, 서버에서 지정한 길이 제한 적용|  
|**허용된 값**|**NONE**<br /> 기존 구조 없음<br /><br /> **ALL**<br /> 모든 기존 구조<br /><br /> **ALIGNED**<br /> 모든 파티션 정렬 구조<br /><br /> **CL_IDX**<br /> 테이블의 모든 클러스터형 인덱스<br /><br /> **IDX**<br /> 테이블의 모든 클러스터형 및 비클러스터형 인덱스<br /><br /> 이 요소에 이러한 값 중 하나만 사용합니다.|  
|**기본값**|없음|  
|**발생 빈도**|(선택 사항) 각각에 대해 한 번만 사용할 수 `TuningOptions` 요소입니다.|  
  
## <a name="element-relationships"></a>요소 관계  
  
|관계|요소|  
|------------------|--------------|  
|**부모 요소**|[TuningOptions 요소 &#40;DTA&#41;](tuningoptions-element-dta.md)|  
|**자식 요소**|없음|  
  
## <a name="example"></a>예제  
 이 요소의 사용 예제를 보려면 [단순 XML 입력 파일 예제&#40;DTA&#41;](simple-xml-input-file-sample-dta.md)를 참조하세요.  
  
## <a name="see-also"></a>관련 항목  
 [XML 입력 파일 참조&#40;데이터베이스 엔진 튜닝 관리자&#41;](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
