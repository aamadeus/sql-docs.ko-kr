---
title: ISSCommandWithParameters (OLE DB) | Microsoft Docs
description: ISSCommandWithParameters(OLE DB)
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
apiname:
- ISSCommandWithParameters (OLE DB)
apitype: COM
helpviewer_keywords:
- ISSCommandWithParameters interface
author: pmasl
ms.author: Pedro.Lopes
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: fd350eb8c63a95d0ba64950be2ab689696fef0e5
ms.sourcegitcommit: 9f4330a4b067deea396b8567747a6771f35e6eee
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/30/2018
---
# <a name="isscommandwithparameters-ole-db"></a>ISSCommandWithParameters(OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  **ISSCommandWithParameters** 인터페이스에 대 한 지원을 노출 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] XML 및 사용자 정의 형식 (UDT). 핵심 OLE DB 인터페이스에서 상속 되는 선택적 인터페이스 **ICommandWithParameters**합니다. 상속 되며, 세 가지 방법 외에도 **ICommandWithParameters**; **GetParameterInfo**, **MapParameterNames**, 및 **SetParameterInfo**; **ISSCommandWithParameters** 서버별 데이터 형식을 처리 하는 데 사용 되는 두 개의 새 메서드를 제공 합니다.  
  
> [!NOTE]  
>  **ISSCommandWithParameters** 서비스 구성 요소는 사용 하지만 서비스 구성 요소는이 인터페이스를 사용 하지 않으며 인터페이스를 사용할 수 있습니다.  
  
|메서드|설명|  
|------------|-----------------|  
|[Isscommandwithparameters:: Getparameterproperties &#40; OLE db&#41;](../../oledb/ole-db-interfaces/isscommandwithparameters-getparameterproperties-ole-db.md)|명령에 전달된 각 UDT 또는 XML 매개 변수에 대해 배열의 **SSPARAMPROPS** 속성 집합 구조를 하나씩 반환하지만 다른 유형의 매개 변수에 대해서는 아무 것도 반환되지 않습니다.|  
|[Isscommandwithparameters:: Setparameterproperties &#40; OLE db&#41;](../../oledb/ole-db-interfaces/isscommandwithparameters-setparameterproperties-ole-db.md)|매개 변수별 서수로 매개 변수 속성을 설정하거나, **SSPARAMPROPS** 구조의 배열을 지정하여 대량 매개 변수 속성을 설정합니다.|  
  
## <a name="see-also"></a>관련 항목:  
 [인터페이스 &#40; OLE db&#41;](../../oledb/ole-db-interfaces/oledb-driver-for-sql-server-ole-db-interfaces.md)    
 [XML 데이터 형식 사용](../../oledb/features/using-xml-data-types.md)   
 [사용자 정의 형식 사용](../../oledb/features/using-user-defined-types.md)  
  
  