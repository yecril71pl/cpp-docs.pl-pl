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
ms.openlocfilehash: aadc5cffd6f88de175ff04f50d6572e38ba05533
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/21/2019
ms.locfileid: "72686585"
---
# <a name="reverse_iterator-class"></a>reverse_iterator — Klasa

Szablon klasy jest adapterem iteratora opisującym obiekt iteratora odwrotnego, który zachowuje się jak Iterator dostępu swobodnego lub dwukierunkowego, tylko w odwrotnej postaci. Umożliwia przechodzenie do tyłu zakresu.

## <a name="syntax"></a>Składnia

```cpp
template <class RandomIterator>
class reverse_iterator
```

### <a name="parameters"></a>Parametry

RandomIterator typ reprezentujący iterator, który ma zostać dostosowany do działania w odwrotnej postaci.

## <a name="remarks"></a>Uwagi

Istniejące C++ Kontenery biblioteki standardowej również definiują `reverse_iterator` i typy `const_reverse_iterator` i mają funkcje członkowskie `rbegin` i `rend`, które zwracają Iteratory zwrotne. Te iteratory mają semantykę nadpisywania. @No__t_0 adapter uzupełnia tę funkcję, ponieważ oferuje semantykę wstawiania i może być również używany z strumieniami.

@No__t_0, które wymaga iteratora dwukierunkowego, nie może wywołać żadnej z funkcji składowych `operator+=`, `operator+`, `operator-=`, `operator-` ani `operator[]`, które mogą być używane tylko z iteratorami dostępu swobodnego.

Zakres iteratora to [*First*, *Last*), gdzie kwadratowy nawias po lewej stronie wskazuje, że dołączenie *pierwszego* i nawiasu po prawej stronie wskazuje na włączenie elementów do, ale z wyłączeniem *ostatniego* . Te same elementy są zawarte w odwróconej sekwencji [ **rev**  - *first*, **Rev**  - *Last*), tak aby w przypadku, gdy *ostatni* jest elementem typu "jeden do końca" w sekwencji, a następnie pierwszy element **Rev**  -  *najpierw* w odwróconych punktach sekwencji do 0 (*ostatni* -1). Tożsamość, która odnosi wszystkie iteratory odwrócone do ich iteratorów podstawowych, to:

& \* ( **reverse_iterator** ( *i* )) = = & \* ( *i* -1).

W praktyce oznacza to, że w odwróconej sekwencji reverse_iterator będzie się odnosił do elementu w jednej pozycji poza elementem (z jego prawej strony), do którego odnosił się iterator w oryginalnej sekwencji. Dlatego jeśli iterator odnosił się do elementu 6 w sekwencji (2, 4, 6, 8), wówczas `reverse_iterator` będzie odnosił się do elementu 4 w odwróconej sekwencji (8, 6, 4, 2).

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[reverse_iterator](#reverse_iterator)|Konstruuje domyślną `reverse_iterator` lub `reverse_iterator` z iteratora podstawowego.|

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[difference_type](#difference_type)|Typ, który zawiera różnicę między dwoma `reverse_iterator`s odwołującymi się do elementów w tym samym kontenerze.|
|[iterator_type](#iterator_type)|Typ, który dostarcza podstawowy iterator dla `reverse_iterator`.|
|[przytrzymaj](#pointer)|Typ, który dostarcza wskaźnik do elementu, do którego odnosi się `reverse_iterator`.|
|[odwoła](#reference)|Typ, który zawiera odwołanie do elementu, do którego odnosi się `reverse_iterator`.|

### <a name="member-functions"></a>Funkcje członkowskie

|Funkcja członkowska|Opis|
|-|-|
|[base](#base)|Odzyskuje podstawowy iterator z jego `reverse_iterator`.|

### <a name="operators"></a>Operatory

|Operator|Opis|
|-|-|
|[operator_star](#op_star)|Zwraca element, który `reverse_iterator` adresów.|
|[operator +](#op_add)|Dodaje przesunięcie do iteratora i zwraca nowy `reverse_iterator` odnoszący się do wstawionego elementu w nowym położeniu przesunięcia.|
|[operator + +](#op_add_add)|Zwiększa `reverse_iterator` do następnego elementu.|
|[operator + =](#op_add_eq)|Dodaje określone przesunięcie z `reverse_iterator`.|
|[zakład](#operator-)|Odejmuje przesunięcie od `reverse_iterator` i zwraca `reverse_iterator` odnoszące się do elementu w pozycji przesunięcia.|
|[operator--](#operator--)|Zmniejsza `reverse_iterator` do poprzedniego elementu.|
|[operator-=](#operator-_eq)|Odejmuje określone przesunięcie z `reverse_iterator`.|
|[operator — >](#op-arrow)|Zwraca wskaźnik do elementu, do którego odnosi się `reverse_iterator`.|
|[zakład&#91;&#93;](#op_at)|Zwraca odwołanie do przesunięcia elementu z elementu, do którego odnosi się `reverse_iterator` przez określoną liczbę pozycji.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<iterator >

**Przestrzeń nazw:** std

## <a name="base"></a>reverse_iterator:: Base

Odzyskuje podstawowy iterator z jego `reverse_iterator`.

```cpp
RandomIterator base() const;
```

### <a name="return-value"></a>Wartość zwracana

Iterator bazowy `reverse_iterator`.

### <a name="remarks"></a>Uwagi

Tożsamość, która wiąże wszystkie Iteratory odwrotne do ich iteratorów podstawowych, to:

& \* (`reverse_iterator` ( *i* )) = = & \* ( *i* -1).

W tym przypadku oznacza to, że w odwróconej sekwencji `reverse_iterator` będzie odnosić się do elementu w jednej pozycji poza (z prawej strony) elementu, do którego odnosił się iterator w oryginalnej sekwencji. Dlatego jeśli iterator odnosił się do elementu 6 w sekwencji (2, 4, 6, 8), wówczas `reverse_iterator` będzie odnosił się do elementu 4 w odwróconej sekwencji (8, 6, 4, 2).

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

## <a name="difference_type"></a>reverse_iterator::d ifference_type

Typ, który zawiera różnicę między dwoma `reverse_iterator`s odwołującymi się do elementów w tym samym kontenerze.

```cpp
typedef typename iterator_traits<RandomIterator>::difference_type  difference_type;
```

### <a name="remarks"></a>Uwagi

Typ różnicy `reverse_iterator` jest taki sam jak typ różnicy iteratora.

Typ jest synonimem dla elementu TypeName cech `iterator_traits` \< **RandomIterator** >  **::p ointer**.

### <a name="example"></a>Przykład

Zobacz [reverse_iterator:: operator&#91; ](#op_at) , aby zapoznać się z przykładem sposobu deklarowania i używania `difference_type`.

## <a name="iterator_type"></a>reverse_iterator::iterator_type

Typ, który dostarcza podstawowy iterator dla `reverse_iterator`.

```cpp
typedef RandomIterator iterator_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla parametru szablonu `Iterator`.

### <a name="example"></a>Przykład

Zobacz [reverse_iterator:: Base](#base) , aby zapoznać się z przykładem sposobu deklarowania i używania `iterator_type`.

## <a name="op_star"></a>reverse_iterator:: operator \*

Zwraca element, który jest adresem reverse_iterator.

```cpp
reference operator*() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość elementów, do których odnosi się reverse_iterator.

### <a name="remarks"></a>Uwagi

Operator zwraca \* ( **Current** -1).

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

## <a name="op_add"></a>reverse_iterator:: operator +

Dodaje przesunięcie do iteratora i zwraca nowy `reverse_iterator` odnoszący się do wstawionego elementu w nowym położeniu przesunięcia.

```cpp
reverse_iterator<RandomIterator> operator+(difference_type Off) const;
```

### <a name="parameters"></a>Parametry

*Wyłączone* \
Przesunięcie, które ma zostać dodane do iteratora odwrotnego.

### <a name="return-value"></a>Wartość zwracana

@No__t_0 odnoszący się do elementu przesunięcia.

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska może być używana tylko wtedy, gdy `reverse_iterator` spełnia wymagania iteratora dostępu swobodnego.

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

## <a name="op_add_add"></a>reverse_iterator:: operator + +

Zwiększa reverse_iterator do poprzedniego elementu.

```cpp
reverse_iterator<RandomIterator>& operator++();
reverse_iterator<RandomIterator> operator++(int);
```

### <a name="return-value"></a>Wartość zwracana

Pierwszy operator zwraca `reverse_iterator`, a drugi, operator postinkrementacji, zwraca kopię przyrostowego `reverse_iterator`.

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska może być używana tylko wtedy, gdy `reverse_iterator` spełnia wymagania dla iteratora dwukierunkowego.

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

## <a name="op_add_eq"></a>reverse_iterator:: operator + =

Dodaje określone przesunięcie z reverse_iterator.

```cpp
reverse_iterator<RandomIterator>& operator+=(difference_type Off);
```

### <a name="parameters"></a>Parametry

*Wyłączone* \
Przesunięcie, według którego ma zostać zwiększony iterator.

### <a name="return-value"></a>Wartość zwracana

Odwołanie do elementu, do którego odnosi się `reverse_iterator`.

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

## <a name="operator-"></a>reverse_iterator:: operator-

Odejmuje przesunięcie od `reverse_iterator` i zwraca `reverse_iterator` odnoszące się do elementu w pozycji przesunięcia.

```cpp
reverse_iterator<RandomIterator> operator-(difference_type Off) const;
```

### <a name="parameters"></a>Parametry

*Wyłączone* \
Przesunięcie, które ma zostać odjęte od reverse_iterator.

### <a name="return-value"></a>Wartość zwracana

@No__t_0 odnoszący się do elementu przesunięcia.

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska może być używana tylko wtedy, gdy `reverse_iterator` spełnia wymagania iteratora dostępu swobodnego.

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

## <a name="operator--"></a>reverse_iterator:: operator--

Zmniejsza reverse_iterator do poprzedniego elementu.

```cpp
reverse_iterator<RandomIterator>& operator--();
reverse_iterator<RandomIterator> operator--(int);
```

### <a name="return-value"></a>Wartość zwracana

Pierwszy operator zwraca `reverse_iterator`, a drugi, operator postdekrementacyjne, zwraca kopię `reverse_iterator` o zmniejszonej wartości.

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska może być używana tylko wtedy, gdy `reverse_iterator` spełnia wymagania dla iteratora dwukierunkowego.

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

## <a name="operator-_eq"></a>reverse_iterator:: operator-=

Odejmuje określone przesunięcie z `reverse_iterator`.

```cpp
reverse_iterator<RandomIterator>& operator-=(difference_type Off);
```

### <a name="parameters"></a>Parametry

*Wyłączone* \
Przesunięcie, które ma zostać odjęte od `reverse_iterator`.

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska może być używana tylko wtedy, gdy `reverse_iterator` spełnia wymagania iteratora dostępu swobodnego.

Operator oblicza wartość **Current** + _ *off*. następnie zwraca **\*this**.

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

## <a name="op-arrow"></a>reverse_iterator:: operator-&gt;

Zwraca wskaźnik do elementu, do którego odnosi się `reverse_iterator`.

```cpp
pointer operator->() const;
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do elementu, do którego odnosi się `reverse_iterator`.

### <a name="remarks"></a>Uwagi

Operator zwraca **& \* \*this**.

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

## <a name="op_at"></a>reverse_iterator:: operator []

Zwraca odwołanie do przesunięcia elementu z elementu, do którego odnosi się `reverse_iterator` przez określoną liczbę pozycji.

```cpp
reference operator[](difference_type Off) const;
```

### <a name="parameters"></a>Parametry

*Wyłączone* \
Przesunięcie od adresu `reverse_iterator`.

### <a name="return-value"></a>Wartość zwracana

Odwołanie do przesunięcia elementu.

### <a name="remarks"></a>Uwagi

Operator zwraca <strong>\*</strong>( **\*this**  +  `Off`).

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

## <a name="pointer"></a>reverse_iterator::p ointer

Typ, który dostarcza wskaźnik do elementu, do którego odnosi się `reverse_iterator`.

```cpp
typedef typename iterator_traits<RandomIterator>::pointer pointer;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla elementu TypeName cech `iterator_traits` \< *RandomIterator* >  **::p ointer**.

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

## <a name="reference"></a>reverse_iterator:: Reference

Typ, który zawiera odwołanie do elementu, do którego odnosi się reverse_iterator.

```cpp
typedef typename iterator_traits<RandomIterator>::reference reference;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla elementu TypeName cech `iterator_traits` \< *RandomIterator* >  **:: Reference**.

### <a name="example"></a>Przykład

Zobacz [reverse_iterator:: operator&#91; ](#op_at) lub [reverse_iterator:: operator *](#op_star) , aby zapoznać się z przykładami sposobu deklarowania i używania `reference`.

## <a name="reverse_iterator"></a>reverse_iterator::reverse_iterator

Konstruuje domyślną `reverse_iterator` lub `reverse_iterator` z iteratora podstawowego.

```cpp
reverse_iterator();
explicit reverse_iterator(RandomIterator right);

template <class Type>
reverse_iterator(const reverse_iterator<Type>& right);
```

### <a name="parameters"></a>Parametry

*prawa* \
Iterator, który ma zostać dostosowany do `reverse_iterator`.

### <a name="return-value"></a>Wartość zwracana

Domyślny `reverse_iterator` lub `reverse_iterator` dostosowujący podstawowy iterator.

### <a name="remarks"></a>Uwagi

Tożsamość, która odnosi wszystkie iteratory odwrócone do ich iteratorów podstawowych, to:

& \* (`reverse_iterator` ( *i* )) = = & \* ( *i* -1).

W praktyce oznacza to, że w odwróconej sekwencji reverse_iterator będzie się odnosił do elementu w jednej pozycji poza elementem (z jego prawej strony), do którego odnosił się iterator w oryginalnej sekwencji. Dlatego jeśli iterator odnosił się do elementu 6 w sekwencji (2, 4, 6, 8), wówczas `reverse_iterator` będzie odnosił się do elementu 4 w odwróconej sekwencji (8, 6, 4, 2).

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

## <a name="see-also"></a>Zobacz także

[\<iterator >](../standard-library/iterator.md) \
[Bezpieczeństwo wątku w C++ standardowej bibliotece](../standard-library/thread-safety-in-the-cpp-standard-library.md) \
[Dokumentacja standardowej biblioteki C++](../standard-library/cpp-standard-library-reference.md)
