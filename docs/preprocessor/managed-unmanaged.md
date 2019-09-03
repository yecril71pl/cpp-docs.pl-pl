---
title: managed, unmanaged, pragmy
ms.date: 08/29/2019
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
ms.openlocfilehash: 4c13155d1c84966a593df11baf525a0c3539f02c
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2019
ms.locfileid: "70218812"
---
# <a name="managed-unmanaged-pragmas"></a>managed, unmanaged, pragmy

Włącz kontrolę poziomu funkcji, aby kompilować funkcje jako zarządzane lub niezarządzane.

## <a name="syntax"></a>Składnia

> **#pragma zarządzany**\
> **niezarządzana #pragma**\
> **zarządzane #pragma (** [ **push,** ] { **on** | **off** } **)** \
> **zarządzane #pragma (pop)**

## <a name="remarks"></a>Uwagi

Opcja kompilatora [/CLR](../build/reference/clr-common-language-runtime-compilation.md) zapewnia kontrolę poziomu modułu do kompilowania funkcji jako zarządzanych lub niezarządzanych.

Funkcja niezarządzana zostanie skompilowana dla platformy natywnej. Wykonanie tej części programu zostanie przesłane do natywnej platformy przez środowisko uruchomieniowe języka wspólnego.

Funkcje są kompilowane jako zarządzane domyślnie, gdy `/clr` jest używany.

Podczas stosowania tych pragm:

- Dodaj pragmę poprzedzającą funkcję, ale nie w treści funkcji.

- Dodaj pragma After `#include` instrukcji. Nie używaj tych pragm przed `#include` instrukcją.

Kompilator ignoruje **zarządzane** i **niezarządzane** dyrektywy pragma, `/clr` Jeśli nie jest używany w kompilacji.

Gdy jest tworzone wystąpienie funkcji szablonu, pragma stan, gdy szablon jest zdefiniowany, określa, czy jest zarządzany lub niezarządzany.

Aby uzyskać więcej informacji, zobacz [Inicjowanie zestawów mieszanych](../dotnet/initialization-of-mixed-assemblies.md).

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

## <a name="see-also"></a>Zobacz także

[Dyrektywy pragma i słowo kluczowe __pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
