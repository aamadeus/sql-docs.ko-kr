---
title: Analysis Services에서 XMLA를 사용 하 여 개발 | Microsoft Docs
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
helpviewer_keywords:
- XML for Analysis, data mining
- commands [XML for Analysis]
- data mining [XML for Analysis]
- XMLA, data mining
- XML for Analysis, Analysis Services tasks
- XMLA, Analysis Services tasks
ms.assetid: 54445ee7-720c-4683-99a6-e75b3dcca904
caps.latest.revision: 31
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 04c3459dca4edabcc56753a076bad1e4ffdddfde
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36186857"
---
# <a name="developing-with-xmla-in-analysis-services"></a>Analysis Services에서 XMLA를 사용하여 개발
  XMLA(XML for Analysis)는 HTTP 연결을 통해 액세스할 수 있는 표준 다차원 데이터 원본에 대한 범용 데이터 액세스를 위해 특별히 설계된 SOAP 기반 XML 프로토콜입니다. [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]에서는 클라이언트 응용 프로그램과 통신할 때의 유일한 프로토콜로 XMLA를 사용합니다. 기본적으로 Analysis Services에서 지원하는 모든 클라이언트 라이브러리는 XMLA의 요청 및 응답을 작성합니다.  
  
 개발자는 .NET Framework 또는 COM 인터페이스에 대한 종속성 없이 XMLA를 사용하여 클라이언트 응용 프로그램을 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]에 통합할 수 있습니다. 광범위한 플랫폼에서의 호스팅을 포함하는 응용 프로그램 요구 사항은 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]에 대한 HTTP 연결 및 XMLA를 사용하여 충족할 수 있습니다.  
  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]는 XMLA의 1.1 사양과 완전히 호환되지만 데이터 정의, 데이터 조작 및 데이터 제어 지원도 사용할 수 있도록 확장되었습니다. Analysis Services 확장 프로그램을 ASSL(Analysis Services Scripting Language)이라고 합니다. XMLA와 ASSL을 함께 사용하면 XMLA 하나에서만 제공하는 기능보다 더 다양한 기능 집합을 사용할 수 있습니다. ASSL에 대 한 자세한 내용은 참조 [Analysis Services Scripting Language를 사용 하 여 개발 &#40;ASSL&#41;](../multidimensional-models/scripting-language-assl/developing-with-analysis-services-scripting-language-assl.md)합니다.  
  
## <a name="in-this-section"></a>섹션 내용  
  
|항목|Description|  
|-----------|-----------------|  
|[연결 및 세션 관리 &#40;XMLA&#41;](managing-connections-and-sessions-xmla.md)|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 인스턴스에 연결하는 방법과 XMLA의 세션 및 상태 저장 관리 방법에 대해 설명합니다.|  
|[오류 및 경고 처리 &#40;XMLA&#41;](handling-errors-and-warnings-xmla.md)|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]에서 XMLA의 메서드 및 명령에 대한 오류 및 경고 정보를 반환하는 방법에 대해 설명합니다.|  
|[개체 정의 및 식별 &#40;XMLA&#41;](../xmla/xml-elements-objects.md)|개체 식별자 및 개체 참조에 대해 설명하고 XMLA 명령 내에서 식별자 및 참조를 사용하는 방법에 대해 설명합니다.|  
|[트랜잭션 관리 &#40;XMLA&#41;](managing-transactions-xmla.md)|사용 하는 방법에 자세히 설명 된 [BeginTransaction](../xmla/xml-elements-commands/begintransaction-element-xmla.md), [CommitTransaction](../xmla/xml-elements-commands/committransaction-element-xmla.md), 및 [RollbackTransaction](../xmla/xml-elements-commands/rollbacktransaction-element-xmla.md) 명시적으로 정의 하 고 현재 XMLA에서 트랜잭션을 관리 하는 명령 세션입니다.|  
|[명령 취소 &#40;XMLA&#41;](../multidimensional-models-scripting-language-assl-xmla/canceling-commands-xmla.md)|사용 하는 방법에 설명 된 [취소](../xmla/xml-elements-commands/cancel-element-xmla.md)명령, 세션 및 XMLA에 대 한 연결을 취소 하는 명령입니다.|  
|[일괄 처리 작업 수행 &#40;XMLA&#41;](performing-batch-operations-xmla.md)|사용 하는 방법에 설명 된 [일괄 처리](../xmla/xml-elements-commands/batch-element-xmla.md) 순차적으로 또는 병렬로: 동일한 트랜잭션 내에서 또는 단일 XMLA를 사용 하 여 별도 트랜잭션으로 실행 될 여러 XMLA 명령을 명령을 [Execute](../xmla/xml-elements-methods-execute.md) 메서드.|  
|[개체 만들기 및 변경 &#40;XMLA&#41;](creating-and-altering-objects-xmla.md)|사용 하는 방법에 설명 된 [만들기](../xmla/xml-elements-commands/create-element-xmla.md), [Alter](../xmla/xml-elements-commands/alter-element-xmla.md), 및 [삭제](../xmla/xml-elements-commands/delete-element-xmla.md) 명령, Analysis Services Scripting Language (ASSL) 요소와 함께 정의 하려면, 변경 또는 제거 개체는 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 인스턴스.|  
|[잠금 및 데이터베이스를 잠금 해제 &#40;XMLA&#41;](locking-and-unlocking-databases-xmla.md)|사용 하는 방법에 자세히 설명 된 [잠금](../xmla/xml-elements-commands/lock-element-xmla.md) 및 [잠금 해제](../xmla/xml-elements-commands/unlock-element-xmla.md) 잠금 해제 하는 명령을 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 데이터베이스입니다.|  
|[개체 처리 &#40;XMLA&#41;](processing-objects-xmla.md)|사용 하는 방법에 설명 된 [프로세스](../xmla/xml-elements-commands/process-element-xmla.md) 명령을 프로세스에는 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 개체입니다.|  
|[파티션 병합 &#40;XMLA&#41;](merging-partitions-xmla.md)|사용 하는 방법에 설명 된 [MergePartitions](../xmla/xml-elements-commands/mergepartitions-element-xmla.md) 파티션을 병합 하는 명령을 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 인스턴스.|  
|[집계 디자인 &#40;XMLA&#41;](designing-aggregations-xmla.md)|사용 하는 방법에 설명 된 [DesignAggregations](../xmla/xml-elements-commands/designaggregations-element-xmla.md) 명령 반복 또는 일괄 처리 모드는 집계 디자인에 대 한 집계를 디자인 하 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]합니다.|  
|[백업, 복원 및 데이터베이스를 동기화 할 &#40;XMLA&#41;](backing-up-restoring-and-synchronizing-databases-xmla.md)|사용 하는 방법에 설명는 [백업](../xmla/xml-elements-commands/backup-element-xmla.md) 및 [복원](../xmla/xml-elements-commands/restore-element-xmla.md) 명령을 백업 및 복원 하는 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 백업 파일에서 데이터베이스입니다.<br /><br /> 또한 사용 하는 방법에 설명 된 [동기화](../xmla/xml-elements-commands/synchronize-element-xmla.md) 동기화 하는 명령을 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 동일한 인스턴스 또는 다른 인스턴스에서 기존 데이터베이스를 사용 하 여 데이터베이스입니다.|  
|[삽입, 업데이트 및 멤버 삭제 &#40;XMLA&#41;](inserting-updating-and-dropping-members-xmla.md)|사용 하는 방법에 설명 된 [삽입](../xmla/xml-elements-commands/insert-element-xmla.md), [업데이트](../xmla/xml-elements-commands/update-element-xmla.md), 및 [Drop](../xmla/xml-elements-commands/drop-element-xmla.md) 를 추가, 변경 또는 쓰기 가능 차원에서 멤버를 삭제 합니다.|  
|[셀 업데이트 &#40;XMLA&#41;](updating-cells-xmla.md)|사용 하는 방법에 설명 된 [UpdateCells](../xmla/xml-elements-commands/updatecells-element-xmla.md) 쓰기 가능한 파티션의 셀 값을 변경 하는 명령입니다.|  
|[캐시 관리 &#40;XMLA&#41;](managing-caches-xmla.md)|사용 하는 방법에 자세히 설명 된 [ClearCache](../xmla/xml-elements-commands/clearcache-element-xmla.md) 의 캐시를 지울 명령을 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 개체입니다.|  
|[추적 모니터링 &#40;XMLA&#41;](monitoring-traces-xmla.md)|사용 하는 방법에 설명 된 [Subscribe](../xmla/xml-elements-commands/subscribe-element-xmla.md) 구독 하 고 기존 추적에서 모니터링 하는 명령을 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 인스턴스.|  
  
## <a name="data-mining-with-xmla"></a>XMLA를 사용한 데이터 마이닝  
 XML for Analysis는 데이터 마이닝 스키마 행 집합을 완전하게 지원합니다. 사용 하 여 데이터 마이닝 모델을 쿼리 하는 것에 대 한 정보를 제공 하는 이러한 행 집합은 [Discover](../xmla/xml-elements-methods-discover.md) 메서드. 데이터 마이닝 스키마 행 집합에 대 한 자세한 내용은 참조 하십시오. [데이터 마이닝 스키마 행 집합](../schema-rowsets/data-mining/data-mining-schema-rowsets.md) 
  
 DMX에 대 한 자세한 내용은 참조 [Data Mining Extensions &#40;DMX&#41; 참조](/sql/dmx/data-mining-extensions-dmx-reference)합니다.  
  
## <a name="namespace-and-schema"></a>네임스페이스 및 스키마  
  
### <a name="namespace"></a>Namespace  
 이 사양에 정의 된 스키마는 XML 네임 스페이스를 사용 하 여 http://schemas.microsoft.com/AnalysisServices/2003/Engine 과 표준 약어 "DDL"을 선택 합니다.  
  
### <a name="schema"></a>스키마  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 개체 정의 언어에 대한 XSD(XML 스키마 정의 언어) 스키마의 정의는 이 섹션에 설명된 스키마 요소 및 계층 구조의 정의를 기반으로 합니다.  
  
## <a name="extensibility"></a>확장성  
 개체 정의 언어 스키마의 확장성은 모든 개체에 포함된 `Annotation` 요소를 사용하여 제공됩니다. 이 요소는 다음 규칙에 따라 DDL을 정의하는 대상 네임스페이스 이외의 모든 XML 네임스페이스에서 유효한 XML을 포함할 수 있습니다.  
  
-   XML은 요소만 포함할 수 있습니다.  
  
-   각 요소 이름은 고유해야 합니다. `Name` 값은 대상 네임스페이스를 참조하는 것이 좋습니다.  
  
 이러한 규칙은 `Annotation` 태그의 내용이 DSO(의사 결정 지원 개체) 9.0을 통해 이름/값 쌍 집합으로 표시되기 위해 반드시 필요합니다.  
  
 자식 요소로 묶이지 않은 `Annotation` 태그 내 주석 및 공백은 그대로 유지되지 않을 수 있습니다. 또한 모든 요소는 읽기/쓰기 요소여야 하며 읽기 전용 요소는 무시됩니다.  
  
 서버에서 스키마에 정의된 요소의 파생 유형을 대체할 수 없는 경우에는 개체 정의 언어 스키마가 닫힙니다. 따라서 서버에서는 여기에 정의된 요소 집합만 허용되며 다른 요소나 특성은 허용되지 않습니다. 알 수 없는 요소의 경우 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 엔진에서 오류가 발생합니다.  
  
## <a name="see-also"></a>관련 항목  
 [개발 analysis Services Scripting Language &#40;ASSL&#41;](../multidimensional-models/scripting-language-assl/developing-with-analysis-services-scripting-language-assl.md)   
 [Microsoft OLAP 아키텍처 이해](../multidimensional-models/olap-physical/understanding-microsoft-olap-architecture.md)  
  
  