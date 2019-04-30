---
title: Błąd kompilatora C2422
ms.date: 11/04/2016
f1_keywords:
- C2422
helpviewer_keywords:
- C2422
ms.assetid: ef0ec302-4028-4778-b134-0b8cea4bcad9
ms.openlocfilehash: 524eeadb6cf066d3eba3a7e88c45a9e2b993c0ae
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62402895"
---
# <a name="compiler-error-c2422"></a>Błąd kompilatora C2422

niedozwolone przesłonięcie segmentu w "operandu"

Wbudowany kod asemblera niepoprawnie użyto operatora przesłonięcie segmentu (dwukropek) dla argumentu operacji.  Możliwe przyczyny:

- Zarejestruj poprzedzających operator nie jest rejestru segmentu.

- Zarejestruj poprzedzających operator nie jest tylko rejestru segmentu w argumencie operacji.

- Operator przesłonięcie segmentu pojawia się w obrębie operatora pośredniego (nawiasy kwadratowe).

- Wyrażenie po operatorze przesłonięcie segmentu nie jest bezpośredni argument lub argument pamięci.

Poniższy przykład spowoduje wygenerowanie C2422:

```
// C2422.cpp
// processor: x86
int main() {
   _asm {
      mov AX, [BX:ES]   // C2422
      mov AX, ES   // OK
   }
}
```