---
title: Błąd kompilatora C2422
ms.date: 11/04/2016
f1_keywords:
- C2422
helpviewer_keywords:
- C2422
ms.assetid: ef0ec302-4028-4778-b134-0b8cea4bcad9
ms.openlocfilehash: 39f779ee846cf4f328f9c7af59ae394d97d7a3ca
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74744735"
---
# <a name="compiler-error-c2422"></a>Błąd kompilatora C2422

niedozwolone przesłonięcie segmentu w "operandzie"

Wbudowany kod asemblera niepoprawnie używa operatora przesłaniania segmentu (dwukropek) dla operandu.  Możliwe przyczyny:

- Rejestr poprzedzający operator nie jest rejestrem segmentów.

- Rejestr poprzedzający operator nie jest jedynym rejestrem segmentów w argumencie operacji.

- Operator przesłonięcia segmentu pojawia się w operatorze pośrednim (nawiasy).

- Wyrażenie następujące po przesłonięciu segmentu nie jest bezpośrednim operandem lub operandem pamięci.

Poniższy przykład generuje C2422:

```cpp
// C2422.cpp
// processor: x86
int main() {
   _asm {
      mov AX, [BX:ES]   // C2422
      mov AX, ES   // OK
   }
}
```
