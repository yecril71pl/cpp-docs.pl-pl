---
title: Konwersja boxing (C + +/ CX) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: language-reference
ms.assetid: edfb12fa-2a9b-42f6-bdac-d4d76cb8274e
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 9e47313f65c4129bbc6fbf0a7bfbf698eb092f9f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="boxing-ccx"></a>Konwersja boxing (C + +/ CX)
*Konwersja boxing* jest zawijany takie jak zmienna typu wartości [Windows::Foundation::DateTime](http://msdn.microsoft.com/library/windows/apps/windows.foundation.datetime.aspx)— lub typem skalarnym podstawowych, takich jak `int`— w klasie ref, gdy zmienna została przekazana do metody pobierającej [ Platform::Object ^](../cppcx/platform-object-class.md) jako jego typ danych wejściowych.  
  
## <a name="passing-a-value-type-to-an-object-parameter"></a>Przekazywanie do obiektu typu wartości ^ parametru  
 Chociaż nie trzeba jawnie pole zmiennej, aby przekazać go do parametru metody typu [Platform::Object ^](../cppcx/platform-object-class.md), trzeba jawnie rzutowanie do oryginalnego typu podczas pobierania wartości, które zostały wcześniej ramce.  
  
 [!code-cpp[cx_boxing#01](../cppcx/codesnippet/CPP/cx_boxing/class1.cpp#01)]  
  
### <a name="using-platformiboxt-to-support-nullable-value-types"></a>Przy użyciu Platform::IBox\<T > do obsługi typów wartości null  
 C# i Visual Basic obsługuje pojęcie typów wartości null. W języku C + +/ CX, można użyć `Platform::IBox<T>` typu do udostępnienia metody publiczne, które obsługują parametrów typu wartość null. W poniższym przykładzie przedstawiono C + +/ CX metodę publiczną, która zwraca wartość null, gdy obiekt wywołujący C# przekazuje wartość null dla jednego z argumentów.  
  
 [!code-cpp[cx_boxing#02](../cppcx/codesnippet/CPP/cx_boxing/class1.h#02)]  
  
 W kliencie XAML C# będzie można korzystać następująco:  
  
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