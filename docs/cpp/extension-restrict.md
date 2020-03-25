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
ms.openlocfilehash: cb340554bc20516175400c4d14a5d0dba934a313
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80188964"
---
# <a name="__restrict"></a>__restrict

Podobnie jak **__declspec ( [ograniczanie](../cpp/restrict.md) )** modyfikator, słowo kluczowe **__restrict** wskazuje, że symbol nie jest aliasem w bieżącym zakresie. Słowo kluczowe **__restrict** różni się od modyfikatora `__declspec ( restrict )` w następujący sposób:

- Słowo kluczowe **__restrict** jest prawidłowe tylko w przypadku zmiennych, a `__declspec ( restrict )` jest prawidłowy tylko w deklaracjach i definicjach funkcji.

- **__restrict** jest podobna do **ograniczenia** z specyfikacji C99, ale **__restrict** może być używana w programach C++ lub w języku C.

- Gdy **__restrict** jest używany, kompilator nie będzie propagować właściwości No-alias zmiennej. Oznacza to, że Jeśli przypiszesz zmienną **__restrict** do zmiennej nie **__restrict** , kompilator nadal zezwoli na aliasowanie zmiennej nie__restrict. Różni się to od zachowania słowa kluczowego **ograniczenia** ze specyfikacji C99.

Ogólnie rzecz biorąc, jeśli wpłynie to na zachowanie całej funkcji, lepiej jest używać `__declspec ( restrict )` niż słowo kluczowe.

W celu zapewnienia zgodności z poprzednimi wersjami **_restrict** jest synonimem dla **__restrict** , chyba że opcja kompilatora [/za \(Wyłącz rozszerzenia językowe)](../build/reference/za-ze-disable-language-extensions.md) .

W programie Visual Studio 2015 i nowszych **__restrict** mogą być używane na C++ odwołaniach.

> [!NOTE]
>  W przypadku użycia na **zmiennej, która** ma także słowo kluczowe [volatile](../cpp/volatile-cpp.md) , będzie miało pierwszeństwo.

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
