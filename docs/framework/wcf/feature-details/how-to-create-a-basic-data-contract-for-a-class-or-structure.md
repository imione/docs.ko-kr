---
title: '방법: 클래스 또는 구조체에 대한 기본 데이터 계약 만들기'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataMemberAttribute
- DataContractAttribute class
- data contracts [WCF], creating for a class or structure
ms.assetid: bc464889-3070-4a2f-91d2-e788a0f686a7
ms.openlocfilehash: bb2cebabc8e51870398689ea032d27c72f0503b5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-create-a-basic-data-contract-for-a-class-or-structure"></a>방법: 클래스 또는 구조체에 대한 기본 데이터 계약 만들기
이 항목에서는 클래스 또는 구조를 사용하여 데이터 계약을 만드는 기본 단계를 보여 줍니다. 데이터 계약 및 사용 방법에 대 한 자세한 내용은 참조 하십시오. [를 사용 하 여 데이터 계약](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)합니다.  
  
 에서 기본 Windows Communication Foundation (WCF) 서비스 및 클라이언트를 만드는 단계를 안내 하는 방법에 대 한 참조는 [초보자를 위한 자습서](../../../../docs/framework/wcf/getting-started-tutorial.md)합니다. 기본 서비스와 클라이언트로 구성 된 작업 예제 응용 프로그램을 참조 하십시오. [기본 데이터 계약](../../../../docs/framework/wcf/samples/basic-data-contract.md)합니다.  
  
### <a name="to-create-a-basic-data-contract-for-a-class-or-structure"></a>클래스 또는 구조체에 대한 기본 데이터 계약을 만들려면  
  
1.  <xref:System.Runtime.Serialization.DataContractAttribute> 특성을 클래스에 적용하여 형식에 데이터 계약이 있음을 선언합니다. 특성이 없는 경우를 비롯한 모든 public 형식을 serialize할 있습니다. <xref:System.Runtime.Serialization.DataContractSerializer> 특성이 없는 경우 <xref:System.Runtime.Serialization.DataContractAttribute>는 데이터 계약을 유추합니다. 자세한 내용은 참조 [Serializable 형식](../../../../docs/framework/wcf/feature-details/serializable-types.md)합니다.  
  
2.  <xref:System.Runtime.Serialization.DataMemberAttribute> 특성을 각 멤버에 적용하여 serialize되는 멤버(속성, 필드 또는 이벤트)를 정의합니다. 이러한 멤버를 데이터 멤버라고 합니다. 기본적으로 모든 public 형식을 serialize할 있습니다. 자세한 내용은 참조 [Serializable 형식](../../../../docs/framework/wcf/feature-details/serializable-types.md)합니다.  
  
    > [!NOTE]
    >  <xref:System.Runtime.Serialization.DataMemberAttribute> 특성을 private 필드에 적용하여 데이터가 다른 사용자에게 노출되게 할 수 있습니다. 멤버에 중요한 데이터가 포함되지 않도록 해야 합니다.  
  
## <a name="example"></a>예제  
 다음 예제에서는 클래스 및 해당 멤버에 `Person` 및 <xref:System.Runtime.Serialization.DataContractAttribute> 특성을 적용하여 <xref:System.Runtime.Serialization.DataMemberAttribute> 형식의 데이터 계약을 만드는 방법을 보여 줍니다.  
  
 [!code-csharp[DataContractAttribute#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/datacontractattribute/cs/overview.cs#2)]
 [!code-vb[DataContractAttribute#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/datacontractattribute/vb/overview.vb#2)]  
  
## <a name="see-also"></a>참고 항목  
 <xref:System.Runtime.Serialization.DataContractAttribute>  
 <xref:System.Runtime.Serialization.DataMemberAttribute>  
 [데이터 계약 사용](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)  
 [초보자를 위한 자습서](../../../../docs/framework/wcf/getting-started-tutorial.md)  
 [시작](../../../../docs/framework/wcf/samples/getting-started-sample.md)
