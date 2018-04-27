---
title: tuple_element — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- utility/std::tuple_element
dev_langs:
- C++
helpviewer_keywords:
- std::tuple_element
ms.assetid: 4c51a6c1-ce81-462f-8c6c-291d69f2b77c
caps.latest.revision: 23
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 08a7ab97d397022f86a390622803c38752f78808
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="tupleelement-class"></a>tuple_element — Klasa

Opakowuje `tuple` elementu. Zawijaj specjalizacje `array` elementów i `pair` elementy.

## <a name="syntax"></a>Składnia

```cpp
// CLASS tuple_element (find element by index)
template <size_t Index, class Tuple>
   struct tuple_element;

// tuple_element for const
template <size_t Index, class Tuple>
   struct tuple_element<Index, const Tuple>;

// tuple_element for volatile
template <size_t Index, class Tuple>
   struct tuple_element<Index, volatile Tuple>;

// tuple_element for const volatile
template <size_t Index, class Tuple>
   struct tuple_element<Index, const volatile Tuple>;

// Helper typedef
template <size_t Index, class Tuple>
   using tuple_element_t = typename tuple_element<Index, Tuple>::type;

// Specialization for arrays
template <size_t Index, class Elem, size_t Size>
   struct tuple_element<Index, array<Elem, Size>>;

// Specializations for pairs
// struct to determine type of element 0 in pair
template <class T1, class T2>
   struct tuple_element<0, pair<T1, T2>>;

// struct to determine type of element 1 in pair
template <class T1, class T2>
   struct tuple_element<1, pair<T1, T2>>;
```

### <a name="parameters"></a>Parametry

*Indeks* indeks elementu wyznaczonych.

*Tuple* typ spójnej kolekcji.

*Element* typ elementu tablicy.

*Rozmiar* rozmiar tablicy.

*T1* typ pierwszego elementu w parze.

*T2* typ drugiego elementu w parze.

## <a name="remarks"></a>Uwagi

Klasy szablonów `tuple_element` zagnieżdżony element typedef ma `type` oznacza to synonim dla typu w indeksie `Index` typu krotki `Tuple`.

Typedef `tuple_element_t` jest wygodne alias dla `tuple_element<Index, Tuple>::type`.

Specjalizacji klasy szablonów dla tablic zapewnia interfejs do `array` jako krotki liczącej `Size` elementów, z których każda ma tego samego typu. Zagnieżdżony element typedef ma każdej specjalizacji `type` oznacza to synonim dla typu `Index` elementu `array`, z dowolnego kwalifikacji const-volatile zachowane.

Specjalizacji szablonu dla `pair` typy każdego zapewniają typedef pojedynczy element członkowski, `type`, który jest synonimem typ elementu w określonej pozycji w parze z dowolnego kwalifikacji const i/lub volatile zachowane. Typedef `tuple_element_t` jest wygodne alias dla `tuple_element<N, pair<T1, T2>>::type`.

Użyj [get — funkcja &lt;narzędzie&gt; ](../standard-library/utility-functions.md#get) do zwrócenia elementu w określonej pozycji lub określonego typu.

## <a name="example"></a>Przykład

```cpp
#include <tuple>
#include <string>
#include <iostream>

using namespace std;
typedef tuple<int, double, string> MyTuple;

int main() {
    MyTuple c0{ 0, 1.5, "Tail" };

    tuple_element_t<0, MyTuple> val = get<0>(c0); //get by index
    tuple_element_t<1, MyTuple> val2 = get<1>(c0);
    tuple_element_t<2, MyTuple> val3 = get<string>(c0); // get by type

    cout << val << " " << val2 << " " << val3 << endl;
}
```

```Output
0 1.5 Tail
```

## <a name="example"></a>Przykład

```cpp
#include <array>
#include <iostream>

using namespace std;
typedef array<int, 4> MyArray;

int main()
{
    MyArray c0 { 0, 1, 2, 3 };

    for (const auto& e : c0)
    {
        cout << " " << e;
    }
    cout << endl;

    // display first element " 0"
    tuple_element<0, MyArray>::type val = c0.front();
    cout << " " << val << endl;
}
```

```Output
 0 1 2 3
 0
```

## <a name="example"></a>Przykład

```cpp
#include <utility>
#include <iostream>

using namespace std;

typedef pair<int, double> MyPair;
int main() {
    MyPair c0(0, 1.333);

    // display contents " 0 1"
    cout << " " << get<0>(c0);
    cout << " " << get<1>(c0) << endl;

    // display first element " 0" by index
    tuple_element<0, MyPair>::type val = get<0>(c0);
    cout << " " << val;

    // display second element by type
    tuple_element<1, MyPair>::type val2 = get<double>(c0);
    cout << " " << val2 << endl;
}
```

```Output
 0 1.333
 0 1.333
```

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<krotki > **nagłówka:** \<tablicy > (dla specjalizacji tablicy) **nagłówka:** \<narzędzie > (dla specjalizacji pary)  **Namespace:** Standard

## <a name="see-also"></a>Zobacz także

[krotki ](../standard-library/tuple-class.md)<br/>
