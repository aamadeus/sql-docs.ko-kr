---
title: '외부 데이터 원본에 대한 연결을 설정하는 동안 오류가 발생했습니다. 다음과 같은 연결을 새로 고치지 못했습니다: PowerPivot 데이터 | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1b951da1-f62d-43d2-b40b-270a4a9ab92c
caps.latest.revision: 5
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 36c9846ec1af5589f7fb29d3486ef11632eb01fd
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36080291"
---
# <a name="an-error-occurred-during-an-attempt-to-establish-a-connection-to-the-external-data-source-the-following-connections-failed-to-refresh-powerpivot-data"></a>외부 데이터 원본에 대한 연결을 설정하는 동안 오류가 발생했습니다. PowerPivot 데이터 연결을 새로 고치지 못했습니다.
  이 오류는 SharePoint용 PowerPivot이 설치되어 있지 않은 서버에서 PowerPivot 데이터를 쿼리하면 발생합니다. 이 오류는 SQL Server Analysis Services(PowerPivot) 서비스가 중지되었거나 이전 버전에서 PowerPivot 데이터를 보려고 시도하는 경우에도 발생합니다.  
  
## <a name="details"></a>설명  
  
|||  
|-|-|  
|적용 대상|SharePoint용 PowerPivot|  
|제품 버전|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]|  
|원인|데이터 연결이 실패했습니다.|  
|메시지 텍스트|외부 데이터 원본에 대한 연결을 설정하는 동안 오류가 발생했습니다. PowerPivot 데이터 연결을 새로 고치지 못했습니다.|  
  
## <a name="explanation"></a>설명  
 SharePoint에 게시된 Excel 통합 문서에서 PowerPivot 데이터를 쿼리할 때 SharePoint 환경에 SharePoint용 PowerPivot 서버가 없거나 SQL Server Analysis Services(PowerPivot) 서비스가 중지된 경우 Excel Services가 이 오류를 반환합니다.  
  
 쿼리 엔진을 사용할 수 없을 때 PowerPivot 데이터를 필터링하거나 조각을 생성하면 이 오류가 발생합니다.  
  
## <a name="user-action"></a>사용자 동작  
 SharePoint용 PowerPivot을 설치하거나 SharePoint용 PowerPivot이 설치된 SharePoint 환경으로 PowerPivot 통합 문서를 이동합니다. 자세한 내용은 [PowerPivot for SharePoint 2010 Installation](../../sql-server/install/powerpivot-for-sharepoint-2010-installation.md)을 참조하세요.  
  
 소프트웨어가 설치되어 있는 경우 SQL Server Analysis Services(PowerPivot) 인스턴스가 실행되고 있는지 확인합니다. 중앙 관리에서 **서버의 서비스 관리** 를 확인합니다. 또한 관리 도구에서 서비스 콘솔 응용 프로그램을 확인합니다.  
  
 SQL Server 2008 R2 버전의 PowerPivot for Excel에서 만든 PowerPivot 통합 문서의 경우 SQL Server 2008 R2 버전의 Analysis Services OLE DB 공급자를 설치해야 합니다. 이 오류는 공급자를 설치했지만 Microsoft.AnalysisServices.ChannelTransport.dll 파일을 등록하지 않은 경우 발생합니다. 파일 등록에 대한 자세한 내용은 [SharePoint 서버에서 Analysis Services OLE DB 공급자 설치](../../sql-server/install/install-the-analysis-services-ole-db-provider-on-sharepoint-servers.md)를 참조하세요.  
  
## <a name="see-also"></a>관련 항목  
 [데이터 연결은 Windows 인증을 사용하지만 사용자 자격 증명을 위임할 수 없습니다. PowerPivot 데이터 연결을 새로 고치지 못했습니다.](the-data-connection-user-could-not-be-delegated.md)  
  
  