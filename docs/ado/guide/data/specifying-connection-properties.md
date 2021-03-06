---
title: 연결 속성 지정 | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- connection properties [ADO]
- connections [ADO]
ms.assetid: 49456201-b085-4851-9686-e814136b07be
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 885d201736adb3cd16efbea4f3907cd0aa324128
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47622761"
---
# <a name="specifying-connection-properties"></a>연결 속성 지정
대부분의 지정 된 정보를 제공할 수 있습니다는 [연결 문자열](../../../ado/guide/data/creating-a-connection-string.md) 의 속성을 설정 하 여 합니다 **연결** 연결을 열기 전에 개체입니다. 예를 들어 연결 문자열에 설명 된 대로 동일한 효과 얻을 수 있습니다 [연결 문자열 만들기](../../../ado/guide/data/creating-a-connection-string.md) 다음 코드를 사용 하 여 합니다.  
  
```  
With objConn  
.Provider = "SQLOLEDB"  
.Properties("Data Source") = "MySqlServer"  
   .Properties("Integrated Security") = "SSPI"  
.Open  
.DefaultDatabase = "Northwind"  
End With  
```  
  
 DefaultDatabase 연결을 연 후에 설정 됩니다.  
  
> [!NOTE]
>  ADO 세미콜론을 포함 하는 암호를 사용 해야 하면 (";") 암호는 작은따옴표로 묶여 있지 않은 한 합니다.
