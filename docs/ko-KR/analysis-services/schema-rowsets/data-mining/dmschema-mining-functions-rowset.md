---
title: DMSCHEMA_MINING_FUNCTIONS 행 집합 | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: data-mining
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- DMSCHEMA_MINING_FUNCTIONS
apitype: NA
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- DMSCHEMA_MINING_FUNCTIONS rowset
ms.assetid: 9ace7493-a7b1-45ca-93de-3cb2f3597017
caps.latest.revision: 35
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 70dd46fa691630b2ebdb9a86e980fbad6e41f6b0
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
---
# <a name="dmschemaminingfunctions-rowset"></a>DMSCHEMA_MINING_FUNCTIONS 행 집합
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]를 실행 중인 서버에서 사용할 수 있는 데이터 마이닝 알고리즘이 지원하는 데이터 마이닝 함수에 대해 설명합니다.  
  
## <a name="rowset-columns"></a>행 집합 열  
 **DMSCHEMA_MINING_FUNCTIONS** 행 집합에는 다음 열이 포함되어 있습니다.  
  
|열 이름|유형 표시기|길이|Description|  
|-----------------|--------------------|------------|-----------------|  
|**SERVICE_NAME**|**DBTYPE_WSTR**||알고리즘의 이름입니다.|  
|**FUNCTION_NAME**|**DBTYPE_WSTR**||함수의 이름입니다.|  
|**T E R**|**DBTYPE_WSTR**||함수의 서명입니다.|  
|**RETURNS_TABLE**|**DBTYPE_BOOL**||함수에서 문자 인수 길이와 같은 스칼라 콘텐츠를 반환하면**FALSE** 이고, 히스토그램 테이블과 같은 테이블을 반환하면 **TRUE** 입니다.|  
|**DESCRIPTION**|**DBTYPE_WSTR**||함수에 대한 알기 쉬운 설명입니다.|  
|**HELP_FILE**|**DBTYPE_WSTR**||이 함수의 설명서가 있는 파일의 이름입니다.|  
|**HELP_CONTEXT**|**DBTYPE_I4**||이 함수에 대한 도움말 컨텍스트 ID입니다.|  
  
## <a name="restriction-columns"></a>제한 열  
 **DMSCHEMA_MINING_FUNCTIONS** 행 집합은 다음 표의 열을 기준으로 제한될 수 있습니다.  
  
|열 이름|유형 표시기|제한 상태|  
|-----------------|--------------------|-----------------------|  
|**SERVICE_NAME**|**DBTYPE_WSTR**|(선택 사항)|  
|**FUNCTION_NAME**|**DBTYPE_WSTR**|(선택 사항)|  
  
## <a name="see-also"></a>참고 항목  
 [데이터 마이닝 스키마 행 집합](../../../analysis-services/schema-rowsets/data-mining/data-mining-schema-rowsets.md)  
  
  