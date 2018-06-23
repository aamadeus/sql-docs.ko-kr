---
title: MSSQLSERVER_21899 | Microsoft 문서
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
- 21899 (Database Engine error)
ms.assetid: 32b87a7c-5380-4638-b147-dd78618f6625
caps.latest.revision: 7
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 085d2357d3661d3567d5074cf56fe4eaf2b3e4da
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36081199"
---
# <a name="mssqlserver21899"></a>MSSQLSERVER_21899
    
## <a name="details"></a>설명  
  
|||  
|-|-|  
|제품 이름|SQL Server|  
|이벤트 ID|21899|  
|이벤트 원본|MSSQLSERVER|  
|구성 요소|SQLEngine|  
|심볼 이름|SQLErrorNum21899|  
|메시지 텍스트|'%d' 오류로 인해 리디렉션된 게시자 '%s'에서 원래 게시자 '%s'의 구독자에 대한 sysserver 항목이 있는지 확인하기 위한 쿼리에 실패했습니다(오류 메시지 '%s').|  
  
## <a name="explanation"></a>설명  
 `sp_validate_redirected_publisher`는 원격 서버에 있는 게시자 데이터베이스의 구독 메타데이터 테이블을 쿼리하여 연관된 구독자를 확인합니다. 오류 21899는 이 쿼리에 실패한 경우에 반환됩니다. 유효성 검사 쿼리를 실행하려면 리디렉션된 게시자의 게시된 데이터베이스에 액세스해야 합니다. 원래 게시자에 대해 `sp_adddistpublisher`가 호출될 때 지정된 로그인에 리디렉션된 게시자의 게시된 데이터베이스에 액세스할 수 있는 권한이 없으면 오류 21899가 반환됩니다.  
  
## <a name="user-action"></a>사용자 동작  
 지정된 오류 메시지를 검토하여 실패 원인을 파악하고 적절한 수정 동작을 수행하십시오.  
  
  