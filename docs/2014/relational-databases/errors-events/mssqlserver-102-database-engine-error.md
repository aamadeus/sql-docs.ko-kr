---
title: MSSQLSERVER_102 | Microsoft 문서
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
- 102 (Database Engine error)
ms.assetid: 264dc1a2-c8a0-4c89-b5f6-951baf950299
caps.latest.revision: 7
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: ea5648a886a9b3e9c0ea2e1a9f7cdb04565444e2
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36172199"
---
# <a name="mssqlserver102"></a>MSSQLSERVER_102
    
## <a name="details"></a>설명  
  
|||  
|-|-|  
|제품 이름|SQL Server|  
|이벤트 ID|102|  
|이벤트 원본|MSSQLSERVER|  
|구성 요소|SQLEngine|  
|심볼 이름|P_SYNTAXERR2|  
|메시지 텍스트|'%.*ls' 근처의 구문이 잘못되었습니다.|  
  
## <a name="explanation"></a>설명  
 구문 오류를 나타냅니다. 오류로 인해 [!INCLUDE[ssDE](../../includes/ssde-md.md)]에서 문을 처리할 수 없기 때문에 추가 정보를 확인할 수 없습니다.  
  
 이 오류는 90 또는 100 호환성 모드가 아닐 경우 사용되지 않는 RC4 또는 RC4_128 암호화를 사용하여 대칭 키를 만들려고 할 때 발생할 수 있습니다.  
  
## <a name="user-action"></a>사용자 동작  
 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문에서 구문 오류를 검색하십시오.  
  
 RC4 또는 RC4_128을 사용하여 대칭 키를 만들 경우 AES 알고리즘 같은 최신 암호화 기술을 선택하는 것이 좋습니다. RC4를 꼭 사용해야 할 경우에는 ALTER DATABASE SET COMPATIBILITY_LEVEL을 사용하여 데이터베이스 호환성 수준을 90 또는 100으로 설정합니다. 이 옵션은 사용하지 않는 것이 좋습니다.  
  
  