---
title: tuple — Klasa
ms.date: 11/04/2016
f1_keywords:
- tuple/std::tuple
- tuple/std::tuple::operator=
helpviewer_keywords:
- tuple class
ms.assetid: c38749be-ae4d-41f3-98ea-6aa3250de9a3
ms.openlocfilehash: 1727d3a12b7186d3cc868ef6bb78711774057407
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/21/2019
ms.locfileid: "72688864"
---
# <a name="tuple-class"></a>tuple — Klasa

Otacza sekwencję o stałej długości elementów.

## <a name="syntax"></a>Składnia

```
class tuple {
   tuple();
   explicit tuple(P1, P2, ..., PN); // 0 < N
   tuple(const tuple&);
   template <class U1, class U2, ..., class UN>
      tuple(const tuple<U1, U2, ..., UN>&);
   template <class U1, class U2>
      tuple(const pair<U1, U2>&); // N == 2

   void swap(tuple& right);
   tuple& operator=(const tuple&);
   template <class U1, class U2, ..., class UN>
      tuple& operator=(const tuple<U1, U2, ..., UN>&);
   template <class U1, class U2>
      tuple& operator=(const pair<U1, U2>&); // N == 2
};
```

### <a name="parameters"></a>Parametry

@No__t_1 *TN*
Typ n-tego elementu krotki.

## <a name="remarks"></a>Uwagi

Szablon klasy opisuje obiekt, który przechowuje N obiektów typu `T1`, `T2`,..., `TN`, odpowiednio, gdzie `0 <= N <= Nmax`. Zakresem `tuple<T1, T2, ..., TN>` wystąpienia krotki jest liczba `N` argumentów szablonu. Indeks argumentu szablonu `Ti` i z odpowiadającej jej wartości przechowywanej tego typu jest `i - 1`. W ten sposób, chociaż numery typy z zakresu od 1 do N w tej dokumentacji, odpowiednie wartości indeksu mieszczą się w zakresie od 0 do N-1.

## <a name="example"></a>Przykład

```cpp
// tuple.cpp
// compile with: /EHsc

#include <vector>
#include <iomanip>
#include <iostream>
#include <tuple>
#include <string>

using namespace std;

typedef tuple <int, double, string> ids;

void print_ids(const ids& i)
{
   cout << "( "
        << get<0>(i) << ", "
        << get<1>(i) << ", "
        << get<2>(i) << " )." << endl;
}

int main( )
{
   // Using the constructor to declare and initialize a tuple
   ids p1(10, 1.1e-2, "one");

   // Compare using the helper function to declare and initialize a tuple
   ids p2;
   p2 = make_tuple(10, 2.22e-1, "two");

   // Making a copy of a tuple
   ids p3(p1);

   cout.precision(3);
   cout << "The tuple p1 is: ( ";
   print_ids(p1);
   cout << "The tuple p2 is: ( ";
   print_ids(p2);
   cout << "The tuple p3 is: ( ";
   print_ids(p3);

   vector<ids> v;

   v.push_back(p1);
   v.push_back(p2);
   v.push_back(make_tuple(3, 3.3e-2, "three"));

   cout << "The tuples in the vector are" << endl;
   for(vector<ids>::const_iterator i = v.begin(); i != v.end(); ++i)
   {
      print_ids(*i);
   }
}
```

```Output
The tuple p1 is: ( 10, 0.011, one ).
The tuple p2 is: ( 10, 0.222, two ).
The tuple p3 is: ( 10, 0.011, one ).
The tuples in the vector are
( 10, 0.011, one ).
( 10, 0.222, two ).
( 3, 0.033, three ).
```

## <a name="op_eq"></a>operator =

Przypisuje obiekt `tuple`.

```cpp
tuple& operator=(const tuple& right);

template <class U1, class U2, ..., class UN>
   tuple& operator=(const tuple<U1, U2, ..., UN>& right);

template <class U1, class U2>
   tuple& operator=(const pair<U1, U2>& right); // N == 2

tuple& operator=(tuple&& right);

template <class U1, class U2>
   tuple& operator=(pair<U1, U2>&& right);
```

### <a name="parameters"></a>Parametry

*@No__t_1*
Typ n-ty skopiowanego elementu krotki.

*prawa* \
Krotka, z której ma zostać skopiowane.

### <a name="remarks"></a>Uwagi

Pierwsze dwa operatory Członkowskie przypisują elementy *bezpośrednio* do odpowiednich elementów `*this`. Trzeci operator członkowski przypisuje `right.first` do elementu pod indeksem 0 `*this` i `right.second` do elementu pod indeksem 1. Wszystkie trzy operatory Członkowskie zwracają `*this`.

Pozostałe operatory składowe są analogiczne do wcześniejszych, ale z [rvalue Reference deklarator: & &](../cpp/rvalue-reference-declarator-amp-amp.md).

### <a name="example"></a>Przykład

```cpp
// std__tuple__tuple_operator_as.cpp
// compile with: /EHsc
#include <tuple>
#include <iostream>
#include <utility>

typedef std::tuple<int, double, int, double> Mytuple;
int main()
    {
    Mytuple c0(0, 1, 2, 3);

// display contents " 0 1 2 3"
    std::cout << " " << std::get<0>(c0);
    std::cout << " " << std::get<1>(c0);
    std::cout << " " << std::get<2>(c0);
    std::cout << " " << std::get<3>(c0);
    std::cout << std::endl;

    Mytuple c1;
    c1 = c0;

// display contents " 0 1 2 3"
    std::cout << " " << std::get<0>(c1);
    std::cout << " " << std::get<1>(c1);
    std::cout << " " << std::get<2>(c1);
    std::cout << " " << std::get<3>(c1);
    std::cout << std::endl;

    std::tuple<char, int> c2;
    c2 = std::make_pair('x', 4);

// display contents " x 4"
    std::cout << " " << std::get<0>(c2);
    std::cout << " " << std::get<1>(c2);
    std::cout << std::endl;

    return (0);
}
```

```Output
0 1 2 3
0 1 2 3
x 4
```

## <a name="tuple_swap"></a>wymiany

Wymienia elementy dwóch krotek.

```cpp
template <class... Types>
   void swap(tuple<Types...&> left, tuple<Types...&> right);
```

### <a name="parameters"></a>Parametry

\ *lewo*
Krotka, której elementy są wymieniane z tymi, które są z *prawej strony*.

*prawa* \
Krotka, której elementy są wymieniane z *pozostałymi*kolekcjami z lewej strony.

### <a name="remarks"></a>Uwagi

Funkcja wykonuje `left.swap(right)`.

## <a name="tuple"></a>spoin

Konstruuje obiekt `tuple`.

```cpp
constexpr tuple();
explicit constexpr tuple(const Types&...);
template <class... UTypes>
   explicit constexpr tuple(UTypes&&...);

tuple(const tuple&) = default;
tuple(tuple&&) = default;

template <class... UTypes>
   constexpr tuple(const tuple<UTypes...>&);
template <class... UTypes>
   constexpr tuple(tuple<UTypes...>&&);

// only if sizeof...(Types) == 2
template <class U1, class U2>
   constexpr tuple(const pair<U1, U2>&);
template <class U1, class U2>
   constexpr tuple(pair<U1, U2>&&);
```

### <a name="parameters"></a>Parametry

*@No__t_1*
Typ n-ty skopiowanego elementu krotki.

*prawa* \
Krotka, z której ma zostać skopiowane.

### <a name="remarks"></a>Uwagi

Pierwszy Konstruktor konstruuje obiekt, którego elementy są konstruowane domyślnie.

Drugi Konstruktor konstruuje obiekt, którego elementy są kopiowane z argumentów `P1`, `P2`,..., `PN` z każdym `Pi` inicjowania elementu przy indeksie `i - 1`.

Trzeci i czwarty konstruktory konstruują obiekt, którego elementy są kopiowane z odpowiedniego elementu z *prawej strony*.

Piąty Konstruktor konstruuje obiekt, którego element pod indeksem 0 jest kopiowany z `right.first` i którego element o indeksie 1 jest kopiowany z `right.second`.

Pozostałe konstruktory są analogowe do wcześniejszych, ale z [rvalue Reference deklarator: & &](../cpp/rvalue-reference-declarator-amp-amp.md).

### <a name="example"></a>Przykład

```cpp
// std__tuple__tuple_tuple.cpp
// compile with: /EHsc
#include <tuple>
#include <iostream>
#include <utility>

typedef std::tuple<int, double, int, double> Mytuple;
int main()
{
    Mytuple c0(0, 1, 2, 3);

    // display contents "0 1 2 3"
    std::cout << std::get<0>(c0) << " ";
    std::cout << std::get<1>(c0) << " ";
    std::cout << std::get<2>(c0) << " ";
    std::cout << std::get<3>(c0);
    std::cout << std::endl;

    Mytuple c1;
    c1 = c0;

    // display contents "0 1 2 3"
    std::cout << std::get<0>(c1) << " ";
    std::cout << std::get<1>(c1) << " ";
    std::cout << std::get<2>(c1) << " ";
    std::cout << std::get<3>(c1);
    std::cout << std::endl;

    std::tuple<char, int> c2(std::make_pair('x', 4));

    // display contents "x 4"
    std::cout << std::get<0>(c2) << " ";
    std::cout << std::get<1>(c2);
    std::cout << std::endl;

    Mytuple c3(c0);

    // display contents "0 1 2 3"
    std::cout << std::get<0>(c3) << " ";
    std::cout << std::get<1>(c3) << " ";
    std::cout << std::get<2>(c3) << " ";
    std::cout << std::get<3>(c3);
    std::cout << std::endl;

    typedef std::tuple<int, float, int, float> Mytuple2;
    Mytuple c4(Mytuple2(4, 5, 6, 7));

    // display contents "4 5 6 7"
    std::cout << std::get<0>(c4) << " ";
    std::cout << std::get<1>(c4) << " ";
    std::cout << std::get<2>(c4) << " ";
    std::cout << std::get<3>(c4);
    std::cout << std::endl;

    return (0);
}
```

```Output
0 1 2 3
0 1 2 3
x 4
0 1 2 3
4 5 6 7
```
