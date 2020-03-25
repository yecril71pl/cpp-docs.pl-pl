---
title: Ostrzeżenie kompilatora (poziom 1) C4739
ms.date: 11/04/2016
f1_keywords:
- C4739
helpviewer_keywords:
- C4739
ms.assetid: 600873b3-7c85-4cd4-944e-cd8e01bfcbb0
ms.openlocfilehash: 9c68a9e0a2873de7e919fafbef68835f0970c03b
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80185701"
---
# <a name="compiler-warning-level-1-c4739"></a>Ostrzeżenie kompilatora (poziom 1) C4739

odwołanie do zmiennej "var" przekracza jego miejsce w magazynie

Wartość została przypisana do zmiennej, ale wartość jest większa niż rozmiar zmiennej. Pamięć zostanie zapisywana poza lokalizacją pamięci zmiennej i będzie możliwa utrata danych.

Aby rozwiązać ten problem, należy przypisać wartość tylko do zmiennej, której rozmiar może posłużyć wartości.

Poniższy przykład generuje C4739:

```cpp
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
