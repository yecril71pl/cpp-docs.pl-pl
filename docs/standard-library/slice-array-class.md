---
title: slice_array — Klasa
ms.date: 11/04/2016
f1_keywords:
- valarray/std::slice_array
helpviewer_keywords:
- slice_array class
ms.assetid: a182d5f7-f35c-4e76-86f2-b5ac64ddc846
ms.openlocfilehash: cf33c5f627a88698c84947f9b803edaebccf5566
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68450400"
---
# <a name="slicearray-class"></a>slice_array — Klasa

Wewnętrzna, pomocnicza Klasa szablonu, która obsługuje obiekty plasterków, dostarczając operacje między tablicami podzestawu zdefiniowanymi przez wycinek elementu valarray.

## <a name="syntax"></a>Składnia

```cpp
template <class Type>
class slice_array : public slice {
public:
    typedef Type value_type;
    void operator=(const valarray<Type>& x) const;
    void operator=(const Type& x) const;
    void operator*=(const valarray<Type>& x) const;
    void operator/=(const valarray<Type>& x) const;
    void operator%=(const valarray<Type>& x) const;
    void operator+=(const valarray<Type>& x) const;
    void operator-=(const valarray<Type>& x) const;
    void operator^=(const valarray<Type>& x) const;
    void operator&=(const valarray<Type>& x) const;
    void operator|=(const valarray<Type>& x) const;
    void operator<<=(const valarray<Type>& x) const;
    void operator>>=(const valarray<Type>& x) const;
    // The rest is private or implementation defined
}
```

## <a name="remarks"></a>Uwagi

Klasa opisuje obiekt, który przechowuje odwołanie do obiektu klasy [valarray](../standard-library/valarray-class.md) **\<typu >** , wraz z obiektem wycinka klasy, który opisuje [](../standard-library/slice-class.md)sekwencję elementów do wybrania z **valarray\<Wpisz >** obiektu.

Klasa szablonu jest tworzona pośrednio przez pewne operacje valarray i nie może być używana bezpośrednio w programie. Wewnętrzna, pomocnicza Klasa szablonu, która jest używana przez Operator indeksu dolnego:

`slice_array`\<**Typ** >  **Typ:** : (`operator[]` ). `valarray` <  `slice`

`slice_array<Type>` Obiekt można skonstruować tylko przez napisanie wyrażenia w postaci [VA&#91;SL&#93;](../standard-library/valarray-class.md#op_at), dla wycinka `sl` valarray `va`. Funkcje składowe klasy slice_array, zachowują się jak odpowiadające im sygnatury `valarray<Type>`funkcji zdefiniowane dla, z tą różnicą, że dotyczy tylko sekwencji wybranych elementów. Sekwencja kontrolowana przez slice_array jest definiowana przez trzy parametry konstruktora wycinka, indeks pierwszego elementu w wycinkze, liczbę elementów i odległość między elementami. Slice_array wycięty z valarray `va` zadeklarowanych przez VA `slice`[(2, 5, 3)] wybiera elementy z indeksami 2, 5, 8, 11 i 14 z. `va` Indeksy muszą być prawidłowe, aby procedura była prawidłowa.

## <a name="example"></a>Przykład

Zapoznaj się z przykładem [wycinka:: Slice](../standard-library/slice-class.md#slice) , aby zapoznać się z przykładem sposobu deklarowania i używania slice_array.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<valarray >

**Przestrzeń nazw:** std

## <a name="see-also"></a>Zobacz także

[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
