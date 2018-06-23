---
title: ADOMD.NET 클라이언트 프로그래밍 | Microsoft Docs
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
- programming [ADOMD.NET]
- ADOMD.NET, programming
ms.assetid: 55156115-ecd1-4ed9-876e-23406af9bbf9
caps.latest.revision: 41
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 9faa64cce77c883ed6adb86bca6d50f32f015c97
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36184592"
---
# <a name="adomdnet-client-programming"></a>ADOMD.NET 클라이언트 프로그래밍
  ADOMD.NET 클라이언트 구성 요소는 `Microsoft.AnalysisServices.AdomdClient` 네임스페이스(microsoft.analysisservices.adomdclient.dll) 안에 있습니다. 이러한 클라이언트 구성 요소가 클라이언트에 대 한 기능 및 중간 계층 응용 프로그램을 쉽게 쿼리 데이터와 메타 데이터는 분석 데이터 저장소에서 제공와 같은 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]합니다.  
  
## <a name="using-the-adomdnet-client-objects"></a>ADOMD.NET 클라이언트 개체 사용  
 분석 데이터 원본을 쿼리할 경우 일반적인 일련의 태스크를 수행해야 합니다. 다음 표에서는 쿼리 수행과 같이 ADOMD.NET 클라이언트 개체를 사용할 때 필요한 일반적인 태스크를 보여 줍니다.  
  
|태스크|Description|  
|----------|-----------------|  
|[ADOMD.NET에서 연결 설정](connections-in-adomd-net.md)|ADOMD.NET에서 <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection> 개체를 사용하여 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 데이터베이스와 같은 분석 데이터 원본에 대한 연결을 설정합니다. <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection> 개체를 사용하여 분석 데이터 원본에 대해 명령을 실행하고 데이터 및 메타데이터를 검색할 수 있습니다.|  
|[분석 데이터 원본에서 메타데이터 검색](retrieving-metadata-from-an-analytical-data-source.md)|연결이 설정된 후에는 다양한 개체를 사용하여 내부 데이터 원본에 대한 정보를 검색할 수 있습니다. 응용 프로그램에서 이 기능을 사용하여 연결된 데이터 원본을 적용할 수 있습니다.|  
|[분석 데이터 원본에 대한 명령 실행](executing-commands-against-an-analytical-data-source.md)|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand> 개체는 내부 분석 데이터 원본에 대한 명령을 실행하는 데 필요한 인터페이스를 제공합니다.|  
|[분석 데이터 원본에서 데이터 검색](retrieving-data-from-an-analytical-data-source.md)|명령을 실행한 후 <xref:Microsoft.AnalysisServices.AdomdClient.CellSet>, <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader> 또는 `System.XmlReader` 개체를 사용하여 데이터를 검색하고 구문 분석할 수 있습니다.|  
|[ADOMD.NET에서 트랜잭션 수행](../../relational-databases/native-client-ole-db-transactions/transactions.md)|이 표의 이전 행에 나열된 모든 동작은 커밋된 읽기 트랜잭션 내에서 발생할 수 있습니다. 데이터를 읽는 동안 더티 읽기를 방지하기 위해 공유 잠금이 유지되지만 트랜잭션이 끝나기 전에 데이터가 변경되어 반복되지 않은 읽기나 팬텀 데이터가 생성될 수도 있습니다. <xref:Microsoft.AnalysisServices.AdomdClient.AdomdTransaction> 개체는 ADOMD.NET에서 트랜잭션 기능을 제공합니다.|  
  
 ADOMD.NET 개체 계층 구조와의 상호 작용은 일반적으로 다음 표에 설명된 최상위 레이어에 있는 하나 이상의 개체에서 시작됩니다.  
  
|수행할 작업|사용 개체|  
|--------|---------------------|  
|분석 데이터 원본에 연결|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection><br /> <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection> 개체는 데이터 원본 및 데이터 원본 메타데이터 모두에 대한 연결을 나타냅니다. 예를 들어에 연결할 수는 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] (.cub) 로컬 큐브 파일을 선택한 다음 검사는 <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.Cubes%2A> 분석 데이터 원본에 있는 큐브에 대 한 메타 데이터를 가져올 속성입니다. 또한 이 개체는 모든 .NET Framework 데이터 공급자에 필요한 인터페이스인 `IDbConnection` 인터페이스의 구현을 나타냅니다.|  
|데이터 원본의 데이터 마이닝 기능 검색|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection><br /> <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection> 개체는 여러 마이닝 컬렉션을 노출합니다.<br /><br /> - <xref:Microsoft.AnalysisServices.AdomdClient.MiningModelCollection> 데이터 원본의 모든 마이닝 모델의 목록을 포함 합니다.<br />- <xref:Microsoft.AnalysisServices.AdomdClient.MiningServiceCollection> 사용 가능한 마이닝 알고리즘에 대 한 정보를 제공 합니다.<br />- <xref:Microsoft.AnalysisServices.AdomdClient.MiningStructureCollection> 서버에서 마이닝 구조에 대 한 정보를 노출 합니다.|  
|데이터 원본 쿼리|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand><br /> <xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand> 개체는 서버로 전송될 쿼리 또는 문을 나타냅니다. 데이터 원본에 연결된 후에는 <xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand> 개체를 사용하여 MDX(Multidimensional Expressions) 또는 데이터 마이닝 DMX(Data Mining Extensions)와 같은 지원되는 언어로 문을 실행할 수 있습니다. <xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand> 개체를 사용하여 <xref:Microsoft.AnalysisServices.AdomdClient.CellSet> 또는 <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader> 개체 형식으로 결과를 반환할 수도 있습니다.|  
|빠르고 효율적인 방법으로 데이터 검색|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader><br /> <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader>는 <xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand.Execute%2A> 개체의 <xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand.ExecuteReader%2A> 또는 <xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand> 메서드를 호출하여 만들 수 있습니다. 이 개체는 .NET Framework 클래스 라이브러리의 `IDbDataReader` 네임스페이스에서 `System.Data` 인터페이스를 구현합니다.|  
|많은 양의 메타데이터를 사용하여 분석 데이터 검색|<xref:Microsoft.AnalysisServices.AdomdClient.CellSet><br /> <xref:Microsoft.AnalysisServices.AdomdClient.CellSet>은 <xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand.Execute%2A>의 <xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand.ExecuteCellSet%2A> 또는 <xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand> 메서드를 호출하여 만들 수 있습니다. <xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand>에서 <xref:Microsoft.AnalysisServices.AdomdClient.CellSet>이 반환되면 <xref:Microsoft.AnalysisServices.AdomdClient.CellSet>에 들어 있는 분석 데이터를 검사할 수 있습니다.|  
|사용 가능한 차원, 측정값, 명명된 집합 등의 큐브에 대한 메타데이터 검색|<xref:Microsoft.AnalysisServices.AdomdClient.CubeDef><br /> <xref:Microsoft.AnalysisServices.AdomdClient.CubeDef>는 큐브에 대한 메타데이터를 나타냅니다. <xref:Microsoft.AnalysisServices.AdomdClient.CubeDef>는 <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection>을 통해 참조됩니다.|  
|`System.Data.IDbDataAdapter` 인터페이스를 사용하여 데이터 검색|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataAdapter><br /> <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataAdapter>는 기존 .NET Framework 클라이언트 응용 프로그램에 대한 읽기 전용 지원을 제공합니다.|  
  
## <a name="see-also"></a>관련 항목  
 [ADOMD.NET 서버 프로그래밍](../multidimensional-models-adomd-net-server/adomd-net-server-programming.md)   
 [ADOMD.NET을 사용하여 개발](../multidimensional-models/adomd-net/developing-with-adomd-net.md)  
  
  