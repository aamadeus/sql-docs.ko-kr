---
title: "Update-PowerPivotSystemService cmdlet | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: a90f1158-68d3-4330-98c1-fb0f81e13328
caps.latest.revision: 8
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 8
---
# Update-PowerPivotSystemService cmdlet
  팜에 있는 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 시스템 서비스의 부모 개체를 업그레이드합니다.  
  
 **적용 대상:** SharePoint 2010 및 SharePoint 2013  
  
## 구문  
  
```  
Update-PowerPivotSystemService [-Confirm <switch>] [<CommonParameters>]  
```  
  
## Description  
 **Update-PowerPivotSystemService** cmdlet은 팜에서 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 시스템 서비스 부모 개체, 인스턴스 및 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 서비스 응용 프로그램에 대해 일련의 업그레이드 동작을 실행합니다. SharePoint용 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 배포 내의 모든 중간 계층 서비스와 응용 프로그램은 동일한 기능 수준에서 실행되어야 합니다. 이 cmdlet은 이러한 모든 개체에 대해 업그레이드 동작을 실행합니다.  
  
 SQL Server 설치 프로그램을 사용하여 최신 버전의 SharePoint용 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 을 설치한 후나 서버에 누적 업데이트를 적용한 경우에 이 cmdlet을 실행하십시오. 업그레이드가 필요한지 여부를 확인하려면 `Get-PowerPivotSystemService` 를 실행하여 **NeedsUpgrade** 속성을 검토합니다. **NeedsUpgrade**가 true이면 cmdlet을 실행하여 팜의 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 중간 계층 개체를 업그레이드해야 합니다.  
  
 SharePoint용 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 배포에는 중간 계층 및 백 엔드 데이터 서비스가 포함되므로 **Update-PowerPivotSystemService**를 실행할 때마다 **Update-PowerPivotEngineService**를 실행하여 팜 전체에서 두 계층이 동일한 버전이 되도록 해야 합니다.  
  
 업그레이드한 후에는 이전 버전으로 롤백할 수 없습니다. 꼭 이전 버전으로 되돌려야 한다면 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 을 SharePoint 팜에서 제거한 후 소프트웨어를 다시 설치합니다. 업그레이드 작업이 성공했는지 확인하려면 `Get-PowerPivotSystemService` 를 실행하여 전역 속성에서 버전 정보를 검토하고 **NeedsUpgrade** 가 이제 true로 설정되지 않았는지 확인하십시오.  
  
## 매개 변수  
  
### -Confirm \<switch>  
 명령을 실행하기 전 확인 메시지를 표시합니다. 이 값은 기본적으로 설정되어 있습니다. 명령에서 확인 응답을 무시하려면 명령에 Confirm:$false를 지정합니다.  
  
|||  
|-|-|  
|필수 여부|false|  
|위치|명명됨|  
|기본값||  
|파이프라인 입력 허용|false|  
|와일드카드 문자 허용|false|  
  
### \<CommonParameters>  
 이 cmdlet은 다음 매개 변수를 지원합니다.  
  
-   자세히  
  
-   디버그  
  
-   ErrorAction  
  
-   ErrorVariable  
  
-   WarningAction  
  
-   WarningVariable  
  
-   OutBuffer  
  
-   OutVariable  
  
 자세한 내용은 [about_commonparameters](http://go.microsoft.com/fwlink/?linkID=227825)를 참조하세요.  
  
## 입/출력  
 입력 유형은 cmdlet에 파이프할 수 있는 개체 유형입니다. 반환 유형은 cmdlet에서 반환하는 개체 유형입니다.  
  
|||  
|-|-|  
|입력|없음|  
|출력|없음|  
  
  