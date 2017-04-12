---
title: "5단원: 간단한 시뮬레이션 만들기(데이터 과학 심층 분석) | Microsoft Docs"
ms.custom: ""
ms.date: "10/03/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
applies_to: 
  - "SQL Server 2016"
dev_langs: 
  - "R"
ms.assetid: f420b816-ddab-4a1a-89b9-c8285a2d33a3
caps.latest.revision: 16
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 15
---
# 5단원: 간단한 시뮬레이션 만들기(데이터 과학 심층 분석)
지금까지는 SQL Server R Services에서 제공하며 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]와 로컬 계산 컨텍스트 간에 데이터를 이동하도록 설계된 R 함수를 사용했습니다. 그러나 사용자 지정 R 함수를 작성하고 서버 컨텍스트에서 실행하려는 경우를 가정해 보세요.  
  
*rxExec* 함수를 사용하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 컴퓨터 컨텍스트에서 임의 함수를 호출할 수 있습니다. *rxExec*를 사용하여 단일 서버 노드의 전체 코어에 작업을 명시적으로 분산할 수도 있습니다.  
  
이 단원에서는 원격 서버를 사용하여 간단한 시뮬레이션을 만듭니다. 시뮬레이션에는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터가 필요하지 않습니다. 예제에서는 사용자 지정 함수를 디자인한 다음 *rxExec* 함수를 사용하여 호출하는 방법만 보여 줍니다.  
  
*rxExec*를 사용하는 더 복잡한 예제를 보려면 [http://blog.revolutionanalytics.com/2015/04/coarse-grain-parallelism-with-foreach-and-rxexec.html](http://blog.revolutionanalytics.com/2015/04/coarse-grain-parallelism-with-foreach-and-rxexec.html) 문서를 참조하세요.  
  
## 함수 만들기  
일반적인 카지노 게임은 다음과 같은 규칙에 따라 한 쌍의 주사위를 굴리는 동작으로 구성됩니다.  
  
-   처음 굴릴 때 7 또는 11이 나오면 이깁니다.  
  
-   2, 3 또는 12가 나오면 집니다.  
  
-   4, 5, 6, 8, 9 또는 10이 나오면 해당 숫자가 포인트가 되고, 다시 포인트를 얻거나(이기는 경우) 7이 나올 때까지(지는 경우) 계속해서 주사위를 굴립니다.  
  
R에서 사용자 지정 함수를 만든 다음 여러 번 실행하면 게임을 쉽게 시뮬레이트할 수 있습니다.  
  
1.  다음 R 코드를 사용하여 사용자 지정 함수를 만듭니다.  
  
    ```R  
    rollDice <- function()   
    {   
        result <- NULL        
        point <- NULL     
        count <- 1   
            while (is.null(result))   
            {   
                roll <- sum(sample(6, 2, replace=TRUE))   
  
                if (is.null(point))   
                { point <- roll }   
                if (count == 1 && (roll == 7 || roll == 11))   
                {  result <- "Win" }   
                else if (count == 1 && (roll == 2 || roll == 3 || roll == 12))    
                { result <- "Loss" }    
                else if (count > 1 && roll == 7 )   
                { result <- "Loss" }    
                else if (count > 1 && point == roll)   
                { result <- "Win" }    
                else { count <- count + 1 }   
            }   
            result   
    }  
  
    ```  
  
2.  단일 주사위 게임을 시뮬레이트하려면 함수를 실행합니다.  
  
    ```R  
    rollDice()   
    ```  
  
    이겼나요, 졌나요?  
  
이제 함수를 여러 번 실행하여 이길 확률을 확인하는 데 도움이 되는 시뮬레이션을 만드는 방법을 살펴보겠습니다.  
  
## 시뮬레이션 만들기  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 컴퓨터 컨텍스트에서 임의 함수를 실행하려면 *rxExec* 함수를 호출합니다. *rxExec*는 서버 컨텍스트에서 노드 또는 코어 전체에 분산된 함수의 병렬 실행도 지원하지만 여기서는 단순히 이 함수를 사용하여 서버에서 사용자 지정 함수를 실행합니다.  
  
1.  시뮬레이션을 수정하는 다른 몇 가지 매개 변수와 함께 *rxExec*에 대한 인수로 사용자 지정 함수를 호출합니다.  
  
    ```R  
    sqlServerExec <- rxExec(rollDice, timesToRun=20, RNGseed="auto")   
    length(sqlServerExec)   
    ```  
  
    -   *timesToRun* 인수를 사용하여 함수를 실행해야 하는 횟수를 나타냅니다.  이 경우 주사위를 20회 굴립니다.  
  
    -   *RNGseed* 및 *RNGkind* 인수를 사용하여 난수 생성을 제어할 수 있습니다. *RNGseed*를 **auto**로 설정하면 병렬 난수 스트림이 각 작업자에 대해 초기화됩니다.  
  
2.  *rxExec* 함수는 각 실행에 대한 하나의 요소가 포함된 목록을 만듭니다. 그러나 목록이 완성될 때까지 큰 변화는 없습니다. 모든 반복이 완료되면 `length`로 시작하는 줄에 값이 반환됩니다.  
  
    그러면 다음 단계로 이동하여 승패 레코드 요약을 가져올 수 있습니다.  
  
3.  R의 *unlist* 함수를 사용하여 반환된 목록을 벡터로 변환하고 *table* 함수를 사용하여 결과를 요약합니다.  
  
    ```R  
    table(unlist(sqlServerExec))  
    ```  
  
    결과가 다음과 같이 표시됩니다.  
  
     *Loss  Win*   
     *12  8*  
  
## 결론  
이 자습서에서는 다음과 같은 태스크를 익혔습니다.  
  
-   분석에 사용할 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]데이터 가져오기  
  
-   R에서 데이터 원본 만들기 및 수정  
  
-   워크스테이션과 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 서버 간에 모델, 데이터 및 그림 전달  
  
>  [!TIP]
> 
> 1,000만 개의 관찰이 포함된 큰 데이터 집합을 사용하여 이러한 기술을 실험하려는 경우 [http://packages.revolutionanalytics.com/datasets](http://packages.revolutionanalytics.com/datasets)에서 데이터 파일을 사용할 수 있습니다.  
>   
> 큰 데이터 파일로 이 연습을 다시 사용하려면 데이터를 다운로드한 후 데이터 원본을 다음과 같이 수정하면 됩니다.   
>  -   새 데이터 파일을 가리키도록 *ccFraudCsv* 및 *ccScoreCsv* 변수 설정     
>  -   *sqlFraudTable*에서 참조된 테이블의 이름을 *ccFraud10*으로 변경    
>  -   *sqlScoreTable*에서 참조된 테이블의 이름을 *ccFraudScore10*으로 변경   
  
## 이전 단계  
[SQL Server와 XDF 파일 간에 데이터 이동&#40;데이터 과학 심층 분석&#41;](../../advanced-analytics/r-services/move-data-between-sql-server-and-xdf-file-data-science-deep-dive.md)  
  
  
  