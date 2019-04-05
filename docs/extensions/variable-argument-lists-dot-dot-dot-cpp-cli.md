---
title: Listy zmiennych argumentów (...) (C++/CLI)
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- variable argument lists
- parameter arrays
ms.assetid: db1a27f4-02a8-4318-8690-1f2893f52b38
ms.openlocfilehash: ec1e2cefa33bc9d749d0f05e170c2f2db9b25f02
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/05/2019
ms.locfileid: "59031613"
---
# <a name="variable-argument-lists--ccli"></a>Listy zmiennych argumentów (...) (C++/CLI)

W tym przykładzie pokazano, jak za pomocą `...` składnię w języku C + +/ interfejsu wiersza polecenia, aby zaimplementować funkcje, które mają zmienną liczbę argumentów.

> [!NOTE]
> Ten temat dotyczy C + +/ interfejsu wiersza polecenia. Aby uzyskać informacje o korzystaniu z `...` w ISO Standard C++, zobacz [wielokropki i szablony Wariadyczne](../cpp/ellipses-and-variadic-templates.md) i wielokropki i argumenty domyślne w [wyrażenia przyrostków](../cpp/postfix-expressions.md).

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

Poniższy przykład pokazuje sposób wywoływania z kodu C# funkcji Visual C++, która przyjmuje zmienną liczbę argumentów.

```cpp
// mcppv2_paramarray2.cpp
// compile with: /clr:safe /LD
using namespace System;

public ref class C {
public:
   void f( ... array<String^>^ a ) {}
};
```

Funkcja `f` może być wywoływana z języka C# lub Visual Basic, na przykład tak, jakby była to funkcja, która może przyjąć zmienną liczbę argumentów.

W języku C# argument, który jest przekazywany do `ParamArray` parametru może być wywoływany przez zmienną liczbę argumentów. Poniższy przykładowy kod jest w języku C#.

```cs
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

Wywołanie `f` w programie Visual C++ można przekazać zainicjowanej tablicy lub tablicy o zmiennej długości.

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