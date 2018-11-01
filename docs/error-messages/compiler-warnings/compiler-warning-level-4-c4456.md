---
title: Kompilator ostrzeżenie (poziom 4) C4456
ms.date: 11/04/2016
f1_keywords:
- C4456
helpviewer_keywords:
- C4456
ms.assetid: 5ab39fc1-0e19-461b-842b-4da80560b044
ms.openlocfilehash: 006628721598d838070412c895f64b9a8d3de4e9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50452588"
---
# <a name="compiler-warning-level-4-c4456"></a>Kompilator ostrzeżenie (poziom 4) C4456

> Deklaracja "*identyfikator*" powoduje ukrycie poprzedniej deklaracji lokalnej

Deklaracja *identyfikator* w zakresie lokalnym ukrywa deklarację poprzedniej deklaracji lokalnej o tej samej nazwie. To ostrzeżenie informuje o tym, który odwołuje się do *identyfikator* w zakresie lokalnym rozpoznać lokalnie zadeklarowanych wersji, a nie lokalny poprzedniej, która może być lub może nie być zgodne z zamiarami użytkownika. Aby rozwiązać ten problem, zalecane jest nadać nazwy zmiennych lokalnych, które nie wchodzą w konflikt z nazwami innych lokalnych.

## <a name="example"></a>Przykład

Poniższy przykład generuje C4456, ponieważ kontrolować pętli, zmienna `int x` i zmienną lokalną `double x` w `member_fn` takich samych nazwach. Aby rozwiązać ten problem, należy użyć innej nazwy dla zmiennych lokalnych.

```cpp
// C4456_hide.cpp
// compile with: cl /W4 /c C4456_hide.cpp

struct S {
    void member_fn(unsigned u) {
        double x = 0;
        for (int x = 0; x < 10; ++x) {  // C4456
            u += x; // uses local int x
        }
        x += u; // uses local double x
    }
} s;
```
