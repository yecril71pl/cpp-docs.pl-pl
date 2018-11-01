---
title: Błąd kompilatora C2197
ms.date: 11/04/2016
f1_keywords:
- C2197
helpviewer_keywords:
- C2197
ms.assetid: 6dd5a6ec-bc80-41b9-a4ac-46f80eaca42d
ms.openlocfilehash: 8999edcf37277e2e05a92a6601d60d34a675719c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50527403"
---
# <a name="compiler-error-c2197"></a>Błąd kompilatora C2197

'Funkcja': za dużo argumentów dla wywołania

Kompilator wykrył zbyt wiele parametrów dla wywołania funkcji lub deklaracji Niepoprawna funkcja.

Poniższy przykład spowoduje wygenerowanie C2197:

```
// C2197.c
// compile with: /Za /c
void func( int );
int main() {
   func( 1, 2 );   // C2197 two actual parameters
   func( 2 );   // OK
}
```