---
title: 테이블에서 열 순서 변경 | Microsoft 문서
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
- columns [SQL Server], change order in a table
- column order, change
ms.assetid: cd99ef56-9085-431a-a0fc-58e7add5399f
caps.latest.revision: 14
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 07dbfa235a722220d42e68d7f98485a8a85e829f
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36079481"
---
# <a name="change-column-order-in-a-table"></a>테이블에서 열 순서 변경
  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 에서는 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]를 사용하여 테이블 디자이너에서 열 순서를 변경할 수 있습니다.  
  
> [!CAUTION]  
>  테이블의 열 순서를 변경하면 특정 열 순서에 의존하는 코드나 응용 프로그램에 영향을 줄 수 있습니다. 여기에는 쿼리, 뷰, 저장 프로시저, 사용자 정의 함수, 클라이언트 응용 프로그램 등이 포함됩니다. 따라서 열 순서를 변경할 때는 이러한 결과를 미리 신중하게 고려해야 합니다. 가장 좋은 방법은 응용 프로그램 및 쿼리 수준에서 반환된 열에서 순서를 지정하는 것입니다. SELECT *를 사용해도 테이블에 정의된 순서에 따라 모든 열이 순서대로 반환된다고 가정해서는 안됩니다. 항상 열을 표시하려는 순서에 따라 쿼리 및 응용 프로그램에서 이름으로 열을 지정하세요.  
  
 **항목 내용**  
  
-   **열 순서를 변경하려면**  
  
     다른 도구는 [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="SSMSProcedure"></a> SQL Server Management Studio 사용  
  
#### <a name="to-change-the-column-order"></a>열 순서를 변경하려면  
  
1.  **개체 탐색기**에서 순서를 바꾸려는 열이 있는 테이블을 마우스 오른쪽 단추로 클릭하고 **디자인**을 선택합니다.  
  
2.  순서를 바꾸려는 열 이름의 왼쪽에 있는 상자를 선택합니다.  
  
3.  테이블 내에 다른 위치로 열을 끌어 놓습니다.  
  
##  <a name="TsqlProcedure"></a> Transact-SQL 사용  
 **열 순서를 변경하려면**  
  
 이 작업은 Transact-SQL 문을 사용하여 수행할 수 없습니다.  
  
###  <a name="TsqlExample"></a>  