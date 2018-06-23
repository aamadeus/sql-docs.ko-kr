---
title: MSSQLSERVER_1205 | Microsoft 문서
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
- 1205 (Database Engine error)
ms.assetid: 9fe3f67c-df3c-4642-a3a4-ccc0e138b632
caps.latest.revision: 20
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 6ff71ecae0e352ca47640d3047ae9b2c8a4ecba2
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36173119"
---
# <a name="mssqlserver1205"></a>MSSQLSERVER_1205
    
## <a name="details"></a>설명  
  
|||  
|-|-|  
|제품 이름|SQL Server|  
|이벤트 ID|1205|  
|이벤트 원본|MSSQLSERVER|  
|구성 요소|SQLEngine|  
|심볼 이름|LK_VICTIM|  
|메시지 텍스트|트랜잭션(프로세스 ID %d)이 %.*ls 리소스에서 다른 프로세스와의 교착 상태가 발생하여 실행이 중지되었습니다. 트랜잭션을 다시 실행하십시오.|  
  
## <a name="explanation"></a>설명  
 분리된 트랜잭션에서 리소스에 액세스하는 순서가 적절하지 못하여 교착 상태가 발생합니다. 예를 들어:  
  
-   Transaction2가 **Table2.Row2**를 업데이트하는 동안 Transaction1이 **Table1.Row1**을 업데이트합니다.  
  
-   Transaction1이 **Table2.Row2**의 업데이트를 시도하지만 Transaction2가 커밋되지 않아 차단됩니다.  
  
-   이제 Transaction2가 **Table1.Row1**의 업데이트를 시도하지만 Transaction1이 커밋되지 않아 차단됩니다.  
  
-   Transaction1은 Transaction2가 완료되기를 기다리지만 Transaction2는 Transaction1이 완료되기를 기다리므로 교착 상태가 발생합니다.  
  
 시스템이 이 교착 상태를 발견하고 교착 상태가 발생한 트랜잭션 중 하나를 선택하여 이 메시지를 표시한 후 선택한 트랜잭션을 롤백합니다.  
  
## <a name="user-action"></a>사용자 동작  
 트랜잭션을 다시 실행하십시오. 교착 상태가 발생하지 않도록 응용 프로그램을 수정할 수도 있습니다. 교착 상태가 발생한 트랜잭션을 다시 실행하면 동시에 실행 중인 작업이 무엇인지에 따라 성공할 수도 있습니다.  
  
 교착 상태를 방지하거나 발생하지 않도록 하려면 모든 트랜잭션이 동일한 순서(**Table1**에 액세스한 뒤 **Table2**에 액세스)로 행에 액세스하도록 하세요. 이렇게 하면 차단이 발생할 수는 있으나 교착 상태는 발생하지 않습니다.  
  
  