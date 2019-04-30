---
title: 'Instrukcje: Określanie braku parametrów'
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- function parameters
- out parameters
ms.assetid: 02862448-603c-4e9d-a5c5-b45fe38446e3
ms.openlocfilehash: 901257b92aaa5e13e6e79d612ca590b734e15881
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62387223"
---
# <a name="how-to-specify-an-out-parameter"></a>Instrukcje: Określanie braku parametrów

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

## <a name="see-also"></a>Zobacz także

[Korzystanie z międzyoperacyjności języka C++ (niejawna funkcja PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)
