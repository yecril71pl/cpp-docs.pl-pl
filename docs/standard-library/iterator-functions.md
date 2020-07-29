---
title: '&lt;funkcje iteratora &gt;'
ms.date: 11/04/2016
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
ms.openlocfilehash: 615ebeedc87563eeac46c462304072ff1979040c
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87222319"
---
# <a name="ltiteratorgt-functions"></a>&lt;funkcje iteratora &gt;

## <a name="advance"></a><a name="advance"></a>chodzenie

Inkrementuje iterator o określoną liczbę pozycji.

```cpp
template <class InputIterator, class Distance>
    void advance(InputIterator& InIt, Distance Off);
```

### <a name="parameters"></a>Parametry

*InIt*\
Iterator, który ma być inkrementowany i który musi spełniać wymagania dla iteratora danych wejściowych.

*Logowanie*\
Typ całkowitoliczbowy, który jest konwertowany na typ różnicy iteratora i który określa liczbę inkrementacji, o którą ma być zwiększone położenie iteratora.

### <a name="remarks"></a>Uwagi

Zakres zwiększania musi być niepojedynczy, a iteratory muszą być wyłuskiwalne lub znajdować się po końcu.

Jeśli `InputIterator` spełnia wymagania dla typu iteratora dwukierunkowego, wartość *Off* ta może być ujemna. Jeśli `InputIterator` jest typem iteratora wejściowego lub do przodu, *off* musi być nieujemny.

Funkcja Advance ma stałą złożoność `InputIterator` , gdy spełnia wymagania iteratora dostępu swobodnego; w przeciwnym razie ma złożoność liniową i dlatego może być kosztowna.

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

## <a name="back_inserter"></a><a name="back_inserter"></a>back_inserter

Tworzy iterator, który może wstawiać elementy z tyłu określonego kontenera.

```cpp
template <class Container>
back_insert_iterator<Container> back_inserter(Container& _Cont);
```

### <a name="parameters"></a>Parametry

*_Cont*\
Kontener, w którym ma zostać wykonane Wstawianie wsteczne.

### <a name="return-value"></a>Wartość zwracana

`back_insert_iterator`Skojarzone z obiektem kontenera *_Cont*.

### <a name="remarks"></a>Uwagi

W standardowej bibliotece języka C++ argument musi odwoływać się do jednego z trzech kontenerów sekwencji, które mają funkcję członkowską `push_back` : [Klasa deque](../standard-library/deque-class.md), [Klasa listy](../standard-library/list-class.md)lub [Klasa Vector](../standard-library/vector-class.md).

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

## <a name="begin"></a><a name="begin"></a>zaczną

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

*dawanie*\
Kontener.

*macierzy*\
Tablica obiektów typu `Ty` .

### <a name="return-value"></a>Wartość zwracana

Pierwsze dwie funkcje szablonu zwracają `cont.begin()` . Pierwsza funkcja jest niestała; druga jest stała.

Trzecia funkcja szablonu zwraca *tablicę*.

### <a name="example"></a>Przykład

Zaleca się używanie tej funkcji szablonu zamiast elementu członkowskiego kontenera, `begin()` gdy wymagane jest bardziej ogólne zachowanie.

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

Funkcja `reverse_sort` obsługuje kontenery dowolnego rodzaju, oprócz zwykłych tablic, ponieważ wywołuje nieczłonkowską wersję programu `begin()` . Jeśli `reverse_sort` zostały zakodowane w celu użycia elementu członkowskiego kontenera `begin()` :

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

## <a name="cbegin"></a><a name="cbegin"></a>cbegin

Pobiera iterator const do pierwszego elementu w określonym kontenerze.

```cpp
template <class Container>
auto cbegin(const Container& cont)
   -> decltype(cont.begin());
```

### <a name="parameters"></a>Parametry

*dawanie*\
Kontener lub lista initializer_list.

### <a name="return-value"></a>Wartość zwracana

Stała `cont.begin()` .

### <a name="remarks"></a>Uwagi

Ta funkcja działa ze wszystkimi kontenerami standardowej biblioteki C++ i z [initializer_list](../standard-library/initializer-list-class.md).

Można użyć tej funkcji elementu członkowskiego zamiast `begin()` funkcji szablonu, aby zagwarantować, że wartość zwracana to `const_iterator` . Zwykle jest używany w połączeniu z słowem kluczowym odejmowania [autotype,](../cpp/auto-cpp.md) jak pokazano w poniższym przykładzie. W tym przykładzie należy rozważyć możliwość `Container` przepustki (nie **`const`** ) kontenera lub `initializer_list` dowolnego rodzaju, który obsługuje `begin()` i `cbegin()` .

```cpp
auto i1 = Container.begin();
// i1 is Container<T>::iterator
auto i2 = Container.cbegin();

// i2 is Container<T>::const_iterator
```

## <a name="cend"></a><a name="cend"></a>cend

Pobiera iterator const do elementu, który następuje po ostatnim elemencie w określonym kontenerze.

```cpp
template <class Container>
auto cend(const Container& cont)
   -> decltype(cont.end());
```

### <a name="parameters"></a>Parametry

*dawanie*\
Kontener lub lista initializer_list.

### <a name="return-value"></a>Wartość zwracana

Stała `cont.end()` .

### <a name="remarks"></a>Uwagi

Ta funkcja działa ze wszystkimi kontenerami standardowej biblioteki C++ i z [initializer_list](../standard-library/initializer-list-class.md).

Można użyć tej funkcji elementu członkowskiego zamiast funkcji szablonu [end ()](../standard-library/iterator-functions.md#end) w celu zagwarantowania, że wartość zwracana to `const_iterator` . Zwykle jest używany w połączeniu z słowem kluczowym odejmowania [autotype,](../cpp/auto-cpp.md) jak pokazano w poniższym przykładzie. W tym przykładzie należy rozważyć możliwość `Container` przepustki (nie **`const`** ) kontenera lub `initializer_list` dowolnego rodzaju, który obsługuje `end()` i `cend()` .

```cpp
auto i1 = Container.end();
// i1 is Container<T>::iterator
auto i2 = Container.cend();

// i2 is Container<T>::const_iterator
```

## <a name="crbegin"></a><a name="crbegin"></a>crbegin —

```cpp
template <class C> constexpr auto crbegin(const C& c) -> decltype(std::rbegin(c));
```

## <a name="crend"></a><a name="crend"></a>crend

```cpp
template <class C> constexpr auto crend(const C& c) -> decltype(std::rend(c));
```

## <a name="data"></a><a name="data"></a>Data

```cpp
template <class C> constexpr auto data(C& c) -> decltype(c.data());
template <class C> constexpr auto data(const C& c) -> decltype(c.data());
template <class T, size_t N> constexpr T* data(T (&array)[N]) noexcept;
template <class E> constexpr const E* data(initializer_list<E> il) noexcept;
```

## <a name="distance"></a><a name="distance"></a>miast

Określa liczbę przyrostów między położeniami, do których odnoszą się dwa iteratory.

```cpp
template <class InputIterator>
typename iterator_traits<InputIterator>::difference_type distance(InputIterator first, InputIterator last);
```

### <a name="parameters"></a>Parametry

*pierwszego*\
Pierwszy iterator, którego odległość od sekundy ma zostać określony.

*ostatniego*\
Drugi iterator, którego odległość od początku ma zostać określony.

### <a name="return-value"></a>Wartość zwracana

Liczba przypadków, gdy *pierwszy* musi zostać zwiększony, dopóki nie będzie równa wartości *Last*.

### <a name="remarks"></a>Uwagi

Funkcja Distance ma stałą złożoność `InputIterator` , gdy spełnia wymagania iteratora dostępu swobodnego; w przeciwnym razie ma złożoność liniową i dlatego może być kosztowna.

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

## <a name="empty"></a><a name="empty"></a>ciągiem

```cpp
template <class C> constexpr auto empty(const C& c) -> decltype(c.empty());
template <class T, size_t N> constexpr bool empty(const T (&array)[N]) noexcept;
template <class E> constexpr bool empty(initializer_list<E> il) noexcept;
```

## <a name="end"></a><a name="end"></a>punktów

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

*dawanie*\
Kontener.

*macierzy*\
Tablica obiektów typu `Ty` .

### <a name="return-value"></a>Wartość zwracana

Pierwsze dwie funkcje szablonu zwracają `cont.end()` (pierwszy nie jest stałą, a drugi to stała).

Trzecia funkcja szablonu zwraca wartość `array + Size` .

### <a name="remarks"></a>Uwagi

Aby uzyskać przykład kodu, zobacz [BEGIN](../standard-library/iterator-functions.md#begin).

## <a name="front_inserter"></a><a name="front_inserter"></a>front_inserter

Tworzy iterator, która może wstawiać elementy z przodu określonego kontenera.

```cpp
template <class Container>
front_insert_iterator<Container> front_inserter(Container& _Cont);
```

### <a name="parameters"></a>Parametry

*_Cont*\
Obiekt kontenera, którego przód ma element wstawiony.

### <a name="return-value"></a>Wartość zwracana

`front_insert_iterator`Skojarzone z obiektem kontenera *_Cont*.

### <a name="remarks"></a>Uwagi

Funkcja członkowska [front_insert_iterator](../standard-library/front-insert-iterator-class.md#front_insert_iterator) klasy front_insert_iterator może być również używana.

W standardowej bibliotece języka C++ argument musi odwoływać się do jednego z dwóch kontenerów sekwencji, które mają funkcję członkowską `push_back` : [deque Class](../standard-library/deque-class.md) lub "list Class".

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

## <a name="inserter"></a><a name="inserter"></a>Inserter

Funkcja szablonu pomocnika, która umożliwia korzystanie `inserter(_Cont, _Where)` z elementu zamiast `insert_iterator<Container>(_Cont, _Where)` .

```cpp
template <class Container>
insert_iterator<Container>
inserter(
    Container& _Cont,
    typename Container::iterator _Where);
```

### <a name="parameters"></a>Parametry

*_Cont*\
Kontener, do którego mają zostać dodane nowe elementy.

*_Where*\
Iterator lokalizowania punktu wstawiania.

### <a name="remarks"></a>Uwagi

Funkcja szablonu zwraca [insert_iterator](../standard-library/insert-iterator-class.md#insert_iterator) `<Container>(_Cont, _Where)` .

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

## <a name="make_checked_array_iterator"></a><a name="make_checked_array_iterator"></a>make_checked_array_iterator

Tworzy [checked_array_iterator](../standard-library/checked-array-iterator-class.md) , które mogą być używane przez inne algorytmy.

> [!NOTE]
> Ta funkcja jest rozszerzeniem firmy Microsoft biblioteki standardowej języka C++. Kod zaimplementowany przy użyciu tej funkcji nie jest przenośny do standardowych środowisk kompilacji C++, które nie obsługują tego rozszerzenia Microsoft.

```cpp
template <class Iter>
checked_array_iterator<Iter>
    make_checked_array_iterator(
Iter Ptr,
    size_t Size,
    size_t Index = 0);
```

### <a name="parameters"></a>Parametry

*PTR*\
Wskaźnik do tablicy docelowej.

*Zmienia*\
Rozmiar tablicy docelowej.

*Indeks*\
Opcjonalny indeks do tablicy.

### <a name="return-value"></a>Wartość zwracana

Wystąpienie elementu `checked_array_iterator`.

### <a name="remarks"></a>Uwagi

`make_checked_array_iterator`Funkcja jest zdefiniowana w `stdext` przestrzeni nazw.

Ta funkcja pobiera surowy wskaźnik — co może zwykle prowadzić do przekroczenia granic — i zawija ją w klasie [checked_array_iterator](../standard-library/checked-array-iterator-class.md) , która sprawdza. Ponieważ ta klasa jest oznaczona jako zaznaczona, standardowa biblioteka języka C++ nie ostrzega o niej. Aby uzyskać więcej informacji i przykładów kodu, zobacz [sprawdzone Iteratory](../standard-library/checked-iterators.md).

### <a name="example"></a>Przykład

W poniższym przykładzie jest tworzony [wektor](../standard-library/vector-class.md) i wypełniany 10 elementów. Zawartość wektora jest kopiowana do tablicy przy użyciu algorytmu kopiowania, a następnie `make_checked_array_iterator` służy do określania miejsca docelowego. Następnie ma miejsce sprawdzenie celowego naruszenia granic, aby wywołać błąd asercji debugowania.

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

## <a name="make_move_iterator"></a><a name="make_move_iterator"></a>make_move_iterator

Tworzy `move iterator` , który zawiera dostarczony iterator jako `stored` iterator.

```cpp
template <class Iterator>
move_iterator<Iterator>
make_move_iterator(const Iterator& _It);
```

### <a name="parameters"></a>Parametry

*_It*\
Iterator przechowywany w nowym iteratoru przenoszenia.

### <a name="remarks"></a>Uwagi

Funkcja szablonu zwraca wartość `move_iterator` `<Iterator>(_It)` .

## <a name="make_unchecked_array_iterator"></a><a name="make_unchecked_array_iterator"></a>make_unchecked_array_iterator

Tworzy [unchecked_array_iterator](../standard-library/unchecked-array-iterator-class.md) , które mogą być używane przez inne algorytmy.

> [!NOTE]
> Ta funkcja jest rozszerzeniem firmy Microsoft biblioteki standardowej języka C++. Kod zaimplementowany przy użyciu tej funkcji nie jest przenośny do standardowych środowisk kompilacji C++, które nie obsługują tego rozszerzenia Microsoft.

```cpp
template <class Iter>
unchecked_array_iterator<Iter>
    make_unchecked_array_iterator(Iter Ptr);
```

### <a name="parameters"></a>Parametry

*PTR*\
Wskaźnik do tablicy docelowej.

### <a name="return-value"></a>Wartość zwracana

Wystąpienie elementu `unchecked_array_iterator`.

### <a name="remarks"></a>Uwagi

`make_unchecked_array_iterator`Funkcja jest zdefiniowana w `stdext` przestrzeni nazw.

Ta funkcja pobiera surowy wskaźnik i otacza go w klasie, która nie sprawdza i dlatego optymalizuje do Nothing, ale również wyciszy ostrzeżenia kompilatora, takie jak [C4996](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md). Dlatego jest to ukierunkowany sposób na radzenie sobie z ostrzeżeniami o niesprawdzonym wskaźniku, który nie powoduje ich całkowitego wyłączenia ani konieczności sprawdzania. Aby uzyskać więcej informacji i przykładów kodu, zobacz [sprawdzone Iteratory](../standard-library/checked-iterators.md).

### <a name="example"></a>Przykład

W poniższym przykładzie jest tworzony [wektor](../standard-library/vector-class.md) i wypełniany 10 elementów. Zawartość wektora jest kopiowana do tablicy przy użyciu algorytmu kopiowania, a następnie `make_unchecked_array_iterator` służy do określania miejsca docelowego.

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

## <a name="next"></a><a name="next"></a>ponown

Dokonuje iteracji określoną liczbę razy i zwraca nową pozycję iteratora.

```cpp
template <class InputIterator>
InputIterator next(
    InputIterator first,
    typename iterator_traits<InputIterator>::difference_type _Off = 1);
```

### <a name="parameters"></a>Parametry

*pierwszego*\
Bieżąca pozycja.

*_Off*\
Liczba powtórzeń iteracji.

### <a name="return-value"></a>Wartość zwracana

Zwraca nową pozycję iteratora po iteracji *_Off* czas.

### <a name="remarks"></a>Uwagi

Funkcja szablonu zwraca `next` przyrostowe czasy *_Off*

## <a name="prev"></a><a name="prev"></a>przeglądan

Dokonuje iteracji odwrotnej określoną liczbę razy i zwraca nową pozycję iteratora.

```cpp
template <class BidirectionalIterator>
BidirectionalIterator prev(
    BidirectionalIterator first,
    typename iterator_traits<BidirectionalIterator>::difference_type _Off = 1);
```

### <a name="parameters"></a>Parametry

*pierwszego*\
Bieżąca pozycja.

*_Off*\
Liczba powtórzeń iteracji.

### <a name="remarks"></a>Uwagi

Funkcja szablonu zwraca `next` liczbę `off` razy.

## <a name="rbegin"></a><a name="rbegin"></a>rbegin

```cpp
template <class C> constexpr auto rbegin(C& c) -> decltype(c.rbegin());
template <class C> constexpr auto rbegin(const C& c) -> decltype(c.rbegin());
```

## <a name="rend"></a><a name="rend"></a>rend

```cpp
template <class C> constexpr auto rend(C& c) -> decltype(c.rend());
template <class C> constexpr auto rend(const C& c) -> decltype(c.rend());
```

## <a name="size"></a><a name="size"></a>zmienia

```cpp
template <class C> constexpr auto size(const C& c) -> decltype(c.size());
template <class T, size_t N> constexpr size_t size(const T (&array)[N]) noexcept;
```
