---
title: Listy zmiennych argumentów (...) (C++/CLI)
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- variable argument lists
- parameter arrays
ms.assetid: db1a27f4-02a8-4318-8690-1f2893f52b38
ms.openlocfilehash: 8ea4d71bf9a22fc96c794a92ba43bed6548cf5d1
ms.sourcegitcommit: 89d9e1cb08fa872483d1cde98bc2a7c870e505e9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "82032307"
---
# <a name="variable-argument-lists--ccli"></a>Listy zmiennych argumentów (...) (C++/CLI)

W tym przykładzie pokazano, jak można użyć `...` składni w języku C++/CLI do zaimplementowania funkcji, które mają zmienną liczbę argumentów.

> [!NOTE]
> Ten temat dotyczy języka C++/CLI. Aby uzyskać informacje `...` na temat używania w iso standard C ++, zobacz [Wielokropek i szablony variadic](../cpp/ellipses-and-variadic-templates.md) i wielokropek i domyślne argumenty w [postfix wyrażeń](../cpp/postfix-expressions.md).

Parametr, który `...` używa musi być ostatnim parametrem na liście parametrów.

## <a name="example"></a>Przykład

### <a name="code"></a>Code

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

Poniższy przykład pokazuje, jak wywołać z języka C# visual C++ funkcja, która przyjmuje zmienną liczbę argumentów.

```cpp
// mcppv2_paramarray2.cpp
// compile with: /clr:safe /LD
using namespace System;

public ref class C {
public:
   void f( ... array<String^>^ a ) {}
};
```

Funkcja `f` może być wywoływana z języka C# lub Visual Basic, na przykład, jakby była to funkcja, która może przyjmować zmienną liczbę argumentów.

W języku C#argument, który `ParamArray` jest przekazywany do parametru może być wywoływana przez zmienną liczbę argumentów. Poniższy przykład kodu jest w języku C#.

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

Wywołanie `f` w języku Visual C++ może przekazać zainicjowaną tablicę lub tablicę o zmiennej długości.

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

## <a name="see-also"></a>Zobacz też

[Tablice](arrays-cpp-component-extensions.md)
