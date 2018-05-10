---
title: ImpersonationInfoSecurity 요소 (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
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
- ImpersonationInfoSecurity Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- ImpersonationInfoSecurity element
ms.assetid: 583fec36-90ef-4d6a-9888-ece6ae865c53
caps.latest.revision: 13
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 63329e6d25a4ec1788a37d8b723fd220f124259c
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
---
# <a name="impersonationinfosecurity-element-assl"></a>ImpersonationInfoSecurity 요소(ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  에 제공 된 보안 자격 증명에이 변경 사항이 여부를 나타내는 읽기 전용 값이 포함 된 [ImpersonationInfo](../../../analysis-services/scripting/data-type/impersonationinfo-data-type-assl.md) 데이터 형식입니다.  
  
## <a name="syntax"></a>구문  
  
```xml  
  
<ImpersonationInfo>  
   ...  
   <ImpersonationInfoSecurity>...</ImpersonationInfoSecurity>  
  
</ImpersonationInfo>...  
```  
  
## <a name="element-characteristics"></a>요소 특징  
  
|특징|설명|  
|--------------------|-----------------|  
|데이터 형식 및 길이|String(열거형)|  
|기본값|없음|  
|카디널리티|0-1: 한 번만 나타날 수 있는 선택적 요소입니다.|  
  
## <a name="element-relationships"></a>요소 관계  
  
|관계|요소|  
|------------------|-------------|  
|부모 요소|[ImpersonationInfo](../../../analysis-services/scripting/data-type/impersonationinfo-data-type-assl.md)|  
|자식 요소|없음|  
  
## <a name="remarks"></a>주의  
 이 요소의 값은 다음 표에 있는 문자열 중 하나로 제한됩니다.  
  
|값|Description|  
|-----------|-----------------|  
|*PasswordRemoved*|제공된 보안 자격 증명에서 암호 정보가 제거되었습니다.|  
|*Unchanged*|제공된 보안 자격 증명이 변경되지 않았습니다.|  
  
 에 대 한 허용된 된 값에 해당 하는 열거형 **ImpersonationInfoSecurity** Analysis Management Objects (AMO) 개체 모델은 <xref:Microsoft.AnalysisServices.ImpersonationInfoSecurity>합니다.  
  
## <a name="see-also"></a>관련 항목:  
 [속성 & #40; ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  