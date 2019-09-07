---
title: Opakowanie (C++/CX)
ms.date: 12/30/2016
ms.assetid: edfb12fa-2a9b-42f6-bdac-d4d76cb8274e
ms.openlocfilehash: 90c5af31efc6523683227dbf54c85390bc98510a
ms.sourcegitcommit: 180f63704f6ddd07a4172a93b179cf0733fd952d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70740665"
---
# <a name="boxing-ccx"></a>Opakowanie (C++/CX)

*Opakowanie* dzieli zmienną typu wartości, taką jak [Windows:: Foundation::D atetime](/uwp/api/windows.foundation.datetime)— lub podstawowy typ skalarny, taki `int`jak — w klasie referencyjnej, gdy zmienna jest przenoszona do metody przyjmującej [platform:: Object ^](../cppcx/platform-object-class.md) jako typ danych wejściowych .

## <a name="passing-a-value-type-to-an-object-parameter"></a>Przekazywanie typu wartości do obiektu ^ Parameter

Chociaż nie musisz jawnie korzystać z zmiennej, aby przekazać ją do parametru metody typu [platform:: Object ^](../cppcx/platform-object-class.md), musisz jawnie rzutować z powrotem do oryginalnego typu podczas pobierania wartości, które zostały wcześniej opakowane.

[!code-cpp[cx_boxing#01](../cppcx/codesnippet/CPP/cx_boxing/class1.cpp#01)]

### <a name="using-platformiboxt-to-support-nullable-value-types"></a>Używanie funkcji platform::\<IBox T > do obsługi typów wartości null

C#i Visual Basic wspierać koncepcję typów wartości null. W C++/CX można użyć `Platform::IBox<T>` typu, aby uwidocznić metody publiczne, które obsługują parametry typu wartości null. Poniższy przykład przedstawia metodę publiczną C++/CX, która zwraca wartość null, C# gdy obiekt wywołujący przekazuje wartość null dla jednego z argumentów.

[!code-cpp[cx_boxing#02](../cppcx/codesnippet/CPP/cx_boxing/class1.h#02)]

W kliencie C# XAML można wykorzystać go w następujący sposób:

```

// C# client code
    BoxingDemo.Class1 obj = new BoxingDemo.Class1();
    int? a = null;
    int? b = 5;
    var result = obj.Multiply(a,b); //result = null
```

## <a name="see-also"></a>Zobacz także

[System typów (C++/CX)](../cppcx/type-system-c-cx.md)<br/>
[Rzutowanie (C++/CX)](../cppcx/casting-c-cx.md)<br/>
[Dokumentacja języka C++/CX](../cppcx/visual-c-language-reference-c-cx.md)<br/>
[Dokumentacja przestrzeni nazw](../cppcx/namespaces-reference-c-cx.md)
