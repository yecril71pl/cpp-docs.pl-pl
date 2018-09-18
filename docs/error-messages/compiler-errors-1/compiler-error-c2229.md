---
title: Błąd kompilatora C2229 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2229
dev_langs:
- C++
helpviewer_keywords:
- C2229
ms.assetid: 933c7cf2-a463-4e74-b0b4-59dedad987fb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b235b5fae84ba605ecec5419f9334ccfa0a4be6e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46035594"
---
# <a name="compiler-error-c2229"></a>Błąd kompilatora C2229

Typ 'Identyfikator' ma niedozwolony zerowy rozmiar tablicy

Element członkowski pola struktury lub bitowego zawiera zerowy rozmiar tablicy, który nie jest ostatni element członkowski.

Ponieważ może mieć zero wielkości tablicy ostatni element członkowski struktury, należy określić jego rozmiar podczas alokowania struktury.

Jeśli tablicy o rozmiarze zero nie jest ostatniego członka struktury, kompilator nie może obliczyć przesunięcie dla pozostałych pól.

Poniższy przykład spowoduje wygenerowanie C2229:

```
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