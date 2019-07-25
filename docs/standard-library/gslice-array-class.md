---
title: gslice_array — Klasa
ms.date: 11/04/2016
f1_keywords:
- valarray/std::gslice_array
helpviewer_keywords:
- gslice_array class
ms.assetid: ad1b4514-b14a-4baf-a293-d5a8e8674c75
ms.openlocfilehash: 37c54d09fdfe920c832c4baa7984fee4e090d04a
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68448921"
---
# <a name="gslicearray-class"></a>gslice_array — Klasa

Wewnętrzna, pomocnicza Klasa szablonu, która obsługuje ogólne obiekty wycinków, dostarczając operacje między tablicami podzestawu zdefiniowanymi przez ogólny wycinek elementu valarray.

## <a name="syntax"></a>Składnia

```cpp
template <class Type>
class gslice_array : public gsplice {
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

Klasa opisuje obiekt `va` , który przechowuje odwołanie do obiektu klasy [valarray](../standard-library/valarray-class.md) **\<typu >** , wraz z obiektem `gs` klasy [gslice](../standard-library/gslice-class.md) , który opisuje sekwencję elementów do wyboru `valarray<Type>` obiekt.

`gslice_array<Type>` Obiekt można skonstruować tylko przez napisanie wyrażenia w postaci [VA&#91;GS&#93;](../standard-library/valarray-class.md#op_at). Funkcje składowe klasy gslice_array, zachowują się jak odpowiadające im sygnatury `valarray<Type>`funkcji zdefiniowane dla, z tą różnicą, że dotyczy tylko sekwencji wybranych elementów.

Klasa szablonu jest tworzona pośrednio przez pewne operacje valarray i nie może być używana bezpośrednio w programie. Wewnętrzna Klasa szablonu pomocniczego jest używana przez Operator indeksu dolnego:

`gslice_array`\<**Typ** >  **Wpisz >** : :`operator[]` ( **constgslice &** ). `valarray` \<

`gslice_array<Type>` Obiekt można skonstruować tylko przez napisanie wyrażenia w postaci `va[gsl]`dla wycinka `gsl` valarray `va`. Funkcje składowe klasy gslice_array, zachowują się jak odpowiadające im sygnatury `valarray<Type>`funkcji zdefiniowane dla, z tą różnicą, że dotyczy tylko sekwencji wybranych elementów. Sekwencja kontrolowana przez gslice_array jest definiowana przez trzy parametry konstruktora wycinka, indeks pierwszego elementu w pierwszym wycinkze, liczbę elementów w każdym wycinku i odległość między elementami w każdym wycinku.

W poniższym przykładzie:

```cpp
const size_t lv[] = {2, 3};
const size_t dv[] = {7, 2};
const valarray<size_t> len(lv, 2), str(dv, 2);

// va[gslice(3, len, str)] selects elements with
//   indices 3, 5, 7, 10, 12, 14
```

Indeksy muszą być prawidłowe, aby procedura była prawidłowa.

## <a name="example"></a>Przykład

Zobacz przykład dla [gslice:: gslice](../standard-library/gslice-class.md#gslice) , aby zapoznać się z przykładem sposobu deklarowania i używania slice_array.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<valarray >

**Przestrzeń nazw:** std

## <a name="see-also"></a>Zobacz także

[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
