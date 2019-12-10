---
title: 'Porady: określanie parametru wyjściowego'
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- function parameters
- out parameters
ms.assetid: 02862448-603c-4e9d-a5c5-b45fe38446e3
ms.openlocfilehash: 5f0b462e672de4408d50bf95d65c749bf1881078
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2019
ms.locfileid: "74988437"
---
# <a name="how-to-specify-an-out-parameter"></a>Porady: określanie parametru wyjściowego

Ten przykład pokazuje, jak określić, że parametr funkcji jest parametrem out i jak wywołać tę funkcję z C# programu.

Parametr out jest określony w wizualizacji C++ z <xref:System.Runtime.InteropServices.OutAttribute>.

## <a name="example"></a>Przykład

Pierwsza część tego przykładu jest wizualną C++ biblioteką DLL z typem, który zawiera funkcję z parametrem out.

```cpp
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

Jest to C# klient korzystający ze składnika wizualnego C++ utworzonego w poprzednim przykładzie.

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
