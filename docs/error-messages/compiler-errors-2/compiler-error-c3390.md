---
title: Błąd kompilatora C3390
ms.date: 11/04/2016
f1_keywords:
- C3390
helpviewer_keywords:
- C3390
ms.assetid: 84800a87-c8e6-45aa-82ae-02f816dc8d97
ms.openlocfilehash: 3f1149d4584a0ea3d0061a3ec4e2b77830603ef2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62400321"
---
# <a name="compiler-error-c3390"></a>Błąd kompilatora C3390

"type_arg": nieprawidłowy typ argumentu dla parametru generycznego param, z ogólnego "generic_type" musi być typem referencyjnym

Niepoprawnie wystąpienia typu ogólnego.  Sprawdź definicję typu.  Aby uzyskać więcej informacji, zobacz [ogólne](../../extensions/generics-cpp-component-extensions.md).

## <a name="example"></a>Przykład

W pierwszym przykładzie użyto C# tworzenia składnika, który zawiera typ ogólny, który ma pewne ograniczenia, które nie są obsługiwane w przypadku tworzenia typów ogólnych w C++/CLR. Aby uzyskać więcej informacji, zobacz [ograniczenia dotyczące parametrów typu](/dotnet/csharp/programming-guide/generics/constraints-on-type-parameters).

```cs
// C3390.cs
// Compile by using: csc /target:library C3390.cs
// a C# program
public class GR<C, V, N>
where C : class
where V : struct
where N : new() {}
```

Po udostępnieniu składnika C3390.dll poniższy przykład spowoduje wygenerowanie C3390.

```cpp
// C3390_b.cpp
// Compile by using: cl /clr C3390_b.cpp
#using <C3390.dll>
ref class R { R(int) {} };
value class V {};
ref struct N { N() {} };

int main () {
   GR<V, V, N^>^ gr2;   // C3390 first type must be a ref type
   GR<R^, V, N^>^ gr2b; // OK
}
```