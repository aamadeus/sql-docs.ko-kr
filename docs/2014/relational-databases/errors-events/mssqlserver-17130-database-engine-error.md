---
title: MSSQLSERVER_17130 | Microsoft 문서
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
- 17130 (Database Engine error)
ms.assetid: 7ce6afca-221d-402f-89df-da7e74a339a8
caps.latest.revision: 16
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: e4f8a2414ef1d1aba309bdbaffdbcce1d6494a87
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36080863"
---
# <a name="mssqlserver17130"></a>MSSQLSERVER_17130
    
## <a name="details"></a>설명  
  
|||  
|-|-|  
|제품 이름|SQL Server|  
|이벤트 ID|17130|  
|이벤트 원본|MSSQLSERVER|  
|구성 요소|SQLEngine|  
|심볼 이름|INIT_NOLOCKSPACE|  
|메시지 텍스트|구성된 잠금 수에 대한 메모리가 부족합니다. 더 작은 수의 잠금 해시 테이블로 시작되며 이 경우 성능이 저하될 수 있습니다. 데이터베이스 엔진의 이 인스턴스에 대한 추가 메모리를 구성해 줄 것을 데이터베이스 관리자에게 요청하십시오.|  
  
## <a name="explanation"></a>설명  
 메모리가 부족하여 원하는 크기의 잠금 관리자 해시 테이블을 할당할 수 없습니다.  더 작은 해시 테이블을 할당하려는 시도가 수행됩니다.  
  
## <a name="user-action"></a>사용자 동작  
 서버 메모리 구성 매개 변수(min/max server memory)를 확인하고 메모리가 부족한지 확인합니다. SQL Server에서 사용할 수 있는 메모리를 늘립니다.  
  
  