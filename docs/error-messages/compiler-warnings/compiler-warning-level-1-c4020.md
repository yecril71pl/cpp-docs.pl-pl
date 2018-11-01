---
title: Kompilator ostrzeżenie (poziom 1) C4020
ms.date: 11/04/2016
f1_keywords:
- C4020
helpviewer_keywords:
- C4020
ms.assetid: 8c4cd6be-9371-4c8c-b0ff-a5ad367bbab0
ms.openlocfilehash: 75148c210ddd2a611061d58c036d12c084f442cb
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50482033"
---
# <a name="compiler-warning-level-1-c4020"></a>Kompilator ostrzeżenie (poziom 1) C4020

'Funkcja': zbyt wiele parametrów rzeczywistych

Liczba rzeczywistych parametrów w wywołaniu funkcji przekracza liczbę parametrów formalnych w definicji lub prototypu funkcji. Kompilator przekazuje bardzo rzeczywistych parametrów, zgodnie z konwencji wywołania funkcji.

Poniższy przykład spowoduje wygenerowanie C4020:

```
// C4020.c
// compile with: /W1 /c
void f(int);
int main() {
   f(1,2);   // C4020
}
```

Możliwe rozwiązanie:

```
// C4020b.c
// compile with: /c
void f(int);
int main() {
   f(1);
}
```