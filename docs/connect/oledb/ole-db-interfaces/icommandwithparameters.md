---
title: ICommandWithParameters | Microsoft Docs
description: ICommandWithParameters 인터페이스
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: ole-db-interfaces
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: reference
author: pmasl
ms.author: Pedro.Lopes
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 9d810ea13512537572bf39fbda938b6b59d64db7
ms.sourcegitcommit: 9f4330a4b067deea396b8567747a6771f35e6eee
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/30/2018
---
# <a name="icommandwithparameters"></a>ICommandWithParameters
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  로 시작 하는 데이터베이스 엔진의에서 향상 된 [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] icommandwithparameters:: Getparameterinfo 예상된 결과 대 한 보다 정확한 설명의 얻을를 허용 합니다. 이전 버전의 CommandWithParameters::GetParameterInfo 반환 하는 값에서 다를 수 있습니다 이러한 보다 정확한 결과 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]합니다. 자세한 내용은 [Metadata Discovery](../../oledb/features/metadata-discovery.md)를 참조하십시오.  
  
 또한 부터는 [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)]전달 되는 값 icommandwithparameters:: Setparameterinfo를 호출할 때는 *pwszName* 매개 변수는 유효한 식별자 여야 합니다. 자세한 내용은 [Database Identifiers](../../../relational-databases/databases/database-identifiers.md)을 참조하세요.  
  
## <a name="see-also"></a>관련 항목:  
 [인터페이스 &#40; OLE db&#41;](../../oledb/ole-db-interfaces/oledb-driver-for-sql-server-ole-db-interfaces.md) 
  
  