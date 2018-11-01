---
title: Błąd kompilatora C3866
ms.date: 11/04/2016
f1_keywords:
- C3866
helpviewer_keywords:
- C3866
ms.assetid: 685870af-2440-4cdf-a6cb-284a5b96ef9d
ms.openlocfilehash: 98014fec77ce47fa4c484645f401e615f1470e2f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50446296"
---
# <a name="compiler-error-c3866"></a>Błąd kompilatora C3866

wywołaniu funkcji brakuje listy argumentów

Wewnątrz funkcji niestatycznej składowej wywołanie destruktora lub finalizatora nie ma listy argumentów.

Poniższy przykład spowoduje wygenerowanie C3866:

```
// C3866.cpp
// compile with: /c
class C {
   ~C();
   void f() {
      this->~C;   // C3866
      this->~C();   // OK
   }
};
```