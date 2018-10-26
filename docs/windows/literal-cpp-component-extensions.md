---
title: literał (C + +/ CLI i C + +/ CX) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 10/12/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- literal
- literal_cpp
dev_langs:
- C++
helpviewer_keywords:
- literal keyword [C++]
ms.assetid: 6b1a1f36-2e1d-4a23-8eb6-172f4f3c477f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 626f05dff87bcff2d10d0726bcc10dfa767117d5
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50069926"
---
# <a name="literal-ccli-and-ccx"></a>literał (C + +/ CLI i C + +/ CX)

Zmienna (element członkowski danych) jest oznaczony jako **literału** w **/CLR** kompilacji odpowiada natywnych **statyczna stała** zmiennej.

## <a name="all-platforms"></a>Wszystkie platformy

### <a name="remarks"></a>Uwagi

(Nie ma żadnych uwag dla tej funkcji języka, które są stosowane do wszystkich środowisk uruchomieniowych).

## <a name="windows-runtime"></a>Środowisko wykonawcze systemu Windows

### <a name="remarks"></a>Uwagi

(Nie ma żadnych uwag dla tej funkcji języka, które dotyczą tylko środowiska uruchomieniowego Windows).

### <a name="requirements"></a>Wymagania

— Opcja kompilatora: `/ZW`

## <a name="common-language-runtime"></a>środowiska uruchomieniowe w trakcie wykonania

## <a name="remarks"></a>Uwagi

Element członkowski danych oznaczone jako **literału** musi być inicjowana, gdy zadeklarowana i wartość musi być stałe całkowite, enum lub typu string. Konwersja z typu wyrażenia inicjowania na typ statyczny const-składowej danych nie może wymagać konwersji zdefiniowanej przez użytkownika.

Nie pamięć została przydzielona dla pola literal w czasie wykonywania; Kompilator wstawia tylko jego wartości w metadanych dla tej klasy.

Oznaczone jako zmienną **statyczna stała** nie będą dostępne w metadanych innych kompilatorach.

Aby uzyskać więcej informacji, zobacz [statyczne](../cpp/storage-classes-cpp.md) i [const](../cpp/const-cpp.md).

**Literał** jest kontekstowej słowem kluczowym. Zobacz [Context-Sensitive Keywords](../windows/context-sensitive-keywords-cpp-component-extensions.md) Aby uzyskać więcej informacji.

## <a name="example"></a>Przykład

Ten przykład pokazuje, że **literału** zmienna oznacza **statyczne**.

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

Należy zauważyć różnicę w metadanych dla `sc` i `lit`: `modopt` dyrektywa jest stosowana do `sc`, czyli można zignorować przez inne kompilatory.

```
.field public static int32 modopt([mscorlib]System.Runtime.CompilerServices.IsConst) sc = int32(0x0000000A)
```

```
.field public static literal int32 lit = int32(0x0000000A)
```

## <a name="example"></a>Przykład

Odwołuje się do metadanych utworzony w poprzednim przykładzie poniższego przykładu, utworzone w języku C# i prezentuje wpływ **literału** i **statyczna stała** zmiennych:

```cs
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

— Opcja kompilatora: `/clr`

## <a name="see-also"></a>Zobacz też

[Rozszerzenia składników dla platformy .NET i platformy uniwersalnej systemu Windows](../windows/component-extensions-for-runtime-platforms.md)