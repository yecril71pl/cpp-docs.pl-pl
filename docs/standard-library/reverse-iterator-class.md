---
title: reverse_iterator — Klasa
ms.date: 03/27/2019
f1_keywords:
- xutility/std::reverse_iterator
- iterator/std::reverse_iterator::difference_type
- iterator/std::reverse_iterator::iterator_type
- iterator/std::reverse_iterator::pointer
- iterator/std::reverse_iterator::reference
- iterator/std::reverse_iterator::base
- iterator/std::reverse_iterator::operator_star
helpviewer_keywords:
- std::reverse_iterator [C++]
- std::reverse_iterator [C++], difference_type
- std::reverse_iterator [C++], iterator_type
- std::reverse_iterator [C++], pointer
- std::reverse_iterator [C++], reference
- std::reverse_iterator [C++], base
- std::reverse_iterator [C++], operator_star
ms.assetid: c0b34d04-ae9a-4999-9aff-28b313897ffa
ms.openlocfilehash: 882d0f7f4930e9d809098a29384a962d0aa8f4ea
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373439"
---
# <a name="reverse_iterator-class"></a>reverse_iterator — Klasa

Szablon klasy jest adapterem iteratora, który opisuje obiekt odwrotnej iteratora, który zachowuje się jak zmiennoumisowy dostęp losowy lub dwukierunkowy iterator, tylko w odwrotnej kolejności. Umożliwia przechodzenie do tyłu zakresu.

## <a name="syntax"></a>Składnia

```cpp
template <class RandomIterator>
class reverse_iterator
```

### <a name="parameters"></a>Parametry

RandomIterator Typ, który reprezentuje iteratora, który ma być dostosowany do pracy w odwrotnej kolejności.

## <a name="remarks"></a>Uwagi

Istniejące kontenery biblioteki standardowej języka C++ również definiują `reverse_iterator` i `const_reverse_iterator` typują i mają funkcje `rbegin` członkowskie oraz `rend` zwracają iteratory odwrotne. Te iteratory mają semantykę nadpisywania. Adapter `reverse_iterator` uzupełnia tę funkcję, ponieważ oferuje semantykę wstawiania i może być również używany ze strumieniami.

To `reverse_iterator` wymaga dwukierunkowego iteratora nie może wywoływać `operator+=` `operator+`żadnej `operator-=` `operator-`z `operator[]`funkcji członkowskich , , , lub , które mogą być używane tylko z iteratorami dostępu losowego.

Zakres iteratora jest [*pierwszy*, *ostatni*), gdzie nawias kwadratowy po lewej stronie wskazuje włączenie *pierwszego,* a nawias po prawej stronie wskazuje włączenie elementów do, ale z wyłączeniem *samego ostatniego.* Te same elementy są zawarte w odwróconej sekwencji [ **rev** - *first*, **rev** - *last*), tak że jeśli *ostatni* jest elementem one-past-the-end w sekwencji, a następnie pierwszy element **rev** - *pierwszy* w odwróconej sekwencji wskazuje na \*(*ostatni* - 1). Tożsamość, która odnosi wszystkie iteratory odwrócone do ich iteratorów podstawowych, to:

&\*( **reverse_iterator** ( *i* ) ) == \*&( *i* - 1 ).

W praktyce oznacza to, że w odwróconej sekwencji reverse_iterator będzie się odnosił do elementu w jednej pozycji poza elementem (z jego prawej strony), do którego odnosił się iterator w oryginalnej sekwencji. Więc jeśli iterator skierowana element 6 w sekwencji (2, 4, `reverse_iterator` 6, 8), a następnie będzie adres elementu 4 w odwróconej sekwencji (8, 6, 4, 2).

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[Reverse_iterator](#reverse_iterator)|Tworzy domyślne `reverse_iterator` lub `reverse_iterator` z podstawowego iteratora.|

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[difference_type](#difference_type)|Typ, który zapewnia różnicę `reverse_iterator`między dwoma s odnoszących się do elementów w tym samym kontenerze.|
|[iterator_type](#iterator_type)|Typ, który zapewnia podstawowe iteratora dla `reverse_iterator`.|
|[pointer](#pointer)|Typ, który zapewnia wskaźnik do elementu `reverse_iterator`skierowanego przez .|
|[Odwołanie](#reference)|Typ, który zawiera odwołanie do elementu `reverse_iterator`skierowanego przez .|

### <a name="member-functions"></a>Funkcje członkowskie

|Funkcja członkowce|Opis|
|-|-|
|[base](#base)|Odzyskuje podstawowego iteratora z jego `reverse_iterator`.|

### <a name="operators"></a>Operatory

|Operator|Opis|
|-|-|
|[operator_star](#op_star)|Zwraca element, `reverse_iterator` który adresuje.|
|[operator+](#op_add)|Dodaje przesunięcie do iteratora i `reverse_iterator` zwraca nowy adresowanie wstawionego elementu w nowym położeniu odsunięcia.|
|[operator++](#op_add_add)|Zwiększa do `reverse_iterator` następnego elementu.|
|[operator+=](#op_add_eq)|Dodaje określone przesunięcie `reverse_iterator`z pliku .|
|[operator-](#operator-)|Odejmuje odsunięcie od a `reverse_iterator` i zwraca `reverse_iterator` adresowanie elementu w pozycji odsunięcia.|
|[operator --](#operator--)|Zmniejsza do `reverse_iterator` poprzedniego elementu.|
|[operator-=](#operator-_eq)|Odejmuje określone przesunięcie `reverse_iterator`od .|
|[operator->](#op-arrow)|Zwraca wskaźnik do elementu adresowane przez `reverse_iterator`.|
|[&#91;&#93;operatora](#op_at)|Zwraca odwołanie do elementu odsuniętego `reverse_iterator` od elementu adresowane przez określoną liczbę pozycji.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<> iteratora

**Przestrzeń nazw:** std

## <a name="reverse_iteratorbase"></a><a name="base"></a>reverse_iterator::base

Odzyskuje podstawowego iteratora z jego `reverse_iterator`.

```cpp
RandomIterator base() const;
```

### <a name="return-value"></a>Wartość zwracana

Iterator leżący `reverse_iterator`u podstaw pliku .

### <a name="remarks"></a>Uwagi

Tożsamość, która odnosi się do wszystkich iteratorów odwrotnych do ich podstawowych iteratorów jest:

&\*( `reverse_iterator` ( *i* ) ) == &\*( *i* - 1 ).

W praktyce oznacza to, że `reverse_iterator` w sekwencji odwróconej będzie odwoływać się do elementu jednej pozycji poza (po prawej stronie) elementu, który iterator miał określone w oryginalnej sekwencji. Więc jeśli iterator skierowana element 6 w sekwencji (2, 4, `reverse_iterator` 6, 8), a następnie będzie adres elementu 4 w odwróconej sekwencji (8, 6, 4, 2).

### <a name="example"></a>Przykład

```cpp
// reverse_iterator_base.cpp
// compile with: /EHsc
#include <iterator>
#include <algorithm>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   vector<int> vec;
   for ( i = 1 ; i < 6 ; ++i )
   {
      vec.push_back ( 2 * i );
   }

   vector <int>::iterator vIter;
   cout << "The vector vec is: ( ";
   for ( vIter = vec.begin ( ) ; vIter != vec.end ( ); vIter++ )
      cout << *vIter << " ";
   cout << ")." << endl;

   vector <int>::reverse_iterator rvIter;
   cout << "The vector vec reversed is: ( ";
   for ( rvIter = vec.rbegin( ) ; rvIter != vec.rend( ); rvIter++)
      cout << *rvIter << " ";
   cout << ")." << endl;

   vector <int>::iterator pos, bpos;
   pos = find ( vec.begin ( ), vec.end ( ), 6 );
   cout << "The iterator pos points to: " << *pos << "." << endl;

   typedef reverse_iterator<vector<int>::iterator>::iterator_type it_vec_int_type;

   reverse_iterator<it_vec_int_type> rpos ( pos );
   cout << "The reverse_iterator rpos points to: " << *rpos
        << "." << endl;

   bpos = rpos.base ( );
   cout << "The iterator underlying rpos is bpos & it points to: "
        << *bpos << "." << endl;
}
```

## <a name="reverse_iteratordifference_type"></a><a name="difference_type"></a>reverse_iterator::d00_typ

Typ, który zapewnia różnicę `reverse_iterator`między dwoma s odnoszących się do elementów w tym samym kontenerze.

```cpp
typedef typename iterator_traits<RandomIterator>::difference_type  difference_type;
```

### <a name="remarks"></a>Uwagi

Typ `reverse_iterator` różnicy jest taki sam jak typ różnicy iteratora.

Typ jest synonimem typu traerator `iterator_traits` \< **randomiterator**> **::pointer**.

### <a name="example"></a>Przykład

Zobacz [reverse_iterator::operator&#91;&#93;](#op_at) na przykład jak zadeklarować i `difference_type`używać .

## <a name="reverse_iteratoriterator_type"></a><a name="iterator_type"></a>reverse_iterator::iterator_type

Typ, który zapewnia podstawowe iteratora dla `reverse_iterator`.

```cpp
typedef RandomIterator iterator_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem parametru `Iterator`szablonu .

### <a name="example"></a>Przykład

Zobacz [reverse_iterator::base,](#base) aby uzyskać przykład sposobu deklarowania i używania `iterator_type`.

## <a name="reverse_iteratoroperator"></a><a name="op_star"></a>reverse_iterator::operator\*

Zwraca element, który adresuje reverse_iterator.

```cpp
reference operator*() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość elementów, do którego odnosi się reverse_iterator.

### <a name="remarks"></a>Uwagi

Operator zwraca \*( **bieżący** - 1).

### <a name="example"></a>Przykład

```cpp
// reverse_iterator_op_ref.cpp
// compile with: /EHsc
#include <iterator>
#include <algorithm>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   vector<int> vec;
   for (i = 1 ; i < 6 ; ++i )
   {
      vec.push_back ( 2 * i );
   }

   vector <int>::iterator vIter;
   cout << "The vector vec is: ( ";
   for ( vIter = vec.begin ( ) ; vIter != vec.end ( ); vIter++ )
      cout << *vIter << " ";
   cout << ")." << endl;

   vector <int>::reverse_iterator rvIter;
   cout << "The vector vec reversed is: ( ";
   for ( rvIter = vec.rbegin( ) ; rvIter != vec.rend( ); rvIter++)
      cout << *rvIter << " ";
   cout << ")." << endl;

   vector <int>::iterator pos, bpos;
   pos = find ( vec.begin ( ), vec.end ( ), 6 );

   // Declare a difference type for a parameter
   // declare a reference return type
   reverse_iterator<vector<int>::iterator>::reference refpos = *pos;
   cout << "The iterator pos points to: " << refpos << "." << endl;
}
```

## <a name="reverse_iteratoroperator"></a><a name="op_add"></a>reverse_iterator::operator+

Dodaje przesunięcie do iteratora i `reverse_iterator` zwraca nowy adresowanie wstawionego elementu w nowym położeniu odsunięcia.

```cpp
reverse_iterator<RandomIterator> operator+(difference_type Off) const;
```

### <a name="parameters"></a>Parametry

*Wył.*\
Przesunięcie, które ma zostać dodane do odwrotnej iteratora.

### <a name="return-value"></a>Wartość zwracana

Adresowanie `reverse_iterator` elementu odsunięcia.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego może `reverse_iterator` być używana tylko wtedy, gdy spełnia wymagania dla iteratora dostępu losowego.

### <a name="example"></a>Przykład

```cpp
// reverse_iterator_op_add.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   vector<int> vec;
   for (i = 1 ; i < 6 ; ++i )
   {
      vec.push_back ( 2 * i );
   }

   vector <int>::iterator vIter;
   cout << "The vector vec is: ( ";
   for ( vIter = vec.begin( ) ; vIter != vec.end( ); vIter++)
      cout << *vIter << " ";
   cout << ")." << endl;

   vector <int>::reverse_iterator rvIter;
   cout << "The vector vec reversed is: ( ";
   for ( rvIter = vec.rbegin( ) ; rvIter != vec.rend( ); rvIter++)
      cout << *rvIter << " ";
   cout << ")." << endl;

   // Initializing reverse_iterators to the first element
   vector <int>::reverse_iterator rVPOS1 = vec.rbegin ( );

   cout << "The iterator rVPOS1 initially points to the first "
        << "element\n in the reversed sequence: "
        << *rVPOS1 << "." << endl;

   vector <int>::reverse_iterator rVPOS2 =rVPOS1 + 2; // offset added
   cout << "After the +2 offset, the iterator rVPOS2 points\n"
        << " to the 3rd element in the reversed sequence: "
        << *rVPOS2 << "." << endl;
}
```

```Output
The vector vec is: ( 2 4 6 8 10 ).
The vector vec reversed is: ( 10 8 6 4 2 ).
The iterator rVPOS1 initially points to the first element
in the reversed sequence: 10.
After the +2 offset, the iterator rVPOS2 points
to the 3rd element in the reversed sequence: 6.
```

## <a name="reverse_iteratoroperator"></a><a name="op_add_add"></a>reverse_iterator::operator++

Zwiększa reverse_iterator do poprzedniego elementu.

```cpp
reverse_iterator<RandomIterator>& operator++();
reverse_iterator<RandomIterator> operator++(int);
```

### <a name="return-value"></a>Wartość zwracana

Pierwszy operator zwraca wstępnie z `reverse_iterator` góry, a drugi, operator postincrement, zwraca kopię `reverse_iterator`przyrostu .

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego może `reverse_iterator` być używana tylko wtedy, gdy spełnia wymagania dla iteratora dwukierunkowego.

### <a name="example"></a>Przykład

```cpp
// reverse_iterator_op_incr.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   vector<int> vec;
   for ( i = 1 ; i < 6 ; ++i )
   {
      vec.push_back ( 2 * i - 1 );
   }

   vector <int>::iterator vIter;
   cout << "The vector vec is: ( ";
   for ( vIter = vec.begin( ) ; vIter != vec.end( ); vIter++)
      cout << *vIter << " ";
   cout << ")." << endl;

   vector <int>::reverse_iterator rvIter;
   cout << "The vector vec reversed is: ( ";
   for ( rvIter = vec.rbegin( ) ; rvIter != vec.rend( ); rvIter++)
      cout << *rvIter << " ";
   cout << ")." << endl;

   // Initializing reverse_iterators to the last element
   vector <int>::reverse_iterator rVPOS1 = vec.rbegin( );

   cout << "The iterator rVPOS1 initially points to the first "
        << "element\n in the reversed sequence: "
        << *rVPOS1 << "." << endl;

   rVPOS1++;  // postincrement, preincrement: ++rVPSO1

   cout << "After incrementing, the iterator rVPOS1 points\n"
        << " to the second element in the reversed sequence: "
        << *rVPOS1 << "." << endl;
}
```

```Output
The vector vec is: ( 1 3 5 7 9 ).
The vector vec reversed is: ( 9 7 5 3 1 ).
The iterator rVPOS1 initially points to the first element
in the reversed sequence: 9.
After incrementing, the iterator rVPOS1 points
to the second element in the reversed sequence: 7.
```

## <a name="reverse_iteratoroperator"></a><a name="op_add_eq"></a>reverse_iterator::operator+=

Dodaje określone przesunięcie z reverse_iterator.

```cpp
reverse_iterator<RandomIterator>& operator+=(difference_type Off);
```

### <a name="parameters"></a>Parametry

*Wył.*\
Przesunięcie, o które należy zwiększać iteratora.

### <a name="return-value"></a>Wartość zwracana

Odwołanie do elementu, do `reverse_iterator`którego odnosi się .

### <a name="example"></a>Przykład

```cpp
// reverse_iterator_op_addoff.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   vector<int> vec;
   for (i = 1 ; i < 6 ; ++i )
   {
      vec.push_back ( 2 * i );
   }

   vector <int>::iterator vIter;

   cout << "The vector vec is: ( ";
   for ( vIter = vec.begin( ) ; vIter != vec.end( ); vIter++)
      cout << *vIter << " ";
   cout << ")." << endl;

   vector <int>::reverse_iterator rvIter;
   cout << "The vector vec reversed is: ( ";
   for ( rvIter = vec.rbegin( ) ; rvIter != vec.rend( ); rvIter++)
      cout << *rvIter << " ";
   cout << ")." << endl;

   // Initializing reverse_iterators to the last element
   vector <int>::reverse_iterator rVPOS1 = vec.rbegin ( );

   cout << "The iterator rVPOS1 initially points to the first "
        << "element\n in the reversed sequence: "
        << *rVPOS1 << "." << endl;

   rVPOS1+=2;   // addition of an offset
   cout << "After the +2 offset, the iterator rVPOS1 now points\n"
        << " to the third element in the reversed sequence: "
        << *rVPOS1 << "." << endl;
}
```

```Output
The vector vec is: ( 2 4 6 8 10 ).
The vector vec reversed is: ( 10 8 6 4 2 ).
The iterator rVPOS1 initially points to the first element
in the reversed sequence: 10.
After the +2 offset, the iterator rVPOS1 now points
to the third element in the reversed sequence: 6.
```

## <a name="reverse_iteratoroperator-"></a><a name="operator-"></a>reverse_iterator::operator-

Odejmuje odsunięcie od a `reverse_iterator` i zwraca `reverse_iterator` adresowanie elementu w pozycji odsunięcia.

```cpp
reverse_iterator<RandomIterator> operator-(difference_type Off) const;
```

### <a name="parameters"></a>Parametry

*Wył.*\
Odsunięcie do odjęcia od reverse_iterator.

### <a name="return-value"></a>Wartość zwracana

Adresowanie `reverse_iterator` elementu odsunięcia.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego może `reverse_iterator` być używana tylko wtedy, gdy spełnia wymagania dla iteratora dostępu losowego.

### <a name="example"></a>Przykład

```cpp
// reverse_iterator_op_sub.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   vector<int> vec;
   for ( i = 1 ; i < 6 ; ++i )
   {
      vec.push_back ( 3 * i );
   }

   vector <int>::iterator vIter;

   cout << "The vector vec is: ( ";
   for ( vIter = vec.begin( ) ; vIter != vec.end( ); vIter++)
      cout << *vIter << " ";
   cout << ")." << endl;

   vector <int>::reverse_iterator rvIter;
   cout << "The vector vec reversed is: ( ";
   for ( rvIter = vec.rbegin( ) ; rvIter != vec.rend( ); rvIter++)
      cout << *rvIter << " ";
   cout << ")." << endl;

   // Initializing reverse_iterators to the first element
   vector <int>::reverse_iterator rVPOS1 = vec.rend ( ) - 1;

   cout << "The iterator rVPOS1 initially points to the last "
        << "element\n in the reversed sequence: "
        << *rVPOS1 << "." << endl;

   vector <int>::reverse_iterator rVPOS2 =rVPOS1 - 2; // offset subtracted
   cout << "After the -2 offset, the iterator rVPOS2 points\n"
        << " to the 2nd element from the last in the reversed sequence: "
        << *rVPOS2 << "." << endl;
}
```

```Output
The vector vec is: ( 3 6 9 12 15 ).
The vector vec reversed is: ( 15 12 9 6 3 ).
The iterator rVPOS1 initially points to the last element
in the reversed sequence: 3.
After the -2 offset, the iterator rVPOS2 points
to the 2nd element from the last in the reversed sequence: 9.
```

## <a name="reverse_iteratoroperator--"></a><a name="operator--"></a>reverse_iterator::operator--

Zmniejsza reverse_iterator do poprzedniego elementu.

```cpp
reverse_iterator<RandomIterator>& operator--();
reverse_iterator<RandomIterator> operator--(int);
```

### <a name="return-value"></a>Wartość zwracana

Pierwszy operator zwraca wstępnie zdekralizowanym, `reverse_iterator` a drugi operator postdekreacji zwraca `reverse_iterator`kopię zdemprokowanego .

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego może `reverse_iterator` być używana tylko wtedy, gdy spełnia wymagania dla iteratora dwukierunkowego.

### <a name="example"></a>Przykład

```cpp
// reverse_iterator_op_decr.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   vector<int> vec;
   for (i = 1 ; i < 6 ; ++i )
   {
      vec.push_back ( 2 * i - 1 );
   }

   vector <int>::iterator vIter;

   cout << "The vector vec is: ( ";
   for ( vIter = vec.begin( ) ; vIter != vec.end( ); vIter++)
      cout << *vIter << " ";
   cout << ")." << endl;

   vector <int>::reverse_iterator rvIter;
   cout << "The vector vec reversed is: ( ";
   for ( rvIter = vec.rbegin( ) ; rvIter != vec.rend( ); rvIter++)
      cout << *rvIter << " ";
   cout << ")." << endl;

   // Initializing reverse_iterators to the first element
   vector <int>::reverse_iterator rVPOS1 = vec.rend ( ) - 1;

   cout << "The iterator rVPOS1 initially points to the last "
        << "element\n in the reversed sequence: "
        << *rVPOS1 << "." << endl;
   rVPOS1--;  // postdecrement, predecrement: --rVPSO1

   cout << "After the decrement, the iterator rVPOS1 points\n"
        << " to the next-to-last element in the reversed sequence: "
        << *rVPOS1 << "." << endl;
}
```

```Output
The vector vec is: ( 1 3 5 7 9 ).
The vector vec reversed is: ( 9 7 5 3 1 ).
The iterator rVPOS1 initially points to the last element
in the reversed sequence: 1.
After the decrement, the iterator rVPOS1 points
to the next-to-last element in the reversed sequence: 3.
```

## <a name="reverse_iteratoroperator-"></a><a name="operator-_eq"></a>reverse_iterator::operator-=

Odejmuje określone przesunięcie `reverse_iterator`od .

```cpp
reverse_iterator<RandomIterator>& operator-=(difference_type Off);
```

### <a name="parameters"></a>Parametry

*Wył.*\
Odsunięcie do odjęcia od . `reverse_iterator`

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego może `reverse_iterator` być używana tylko wtedy, gdy spełnia wymagania dla iteratora dostępu losowego.

Operator ocenia **bieżące** + *Wyłączone,* a następnie zwraca ** \*ten**.

### <a name="example"></a>Przykład

```cpp
// reverse_iterator_op_suboff.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   vector<int> vec;
   for (i = 1 ; i < 6 ; ++i )
   {
      vec.push_back ( 3 * i );
   }

   vector <int>::iterator vIter;

   cout << "The vector vec is: ( ";
   for ( vIter = vec.begin( ) ; vIter != vec.end( ); vIter++)
      cout << *vIter << " ";
   cout << ")." << endl;

   vector <int>::reverse_iterator rvIter;
   cout << "The vector vec reversed is: ( ";
   for ( rvIter = vec.rbegin( ) ; rvIter != vec.rend( ); rvIter++)
      cout << *rvIter << " ";
   cout << ")." << endl;

   // Initializing reverse_iterators to the first element
   vector <int>::reverse_iterator rVPOS1 = vec.rend ( ) - 1;

   cout << "The iterator rVPOS1 initially points to the last "
        << "element\n in the reversed sequence: "
        << *rVPOS1 << "." << endl;

   rVPOS1-=2;      // Subtraction of an offset
   cout << "After the -2 offset, the iterator rVPOS1 now points\n"
        << " to the 2nd element from the last in the reversed sequence: "
        << *rVPOS1 << "." << endl;
}
```

```Output
The vector vec is: ( 3 6 9 12 15 ).
The vector vec reversed is: ( 15 12 9 6 3 ).
The iterator rVPOS1 initially points to the last element
in the reversed sequence: 3.
After the -2 offset, the iterator rVPOS1 now points
to the 2nd element from the last in the reversed sequence: 9.
```

## <a name="reverse_iteratoroperator-gt"></a><a name="op-arrow"></a>reverse_iterator::operator-&gt;

Zwraca wskaźnik do elementu adresowane przez `reverse_iterator`.

```cpp
pointer operator->() const;
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do elementu adresowane `reverse_iterator`przez .

### <a name="remarks"></a>Uwagi

Operator zwraca ** & \* \*to**.

### <a name="example"></a>Przykład

```cpp
// reverse_iterator_ptrto.cpp
// compile with: /EHsc
#include <iterator>
#include <algorithm>
#include <vector>
#include <utility>
#include <iostream>

int main( )
{
   using namespace std;

   typedef vector<pair<int,int> > pVector;
   pVector vec;
   vec.push_back(pVector::value_type(1,2));
   vec.push_back(pVector::value_type(3,4));
   vec.push_back(pVector::value_type(5,6));

   pVector::iterator pvIter;
   cout << "The vector vec of integer pairs is:\n( ";
   for ( pvIter = vec.begin ( ) ; pvIter != vec.end ( ); pvIter++)
      cout << "( " << pvIter -> first << ", " << pvIter -> second << ") ";
   cout << ")" << endl << endl;

   pVector::reverse_iterator rpvIter;
   cout << "The vector vec reversed is:\n( ";
   for ( rpvIter = vec.rbegin( ) ; rpvIter != vec.rend( ); rpvIter++ )
      cout << "( " << rpvIter -> first << ", " << rpvIter -> second << ") ";
   cout << ")" << endl << endl;

   pVector::iterator pos = vec.begin ( );
   pos++;
   cout << "The iterator pos points to:\n( " << pos -> first << ", "
   << pos -> second << " )" << endl << endl;

   pVector::reverse_iterator rpos (pos);

   // Use operator -> with return type: why type int and not int*
   int fint = rpos -> first;
   int sint = rpos -> second;

   cout << "The reverse_iterator rpos points to:\n( " << fint << ", "
   << sint << " )" << endl;
}
```

```Output
The vector vec of integer pairs is:
( ( 1, 2) ( 3, 4) ( 5, 6) )

The vector vec reversed is:
( ( 5, 6) ( 3, 4) ( 1, 2) )

The iterator pos points to:
( 3, 4 )

The reverse_iterator rpos points to:
( 1, 2 )
```

## <a name="reverse_iteratoroperator"></a><a name="op_at"></a>reverse_iterator::operator[]

Zwraca odwołanie do elementu odsuniętego `reverse_iterator` od elementu adresowane przez określoną liczbę pozycji.

```cpp
reference operator[](difference_type Off) const;
```

### <a name="parameters"></a>Parametry

*Wył.*\
Przesunięcie od `reverse_iterator` adresu.

### <a name="return-value"></a>Wartość zwracana

Odwołanie do odsunięcia elementu.

### <a name="remarks"></a>Uwagi

Operator zwraca <strong>\*</strong> ** \*(to** + `Off`).

### <a name="example"></a>Przykład

```cpp
// reverse_iterator_ret_ref.cpp
// compile with: /EHsc
#include <iterator>
#include <algorithm>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   vector<int> vec;
   for (i = 1 ; i < 6 ; ++i )
   {
      vec.push_back ( 2 * i );
   }

   vector <int>::iterator vIter;
   cout << "The vector vec is: ( ";
   for ( vIter = vec.begin ( ) ; vIter != vec.end ( ); vIter++ )
      cout << *vIter << " ";
   cout << ")." << endl;

   vector <int>::reverse_iterator rvIter;
   cout << "The vector vec reversed is: ( ";
   for ( rvIter = vec.rbegin( ) ; rvIter != vec.rend( ); rvIter++)
      cout << *rvIter << " ";
   cout << ")." << endl;

   vector <int>::iterator pos;
   pos = find ( vec.begin ( ), vec.end ( ), 8 );
   reverse_iterator<vector<int>::iterator> rpos ( pos );

   // Declare a difference type for a parameter
   reverse_iterator<vector<int>::iterator>::difference_type diff = 2;

   cout << "The iterator pos points to: " << *pos << "." << endl;
   cout << "The iterator rpos points to: " << *rpos << "." << endl;

   // Declare a reference return type & use operator[]
   reverse_iterator<vector<int>::iterator>::reference refrpos = rpos [diff];
   cout << "The iterator rpos now points to: " << refrpos << "." << endl;
}
```

```Output
The vector vec is: ( 2 4 6 8 10 ).
The vector vec reversed is: ( 10 8 6 4 2 ).
The iterator pos points to: 8.
The iterator rpos points to: 6.
The iterator rpos now points to: 2.
```

## <a name="reverse_iteratorpointer"></a><a name="pointer"></a>reverse_iterator::pointer

Typ, który zapewnia wskaźnik do elementu `reverse_iterator`skierowanego przez .

```cpp
typedef typename iterator_traits<RandomIterator>::pointer pointer;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem typu traerator `iterator_traits` \< *randomiterator*> **::pointer**.

### <a name="example"></a>Przykład

```cpp
// reverse_iterator_pointer.cpp
// compile with: /EHsc
#include <iterator>
#include <algorithm>
#include <vector>
#include <utility>
#include <iostream>

int main( )
{
   using namespace std;

   typedef vector<pair<int,int> > pVector;
   pVector vec;
   vec.push_back( pVector::value_type( 1,2 ) );
   vec.push_back( pVector::value_type( 3,4 ) );
   vec.push_back( pVector::value_type( 5,6 ) );

   pVector::iterator pvIter;
   cout << "The vector vec of integer pairs is:\n" << "( ";
   for ( pvIter = vec.begin ( ) ; pvIter != vec.end ( ); pvIter++)
      cout << "( " << pvIter -> first << ", " << pvIter -> second << ") ";
   cout << ")" << endl;

   pVector::reverse_iterator rpvIter;
   cout << "\nThe vector vec reversed is:\n" << "( ";
   for ( rpvIter = vec.rbegin( ) ; rpvIter != vec.rend( ); rpvIter++)
      cout << "( " << rpvIter -> first << ", " << rpvIter -> second << ") ";
   cout << ")" << endl;

   pVector::iterator pos = vec.begin ( );
   pos++;
   cout << "\nThe iterator pos points to:\n"
        << "( " << pos -> first << ", "
        << pos -> second << " )" << endl;

   pVector::reverse_iterator rpos (pos);
   cout << "\nThe iterator rpos points to:\n"
        << "( " << rpos -> first << ", "
        << rpos -> second << " )" << endl;
}
```

```Output
The vector vec of integer pairs is:
( ( 1, 2) ( 3, 4) ( 5, 6) )

The vector vec reversed is:
( ( 5, 6) ( 3, 4) ( 1, 2) )

The iterator pos points to:
( 3, 4 )

The iterator rpos points to:
( 1, 2 )
```

## <a name="reverse_iteratorreference"></a><a name="reference"></a>reverse_iterator::odwołanie

Typ, który zawiera odwołanie do elementu adresowane przez reverse_iterator.

```cpp
typedef typename iterator_traits<RandomIterator>::reference reference;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem typu traeratora `iterator_traits` \< *RandomIterator*> **::reference**.

### <a name="example"></a>Przykład

Zobacz [reverse_iterator::operator&#91;&#93;](#op_at) lub [reverse_iterator:operator*,](#op_star) aby zapoznać się z przykładami `reference`sposobu deklarowania i używania pliku .

## <a name="reverse_iteratorreverse_iterator"></a><a name="reverse_iterator"></a>reverse_iterator::reverse_iterator

Tworzy domyślne `reverse_iterator` lub `reverse_iterator` z podstawowego iteratora.

```cpp
reverse_iterator();
explicit reverse_iterator(RandomIterator right);

template <class Type>
reverse_iterator(const reverse_iterator<Type>& right);
```

### <a name="parameters"></a>Parametry

*Prawo*\
Iterator, który ma być dostosowany do `reverse_iterator`.

### <a name="return-value"></a>Wartość zwracana

Domyślny `reverse_iterator` `reverse_iterator` lub dostosowujący się do podstawowego iteratora.

### <a name="remarks"></a>Uwagi

Tożsamość, która odnosi wszystkie iteratory odwrócone do ich iteratorów podstawowych, to:

&\*( `reverse_iterator` ( *i* ) ) == &\*( *i* - 1 ).

W praktyce oznacza to, że w odwróconej sekwencji reverse_iterator będzie się odnosił do elementu w jednej pozycji poza elementem (z jego prawej strony), do którego odnosił się iterator w oryginalnej sekwencji. Więc jeśli iterator skierowana element 6 w sekwencji (2, 4, `reverse_iterator` 6, 8), a następnie będzie adres elementu 4 w odwróconej sekwencji (8, 6, 4, 2).

### <a name="example"></a>Przykład

```cpp
// reverse_iterator_reverse_iterator.cpp
// compile with: /EHsc
#include <iterator>
#include <algorithm>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   vector<int> vec;
   for ( i = 1 ; i < 6 ; ++i )
   {
      vec.push_back ( i );
   }

   vector <int>::iterator vIter;
   cout << "The vector vec is: ( ";
   for ( vIter = vec.begin ( ) ; vIter != vec.end ( ); vIter++)
      cout << *vIter << " ";
   cout << ")." << endl;

   vector <int>::reverse_iterator rvIter;
   cout << "The vector vec reversed is: ( ";
   for ( rvIter = vec.rbegin( ) ; rvIter != vec.rend( ); rvIter++)
      cout << *rvIter << " ";
   cout << ")." << endl;

   vector <int>::iterator pos;
   pos = find ( vec.begin ( ), vec.end ( ), 4 );
   cout << "The iterator pos = " << *pos << "." << endl;

   vector <int>::reverse_iterator rpos ( pos );
   cout << "The reverse_iterator rpos = " << *rpos
        << "." << endl;
}
```

## <a name="see-also"></a>Zobacz też

[\<>iteratora](../standard-library/iterator.md)\
[Bezpieczeństwo gwintów w standardowej bibliotece języka C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Odwołanie do standardowej biblioteki języka C++](../standard-library/cpp-standard-library-reference.md)
