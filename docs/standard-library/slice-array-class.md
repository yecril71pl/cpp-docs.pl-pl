---
title: slice_array — Klasa
ms.date: 11/04/2016
f1_keywords:
- valarray/std::slice_array
helpviewer_keywords:
- slice_array class
ms.assetid: a182d5f7-f35c-4e76-86f2-b5ac64ddc846
ms.openlocfilehash: 9577447b2201c1c9e53192b99abad1979f45d15f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50467218"
---
# <a name="slicearray-class"></a>slice_array — Klasa

Klasy wewnętrzne, pomocnicze w ramach szablonu, która obsługuje obiekty wycinek, zapewniając operacji między macierzami z podzbioru zdefiniowanych przez wycinek tablicy valarray.

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

Klasa opisująca obiekt, który zawiera odwołanie do obiektu klasy [valarray](../standard-library/valarray-class.md)**\<typ >**, oraz obiekt klasy [wycinek](../standard-library/slice-class.md), który Zawiera opis sekwencji elementów, które można wybierać **valarray\<typ >** obiektu.

Klasa szablonu jest pośrednio tworzony przez niektóre operacje valarray i nie można użyć bezpośrednio w programie. Klasa szablonu pomocnicze, wewnętrzne, która jest używana przez operatora indeksu dolnego wycinek:

`slice_array`\< **Typ**> `valarray`< **typu**:: `operator[]` ( `slice`).

Konstruowanie `slice_array<Type>` obiektu Pisząc wyrażenie w formie [oceny luk w zabezpieczeniach&#91;sl&#93;](../standard-library/valarray-class.md#op_at), dla wycinka `sl` z tablicy valarray `va`. Funkcje Członkowskie slice_array — klasa następnie zachowują się jak odpowiedniej sygnatury funkcji zdefiniowanych dla `valarray<Type>`, z tą różnicą, że dotyczy tylko kolejność wybranych elementów. Na sekwencję kontrolowaną przez slice_array — jest definiowany przez trzy parametry konstruktora wycinek, indeksu pierwszego elementu w wycinek, liczbę elementów i odległości między elementami. Tablica typu slice_array obcięty z tablicy valarray `va` zdeklarowane **oceny luk w zabezpieczeniach**[ `slice`(2, 5, 3)] wybiera elementy z indeksów, 2, 5, 8, 11 i 14 z `va`. Indeksy muszą być prawidłowe procedury był prawidłowy.

## <a name="example"></a>Przykład

Zobacz przykład [slice::slice](../standard-library/slice-class.md#slice) przykładowy sposób deklarowania i użyj Tablica typu slice_array.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<valarray >

**Namespace:** standardowe

## <a name="see-also"></a>Zobacz także

[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
