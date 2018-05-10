---
title: AMO 기본 클래스 | Microsoft Docs
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: amo
ms.topic: article
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: ffa7973757ce41a3975bcbb70170679109527e42
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
---
# <a name="amo-fundamental-classes"></a>AMO 기본 클래스
  AMO(Analysis Management Objects) 작업은 기본 클래스에서 시작합니다. 이러한 클래스를 통해 응용 프로그램에 사용할 나머지 개체의 환경을 설정합니다. 기본 클래스에는 <xref:Microsoft.AnalysisServices.Server>, <xref:Microsoft.AnalysisServices.Database>, <xref:Microsoft.AnalysisServices.DataSource> 및 <xref:Microsoft.AnalysisServices.DataSourceView> 개체가 포함됩니다.  
  
 다음 그림에서는 이 항목에 설명된 클래스의 관계를 보여 줍니다.  
  
 ![AMO 기본 클래스](../../../analysis-services/multidimensional-models/analysis-management-objects/media/amo-fundamentalclasses.gif "AMO 기본 클래스")  
  
 이 항목에는 다음과 같은 섹션이 포함되어 있습니다.  
  
-   [서버 개체](#ServerObjects)  
  
-   [데이터베이스 개체](#DatabaseObjects)  
  
-   [DataSource 및 DataSourceView 개체](#DSandDSV)  
  
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
  
## <a name="see-also"></a>관련 항목:  
 <xref:Microsoft.AnalysisServices>   
 [AMO 클래스 소개](../../../analysis-services/multidimensional-models/analysis-management-objects/amo-classes-introduction.md)   
 [AMO 기본 개체 프로그래밍](../../../analysis-services/multidimensional-models/analysis-management-objects/programming-amo-fundamental-objects.md)  
  
  