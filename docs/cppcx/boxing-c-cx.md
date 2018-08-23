---
title: Konwersja boxing (C + +/ CX) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: language-reference
ms.assetid: edfb12fa-2a9b-42f6-bdac-d4d76cb8274e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e70b908bddbf7034e1d60f16cb0e492c0a707586
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42598883"
---
# <a name="boxing-ccx"></a>Konwersja boxing (C + +/ CX)
*Konwersja boxing* jest zawijany zmiennej typu wartości takie jak [Windows::Foundation::DateTime](http://msdn.microsoft.com/library/windows/apps/windows.foundation.datetime.aspx)— lub typem skalarnym o podstawowych, takich jak `int`— w klasie ref, gdy zmienna jest przekazywana do metody, która przyjmuje [ Platform::Object ^](../cppcx/platform-object-class.md) jako jej typ danych wejściowych.  
  
## <a name="passing-a-value-type-to-an-object-parameter"></a>Przekazywanie typu wartości do obiektu ^ parametru  
 Mimo że nie trzeba jawnie polu zmiennej w celu przekazania go do parametru metody typu [Platform::Object ^](../cppcx/platform-object-class.md), trzeba jawnie rzutowane do oryginalnego typu podczas pobierania wartości, które zostały wcześniej ramce.  
  
 [!code-cpp[cx_boxing#01](../cppcx/codesnippet/CPP/cx_boxing/class1.cpp#01)]  
  
### <a name="using-platformiboxt-to-support-nullable-value-types"></a>Za pomocą Platform::IBox\<T > do obsługi typy o wartości zerowalnej  
 C# i Visual Basic obsługuje pojęcie typy o wartości zerowalnej. W języku C + +/ CX, można użyć `Platform::IBox<T>` typu do udostępnienia metody publiczne, które obsługują parametrów typu wartości null. Poniższy przykład pokazuje, w języku C + +/ CX metodę publiczną, która zwraca wartość null, gdy C# wywołujący przekazuje wartość null dla jednego z argumentów.  
  
 [!code-cpp[cx_boxing#02](../cppcx/codesnippet/CPP/cx_boxing/class1.h#02)]  
  
 W kliencie C#, XAML będzie można korzystać następująco:  
  
```  
  
// C# client code  
    BoxingDemo.Class1 obj = new BoxingDemo.Class1();  
    int? a = null;  
    int? b = 5;  
    var result = obj.Multiply(a,b); //result = null  
  
```  
  
## <a name="see-also"></a>Zobacz też  
 [System typów (C + +/ CX)](../cppcx/type-system-c-cx.md)   
 [Rzutowanie (C + +/ CX)](../cppcx/casting-c-cx.md)   
 [Dokumentacja języka Visual C++](../cppcx/visual-c-language-reference-c-cx.md)   
 [Odwołanie do przestrzeni nazw](../cppcx/namespaces-reference-c-cx.md)