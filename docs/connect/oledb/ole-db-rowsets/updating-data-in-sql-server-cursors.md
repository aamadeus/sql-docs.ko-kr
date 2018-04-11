---
title: SQL Server 커서의 데이터 업데이트 | Microsoft Docs
description: SQL Server 커서의 데이터 업데이트
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
- updating data [SQL Server]
- isolation levels [SQL Server]
- delayed update mode [OLE DB]
- immediate update mode [OLE DB]
- cursors [OLE DB]
- data updates [SQL Server], OLE DB
author: pmasl
ms.author: Pedro.Lopes
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: caa6d40c0e643a7c73f66a56740e9aba22a824e0
ms.sourcegitcommit: 9351e8b7b68f599a95fb8e76930ab886db737e5f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2018
---
# <a name="updating-data-in-sql-server-cursors"></a>SQL Server 커서의 데이터 업데이트
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  페치 및를 통해 데이터를 업데이트 하는 경우 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 커서의 경우는 OLE DB Driver for SQL Server 소비자 응용 프로그램은 동일한 고려 사항 및 기타 클라이언트 응용 프로그램에 적용 되는 제약 조건으로 바인딩됩니다.  
  
 동시 데이터 액세스 제어에는 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 커서의 행만 참여합니다. 소비자가 수정이 가능한 행 집합을 요청하면 DBPROP_LOCKMODE에서 동시성 제어를 관리합니다. 소비자는 행 집합을 열기 전에 DBPROP_LOCKMODE 속성을 설정하여 동시 액세스 제어의 수준을 변경합니다.  
  
 트랜잭션이 오랫동안 열려 있을 수 있도록 설계된 클라이언트 응용 프로그램의 경우 트랜잭션 격리 수준 때문에 행 위치 지정에 상당한 시간 지연이 발생할 수 있습니다. 기본적으로는 OLE DB Driver for SQL Server는 DBPROPVAL_TI_READCOMMITTED로 지정 하는 커밋된 읽기 격리 수준을 사용 합니다. OLE DB Driver for SQL Server는 행 집합 동시성이 읽기 전용일 때 더티 읽기 격리를 지원 합니다. 따라서 소비자는 수정이 가능한 행 집합에 더 높은 수준의 격리를 요청할 수 있지만 더 낮은 수준은 요청할 수 없습니다.  
  
## <a name="immediate-and-delayed-update-modes"></a>즉시 및 지연 업데이트 모드  
 즉시 업데이트 모드에서를 호출할 때마다 **irowsetchange:: Setdata** 라운드트립을 사용 하면는 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]합니다. 단일 모든 변경 내용을 전송 하는 더 효율적 소비자 단일 행을 여러 번 변경 된 경우 **SetData** 호출 합니다.  
  
 지연된 업데이트 모드에서는 왕복이로 만들어지는 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 각 행에 표시 된는 *cRows* 및 *rghRows* 의 매개 변수 **irowsetupdate:: Update**합니다.  
  
 두 모드 모두 왕복은 행 집합에 대해 열려 있는 트랜잭션 개체가 없는 경우 고유한 트랜잭션을 나타냅니다.  
  
 사용 하는 **irowsetupdate:: Update**는 OLE DB Driver for SQL Server가 지정 된 각 행을 처리 하려고 합니다. 모든 행에 대 한 잘못 된 데이터, 길이 또는 상태 값 때문에 오류가 발생 SQL Server 처리에 대 한 OLE DB 드라이버를 중지 하지 않습니다. 업데이트에 참여하는 행은 모두 수정되거나 전혀 수정되지 않습니다. 소비자는 반환 된 검사 해야 *prgRowStatus* 는 OLE DB Driver for SQL Server가 DB_S_ERRORSOCCURRED를 반환 하는 경우 특정 행에 대 한 오류를 확인 하는 배열입니다.  
  
 소비자는 행이 특정한 순서로 처리된다고 가정해서는 안 됩니다. 소비자가 두 개 이상의 행에서 수정된 데이터를 순서대로 처리해야 하는 경우에는 응용 프로그램 논리에서 이러한 순서를 설정하고 트랜잭션을 열어 여기에 프로세스를 넣어야 합니다.  
  
## <a name="see-also"></a>관련 항목:  
 [행 집합의 데이터 업데이트](../../oledb/ole-db-rowsets/updating-data-in-rowsets.md)  
  
  