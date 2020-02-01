---
title: 'Instrukcje: Określanie parametru out'
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- function parameters
- out parameters
ms.assetid: 02862448-603c-4e9d-a5c5-b45fe38446e3
ms.openlocfilehash: 4bd6ad1d3009adcc124bdeb90d9d67de07112de2
ms.sourcegitcommit: c4528a7424d35039454f17778baf1b5f98fbbee7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/01/2020
ms.locfileid: "76912793"
---
# <a name="how-to-specify-an-out-parameter"></a>Instrukcje: Określanie parametru out

Ten przykład pokazuje, jak określić, że parametr funkcji jest parametrem `out` i jak wywołać tę funkcję z C# programu.

Parametr `out` jest określony w programie C++ przy użyciu <xref:System.Runtime.InteropServices.OutAttribute>.

## <a name="example"></a>Przykład

Pierwsza część tego przykładu tworzy C++ bibliotekę DLL. Definiuje typ, który zawiera funkcję z parametrem `out`.

```cpp
// cpp_out_param.cpp
// compile with: /LD /clr
using namespace System;
public value struct TestStruct {
   static void Test([Runtime::InteropServices::Out] String^ %s) {
      s = "a string";
   }
};
```

Ten plik źródłowy jest C# klientem korzystającym z C++ składnika utworzonego w poprzednim przykładzie.

```csharp
// cpp_out_param_2.cs
// compile with: /reference:cpp_out_param.dll
using System;
class TestClass {
   public static void Main() {
      String t;
      TestStruct.Test(out t);
      System.Console.WriteLine(t);
   }
}
```

```Output
a string
```

## <a name="see-also"></a>Zobacz także

[Korzystanie z międzyoperacyjności języka C++ (niejawna funkcja PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)
