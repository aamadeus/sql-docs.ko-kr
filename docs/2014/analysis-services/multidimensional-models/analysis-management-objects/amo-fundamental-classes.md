---
title: AMO 기본 클래스 | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- data sources [AMO]
- AMO, database objects
- AMO, server objects
- Analysis Management Objects, server objects
- database objects [AMO]
- Analysis Management Objects, database objects
- AMO, data sources
- Analysis Management Objects, data sources
ms.assetid: 440e9287-53a2-4db3-9481-1d2ceb6e5b5a
caps.latest.revision: 28
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: ee31478a526dad385d9721256beebc4324cadb60
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36182463"
---
# <a name="amo-fundamental-classes"></a>AMO 기본 클래스
  AMO(Analysis Management Objects) 작업은 기본 클래스에서 시작합니다. 이러한 클래스를 통해 응용 프로그램에 사용할 나머지 개체의 환경을 설정합니다. 기본 클래스에는 <xref:Microsoft.AnalysisServices.Server>, <xref:Microsoft.AnalysisServices.Database>, <xref:Microsoft.AnalysisServices.DataSource> 및 <xref:Microsoft.AnalysisServices.DataSourceView> 개체가 포함됩니다.  
  
 다음 그림에서는 이 항목에 설명된 클래스의 관계를 보여 줍니다.  
  
 ![AMO 기본 클래스](../../../analysis-services/dev-guide/media/amo-fundamentalclasses.gif "AMO 기본 클래스")  
  
  
  
##  <a name="ServerObjects"></a> 서버 개체  
 또한 다음 메서드에 액세스할 수 있습니다.  
  
-   연결 관리: 연결, 연결 끊기, Reconnect 및 GetConnectionState 합니다.  
  
-   트랜잭션 관리: BeginTransaction, CommitTransaction 및 RollbackTransaction 합니다.  
  
-   Backup 및 Restore  
  
-   DDL 실행: CancelCommand, SendXmlaRequest 및을 실행 합니다.  
  
-   메타 데이터 관리: UpdateObjects 및 유효성 검사 합니다.  
  
 서버에 연결하려면 ADOMD.NET 및 OLEDB에서 사용하는 것과 같은 표준 연결 문자열이 필요합니다. 자세한 내용은 참조 <xref:System.Configuration.ConnectionStringSettings.ConnectionString%2A>합니다. 연결 문자열 형식을 사용할 필요 없이 서버 이름을 연결 문자열로 지정할 수도 있습니다.  
  
 사용할 수 있는 메서드 및 속성에 대한 자세한 내용은 <xref:Microsoft.AnalysisServices.Server>의 <xref:Microsoft.AnalysisServices>를 참조하십시오.  
  
##  <a name="DatabaseObjects"></a> 데이터베이스 개체  
 응용 프로그램에서 <xref:Microsoft.AnalysisServices.Database> 개체를 사용하려면 부모 서버 데이터베이스 컬렉션에서 데이터베이스의 인스턴스를 가져와야 합니다. 데이터베이스를 만들려면 서버 데이터베이스 컬렉션에 <xref:Microsoft.AnalysisServices.Database> 개체를 추가한 다음 새 인스턴스를 서버로 업데이트합니다. 데이터베이스를 삭제하려면 Drop 메서드를 사용하여 <xref:Microsoft.AnalysisServices.Database> 개체를 삭제합니다.  
  
 <xref:Microsoft.AnalysisServices.Database> 개체나 <xref:Microsoft.AnalysisServices.Server> 개체에서 BackUp 메서드를 사용하여 데이터베이스를 백업할 수 있지만 데이터베이스를 복원할 때는 <xref:Microsoft.AnalysisServices.Server> 개체에서만 Restore 메서드를 사용할 수 있습니다.  
  
 사용할 수 있는 메서드 및 속성에 대한 자세한 내용은 <xref:Microsoft.AnalysisServices.Database>의 <xref:Microsoft.AnalysisServices>를 참조하십시오.  
  
##  <a name="DSandDSV"></a> DataSource 및 DataSourceView 개체  
 DataSource는 Database 클래스에서 <xref:Microsoft.AnalysisServices.DataSourceCollection>을 사용하여 관리할 수 있습니다. <xref:Microsoft.AnalysisServices.DataSource> 개체에서 Add 메서드를 사용하여 <xref:Microsoft.AnalysisServices.DataSourceCollection>의 인스턴스를 만들 수 있습니다. 또한 <xref:Microsoft.AnalysisServices.DataSource> 개체에서 Remove 메서드를 사용하여 <xref:Microsoft.AnalysisServices.DataSourceCollection>의 인스턴스를 삭제할 수 있습니다.  
  
 <xref:Microsoft.AnalysisServices.DataSourceView> 개체는 Database 클래스의 <xref:Microsoft.AnalysisServices.DataSourceViewCollection> 개체에서 관리됩니다.  
  
 사용할 수 있는 메서드 및 속성에 대한 자세한 내용은 <xref:Microsoft.AnalysisServices.DataSource>의 <xref:Microsoft.AnalysisServices.DataSourceView> 및 <xref:Microsoft.AnalysisServices>를 참조하십시오.  
  
## <a name="see-also"></a>관련 항목  
 <xref:Microsoft.AnalysisServices>   
 [AMO 클래스 소개](amo-classes-introduction.md)   
 [AMO 기본 개체 프로그래밍](programming-amo-fundamental-objects.md)  
  
  