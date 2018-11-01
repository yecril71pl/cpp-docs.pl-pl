---
title: Błąd kompilatora C3160
ms.date: 11/04/2016
f1_keywords:
- C3160
helpviewer_keywords:
- C3160
ms.assetid: a250c433-8adf-43b9-8dee-c3794e09b0a5
ms.openlocfilehash: 96fd97aa5021b7e1bc5226162f9c54ff4d6211b1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50649751"
---
# <a name="compiler-error-c3160"></a>Błąd kompilatora C3160

"wskaźnik": element członkowski danych zarządzanej lub klasa WinRT nie może mieć tego typu

Wskaźniki kolekcji wyrzucania elementów wewnętrznych mogą wskazywać na wnętrze zarządzanej lub klasa WinRT. Ponieważ są wolniejsze od wskaźniki całego obiektu i wymagają specjalnej obsługi przez moduł odśmiecania pamięci, nie można zadeklarować wewnętrznymi wskaźnikami zarządzanymi jako elementy członkowskie klasy.

Poniższy przykład spowoduje wygenerowanie C3160:

```
// C3160.cpp
// compile with: /clr
ref struct A {
   // cannot create interior pointers inside a class
   interior_ptr<int> pg;   // C3160
   int g;   // OK
   int* pg2;   // OK
};

int main() {
   interior_ptr<int> pg2;   // OK
}
```
