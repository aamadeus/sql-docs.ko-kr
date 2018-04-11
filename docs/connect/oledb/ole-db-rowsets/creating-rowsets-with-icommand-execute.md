---
title: 'Icommand:: Execute를 사용 하 여 행 집합 만들기 | Microsoft Docs'
description: 'Icommand:: Execute를 사용 하 여 행 집합 만들기'
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: ole-db-rowsets
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- rowsets [OLE DB], creating
- OLE DB Driver for SQL Server, rowsets
- OLE DB rowsets, creating
- Execute method
author: pmasl
ms.author: Pedro.Lopes
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: b7b2562c3b8edf44fc7ead6fbba0ecdc577509f4
ms.sourcegitcommit: 9351e8b7b68f599a95fb8e76930ab886db737e5f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2018
---
# <a name="creating-rowsets-with-icommandexecute"></a>ICommand::Execute를 사용하여 행 집합 만들기
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  사용 하 여 생성 된 행 집합에 대 한는 **icommand:: Execute** 메서드, 속성을 결과 행 집합에 명령 텍스트를 제한할 수 있습니다. 이는 동적 명령 텍스트를 지원하는 고객에게 특히 중요합니다.  
  
 OLE DB Driver for SQL Server를 사용할 수 없습니다 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 많은 명령을 통해 생성 되는 여러 행 집합 결과 지 원하는 데 커서입니다. 고객이 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 커서 지원을 필요로 하는 행 집합을 요청할 경우 명령 텍스트가 둘 이상의 행 집합을 해당 결과로 생성하면 오류가 발생합니다. 자세한 내용은 참조 [여러 행 집합 결과 생성 하는 명령을](../../oledb/ole-db-commands/commands-generating-multiple-rowset-results.md)합니다.  
  
 스크롤할 수 있는 OLE DB Driver for SQL Server 행 집합에서 지원 되는 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 커서입니다. [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]에서는 데이터베이스의 다른 사용자가 변경한 내용의 영향을 받는 커서에 제한을 설정합니다. 특히 일부 커서의 행을 정렬할 수 없기 때문에 SQL ORDER BY 절이 포함된 명령을 사용하여 행 집합을 만들려고 하면 작업이 실패할 수 있습니다. 자세한 내용은 참조 [행 집합 및 SQL Server 커서](../../oledb/ole-db-rowsets/rowsets-and-sql-server-cursors.md)합니다.  
  
## <a name="see-also"></a>관련 항목:  
 [행 집합](../../oledb/ole-db-rowsets/rowsets.md)  
  
  