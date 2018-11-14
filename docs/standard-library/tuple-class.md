---
title: tuple — Klasa
ms.date: 11/04/2016
f1_keywords:
- tuple/std::tuple
- tuple/std::tuple::operator=
helpviewer_keywords:
- tuple class
ms.assetid: c38749be-ae4d-41f3-98ea-6aa3250de9a3
ms.openlocfilehash: 7e85ad445743cc02ba078eb3c09342f69915c09c
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/10/2018
ms.locfileid: "51518531"
---
# <a name="tuple-class"></a>tuple — Klasa

Opakowuje o stałej długości sekwencji elementów.

## <a name="syntax"></a>Składnia

```
class tuple {
public:
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

*TN*<br/>
Typ elementu spójnej kolekcji n-ty.

## <a name="remarks"></a>Uwagi

Klasa szablonu opisuje obiekt przechowujący N obiektów typów `T1`, `T2`,..., `TN`, odpowiednio, gdzie `0 <= N <= Nmax`. Zakres wystąpień krotki `tuple<T1, T2, ..., TN>` jest to liczba `N` z jej argumentów szablonu. Indeks argument szablonu `Ti` i odpowiednie przechowywaną wartość tego typu jest `i - 1`. W związku z tym gdy firma Microsoft numer typy z zakresu od 1 do N w tej dokumentacji, odpowiedni indeks wartości z zakresu od 0 do N - 1.

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

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<krotki >

**Namespace:** standardowe

## <a name="op_eq"></a>  Tuple::operator =

Przypisuje `tuple` obiektu.

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

*NZ*<br/>
Typ n-tej skopiować element spójnej kolekcji.

*right*<br/>
Krotka do skopiowania.

### <a name="remarks"></a>Uwagi

Pierwszy operatory dwóch elementów członkowskich Przypisz elementy *prawo* do odpowiednich elementów `*this`. Trzeci operator składowy przypisuje `right.first` do elementu w indeksie 0 `*this` i `right.second` na element pod indeksem 1. Zwróć wszystkie operatory trzech członków `*this`.

Pozostałe operatory elementów członkowskich są analogs starszych z nich, ale z [Rvalue Reference Declarator: & &](../cpp/rvalue-reference-declarator-amp-amp.md).

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

## <a name="tuple_swap"></a>  Tuple:swap

Zamienia elementy z dwóch krotek.

```cpp
template <class... Types>
   void swap(tuple<Types...&> left, tuple<Types...&> right);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*left*|Spójna kolekcja, której elementy są wymieniane z tymi krotki *prawo*.|
|*right*|Spójna kolekcja, której elementy są wymieniane z tymi krotki *po lewej stronie*.|

### <a name="remarks"></a>Uwagi

Wykonuje funkcję `left.swap(right)`.

## <a name="tuple"></a>  Tuple::Tuple

Konstruuje `tuple` obiektu.

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

*NZ*<br/>
Typ n-tej skopiować element spójnej kolekcji.

*right*<br/>
Krotka do skopiowania.

### <a name="remarks"></a>Uwagi

Pierwszy Konstruktor konstruuje obiekt, którego elementy mają domyślne.

Drugi Konstruktor konstruuje obiekt, którego elementy mają kopiowania skonstruowany na podstawie argumentów `P1`, `P2`,..., `PN` z każdym `Pi` inicjowanie element w indeksie `i - 1`.

Konstruktory trzecia i czwarta skonstruować obiekt, w której elementy są konstruowane na podstawie odpowiedniego elementu kopii *prawo*.

Piąty Konstruktor konstruuje obiekt, którego element pod indeksem 0 jest kopią skonstruowany na podstawie `right.first` i którego element pod indeksem 1 jest kopia zbudowane z `right.second`.

Pozostałe konstruktory są analogs starszych z nich, ale z [Rvalue Reference Declarator: & &](../cpp/rvalue-reference-declarator-amp-amp.md).

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

## <a name="see-also"></a>Zobacz także

[\<tuple>](../standard-library/tuple.md)<br/>
[make_tuple](../standard-library/tuple-functions.md#make_tuple)<br/>
