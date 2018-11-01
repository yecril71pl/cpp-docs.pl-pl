---
title: Kompilator ostrzeżenie (poziom 4) C4714
ms.date: 11/04/2016
f1_keywords:
- C4714
helpviewer_keywords:
- C4714
ms.assetid: 22c7fd0c-899d-4e9b-95f3-725b2c49fb46
ms.openlocfilehash: ed94e5b716a697ec96d7fecac75433823c9a67e9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50553858"
---
# <a name="compiler-warning-level-4-c4714"></a>Kompilator ostrzeżenie (poziom 4) C4714

funkcji "function" oznaczona jako __forceinline nie jest śródwierszowa

Daną funkcję został wybrany dla wbudowane rozwijanie, ale kompilator nie wykonał wbudowanie.

Mimo że `__forceinline` silniejsze wskazuje kompilatora niż `__inline`, wbudowanie jest nadal wykonywane według uznania kompilatora, ale nie Algorytm heurystyczny służą do określania korzyści związane z wbudowanie tej funkcji.

W niektórych przypadkach kompilator będzie niewyrównane określonej funkcji mechanicznych powodów. Na przykład kompilator będzie niewyrównane:

- Funkcja, przypadku mogłyby spowodować mieszanie SEH i EH w języku C++.

- Niektóre funkcje z kopią skonstruowane obiekty przekazywane przez wartość, gdy - GX/EHs/EHa znajduje się na.

- Funkcji zwracających odwracalnych obiektów według wartości, gdy - GX/EHs/EHa znajduje się na.

- Funkcje w zestawie wbudowanym podczas kompilowania kodu bez - Og/Ox/O1/O2.

- Funkcje o zmiennej liczbie argumentów.

- Funkcja z **spróbuj** — instrukcja (C++ obsługę wyjątków).

Poniższy przykład spowoduje wygenerowanie C4714:

```
// C4714.cpp
// compile with: /Ob1 /GX /W4
__forceinline void func1()
{
   try
   {
   }
   catch (...)
   {
   }
}

void func2()
{
   func1();   // C4714
}

int main()
{
}
```