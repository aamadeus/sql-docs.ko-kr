---
title: MSSQLSERVER_21862 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- 21862 (Database Engine error)
ms.assetid: a1d393dd-453b-4d45-9aa5-7d371213e32b
caps.latest.revision: 12
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 61ab48b6cf5fcc108369966308442f7e9137b9c5
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36182797"
---
# <a name="mssqlserver21862"></a>MSSQLSERVER_21862
    
## <a name="details"></a>설명  
  
|||  
|-|-|  
|제품 이름|MSSQLSERVER|  
|이벤트 ID|21862|  
|이벤트 원본|MSSQLSERVER|  
|구성 요소|SQLEngine|  
|심볼 이름|SQLErrorNum21862|  
|메시지 텍스트|'database snapshot' 또는 'database snapshot character' 동기화 메서드를 사용하여 게시에 FILESTREAM 열을 게시할 수 없습니다.|  
  
## <a name="explanation"></a>설명  
 데이터베이스 스냅숏을 통해 FILESTREAM 데이터에 액세스할 수 없으므로 게시의 동기화 메서드에 대해 *database snapshot* 또는 *database_snapshot_character* 매개 변수를 지정하면 스냅숏 에이전트가 FILESTREAM 데이터를 읽을 수 없게 됩니다.  
  
## <a name="user-action"></a>사용자 동작  
 게시 동기화 메서드를 *database snapshot* 또는 *database_snapshot_character*가 아닌 다른 것으로 변경하거나 게시에서 FILESTREAM 열을 제외하세요.  
  
  