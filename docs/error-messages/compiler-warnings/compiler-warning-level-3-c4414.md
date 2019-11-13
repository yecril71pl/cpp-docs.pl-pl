---
title: Ostrzeżenie kompilatora (poziom 3) C4414
ms.date: 11/04/2016
f1_keywords:
- C4414
helpviewer_keywords:
- C4414
ms.assetid: bc81d3ad-55dc-4a6b-a6f2-ec0ef38347df
ms.openlocfilehash: 43570cd43ca6e9d4f892dc577f615e9fa980e561
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/13/2019
ms.locfileid: "74051585"
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