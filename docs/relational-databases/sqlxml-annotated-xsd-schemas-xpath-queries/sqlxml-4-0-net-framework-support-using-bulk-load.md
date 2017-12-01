---
title: ".NET 환경에서 SQLXML 대량 로드를 사용 하 여 | Microsoft Docs"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: sqlxml
ms.reviewer: 
ms.suite: sql
ms.technology: dbe-xml
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- SQLXML, XML Bulk Load
- XML Bulk Load [SQLXML], .NET environment
- .NET Framework [SQLXML], XML Bulk Load
- bulk load [SQLXML], .NET environment
ms.assetid: b85df83b-ba56-43bf-bcdf-b2a6fca43276
caps.latest.revision: "23"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: efde232c2ab6fdd182547f6428994d410ea8e618
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2017
---
# <a name="sqlxml-40-net-framework-support---using-bulk-load"></a>대량 로드를 사용 하 여 SQLXML 4.0.NET Framework 지원-
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]이 항목에서는.NET 환경에서 XML 대량 로드 기능을 사용할 수 있는 방법을 설명 합니다. XML 대량 로드에 대 한 자세한 내용은 참조 하세요. [XML 데이터의 대량 로드 수행 &#40; SQLXML 4.0 &#41; ](../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/bulk-load-xml/performing-bulk-load-of-xml-data-sqlxml-4-0.md).  
  
 관리되는 환경에서 SQLXML 대량 로드 COM 개체를 사용하려면 이 개체에 대한 프로젝트 참조를 추가해야 합니다. 이렇게 하면 대량 로드 COM 개체에 대한 관리되는 래퍼 인터페이스가 생성됩니다.  
  
> [!NOTE]  
>  관리되는 XML 대량 로드는 관리되는 스트림에는 사용할 수 없으며 네이티브 스트림에 대한 래퍼가 있어야 합니다. SQLXML 대량 로드 구성 요소는 다중 스레드 환경('[MTAThread]' 특성)에서는 실행되지 않습니다. 다중 스레드 환경에서 대량 로드 구성 요소를 실행 하려고 하면 예외가 InvalidCastException 다음과 같은 추가 정보: "SQLXMLBULKLOADLib.ISQLXMLBulkLoad 인터페이스에 대 한 QueryInterface 실패 했습니다." 대량 로드 개체가 단일 스레드 액세스할 수 있는 개체를 설정 하 여이 문제를 해결 (사용 하 여 예를 들어는 **[STAThread]** 샘플에 표시 된 대로 특성).  
  
 이 항목에서는 XML 데이터를 데이터베이스에 대량 로드하기 위한 C# 작업 예제 응용 프로그램을 제공합니다. 작업 예제를 만들려면 다음 단계를 수행합니다.  
  
1.  다음 테이블을 만듭니다.  
  
    ```  
    CREATE TABLE Ord (  
             OrderID     int identity(1,1)  PRIMARY KEY,  
             CustomerID  varchar(5))  
    GO  
    CREATE TABLE Product (  
             ProductID   int identity(1,1) PRIMARY KEY,  
             ProductName varchar(20))  
    GO  
    CREATE TABLE OrderDetail (  
           OrderID     int FOREIGN KEY REFERENCES Ord(OrderID),  
           ProductID   int FOREIGN KEY REFERENCES Product(ProductID),  
                       CONSTRAINT OD_key PRIMARY KEY (OrderID, ProductID))  
    GO  
    ```  
  
2.  다음 스키마를 schema.xml 파일에 저장합니다.  
  
    ```  
    <xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
                xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
    <xsd:annotation>  
      <xsd:appinfo>  
        <sql:relationship name="OrderOD"  
              parent="Ord"  
              parent-key="OrderID"  
              child="OrderDetail"  
              child-key="OrderID" />  
  
        <sql:relationship name="ODProduct"  
              parent="OrderDetail"  
              parent-key="ProductID"  
              child="Product"  
              child-key="ProductID"   
              inverse="true"/>  
      </xsd:appinfo>  
    </xsd:annotation>  
  
      <xsd:element name="Order" sql:relation="Ord"   
                                sql:key-fields="OrderID" >  
       <xsd:complexType>  
         <xsd:sequence>  
            <xsd:element name="Product" sql:relation="Product"   
                         sql:key-fields="ProductID"  
                         sql:relationship="OrderOD ODProduct">  
              <xsd:complexType>  
                 <xsd:attribute name="ProductID" type="xsd:int" />  
                 <xsd:attribute name="ProductName" type="xsd:string" />  
              </xsd:complexType>  
            </xsd:element>  
         </xsd:sequence>  
            <xsd:attribute name="OrderID"   type="xsd:integer" />   
            <xsd:attribute name="CustomerID"   type="xsd:string" />  
        </xsd:complexType>  
      </xsd:element>  
    </xsd:schema>  
    ```  
  
3.  다음 예제 XML 문서를 data.xml 파일에 저장합니다.  
  
    ```  
    <ROOT>    
      <Order OrderID="11" CustomerID="ALFKI">  
        <Product ProductID="11" ProductName="Chai" />  
        <Product ProductID="22" ProductName="Chang" />  
      </Order>  
      <Order OrderID="22" CustomerID="ANATR">  
         <Product ProductID="33" ProductName="Aniseed Syrup" />  
        <Product ProductID="44" ProductName="Gumbo Mix" />  
      </Order>  
    </ROOT>  
    ```  
  
4.  Visual Studio를 시작합니다.  
  
5.  C# 콘솔 응용 프로그램을 만듭니다.  
  
6.  **프로젝트** 메뉴 선택 **참조 추가**합니다.  
  
7.  에 **COM** 탭에서 **Microsoft SQLXML Bulkload 4.0 Type Library** (xblkld4.dll)를 클릭 하 고 **확인**합니다. 표시 됩니다는 **Interop.SQLXMLBULKLOADLib** 어셈블리를 프로젝트에 생성 합니다.  
  
8.  Main() 메서드를 다음 코드로 바꿉니다. 업데이트는 **ConnectionString** 속성과 스키마 및 데이터 파일의 파일 경로입니다.  
  
    ```  
    [STAThread]  
       static void Main(string[] args)  
       {     
             try  
             {  
                SQLXMLBULKLOADLib.SQLXMLBulkLoad4Class objBL = new SQLXMLBULKLOADLib.SQLXMLBulkLoad4Class();  
                objBL.ConnectionString = "Provider=sqloledb;server=server;database=databaseName;integrated security=SSPI";  
                objBL.ErrorLogFile = "error.xml";  
                objBL.KeepIdentity = false;  
                objBL.Execute ("schema.xml","data.xml");  
             }  
             catch(Exception e)  
             {  
             Console.WriteLine(e.ToString());  
             }  
       }  
    ```  
  
9. 앞에서 만든 테이블에 XML을 로드하려면 프로젝트를 빌드하고 실행합니다.  
  
    > [!NOTE]  
    >  대량 로드 구성 요소(xblkld4.dll)에 대한 참조는 .NET Framework에 포함된 tlbimp.exe 도구를 사용하여 추가할 수도 있습니다. 이 도구는 네이티브 DLL(xblkld4.dll)에 대한 관리되는 래퍼를 만들며 이 래퍼는 모든 .NET 프로젝트에서 사용할 수 있습니다. 예를 들어  
  
    ```  
    c:\>tlbimp xblkld4.dll  
    ```  
  
     그러면 .NET Framework 프로젝트에서 사용할 수 있는 관리되는 래퍼 DLL(SQLXMLBULKLOADLib.dll)이 생성됩니다. .NET Framework에서 새로 생성된 DLL에 대한 프로젝트 참조를 추가합니다.  
  
## <a name="see-also"></a>관련 항목:  
 [XML 데이터 &#40; 대량 로드 수행 SQLXML 4.0 &#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/bulk-load-xml/performing-bulk-load-of-xml-data-sqlxml-4-0.md)  
  
  