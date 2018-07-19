---
title: gslice_array — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- valarray/std::gslice_array
dev_langs:
- C++
helpviewer_keywords:
- gslice_array class
ms.assetid: ad1b4514-b14a-4baf-a293-d5a8e8674c75
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ff44a91b4916092e319c7acc0520c49aeb9a5fa4
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/11/2018
ms.locfileid: "38953078"
---
# <a name="gslicearray-class"></a>gslice_array — Klasa

Klasy wewnętrzne, pomocnicze w ramach szablonu, która obsługuje obiekty wycinek ogólne, zapewniając operacji między macierzami podzbioru zdefiniowanych przez ogólne wycinek tablicy valarray.

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

Klasa opisująca obiekt, który zawiera odwołanie do obiektu `va` klasy [valarray](../standard-library/valarray-class.md)**\<typ >**, wraz z obiektem `gs` klasy [ gslice —](../standard-library/gslice-class.md) opisano sekwencji elementów, które można wybierać `valarray<Type>` obiektu.

Konstruowanie `gslice_array<Type>` obiektu Pisząc wyrażenie w formie [oceny luk w zabezpieczeniach&#91;gs&#93;](../standard-library/valarray-class.md#op_at). Funkcje Członkowskie gslice_array — klasa następnie zachowują się jak odpowiedniej sygnatury funkcji zdefiniowanych dla `valarray<Type>`, z tą różnicą, że dotyczy tylko kolejność wybranych elementów.

Klasa szablonu jest pośrednio tworzony przez niektóre operacje valarray i nie można użyć bezpośrednio w programie. Klasa wewnętrznego pomocnicze w ramach szablonu zamiast tego jest używany przez operator indeksu dolnego wycinek:

`gslice_array`\< **Typ** >  `valarray` \< **typu**>:: `operator[]` ( **constgslice &**).

Konstruowanie `gslice_array<Type>` obiektu Pisząc wyrażenie w formie `va[gsl]`, dla wycinka `gsl` z tablicy valarray `va`. Funkcje Członkowskie gslice_array — klasa następnie zachowują się jak odpowiedniej sygnatury funkcji zdefiniowanych dla `valarray<Type>`, z tą różnicą, że dotyczy tylko kolejność wybranych elementów. Na sekwencję kontrolowaną przez gslice_array — jest definiowany przez trzy parametry konstruktora wycinek, indeksu pierwszego elementu w pierwszym wycinku liczbę elementów w każdym wycinkiem i odległości między elementami w każdym wycinkiem.

W poniższym przykładzie:

```cpp
const size_t lv[] = {2, 3};
const size_t dv[] = {7, 2};
const valarray<size_t> len(lv, 2), str(dv, 2);

// va[gslice(3, len, str)] selects elements with
//   indices 3, 5, 7, 10, 12, 14
```

Indeksy muszą być prawidłowe procedury był prawidłowy.

## <a name="example"></a>Przykład

Zobacz przykład [gslice::gslice](../standard-library/gslice-class.md#gslice) przykładowy sposób deklarowania i użyj Tablica typu slice_array.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<valarray >

**Namespace:** standardowe

## <a name="see-also"></a>Zobacz także

[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
