---
title: Ostrzeżenie kompilatora (poziom 1) C4744
ms.date: 11/04/2016
f1_keywords:
- C4744
helpviewer_keywords:
- C4744
ms.assetid: f2a7d0b5-afd5-4926-abc3-cfbd367e3ff5
ms.openlocfilehash: f932b1bcdf011678d4f85e0edf1e116a954b59fe
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367377"
---
# <a name="compiler-warning-level-1-c4744"></a>Ostrzeżenie kompilatora (poziom 1) C4744

'var' ma inny typ w 'file1' i 'file2': 'type1' i 'type2'

Zmienna zewnętrzna, do których istnieją odwołania lub zdefiniowane w dwóch plikach, ma różne typy w tych plikach.  Aby rozwiązać problem, należy dokonać definicji typu takie same lub zmienić nazwę zmiennej w jednym z plików.

C4744 jest emitowany tylko wtedy, gdy pliki są kompilowane z /GL.  Aby uzyskać więcej informacji, zobacz [/GL (Optymalizacja całego programu)](../../build/reference/gl-whole-program-optimization.md).

> [!NOTE]
> C4744 zwykle występuje w plikach C (nie C++), ponieważ w języku C++ nazwa zmiennej jest ozdobiona informacjami o typie.  Gdy przykład (poniżej) jest kompilowany jako C++, otrzymasz błąd konsolidatora LNK2019.

## <a name="example"></a>Przykład

Ten przykład zawiera pierwszą definicję.

```c
// C4744.c
// compile with: /c /GL
int global;
```

## <a name="example"></a>Przykład

Poniższy przykład generuje C4744.

```c
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
