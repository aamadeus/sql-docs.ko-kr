---
title: 게시 데이터베이스 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.rep.newpubwizard.publicationdatabase.f1
ms.assetid: a9fafc9b-9963-4b59-97a0-3472158fa665
caps.latest.revision: 22
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: cb4f3f0e770b1511145f079908e0fd019d1b0c57
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36091704"
---
# <a name="publication-database"></a>게시 데이터베이스
  게시 데이터베이스는 복제될 데이터 및 데이터베이스 개체의 원본인 게시자에 있는 데이터베이스입니다. 복제에 사용할 각 게시 데이터베이스는 활성화되어 있어야 합니다. 데이터베이스는 **sysadmin** 고정 서버 역할의 멤버가 다음과 같은 작업을 수행할 때 활성화됩니다.  
  
-   새 게시 마법사를 사용하여 데이터베이스에 게시를 만듭니다.  
  
-   **게시자 속성** 대화 상자에서 데이터베이스를 선택합니다.  
  
-   **sp_replicationdboption** 을 실행하여 **publish** (스냅숏 또는 트랜잭션 게시의 경우) 또는 **merge publish** (병합 게시의 경우) 옵션을 **True**로 설정합니다.  
  
## <a name="options"></a>변수  
 **데이터베이스**  
 게시할 데이터 및 데이터베이스 개체를 포함하는 데이터베이스의 이름을 선택합니다.  
  
## <a name="see-also"></a>관련 항목  
 [데이터 및 데이터베이스 개체 게시](publish/publish-data-and-database-objects.md)   
 [Create a Publication](publish/create-a-publication.md)   
 [배포자 및 게시자 속성 보기 및 수정](view-and-modify-distributor-and-publisher-properties.md)   
 [sp_replicationdboption&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-replicationdboption-transact-sql)  
  
  