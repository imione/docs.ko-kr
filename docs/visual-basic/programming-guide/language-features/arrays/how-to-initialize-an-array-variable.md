---
title: '방법: Visual Basic에서 배열 변수 초기화'
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], initializing
- arrays [Visual Basic], variables
- arrays [Visual Basic], initializing
- arrays [Visual Basic], declaring
ms.assetid: aadd7a60-7ca4-4608-b986-091f19e7fc10
ms.openlocfilehash: ee8cb91fd2fae9637a0d0e33fca63a4cdb9d2fce
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-initialize-an-array-variable-in-visual-basic"></a>방법: Visual Basic에서 배열 변수 초기화
배열에 리터럴을 포함 하 여 배열 변수 초기화는 `New` 절과 배열의 초기 값을 지정 합니다. 형식을 지정 하거나 배열 리터럴의 값에서 유추 될 수 있도록 허용 합니다. 형식 유추 되는 방법에 대 한 자세한 내용은 "채우기는 배열에 초기 값"의 참조 [배열](../../../../visual-basic/programming-guide/language-features/arrays/index.md)합니다.  
  
### <a name="to-initialize-an-array-variable-by-using-an-array-literal"></a>배열 리터럴을 사용 하 여 배열 변수를 초기화 하려면  
  
-   에 `New` 절, 배열 값을 할당할 경우 중괄호 안에 요소 값을 제공 하거나 (`{}`). 다음 예제에서는 선언 만들고 형식의 요소가 있는 배열을 포함 하는 변수를 초기화 하는 여러 가지 방법으로 `Char`합니다.  
  
     [!code-vb[VbVbalrArrays#16](../../../../visual-basic/programming-guide/language-features/arrays/codesnippet/VisualBasic/how-to-initialize-an-array-variable_1.vb)]  
  
     각 문이 실행 된 후 만들어진 배열 길이가 2 초기 값이 포함 된 인덱스를 인덱스 0에 있는 요소와 3에 있습니다. 상한 값과 값이 모두를 제공 하는 경우에 인덱스 0부터 상한 까지의 모든 요소에 대 한 값을 포함 해야 합니다.  
  
     배열 리터럴을에서 요소 값을 지정할 경우 인덱스 상한을 지정할 필요가 없습니다 것을 확인 합니다. 상한이 없음을 지정 된 배열의 크기가 배열 리터럴의 값의 수에 따라 유추 됩니다.  
  
### <a name="to-initialize-a-multidimensional-array-variable-by-using-array-literals"></a>배열 리터럴을 사용 하 여 다차원 배열 변수를 초기화 하려면  
  
-   중괄호 안에 값을 중첩 (`{}`) 중괄호 안에 있습니다. 동일한 유형 및 길이 배열로 유추 모든 중첩 된 배열 리터럴을 있는지 확인 합니다. 다음 코드 예제에서는 다차원 배열 초기화의 몇 가지 예를 보여 줍니다.  
  
     [!code-vb[VbVbalrArrays#17](../../../../visual-basic/programming-guide/language-features/arrays/codesnippet/VisualBasic/how-to-initialize-an-array-variable_2.vb)]  
  
-   명시적으로 배열 범위를 지정 하거나 그대로 있고 컴파일러가 배열 리터럴의 값을 기반으로 배열 범위를 유추 하도록 합니다. 상한 및 값이 모두를 제공 하는 경우에 모든 차원에서 인덱스 0부터 상한 까지의 모든 요소에 대 한 값을 포함 해야 합니다. 다음 예제에서는 선언 만들고 형식의 요소가 있는 2 차원 배열을 포함 하는 변수를 초기화 하는 여러 가지 방법으로 `Short`  
  
     [!code-vb[VbVbalrArrays#18](../../../../visual-basic/programming-guide/language-features/arrays/codesnippet/VisualBasic/how-to-initialize-an-array-variable_3.vb)]  
  
     만들어진된 배열 인덱스는 6 개의 초기화 요소가 포함 각 문이 실행 된 후 `(0,0)`, `(0,1)`, `(0,2)`, `(1,0)`, `(1,1)`, 및 `(1,2)`합니다. 값을 포함 하는 각 배열 위치 `10`합니다.  
  
-   다음 예제에서는 다차원 배열을 반복 합니다. Visual Basic에서 작성 된 Windows 콘솔 응용 프로그램에서 내부 코드를 붙여 넣습니다.는 `Sub Main()` 메서드. 마지막 주석을 출력을 보여 줍니다.  
  
     [!code-vb[VbVbalrArrays#31](../../../../visual-basic/programming-guide/language-features/arrays/codesnippet/VisualBasic/how-to-initialize-an-array-variable_4.vb)]  
  
### <a name="to-initialize-a-jagged-array-variable-by-using-array-literals"></a>배열 리터럴을 사용 하 여 가변된 배열 변수를 초기화 하려면  
  
-   중괄호 안에 개체 값을 중첩 (`{}`). 가변된 배열의 경우 길이가 다른 배열을 지정 하는 배열 리터럴을 중첩할 수도 있지만 있는지 확인 하는 중첩 된 배열 리터럴을 괄호로 묶인 (`()`). 괄호는 중첩 된 배열 리터럴 평가 하 고 결과 배열은 가변 배열의 초기 값으로 사용 됩니다. 다음 코드 예제에서는 가변된 배열의 초기화는 두 가지 예를 보여 줍니다.  
  
     [!code-vb[VbVbalrArrays#19](../../../../visual-basic/programming-guide/language-features/arrays/codesnippet/VisualBasic/how-to-initialize-an-array-variable_5.vb)]  
  
-   다음 예제에서는 가변된 배열을 반복 합니다. Visual Basic에서 작성 된 Windows 콘솔 응용 프로그램에서 내부 코드를 붙여 넣습니다.는 `Sub Main()` 메서드.  코드의 마지막 주석을 출력을 보여 줍니다.  
  
     [!code-vb[VbVbalrArrays#32](../../../../visual-basic/programming-guide/language-features/arrays/codesnippet/VisualBasic/how-to-initialize-an-array-variable_6.vb)]  
  
## <a name="see-also"></a>참고 항목  
 [배열](../../../../visual-basic/programming-guide/language-features/arrays/index.md)  
 [배열 문제 해결](../../../../visual-basic/programming-guide/language-features/arrays/troubleshooting-arrays.md)
