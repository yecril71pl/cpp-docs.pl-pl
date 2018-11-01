---
title: Błąd kompilatora C2362
ms.date: 11/04/2016
f1_keywords:
- C2362
helpviewer_keywords:
- C2362
ms.assetid: 7aafecbc-b3cf-45a6-9ec3-a17e3f222511
ms.openlocfilehash: 17656b2a48a3680a9269d3ca300fd4188eda6b84
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50661113"
---
# <a name="compiler-error-c2362"></a>Błąd kompilatora C2362

Inicjalizacja 'Identyfikator' jest pomijana przy "Przejdź do etykiety"

Podczas kompilowania za pomocą [/Za](../../build/reference/za-ze-disable-language-extensions.md), przeskakiwanie do etykiety zapobiega inicjowany przez identyfikator.

Nie można przeskoczyć poza deklaracją za pomocą inicjatora, chyba że deklaracja jest ujęty w bloku, który nie jest wprowadzone lub zmiennej został już zainicjowany.

Poniższy przykład spowoduje wygenerowanie C2326:

```
// C2362.cpp
// compile with: /Za
int main() {
   goto label1;
   int i = 1;      // C2362, initialization skipped
label1:;
}
```

Możliwe rozwiązanie:

```
// C2362b.cpp
// compile with: /Za
int main() {
   goto label1;
   {
      int j = 1;   // OK, this block is never entered
   }
label1:;
}
```