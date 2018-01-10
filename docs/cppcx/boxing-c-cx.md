---
title: Konwersja boxing (C + +/ CX) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: edfb12fa-2a9b-42f6-bdac-d4d76cb8274e
caps.latest.revision: "12"
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 5d953e35c0fe238dc8dee76ad6c2d5aab7a0ab1b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="boxing-ccx"></a>Konwersja boxing (C + +/ CX)
*Konwersja boxing* jest zawijany takie jak zmienna typu wartości [Windows::Foundation::DateTime](http://msdn.microsoft.com/library/windows/apps/windows.foundation.datetime.aspx)— lub typem skalarnym podstawowych, takich jak `int`— w klasie ref, gdy zmienna została przekazana do metody pobierającej [Platform::Object ^](../cppcx/platform-object-class.md) jako jego typ danych wejściowych.  
  
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