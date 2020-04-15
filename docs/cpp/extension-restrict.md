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
ms.openlocfilehash: 27ac76251456d9a0bf5908ad6d1fc2bee7534e9f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81360816"
---
# <a name="__restrict"></a>__restrict

Podobnie jak **modyfikator __declspec ( [restrict),](../cpp/restrict.md) ** **__restrict** słowo kluczowe wskazuje, że symbol nie jest aliasowany w bieżącym zakresie. __restrict **__restrict** słowo kluczowe różni się `__declspec ( restrict )` od modyfikatora w następujący sposób:

- **__restrict** słowo kluczowe jest prawidłowe tylko dla `__declspec ( restrict )` zmiennych i jest prawidłowe tylko w deklaracjach funkcji i definicjach.

- **__restrict** jest podobny do **ograniczenia** ze specyfikacji C99, ale **__restrict** może być używany w programach C++ lub C.

- Gdy jest używany **__restrict,** kompilator nie będzie propagować no-alias właściwości zmiennej. Oznacza to, że jeśli zostanie przypisana zmienna **__restrict** do zmiennej **__restrict,** kompilator nadal będzie zezwalał na aliasowanie zmiennej __restrict. To różni się od zachowania słowa kluczowego **ograniczyć** ze specyfikacji C99.

Ogólnie rzecz biorąc, jeśli wpływasz na zachowanie całej `__declspec ( restrict )` funkcji, lepiej jest użyć niż słowa kluczowego.

W przypadku zgodności z poprzednimi wersjami **_restrict** jest synonimem **__restrict** chyba że określono opcję kompilatora [/Za \(Wyłącz rozszerzenia języka).](../build/reference/za-ze-disable-language-extensions.md)

W programie Visual Studio 2015 i nowszych **__restrict** można używać w odwołaniach do języka C++.

> [!NOTE]
> Gdy jest używana w zmiennej, która ma również [volatile](../cpp/volatile-cpp.md) słowa kluczowego, **volatile** będzie pierwszeństwo.

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

## <a name="see-also"></a>Zobacz też

[Słowa kluczowe](../cpp/keywords-cpp.md)
