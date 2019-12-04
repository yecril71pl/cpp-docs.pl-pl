---
title: Błąd kompilatora C2229
ms.date: 11/04/2016
f1_keywords:
- C2229
helpviewer_keywords:
- C2229
ms.assetid: 933c7cf2-a463-4e74-b0b4-59dedad987fb
ms.openlocfilehash: 2d974c4f0630a592daad956448bf21cea21efb7c
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74759272"
---
# <a name="compiler-error-c2229"></a>Błąd kompilatora C2229

Typ "identifier" ma niedozwoloną tablicę o rozmiarze zerowym

Składowa struktury lub pola bitowego zawiera tablicę o rozmiarze zerowym, która nie jest ostatnią składową.

Ponieważ można mieć tablicę o rozmiarze zerowym jako ostatni element członkowski struktury, należy określić jej rozmiar podczas przydzielania struktury.

Jeśli tablica o rozmiarze zerowym nie jest ostatnią składową struktury, kompilator nie może obliczyć przesunięcia dla pozostałych pól.

Poniższy przykład generuje C2229:

```cpp
// C2229.cpp
struct S {
   int a[0];  // C2229  zero-sized array
   int b[1];
};

struct S2 {
   int a;
   int b[0];
};

int main() {
   // allocate 7 elements for b field
   S2* s2 = (S2*)new int[sizeof(S2) + 7*sizeof(int)];
   s2->b[6] = 100;
}
```
