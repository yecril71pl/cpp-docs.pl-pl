---
title: Kompilator ostrzeżenie (poziom 1) C4794
ms.date: 11/04/2016
f1_keywords:
- C4794
helpviewer_keywords:
- C4794
ms.assetid: badc9c36-fa1a-4fec-929b-7bfda7a7b79f
ms.openlocfilehash: d44e3af88de9457fdc5c2df905ccbae22d3562da
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50464080"
---
# <a name="compiler-warning-level-1-c4794"></a>Kompilator ostrzeżenie (poziom 1) C4794

segment zmiennej lokalny magazyn wątków 'Zmienna' zmieniony z "Nazwa sekcji" na ".tls$"

Użyte [#pragma data_seg](../../preprocessor/data-seg.md) umieścić zmiennej tls w sekcji nie uruchamia się za pomocą .tls$.

.Tls$*x* sekcji będzie istnieć w pliku obiektu gdzie [__declspec(thread)](../../cpp/thread.md) zmienne są zdefiniowane. Sekcja .tls w pliku EXE lub DLL spowoduje w tych sekcjach.

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C4794:

```
// C4794.cpp
// compile with: /W1 /c
#pragma data_seg(".someseg")
__declspec(thread) int i;   // C4794

// OK
#pragma data_seg(".tls$9")
__declspec(thread) int j;
```