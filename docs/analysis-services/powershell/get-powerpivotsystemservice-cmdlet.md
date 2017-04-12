---
title: "Get-PowerPivotSystemService cmdlet | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 33231250-3880-4d75-936b-d70662a01855
caps.latest.revision: 9
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 9
---
# Get-PowerPivotSystemService cmdlet
  팜에 있는 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 시스템 서비스 개체의 전역 속성을 반환합니다.  
  
 **적용 대상:** SharePoint 2010 및 SharePoint 2013  
  
## 구문  
  
```  
Get-PowerPivotSystemService [-Identity <PowerPivotMidTierServicePipeBind>] [<CommonParameters>]  
```  
  
## Description  
 Get-PowerPivotSystemService cmdlet은 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 시스템 서비스 개체의 전역 속성을 반환합니다. 부모 개체는 팜마다 하나씩이지만 팜의 개별 응용 프로그램 서버에서 실행되는 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 시스템 서비스 인스턴스는 여러 개 있을 수 있습니다. 부모 개체는 인스턴스별로 달라지지 않는 팜 수준 설정을 보여 줍니다. 팜에 SharePoint용 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 설치가 여러 개 있는 경우 팜의 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 시스템 서비스 인스턴스 수를 나타내는 쉼표로 구분된 인스턴스 목록이 제공됩니다.  
  
## 매개 변수  
  
### -Identity \<PowerPivotMidTierServicePipeBind>  
 가져올 부모 개체를 지정합니다. 팜에서 개체를 고유하게 식별하는 유효한 GUID 값을 지정해야 합니다.  
  
|||  
|-|-|  
|필수 여부|false|  
|위치|0|  
|기본값||  
|파이프라인 입력 허용|true|  
|와일드카드 문자 허용|false|  
  
### \<CommonParameters>  
 이 cmdlet은 공통 매개 변수 Verbose, Debug, ErrorAction, ErrorVariable, WarningAction, WarningVariable, OutBuffer 및 OutVariable을 지원합니다. 자세한 내용은 [About_CommonParameters](http://go.microsoft.com/fwlink/?linkID=227825)를 참조하세요.  
  
## 입/출력  
 입력 유형은 cmdlet에 파이프할 수 있는 개체 유형입니다. 반환 유형은 cmdlet에서 반환하는 개체 유형입니다.  
  
|||  
|-|-|  
|입력|없음|  
|출력|없음|  
  
## 예제 1  
  
```  
C:\PS>Get-PowerPivotSystemService  
```  
  
 이 예에서는 팜의 모든 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 시스템 서비스 인스턴스가 공유하는 속성을 보여 주는 부모 개체의 전역 속성을 반환합니다.  
  
  