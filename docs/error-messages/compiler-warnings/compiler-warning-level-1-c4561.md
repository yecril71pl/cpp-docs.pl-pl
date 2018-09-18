---
title: Kompilator ostrzeżenie (poziom 1) C4561 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4561
dev_langs:
- C++
helpviewer_keywords:
- C4561
ms.assetid: 3a10c12c-601b-4b6c-9861-331fd022e021
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0ba0770a8b8b42c8174d421f55dd45ff7f335d06
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46115791"
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