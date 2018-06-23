---
title: '통합 문서의 데이터 연결 경로가 로컬 드라이브의 파일을 가리키거나 잘못된 URI입니다. 다음과 같은 연결을 새로 고치지 못했습니다: PowerPivot 데이터 | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bd22e41a-0931-4d32-888a-633a3046fc5e
caps.latest.revision: 5
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 5cb4c4794a59d203c119f09fba83fedeb7edb458
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36091829"
---
# <a name="the-data-connection-path-in-the-workbook-points-to-a-file-on-the-local-drive-or-is-an-invalid-uri-the-following-connections-failed-to-refresh-powerpivot-data"></a>통합 문서의 데이터 연결 경로가 로컬 드라이브의 파일을 가리키거나 잘못된 URI입니다. PowerPivot 데이터 연결을 새로 고치지 못했습니다.
  Excel 서비스는 포함된 데이터 원본에 연결할 수 없는 경우 PowerPivot 데이터를 포함하는 Excel 통합 문서에 대해 이 오류를 반환합니다.  
  
## <a name="details"></a>설명  
  
|||  
|-|-|  
|적용 대상|SharePoint용 PowerPivot|  
|제품 버전|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]|  
|원인|Excel 서비스가 신뢰할 수 있는 데이터 연결 라이브러리에 있는 .odc 파일로부터의 데이터 연결만 허용하도록 구성되어 있습니다.|  
|메시지 텍스트|통합 문서의 데이터 연결 경로가 로컬 드라이브의 파일을 가리키거나 잘못된 URI입니다. PowerPivot 데이터 연결을 새로 고치지 못했습니다.|  
  
## <a name="explanation"></a>설명  
 PowerPivot 통합 문서에는 포함된 데이터 연결이 들어 있습니다. 슬라이서 및 필터를 통한 통합 문서 상호 작용을 지원하려면 포함된 연결 정보를 통한 외부 데이터 액세스를 허용하도록 Excel 서비스를 구성해야 합니다. 팜의 PowerPivot 서버에 로드된 PowerPivot 데이터를 검색하려면 외부 데이터에 액세스해야 합니다.  
  
## <a name="user-action"></a>사용자 동작  
 포함된 데이터 원본 연결을 허용하도록 구성 설정을 변경합니다.  
  
1.  중앙 관리의 응용 프로그램 관리에서 **서비스 응용 프로그램 관리**를 클릭합니다.  
  
2.  **Excel 서비스 응용 프로그램**을 클릭합니다.  
  
3.  **신뢰할 수 있는 파일 위치**를 클릭합니다.  
  
4.  **http://** 또는 구성할 위치를 클릭합니다.  
  
5.  외부 데이터의 외부 데이터 허용에서 **신뢰할 수 있는 데이터 연결 라이브러리 및 포함 라이브러리**를 클릭합니다.  
  
6.  **확인**을 클릭합니다.  
  
 또는 PowerPivot 통합 문서를 포함하는 사이트에 대한 신뢰할 수 있는 위치를 새로 만든 다음 해당 사이트에 대한 구성 설정을 수정할 수도 있습니다. 자세한 내용은 [Create a trusted location for PowerPivot sites in Central Administration](create-a-trusted-location-for-power-pivot-sites-in-central-administration.md)을 참조하세요.  
  
  