---
title: Kompilator ostrzeżenie (poziom 1) C4561
ms.date: 11/04/2016
f1_keywords:
- C4561
helpviewer_keywords:
- C4561
ms.assetid: 3a10c12c-601b-4b6c-9861-331fd022e021
ms.openlocfilehash: 24a3ca8b35266e93f298314f45015b7a480e2af0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62397292"
---
# <a name="compiler-warning-level-1-c4561"></a>Kompilator ostrzeżenie (poziom 1) C4561

Wywołanie "__fastcall" niezgodne z "/ clr" opcja: konwertowanie "\__stdcall"

[__Fastcall](../../cpp/fastcall.md) Konwencja wywoływania funkcji nie można używać z [/CLR](../../build/reference/clr-common-language-runtime-compilation.md) — opcja kompilatora. Kompilator ignoruje wywołania `__fastcall`. Aby usunąć to ostrzeżenie, albo Usuń wywołania **__fastcall** lub skompilować bez **/CLR**.

Poniższy przykład spowoduje wygenerowanie C4561:

```
// C4561.cpp
// compile with: /clr /W1 /c
// processor: x86
void __fastcall Func(void *p);   // C4561, remove __fastcall to resolve
```