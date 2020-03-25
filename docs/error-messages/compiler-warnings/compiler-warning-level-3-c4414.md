---
title: Ostrzeżenie kompilatora (poziom 3) C4414
ms.date: 11/04/2016
f1_keywords:
- C4414
helpviewer_keywords:
- C4414
ms.assetid: bc81d3ad-55dc-4a6b-a6f2-ec0ef38347df
ms.openlocfilehash: 4625f6bdb4aa6fe86ca881a8e36e5673e55ccb87
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80185597"
---
# <a name="compiler-warning-level-3-c4414"></a>Ostrzeżenie kompilatora (poziom 3) C4414

"Function": Krótki przeskok do funkcji konwertowanej na blisko

Krótkie uskoki generują kompaktową instrukcję, która oddziałuje do adresu w ograniczonym zakresie od instrukcji. Instrukcja zawiera krótkie przesunięcie, które reprezentuje odległość między skokiem a adresem docelowym, definicję funkcji. Podczas łączenia funkcji można przenieść lub przyczynić się do optymalizacji w czasie konsolidacji, która powoduje, że funkcja jest przenoszona z zakresu dostępnego od krótkiego przesunięcia. Kompilator musi generować specjalny rekord dla skoku, który wymaga, aby instrukcja element JMP była niemal lub bliska. Kompilator wykonał konwersję.

Na przykład poniższy kod generuje C4414:

```cpp
// C4414.cpp
// compile with: /W3 /c
// processor: x86
int DoParityEven();
int DoParityOdd();
unsigned char global;
int __declspec(naked) DoParityEither()
{
   __asm
   {
      test global,0
      jpe SHORT DoParityEven  // C4414
      jmp SHORT DoParityOdd   // C4414
   }
}
```
