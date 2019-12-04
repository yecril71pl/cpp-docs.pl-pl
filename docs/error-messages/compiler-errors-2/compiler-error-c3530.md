---
title: Błąd kompilatora C3530
ms.date: 11/04/2016
f1_keywords:
- C3530
helpviewer_keywords:
- C3530
ms.assetid: 21be81ce-b699-4c74-81bc-80a0c34d2d5a
ms.openlocfilehash: 3766eaa83457ba6cffaf8b1599983a065772911c
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74750146"
---
# <a name="compiler-error-c3530"></a>Błąd kompilatora C3530

nie można łączyć instrukcji "Auto" z jakimkolwiek innym specyfikatorem typu

Specyfikator typu jest używany ze słowem kluczowym `auto`.

### <a name="to-correct-this-error"></a>Aby poprawić ten błąd

1. Nie używaj specyfikatora typu w deklaracji zmiennej, która używa słowa kluczowego `auto`.

## <a name="example"></a>Przykład

Poniższy przykład daje C3530, ponieważ zmienna `x` jest zadeklarowana zarówno ze słowem kluczowym `auto`, jak i typem `int`, i ponieważ przykład jest kompilowany z **/Zc:** Auto.

```cpp
// C3530.cpp
// Compile with /Zc:auto
int main()
{
   auto int x;   // C3530
   return 0;
}
```

## <a name="see-also"></a>Zobacz także

[Auto, słowo kluczowe](../../cpp/auto-keyword.md)
