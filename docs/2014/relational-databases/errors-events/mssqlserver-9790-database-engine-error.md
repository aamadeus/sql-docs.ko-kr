---
title: MSSQLSERVER_9790 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- 9790 (Database Engine error)
ms.assetid: 83fd379f-5deb-4f97-8cb4-282e3d3fed94
caps.latest.revision: 13
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: abc78d3fa5ef749afc32a9a7efab6c9df9a15223
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36081106"
---
# <a name="mssqlserver9790"></a>MSSQLSERVER_9790
    
## <a name="details"></a>설명  
  
|||  
|-|-|  
|제품 이름|SQL Server|  
|이벤트 ID|9790|  
|이벤트 원본|MSSQLSERVER|  
|구성 요소|SQLEngine|  
|심볼 이름|SB3_XMIT_ERROR_ENTRANCE_BROKER_SINGLE_USER|  
|메시지 텍스트|들어오는 메시지를 라우팅할 수 없습니다. 라우팅 정보를 포함하는 시스템 데이터베이스 MSDB가 단일 사용자 모드입니다.|  
  
## <a name="explanation"></a>설명  
 MSDB 데이터베이스가 단일 사용자 모드에 있었기 때문에 네트워크를 통해 수신한 메시지를 분류하려고 하는 동안 오류가 발생했습니다.  
  
## <a name="user-action"></a>사용자 동작  
 ALTER DATABASE 명령을 사용하여 MSDB를 다중 사용자 모드로 변경합니다.  
  
  