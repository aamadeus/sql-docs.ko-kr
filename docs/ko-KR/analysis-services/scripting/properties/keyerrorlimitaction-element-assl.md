---
title: KeyErrorLimitAction 요소 (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- KeyErrorLimitAction Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- KeyErrorLimitAction
helpviewer_keywords:
- KeyErrorLimitAction element
ms.assetid: a2a01aae-0571-499f-9025-b61c741f3ddb
caps.latest.revision: 35
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: d698aa6bc6a29818371037488516d4b9e486bbbb
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
---
# <a name="keyerrorlimitaction-element-assl"></a>KeyErrorLimitAction 요소(ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  작업을 지정 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 에 지정 된 키 오류 수 하는 경우는 [KeyErrorLimit](../../../analysis-services/scripting/properties/keyerrorlimit-element-assl.md) 요소에 도달할 때.  
  
## <a name="syntax"></a>구문  
  
```xml  
  
<ErrorConfiguration>  
   ...  
      <KeyErrorLimitAction>...</KeyErrorLimitAction>  
   ...  
</ErrorConfiguration>  
```  
  
## <a name="element-characteristics"></a>요소 특징  
  
|특징|설명|  
|--------------------|-----------------|  
|데이터 형식 및 길이|String(열거형)|  
|기본값|*StopProcessing*|  
|카디널리티|0-1: 한 번만 나타날 수 있는 선택적 요소입니다.|  
  
## <a name="element-relationships"></a>요소 관계  
  
|관계|요소|  
|------------------|-------------|  
|부모 요소|[ErrorConfiguration](../../../analysis-services/scripting/objects/errorconfiguration-element-assl.md)|  
|자식 요소|없음|  
  
## <a name="remarks"></a>주의  
 이 요소의 값은 다음 표에 있는 문자열 중 하나로 제한됩니다.  
  
|값|Description|  
|-----------|-----------------|  
|*StopProcessing*|개체 처리를 중지합니다.|  
|*StopLogging*|처리 중 발생한 오류 기록은 중지하지만 개체는 계속 처리합니다.|  
  
 에 대 한 허용된 된 값에 해당 하는 열거형 **KeyErrorLimitAction** Analysis Management Objects (AMO) 개체 모델은 <xref:Microsoft.AnalysisServices.KeyErrorLimitAction>합니다.  
  
## <a name="see-also"></a>관련 항목:  
 [속성 & #40; ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  