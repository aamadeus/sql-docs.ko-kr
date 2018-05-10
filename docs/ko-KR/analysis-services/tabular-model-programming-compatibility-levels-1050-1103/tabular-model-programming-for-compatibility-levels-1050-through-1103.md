---
title: 테이블 형식 모델 프로그래밍에 대 한 호환성 수준 1050-1103 | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 0ceb461e-12c1-44ea-97ac-b99bf308676b
caps.latest.revision: 16
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 7008c37fd23f351f1e20a09fe3454a1dc8a7f688
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
---
# <a name="tabular-model-programming-for-compatibility-levels-1050-through-1103"></a>테이블 형식 모델 프로그래밍에 대 한 호환성 수준 1050-1103
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  테이블 형식 모델은 분석 및 보고 응용 프로그램에서 사용되는 Analysis Services 데이터를 모델링하는 데 관계형 구문을 사용합니다. 이러한 모델은 테이블 형식 모드에 맞게 구성된 Analysis Service 인스턴스에서 실행되며 이때 요청 시 데이터를 집계하고 계산하는 빠른 테이블 검색 및 저장소용 메모리 내 분석 엔진을 사용합니다.  
  
 사용자 지정 BI 솔루션의 요구 사항이 테이블 형식 모델 데이터베이스에서 가장 잘 충족되는 경우 임의의 Analysis Services 클라이언트 라이브러리 및 프로그래밍 인터페이스를 사용하여 Analysis Services 인스턴스의 테이블 형식 모델과 응용 프로그램을 통합할 수 있습니다. 코드에 포함된 MDX 또는 DAX를 사용하여 테이블 형식 모델 데이터를 쿼리하고 계산할 수 있습니다.  
  
 호환성 수준 1050-1103에서 특정 모델의 Analysis Services의 이전 버전에서 만든 테이블 형식 모델에 대 한 AMO, ADOMD.NET, XMLA, 또는 OLE DB에서 프로그래밍 방식으로 작업 하는 개체가 테이블 형식 모두에 대 한 기본적으로 동일한 지 고 다차원 솔루션입니다. 특히, 다차원 모델에 대해 정의 된 개체 메타 데이터 호환성 수준 1050 ~ 1103 테이블 형식 모델에도 사용 됩니다.  
  
 SQL Server 2016 부터는 테이블 형식 모델 작성 하거나 수를 사용 하 여 테이블 형식 메타 데이터 모델을 정의 1200 이상 호환성 수준으로 업그레이드 합니다. 이 수준에서 메타 데이터 및 프로그래밍은 근본적으로 다릅니다. 참조 [테이블 형식 모델 프로그래밍에 대 한 호환성 수준 1200 이상](../../analysis-services/tabular-model-programming-compatibility-level-1200/tabular-model-programming-for-compatibility-level-1200.md) 및 [Analysis Services 업그레이드](../../database-engine/install-windows/upgrade-analysis-services.md) 자세한 정보에 대 한 합니다.  
  
## <a name="in-this-section"></a>섹션 내용  
 [Business Intelligence & #40;에 대 한 CSDL 주석 CSDLBI & #41;](../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/csdl-annotations-for-business-intelligence-csdlbi.md)  
  
 [1050-1103을 수준 테이블 형식 개체 모델 호환성을 이해 합니다.](../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/representation/understanding-tabular-object-model-at-levels-1050-through-1103.md)  
  
 [CSDL BI 주석에 대 한 기술 참조](../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/conceptual-schema-definition-language-csdl/technical-reference-for-bi-annotations-to-csdl.md)  
  

[IMDEmbeddedData 인터페이스](../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/imdembeddeddata-interface.md)


  
  