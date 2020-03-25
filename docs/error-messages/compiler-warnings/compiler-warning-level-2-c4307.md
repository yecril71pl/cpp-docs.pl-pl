---
title: Ostrzeżenie kompilatora (poziom 2) C4307
ms.date: 11/04/2016
f1_keywords:
- C4307
helpviewer_keywords:
- C4307
ms.assetid: 7cca11e9-be61-49e4-8b15-88b84f0cbf07
ms.openlocfilehash: f6e06acaf43708d6c0da6d67531b6c4b9f202971
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80161883"
---
# <a name="compiler-warning-level-2-c4307"></a>Ostrzeżenie kompilatora (poziom 2) C4307

"operator": przepełnienie stałej całkowitej

Operator jest używany w wyrażeniu, które powoduje stałe przepełnienie przyjmowanego miejsca. Może być konieczne użycie większego typu dla stałej. **Podpisana int** ma mniejszą wartość niż `unsigned int`, ponieważ **podpisana int** używa jednego bitu do reprezentowania znaku.

Poniższy przykład generuje C4307:

```cpp
// C4307.cpp
// compile with: /W2
int i = 2000000000 + 2000000000;   // C4307
int j = (unsigned)2000000000 + 2000000000;   // OK

int main()
{
}
```
