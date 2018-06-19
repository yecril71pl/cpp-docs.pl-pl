---
title: '&lt;Iterator&gt; funkcje | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- xutility/std::advance
- xutility/std::back_inserter
- xutility/std::begin
- xutility/std::cbegin
- xutility/std::cend
- xutility/std::distance
- xutility/std::end
- xutility/std::front_inserter
- xutility/std::inserter
- xutility/std::make_checked_array_iterator
- xutility/std::make_move_iterator
- xutility/std::make_unchecked_array_iterator
- xutility/std::next
- xutility/std::prev
ms.assetid: 4a57c9a3-7e36-411f-8655-e0be2eec88e7
helpviewer_keywords:
- std::advance [C++]
- std::back_inserter [C++]
- std::begin [C++]
- std::cbegin [C++]
- std::cend [C++]
- std::distance [C++]
- std::end [C++]
- std::front_inserter [C++]
- std::inserter [C++]
- std::make_checked_array_iterator [C++]
- std::make_move_iterator [C++]
- std::make_unchecked_array_iterator [C++]
- std::next [C++]
- std::prev [C++]
ms.openlocfilehash: 965ff7aadb4add306061599bbe55466bbfb87f94
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33861821"
---
# <a name="ltiteratorgt-functions"></a>&lt;Iterator&gt; funkcji

||||
|-|-|-|
|[advance](#advance)|[back_inserter](#back_inserter)|[begin](#begin)|
|[cbegin](#cbegin)|[cend](#cend)|[odległość](#distance)|
|[Koniec](#end)|[front_inserter](#front_inserter)|[Wstawianie](#inserter)|
|[make_checked_array_iterator](#make_checked_array_iterator)|[make_move_iterator](#make_move_iterator)|[make_unchecked_array_iterator](#make_unchecked_array_iterator)|
|[next](#next)|[Poprzedni](#prev)|

## <a name="advance"></a>  ADVANCE

Inkrementuje iterator o określoną liczbę pozycji.

```cpp
template <class InputIterator, class Distance>
void advance(
    InputIterator& InIt,
    Distance Off);
```

### <a name="parameters"></a>Parametry

`InIt` Iterator, który ma być zwiększany, a które muszą spełniać wymagania dotyczące wejściowych iteratora.

`Off` Typ całkowity jest możliwe do przekonwertowania na typ różnica iteratora oraz określa liczbę zwiększa położenie iteratora jest zaawansowane.

### <a name="remarks"></a>Uwagi

Zakres zwiększania musi być niepojedynczy, a iteratory muszą być wyłuskiwalne lub znajdować się po końcu.

Jeśli **InputIterator** następnie spełnia wymagania dotyczące typu iteratora dwukierunkowego `Off` może być ujemna. Jeśli **InputIterator** jest typem danych wejściowych lub do przodu iteratora `Off` musi być nieujemna.

Funkcja wyprzedzeniem ma stałą złożoności podczas **InputIterator** spełnia wymagania dotyczące iteratora dostępie swobodnym; w przeciwnym razie ma złożoność liniowej i dlatego jest potencjalnie kosztowne.

### <a name="example"></a>Przykład

```cpp
// iterator_advance.cpp
// compile with: /EHsc
#include <iterator>
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   list<int> L;
   for ( i = 1 ; i < 9 ; ++i )
   {
      L.push_back ( i );
   }
   list <int>::iterator L_Iter, LPOS = L.begin ( );

   cout << "The list L is: ( ";
   for ( L_Iter = L.begin( ) ; L_Iter != L.end( ); L_Iter++)
      cout << *L_Iter << " ";
   cout << ")." << endl;

   cout << "The iterator LPOS initially points to the first element: "
        << *LPOS << "." << endl;

   advance ( LPOS , 4 );
   cout << "LPOS is advanced 4 steps forward to point"
        << " to the fifth element: "
        << *LPOS << "." << endl;

   advance ( LPOS , -3 );
   cout << "LPOS is moved 3 steps back to point to the "
        << "2nd element: " << *LPOS << "." << endl;
}
```

```Output
The list L is: ( 1 2 3 4 5 6 7 8 ).
The iterator LPOS initially points to the first element: 1.
LPOS is advanced 4 steps forward to point to the fifth element: 5.
LPOS is moved 3 steps back to point to the 2nd element: 2.
```

## <a name="back_inserter"></a>  back_inserter

Tworzy iterator, który może wstawiać elementy z tyłu określonego kontenera.

```cpp
template <class Container>
back_insert_iterator<Container> back_inserter(Container& _Cont);
```

### <a name="parameters"></a>Parametry

`_Cont` Kontener, do którego ma zostać wykonana wstecz wstawiania.

### <a name="return-value"></a>Wartość zwracana

A `back_insert_iterator` skojarzony z obiektem kontenera `_Cont`.

### <a name="remarks"></a>Uwagi

W standardowej bibliotece C++ argument musi odwoływać się do jednego z kontenerów trzy sekwencji, których funkcji członkowskiej `push_back`: [deque — klasa](../standard-library/deque-class.md), [list — klasa](../standard-library/list-class.md), lub [wektora Klasa](../standard-library/vector-class.md).

### <a name="example"></a>Przykład

```cpp
// iterator_back_inserter.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   vector<int> vec;
   for ( i = 0 ; i < 3 ; ++i )
   {
      vec.push_back ( i );
   }

   vector <int>::iterator vIter;
   cout << "The initial vector vec is: ( ";
   for ( vIter = vec.begin ( ) ; vIter != vec.end ( ); vIter++)
      cout << *vIter << " ";
   cout << ")." << endl;

   // Insertions can be done with template function
   back_insert_iterator<vector<int> > backiter ( vec );
 *backiter = 30;
   backiter++;
 *backiter = 40;

   // Alternatively, insertions can be done with the
   // back_insert_iterator member function
   back_inserter ( vec ) = 500;
   back_inserter ( vec ) = 600;

   cout << "After the insertions, the vector vec is: ( ";
   for ( vIter = vec.begin ( ) ; vIter != vec.end ( ); vIter++ )
      cout << *vIter << " ";
   cout << ")." << endl;
}
```

```Output
The initial vector vec is: ( 0 1 2 ).
After the insertions, the vector vec is: ( 0 1 2 30 40 500 600 ).
```

## <a name="begin"></a>  Rozpocznij

Pobiera iterator do pierwszego elementu w określonym kontenerze.

```cpp
template <class Container>
auto begin(Container& cont)  `
   -> decltype(cont.begin());

template <class Container>
auto begin(const Container& cont)   `
   -> decltype(cont.begin());

template <class Ty, class Size>
Ty *begin(Ty (& array)[Size]);
```

### <a name="parameters"></a>Parametry

`cont` Kontener.

`array` Tablica obiektów typu `Ty`.

### <a name="return-value"></a>Wartość zwracana

Zwraca pierwszy funkcje dwóch szablonów `cont.begin()`. Pierwsza funkcja jest niestała; druga jest stała.

Zwraca trzecie funkcji szablonu `array`.

### <a name="example"></a>Przykład

Zalecane jest użycie tej funkcji szablonu zamiast członek kontenera `begin()` gdy wymagane jest zachowanie bardziej ogólnym.

```cpp
// cl.exe /EHsc /nologo /W4 /MTd
#include <algorithm>
#include <functional>
#include <iostream>
#include <iterator>
#include <vector>

template <typename C> void reverse_sort(C& c) {
    using std::begin;
    using std::end;

    std::sort(begin(c), end(c), std::greater<>());
}

template <typename C> void print(const C& c) {
    for (const auto& e : c) {
        std::cout << e << " ";
    }

    std::cout << "\n";
}

int main() {
    std::vector<int> v = { 11, 34, 17, 52, 26, 13, 40, 20, 10, 5, 16, 8, 4, 2, 1 };

    print(v);
    reverse_sort(v);
    print(v);

    std::cout << "--\n";

    int arr[] = { 23, 70, 35, 106, 53, 160, 80, 40, 20, 10, 5, 16, 8, 4, 2, 1 };

    print(arr);
    reverse_sort(arr);
    print(arr);
}
```

```Output
11 34 17 52 26 13 40 20 10 5 16 8 4 2 1
52 40 34 26 20 17 16 13 11 10 8 5 4 2 1
--
23 70 35 106 53 160 80 40 20 10 5 16 8 4 2 1
160 106 80 70 53 40 35 23 20 16 10 8 5 4 2 1
```

Funkcja `reverse_sort` obsługuje kontenery dowolnego rodzaju, oprócz regularne tablice, ponieważ wywołuje wersji niebędący elementem członkowskim `begin()`. Jeśli `reverse_sort` zostały zakodowane można używać elementu członkowskiego kontenera `begin()`:

```cpp
template <typename C>
void reverse_sort(C& c) {
    using std::begin;
    using std::end;

    std::sort(c.begin(), c.end(), std::greater<>());

}
```

Wówczas wysłanie do niego tablicy spowodowałoby następujący błąd kompilatora:

```Output
error C2228: left of '.begin' must have class/struct/union
```

## <a name="cbegin"></a>  cbegin

Pobiera iterator const do pierwszego elementu w określonym kontenerze.

```cpp
template <class Container>
auto cbegin(const Container& cont)
   -> decltype(cont.begin());
```

### <a name="parameters"></a>Parametry

`cont` Kontener lub initializer_list.

### <a name="return-value"></a>Wartość zwracana

Stała `cont.begin()`.

### <a name="remarks"></a>Uwagi

Ta funkcja działa z wszystkich kontenerów standardowa biblioteka C++ i [initializer_list](../standard-library/initializer-list-class.md).

Można użyć funkcji członkowskiej zamiast `begin()` funkcji szablonu, aby zagwarantować, że jest zwracana wartość `const_iterator`. Zazwyczaj jest używany w połączeniu z [automatycznie](../cpp/auto-cpp.md) wpisz słowo kluczowe wnioskowanie, jak pokazano w poniższym przykładzie. W tym przykładzie należy wziąć pod uwagę `Container` do można modyfikować (z systemem innym niż `const`) kontenera lub `initializer_list` dowolnego rodzaju, który obsługuje `begin()` i `cbegin()`.

```cpp
auto i1 = Container.begin();
// i1 is Container<T>::iterator
auto i2 = Container.cbegin();

// i2 is Container<T>::const_iterator
```

## <a name="cend"></a>  cend

Pobiera iterator const do elementu, który następuje po ostatnim elemencie w określonym kontenerze.

```cpp
template <class Container>
auto cend(const Container& cont)
   -> decltype(cont.end());
```

### <a name="parameters"></a>Parametry

`cont` Kontener lub initializer_list.

### <a name="return-value"></a>Wartość zwracana

Stała `cont.end()`.

### <a name="remarks"></a>Uwagi

Ta funkcja działa z wszystkich kontenerów standardowa biblioteka C++ i [initializer_list](../standard-library/initializer-list-class.md).

Można użyć funkcji członkowskiej zamiast [end()](../standard-library/iterator-functions.md#end) funkcji szablonu, aby zagwarantować, że jest zwracana wartość `const_iterator`. Zazwyczaj jest używany w połączeniu z [automatycznie](../cpp/auto-cpp.md) wpisz słowo kluczowe wnioskowanie, jak pokazano w poniższym przykładzie. W tym przykładzie należy wziąć pod uwagę `Container` do można modyfikować (z systemem innym niż `const`) kontenera lub `initializer_list` dowolnego rodzaju, który obsługuje `end()` i `cend()`.

```cpp
auto i1 = Container.end();
// i1 is Container<T>::iterator
auto i2 = Container.cend();

// i2 is Container<T>::const_iterator
```

## <a name="distance"></a>  odległość

Określa liczbę przyrostów między położeniami, do których odnoszą się dwa iteratory.

```cpp
template <class InputIterator>
typename iterator_traits<InputIterator>::difference_type distance(InputIterator first, InputIterator last);
```

### <a name="parameters"></a>Parametry

`first` Pierwszy iteratora ustala się których odległość od drugiego.

`last` Drugi iteratora, których odległość od pierwszego zostanie określony.

### <a name="return-value"></a>Wartość zwracana

Liczba razy `first` muszą być zwiększane aż równy `last`.

### <a name="remarks"></a>Uwagi

Funkcja odległość ma stałą złożoności podczas **InputIterator** spełnia wymagania dotyczące iteratora dostępie swobodnym; w przeciwnym razie ma złożoność liniowej i dlatego jest potencjalnie kosztowne.

### <a name="example"></a>Przykład

```cpp
// iterator_distance.cpp
// compile with: /EHsc
#include <iterator>
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   list<int> L;
   for ( i = -1 ; i < 9 ; ++i )
   {
      L.push_back ( 2 * i );
   }
   list <int>::iterator L_Iter, LPOS = L.begin ( );

   cout << "The list L is: ( ";
   for ( L_Iter = L.begin( ) ; L_Iter != L.end( ); L_Iter++ )
      cout << *L_Iter << " ";
   cout << ")." << endl;

   cout << "The iterator LPOS initially points to the first element: "
        << *LPOS << "." << endl;

   advance ( LPOS , 7 );
   cout << "LPOS is advanced 7 steps forward to point "
        << " to the eighth element: "
        << *LPOS << "." << endl;

   list<int>::difference_type Ldiff ;
   Ldiff = distance ( L.begin ( ) , LPOS );
   cout << "The distance from L.begin( ) to LPOS is: "
        << Ldiff << "." << endl;
}
```

```Output
The list L is: ( -2 0 2 4 6 8 10 12 14 16 ).
The iterator LPOS initially points to the first element: -2.
LPOS is advanced 7 steps forward to point  to the eighth element: 12.
The distance from L.begin( ) to LPOS is: 7.
```

## <a name="end"></a>  Koniec

Pobiera iterator do elementu, który następuje po ostatnim elemencie w określonym kontenerze.

```cpp
template <class Container>
auto end(Container& cont)
   -> decltype(cont.end());

template <class Container>
auto end(const Container& cont)
   -> decltype(cont.end());

template <class Ty, class Size>
Ty *end(Ty (& array)[Size]);
```

### <a name="parameters"></a>Parametry

`cont` Kontener.

`array` Tablica obiektów typu `Ty`.

### <a name="return-value"></a>Wartość zwracana

Zwraca pierwszy funkcje dwóch szablonów `cont.end()` (z systemem innym niż stała jest pierwszy i drugi jest stałe).

Zwraca trzecie funkcji szablonu `array + Size`.

### <a name="remarks"></a>Uwagi

Na przykład kod, zobacz [rozpocząć](../standard-library/iterator-functions.md#begin).

## <a name="front_inserter"></a>  front_inserter

Tworzy iterator, która może wstawiać elementy z przodu określonego kontenera.

```cpp
template <class Container>
front_insert_iterator<Container> front_inserter(Container& _Cont);
```

### <a name="parameters"></a>Parametry

`_Cont` Obiekt kontenera, w których przodu ma element wstawiony.

### <a name="return-value"></a>Wartość zwracana

A `front_insert_iterator` skojarzony z obiektem kontenera `_Cont`.

### <a name="remarks"></a>Uwagi

Funkcja członkowska [front_insert_iterator](../standard-library/front-insert-iterator-class.md#front_insert_iterator) z front_insert_iterator — klasa może być używany.

W standardowej bibliotece C++ argument musi odwoływać się do jednego z kontenerów dwóch sekwencji, których funkcji członkowskiej `push_back`: [deque — klasa](../standard-library/deque-class.md) lub "list — klasa".

### <a name="example"></a>Przykład

```cpp
// iterator_front_inserter.cpp
// compile with: /EHsc
#include <iterator>
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   int i;
   list <int>::iterator L_Iter;

   list<int> L;
   for ( i = -1 ; i < 9 ; ++i )
   {
      L.push_back ( i );
   }

   cout << "The list L is:\n ( ";
   for ( L_Iter = L.begin( ) ; L_Iter != L.end( ); L_Iter++)
      cout << *L_Iter << " ";
   cout << ")." << endl;

   // Using the template function to insert an element
   front_insert_iterator< list < int> > Iter(L);
 *Iter = 100;

   // Alternatively, you may use the front_insert member function
   front_inserter ( L ) = 200;

   cout << "After the front insertions, the list L is:\n ( ";
   for ( L_Iter = L.begin( ) ; L_Iter != L.end( ); L_Iter++)
      cout << *L_Iter << " ";
   cout << ")." << endl;
}
```

```Output
The list L is:
 ( -1 0 1 2 3 4 5 6 7 8 ).
After the front insertions, the list L is:
 ( 200 100 -1 0 1 2 3 4 5 6 7 8 ).
```

## <a name="inserter"></a>  Wstawianie

Funkcja szablonu pomocnika, które umożliwiają użycie `inserter(_Cont, _Where)` zamiast `insert_iterator<Container>(_Cont, _Where)`.

```cpp
template <class Container>
insert_iterator<Container>
inserter(
    Container& _Cont,
    typename Container::iterator _Where);
```

### <a name="parameters"></a>Parametry

`_Cont` Kontener, do którego mają być dodawane nowe elementy.

`_Where` Lokalizowanie punkt wstawiania iteratora.

### <a name="remarks"></a>Uwagi

Funkcja szablonu [insert_iterator —](../standard-library/insert-iterator-class.md#insert_iterator)`<Container>(_Cont, _Where)`.

### <a name="example"></a>Przykład

```cpp
// iterator_inserter.cpp
// compile with: /EHsc
#include <iterator>
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   int i;
   list <int>::iterator L_Iter;

   list<int> L;
   for (i = 2 ; i < 5 ; ++i )
   {
      L.push_back ( 10 * i );
   }

   cout << "The list L is:\n ( ";
   for ( L_Iter = L.begin( ) ; L_Iter != L.end( ); L_Iter++ )
      cout << *L_Iter << " ";
   cout << ")." << endl;

   // Using the template version to insert an element
   insert_iterator<list <int> > Iter( L, L.begin ( ) );
 *Iter = 1;

   // Alternatively, using the member function to insert an element
   inserter ( L, L.end ( ) ) = 500;

   cout << "After the insertions, the list L is:\n ( ";
   for ( L_Iter = L.begin( ) ; L_Iter != L.end( ); L_Iter++)
      cout << *L_Iter << " ";
   cout << ")." << endl;
}
```

```Output
The list L is:
 ( 20 30 40 ).
After the insertions, the list L is:
 ( 1 20 30 40 500 ).
```

## <a name="make_checked_array_iterator"></a>  make_checked_array_iterator

Tworzy [checked_array_iterator —](../standard-library/checked-array-iterator-class.md) które mogą być używane przez inne algorytmy.

> [!NOTE]
> Ta funkcja jest rozszerzenie Microsoft standardowa biblioteka C++. Kod zaimplementowany przy użyciu tej funkcji nie jest przenośny do standardowych środowisk kompilacji C++, które nie obsługują tego rozszerzenia Microsoft.

```cpp
template <class Iter>
checked_array_iterator<Iter>
    make_checked_array_iterator(
 Iter Ptr,
    size_t Size,
    size_t Index = 0);
```

### <a name="parameters"></a>Parametry

`Ptr` Wskaźnik do tablicy docelowej.

`Size` Rozmiar tablicy docelowej.

`Index` Opcjonalne indeks w tablicy.

### <a name="return-value"></a>Wartość zwracana

Wystąpienie `checked_array_iterator`.

### <a name="remarks"></a>Uwagi

`make_checked_array_iterator` Funkcji jest zdefiniowany w `stdext` przestrzeni nazw.

Ta funkcja przyjmuje raw wskaźnika — które zwykle spowodowałoby dotyczy przepełnienie granic — i opakowuje w [checked_array_iterator —](../standard-library/checked-array-iterator-class.md) klasy, który wykonuje sprawdzanie. Ponieważ tej klasy jest oznaczony jako zaznaczone, standardowa biblioteka C++ nie Ostrzegaj o nim. Aby uzyskać więcej informacji oraz przykłady kodu, zobacz [zaznaczone Iteratory](../standard-library/checked-iterators.md).

### <a name="example"></a>Przykład

W poniższym przykładzie [wektor](../standard-library/vector-class.md) jest tworzone i wypełniane 10 elementów. Zawartość wektora są kopiowane do tablicy przy użyciu algorytmu kopiowania, a następnie `make_checked_array_iterator` służy do określania miejsca docelowego. Następnie ma miejsce sprawdzenie celowego naruszenia granic, aby wywołać błąd asercji debugowania.

```cpp
// make_checked_array_iterator.cpp
// compile with: /EHsc /W4 /MTd

#include <algorithm>
#include <iterator> // stdext::make_checked_array_iterator
#include <memory> // std::make_unique
#include <iostream>
#include <vector>
#include <string>

using namespace std;

template <typename C> void print(const string& s, const C& c) {
    cout << s;

    for (const auto& e : c) {
        cout << e << " ";
    }

    cout << endl;
}

int main()
{
    const size_t dest_size = 10;
    // Old-school but not exception safe, favor make_unique<int[]>
    // int* dest = new int[dest_size];
    unique_ptr<int[]> updest = make_unique<int[]>(dest_size);
    int* dest = updest.get(); // get a raw pointer for the demo

    vector<int> v;

    for (int i = 0; i < dest_size; ++i) {
        v.push_back(i);
    }
    print("vector v: ", v);

    copy(v.begin(), v.end(), stdext::make_checked_array_iterator(dest, dest_size));

    cout << "int array dest: ";
    for (int i = 0; i < dest_size; ++i) {
        cout << dest[i] << " ";
    }
    cout << endl;

    // Add another element to the vector to force an overrun.
    v.push_back(10);
    // The next line causes a debug assertion when it executes.
    copy(v.begin(), v.end(), stdext::make_checked_array_iterator(dest, dest_size));
}

```

## <a name="make_move_iterator"></a>  make_move_iterator

Tworzy `move iterator` zawierający podany iteratora jako `stored` iteratora.

```cpp
template <class Iterator>
move_iterator<Iterator>
make_move_iterator(const Iterator& _It);
```

### <a name="parameters"></a>Parametry

`_It` Iterator przechowywane w nowych iteratora przenoszenia.

### <a name="remarks"></a>Uwagi

Funkcja szablonu `move_iterator` `<Iterator>(_It)`.

## <a name="make_unchecked_array_iterator"></a>  make_unchecked_array_iterator

Tworzy [unchecked_array_iterator —](../standard-library/unchecked-array-iterator-class.md) które mogą być używane przez inne algorytmy.

> [!NOTE]
> Ta funkcja jest rozszerzenie Microsoft standardowa biblioteka C++. Kod zaimplementowany przy użyciu tej funkcji nie jest przenośny do standardowych środowisk kompilacji C++, które nie obsługują tego rozszerzenia Microsoft.

```cpp
template <class Iter>
unchecked_array_iterator<Iter>
    make_unchecked_array_iterator(Iter Ptr);
```

### <a name="parameters"></a>Parametry

`Ptr` Wskaźnik do tablicy docelowej.

### <a name="return-value"></a>Wartość zwracana

Wystąpienie `unchecked_array_iterator`.

### <a name="remarks"></a>Uwagi

`make_unchecked_array_iterator` Funkcji jest zdefiniowany w `stdext` przestrzeni nazw.

Ta funkcja przyjmuje raw wskaźnik i otacza klasę, która wykonuje bez sprawdzania i w związku z tym optymalizuje optymalizacji na wartość nothing, ale również wycisza ostrzeżeń kompilatora, takich jak [C4996](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md). Dlatego jest to ukierunkowany sposób na radzenie sobie z ostrzeżeniami o niesprawdzonym wskaźniku, który nie powoduje ich całkowitego wyłączenia ani konieczności sprawdzania. Aby uzyskać więcej informacji oraz przykłady kodu, zobacz [zaznaczone Iteratory](../standard-library/checked-iterators.md).

### <a name="example"></a>Przykład

W poniższym przykładzie [wektor](../standard-library/vector-class.md) jest tworzone i wypełniane 10 elementów. Zawartość wektora są kopiowane do tablicy przy użyciu algorytmu kopiowania, a następnie `make_unchecked_array_iterator` służy do określania miejsca docelowego.

```cpp
// make_unchecked_array_iterator.cpp
// compile with: /EHsc /W4 /MTd

#include <algorithm>
#include <iterator> // stdext::make_unchecked_array_iterator
#include <iostream>
#include <vector>
#include <string>

using namespace std;

template <typename C> void print(const string& s, const C& c) {
    cout << s;

    for (const auto& e : c) {
        cout << e << " ";
    }

    cout << endl;
}

int main()
{
    const size_t dest_size = 10;
    int *dest = new int[dest_size];
    vector<int> v;

    for (int i = 0; i < dest_size; ++i) {
        v.push_back(i);
    }
    print("vector v: ", v);

    // COMPILER WARNING SILENCED: stdext::unchecked_array_iterator is marked as checked in debug mode
    // (it performs no checking, so an overrun will trigger undefined behavior)
    copy(v.begin(), v.end(), stdext::make_unchecked_array_iterator(dest));

    cout << "int array dest: ";
    for (int i = 0; i < dest_size; ++i) {
        cout << dest[i] << " ";
    }
    cout << endl;

    delete[] dest;
}

```

## <a name="next"></a>  Dalej

Dokonuje iteracji określoną liczbę razy i zwraca nową pozycję iteratora.

```cpp
template <class InputIterator>
InputIterator next(
    InputIterator first,
    typename iterator_traits<InputIterator>::difference_type _Off = 1);
```

### <a name="parameters"></a>Parametry

`first` Bieżąca pozycja.

`_Off` Liczba godzin w celu wykonania iteracji.

### <a name="return-value"></a>Wartość zwracana

Zwraca nowe położenie iteratora po iteracja `_Off` razy.

### <a name="remarks"></a>Uwagi

Funkcja szablonu `next` zwiększany `_Off` razy

## <a name="prev"></a>  Poprzedni

Dokonuje iteracji odwrotnej określoną liczbę razy i zwraca nową pozycję iteratora.

```cpp
template <class BidirectionalIterator>
BidirectionalIterator prev(
    BidirectionalIterator first,
    typename iterator_traits<BidirectionalIterator>::difference_type _Off = 1);
```

### <a name="parameters"></a>Parametry

`first` Bieżąca pozycja.

`_Off` Liczba godzin w celu wykonania iteracji.

### <a name="remarks"></a>Uwagi

Funkcja szablonu `next` zmniejszany `off` razy.

## <a name="see-also"></a>Zobacz także

[\<iterator>](../standard-library/iterator.md)<br/>
