---
title: Błąd kompilatora C2198
ms.date: 11/04/2016
f1_keywords:
- C2198
helpviewer_keywords:
- C2198
ms.assetid: 638a845c-9d7f-4115-a9aa-d72455605668
ms.openlocfilehash: a7fbc5dc6dc91dab5bfea3a81c8d5c045e485161
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50651753"
---
# <a name="compiler-error-c2198"></a>Błąd kompilatora C2198

'Funkcja': za mało argumentów dla wywołania

Kompilator odnaleziono za mało parametrów dla wywołania funkcji lub deklaracji Niepoprawna funkcja.

Poniższy przykład spowoduje wygenerowanie C2198:

```
// C2198.c
// compile with: /c
void func( int, int );
int main() {
   func( 1 );   // C2198 only one actual parameter
   func( 1, 1 );   // OK
}
```