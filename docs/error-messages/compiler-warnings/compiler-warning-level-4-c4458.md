---
title: Kompilator ostrzeżenie (poziom 4) C4458
ms.date: 11/04/2016
f1_keywords:
- C4458
helpviewer_keywords:
- C4458
ms.assetid: 7bdaa1b1-0caf-4d68-98c4-6bdd441c23fb
ms.openlocfilehash: 9e5eb8dc44968332abc097bfbd16b48e3240695c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50500987"
---
# <a name="compiler-warning-level-4-c4458"></a>Kompilator ostrzeżenie (poziom 4) C4458

> Deklaracja "*identyfikator*" powoduje ukrycie składowej klasy

Deklaracja *identyfikator* w zakresie lokalnym ukrywa deklarację o takiej samej nazwie *identyfikator* w zakresie klasy. To ostrzeżenie informuje o tym, który odwołuje się do *identyfikator* w tym zakresie rozpoznać lokalnie zadeklarowanych wersji, a nie wersji elementu członkowskiego klasy, która może być lub może nie być zgodne z zamiarami użytkownika. Aby rozwiązać ten problem, zalecane jest nadać nazwy zmiennych lokalnych, które nie wchodzą w konflikt z nazwą składowej klasy.

## <a name="example"></a>Przykład

Poniższy przykład generuje C4458, ponieważ parametr `x` i zmienną lokalną `y` w `member_fn` mają takie same nazwy elementów członkowskich danych klasy. Aby rozwiązać ten problem, należy używać różnych nazw parametrów i zmiennych lokalnych.

```cpp
// C4458_hide.cpp
// compile with: cl /W4 /c C4458_hide.cpp

struct S {
    int x;
    float y;
    void member_fn(long x) {   // C4458
        double y;  // C4458
        y = x;
        // To fix this issue, change the parameter name x
        // and local name y to something that does not
        // conflict with the data member names.
    }
} s;
```
