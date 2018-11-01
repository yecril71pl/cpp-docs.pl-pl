---
title: Kompilator ostrzeżenie (poziom 4) C4457
ms.date: 11/04/2016
f1_keywords:
- C4457
helpviewer_keywords:
- C4457
ms.assetid: 02fd149a-917d-4f67-97a6-eb714572271f
ms.openlocfilehash: 11307ddc3b13a9cd9b36f1ee927082104792b07f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50648360"
---
# <a name="compiler-warning-level-4-c4457"></a>Kompilator ostrzeżenie (poziom 4) C4457

> Deklaracja "*identyfikator*" powoduje ukrycie parametru funkcji

Deklaracja *identyfikator* w zakresie lokalnym ukrywa deklarację parametru funkcji takiej samej nazwie. To ostrzeżenie informuje o tym, który odwołuje się do *identyfikator* w zakresie lokalnym rozwiązać wersji lokalnie zadeklarowane, nie parametrze, co może spowodować lub może nie być zgodne z zamiarami użytkownika. Aby rozwiązać ten problem, zalecane jest nadać nazwy zmiennych lokalnych, które nie wchodzą w konflikt z nazwy parametru.

## <a name="example"></a>Przykład

Poniższy przykład generuje C4457, ponieważ parametr `x` i zmienną lokalną `x` w `member_fn` takich samych nazwach. Aby rozwiązać ten problem, należy używać różnych nazw parametrów i zmiennych lokalnych.

```cpp
// C4457_hide.cpp
// compile with: cl /W4 /c C4457_hide.cpp

struct S {
    void member_fn(unsigned x) {
        double a = 0;
        for (int x = 0; x < 10; ++x) {  // C4457
            a += x; // uses local x
        }
        a += x; // uses parameter x
    }
} s;
```
