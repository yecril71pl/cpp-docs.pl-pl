---
title: Błąd kompilatora C3390
description: Błąd kompilatora Microsoft C++ C3390, jego przyczyny i sposoby ich rozwiązywania.
ms.date: 09/26/2020
f1_keywords:
- C3390
helpviewer_keywords:
- C3390
ms.assetid: 84800a87-c8e6-45aa-82ae-02f816dc8d97
ms.openlocfilehash: 467b379d7f5a349a217b566dc55b28d5fbd789da
ms.sourcegitcommit: 94893973211d0b254c8bcdcf0779997dcc136b0c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/28/2020
ms.locfileid: "91414363"
---
# <a name="compiler-error-c3390"></a>Błąd kompilatora C3390

> "*type_arg*": nieprawidłowy typ argumentu dla parametru generycznego "*param*" generycznej "*generic_type*", musi być typem referencyjnym

Wystąpienie typu ogólnego zostało nieprawidłowo utworzone. Sprawdź definicję typu.

## <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [Ogólne](../../extensions/generics-cpp-component-extensions.md).

## <a name="example"></a>Przykład

Pierwszy przykład używa języka C# do tworzenia składnika, który zawiera typ ogólny. Ten typ ma pewne ograniczenia, które nie są obsługiwane podczas tworzenia typów ogólnych w języku C++/CLI. Aby uzyskać więcej informacji, zobacz [ograniczenia dotyczące parametrów typu](/dotnet/csharp/programming-guide/generics/constraints-on-type-parameters).

```csharp
// C3390.cs
// Compile by using: csc /target:library C3390.cs
// a C# program
public class GR<C, V, N>
where C : class
where V : struct
where N : new() {}
```

Gdy dostępny jest składnik C3390.dll, Poniższy przykład generuje C3390.

```cpp
// C3390_b.cpp
// Compile by using: cl /clr C3390_b.cpp
#using <C3390.dll>
ref class R { R(int) {} };
value class V {};
ref struct N { N() {} };

int main () {
   GR<V, V, N^>^ gr2;   // C3390 first type must be a ref type
   GR<R^, V, N^>^ gr2b; // OK - do this instead
}
```
