---
title: "리플렉션을 사용하여 특성 액세스(C#) | Microsoft 문서"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: dce3a696-4ceb-489a-b5e4-322a83052f18
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: cfbcdccd8c648fcb3f989e2ee551ed33709ba784
ms.lasthandoff: 03/13/2017

---
# <a name="accessing-attributes-by-using-reflection-c"></a>리플렉션을 사용하여 특성 액세스(C#)
어느 정도 해당 정보를 검색하고 이에 따라 작업을 수행하지 않는다면 사용자 지정 특성을 정의하고 소스 코드에 배치할 수 있다는 사실은 별로 중요하지 않습니다. 리플렉션을 통해 사용자 지정 특성을 사용하여 정의된 정보를 검색할 수 있습니다. 핵심 메서드는 소스 코드 특성에 해당하는 런타임 항목인 개체의 배열을 반환하는 `GetCustomAttributes`입니다. 이 메서드에는 여러 개의 오버로드된 버전이 있습니다. 자세한 내용은 <xref:System.Attribute>를 참조하세요.  
  
 다음과 같은 특성 사양은  
  
```csharp  
[Author("P. Ackerman", version = 1.1)]  
class SampleClass  
```  
  
 다음과 개념적으로 동일합니다.  
  
```csharp  
Author anonymousAuthorObject = new Author("P. Ackerman");  
anonymousAuthorObject.version = 1.1;  
```  
  
 하지만 `SampleClass`에서 특성을 쿼리할 때까지 코드가 실행되지 않습니다. `SampleClass`에서 `GetCustomAttributes`를 호출하면 `Author` 개체가 위와 같이 구성 및 초기화됩니다. 클래스에 다른 특성이 있으면 다른 특성 개체가 비슷하게 구성됩니다. 그런 다음 `GetCustomAttributes`는 `Author` 개체 및 기타 특성 개체를 배열로 반환합니다. 이 배열을 반복하고, 각 배열 요소의 형식에 따라 적용된 특성을 확인하고, 특성 개체에서 정보를 추출할 수 있습니다.  
  
## <a name="example"></a>예제  
 다음은 전체 예제입니다. 사용자 지정 특성이 정의되고 여러 엔터티에 적용되고 리플렉션을 통해 검색됩니다.  
  
```csharp  
// Multiuse attribute.  
[System.AttributeUsage(System.AttributeTargets.Class |  
                       System.AttributeTargets.Struct,  
                       AllowMultiple = true)  // Multiuse attribute.  
]  
public class Author : System.Attribute  
{  
    string name;  
    public double version;  
  
    public Author(string name)  
    {  
        this.name = name;  
  
        // Default value.  
        version = 1.0;  
    }  
  
    public string GetName()  
    {  
        return name;  
    }  
}  
  
// Class with the Author attribute.  
[Author("P. Ackerman")]  
public class FirstClass  
{  
    // ...  
}  
  
// Class without the Author attribute.  
public class SecondClass  
{  
    // ...  
}  
  
// Class with multiple Author attributes.  
[Author("P. Ackerman"), Author("R. Koch", version = 2.0)]  
public class ThirdClass  
{  
    // ...  
}  
  
class TestAuthorAttribute  
{  
    static void Test()  
    {  
        PrintAuthorInfo(typeof(FirstClass));  
        PrintAuthorInfo(typeof(SecondClass));  
        PrintAuthorInfo(typeof(ThirdClass));  
    }  
  
    private static void PrintAuthorInfo(System.Type t)  
    {  
        System.Console.WriteLine("Author information for {0}", t);  
  
        // Using reflection.  
        System.Attribute[] attrs = System.Attribute.GetCustomAttributes(t);  // Reflection.  
  
        // Displaying output.  
        foreach (System.Attribute attr in attrs)  
        {  
            if (attr is Author)  
            {  
                Author a = (Author)attr;  
                System.Console.WriteLine("   {0}, version {1:f}", a.GetName(), a.version);  
            }  
        }  
    }  
}  
/* Output:  
    Author information for FirstClass  
       P. Ackerman, version 1.00  
    Author information for SecondClass  
    Author information for ThirdClass  
       R. Koch, version 2.00  
       P. Ackerman, version 1.00  
*/  
```  
  
## <a name="see-also"></a>참고 항목  
 <xref:System.Reflection>   
 <xref:System.Attribute>   
 [C# 프로그래밍 가이드](../../../../csharp/programming-guide/index.md)   
 [특성에 저장된 정보 검색](http://msdn.microsoft.com/library/37dfe4e3-7da0-48b6-a3d9-398981524e1c)   
 [리플렉션(C#)](../../../../csharp/programming-guide/concepts/reflection.md)   
 [특성(C#)](../../../../csharp/programming-guide/concepts/attributes/index.md)   
 [사용자 지정 특성 만들기(C#)](../../../../csharp/programming-guide/concepts/attributes/creating-custom-attributes.md)