---
title: Kompilator ostrzeżenie (poziom 1) C4744
ms.date: 11/04/2016
f1_keywords:
- C4744
helpviewer_keywords:
- C4744
ms.assetid: f2a7d0b5-afd5-4926-abc3-cfbd367e3ff5
ms.openlocfilehash: 2118a32af8b99d35c1e1a6691561391ec5d2b8cc
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62385423"
---
# <a name="compiler-warning-level-1-c4744"></a>Kompilator ostrzeżenie (poziom 1) C4744

"var" ma inny typ w 'plik1' i 'plik2': 'Typ1' i 'type2'

Zewnętrznej zmiennej lub odwołuje się do zdefiniowanych w dwóch plikach ma różne typy w tych plikach.  Aby rozwiązać problem, ten sam definicje typów lub zmień nazwę zmiennej w jeden z plików.

C4744 jest emitowane tylko wtedy, gdy pliki są kompilowane z opcją/GL.  Aby uzyskać więcej informacji, zobacz [/GL (Optymalizacja Całoprogramowa)](../../build/reference/gl-whole-program-optimization.md).

> [!NOTE]
>  C4744 zwykle występuje w plikach C (nie C++), ponieważ w języku C++ nazwę zmiennej ma informacje o typie.  Próbki (poniżej) jest kompiluje co kod C++, otrzymasz błąd konsolidatora LNK2019.

## <a name="example"></a>Przykład

Ten przykład zawiera pierwszą definicję.

```
// C4744.c
// compile with: /c /GL
int global;
```

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C4744.

```
// C4744b.c
// compile with: C4744.c /GL /W1
// C4744 expected
#include <stdio.h>

extern unsigned global;

main()
{
    printf_s("%d\n", global);
}
```