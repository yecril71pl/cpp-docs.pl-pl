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
ms.openlocfilehash: 6318e6d78f6c4c4bb6827a79d26bca028dfe3f3f
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87233746"
---
# <a name="__restrict"></a>__restrict

Podobnie jak **__declspec ( [ograniczanie](../cpp/restrict.md) )** , **`__restrict`** słowo kluczowe wskazuje, że symbol nie jest aliasem w bieżącym zakresie. **`__restrict`** Słowo kluczowe różni się od `__declspec ( restrict )` modyfikatora w następujący sposób:

- **`__restrict`** Słowo kluczowe jest prawidłowe tylko dla zmiennych i `__declspec ( restrict )` jest prawidłowe tylko w deklaracjach i definicjach funkcji.

- **`__restrict`** jest podobny do **`restrict`** od specyfikacji C99, ale **`__restrict`** może być używany w programach C++ lub C.

- Gdy **`__restrict`** jest używany, kompilator nie propaguje właściwości "No-alias" zmiennej. Oznacza to, że jeśli zmienna zostanie przypisana **`__restrict`** do **`__restrict`** niezmiennej, kompilator nadal zezwoli na aliasowanie zmiennej nie__restrictj. Różni się to od zachowania **`restrict`** słowa kluczowego ze specyfikacji C99.

Ogólnie rzecz biorąc, jeśli wpłynie to na zachowanie całej funkcji, lepiej jest użyć `__declspec ( restrict )` słowa kluczowego.

W celu zapewnienia zgodności z poprzednimi wersjami **_restrict** jest synonimem, **`__restrict`** Jeśli nie określono opcji kompilatora [/za \( disable Language Extensions)](../build/reference/za-ze-disable-language-extensions.md) .

W programie Visual Studio 2015 i nowszych **`__restrict`** można używać odwołań do języka C++.

> [!NOTE]
> W przypadku użycia na zmiennej, która ma także słowo kluczowe [volatile](../cpp/volatile-cpp.md) , **`volatile`** pierwszeństwo ma.

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
