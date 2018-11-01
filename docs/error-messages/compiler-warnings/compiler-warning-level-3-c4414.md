---
title: Kompilator ostrzeżenie (poziom 3) C4414
ms.date: 11/04/2016
f1_keywords:
- C4414
helpviewer_keywords:
- C4414
ms.assetid: bc81d3ad-55dc-4a6b-a6f2-ec0ef38347df
ms.openlocfilehash: 0a9ceb332888e306b8cb3bcbe1832f773d02d63d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50629817"
---
# <a name="compiler-warning-level-3-c4414"></a>Kompilator ostrzeżenie (poziom 3) C4414

'Funkcja': krótki przeskok do funkcji konwertowanej do umieszczonej blisko

Krótkie przechodzi Generowanie compact instrukcji, co gałęzi na adres w ramach ograniczonego zakresu z instrukcji. Instrukcja zawiera krótki przesunięcie, reprezentującą odległość między skok, a także adres docelowy, definicji funkcji. Podczas łączenia funkcji może być przenoszony lub w czasie konsolidowania funkcje optymalizacji, które spowodować, że funkcja, która ma zostać przeniesiona poza zakresem dostępny od krótkich przesunięcia. Kompilator musi wygenerować to rekord specjalny dla szybkie, co wymaga instrukcji element jmp do NAJBLIŻSZEJ lub DALEKO. Kompilator dokonać konwersji.

Na przykład poniższy kod generuje C4414:

```
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