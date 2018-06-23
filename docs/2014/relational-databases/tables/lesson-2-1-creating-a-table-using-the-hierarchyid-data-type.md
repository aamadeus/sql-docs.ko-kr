---
title: hierarchyid 데이터 형식을 사용하여 테이블 만들기 | Microsoft 문서
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
- HierarchyID
ms.assetid: 0d1f361f-336c-4571-99d1-f4813b2d9fc4
caps.latest.revision: 18
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: ecf8817fb0c153298a53ba1be4c49606c0200a93
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36081051"
---
# <a name="creating-a-table-using-the-hierarchyid-data-type"></a>hierarchyid 데이터 형식을 사용하여 테이블 만들기
  다음 예에서는 직원 데이터와 보고 계층을 포함하는 EmployeeOrg라는 테이블을 만듭니다. 이 테이블은 선택 사항인 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 데이터베이스에 만듭니다. 예를 간단히 유지하기 위해 테이블에는 다음 5개 열만 포함합니다.  
  
-   OrgNode는 계층 관계를 저장하는 `hierarchyid` 열입니다.  
  
-   OrgLevel은 계산 열이며 계층의 각 노드 수준을 저장하는 OrgNode 열을 기반으로 합니다. 이는 너비 우선 인덱스에 사용됩니다.  
  
-   EmployeeID에는 급여와 같은 응용 프로그램에 사용되는 일반적인 직원 ID가 포함됩니다. 새 응용 프로그램 개발 시 응용 프로그램에서 OrgNode를 사용할 수 있으므로 이러한 별도의 EmployeeID 열은 필요하지 않습니다.  
  
-   EmpName에는 직원의 이름이 포함됩니다.  
  
-   Title에는 직원의 직책이 포함됩니다.  
  
### <a name="to-create-the-employeeorg-table"></a>EmployeeOrg 테이블을 만들려면  
  
1.  쿼리 편집기 창에서 다음 코드를 실행하여 `EmployeeOrg` 테이블을 만듭니다. `OrgNode` 열을 클러스터형 인덱스가 있는 기본 키로 지정하면 깊이 우선 인덱스가 생성됩니다.  
  
    ```  
    USE AdventureWorks2012 ;  
    GO  
    CREATE TABLE HumanResources.EmployeeOrg  
    (  
       OrgNode hierarchyid PRIMARY KEY CLUSTERED,  
       OrgLevel AS OrgNode.GetLevel(),  
       EmployeeID int UNIQUE NOT NULL,  
       EmpName varchar(20) NOT NULL,  
       Title varchar(20) NULL  
    ) ;  
    GO  
    ```  
  
2.  다음 코드를 실행하여 `OrgLevel` 및 `OrgNode` 열에 복합 인덱스를 만들어 효율적인 너비 우선 검색을 지원합니다.  
  
    ```  
    CREATE UNIQUE INDEX EmployeeOrgNc1   
    ON HumanResources.EmployeeOrg(OrgLevel, OrgNode) ;  
    GO  
    ```  
  
 이제 테이블에 데이터를 채울 준비가 되었습니다. 다음 태스크에서는 계층 메서드를 사용하여 테이블을 채웁니다.  
  
## <a name="next-task-in-lesson"></a>단원의 다음 태스크  
 [계층 메서드를 사용하여 계층적 테이블 채우기](lesson-2-2-populating-a-hierarchical-table-using-hierarchical-methods.md)  
  
  