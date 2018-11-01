---
title: Błąd kompilatora C2233
ms.date: 11/04/2016
f1_keywords:
- C2233
helpviewer_keywords:
- C2233
ms.assetid: 236bdf0b-9607-4f26-a249-d8def0b1333c
ms.openlocfilehash: 7d96230f189a8f9371473d2da4df4e7be295ab03
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50499115"
---
# <a name="compiler-error-c2233"></a>Błąd kompilatora C2233

'Identyfikator': niedozwolone są tablice obiektów zawierające tablice o rozmiarze zerowym

Każdy obiekt w tablicy musi zawierać co najmniej jeden element.

Poniższy przykład spowoduje wygenerowanie C2233:

```
// C2233.cpp
// compile with: /c
class A {
   char somearray[1];
};

class B {
   char zeroarray[];
};

A array[100];   // OK
B array2[100];   // C2233
```