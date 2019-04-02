---
title: Błąd kompilatora C3391
ms.date: 11/04/2016
f1_keywords:
- C3391
helpviewer_keywords:
- C3391
ms.assetid: c32532b9-7db4-4ccd-84b9-479e5a1a19d1
ms.openlocfilehash: 32ba1ca63a3a6fafa3290946a976e6845385126f
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/01/2019
ms.locfileid: "58772595"
---
# <a name="compiler-error-c3391"></a>Błąd kompilatora C3391

"type_arg": nieprawidłowy typ argumentu dla parametru generycznego param, z ogólnego "generic_type" musi być typem wartości niedopuszczającym wartości

Niepoprawnie wystąpienia typu ogólnego. Sprawdź definicję typu. Aby uzyskać więcej informacji, zobacz <xref:System.Nullable> i [ogólne](../../extensions/generics-cpp-component-extensions.md).

## <a name="example"></a>Przykład

Poniższy przykład używa języka C# w celu utworzenia składnika, który zawiera typ ogólny, który ma pewne ograniczenia, które nie są obsługiwane w przypadku tworzenia typów ogólnych w języku C + +/ interfejsu wiersza polecenia. Aby uzyskać więcej informacji, zobacz [ograniczenia dotyczące parametrów typu](/dotnet/csharp/programming-guide/generics/constraints-on-type-parameters).

```cs
// C3391.cs
// Compile by using: csc /target:library C3391.cs
// a C# program
public class GR<N>
where N : struct {}
```

Po udostępnieniu składnika C3391.dll poniższy przykład spowoduje wygenerowanie C3391.

```cpp
// C3391_b.cpp
// Compile by using: cl /clr C3391_b.cpp
#using <C3391.dll>
using namespace System;
value class VClass {};

int main() {
   GR< Nullable<VClass> >^ a =
      gcnew GR< Nullable<VClass> >();   // C3391 can't be Nullable
   GR<VClass>^ aa = gcnew GR<VClass>(); // OK
}
```