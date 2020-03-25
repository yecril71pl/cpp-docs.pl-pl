---
title: Błąd kompilatora C3391
ms.date: 11/04/2016
f1_keywords:
- C3391
helpviewer_keywords:
- C3391
ms.assetid: c32532b9-7db4-4ccd-84b9-479e5a1a19d1
ms.openlocfilehash: 98c4bf43883d15cd17877d7146edf16a73c7ce46
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80201107"
---
# <a name="compiler-error-c3391"></a>Błąd kompilatora C3391

"type_arg": nieprawidłowy typ argumentu dla parametru generycznego "param" generycznego "generic_type", musi być typem wartości niedopuszczających wartości null

Wystąpienie typu ogólnego zostało nieprawidłowo utworzone. Sprawdź definicję typu. Aby uzyskać więcej informacji, zobacz <xref:System.Nullable> i [typy ogólne](../../extensions/generics-cpp-component-extensions.md).

## <a name="example"></a>Przykład

Poniższy przykład używa C# do tworzenia składnika, który zawiera typ ogólny, który ma pewne ograniczenia, które nie są obsługiwane podczas tworzenia typów ogólnych w C++/CLI. Aby uzyskać więcej informacji, zobacz [ograniczenia dotyczące parametrów typu](/dotnet/csharp/programming-guide/generics/constraints-on-type-parameters).

```csharp
// C3391.cs
// Compile by using: csc /target:library C3391.cs
// a C# program
public class GR<N>
where N : struct {}
```

Gdy składnik C3391. dll jest dostępny, Poniższy przykład generuje C3391.

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
