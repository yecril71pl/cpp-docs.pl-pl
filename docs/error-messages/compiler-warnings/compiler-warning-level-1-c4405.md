---
title: Ostrzeżenie kompilatora (poziom 1) C4405
ms.date: 11/04/2016
f1_keywords:
- C4405
helpviewer_keywords:
- C4405
ms.assetid: 155c64d6-58ae-4455-b61f-ccd711c5da96
ms.openlocfilehash: 7ec06e80ac8f61802258a62594029b15a55ebe42
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80162572"
---
# <a name="compiler-warning-level-1-c4405"></a>Ostrzeżenie kompilatora (poziom 1) C4405

"Identyfikator": Identyfikator jest zarezerwowanym słowem

Słowo zarezerwowane dla zestawu wbudowanego jest używane jako nazwa zmiennej. Może to spowodować nieprzewidywalne wyniki. Aby usunąć to ostrzeżenie, należy unikać nazewnictwa zmiennych przy użyciu słów zarezerwowanych dla zestawu wbudowanego. Poniższy przykład generuje C4405:

```cpp
// C4405.cpp
// compile with: /W1
// processor: x86
void func1() {
   int mov = 0, i = 0;
   _asm {
      mov mov, 0;   // C4405
      // instead, try ..
      // mov i, 0;
   }
}

int main() {
}
```
