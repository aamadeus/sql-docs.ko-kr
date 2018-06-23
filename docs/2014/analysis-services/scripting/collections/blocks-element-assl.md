---
title: 차단 요소 (ASSL) | Microsoft Docs
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
- Blocks Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Blocks
helpviewer_keywords:
- Blocks element
ms.assetid: d6fd4e6b-b5bd-43cd-9c28-48af57cf977c
caps.latest.revision: 32
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: bf944cc053e7a8c32efec50d10f6cc176942cce1
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36089646"
---
# <a name="blocks-element-assl"></a>Blocks 요소(ASSL)
  이진 내용을 나타내는 이진 데이터 블록의 컬렉션을 포함 한 [ClrAssemblyFile](../data-type/clrassemblyfile-data-type-assl.md) 요소입니다.  
  
## <a name="syntax"></a>구문  
  
```xml  
  
<Data xsi:type="DataBlock">  
   ...  
   <Blocks>  
      <Block>...</Block>  
   </Blocks>  
   ...  
</File>  
```  
  
## <a name="element-characteristics"></a>요소 특징  
  
|특징|Description|  
|--------------------|-----------------|  
|데이터 형식 및 길이|InclusionThresholdSetting|  
|기본값|InclusionThresholdSetting|  
|카디널리티|1-1: 한 번만 나타나는 필수 요소입니다.|  
  
## <a name="element-relationships"></a>요소 관계  
  
|관계|요소|  
|------------------|-------------|  
|부모 요소|[데이터](../objects/data-element-assl.md) 형식의 [DataBlock](../data-type/datablock-data-type-assl.md)|  
|자식 요소|[블록](../objects/block-element-assl.md)|  
  
## <a name="remarks"></a>Remarks  
 부모에 해당 하는 요소 `Blocks` Analysis Management Objects (AMO) 개체 모델은 <xref:Microsoft.AnalysisServices.ClrAssemblyFile>합니다.  
  
## <a name="see-also"></a>관련 항목  
 [Assembly 요소 &#40;ASSL&#41;](../objects/assembly-element-assl.md)   
 [ClrAssembly 데이터 형식 &#40;ASSL&#41;](../data-type/assembly-data-type-assl.md)   
 [파일 요소 &#40;ASSL&#41;](files-element-assl.md)   
 [파일 요소 &#40;ASSL&#41;](../objects/file-element-assl.md)   
 [ClrAssemblyFile 데이터 형식 &#40;ASSL&#41;](../data-type/clrassemblyfile-data-type-assl.md)   
 [데이터 요소 &#40;ASSL&#41;](../objects/data-element-assl.md)   
 [DataBlock 데이터 형식 &#40;ASSL&#41;](../data-type/datablock-data-type-assl.md)   
 [Blocks 요소](blocks-element-assl.md)   
 [요소를 차단 &#40;ASSL&#41;](../objects/block-element-assl.md)   
 [컬렉션 &#40;ASSL&#41;](collections-assl.md)  
  
  