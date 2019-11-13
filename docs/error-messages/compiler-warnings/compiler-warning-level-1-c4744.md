---
title: Ostrzeżenie kompilatora (poziom 1) C4744
ms.date: 11/04/2016
f1_keywords:
- C4744
helpviewer_keywords:
- C4744
ms.assetid: f2a7d0b5-afd5-4926-abc3-cfbd367e3ff5
ms.openlocfilehash: f6954ae7966edf200249bb5d10f0dfb011bcef22
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/13/2019
ms.locfileid: "74051557"
---
# <a name="compiler-warning-level-1-c4744"></a>Ostrzeżenie kompilatora (poziom 1) C4744

element "var" ma inny typ w "plik1" i "plik2": "type1" i "type2"

Zmienna zewnętrzna, do której odwołuje się lub została zdefiniowana w dwóch plikach, ma różne typy w tych plikach.  Aby rozwiązać ten problem, wprowadź definicje typu tak samo lub Zmień nazwę zmiennej w jednym z plików.

C4744 jest emitowana tylko wtedy, gdy pliki są kompilowane przy użyciu/GL.  Aby uzyskać więcej informacji, zobacz [/GL (Optymalizacja całego programu)](../../build/reference/gl-whole-program-optimization.md).

> [!NOTE]
>  C4744 zazwyczaj występuje w plikach C ( C++nie), ponieważ w C++ nazwie zmiennej są zawarte informacje o typie.  Gdy próbka (poniżej) jest skompilowana jako C++, zostanie wyświetlony komunikat o błędzie konsolidatora LNK2019.

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