---
title: "데이터베이스 다이어그램 소유권 이해(Visual Database Tools) | Microsoft 문서"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vdt.diagnostic.CannotOpenWithInvalidOwner
helpviewer_keywords:
- diagrams [SQL Server], ownership
- database diagrams [SQL Server], ownership
- owners [SQL Server], database diagrams
ms.assetid: 4a27a48e-c4ef-4017-82b8-0cac4d0bbcac
caps.latest.revision: 5
author: stevestein
ms.author: sstein
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: fd71d87c5a2967d23f72b7402c7ca95a8822b688
ms.lasthandoff: 04/11/2017

---
# <a name="understand-database-diagram-ownership-visual-database-tools"></a>데이터베이스 다이어그램 소유권 이해(Visual Database Tools)
데이터베이스 다이어그램 디자이너를 사용하려면 먼저 db_owner 역할([!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 데이터베이스의 역할)의 멤버로 설정하여 다이어그램에 대한 액세스를 제어해야 합니다. 각 다이어그램에는 반드시 한 명의 소유자(다이어그램을 만든 사용자)가 있어야 합니다. 다이어그램 설정에 대한 자세한 내용은 [데이터베이스 다이어그램 디자이너 설정(Visual Database Tools)](../../ssms/visual-db-tools/set-up-database-diagram-designer-visual-database-tools.md)을 참조하세요.  
  
다이어그램 소유권과 관련하여 유의할 점은 다음과 같습니다.  
  
-   데이터베이스에 대한 액세스 권한이 있는 사용자는 누구든지 다이어그램을 만들 수 있지만, 일단 작성된 다이어그램은 db_owner 역할의 멤버와 다이어그램 작성자만 볼 수 있습니다.  
  
-   다이어그램의 소유권은 db_owner 역할이 있는 멤버에게만 전달할 수 있습니다. 다이어그램 소유권을 전달하려면 이전 소유자가 데이터베이스에서 제거된 상태여야 합니다.  
  
-   다이어그램의 소유자가 데이터베이스에서 제거된 후에도 db_owner 역할을 가진 멤버가 해당 다이어그램을 열려고 시도할 때까지 이 다이어그램은 데이터베이스에 유지됩니다. db_owner 멤버는 이러한 다이어그램을 열려고 시도할 때 다이어그램의 소유권을 계승할지 여부를 선택할 수 있습니다.  
  
## <a name="see-also"></a>관련 항목:  
[데이터베이스 다이어그램 작업(Visual Database Tools)](../../ssms/visual-db-tools/work-with-database-diagrams-visual-database-tools.md)  
[데이터베이스 다이어그램 디자이너 설정(Visual Database Tools)](../../ssms/visual-db-tools/set-up-database-diagram-designer-visual-database-tools.md)  
  
