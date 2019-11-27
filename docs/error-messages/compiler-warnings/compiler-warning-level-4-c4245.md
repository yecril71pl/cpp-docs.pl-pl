---
title: Ostrzeżenie kompilatora (poziom 4) C4245
ms.date: 11/04/2016
f1_keywords:
- C4245
helpviewer_keywords:
- C4245
ms.assetid: 85083d53-9cc2-4d12-b58c-6dad28f15cbe
ms.openlocfilehash: 3d55226a368f81a9506b38fe9271da4332bd1f5b
ms.sourcegitcommit: 3ee06ec53153cf21910fc8cfef78a4f25f9633f3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/26/2019
ms.locfileid: "74541720"
---
# <a name="compiler-warning-level-4-c4245"></a>Ostrzeżenie kompilatora (poziom 4) C4245

"Conversion": konwersja z "type1" na "type2", niezgodność ze znakiem/bez znaku

Próbowano skonwertować podpisaną **stałą** , która ma wartość ujemną do `unsigned`.

Poniższy przykład generuje C4245:

```cpp
// C4245.cpp
// compile with: /W4 /c
const int i = -1;
unsigned int j = i; // C4245

const int k = 1;
unsigned int l = k; // okay

int m = -1;
unsigned int n = m; // okay

void Test(size_t i) {}

int main() {
   Test( -19 );   // C4245
}
```