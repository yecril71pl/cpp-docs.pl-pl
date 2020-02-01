---
title: Listy zmiennych argumentów (...) (C++/CLI)
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- variable argument lists
- parameter arrays
ms.assetid: db1a27f4-02a8-4318-8690-1f2893f52b38
ms.openlocfilehash: 4db75653251a558d6f43f5be63098fbb26e1e6ff
ms.sourcegitcommit: c4528a7424d35039454f17778baf1b5f98fbbee7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/01/2020
ms.locfileid: "76912849"
---
# <a name="variable-argument-lists--ccli"></a>Listy zmiennych argumentów (...) (C++/CLI)

Ten przykład pokazuje, jak można użyć składni `...` w C++/CLI, aby zaimplementować funkcje, które mają zmienną liczbę argumentów.

> [!NOTE]
> Ten temat dotyczy C++/CLI. Aby uzyskać informacje o używaniu `...` w standardzie C++ISO, zobacz [wielokropek i szablony wariadyczne](../cpp/ellipses-and-variadic-templates.md) oraz wielokropki i argumenty domyślne w [wyrażeniach przyrostkowych](../cpp/postfix-expressions.md).

Parametr, który używa `...` musi być ostatnim parametrem na liście parametrów.

## <a name="example"></a>Przykład

### <a name="code"></a>Kod

```cpp
// mcppv2_paramarray.cpp
// compile with: /clr
using namespace System;
double average( ... array<Int32>^ arr ) {
   int i = arr->GetLength(0);
   double answer = 0.0;

   for (int j = 0 ; j < i ; j++)
      answer += arr[j];

   return answer / i;
}

int main() {
   Console::WriteLine("{0}", average( 1, 2, 3, 6 ));
}
```

```Output
3
```

## <a name="code-example"></a>Przykład kodu

Poniższy przykład pokazuje, jak wywołać z C# funkcji wizualizacji C++ , która przyjmuje zmienną liczbę argumentów.

```cpp
// mcppv2_paramarray2.cpp
// compile with: /clr:safe /LD
using namespace System;

public ref class C {
public:
   void f( ... array<String^>^ a ) {}
};
```

Funkcja `f` może być wywoływana z C# lub Visual Basic, na przykład, jakby była funkcją, która może przyjmować zmienną liczbę argumentów.

W C#programie argument, który jest przesyłany do `ParamArray` parametru może być wywoływany przez zmienną liczbę argumentów. Poniższy przykład kodu znajduje się w C#.

```csharp
// mcppv2_paramarray3.cs
// compile with: /r:mcppv2_paramarray2.dll
// a C# program

public class X {
   public static void Main() {
      // Visual C# will generate a String array to match the
      // ParamArray attribute
      C myc = new C();
      myc.f("hello", "there", "world");
   }
}
```

Wywołanie `f` w wizualizacji C++ może przekazać zainicjowaną tablicę lub tablicę o zmiennej długości.

```cpp
// mcpp_paramarray4.cpp
// compile with: /clr
using namespace System;

public ref class C {
public:
   void f( ... array<String^>^ a ) {}
};

int main() {
   C ^ myc = gcnew C();
   myc->f("hello", "world", "!!!");
}
```

## <a name="see-also"></a>Zobacz także

[Tablice](arrays-cpp-component-extensions.md)