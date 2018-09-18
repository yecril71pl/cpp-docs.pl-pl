---
title: Kompilator ostrzeżenie (poziom 1) C4312 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4312
dev_langs:
- C++
helpviewer_keywords:
- C4312
ms.assetid: 541906ed-4f62-4bcb-947f-cf9ae7411bcb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3b6b6032ac22233c1662c6a7cc94d5ade7ae3a98
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46095355"
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