---
title: SQL Server 단위 테스트의 스크립트 | Microsoft Docs
ms.custom:
- SSDT
ms.date: 02/09/2017
ms.prod: sql
ms.technology: ssdt
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 80c5cf62-a9c9-4e9d-8c6f-8eed50a595a7
caps.latest.revision: 10
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: f829c583b0591263eeb5db612983efc18e96fa97
ms.sourcegitcommit: c8f7e9f05043ac10af8a742153e81ab81aa6a3c3
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/17/2018
ms.locfileid: "39085885"
---
# <a name="scripts-in-sql-server-unit-tests"></a>SQL Server 단위 테스트의 스크립트
각 SQL Server 단위 테스트에는 단일 테스트 전 작업, 테스트 작업 및 테스트 후 작업이 포함됩니다. 이러한 작업에는 각각 다음과 같은 항목이 포함됩니다.  
  
-   데이터베이스에서 실행되는 Transact\-SQL 스크립트  
  
-   스크립트 실행으로부터 반환된 결과를 평가하는 0개 이상의 테스트 조건  
  
테스트 작업에서 Transact\-SQL 테스트 스크립트는 모든 SQL Server 단위 테스트에 포함해야 하는 유일한 구성 요소입니다. 테스트 스크립트 자체 외에도 테스트 스크립트가 예상한 값 또는 값 집합을 반환하는지 여부를 확인하기 위해 테스트 조건을 지정할 수도 있습니다. 테스트 작업은 해당 데이터베이스에서 특정 개체를 실행하거나 변경한 후 해당 변경 내용을 평가합니다.  
  
각 테스트 작업에 대해 테스트 전 작업과 테스트 후 작업을 각각 한 개씩 포함할 수 있습니다. 테스트 작업과 비슷하게 각 테스트 전 작업과 테스트 후 작업은 한 개의 Transact\-SQL 스크립트와 0개 이상의 테스트 조건을 포함합니다. 테스트 전 작업을 사용하면 데이터베이스가 테스트 작업 실행을 허용하고 의미 있는 결과를 반환할 수 있는 상태인지 확인할 수 있습니다. 예를 들어 테스트 전 작업을 사용하여 테스트 스크립트가 데이터에 대해 작업을 수행하기 전에 테이블에 해당 데이터가 포함되어 있는지 확인할 수 있습니다. 테스트 전 작업으로 데이터베이스를 준비하고 테스트 작업으로 의미 있는 결과를 반환한 후에는 테스트 후 작업을 사용하여 테스트 전 작업이 실행되기 전의 상태로 데이터베이스를 되돌릴 수 있습니다. 경우에 따라 테스트 후 작업을 사용하여 테스트 작업 결과의 유효성을 검사할 수도 있습니다. 그 이유는 테스트 후 작업이 테스트 작업보다 큰 데이터베이스 권한을 가질 수 있기 때문입니다. 자세한 내용은 [연결 문자열 및 사용 권한 개요](../ssdt/overview-of-connection-strings-and-permissions.md)를 참조하세요.  
  
이러한 세 가지 작업 외에도 모든 SQL Server 단위 테스트의 실행 전 및 실행 후에 실행되는 두 가지 테스트 스크립트(일반 스크립트라고도 함)가 있습니다. 따라서 단일 SQL Server 단위 테스트를 실행하는 동안 최대 5개의 Transact\-SQL 스크립트가 실행될 수 있습니다. 테스트 작업 내에 포함된 Transact\-SQL 스크립트만 필수이고 일반 스크립트 및 테스트 전/테스트 후 작업 스크립트는 선택 사항입니다.  
  
다음 표에서는 SQL Server 단위 테스트와 관련된 스크립트의 전체 목록을 제공합니다.  
  
|**동작**|**스크립트 유형**|**설명**|  
|--------------|-------------------|-------------------|  
|TestInitialize|일반 스크립트(초기화)|(선택 사항) 이 스크립트는 단위 테스트의 모든 테스트 전 및 테스트 작업보다 먼저 실행됩니다. TestInitialize 스크립트는 지정된 테스트 클래스의 각 단위 테스트 전에 실행됩니다. 이 스크립트는 권한 있는 컨텍스트를 사용하여 실행됩니다.|  
|테스트 전|테스트 스크립트|(선택 사항) 이 스크립트는 단위 테스트의 일부입니다. 테스트 전 스크립트는 단위 테스트 내에 있는 테스트 작업 전에 실행됩니다. 이 스크립트는 권한 있는 컨텍스트를 사용하여 실행됩니다.|  
|테스트|테스트 스크립트|(필수) 이 스크립트는 단위 테스트의 일부입니다. 예를 들어 이 스크립트는 테이블 값을 가져오거나, 삽입 또는 업데이트하는 저장 프로시저를 실행할 수 있습니다. 이 스크립트는 실행 컨텍스트를 사용하여 실행됩니다.|  
|테스트 후|테스트 스크립트|(선택 사항) 이 스크립트는 단위 테스트의 일부입니다. 테스트 후 스크립트는 개별 단위 테스트 후에 실행됩니다. 이 스크립트는 권한 있는 컨텍스트를 사용하여 실행됩니다.|  
|TestCleanup|일반 스크립트(정리)|(선택 사항) 이 스크립트는 단위 테스트 후에 실행됩니다. TestCleanup 스크립트는 지정된 테스트 클래스의 모든 단위 테스트 후에 실행됩니다. 이 스크립트는 권한 있는 컨텍스트를 사용하여 실행됩니다.|  
  
이러한 각 스크립트가 실행되는 서로 다른 보안 컨텍스트에 대한 자세한 내용은 [연결 문자열 및 사용 권한 개요](../ssdt/overview-of-connection-strings-and-permissions.md) 및 [SQL Server Data Tools에 필요한 권한](../ssdt/required-permissions-for-sql-server-data-tools.md)의 SQL Server 단위 테스트 권한 섹션을 참조하세요.  
  
## <a name="order-in-which-scripts-are-run"></a>스크립트가 실행되는 순서  
각 스크립트가 실행되는 순서를 이해하는 것이 중요합니다. 이 순서는 변경할 수 없지만 실행할 스크립트를 결정할 수 있습니다. 다음 그림에서는 두 개의 SQL Server 단위 테스트가 포함된 테스트 실행에 사용하기 위해 선택할 수 있는 스크립트와 이러한 스크립트가 실행되는 순서를 보여 줍니다.  
  
![데이터베이스 단위 테스트 두 개](../ssdt/media/twodatabaseunittests.png "데이터베이스 단위 테스트 두 개")  
  
> [!NOTE]  
> SQL Server 데이터베이스 프로젝트 배포가 구성된 경우 테스트 실행 시작 시 권한 있는 컨텍스트 연결 문자열을 사용하여 배포가 수행됩니다. 자세한 내용은 [방법: SQL Server 단위 테스트 실행 구성](../ssdt/how-to-configure-sql-server-unit-test-execution.md)을 참조하세요.  
  
## <a name="initialization-and-cleanup-scripts"></a>초기화 및 정리 스크립트  
SQL Server 단위 테스트 디자이너에서는 TestInitialize 및 TestCleanup 스크립트를 일반 스크립트라고 합니다. 이전 예에서는 두 개의 단위 테스트가 동일 테스트 클래스에 포함되는 것으로 가정합니다. 따라서 이 두 테스트는 동일한 TestInitialize 및 TestCleanup 스크립트를 공유합니다. 이러한 조건은 단일 테스트 클래스 내의 모든 단위 테스트에 대해 항상 적용됩니다. 하지만 테스트 실행에 다른 테스트 클래스의 단위 테스트가 포함된 경우 연관된 테스트 클래스의 일반 스크립트가 단위 테스트 실행 전/후에 실행됩니다.  
  
SQL Server 단위 테스트 디자이너만 사용하여 단위 테스트를 작성할 경우에는 테스트 클래스의 개념에 익숙하지 않을 수 있습니다. **테스트** 메뉴를 열고 **새 테스트**를 클릭하여 SQL Server 단위 테스트를 만들 때마다 SQL Server Data Tools에서 테스트 클래스를 생성합니다. 테스트 클래스는 사용자가 지정한 테스트 이름을 사용해서 **솔루션 탐색기**에 표시되며 .cs 또는 .vb 확장명이 사용됩니다. 각 테스트 클래스 내에서 개별 단위 테스트는 테스트 메서드로 저장됩니다. 하지만 테스트 메서드 수(즉, 단위 테스트)에 관계없이 각 테스트 클래스는 0개 또는 1개의 TestInitialize 및 TestCleanup 스크립트를 포함할 수 있습니다.  
  
TestInitialize 스크립트를 사용하면 테스트 데이터베이스를 준비하고, TestCleanup 스크립트를 사용하면 테스트 데이터베이스를 알려진 상태로 반환할 수 있습니다. 예를 들어 TestInitialize를 사용해서 나중에 실행할 도우미 저장 프로시저를 만들고, 테스트 스크립트에서 다른 저장 프로시저를 테스트할 수 있습니다.  
  
## <a name="pre-test-and-post-test-scripts"></a>테스트 전 및 테스트 후 스크립트  
테스트 전 및 테스트 후 작업과 연관된 스크립트는 각 단위 테스트마다 다를 수 있습니다. 이러한 스크립트를 사용하면 데이터베이스에 대한 증분적인 변경 내용을 설정한 후 해당 변경 내용을 정리할 수 있습니다.  
  
## <a name="see-also"></a>참고 항목  
[SQL Server 단위 테스트 만들기 및 정의](../ssdt/creating-and-defining-sql-server-unit-tests.md)  
[SQL Server 단위 테스트에서 테스트 조건 사용](../ssdt/using-test-conditions-in-sql-server-unit-tests.md)  
  