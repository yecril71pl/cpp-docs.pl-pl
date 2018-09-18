---
title: Błąd kompilatora C3392 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3392
dev_langs:
- C++
helpviewer_keywords:
- C3392
ms.assetid: e4757596-e2aa-4314-b01e-5c4bfd2110e9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 04c69220cf9b6bf10a6bae8f9557f83d1e004752
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46112814"
---
# <a name="compiler-error-c3392"></a>Błąd kompilatora C3392

"type_arg": nieprawidłowy typ argumentu dla parametru generycznego param, z ogólnego "generic_type" musi mieć publicznego konstruktora bez parametrów

Niepoprawnie wystąpienia typu ogólnego. Sprawdź definicję typu. Aby uzyskać więcej informacji, zobacz [ogólne](../../windows/generics-cpp-component-extensions.md).

## <a name="example"></a>Przykład

Poniższy przykład używa języka C# w celu utworzenia składnika, który zawiera typ ogólny, który ma pewne ograniczenia, które nie są obsługiwane w przypadku tworzenia typów ogólnych w języku C + +/ interfejsu wiersza polecenia. Aby uzyskać więcej informacji, zobacz [ograniczenia dotyczące parametrów typu](/dotnet/csharp/programming-guide/generics/constraints-on-type-parameters).

```cs
// C3392.cs
// Compile by using: csc /target:library C3392.cs
// a C# program
public class GR<C, V, N>
where C : class
where V : struct
where N : new() {}
```

Po udostępnieniu składnika C3392.dll poniższy przykład spowoduje wygenerowanie C3392.

```cpp
// C3392_b.cpp
// Compile by using: cl /clr C3392_b.cpp
#using <C3392.dll>

ref class R { R(int) {} };
ref class N { N() {} };

value class V {};

ref class N2 { public: N2() {} };
ref class R2 { public: R2() {} };

int main () {
   GR<R^, V, N^>^ gr1;   // C3392
   GR<R^, V, N2^>^ gr1a; // OK

   GR<R^, N^, N^>^ gr3;  // C3392
   GR<R^, V, N2^>^ gr3a; // OK

   GR<R^, V, R^>^ gr4;   // C3392
   GR<R^, V, R2^>^ gr4a; // OK
}
```