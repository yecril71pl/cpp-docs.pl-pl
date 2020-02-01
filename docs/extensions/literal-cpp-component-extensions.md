---
title: Literal (C++/CLI i C++/CX)
ms.date: 10/12/2018
ms.topic: reference
f1_keywords:
- literal
- literal_cpp
helpviewer_keywords:
- literal keyword [C++]
ms.assetid: 6b1a1f36-2e1d-4a23-8eb6-172f4f3c477f
ms.openlocfilehash: d567f8270dcb8965ed2f882c9a0c005f295fc619
ms.sourcegitcommit: c4528a7424d35039454f17778baf1b5f98fbbee7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/01/2020
ms.locfileid: "76912831"
---
# <a name="literal-ccli-and-ccx"></a>Literal (C++/CLI i C++/CX)

Zmienna (składowa danych) oznaczona jako **literał** w kompilacji **/CLR** jest natywnym odpowiednikiem zmiennej **static const** .

## <a name="all-platforms"></a>Wszystkie platformy

### <a name="remarks"></a>Uwagi

(Nie ma żadnych uwag dla tej funkcji języka, które mają zastosowanie do wszystkich środowisk uruchomieniowych).

## <a name="windows-runtime"></a>Środowisko wykonawcze systemu Windows

### <a name="remarks"></a>Uwagi

(Nie ma żadnych uwag dla tej funkcji języka, które mają zastosowanie tylko do środowisko wykonawcze systemu Windows).

### <a name="requirements"></a>Wymagania

Opcja kompilatora: `/ZW`

## <a name="common-language-runtime"></a>środowiska uruchomieniowe w trakcie wykonania

## <a name="remarks"></a>Uwagi

Element członkowski danych oznaczony jako **Literal** musi być zainicjowany, gdy jest zadeklarowany, a wartość musi być stałym typem całkowitym, wyliczeniem lub ciągiem. Konwersja z typu wyrażenia inicjującego na typ składowej danych static const nie może wymagać konwersji zdefiniowanej przez użytkownika.

Nie przydzielono pamięci dla pola literału w czasie wykonywania; kompilator wstawia tylko swoją wartość w metadanych dla klasy.

Zmienna oznaczona jako **static const** nie będzie dostępna w metadanych do innych kompilatorów.

Aby uzyskać więcej informacji, zobacz [static](../cpp/storage-classes-cpp.md) and [const](../cpp/const-cpp.md).

**Literal** jest kontekstowym słowem kluczowym. Aby uzyskać więcej informacji, zobacz [kontekstowe słowa kluczowe](context-sensitive-keywords-cpp-component-extensions.md) .

## <a name="example"></a>Przykład

Ten przykład pokazuje, że zmienna **literału** oznacza **statyczny**.

```cpp
// mcppv2_literal.cpp
// compile with: /clr
ref struct X {
   literal int i = 4;
};

int main() {
   int value = X::i;
}
```

## <a name="example"></a>Przykład

Poniższy przykład pokazuje wpływ literału w metadanych:

```cpp
// mcppv2_literal2.cpp
// compile with: /clr /LD
public ref struct A {
   literal int lit = 0;
   static const int sc = 1;
};
```

Zwróć uwagę na różnice w metadanych dla `sc` i `lit`: dyrektywa `modopt` jest stosowana do `sc`, co oznacza, że może być ignorowana przez inne kompilatory.

```
.field public static int32 modopt([mscorlib]System.Runtime.CompilerServices.IsConst) sc = int32(0x0000000A)
```

```
.field public static literal int32 lit = int32(0x0000000A)
```

## <a name="example"></a>Przykład

Poniższy przykład, który został utworzony w C#, odwołuje się do metadanych utworzonych w poprzednim przykładzie i pokazuje wpływ **literału** i **statyczne zmienne stałe** :

```csharp
// mcppv2_literal3.cs
// compile with: /reference:mcppv2_literal2.dll
// A C# program
class B {
   public static void Main() {
      // OK
      System.Console.WriteLine(A.lit);
      System.Console.WriteLine(A.sc);

      // C# does not enforce C++ const
      A.sc = 9;
      System.Console.WriteLine(A.sc);

      // C# enforces const for a literal
      A.lit = 9;   // CS0131

      // you can assign a C++ literal variable to a C# const variable
      const int i = A.lit;
      System.Console.WriteLine(i);

      // but you cannot assign a C++ static const variable
      // to a C# const variable
      const int j = A.sc;   // CS0133
      System.Console.WriteLine(j);
   }
}
```

## <a name="requirements"></a>Wymagania

Opcja kompilatora: `/clr`

## <a name="see-also"></a>Zobacz także

[Rozszerzenia składników dla platformy .NET i platformy uniwersalnej systemu Windows](component-extensions-for-runtime-platforms.md)