---
title: Ostrzeżenie kompilatora (poziom 1 i poziom 4) C4949
ms.date: 11/04/2016
f1_keywords:
- C4949
helpviewer_keywords:
- C4949
ms.assetid: 34f45a05-c115-49cb-9f67-0bd4f0735d9b
ms.openlocfilehash: 7ce8b3242def187e4b8b442f403f92f013a9ca6e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80164784"
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
