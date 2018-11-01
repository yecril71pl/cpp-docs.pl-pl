---
title: 'Porady: określanie parametru wyjściowego'
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- function parameters
- out parameters
ms.assetid: 02862448-603c-4e9d-a5c5-b45fe38446e3
ms.openlocfilehash: 8c3499a2916eda7ab96f7958df190c803206741e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50437092"
---
# <a name="how-to-specify-an-out-parameter"></a>Porady: określanie parametru wyjściowego

Niniejszy przykład pokazuje, jak określić, że parametr funkcji jest parametrem wyjściowym i jak wywołać tę funkcję z poziomu programu C#.

Określono parametru wyjściowego w programie Visual C++ przy użyciu <xref:System.Runtime.InteropServices.OutAttribute> .

## <a name="example"></a>Przykład

Pierwsza część w tym przykładzie jest plikiem Visual C++ z typu, który zawiera funkcję z parametrem out.

```
// cpp_out_param.cpp
// compile with: /LD /clr:safe
using namespace System;
public value struct TestStruct {
   static void Test([Runtime::InteropServices::Out] String^ %s) {
      s = "a string";
   }
};
```

## <a name="example"></a>Przykład

Jest to klienta języka C#, który używa składnika Visual C++, utworzony w poprzednim przykładzie.

```
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

## <a name="see-also"></a>Zobacz też

[Korzystanie z międzyoperacyjności języka C++ (niejawna funkcja PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)