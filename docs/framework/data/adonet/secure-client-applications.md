---
title: 안전한 클라이언트 응용 프로그램
ms.date: 03/30/2017
ms.assetid: 6239592e-fa7d-4dea-9f00-d296d0048b01
ms.openlocfilehash: ac4f1c3debacd89a0763aa8f30de3c5463c5d24d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/04/2018
---
# <a name="secure-client-applications"></a>안전한 클라이언트 응용 프로그램
일반적으로 응용 프로그램은 데이터 손실을 야기하거나 시스템을 손상시킬 수 있는 취약성으로부터 보호되어야 하는 다양한 부분으로 구성됩니다. 안전한 사용자 인터페이스를 만들면 공격자가 데이터나 시스템 리소스에 액세스하기 전에 이를 차단함으로써 여러 가지 문제를 예방할 수 있습니다.  
  
## <a name="validate-user-input"></a>사용자 입력 유효성 검사  
 데이터에 액세스하는 응용 프로그램을 만들 경우 유효성이 입증되기 전에는 모든 사용자 입력을 악의적인 것으로 간주해야 합니다. 그렇지 않으면 응용 프로그램이 공격에 취약해질 수 있습니다. .NET Framework에서는 입력할 수 있는 문자 수를 제한하는 등 입력 컨트롤에 대한 값 범위를 설정할 수 있게 해 주는 클래스가 포함되어 있으며, 값의 유효성을 검사하는 프로시저를 작성하기 위한 이벤트 후크도 제공합니다. 사용자 입력 데이터에 대해 유효성을 검사하고 강력한 형식을 지정함으로써 응용 프로그램이 스크립트나 SQL 삽입 공격에 노출되지 않도록 할 수 있습니다.  
  
> [!IMPORTANT]
>  클라이언트 응용 프로그램뿐만 아니라 데이터 소스에서도 사용자 입력의 유효성을 검사해야 합니다. 공격자가 응용 프로그램에 침투하여 데이터 소스를 직접 공격하는 방식을 선택할 수도 있습니다.  
  
 [보안 및 사용자 입력](../../../../docs/standard/security/security-and-user-input.md)  
 사용자 입력과 관련하여 잠재적 위험이 있는 버그를 처리하는 방법에 대해 설명합니다.  
  
 [ASP.NET 웹 페이지에서 사용자 입력 유효성 검사](http://msdn.microsoft.com/library/4ad3dacb-89e0-4cee-89ac-40a3f2a85461)  
 ASP.NET 유효성 검사 컨트롤을 통한 사용자 입력 유효성 검사에 대해 간략하게 설명합니다.  
  
 [Windows Forms에 사용자 입력](../../../../docs/framework/winforms/user-input-in-windows-forms.md)  
 Windows Forms 응용 프로그램의 마우스 및 키보드 입력에 대한 유효성 검사와 관련된 정보 및 링크를 제공합니다.  
  
 [.NET Framework 정규식](../../../../docs/standard/base-types/regular-expressions.md)  
 <xref:System.Text.RegularExpressions.Regex> 클래스를 사용하여 사용자 입력의 유효성을 검사하는 방법에 대해 설명합니다.  
  
## <a name="windows-applications"></a>Windows 응용 프로그램  
 예전에는 일반적으로 Windows 응용 프로그램이 모든 권한으로 실행되었습니다. .NET Framework에서는 CAS(코드 액세스 보안)를 사용하여 Windows 응용 프로그램에서의 코드 실행을 제한하는 인프라를 제공합니다. 하지만 CAS만으로는 응용 프로그램을 보호하기에 부족합니다.  
  
 [Windows Forms 보안](../../../../docs/framework/winforms/windows-forms-security.md)  
 Windows Forms 응용 프로그램의 보안을 유지하는 방법을 설명하며 관련 항목 링크를 제공합니다.  
  
 [Windows Forms 및 관리되지 않는 응용 프로그램](../../../../docs/framework/winforms/advanced/windows-forms-and-unmanaged-applications.md)  
 Windows Forms 응용 프로그램에서 관리되지 않는 응용 프로그램과 상호 작용하는 방법에 대해 설명합니다.  
  
 [ClickOnce 배포에 대 한 Windows Forms 응용 프로그램](http://msdn.microsoft.com/library/34d8c770-48f2-460c-8d67-4ea5684511df)  
 Windows Forms 응용 프로그램에서 `ClickOnce` 배포를 사용하는 방법 및 이와 관련된 보안 문제에 대해 설명합니다.  
  
## <a name="aspnet-and-xml-web-services"></a>ASP.NET 및 XML Web Services  
 ASP.NET 응용 프로그램은 일반적으로 웹 사이트의 특정 부분에 대한 액세스를 제한하고 데이터 보호 및 사이트 보안을 위한 기타 메커니즘을 제공해야 합니다. 다음 링크에서는 ASP.NET 응용 프로그램 보안에 관련된 유용한 정보를 제공합니다.  
  
 XML Web service는 ASP.NET 응용 프로그램, Windows Forms 응용 프로그램 또는 다른 웹 서비스에서 사용할 수 있는 데이터를 제공합니다. 따라서 클라이언트 응용 프로그램의 보안뿐만 아니라 웹 서비스 자체의 보안도 관리해야 합니다.  
  
 자세한 내용은 다음 리소스를 참조하세요.  
  
|리소스|설명|  
|--------------|-----------------|  
|[NIB: ASP.NET 보안](http://msdn.microsoft.com/library/04b37532-18d9-40b4-8e5f-ee09a70b311d)|ASP.NET 응용 프로그램의 보안을 유지하는 방법을 설명합니다.|  
|[ASP.NET을 사용 하 여 만든 XML 웹 서비스 보안](http://msdn.microsoft.com/library/354b2ab1-2782-4542-b32a-dc560178b90c)|ASP.NET 웹 서비스의 보안을 구현하는 방법을 설명합니다.|  
|[스크립트 악용 개요](http://msdn.microsoft.com/library/772c7312-211a-4eb3-8d6e-eec0aa1dcc07)|악의적인 문자를 웹 페이지에 삽입하려고 시도하는 스크립트 기반 공격을 차단하는 방법에 대해 설명합니다.|  
|[ASP.NET 웹 응용 프로그램에 대 한 보안 사례 NIB: 기본](http://msdn.microsoft.com/library/94a52ab8-731d-417e-b997-721baf43df38)|일반 보안 관련 정보와 추가 정보에 대한 링크를 제공합니다.|  
  
## <a name="remoting"></a>원격 통신  
 .NET Remoting을 사용하면 응용 프로그램 구성 요소가 모두 한 컴퓨터에 있는지 또는 전 세계에 분산되어 있는지 여부에 관계없이 다양한 영역에 배포되는 응용 프로그램을 쉽게 만들 수 있습니다. 같은 컴퓨터 또는 해당 네트워크를 통해 연결할 수 있는 다른 모든 컴퓨터에 있는 다른 프로세스의 개체를 사용하는 클라이언트 응용 프로그램을 빌드할 수 있습니다. 또한 .NET Remoting을 사용하면 동일한 프로세스에 있는 다른 응용 프로그램 도메인과 통신할 수도 있습니다.  
  
|리소스|설명|  
|--------------|-----------------|  
|[원격 응용 프로그램의 구성](http://msdn.microsoft.com/library/92c0c097-d984-4315-835b-7490ecdf1097)|자주 발생하는 문제를 피할 수 있도록 원격 응용 프로그램을 구성하는 방법에 대해 설명합니다.|  
|[원격 서비스의 보안](http://msdn.microsoft.com/library/9574262c-d4b1-41c5-8600-24ff147c0add)|인증 및 암호화에 대해 설명하고 원격 통신과 관련한 추가 보안 항목을 제공합니다.|  
|[보안 및 원격 서비스 고려 사항](../../../../docs/framework/misc/security-and-remoting-considerations.md)|보호되는 개체 및 응용 프로그램 도메인 간의 보안 문제에 대해 설명합니다.|  
  
## <a name="see-also"></a>참고 항목  
 [ADO.NET 응용 프로그램 보안](../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 [데이터 액세스 전략에 대 한 권장 사항](http://msdn.microsoft.com/library/72411f32-d12a-4de8-b961-e54fca7faaf5)  
 [응용 프로그램 보안](/visualstudio/ide/securing-applications)  
 [연결 정보 보호](../../../../docs/framework/data/adonet/protecting-connection-information.md)  
 [ADO.NET 관리되는 공급자 및 데이터 집합 개발자 센터](http://go.microsoft.com/fwlink/?LinkId=217917)
