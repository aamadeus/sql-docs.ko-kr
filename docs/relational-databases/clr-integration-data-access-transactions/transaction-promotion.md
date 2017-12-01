---
title: "트랜잭션 승격 | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: clr
ms.reviewer: 
ms.suite: sql
ms.technology: docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- distributed transactions [CLR integration]
- promoting transactions [CLR integration]
- Enlist keyword
- transaction promotion [CLR integration]
ms.assetid: 5bc7e26e-28ad-4198-a40d-8b2c648ba304
caps.latest.revision: "13"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: f37528588c5d302036bb39d3de4349c44120e86f
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2017
---
# <a name="transaction-promotion"></a>트랜잭션 승격
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]트랜잭션 *프로 모션* 필요에 따라 완전히 배포 가능한 트랜잭션으로 자동 승격 수 있는 경량 로컬 트랜잭션에 대해 설명 합니다. 서버의 데이터베이스 트랜잭션 내에서 관리되는 저장 프로시저를 호출하면 로컬 트랜잭션의 컨텍스트에서 CLR(공용 언어 런타임) 코드가 실행됩니다.  데이터베이스 트랜잭션 내에서 원격 서버에 대한 연결을 열면 원격 서버에 대한 연결이 분산 트랜잭션에 참여하고 로컬 트랜잭션이 분산 트랜잭션으로 자동 승격됩니다. 따라서 트랜잭션 승격은 필요할 때까지 분산 트랜잭션의 생성을 지연시켜 분산 트랜잭션의 오버헤드를 최소화합니다. **Enlist** 키워드를 사용하여 트랜잭션 승격을 사용하도록 설정한 경우 트랜잭션 승격이 자동으로 수행되며 개발자 작업이 필요하지 않습니다. .NET Framework Data Provider for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .NET Framework의 클래스를 통해 처리 되는 트랜잭션 승격 지원을 제공 **System.Data.SqlClient** 네임 스페이스입니다.  
  
## <a name="the-enlist-keyword"></a>Enlist 키워드  
 **ConnectionString** 개체의 **SqlConnection** 속성은 **Enlist** 에서 트랜잭션 컨텍스트를 검색하고 자동으로 연결을 분산 트랜잭션에 참여시킬지 여부를 나타내는 **System.Data.SqlClient** 키워드를 지원합니다. 이 키워드를 true(기본값)로 설정하면 해당 연결이 여는 스레드의 현재 트랜잭션 컨텍스트에 자동으로 참여합니다. 이 키워드를 false로 설정하면 SqlClient 연결이 분산 트랜잭션과 상호 작용하지 않습니다. 연결 문자열에 **Enlist** 를 지정하지 않은 경우 연결을 열 때 해당 키워드가 검색되면 연결이 자동으로 분산 트랜잭션에 참여합니다.  
  
## <a name="distributed-transactions"></a>분산 트랜잭션  
 분산 트랜잭션은 일반적으로 많은 시스템 리소스를 사용합니다. MS DTC([!INCLUDE[msCoName](../../includes/msconame-md.md)] Distributed Transaction Coordinator)는 이러한 트랜잭션을 관리하고 해당 트랜잭션에서 액세스되는 모든 리소스 관리자를 통합합니다. 반면에 특별 한 형태의 트랜잭션 승격 한 **System.Transactions** 트랜잭션에 작업을 단순 효과적으로 위임 하 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 트랜잭션. **System.Transactions**, **System.Data.SqlClient**, 및 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 필요에 따라이 트랜잭션을 완전 분산 트랜잭션으로 승격 하는 트랜잭션 처리 관련된 작업을 조정 합니다.  
  
 트랜잭션 승격을 사용하면 활성 **TransactionScope** 트랜잭션을 사용하여 연결을 열고 다른 연결은 열지 않을 때 완전 분산 트랜잭션의 추가 오버헤드를 발생시키지 않고 트랜잭션이 경량 트랜잭션으로 커밋된다는 이점이 있습니다. 에 대 한 자세한 내용은 **TransactionScope**, 참조 [System.Transactions를 사용 하 여](../../relational-databases/clr-integration-data-access-transactions/using-system-transactions.md)합니다.  
  
## <a name="see-also"></a>관련 항목:  
 [CLR 통합 및 트랜잭션](../../relational-databases/clr-integration-data-access-transactions/clr-integration-and-transactions.md)  
  
  