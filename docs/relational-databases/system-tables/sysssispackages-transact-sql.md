---
title: sysssispackages (TRANSACT-SQL) | Microsoft Docs
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-tables
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sysdtspackages90_TSQL
- sysdtspackages90
dev_langs: TSQL
helpviewer_keywords: sysssispackages system table
ms.assetid: 66155dcd-dcdb-4e33-a242-1625828ad8d2
caps.latest.revision: "43"
author: spelluru
ms.author: spelluru
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 5b694a277a235b373f1051878551ccca9537623f
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2017
---
# <a name="sysssispackages-transact-sql"></a>sysssispackages(Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  에 저장 된 각 패키지에 대해 하나의 행을 포함 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]합니다. 이 테이블에 저장 되는 **msdb** 데이터베이스입니다.  
  
  
|열 이름|데이터 형식|Description|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|패키지의 고유 식별자입니다.|  
|**id**|**uniqueidentifier**|패키지의 GUID입니다.|  
|**설명**|**nvarchar**|패키지에 대한 설명(옵션)입니다.|  
|**createdate**|**datetime**|패키지를 만든 날짜입니다.|  
|**폴더 id**|**uniqueidentifier**|[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]에서 패키지를 나열하는 논리적 폴더의 GUID입니다.|  
|**ownersid**|**varbinary**|패키지를 만든 사용자의 고유 보안 식별자입니다.|  
|**packagedata**|**image**|패키지입니다.|  
|**packageformat**|**int**|패키지가 저장되는 형식입니다.<br /><br /> 값이 2 이면 패키지에 저장 됩니다는 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 형식입니다.<br /><br /> 값이 3 이면의 형식으로 패키지를 저장할 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]이상.|  
|**packagetype**|**int**|패키지를 만든 클라이언트입니다. 가능한 값은 다음과 같습니다.<br /><br /> 0(기본값)<br /><br /> 1 ([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 가져오기 및 내보내기 마법사)<br /><br /> 3 ([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 복제)<br /><br /> 5 ([!INCLUDE[ssIS](../../includes/ssis-md.md)] 디자이너)<br /><br /> 6(유지 관리 계획 디자이너 또는 마법사)<br /><br /> <br /><br /> 이 열의 값에 해당 하는 <xref:Microsoft.SqlServer.Dts.Runtime.DTSPackageType> 열거형입니다.|  
|**vermajor**|**int**|패키지의 최신 주 버전입니다.|  
|**verminor**|**int**|패키지의 최신 부 버전입니다.|  
|**verbuild**|**int**|패키지의 최신 빌드입니다.|  
|**vercomments**|**nvarchar**|패키지 버전에 대한 설명입니다.|  
|**verid**|**uniqueidentifier**|패키지 버전의 GUID입니다.|  
|**isencrypted**|**bit**|패키지가 암호화되었는지 여부를 나타내는 부울입니다.|  
|**readrolesid**|**varbinary**|패키지를 로드할 수 있는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 역할입니다.|  
|**writerolesid**|**varbinary**|패키지를 저장할 수 있는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 역할입니다.|  
  
## <a name="see-also"></a>관련 항목:  
 [Integration Services&#40;SSIS&#41; 패키지](../../integration-services/integration-services-ssis-packages.md)  
  
  