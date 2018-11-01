---
title: Kompilator ostrzeżenie (poziom 1) C4739
ms.date: 11/04/2016
f1_keywords:
- C4739
helpviewer_keywords:
- C4739
ms.assetid: 600873b3-7c85-4cd4-944e-cd8e01bfcbb0
ms.openlocfilehash: 4c48ad9349361324c18ec790c51d1095cce104e2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50622095"
---
# <a name="compiler-warning-level-1-c4739"></a>Kompilator ostrzeżenie (poziom 1) C4739

Odwołanie do zmiennej "var" przekracza jego miejsce do magazynowania

Wartość została przypisana do zmiennej, ale wartość jest większa niż rozmiar zmiennej. Pamięć zostanie zapisany poza zmienną lokalizacji pamięci, a możliwa jest utrata danych.

Aby rozwiązać tego ostrzeżenia, tylko przypisać wartości do zmiennej, na których może pomieścić wartość.

Poniższy przykład spowoduje wygenerowanie C4739:

```
// C4739.cpp
// compile with: /RTCs /Zi /W1 /c
char *pc;
int main() {
   char c;
   *(int *)&c = 1;   // C4739

   // OK
   *(char *)&c = 1;
}
```