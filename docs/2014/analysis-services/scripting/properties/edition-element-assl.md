---
title: Edition 요소 (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- Edition Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Edition
helpviewer_keywords:
- Edition element
ms.assetid: 521e1286-097e-494f-b036-61047096e87e
caps.latest.revision: 38
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: c9d801f2055513323f473a73662337349207ea6e
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36093635"
---
# <a name="edition-element-assl"></a>Edition 요소(ASSL)
  인스턴스의 읽기 전용 버전을 포함 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 나타내는 [서버](../objects/server-element-assl.md) 요소입니다.  
  
## <a name="syntax"></a>구문  
  
```xml  
  
<Server>  
      ...  
      <Edition>...</Edition>  
   ...  
</Server>  
```  
  
## <a name="element-characteristics"></a>요소 특징  
  
|특징|Description|  
|--------------------|-----------------|  
|데이터 형식 및 길이|String(열거형)|  
|기본값|InclusionThresholdSetting|  
|카디널리티|0-1: 한 번만 나타날 수 있는 선택적 요소입니다.|  
  
## <a name="element-relationships"></a>요소 관계  
  
|관계|요소|  
|------------------|-------------|  
|부모 요소|[Server](../objects/server-element-assl.md)|  
|자식 요소|InclusionThresholdSetting|  
  
## <a name="remarks"></a>Remarks  
 `Edition` 요소는 설치된 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 버전을 설명합니다. 이 요소의 값은 다음 표에 있는 문자열 중 하나로 제한됩니다.  
  
|값|Description|  
|-----------|-----------------|  
|*Standard*|[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 32 비트 프로세서에 대 한 표준 버전입니다.|  
|*Enterprise*|[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 32 비트 프로세서에 대 한 엔터프라이즈 버전입니다.|  
|*EnterpriseCore*|[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 엔터프라이즈 버전: 코어 기반 라이선스 32 비트 프로세서.|  
|*BusinessIntelligence*|[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 32 비트 프로세서에 대 한 business Intelligence 버전입니다.|  
|*개발자*|[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 32 비트 프로세서에 대 한 개발자 버전|  
|*평가*|[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 64 비트 프로세서에 대 한 평가판 버전입니다.|  
|*로컬*|[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 32 비트 프로세서에 대 한 로컬 버전입니다.|  
|*Standard64*|[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 64 비트 프로세서에 대 한 표준 버전입니다.|  
|*Enterprise64*|[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 64 비트 프로세서에 대 한 엔터프라이즈 버전입니다.|  
|*EnterpriseCore64*|[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Enterprise edition: 64 비트 프로세서용 코어 기반 라이선스입니다.|  
|*BusinessIntelligence64*|[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 64 비트 프로세서에 대 한 business Intelligence 버전입니다.|  
|*Developer64*|[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 64 비트 프로세서에 대 한 개발자 버전|  
|*Evaluation64*|[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 64 비트 프로세서에 대 한 평가판 버전입니다.|  
|*Local64*|[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 64 비트 프로세서에 대 한 로컬 버전입니다.|  
  
 AMO(Analysis Management Objects) 개체 모델에서 `ServerEdition`에 대해 허용된 값에 해당하는 열거형은 <xref:Microsoft.AnalysisServices.ServerEdition>입니다.  
  
## <a name="see-also"></a>관련 항목  
 [버전 요소 &#40;ASSL&#41;](version-element-assl.md)   
 [속성 &#40;ASSL&#41;](properties-assl.md)  
  
  