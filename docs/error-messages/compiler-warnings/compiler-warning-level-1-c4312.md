---
title: Kompilator ostrzeżenie (poziom 1) C4312
ms.date: 11/04/2016
f1_keywords:
- C4312
helpviewer_keywords:
- C4312
ms.assetid: 541906ed-4f62-4bcb-947f-cf9ae7411bcb
ms.openlocfilehash: 666df7904a7aac88983af40d31a67271beaa0b1f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50440238"
---
# <a name="compiler-warning-level-1-c4312"></a>Kompilator ostrzeżenie (poziom 1) C4312

'operacja' : konwersja z 'typ1' na 'typ2' o większym rozmiarze

To ostrzeżenie wykrywa Próba przypisania wartości 32-bitowego do typu wskaźnika 64-bitowego, na przykład rzutowanie z 32-bitowym `int` lub `long` na wskaźnik 64-bitowych.

Może to być niebezpieczna konwersja, nawet w przypadku wartości wskaźnika, które mieszczą się w 32-bitowy, gdy wystąpi rozszerzenia znaku. Jeśli ujemna liczba całkowita 32-bitowy jest przypisany do typu wskaźnika 64-bitowym, rozszerzenia znaku powoduje, że wartość wskaźnika odwołać się do adresu pamięci różni się od wartości liczby całkowitej.

To ostrzeżenie zostanie wyświetlone tylko w 64-bitowych kompilacji obiektów docelowych. Aby uzyskać więcej informacji, zobacz [zasady za pomocą wskaźników](/windows/desktop/WinProg64/rules-for-using-pointers).

Poniższy kod generuje C4312, gdy jest ona skompilowana dla celów 64-bitowych:

```
// C4312.cpp
// compile by using: cl /W1 /LD C4312.cpp
void* f(int i) {
   return (void*)i;   // C4312 for 64-bit targets
}

void* f2(__int64 i) {
   return (void*)i;   // OK
}
```