---
title: ExpirationDate 속성 (SecurityCertificate 클래스) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
apiname:
- ExpirationDate Property (SecurityCertificate Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- ExpirationDate property
ms.assetid: b7fbb9e9-85c1-475b-8e49-7c82fb3740aa
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: cf2b4cd081eb36d74438851094284b6e98d55ba8
ms.sourcegitcommit: 9c6a37175296144464ffea815f371c024fce7032
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/15/2018
ms.locfileid: "51656162"
---
# <a name="expirationdate-property-securitycertificate-class"></a>ExpirationDate 속성(SecurityCertificate 클래스)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  보안 인증서의 유효 기간 끝 날짜를 가져옵니다.  
  
## <a name="syntax"></a>구문  
  
```  
  
object.ExpirationDate [= value]  
```  
  
## <a name="parts"></a>부분  
 *object*  
 보안 인증서를 나타내는 [SecurityCertificate 클래스](../../../relational-databases/wmi-provider-configuration-classes/securitycertificate-class/securitycertificate-class.md) 개체입니다.  
  
## <a name="property-valuereturn-value"></a>속성 값/반환 값  
 A **uint32** 보안 인증서의 만료 날짜를 지정 하는 값입니다.  
  
## <a name="remarks"></a>Remarks  
  
## <a name="see-also"></a>관련 항목  
 [서버 네트워크 프로토콜 및 네트워크 라이브러리 구성](https://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)  
  
  
