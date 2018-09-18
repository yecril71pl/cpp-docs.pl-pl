---
title: Błąd kompilatora C2362 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2362
dev_langs:
- C++
helpviewer_keywords:
- C2362
ms.assetid: 7aafecbc-b3cf-45a6-9ec3-a17e3f222511
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f78b850f95614255fed372570742a0f88a9e30e2
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46035984"
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