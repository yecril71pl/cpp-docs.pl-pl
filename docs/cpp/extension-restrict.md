---
title: __restrict
ms.date: 10/10/2018
f1_keywords:
- __restrict_cpp
- __restrict
- _restrict
helpviewer_keywords:
- __restrict keyword [C++]
ms.assetid: 2d151b4d-f930-49df-bd16-d8757ec7fa83
ms.openlocfilehash: 76cdf9424e6eab33a3a92b3f98d9c2b0b04ff667
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50454551"
---
# <a name="restrict"></a>__restrict

Podobnie jak **__declspec ( [ograniczyć](../cpp/restrict.md) )** , modyfikator **element __restrict** słowo kluczowe wskazuje, że symbol nie jest aliasem w bieżącym zakresie. **Element __restrict** — słowo kluczowe różni się od `__declspec ( restrict )` modyfikator w następujący sposób:

- **Element __restrict** — słowo kluczowe jest prawidłowy tylko w zmiennych i `__declspec ( restrict )` jest prawidłowy tylko w deklaracji i definicji funkcji.

- **Element __restrict** jest podobny do **ograniczyć** ze specyfikacji C99, ale **element __restrict** mogą być używane w programach języka C++ lub C.

- Gdy **element __restrict** jest używany, kompilator nie będzie propagowany właściwość alias nie zmiennej. Oznacza to Jeśli przypiszesz **element __restrict** zmiennej do innej niż**element __restrict** zmiennej, kompilator będzie nadal zezwalają na innych niż-element __restrict zmienną aliasem. To różni się od zachowania **ograniczyć** słowo kluczowe z specyfikacją C99.

Ogólnie rzecz biorąc, jeśli mają wpływ na zachowanie całej funkcji, lepiej jest używać `__declspec ( restrict )` niż słowa kluczowego.

W celu zgodności z poprzednimi wersjami **_restrict** jest synonimem dla **element __restrict** chyba że — opcja kompilatora [/Za \(Wyłącz rozszerzenia językowe)](../build/reference/za-ze-disable-language-extensions.md) jest określona.

W programie Visual Studio 2015 i nowszych **element __restrict** mogą być używane na odwołań w języku C++.

> [!NOTE]
>  Gdy jest używana w zmiennej, która także ma [volatile](../cpp/volatile-cpp.md) — słowo kluczowe, **volatile** mają wyższy priorytet.

## <a name="example"></a>Przykład

```cpp
// __restrict_keyword.c
// compile with: /LD
// In the following function, declare a and b as disjoint arrays
// but do not have same assurance for c and d.
void sum2(int n, int * __restrict a, int * __restrict b,
          int * c, int * d) {
   int i;
   for (i = 0; i < n; i++) {
      a[i] = b[i] + c[i];
      c[i] = b[i] + d[i];
    }
}

// By marking union members as __restrict, tell compiler that
// only z.x or z.y will be accessed in any given scope.
union z {
   int * __restrict x;
   double * __restrict y;
};
```

## <a name="see-also"></a>Zobacz także

[Słowa kluczowe](../cpp/keywords-cpp.md)