---
title: Kompilator ostrzeżenie (poziom 1) C4717 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4717
dev_langs:
- C++
helpviewer_keywords:
- C4717
ms.assetid: 5ef3c6c7-8599-4714-a973-0f5b69cdab3c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e9bb7c37cd4a9da8844f30463c6e2d73fcc04609
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46022425"
---
# <a name="compiler-warning-level-1-c4717"></a>Kompilator ostrzeżenie (poziom 1) C4717

'Funkcja': cykliczne we wszystkich ścieżkach, funkcja spowoduje przepełnienie stosu środowiska uruchomieniowego

Każdej ścieżce za pomocą funkcji zawiera wywołanie do funkcji. Ponieważ nie istnieje żaden sposób, aby zakończyć działanie funkcji bez wywoływania pierwszy, sama cyklicznie, funkcja nigdy nie zostanie zakończona.

Poniższy przykład spowoduje wygenerowanie C4717:

```
// C4717.cpp
// compile with: /W1 /c
// C4717 expected
int func(int x) {
   if (x > 1)
      return func(x - 1); // recursive call
   else {
      int y = func(0) + 1; // recursive call
      return y;
   }
}

int main(){
   func(1);
}
```