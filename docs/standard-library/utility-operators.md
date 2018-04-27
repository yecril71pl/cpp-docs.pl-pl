---
title: '&lt;Narzędzie&gt; operatory | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- utility/std::operator!=
- utility/std::operator&gt;
- utility/std::operator&gt;=
- utility/std::operator&lt;
- utility/std::operator&lt;=
- utility/std::operator==
dev_langs:
- C++
ms.assetid: a6617109-2cec-4a69-948f-6c87116eda5f
caps.latest.revision: 13
manager: ghogen
helpviewer_keywords:
- std::operator!= (utility)
- std::operator&gt; (utility)
- std::operator&gt;= (utility)
- std::operator&lt; (utility)
- std::operator&lt;= (utility)
- std::operator== (utility)
ms.openlocfilehash: 412cd623fcffbc2c37d8f5fa58c6ec5c2cd8d3e1
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="ltutilitygt-operators"></a>&lt;Narzędzie&gt; operatory

||||
|-|-|-|
|[operator!=](#op_neq)|[Operator&gt;](#op_gt)|[Operator&gt;=](#op_gt_eq)|
|[Operator&lt;](#op_lt)|[Operator&lt;=](#op_lt_eq)|[operator==](#op_eq_eq)|

## <a name="op_neq"></a>  operator! =

Testy, jeśli obiekt pary po lewej stronie operatora nie jest taki sam jak obiekt pary po prawej stronie.

```cpp
template <class Type>
constexpr bool operator!=(const Type& left, const Type& right);

template <class T, class U>
constexpr bool operator!=(const pair<T, U>& left, const pair<T, U>& right);
```

### <a name="parameters"></a>Parametry

`left` Obiekt typu **pary.**

`right` Obiekt typu `pair`.

### <a name="return-value"></a>Wartość zwracana

**wartość true,** pary nie są równe; **false** pary są równe.

### <a name="remarks"></a>Uwagi

Jedna para jest równa kolejną parę, jeśli każdy z ich odpowiednich elementów jest taki sam. Dwie pary nie są równe, jeśli pierwszy lub drugi element jednego nie jest równa odpowiadającego mu elementu innych pary.

### <a name="example"></a>Przykład

```cpp
// utility_op_ne.cpp
// compile with: /EHsc
#include <utility>
#include <iomanip>
#include <iostream>

int main( )
{
   using namespace std;
   pair <int, double> p1, p2, p3;

   p1 = make_pair ( 10, 1.11e-1 );
   p2 = make_pair ( 1000, 1.11e-3 );
   p3 = make_pair ( 10, 1.11e-1 );

   cout.precision ( 3 );
   cout << "The pair p1 is: ( " << p1.first << ", "
        << p1.second << " )." << endl;
   cout << "The pair p2 is: ( " << p2.first << ", "
        << p2.second << " )." << endl;
   cout << "The pair p3 is: ( " << p3.first << ", "
        << p3.second << " )." << endl << endl;

   if ( p1 != p2 )
      cout << "The pairs p1 and p2 are not equal." << endl;
   else
      cout << "The pairs p1 and p2 are equal." << endl;

   if ( p1 != p3 )
      cout << "The pairs p1 and p3 are not equal." << endl;
   else
      cout << "The pairs p1 and p3 are equal." << endl;
}
```

```Output
The pair p1 is: ( 10, 0.111 ).
The pair p2 is: ( 1000, 0.00111 ).
The pair p3 is: ( 10, 0.111 ).

The pairs p1 and p2 are not equal.
The pairs p1 and p3 are equal.
```

## <a name="op_eq_eq"></a>  operator ==

Testy, jeśli obiekt pary po lewej stronie operatora jest taki sam jak obiekt pary po prawej stronie.

```cpp
template <class T, class U>
constexpr bool operator==(const pair<T, U>& left, const pair<T, U>& right);
```

### <a name="parameters"></a>Parametry

`left` Obiekt typu **pary.**

`right` Obiekt typu `pair`.

### <a name="return-value"></a>Wartość zwracana

**wartość true,** pary są równe; **false** Jeśli `pair`s nie są takie same.

### <a name="remarks"></a>Uwagi

Jedna para jest równa kolejną parę, jeśli każdy z ich odpowiednich elementów jest taki sam. Funkcja zwraca `left`. **pierwszy** == `right`. **pierwszy** && `left`. **drugi** == `right`. **drugi**. Dwie pary nie są równe, jeśli pierwszy lub drugi element jednego nie jest równa odpowiadającego mu elementu innych pary.

### <a name="example"></a>Przykład

```cpp
// utility_op_eq.cpp
// compile with: /EHsc
#include <utility>
#include <iomanip>
#include <iostream>

int main( )
{
   using namespace std;
   pair <int, double> p1, p2, p3;

   p1 = make_pair ( 10, 1.11e-1 );
   p2 = make_pair ( 1000, 1.11e-3 );
   p3 = make_pair ( 10, 1.11e-1 );

   cout.precision ( 3 );
   cout << "The pair p1 is: ( " << p1.first << ", "
        << p1.second << " )." << endl;
   cout << "The pair p2 is: ( " << p2.first << ", "
        << p2.second << " )." << endl;
   cout << "The pair p3 is: ( " << p3.first << ", "
        << p3.second << " )." << endl << endl;

   if ( p1 == p2 )
      cout << "The pairs p1 and p2 are equal." << endl;
   else
      cout << "The pairs p1 and p2 are not equal." << endl;

   if ( p1 == p3 )
      cout << "The pairs p1 and p3 are equal." << endl;
   else
      cout << "The pairs p1 and p3 are not equal." << endl;
}
```

## <a name="op_lt"></a>  Operator&lt;

Testy, jeśli obiekt pary po lewej stronie operatora jest mniejsza niż obiekt pary po prawej stronie.

```cpp
template <class T, class U>
constexpr bool operator<(const pair<T, U>& left, const pair<T, U>& right);
```

### <a name="parameters"></a>Parametry

`left` Obiekt typu `pair` po lewej stronie operatora.

`right` Obiekt typu `pair` po prawej stronie operatora.

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli `pair` po lewej stronie operatora jest ściśle mniejsza niż `pair` po prawej stronie operatora; w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

`left` `pair` Obiektu jest określane jako ściśle mniejsza niż `right` `pair` obiekt zostanie `left` jest mniejsza niż i nie jest równa `right`.

W porównaniu z par pierwszych elementów dwóch par wartości ma najwyższy priorytet. Jeśli będą się różnić, wynik ich porównanie są wykonywane w wyniku porównania pary. Jeśli wartości pierwszych elementów nie są różne, wartości drugi elementów są porównywane i pochodzi wynik ich porównanie wyniku porównania pary.

### <a name="example"></a>Przykład

```cpp
// utility_op_lt.cpp
// compile with: /EHsc
#include <utility>
#include <iomanip>
#include <iostream>

int main( )
{
   using namespace std;
   pair <int, double> p1, p2, p3;

   p1 = make_pair ( 10, 2.22e-1 );
   p2 = make_pair ( 100, 1.11e-1 );
   p3 = make_pair ( 10, 1.11e-1 );

   cout.precision ( 3 );
   cout << "The pair p1 is: ( " << p1.first << ", "
        << p1.second << " )." << endl;
   cout << "The pair p2 is: ( " << p2.first << ", "
        << p2.second << " )." << endl;
   cout << "The pair p3 is: ( " << p3.first << ", "
        << p3.second << " )." << endl << endl;

   if ( p1 < p2 )
      cout << "The pair p1 is less than the pair p2." << endl;
   else
      cout << "The pair p1 is not less than the pair p2." << endl;

   if ( p1 < p3 )
      cout << "The pair p1 is less than the pair p3." << endl;
   else
      cout << "The pair p1 is not less than the pair p3." << endl;
}
```

```Output
The pair p1 is: ( 10, 0.222 ).
The pair p2 is: ( 100, 0.111 ).
The pair p3 is: ( 10, 0.111 ).

The pair p1 is less than the pair p2.
The pair p1 is not less than the pair p3.
```

## <a name="op_lt_eq"></a>  Operator&lt;=

Testy, jeśli obiekt pary po lewej stronie operatora jest mniejsza niż lub równe obiekt pary po prawej stronie.

```cpp
template <class Type>
constexpr bool operator<=(const Type& left, const Type& right);

template <class T, class U>
constexpr bool operator<=(const pair<T, U>& left, const pair<T, U>& right);
```

### <a name="parameters"></a>Parametry

`left` Obiekt typu `pair` po lewej stronie operatora.

`right` Obiekt typu `pair` po prawej stronie operatora.

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli `pair` po lewej stronie operatora jest mniejsze niż lub równe `pair` po prawej stronie operatora; w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

W porównaniu z par pierwszych elementów dwóch par wartości ma najwyższy priorytet. Jeśli będą się różnić, wynik ich porównanie są wykonywane w wyniku porównania pary. Jeśli wartości pierwszych elementów nie są różne, wartości drugi elementów są porównywane i pochodzi wynik ich porównanie wyniku porównania pary.

### <a name="example"></a>Przykład

```cpp
// utility_op_le.cpp
// compile with: /EHsc
#include <utility>
#include <iomanip>
#include <iostream>

int main( )
{
   using namespace std;
   pair <int, double> p1, p2, p3, p4;

   p1 = make_pair ( 10, 2.22e-1 );
   p2 = make_pair ( 100, 1.11e-1 );
   p3 = make_pair ( 10, 1.11e-1 );
   p4 = make_pair ( 10, 2.22e-1 );

   cout.precision ( 3 );
   cout << "The pair p1 is: ( " << p1.first << ", "
        << p1.second << " )." << endl;
   cout << "The pair p2 is: ( " << p2.first << ", "
        << p2.second << " )." << endl;
   cout << "The pair p3 is: ( " << p3.first << ", "
        << p3.second << " )." << endl;
   cout << "The pair p4 is: ( " << p4.first << ", "
        << p4.second << " )." << endl << endl;

   if ( p1 <= p2 )
      cout << "The pair p1 is less than or equal to the pair p2." << endl;
   else
      cout << "The pair p1 is greater than the pair p2." << endl;

   if ( p1 <= p3 )
      cout << "The pair p1 is less than or equal to the pair p3." << endl;
   else
      cout << "The pair p1 is greater than the pair p3." << endl;

   if ( p1 <= p4 )
      cout << "The pair p1 is less than or equal to the pair p4." << endl;
   else
      cout << "The pair p1 is greater than the pair p4." << endl;
}
```

```Output
The pair p1 is: ( 10, 0.222 ).
The pair p2 is: ( 100, 0.111 ).
The pair p3 is: ( 10, 0.111 ).
The pair p4 is: ( 10, 0.222 ).

The pair p1 is less than or equal to the pair p2.
The pair p1 is greater than the pair p3.
The pair p1 is less than or equal to the pair p4.
```

## <a name="op_gt"></a>  Operator&gt;

Testy, jeśli obiekt pary po lewej stronie operatora jest większy niż obiekt pary po prawej stronie.

```cpp
template <class Type>
constexpr bool operator>(const Type& left, const Type& right);

template <class T, class U>
constexpr bool operator>(const pair<T, U>& left, const pair<T, U>& right);
```

### <a name="parameters"></a>Parametry

`left` Obiekt typu `pair` po lewej stronie operatora.

`right` Obiekt typu `pair` po prawej stronie operatora.

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli `pair` po lewej stronie operatora jest większa niż `pair` po prawej stronie operatora; w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

`left` `pair` Obiektu jest określany jako większa niż `right` `pair` obiekt zostanie `left` jest większa i nie jest równa `right`.

W porównaniu z par pierwszych elementów dwóch par wartości ma najwyższy priorytet. Jeśli będą się różnić, wynik ich porównanie są wykonywane w wyniku porównania pary. Jeśli wartości pierwszych elementów nie są różne, wartości drugi elementów są porównywane i pochodzi wynik ich porównanie wyniku porównania pary.

### <a name="example"></a>Przykład

```cpp
// utility_op_gt.cpp
// compile with: /EHsc
#include <utility>
#include <iomanip>
#include <iostream>

int main( )
{
   using namespace std;
   pair <int, double> p1, p2, p3, p4;

   p1 = make_pair ( 10, 2.22e-1 );
   p2 = make_pair ( 100, 1.11e-1 );
   p3 = make_pair ( 10, 1.11e-1 );
   p4 = make_pair ( 10, 2.22e-1 );

   cout.precision ( 3 );
   cout << "The pair p1 is: ( " << p1.first << ", "
        << p1.second << " )." << endl;
   cout << "The pair p2 is: ( " << p2.first << ", "
        << p2.second << " )." << endl;
   cout << "The pair p3 is: ( " << p3.first << ", "
        << p3.second << " )." << endl;
   cout << "The pair p4 is: ( " << p4.first << ", "
        << p4.second << " )." << endl << endl;

   if ( p1 > p2 )
      cout << "The pair p1 is greater than the pair p2." << endl;
   else
      cout << "The pair p1 is not greater than the pair p2." << endl;

   if ( p1 > p3 )
      cout << "The pair p1 is greater than the pair p3." << endl;
   else
      cout << "The pair p1 is not greater than the pair p3." << endl;

   if ( p1 > p4 )
      cout << "The pair p1 is greater than the pair p4." << endl;
   else
      cout << "The pair p1 is not greater than the pair p4." << endl;
}
```

```Output
The pair p1 is: ( 10, 0.222 ).
The pair p2 is: ( 100, 0.111 ).
The pair p3 is: ( 10, 0.111 ).
The pair p4 is: ( 10, 0.222 ).

The pair p1 is not greater than the pair p2.
The pair p1 is greater than the pair p3.
The pair p1 is not greater than the pair p4.
```

## <a name="op_gt_eq"></a>  Operator&gt;=

Testy, jeśli obiekt pary po lewej stronie operatora jest większa niż lub równa obiekt pary po prawej stronie.

```cpp
template <class Type>
constexpr bool operator>=(const Type& left, const Type& right);

template <class T, class U>
constexpr bool operator>=(const pair<T, U>& left, const pair<T, U>& right);
```

### <a name="parameters"></a>Parametry

`left` Obiekt typu `pair` po lewej stronie operatora.

`right` Obiekt typu `pair` po prawej stronie operatora.

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli `pair` po lewej stronie operatora jest większa niż lub równa `pair` po prawej stronie operatora; w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

W porównaniu z par pierwszych elementów dwóch par wartości ma najwyższy priorytet. Jeśli będą się różnić, wynik ich porównanie są wykonywane w wyniku porównania pary. Jeśli wartości pierwszych elementów nie są różne, wartości drugi elementów są porównywane i pochodzi wynik ich porównanie wyniku porównania pary.

### <a name="example"></a>Przykład

```cpp
// utility_op_ge.cpp
// compile with: /EHsc
#include <utility>
#include <iomanip>
#include <iostream>

int main( )
{
   using namespace std;
   pair <int, double> p1, p2, p3, p4;

   p1 = make_pair ( 10, 2.22e-1 );
   p2 = make_pair ( 100, 1.11e-1 );
   p3 = make_pair ( 10, 1.11e-1 );
   p4 = make_pair ( 10, 2.22e-1 );

   cout.precision ( 3 );
   cout << "The pair p1 is: ( " << p1.first << ", "
        << p1.second << " )." << endl;
   cout << "The pair p2 is: ( " << p2.first << ", "
        << p2.second << " )." << endl;
   cout << "The pair p3 is: ( " << p3.first << ", "
        << p3.second << " )." << endl;
   cout << "The pair p4 is: ( " << p4.first << ", "
        << p4.second << " )." << endl << endl;

   if ( p1 >= p2 )
      cout << "Pair p1 is greater than or equal to pair p2." << endl;
   else
      cout << "The pair p1 is less than the pair p2." << endl;

   if ( p1 >= p3 )
      cout << "Pair p1 is greater than or equal to pair p3." << endl;
   else
      cout << "The pair p1 is less than the pair p3." << endl;

   if ( p1 >= p4 )
      cout << "Pair p1 is greater than or equal to pair p4." << endl;
   else
      cout << "The pair p1 is less than the pair p4." << endl;
}
```

```Output
The pair p1 is: ( 10, 0.222 ).
The pair p2 is: ( 100, 0.111 ).
The pair p3 is: ( 10, 0.111 ).
The pair p4 is: ( 10, 0.222 ).

The pair p1 is less than the pair p2.
Pair p1 is greater than or equal to pair p3.
Pair p1 is greater than or equal to pair p4.
```

## <a name="see-also"></a>Zobacz także

[\<utility>](../standard-library/utility.md)<br/>
