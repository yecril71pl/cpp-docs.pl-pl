---
title: Błąd kompilatora C2450
ms.date: 11/04/2016
f1_keywords:
- C2450
helpviewer_keywords:
- C2450
ms.assetid: 929f1c06-8774-468b-be2a-f428757875a2
ms.openlocfilehash: 55c7f7ba8708e1475404a474f85df7dbe37fcec0
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87220356"
---
# <a name="compiler-error-c2450"></a>Błąd kompilatora C2450

wyrażenie Switch typu "Type" jest niedozwolone

**`switch`** Wynikiem wyrażenia jest nieprawidłowy typ. Należy oszacować do typu Integer lub typu klasy z niejednoznaczną konwersją na typ Integer. Jeśli zostanie obliczony do typu zdefiniowanego przez użytkownika, należy podać operator konwersji.

Poniższy przykład generuje C2450:

```cpp
// C2450.cpp
class X {
public:
   int i;
} x;

class Y {
public:
   int i;
   operator int() { return i; }   // conversion operator
} y;

int main() {
   int j = 1;
   switch ( x ) {   // C2450, x is not type int
   // try the following line instead
   // switch ( y ) {
      default:  ;
   }
}
```
