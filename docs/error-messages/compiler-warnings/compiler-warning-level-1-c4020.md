---
title: Ostrzeżenie kompilatora (poziom 1) C4020
ms.date: 11/04/2016
f1_keywords:
- C4020
helpviewer_keywords:
- C4020
ms.assetid: 8c4cd6be-9371-4c8c-b0ff-a5ad367bbab0
ms.openlocfilehash: ccab8eaac42932491fc8b88cd28f2d3334b2e849
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/05/2019
ms.locfileid: "73626321"
---
# <a name="compiler-warning-level-1-c4020"></a>Ostrzeżenie kompilatora (poziom 1) C4020

"Function": zbyt wiele parametrów rzeczywistych

Liczba rzeczywistych parametrów w wywołaniu funkcji przekracza liczbę parametrów formalnych w prototypie lub definicji funkcji. Kompilator przekazuje dodatkowe parametry rzeczywiste zgodnie z konwencją wywoływania funkcji.

Poniższy przykład generuje C4020:

```c
// C4020.c
// compile with: /W1 /c
void f(int);
int main() {
   f(1,2);   // C4020
}
```

Możliwe rozwiązanie:

```c
// C4020b.c
// compile with: /c
void f(int);
int main() {
   f(1);
}
```