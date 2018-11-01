---
title: zarządzane, niezarządzane
ms.date: 11/04/2016
f1_keywords:
- vc-pragma.unmanaged
- managed_CPP
- unmanaged_CPP
- vc-pragma.managed
helpviewer_keywords:
- managed pragma
- pragmas, unmanaged
- pragmas, managed
- unmanaged pragma
ms.assetid: f072ddcc-e1ec-408a-8ce1-326ddb60e4a4
ms.openlocfilehash: 0cc253ad7d0d4529340a13546f931075b0c7dfdc
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50473830"
---
# <a name="managed-unmanaged"></a>zarządzane, niezarządzane
Włącz kontrolę poziomie funkcji do kompilowania funkcji jako zarządzane lub niezarządzane.

## <a name="syntax"></a>Składnia

```
#pragma managed
#pragma unmanaged
#pragma managed([push,] on | off)
#pragma managed(pop)
```

## <a name="remarks"></a>Uwagi

[/CLR](../build/reference/clr-common-language-runtime-compilation.md) — opcja kompilatora można kontrolować poziom modułu do kompilowania funkcji, jako zarządzane lub niezarządzane.

Niezarządzanej funkcji zostanie skompilowany dla platformy natywnej, a wykonanie tej części, program zostanie przekazany do platformy natywnej przez środowisko uruchomieniowe języka wspólnego.

Funkcje są kompilowane jako zarządzany domyślnie podczas `/clr` jest używany.

Podczas stosowania tych pragmy:

- Dodaj pragma poprzedzających funkcji, ale nie w treści funkcji.

- Dodaj dyrektywę po `#include` instrukcji. Nie należy używać tych pragm przed `#include` instrukcji.

Kompilator ignoruje **zarządzane** i **niezarządzanych** pragm Jeśli `/clr` nie jest używany w kompilacji.

Podczas tworzenia wystąpienia szablonu funkcji stan pragmy w czasie definicji szablonu określa, czy ma zarządzane lub niezarządzane.

Aby uzyskać więcej informacji, zobacz [inicjowanie zestawów mieszanych](../dotnet/initialization-of-mixed-assemblies.md).

## <a name="example"></a>Przykład

```cpp
// pragma_directives_managed_unmanaged.cpp
// compile with: /clr
#include <stdio.h>

// func1 is managed
void func1() {
   System::Console::WriteLine("In managed function.");
}

// #pragma unmanaged
// push managed state on to stack and set unmanaged state
#pragma managed(push, off)

// func2 is unmanaged
void func2() {
   printf("In unmanaged function.\n");
}

// #pragma managed
#pragma managed(pop)

// main is managed
int main() {
   func1();
   func2();
}
```

```Output
In managed function.
In unmanaged function.
```

## <a name="see-also"></a>Zobacz też

[Dyrektywy pragma i słowo kluczowe __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)