---
title: tuple_size — klasa; | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- tuple_size
- std::tuple_size
- utility/std::tuple_size
dev_langs:
- C++
helpviewer_keywords:
- std::tuple_size
ms.assetid: 73852fc5-eb68-41f1-8379-465cedc2314a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0c03c47502fdd9309b3d6553c3f46f9685d4eaa9
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/11/2018
ms.locfileid: "38958269"
---
# <a name="tuplesize-class"></a>tuple_size — klasa;

Liczba elementów raportów, `tuple` zawiera.

## <a name="syntax"></a>Składnia

```cpp
// TEMPLATE STRUCT tuple_size
template <class Tuple>
   struct tuple_size;

// number of elements in array
template <class Elem, size_t Size>
   struct tuple_size<array<Elem, Size>>
      : integral_constant<size_t, Size>;

// size of pair
template <class T1, class T2>
   struct tuple_size<pair<T1, T2>>
      : integral_constant<size_t, 2>

// size of tuple
template <class... Types>
   struct tuple_size<tuple<Types...>>
      : integral_constant<size_t, sizeof...(Types)>;

// size of const tuple
template <class Tuple>
   struct tuple_size<const Tuple>;

// size of volatile tuple
template <class Tuple>
   struct tuple_size<volatile Tuple>;

// size of const volatile tuple
template <class Tuple>
   struct tuple_size<const volatile Tuple>;
```

### <a name="parameters"></a>Parametry

*Krotki*  
Typ spójnej kolekcji.

*Elem*  
Typ elementów tablicy.

*Rozmiar*  
Rozmiar tablicy.

*T1*  
Typ pierwszego elementu członkowskiego pary.

*T2*  
Typ drugiego elementu członkowskiego pary.

*Typy*  
Typy elementów krotki.

## <a name="remarks"></a>Uwagi

Klasa szablonu ma składową `value` oznacza to wyrażenie stałej całkowitej którego wartość jest w zakresie typu spoiny *krotki*.

Specjalizacja szablonu dla tablic ma składową `value` oznacza to wyrażenie stałej całkowitej o wartości *rozmiar*, czyli rozmiar tablicy.

Specjalizacja szablonu dla pary ma składową `value` oznacza to wyrażenie stałej całkowitej którego wartość jest równa 2.

## <a name="example"></a>Przykład

```cpp
#include <tuple>
#include <iostream>

using namespace std;

typedef tuple<int, double, int, double> MyTuple;
int main()
{
    MyTuple c0(0, 1.5, 2, 3.7);

    // display contents " 0 1 2 3"
    cout << " " << get<0>(c0);
    cout << " " << get<1>(c0);
    cout << " " << get<2>(c0);
    cout << " " << get<3>(c0) << endl;

    // display size " 4"
    cout << " " << tuple_size<MyTuple>::value << endl;
}
```

```Output
 0 1.5 2 3.7
```

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<krotki > **nagłówka:** \<tablicy > (dla specjalizacji tablicy) **nagłówka:** \<Narzędzia > (dla specjalizacji pary)

**Namespace:** standardowe

## <a name="see-also"></a>Zobacz także

[\<tuple>](../standard-library/tuple.md)<br/>
[krotki](../standard-library/tuple-class.md)<br/>
[tuple_element — klasa](../standard-library/tuple-element-class-tuple.md)<br/>
