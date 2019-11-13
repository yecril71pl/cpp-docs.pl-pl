---
title: Ostrzeżenie kompilatora (poziom 1) C4561
ms.date: 11/04/2016
f1_keywords:
- C4561
helpviewer_keywords:
- C4561
ms.assetid: 3a10c12c-601b-4b6c-9861-331fd022e021
ms.openlocfilehash: b0fd27142f0404a53fa2fee87fb2309e2f54d2c2
ms.sourcegitcommit: e5192a25c084eda9eabfa37626f3274507e026b3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/12/2019
ms.locfileid: "73965978"
---
# <a name="compiler-warning-level-1-c4561"></a>Ostrzeżenie kompilatora (poziom 1) C4561

element "__fastcall" jest niezgodny z opcją "/CLR": konwertowanie na "\__stdcall"

Nie można używać konwencji wywoływania funkcji [__fastcall](../../cpp/fastcall.md) z opcją kompilatora [/CLR](../../build/reference/clr-common-language-runtime-compilation.md) . Kompilator ignoruje wywołania `__fastcall`. Aby usunąć to ostrzeżenie, Usuń wywołania do **__fastcall** lub Kompiluj bez **/CLR**.

Poniższy przykład generuje C4561:

```cpp
// C4561.cpp
// compile with: /clr /W1 /c
// processor: x86
void __fastcall Func(void *p);   // C4561, remove __fastcall to resolve
```