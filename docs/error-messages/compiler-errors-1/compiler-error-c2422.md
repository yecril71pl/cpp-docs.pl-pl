---
title: Błąd kompilatora C2422 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2422
dev_langs:
- C++
helpviewer_keywords:
- C2422
ms.assetid: ef0ec302-4028-4778-b134-0b8cea4bcad9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 17421f2d4a7823c0e2fbb34a54a7c562223c798c
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46047034"
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