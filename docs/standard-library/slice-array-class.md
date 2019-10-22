---
title: slice_array — Klasa
ms.date: 11/04/2016
f1_keywords:
- valarray/std::slice_array
helpviewer_keywords:
- slice_array class
ms.assetid: a182d5f7-f35c-4e76-86f2-b5ac64ddc846
ms.openlocfilehash: 358348a57b823fcea82cd296967c83778819361d
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/21/2019
ms.locfileid: "72688961"
---
# <a name="slice_array-class"></a>slice_array — Klasa

Wewnętrzny, pomocniczy szablon klasy, który obsługuje obiekty wycinków, dostarczając operacje między tablicami podzestawu zdefiniowanymi przez wycinek elementu valarray.

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

Klasa opisuje obiekt, który przechowuje odwołanie do obiektu klasy [valarray](../standard-library/valarray-class.md)  **\<Type >** , wraz z obiektem [wycinka](../standard-library/slice-class.md)klasy, który opisuje sekwencję elementów do wybrania z **\<Type valarray >** obiekt.

Szablon klasy jest tworzony pośrednio przez pewne operacje valarray i nie może być używany bezpośrednio w programie. Wewnętrzny, pomocniczy szablon klasy, który jest używany przez Operator indeksu dolnego:

`slice_array` **typ** \< >  `valarray` < **typ**:: `operator[]` (`slice`).

Obiekt `slice_array<Type>` można skonstruować tylko przez napisanie wyrażenia w formie [VA&#91;SL&#93;](../standard-library/valarray-class.md#op_at)w przypadku wycinka `sl` `va` valarray. Funkcje członkowskie klasy slice_array, zachowują się jak odpowiadające im sygnatury funkcji zdefiniowane dla `valarray<Type>`, z tą różnicą, że dotyczy tylko sekwencji wybranych elementów. Sekwencja kontrolowana przez slice_array jest definiowana przez trzy parametry konstruktora wycinka, indeks pierwszego elementu w wycinkze, liczbę elementów i odległość między elementami. Slice_array wycięty z valarray `va` zadeklarowanych przez **VA**[`slice` (2, 5, 3)] wybiera elementy z indeksami 2, 5, 8, 11 i 14 z `va`. Indeksy muszą być prawidłowe, aby procedura była prawidłowa.

## <a name="example"></a>Przykład

Zapoznaj się z przykładem [wycinka:: Slice](../standard-library/slice-class.md#slice) , aby zapoznać się z przykładem sposobu deklarowania i używania slice_array.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<valarray >

**Przestrzeń nazw:** std

## <a name="see-also"></a>Zobacz także

[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
