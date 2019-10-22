---
title: gslice_array — Klasa
ms.date: 11/04/2016
f1_keywords:
- valarray/std::gslice_array
helpviewer_keywords:
- gslice_array class
ms.assetid: ad1b4514-b14a-4baf-a293-d5a8e8674c75
ms.openlocfilehash: 68ce774128395e941ff80580a02c4ee28a74a4e4
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/21/2019
ms.locfileid: "72689599"
---
# <a name="gslice_array-class"></a>gslice_array — Klasa

Wewnętrzny, pomocniczy szablon klasy, który obsługuje ogólne obiekty wycinków, dostarczając operacje między tablicami podzestawu zdefiniowanymi przez ogólny wycinek elementu valarray.

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

Klasa opisuje obiekt, który przechowuje odwołanie do obiektu `va` klasy [valarray](../standard-library/valarray-class.md)  **\<Type >** oraz obiekt `gs` klasy [gslice](../standard-library/gslice-class.md) , który opisuje sekwencję elementów do wybrania z obiektu `valarray<Type>`.

Obiekt `gslice_array<Type>` można skonstruować tylko przez napisanie wyrażenia w postaci [VA&#91;GS&#93;](../standard-library/valarray-class.md#op_at). Funkcje członkowskie klasy gslice_array, zachowują się jak odpowiadające im sygnatury funkcji zdefiniowane dla `valarray<Type>`, z tą różnicą, że dotyczy tylko sekwencji wybranych elementów.

Szablon klasy jest tworzony pośrednio przez pewne operacje valarray i nie może być używany bezpośrednio w programie. Wewnętrzny szablon klasy pomocniczej jest używany przez Operator indeksu dolnego:

`gslice_array` **typ** \< >  `valarray` \< **Typ**>:: `operator[]` ( **constgslice &** ).

Obiekt `gslice_array<Type>` można skonstruować tylko przez napisanie wyrażenia `va[gsl]` formularza dla wycinka `gsl` `va` valarray. Funkcje członkowskie klasy gslice_array, zachowują się jak odpowiadające im sygnatury funkcji zdefiniowane dla `valarray<Type>`, z tą różnicą, że dotyczy tylko sekwencji wybranych elementów. Sekwencja kontrolowana przez gslice_array jest definiowana przez trzy parametry konstruktora wycinka, indeks pierwszego elementu w pierwszym wycinkze, liczbę elementów w każdym wycinku i odległość między elementami w każdym wycinku.

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
