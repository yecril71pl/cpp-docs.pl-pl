---
title: Ostrzeżenie kompilatora (poziom 1 i poziom 4) C4949
ms.date: 11/04/2016
f1_keywords:
- C4949
helpviewer_keywords:
- C4949
ms.assetid: 34f45a05-c115-49cb-9f67-0bd4f0735d9b
ms.openlocfilehash: f2876813131271ebb2561f8ea7435bb96dc2ce17
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/05/2019
ms.locfileid: "73627414"
---
# <a name="compiler-warning-level-1-and-level-4-c4949"></a>Ostrzeżenie kompilatora (poziom 1 i poziom 4) C4949

dyrektywy pragma "Managed" i "Unmanaged" mają znaczenie tylko wtedy, gdy skompilowano z opcją "/CLR [: Option]"

Kompilator ignoruje [zarządzane](../../preprocessor/managed-unmanaged.md) i niezarządzane dyrektywy pragma, jeśli kod źródłowy nie jest kompilowany z [/CLR](../../build/reference/clr-common-language-runtime-compilation.md). To ostrzeżenie jest informacje.

Poniższy przykład generuje C4949:

```cpp
// C4949.cpp
// compile with: /LD /W1
#pragma managed   // C4949
```

Gdy **#pragma niezarządzane** jest używany bez **/CLR**, C4949 jest ostrzeżeniem poziomu 4.

Poniższy przykład generuje C4949:

```cpp
// C4949b.cpp
// compile with: /LD /W4
#pragma unmanaged   // C4949
```