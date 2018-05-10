---
title: SortColumn 속성 (RDS) | Microsoft Docs
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.prod: sql
ms.prod_service: drivers
ms.component: reference
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- SortColumn property [RDS]
ms.assetid: f6f80f67-f0fb-4e63-a5f5-8fdf312aac63
caps.latest.revision: 18
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 18b6f1ce79c88562382a2974bfc13049acb39f64
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
---
# <a name="sortcolumn-property-rds"></a>SortColumn 속성 (RDS)
기준 레코드를 정렬할 열을 나타냅니다.  
  
> [!IMPORTANT]
>  Windows 8 및 Windows Server 2012 부터는 RDS 서버 구성 요소가 더 이상에 포함 Windows 운영 체제 (Windows 8 참조 및 [Windows Server 2012 호환성 설명서](https://www.microsoft.com/en-us/download/details.aspx?id=27416) 자세한 세부 정보에 대 한). RDS 클라이언트 구성 요소는 나중 버전의 Windows에서 제거 됩니다. 새 개발 작업에서는 이 기능을 사용하지 않도록 하고, 현재 이 기능을 사용하는 응용 프로그램은 수정하세요. RDS를 사용 하는 응용 프로그램을 마이그레이션해야 합니다. [WCF 데이터 서비스](http://go.microsoft.com/fwlink/?LinkId=199565)합니다.  
  
## <a name="syntax"></a>구문  
  
```  
  
DataControl.SortColumn = String  
```  
  
#### <a name="parameters"></a>매개 변수  
 *DataControl*  
 개체 변수를 나타내는 [.rds입니다 DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md) 개체입니다.  
  
 *문자열*  
 A **문자열** 이름이 나 별칭 레코드를 정렬할 기준이 되는 열을 나타내는 값입니다.  
  
## <a name="remarks"></a>주의  
 **SortColumn**, [SortDirection](../../../ado/reference/rds-api/sortdirection-property-rds.md), [FilterValue](../../../ado/reference/rds-api/filtervalue-property-rds.md), [FilterCriterion](../../../ado/reference/rds-api/filtercriterion-property-rds.md), 및 [FilterColumn](../../../ado/reference/rds-api/filtercolumn-property-rds.md)속성 정렬 및 필터링 기능에서 클라이언트 쪽 캐시를 제공 합니다. 특정 열의 값으로 레코드의 순서 정렬 기능입니다. 전체 동안 찾기 조건에 따라 레코드의 하위 집합을 표시 하는 필터링 기능은 [레코드 집합](../../../ado/reference/ado-api/recordset-object-ado.md) 캐시에 유지 됩니다. [재설정](../../../ado/reference/rds-api/reset-method-rds.md) 메서드는 조건을 실행 하 고 현재 교체 **레코드 집합** 와 업데이트할 수 있는 **레코드 집합**합니다.  
  
 에 대해 정렬 하는 **레코드 집합**, 보류 중인 변경 내용을 먼저 저장 해야 합니다. 사용 하는 경우는 **.rds입니다 DataControl**를 사용할 수 있습니다는 [SubmitChanges](../../../ado/reference/rds-api/submitchanges-method-rds.md) 메서드. 예를 들어 경우 프로그램 **.rds입니다 DataControl** 은 ADC1 명명 된, 코드 것 `ADC1.SubmitChanges`합니다. ADO를 사용 하는 경우 **레코드 집합**를 사용할 수 있습니다는 [UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md) 메서드. 사용 하 여 **UpdateBatch** 은 권장 되는 방법에 대 한 **레코드 집합** 사용 하 여 만든 개체는 [CreateRecordset](../../../ado/reference/rds-api/createrecordset-method-rds.md) 메서드. 예를 들어, 코드 일 수 `myRS.UpdateBatch` 또는 `ADC1.Recordset.UpdateBatch`합니다.  
  
## <a name="applies-to"></a>적용 대상  
 [DataControl 개체(RDS)](../../../ado/reference/rds-api/datacontrol-object-rds.md)  
  
## <a name="see-also"></a>관련 항목:  
 [FilterColumn, FilterCriterion, FilterValue, SortColumn, 및 SortDirection 속성 및 Reset 메서드 예제 (VBScript)](../../../ado/reference/rds-api/filter-column-criterion-value-sortcolumn-sortdirection-example-vbscript.md)   
 [정렬 속성](../../../ado/reference/ado-api/sort-property.md)   
 [SortDirection 속성(RDS)](../../../ado/reference/rds-api/sortdirection-property-rds.md)




