---
title: Ostrzeżenie kompilatora (poziom 1) C4312
ms.date: 11/04/2016
f1_keywords:
- C4312
helpviewer_keywords:
- C4312
ms.assetid: 541906ed-4f62-4bcb-947f-cf9ae7411bcb
ms.openlocfilehash: 1983d7b89688568b8152372328216c2a814f7bc0
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69510082"
---
# <a name="compiler-warning-level-1-c4312"></a>Ostrzeżenie kompilatora (poziom 1) C4312

'operacja' : konwersja z 'typ1' na 'typ2' o większym rozmiarze

To ostrzeżenie wykrywa próbę przypisania wartości 32-bitowej do typu wskaźnika 64-bitowego, na przykład rzutowania 32 bitowego `int` lub `long` do wskaźnika 64-bitowego.

Może to być niebezpieczna konwersja nawet w przypadku wartości wskaźnika, które mieszczą się w 32 bitach, gdy występuje rozszerzenie podpisywania. Jeśli ujemna 32-bitowa liczba całkowita jest przypisana do typu wskaźnika 64-bitowego, rozszerzenie znaku powoduje, że wartość wskaźnika odwołuje się do adresu pamięci innego niż wartość całkowita.

To ostrzeżenie jest wydawane wyłącznie dla 64-bitowych kompilacji elementów docelowych. Aby uzyskać więcej informacji, zobacz [reguły dotyczące korzystania ze wskaźników](/windows/win32/WinProg64/rules-for-using-pointers).

Poniższy przykład kodu generuje C4312 podczas kompilowania dla elementów docelowych 64-bitowych:

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