---
title: "LINQ 고려 사항(WCF Data Services) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-oob"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "WCF 데이터 서비스, LINQ"
  - "Data Services 쿼리 [WCF Data Services]"
  - "WCF 데이터 서비스를 쿼리 하는"
ms.assetid: cc4ec9e9-348f-42a6-a78e-1cd40e370656
caps.latest.revision: 5
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# LINQ 고려 사항(WCF Data Services)
이 항목에서는 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] 클라이언트를 사용할 때 LINQ 쿼리가 작성되고 실행되는 방식과 [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)]을 구현하는 데이터 서비스를 LINQ로 쿼리할 경우의 제한 사항에 대한 정보를 제공합니다. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]작성 및 실행에 대 한 쿼리는 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]-기반 데이터 서비스 참조 [데이터 서비스 쿼리](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md)합니다.  
  
## <a name="composing-linq-queries"></a>LINQ 쿼리 작성  
 LINQ를 구현 하는 개체의 컬렉션에 대 한 쿼리를 작성 하면 <xref:System.Collections.Generic.IEnumerable%601>합니다. 모두는 **서비스 참조 추가** 대화 상자에 [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] DataSvcUtil.exe 도구는의 표현을 생성 하는 데 사용 되는 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 에서 상속 되는 엔터티 컨테이너 클래스로 서비스 <xref:System.Data.Services.Client.DataServiceContext>뿐 아니라 피드에서 반환 되는 엔터티를 나타내는 개체입니다. 또한 이러한 도구는 서비스에서 피드로 노출되는 컬렉션의 엔터티 컨테이너 클래스에 대한 속성도 생성합니다. 이러한 각 속성의 반환 데이터 서비스를 캡슐화 하는 클래스는 <xref:System.Data.Services.Client.DataServiceQuery%601>합니다. 때문에 <xref:System.Data.Services.Client.DataServiceQuery%601> 클래스가 구현 하는 <xref:System.Linq.IQueryable%601> LINQ로 정의 된 인터페이스 쿼리 요청 URI는 실행 시 데이터 서비스로 전송 되는 클라이언트 라이브러리에서 변환 되는 데이터 서비스에서 노출 하는 피드에 대해 LINQ 쿼리를 작성할 수 있습니다.  
  
> [!IMPORTANT]
>  LINQ 구문으로 표현할 수 있는 쿼리 집합은 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 데이터 서비스에 사용되는 URI 구문에서 사용할 수 있는 것보다 광범위합니다. A <xref:System.NotSupportedException> 쿼리를 대상 데이터 서비스의 URI에 매핑할 수 없는 경우 발생 합니다. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][지원 되지 않는 LINQ 메서드](../../../../docs/framework/data/wcf/linq-considerations-wcf-data-services.md#unsupportedMethods) 이 여기에 있습니다.  
  
 다음 예는 운송료가 $30를 초과하는 `Orders`를 반환하고 결과를 최근 운송 날짜순으로 정렬하는 LINQ 쿼리입니다.  
  
  [Astoria NorthwindClient #AddQueryOptionsLinqSpecific](../../../../amples/snippets/xml/VS_Snippets_Misc/astoria northwind service/astoria.vsmdi NorthwindClient#AddQueryOptionsLinqSpecific)]  
  
 이 LINQ 쿼리는 다음 쿼리는 Northwind 기반에 대해 실행 되는 URI로 변환 됩니다 [퀵 스타트](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md) 데이터 서비스:  
  
```  
http://localhost:12345/Northwind.svc/Orders?Orderby=ShippedDate&?filter=Freight gt 30  
```  
  
 LINQ에 대 한 자세한 내용은 참조 하십시오. [LINQ (Language-Integrated Query)](../Topic/LINQ%20\(Language-Integrated%20Query\).md)합니다.  
  
 LINQ를 통해 위의 예제와 같은 언어별 선언적 쿼리 구문과 표준 쿼리 연산자로 알려진 쿼리 메서드 집합을 모두 사용하여 쿼리를 작성할 수 있습니다. 위의 예와 동등한 쿼리는 다음 예와 같이 메서드 기반 구문만을 사용하여 작성할 수 있습니다.  
  
  [Astoria NorthwindClient #AddQueryOptionsLinqExpressionSpecific](../../../../amples/snippets/xml/VS_Snippets_Misc/astoria northwind service/astoria.vsmdi NorthwindClient#AddQueryOptionsLinqExpressionSpecific)]  
  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]클라이언트는 두 종류의 작성된 쿼리를 쿼리 URI로 변환할 수 있고 쿼리 식에 쿼리 메서드를 추가하여 LINQ 쿼리를 확장할 수 있습니다. 쿼리 식에 메서드 구문을 추가 하 여 LINQ 쿼리를 작성할 때 또는 <xref:System.Data.Services.Client.DataServiceQuery%601>, 작업 메서드가 호출 되는 순서는 쿼리 URI에 추가 됩니다. 이 호출에 해당 하는 <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> 메서드는 쿼리 URI에 각 쿼리 옵션 추가를 합니다.  
  
## <a name="executing-linq-queries"></a>LINQ 쿼리 실행  
 와 같은 특정 LINQ 쿼리 메서드를 <xref:System.Linq.Enumerable.First%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%29> 또는 <xref:System.Linq.Enumerable.Single%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%29>에 쿼리를 추가 하는 경우 쿼리가 실행 되 게 합니다. 또한 쿼리는 `foreach` 루프 중이나 쿼리가 `List` 컬렉션에 할당될 때와 같이 결과가 명시적으로 열거될 때에도 실행됩니다. 자세한 내용은 참조 [데이터 서비스 쿼리](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md)합니다.  
  
 클라이언트는 LINQ 쿼리를 두 부분으로 실행합니다. 가능한 경우 쿼리의 LINQ 식이 클라이언트에서 먼저 계산된 다음 URI 기반 쿼리가 생성되고 서비스의 데이터와 비교하여 평가되도록 데이터 서비스로 보내집니다. 자세한 내용은 섹션을 참조 하십시오. [클라이언트 및 서버 실행](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md#executingQueries) 에서 [데이터 서비스 쿼리](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md)합니다.  
  
 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 준수 쿼리 URI에서 LINQ 쿼리를 변환할 수 없는 경우 실행을 시도하면 예외가 발생됩니다. 자세한 내용은 참조 [데이터 서비스 쿼리](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md)합니다.  
  
## <a name="linq-query-examples"></a>LINQ 쿼리 예제  
 이후 단원의 예에서는 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 서비스에 대해 실행할 수 있는 LINQ 쿼리 종류를 나타냅니다.  
  
<a name="filtering"></a>   
### <a name="filtering"></a>필터링  
 이 단원의 LINQ 쿼리 예는 서비스에서 반환된 피드의 데이터를 필터링합니다.  
  
 다음 예는 운송료가 $30를 초과하는 주문만 반환되도록 반환된 `Orders` 엔터티를 필터링하는 쿼리입니다.  
  
-   LINQ 쿼리 구문 사용:  
  
      [Astoria NorthwindClient #LinqWhereClauseSpecific](../../../../amples/snippets/xml/VS_Snippets_Misc/astoria northwind service/astoria.vsmdi NorthwindClient#LinqWhereClauseSpecific)]  
  
-   LINQ 쿼리 메서드 사용:  
  
      [Astoria NorthwindClient #LinqWhereMethodSpecific](../../../../amples/snippets/xml/VS_Snippets_Misc/astoria northwind service/astoria.vsmdi NorthwindClient#LinqWhereMethodSpecific)]  
  
-   URI 쿼리 문자열 `$filter` 옵션:  
  
      [Astoria NorthwindClient #ExplicitQueryWhereMethodSpecific](../../../../amples/snippets/xml/VS_Snippets_Misc/astoria northwind service/astoria.vsmdi NorthwindClient#ExplicitQueryWhereMethodSpecific)]  
  
 위의 모든 예제는 쿼리 URI `http://localhost:12345/northwind.svc/Orders()?$filter=Freight gt 30M`으로 변환됩니다.  
  
<a name="sorting"></a>   
### <a name="sorting"></a>정렬  
 다음 예제는 회사 이름 및 우편 번호를 기준으로 반환된 데이터를 내림차순으로 정렬하는 쿼리를 나타냅니다.  
  
-   LINQ 쿼리 구문 사용:  
  
      [Astoria NorthwindClient #LinqOrderByClauseSpecific](../../../../amples/snippets/xml/VS_Snippets_Misc/astoria northwind service/astoria.vsmdi NorthwindClient#LinqOrderByClauseSpecific)]  
  
-   LINQ 쿼리 메서드 사용:  
  
      [Astoria NorthwindClient #LinqOrderByMethodSpecific](../../../../amples/snippets/xml/VS_Snippets_Misc/astoria northwind service/astoria.vsmdi NorthwindClient#LinqOrderByMethodSpecific)]  
  
-   URI 쿼리 문자열 `$orderby` 옵션:  
  
      [Astoria NorthwindClient #ExplicitQueryOrderByMethodSpecific](../../../../amples/snippets/xml/VS_Snippets_Misc/astoria northwind service/astoria.vsmdi NorthwindClient#ExplicitQueryOrderByMethodSpecific)]  
  
 위의 모든 예제는 쿼리 URI `http://localhost:12345/northwind.svc/Customers()?$orderby=CompanyName,PostalCode desc`으로 변환됩니다.  
  
<a name="projection"></a>   
### <a name="projection"></a>프로젝션  
 다음 예는 반환된 데이터를 더 좁은 범위의 `CustomerAddress` 유형으로 프로젝션하는 동등한 쿼리를 나타냅니다.  
  
-   LINQ 쿼리 구문 사용:  
  
      [Astoria NorthwindClient #LinqSelectClauseSpecific](../../../../amples/snippets/xml/VS_Snippets_Misc/astoria northwind service/astoria.vsmdi NorthwindClient#LinqSelectClauseSpecific)]  
  
-   LINQ 쿼리 메서드 사용:  
  
      [Astoria NorthwindClient #LinqSelectMethodSpecific](../../../../amples/snippets/xml/VS_Snippets_Misc/astoria northwind service/astoria.vsmdi NorthwindClient#LinqSelectMethodSpecific)]  
  
> [!NOTE]
>  `$select` 를 사용 하 여 쿼리 URI에 쿼리 옵션을 추가할 수 없습니다는 <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> 메서드. LINQ를 사용 하는 것이 좋습니다 <xref:System.Linq.Enumerable.Select%2A> 클라이언트를 생성 하는 메서드는 `$select` 쿼리 옵션은 요청 URI에서에서.\</TSource, TResult>  
  
 위의 두 가지 예는 쿼리 URI `"http://localhost:12345/northwind.svc/Customers()?$filter=Country eq 'GerGerm'&$select=CustomerID,Address,City,Region,PostalCode,Country"`로 변환됩니다.  
  
<a name="paging"></a>   
### <a name="client-paging"></a>클라이언트 페이징  
 다음 예에서는 첫 50개 주문은 건너뛰고 25개 주문을 포함하는 정렬된 주문 엔터티 페이지를 요청하는 쿼리를 나타냅니다.  
  
-   LINQ 쿼리에 쿼리 메서드 적용:  
  
      [Astoria NorthwindClient #LinqSkipTakeMethodSpecific](../../../../amples/snippets/xml/VS_Snippets_Misc/astoria northwind service/astoria.vsmdi NorthwindClient#LinqSkipTakeMethodSpecific)]  
  
-   URI 쿼리 문자열 `$skip` 및 `$top` 옵션:  
  
      [Astoria NorthwindClient #ExplicitQuerySkipTakeMethodSpecific](../../../../amples/snippets/xml/VS_Snippets_Misc/astoria northwind service/astoria.vsmdi NorthwindClient#ExplicitQuerySkipTakeMethodSpecific)]  
  
 위의 두 가지 예는 쿼리 URI `http://localhost:12345/northwind.svc/Orders()?$orderby=OrderDate desc&$skip=50&$top=25`로 변환됩니다.  
  
<a name="expand"></a>   
### <a name="expand"></a>확장  
 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 데이터 서비스를 쿼리할 때 쿼리의 대상 엔터티와 관련된 엔터티가 반환된 피드에 포함되도록 요청할 수 있습니다. <xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A> 메서드가 호출 되는 <xref:System.Data.Services.Client.DataServiceQuery%601> LINQ 쿼리의 대상인 엔터티 집합에 대 한 관련 엔터티 집합 이름으로 제공 되는 `path` 매개 변수입니다. 자세한 내용은 참조 [지연 콘텐츠 로드](../../../../docs/framework/data/wcf/loading-deferred-content-wcf-data-services.md)합니다.  
  
 다음 예제에서는 사용 하 여 여러 가지 동등한 방법을 보여는 <xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A> 쿼리에서 메서드:  
  
-   LINQ 쿼리 구문:  
  
      [Astoria NorthwindClient #LinqQueryExpandSpecific](../../../../amples/snippets/xml/VS_Snippets_Misc/astoria northwind service/astoria.vsmdi NorthwindClient#LinqQueryExpandSpecific)]  
  
-   LINQ 쿼리 메서드 사용:  
  
      [Astoria NorthwindClient #LinqQueryExpandMethodSpecific](../../../../amples/snippets/xml/VS_Snippets_Misc/astoria northwind service/astoria.vsmdi NorthwindClient#LinqQueryExpandMethodSpecific)]  
  
 위의 두 가지 예는 쿼리 URI `http://localhost:12345/northwind.svc/Orders()?$filter=CustomerID eq 'ALFKI'&$expand=Order_Details`로 변환됩니다.  
  
<a name="unsupportedMethods"></a>   
## <a name="unsupported-linq-methods"></a>지원되는 LINQ 메서드  
 다음 표에는 지원되지 않으며 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 서비스에 대해 실행되는 쿼리에 포함할 수 없는 LINQ 메서드의 클래스가 나와 있습니다.  
  
|연산 유형|지원되지 않는 메서드|  
|--------------------|------------------------|  
|집합 연산자|모든 집합 연산자에 대해 지원 되지 않습니다.는 <xref:System.Data.Services.Client.DataServiceQuery%601>, 다음을 포함 합니다.<br /><br /> -   <xref:System.Linq.Enumerable.All%2A><br />-   <xref:System.Linq.Enumerable.Any%2A><br />-   <xref:System.Linq.Enumerable.Concat%2A><br />-   <xref:System.Linq.Enumerable.DefaultIfEmpty%2A><br />-   <xref:System.Linq.Enumerable.Distinct%2A><br />-   <xref:System.Linq.Enumerable.Except%2A><br />-   <xref:System.Linq.Enumerable.Intersect%2A><br />-   <xref:System.Linq.Enumerable.Union%2A><br />-   <xref:System.Linq.Enumerable.Zip%2A>\</TFirst, TSecond, TResult>|  
|정렬 연산자:|다음과 같은 필요한 정렬 연산자는 <xref:System.Collections.Generic.IComparer%601> 에 대해 지원 되지 않는 한 <xref:System.Data.Services.Client.DataServiceQuery%601>:<br /><br /> -   <xref:System.Linq.Enumerable.OrderBy%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%2CSystem.Collections.Generic.IComparer%7B%60%601%7D%29> </TSource, TKey> </TSource, TKey><br />-   <xref:System.Linq.Enumerable.OrderByDescending%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%2CSystem.Collections.Generic.IComparer%7B%60%601%7D%29> \</TSource, TKey> \</TSource, TKey><br />-   <xref:System.Linq.Enumerable.ThenBy%60%602%28System.Linq.IOrderedEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%2CSystem.Collections.Generic.IComparer%7B%60%601%7D%29> </TSource, TKey> </TSource, TKey><br />-   <xref:System.Linq.Enumerable.ThenByDescending%60%602%28System.Linq.IOrderedEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%2CSystem.Collections.Generic.IComparer%7B%60%601%7D%29> \</TSource, TKey> \</TSource, TKey>|  
|프로젝션 및 필터링 연산자|에 대해 지원 되지 않는 다음과 같은 프로젝션 및 필터링 연산자는 위치 인수를 사용 하는 <xref:System.Data.Services.Client.DataServiceQuery%601>:<br /><br /> -   <xref:System.Linq.Enumerable.Join%60%604%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%2CSystem.Func%7B%60%600%2C%60%602%7D%2CSystem.Func%7B%60%601%2C%60%602%7D%2CSystem.Func%7B%60%600%2C%60%601%2C%60%603%7D%2CSystem.Collections.Generic.IEqualityComparer%7B%60%602%7D%29> </TOuter, TInner, TResult> </TInner, TKey> </TOuter, TKey> </TOuter, TInner, TKey, TResult><br />-   <xref:System.Linq.Enumerable.Select%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2CSystem.Int32%2C%60%601%7D%29> </TSource, Int32, TResult> </TSource, TResult><br />-   <xref:System.Linq.Enumerable.SelectMany%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%7D%29> </TSource, TResult><br />-   <xref:System.Linq.Enumerable.SelectMany%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2CSystem.Int32%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%7D%29> </TSource, TResult><br />-   <xref:System.Linq.Enumerable.SelectMany%60%603%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%7D%2CSystem.Func%7B%60%600%2C%60%601%2C%60%602%7D%29> \</TSource, TCollection, TResult> \</TSource, TCollection, TResult><br />-   <xref:System.Linq.Enumerable.SelectMany%60%603%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2CSystem.Int32%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%7D%2CSystem.Func%7B%60%600%2C%60%601%2C%60%602%7D%29> </TSource, TCollection, TResult> </TSource, TCollection, TResult><br />-   <xref:System.Linq.Enumerable.Where%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2CSystem.Int32%2CSystem.Boolean%7D%29> \</TSource, Int32, Boolean>|  
|그룹화 연산자|에 대해 지원 되지 않는 모든 그룹화 연산자는 <xref:System.Data.Services.Client.DataServiceQuery%601>, 다음을 포함 한 합니다.<br /><br /> -   <xref:System.Linq.Enumerable.GroupBy%2A>\</TSource, TKey><br />-   <xref:System.Linq.Enumerable.GroupJoin%2A>\</TOuter, TInner, TKey, TResult><br /><br /> 그룹화 연산은 클라이언트에서 수행되어야 합니다.|  
|집계 연산자|모든 집계 연산자에 대해 지원 되지 않는 한 <xref:System.Data.Services.Client.DataServiceQuery%601>, 다음을 포함 한 합니다.<br /><br /> -   <xref:System.Linq.Enumerable.Aggregate%2A><br />-   <xref:System.Linq.Enumerable.Average%2A><br />-   <xref:System.Linq.Enumerable.Count%2A><br />-   <xref:System.Linq.Enumerable.LongCount%2A><br />-   <xref:System.Linq.Enumerable.Max%2A><br />-   <xref:System.Linq.Enumerable.Min%2A><br />-   <xref:System.Linq.Enumerable.Sum%2A><br /><br /> 집계 연산은 클라이언트에서 수행되거나 서비스 작업으로 캡슐화되어야 합니다.|  
|페이징 연산자|다음 페이징 연산자에 대해 지원 되지 않습니다는 <xref:System.Data.Services.Client.DataServiceQuery%601>:<br /><br /> -   <xref:System.Linq.Enumerable.ElementAt%2A><br />-   <xref:System.Linq.Enumerable.Last%2A><br />-   <xref:System.Linq.Enumerable.LastOrDefault%2A><br />-   <xref:System.Linq.Enumerable.SkipWhile%2A><br />-   <xref:System.Linq.Enumerable.TakeWhile%2A> **참고:** 페이징 연산자는 빈 시퀀스에서 실행 되는 null을 반환 합니다.|  
|기타 연산자|다음에 대해 다른 연산자를 사용할 수 없습니다는 <xref:System.Data.Services.Client.DataServiceQuery%601>:<br /><br /> 1.  <xref:System.Linq.Enumerable.Empty%2A><br />2.  <xref:System.Linq.Enumerable.Range%2A><br />3.  <xref:System.Linq.Enumerable.Repeat%2A><br />4.  <xref:System.Linq.Enumerable.ToDictionary%2A></TSource, TKey><br />5.  <xref:System.Linq.Enumerable.ToLookup%2A>\</TSource, TKey>|  
  
<a name="supportedExpressions"></a>   
## <a name="supported-expression-functions"></a>지원되는 식 함수  
 다음과 같은 CLR(공용 언어 런타임) 메서드 및 속성은 쿼리 식에서 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 서비스에 대한 요청 URI에 포함되도록 변환될 수 있으므로 지원됩니다.  
  
|<xref:System.String> 멤버|지원되는 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 함수|  
|-----------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------|  
|<xref:System.String.Concat%28System.String%2CSystem.String%29>|`string concat(string p0, string p1)`|  
|<xref:System.String.Contains%28System.String%29>|`bool substringof(string p0, string p1)`|  
|<xref:System.String.EndsWith%28System.String%29>|`bool endswith(string p0, string p1)`|  
|<xref:System.String.IndexOf%28System.String%2CSystem.Int32%29>|`int indexof(string p0, string p1)`|  
|<xref:System.String.Length>|`int length(string p0)`|  
|<xref:System.String.Replace%28System.String%2CSystem.String%29>|`string replace(string p0, string find, string replace)`|  
|<xref:System.String.Substring%28System.Int32%29>|`string substring(string p0, int pos)`|  
|<xref:System.String.Substring%28System.Int32%2CSystem.Int32%29>|`string substring(string p0, int pos, int length)`|  
|<xref:System.String.ToLower>|`string tolower(string p0)`|  
|<xref:System.String.ToUpper>|`string toupper(string p0)`|  
|<xref:System.String.Trim>|`string trim(string p0)`|  
  
|<xref:System.DateTime> 멤버<sup>1</sup>|지원되는 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 함수|  
|-------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------|  
|<xref:System.DateTime.Day>|`int day(DateTime p0)`|  
|<xref:System.DateTime.Hour>|`int hour(DateTime p0)`|  
|<xref:System.DateTime.Minute>|`int minute(DateTime p0)`|  
|<xref:System.DateTime.Month>|`int month(DateTime p0)`|  
|<xref:System.DateTime.Second>|`int second(DateTime p0)`|  
|<xref:System.DateTime.Year>|`int year(DateTime p0)`|  
  
 <sup>1</sup>해당 날짜 및 시간 속성의 <xref:Microsoft.VisualBasic.DateAndTime?displayProperty=fullName>, 인스턴스뿐만 아니라 <xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A> Visual Basic의 메서드도 지원 됩니다.  
  
|<xref:System.Math> 멤버|지원되는 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 함수|  
|---------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------|  
|<xref:System.Math.Ceiling%28System.Decimal%29>|`decimal ceiling(decimal p0)`|  
|<xref:System.Math.Ceiling%28System.Double%29>|`double ceiling(double p0)`|  
|<xref:System.Math.Floor%28System.Decimal%29>|`decimal floor(decimal p0)`|  
|<xref:System.Math.Floor%28System.Double%29>|`double floor(double p0)`|  
|<xref:System.Math.Round%28System.Decimal%29>|`decimal round(decimal p0)`|  
|<xref:System.Math.Round%28System.Double%29>|`double round(double p0)`|  
  
|<xref:> System.Linq.Expressions.Expression?qualifyHint=False&autoUpgrade=True 멤버|지원되는 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 함수|  
|---------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------|  
|<xref:System.Linq.Expressions.Expression.TypeIs%28System.Linq.Expressions.Expression%2CSystem.Type%29>|`bool isof(type p0)`|  
  
 또한 클라이언트가 추가 CLR 함수를 계산할 수 있습니다. A <xref:System.NotSupportedException> 는 식에 클라이언트에서 계산할 수 없고 서버에서 계산 하기 위해 올바른 요청 URI로 변환할 수 없는 경우에 발생 합니다.  
  
## <a name="see-also"></a>참고 항목  
 [데이터 서비스 쿼리](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md)   
 [쿼리 프로젝션](../../../../docs/framework/data/wcf/query-projections-wcf-data-services.md)   
 [개체 구체화](../../../../docs/framework/data/wcf/object-materialization-wcf-data-services.md)   
 [OData: URI 규칙](http://go.microsoft.com/fwlink/?LinkID=185564)