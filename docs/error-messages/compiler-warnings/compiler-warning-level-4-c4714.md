---
title: Kompilator ostrzeżenie (poziom 4) C4714 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4714
dev_langs:
- C++
helpviewer_keywords:
- C4714
ms.assetid: 22c7fd0c-899d-4e9b-95f3-725b2c49fb46
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ecb9ecb1c73373ae96c92c911988a512e2173cec
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46136104"
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