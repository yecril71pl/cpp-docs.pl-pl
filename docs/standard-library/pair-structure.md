---
title: pair — Struktura
ms.date: 11/04/2016
f1_keywords:
- utility/std::pair
helpviewer_keywords:
- pair class
ms.assetid: 539d3d67-80a2-4170-b347-783495d42109
ms.openlocfilehash: 0a78d5074c37f4fbbfb736125626fa4b7fc7e275
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/29/2020
ms.locfileid: "91505762"
---
# <a name="pair-structure"></a>pair — Struktura

Struktura, która umożliwia traktowanie dwóch obiektów jako jednego obiektu.

## <a name="syntax"></a>Składnia

```cpp
struct pair
{
    typedef T1 first_type;
    typedef T2 second_type;
    T1 first;
    T2 second;
    constexpr pair();
    pair(const pair&) = default;
    pair(pair&&) = default;
    constexpr pair(
        const T1& Val1,
        const T2& Val2);

    template <class Other1, class Other2>
    constexpr pair(const pair<Other1, Other2>& Right);

    template <class Other1, class Other2>
    constexpr pair(const pair <Other1 Val1, Other2 Val2>&& Right);

    template <class Other1, class Other2>
    constexpr pair(Other1&& Val1, Other2&& Val2);

    template <class... Args1, class... Args2>
    pair(piecewise_construct_t, tuple<Args1...> first_args, tuple<Args2...> second_args);

    pair& operator=(const pair& p);
    template<class U1, class U2> pair& operator=(const pair<U1, U2>& p);
    pair& operator=(pair&& p) noexcept(see below );
    template<class U1, class U2> pair& operator=(pair<U1, U2>&& p);

    void swap(pair& p) noexcept(see below );
};

template<class T1, class T2>
    pair(T1, T2) -> pair<T1, T2>;
```

### <a name="parameters"></a>Parametry

*Val1*\
Wartość inicjująca pierwszy element `pair` .

*Val2*\
Wartość inicjująca drugi element `pair` .

*Kliknij*\
Para, której wartości mają być używane do inicjowania elementów innej pary.

## <a name="return-value"></a>Wartość zwracana

Pierwszy (domyślny) Konstruktor inicjuje pierwszy element pary do wartości domyślnej typu `T1` i drugiego elementu do wartości domyślnej typu `T2` .  Jest on definiowany, jeśli oba typy to Default-konstrukcyjną.

Drugi Konstruktor inicjuje pierwszy element pary do *Val1* , a drugi do *val2.*  Jest on definiowany, jeśli oba typy to Copy-konstrukcyjną.

Trzeci Konstruktor (Template) inicjuje pierwszy element pary do `Right` . **pierwszy** i drugi do `Right` . **sekunda**.  Jest on definiowany, jeśli oba typy par są konstrukcyjną z dostarczonych typów wartości.

Czwarty Konstruktor inicjuje pierwszy element pary do *Val1* , a drugi do *val2* przy użyciu [rvalue Reference deklarator:  &&](../cpp/rvalue-reference-declarator-amp-amp.md).  Jest on definiowany, jeśli oba typy par są konstrukcyjną z dostarczonych typów wartości.

## <a name="remarks"></a>Uwagi

Struktura szablonu przechowuje parę obiektów typu `T1` i `T2` , odpowiednio. Typ `first_type` jest taki sam jak parametr szablonu `T1` , a typ jest taki `second_type` sam jak parametr szablonu `T2` . `T1``T2`każdy z nich wymaga tylko konstruktora domyślnego, konstruktora pojedynczego argumentu i destruktora. Wszystkie elementy członkowskie tego typu `pair` są publiczne, ponieważ typ jest zadeklarowany jako a, **`struct`** a nie jako **`class`** . Dwa najczęstsze zastosowania dla pary są jako zwracane typy dla funkcji, które zwracają dwie wartości, a jako elementy klas [mapowania](../standard-library/map-class.md) klasy kontenera i klasy [multimap](../standard-library/multimap-class.md) , które mają zarówno klucz, jak i typ wartości skojarzone z każdym elementem. Druga z nich spełnia wymagania dotyczące pary kontenerów asocjacyjnych i ma typ wartości formularza `pair< const key_type, mapped_type >` .

## <a name="example"></a>Przykład

```cpp
// utility_pair.cpp
// compile with: /EHsc
#include <utility>
#include <map>
#include <iomanip>
#include <iostream>

int main( )
{
   using namespace std;

   // Using the constructor to declare and initialize a pair
   pair <int, double> p1 ( 10, 1.1e-2 );

   // Compare using the helper function to declare and initialize a pair
   pair <int, double> p2;
   p2 = make_pair ( 10, 2.22e-1 );

   // Making a copy of a pair
   pair <int, double> p3 ( p1 );

   cout.precision ( 3 );
   cout << "The pair p1 is: ( " << p1.first << ", "
        << p1.second << " )." << endl;
   cout << "The pair p2 is: ( " << p2.first << ", "
        << p2.second << " )." << endl;
   cout << "The pair p3 is: ( " << p3.first << ", "
        << p3.second << " )." << endl;

   // Using a pair for a map element
   map <int, int> m1;
   map <int, int>::iterator m1_Iter;

   typedef pair <int, int> Map_Int_Pair;

   m1.insert ( Map_Int_Pair ( 1, 10 ) );
   m1.insert ( Map_Int_Pair ( 2, 20 ) );
   m1.insert ( Map_Int_Pair ( 3, 30 ) );

   cout << "The element pairs of the map m1 are:";
   for ( m1_Iter = m1.begin( ); m1_Iter != m1.end( ); m1_Iter++ )
      cout << " ( " << m1_Iter -> first << ", "
           << m1_Iter -> second << " )";
   cout   << "." << endl;

   // Using pair as a return type for a function
   pair< map<int,int>::iterator, bool > pr1, pr2;
   pr1 = m1.insert ( Map_Int_Pair ( 4, 40 ) );
   pr2 = m1.insert ( Map_Int_Pair (1, 10 ) );

   if( pr1.second == true )
   {
      cout << "The element (4,40) was inserted successfully in m1."
           << endl;
   }
   else
   {
      cout << "The element with a key value of\n"
           << " ( (pr1.first) -> first ) = " << ( pr1.first ) -> first
           << " is already in m1,\n so the insertion failed." << endl;
   }

   if( pr2.second == true )
   {
      cout << "The element (1,10) was inserted successfully in m1."
           << endl;
   }
   else
   {
      cout << "The element with a key value of\n"
           << " ( (pr2.first) -> first ) = " << ( pr2.first ) -> first
           << " is already in m1,\n so the insertion failed." << endl;
   }
}
```

```Output
The pair p1 is: ( 10, 0.011 ).
The pair p2 is: ( 10, 0.222 ).
The pair p3 is: ( 10, 0.011 ).
The element pairs of the map m1 are: ( 1, 10 ) ( 2, 20 ) ( 3, 30 ).
The element (4,40) was inserted successfully in m1.
The element with a key value of
( (pr2.first) -> first ) = 1 is already in m1,
so the insertion failed.
```
