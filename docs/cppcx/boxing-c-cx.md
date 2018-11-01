---
title: Konwersja boxing (C + +/ CX)
ms.date: 12/30/2016
ms.assetid: edfb12fa-2a9b-42f6-bdac-d4d76cb8274e
ms.openlocfilehash: dd950e2463da7541ebad731e74275ce360a1c8a4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50491042"
---
# <a name="boxing-ccx"></a>Konwersja boxing (C + +/ CX)

*Konwersja boxing* jest zawijany zmiennej typu wartości takie jak [Windows::Foundation::DateTime](https://msdn.microsoft.com/library/windows/apps/windows.foundation.datetime.aspx)— lub typem skalarnym o podstawowych, takich jak `int`— w klasie ref, gdy zmienna jest przekazywana do metody, która przyjmuje [ Platform::Object ^](../cppcx/platform-object-class.md) jako jej typ danych wejściowych.

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

[System typów (C++/CX)](../cppcx/type-system-c-cx.md)<br/>
[Rzutowanie (C++/CX)](../cppcx/casting-c-cx.md)<br/>
[Dokumentacja języka Visual C++](../cppcx/visual-c-language-reference-c-cx.md)<br/>
[Odwołanie do przestrzeni nazw](../cppcx/namespaces-reference-c-cx.md)