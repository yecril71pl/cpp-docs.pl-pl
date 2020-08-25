---
title: deque — Klasa
ms.date: 11/04/2016
f1_keywords:
- deque/std::deque
- deque/std::deque::allocator_type
- deque/std::deque::const_iterator
- deque/std::deque::const_pointer
- deque/std::deque::const_reference
- deque/std::deque::const_reverse_iterator
- deque/std::deque::difference_type
- deque/std::deque::iterator
- deque/std::deque::pointer
- deque/std::deque::reference
- deque/std::deque::reverse_iterator
- deque/std::deque::size_type
- deque/std::deque::value_type
- deque/std::deque::assign
- deque/std::deque::at
- deque/std::deque::back
- deque/std::deque::begin
- deque/std::deque::cbegin
- deque/std::deque::cend
- deque/std::deque::clear
- deque/std::deque::crbegin
- deque/std::deque::crend
- deque/std::deque::emplace
- deque/std::deque::emplace_back
- deque/std::deque::emplace_front
- deque/std::deque::empty
- deque/std::deque::end
- deque/std::deque::erase
- deque/std::deque::front
- deque/std::deque::get_allocator
- deque/std::deque::insert
- deque/std::deque::max_size
- deque/std::deque::pop_back
- deque/std::deque::pop_front
- deque/std::deque::push_back
- deque/std::deque::push_front
- deque/std::deque::rbegin
- deque/std::deque::rend
- deque/std::deque::resize
- deque/std::deque::shrink_to_fit
- deque/std::deque::size
- deque/std::deque::swap
helpviewer_keywords:
- std::deque [C++]
- std::deque [C++], allocator_type
- std::deque [C++], const_iterator
- std::deque [C++], const_pointer
- std::deque [C++], const_reference
- std::deque [C++], const_reverse_iterator
- std::deque [C++], difference_type
- std::deque [C++], iterator
- std::deque [C++], pointer
- std::deque [C++], reference
- std::deque [C++], reverse_iterator
- std::deque [C++], size_type
- std::deque [C++], value_type
- std::deque [C++], assign
- std::deque [C++], at
- std::deque [C++], back
- std::deque [C++], begin
- std::deque [C++], cbegin
- std::deque [C++], cend
- std::deque [C++], clear
- std::deque [C++], crbegin
- std::deque [C++], crend
- std::deque [C++], emplace
- std::deque [C++], emplace_back
- std::deque [C++], emplace_front
- std::deque [C++], empty
- std::deque [C++], end
- std::deque [C++], erase
- std::deque [C++], front
- std::deque [C++], get_allocator
- std::deque [C++], insert
- std::deque [C++], max_size
- std::deque [C++], pop_back
- std::deque [C++], pop_front
- std::deque [C++], push_back
- std::deque [C++], push_front
- std::deque [C++], rbegin
- std::deque [C++], rend
- std::deque [C++], resize
- std::deque [C++], shrink_to_fit
- std::deque [C++], size
- std::deque [C++], swap
ms.assetid: 64842ee5-057a-4063-8c16-4267a0332584
ms.openlocfilehash: 1edcabf526d0f3aa2ba52ba3fd0fc656c5ae6b9c
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88838552"
---
# <a name="deque-class"></a>deque — Klasa

Rozmieszcza elementy danego typu w rozmieszczeniu liniowym i, podobnie jak wektor, włącza szybko losowy dostęp do dowolnego elementu i wydajne Wstawianie i usuwanie z tyłu kontenera. Jednak, w przeciwieństwie do wektora, `deque` Klasa obsługuje również wydajne Wstawianie i usuwanie na początku kontenera.

## <a name="syntax"></a>Składnia

```unstlib
template <class Type, class Allocator =allocator<Type>>
class deque
```

### <a name="parameters"></a>Parametry

*Wprowadź*\
Typ danych elementu, który ma być przechowywany w deque.

*Alokator*\
Typ reprezentujący przechowywany obiekt alokatora, który hermetyzuje szczegóły dotyczące alokacji i dealokacji deque pamięci. Ten argument jest opcjonalny, a wartość domyślna to **Alokator \<Type> **.

## <a name="remarks"></a>Uwagi

Wybór typu kontenera powinien ogólnie być oparty o typ wyszukiwania i wstawiania wymagany przez aplikację. [Wektory](../standard-library/vector-class.md) powinny być preferowanym kontenerem do zarządzania sekwencją, gdy losowy dostęp do dowolnego elementu znajduje się w warstwie Premium, a wstawienia lub usunięcia elementów są wymagane tylko na końcu sekwencji. Wydajność kontenera listy jest najwyższa, gdy efektywne wstawienia i usunięcia (w stałym czasie) w dowolnej lokalizacji w ramach sekwencji są w wersji Premium. Operacje w środku sekwencji wymagają kopiowania elementów i przypisań proporcjonalnie do liczby elementów w sekwencji (czas liniowy).

Ponowne przydzielanie deque występuje, gdy funkcja członkowska musi wstawiać lub wymazywać elementy sekwencji:

- Jeśli element zostanie wstawiony do pustej sekwencji lub jeśli element zostanie wymazany, aby opuścić pustą sekwencję, wówczas Iteratory wcześniejsze zwrócone przez [BEGIN](#begin) i [End](#end) stają się nieprawidłowe.

- Jeśli element zostanie wstawiony na pierwszej pozycji deque, wówczas wszystkie Iteratory, ale bez odwołań, które wyznaczą istniejące elementy staną się nieprawidłowe.

- Jeśli element zostanie wstawiony na końcu deque, a następnie zostaną [zakończone](#end) i wszystkie Iteratory, ale bez odwołań, które wyznaczą istniejące elementy staną się nieprawidłowe.

- Jeśli element zostanie wymazany na początku deque, tylko ten iterator i odwołania do wymazanego elementu stają się nieprawidłowe.

- Jeśli ostatni element zostanie wymazany z końca deque, tylko ten iterator do elementu końcowego i odwołania do wymazanego elementu stają się nieprawidłowe.

W przeciwnym razie Wstawianie lub wymazywanie elementu unieważnia wszystkie Iteratory i odwołania.

## <a name="members"></a>Elementy członkowskie

### <a name="constructors"></a>Konstruktory

|Nazwa|Opis|
|-|-|
|[deque](#deque)|Konstruuje a `deque` . Podano kilka konstruktorów w celu skonfigurowania zawartości nowego `deque` na różne sposoby: puste; załadowane z określoną liczbą pustych elementów; zawartość przeniesiona lub skopiowana z innej `deque` ; zawartość skopiowana lub przeniesiona przy użyciu iteratora; i jeden element jest kopiowany w tym `deque` `count` czasie. Niektóre konstruktory umożliwiają tworzenie elementów przy użyciu niestandardowych `allocator` .|

### <a name="typedefs"></a>Typedefs

|Nazwa|Opis|
|-|-|
|[allocator_type](#allocator_type)|Typ, który reprezentuje `allocator` klasę dla `deque` obiektu.|
|[const_iterator](#const_iterator)|Typ, który dostarcza Iterator dostępu swobodnego, który może uzyskiwać dostęp do elementów w `deque` postaci as **`const`**|
|[const_pointer](#const_pointer)|Typ, który dostarcza wskaźnik do elementu w a `deque` jako `const.`|
|[const_reference](#const_reference)|Typ, który zawiera odwołanie do elementu w `deque` celu odczytu i innych operacji jako `const.`|
|[const_reverse_iterator](#const_reverse_iterator)|Typ, który dostarcza Iterator dostępu swobodnego, który może uzyskiwać dostęp do elementów w postaci AS i je odczytywać `deque` **`const`** . Deque jest wyświetlany w odwrotnej postaci. Aby uzyskać więcej informacji, zobacz [Reverse_iterator Class](../standard-library/reverse-iterator-class.md)|
|[difference_type](#difference_type)|Typ, który zapewnia różnicę między dwoma iteratorami dostępu swobodnego, które odwołują się do elementów w tym samym elemencie `deque` .|
|[Iterator](#iterator)|Typ, który dostarcza Iterator dostępu swobodnego, który może odczytać lub zmodyfikować dowolny element w `deque` .|
|[pointer](#pointer)|Typ, który dostarcza wskaźnik do elementu w `deque` .|
|[odwoła](#reference)|Typ, który zawiera odwołanie do elementu przechowywanego w `deque` .|
|[reverse_iterator](#reverse_iterator)|Typ, który dostarcza Iterator dostępu swobodnego, który może odczytać lub zmodyfikować element w `deque` . Deque jest wyświetlana w odwrotnej kolejności.|
|[size_type](#size_type)|Typ, który zlicza liczbę elementów w `deque` .|
|[value_type](#value_type)|Typ, który reprezentuje typ danych przechowywany w `deque` .|

### <a name="functions"></a>Functions

|Nazwa|Opis|
|-|-|
|[przypisać](#assign)|Wymazuje elementy z `deque` i kopiuje nową sekwencję elementów do obiektu docelowego `deque` .|
|[w](#at)|Zwraca odwołanie do elementu w określonej lokalizacji w `deque` .|
|[Wstecz](#back)|Zwraca odwołanie do ostatniego elementu `deque` .|
|[zaczną](#begin)|Zwraca iterator dostępu swobodnego, odnoszący się do pierwszego elementu w `deque` .|
|[cbegin](#cbegin)|Zwraca iterator const do pierwszego elementu w `deque` .|
|[cend](#cend)|Zwraca iterator dostępu swobodnego **`const`** , który wskazuje tuż poza końcem `deque` .|
|[Wyczyść](#clear)|Kasuje wszystkie elementy `deque` .|
|[crbegin —](#crbegin)|Zwraca iterator const dostępu swobodnego do pierwszego elementu w `deque` przeglądanej kolejności odwrotnej.|
|[crend](#crend)|Zwraca iterator const dostępu swobodnego do pierwszego elementu w `deque` przeglądanej kolejności odwrotnej.|
|[emplace](#emplace)|Wstawia element skonstruowany w miejscu do `deque` podanego położenia.|
|[emplace_back](#emplace_back)|Dodaje element skonstruowany w miejscu na końcu `deque` .|
|[emplace_front](#emplace_front)|Dodaje element skonstruowany w miejscu do początku `deque` .|
|[puste](#empty)|Zwraca **`true`** czy `deque` element zawiera zero, i **`false`** Jeśli zawiera jeden lub więcej elementów.|
|[punktów](#end)|Zwraca iterator dostępu swobodnego, który wskazuje tuż poza końcem `deque` .|
|[Wyłączanie](#erase)|Usuwa element lub zakres elementów `deque` z określonych pozycji.|
|[FSB](#front)|Zwraca odwołanie do pierwszego elementu w `deque` .|
|[get_allocator](#get_allocator)|Zwraca kopię `allocator` obiektu, który jest używany do konstruowania `deque` .|
|[wstawienia](#insert)|Wstawia element, kilka elementów lub zakres elementów do `deque` określonego położenia.|
|[max_size](#max_size)|Zwraca maksymalną możliwą długość `deque` .|
|[pop_back](#pop_back)|Wymazuje element na końcu `deque` .|
|[pop_front](#pop_front)|Wymazuje element na początku `deque` .|
|[push_back](#push_back)|Dodaje element na końcu `deque` .|
|[push_front](#push_front)|Dodaje element do początku `deque` .|
|[rbegin](#rbegin)|Zwraca iterator dostępu swobodnego do pierwszego elementu w odwróconej `deque` .|
|[rend](#rend)|Zwraca iterator dostępu swobodnego, który wskazuje tuż poza ostatnim elementem w odwróconym `deque` .|
|[Zmień rozmiar](#resize)|Określa nowy rozmiar `deque` .|
|[shrink_to_fit](#shrink_to_fit)|Odrzuca nadmiarową pojemność.|
|[zmienia](#size)|Zwraca liczbę elementów w `deque` .|
|[wymiany](#swap)|Wymienia elementy dwóch `deque` s.|

### <a name="operators"></a>Operatory

|Nazwa|Opis|
|-|-|
|[&#91;&#93;operatora ](#op_at)|Zwraca odwołanie do `deque` elementu w określonej pozycji.|
|[operator =](#op_eq)|Zastępuje elementy `deque` z kopią innej `deque` .|

## <a name="allocator_type"></a><a name="allocator_type"></a> allocator_type

Typ, który reprezentuje klasę alokatora dla obiektu deque.

```cpp
typedef Allocator allocator_type;
```

### <a name="remarks"></a>Uwagi

`allocator_type` jest synonimem dla parametru szablonu `Allocator` .

### <a name="example"></a>Przykład

Zapoznaj się z przykładem [get_allocator](#get_allocator).

## <a name="assign"></a><a name="assign"></a> ponownie

Wymazuje elementy z deque i kopiuje nowy zestaw elementów do docelowego deque.

```cpp
template <class InputIterator>
void assign(
    InputIterator First,
    InputIterator Last);

void assign(
    size_type Count,
    const Type& Val);

void assign(initializer_list<Type> IList);
```

### <a name="parameters"></a>Parametry

*Pierwszego*\
Pozycja pierwszego elementu w zakresie elementów, który ma być kopiowany z argumentu deque.

*Ostatniego*\
Pozycja pierwszego elementu poza zakresem elementów, które mają być skopiowane z argumentu deque.

*Liczbą*\
Liczba kopii elementu wstawianych do deque.

*Użyte*\
Wartość elementu wstawianego do deque.

*IList*\
Initializer_list wstawiany do deque.

### <a name="remarks"></a>Uwagi

Gdy wszystkie istniejące elementy w docelowym deque są wymazywane, `assign` Wstawia określony zakres elementów z oryginalnego deque lub z innego deque do docelowego deque lub wstawia kopie nowego elementu określonej wartości w docelowym deque.

### <a name="example"></a>Przykład

```cpp
// deque_assign.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>
#include <initializer_list>

int main()
{
    using namespace std;
    deque <int> c1, c2;
    deque <int>::const_iterator cIter;

    c1.push_back(10);
    c1.push_back(20);
    c1.push_back(30);
    c2.push_back(40);
    c2.push_back(50);
    c2.push_back(60);

    deque<int> d1{ 1, 2, 3, 4 };
    initializer_list<int> iList{ 5, 6, 7, 8 };
    d1.assign(iList);

    cout << "d1 = ";
    for (int i : d1)
        cout << i;
    cout << endl;

    cout << "c1 =";
    for (int i : c1)
        cout << i;
    cout << endl;

    c1.assign(++c2.begin(), c2.end());
    cout << "c1 =";
    for (int i : c1)
        cout << i;
    cout << endl;

    c1.assign(7, 4);
    cout << "c1 =";
    for (int i : c1)
        cout << i;
    cout << endl;
}
```

```Output
d1 = 5678c1 =102030c1 =5060c1 =4444444
```

## <a name="at"></a><a name="at"></a> w

Zwraca odwołanie do elementu w określonej lokalizacji w deque.

```cpp
reference at(size_type pos);

const_reference at(size_type pos) const;
```

### <a name="parameters"></a>Parametry

*Terminal*\
Indeks dolny (lub numer pozycji) elementu do odwołania w deque.

### <a name="return-value"></a>Wartość zwracana

Jeśli wartość *pos* jest większa niż rozmiar deque, `at` zgłasza wyjątek.

### <a name="return-value"></a>Wartość zwracana

Jeśli wartość zwracana `at` jest przypisana do `const_reference` , obiekt deque nie może być modyfikowany. Jeśli wartość zwracana `at` jest przypisana do `reference` , obiekt deque może być modyfikowany.

### <a name="example"></a>Przykład

```cpp
// deque_at.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> c1;

   c1.push_back( 10 );
   c1.push_back( 20 );

   const int& i = c1.at( 0 );
   int& j = c1.at( 1 );
   cout << "The first element is " << i << endl;
   cout << "The second element is " << j << endl;
}
```

```Output
The first element is 10
The second element is 20
```

## <a name="back"></a><a name="back"></a> Wstecz

Zwraca odwołanie do ostatniego elementu deque.

```cpp
reference back();
const_reference back() const;
```

### <a name="return-value"></a>Wartość zwracana

Ostatni element deque. Jeśli deque jest pusty, wartość zwracana jest niezdefiniowana.

### <a name="remarks"></a>Uwagi

Jeśli wartość zwracana `back` jest przypisana do `const_reference` , obiekt deque nie może być modyfikowany. Jeśli wartość zwracana `back` jest przypisana do `reference` , obiekt deque może być modyfikowany.

Podczas kompilowania przy użyciu [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md) zdefiniowanego jako 1 lub 2, wystąpi błąd czasu wykonywania, jeśli spróbujesz uzyskać dostęp do elementu w pustym deque.  Aby uzyskać więcej informacji, zobacz [sprawdzone Iteratory](../standard-library/checked-iterators.md) .

### <a name="example"></a>Przykład

```cpp
// deque_back.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> c1;

   c1.push_back( 10 );
   c1.push_back( 11 );

   int& i = c1.back( );
   const int& ii = c1.front( );

   cout << "The last integer of c1 is " << i << endl;
   i--;
   cout << "The next-to-last integer of c1 is " << ii << endl;
}
```

```Output
The last integer of c1 is 11
The next-to-last integer of c1 is 10
```

## <a name="begin"></a><a name="begin"></a> zaczną

Zwraca iterator odnoszący się do pierwszego elementu w deque.

```cpp
const_iterator begin() const;
iterator begin();
```

### <a name="return-value"></a>Wartość zwracana

Iterator dostępu swobodnego odnoszący się do pierwszego elementu w deque lub do lokalizacji powiodło się puste deque.

### <a name="remarks"></a>Uwagi

Jeśli wartość zwracana `begin` jest przypisana do `const_iterator` , obiekt deque nie może być modyfikowany. Jeśli wartość zwracana `begin` jest przypisana do `iterator` , obiekt deque może być modyfikowany.

### <a name="example"></a>Przykład

```cpp
// deque_begin.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> c1;
   deque <int>::iterator c1_Iter;
   deque <int>::const_iterator c1_cIter;

   c1.push_back( 1 );
   c1.push_back( 2 );

   c1_Iter = c1.begin( );
   cout << "The first element of c1 is " << *c1_Iter << endl;

*c1_Iter = 20;
   c1_Iter = c1.begin( );
   cout << "The first element of c1 is now " << *c1_Iter << endl;

   // The following line would be an error because iterator is const
   // *c1_cIter = 200;
}
```

```Output
The first element of c1 is 1
The first element of c1 is now 20
```

## <a name="cbegin"></a><a name="cbegin"></a> cbegin

Zwraca **`const`** iterator, który odnosi się do pierwszego elementu w zakresie.

```cpp
const_iterator cbegin() const;
```

### <a name="return-value"></a>Wartość zwracana

**`const`** Iterator dostępu swobodnego, który wskazuje na pierwszy element zakresu lub lokalizację tuż poza końcem pustego zakresu (dla pustego zakresu `cbegin() == cend()` ).

### <a name="remarks"></a>Uwagi

Z wartością zwracaną `cbegin` nie można modyfikować elementów w zakresie.

Można użyć tej funkcji elementu członkowskiego zamiast `begin()` funkcji składowej, aby zagwarantować, że wartość zwracana to `const_iterator` . Zwykle jest używany w połączeniu z słowem kluczowym odejmowania [autotype,](../cpp/auto-cpp.md) jak pokazano w poniższym przykładzie. W tym przykładzie Rozważmy, `Container` że jest to modyfikowalny **`const`** kontener dowolnego rodzaju, który obsługuje `begin()` i `cbegin()` .

```cpp
auto i1 = Container.begin();
// i1 is Container<T>::iterator
auto i2 = Container.cbegin();

// i2 is Container<T>::const_iterator
```

## <a name="cend"></a><a name="cend"></a> cend

Zwraca **`const`** iterator, który odnosi się do lokalizacji jedynie poza ostatnim elementem w zakresie.

```cpp
const_iterator cend() const;
```

### <a name="return-value"></a>Wartość zwracana

Iterator dostępu swobodnego, który wskazuje tuż za koniec zakresu.

### <a name="remarks"></a>Uwagi

`cend` służy do sprawdzania, czy iterator przeszedł koniec zakresu.

Można użyć tej funkcji elementu członkowskiego zamiast `end()` funkcji składowej, aby zagwarantować, że wartość zwracana to `const_iterator` . Zwykle jest używany w połączeniu z słowem kluczowym odejmowania [autotype,](../cpp/auto-cpp.md) jak pokazano w poniższym przykładzie. W tym przykładzie Rozważmy, `Container` że jest to modyfikowalny **`const`** kontener dowolnego rodzaju, który obsługuje `end()` i `cend()` .

```cpp
auto i1 = Container.end();
// i1 is Container<T>::iterator
auto i2 = Container.cend();

// i2 is Container<T>::const_iterator
```

Nie można usunąć odwołania do wartości zwracanej przez `cend` .

## <a name="clear"></a><a name="clear"></a> Wyczyść

Usuwa wszystkie elementy deque.

```cpp
void clear();
```

### <a name="example"></a>Przykład

```cpp
// deque_clear.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> c1;

   c1.push_back( 10 );
   c1.push_back( 20 );
   c1.push_back( 30 );

   cout << "The size of the deque is initially " << c1.size( ) << endl;
   c1.clear( );
   cout << "The size of the deque after clearing is " << c1.size( ) << endl;
}
```

```Output
The size of the deque is initially 3
The size of the deque after clearing is 0
```

## <a name="const_iterator"></a><a name="const_iterator"></a> const_iterator

Typ, który dostarcza Iterator dostępu swobodnego, który może uzyskać dostęp do **`const`** elementu w deque.

```cpp
typedef implementation-defined const_iterator;
```

### <a name="remarks"></a>Uwagi

Typ `const_iterator` nie może być używany do modyfikacji wartości elementu.

### <a name="example"></a>Przykład

Zobacz przykład dla z [tyłu](#back).

## <a name="const_pointer"></a><a name="const_pointer"></a> const_pointer

Udostępnia wskaźnik do **`const`** elementu w deque.

```cpp
typedef typename Allocator::const_pointer const_pointer;
```

### <a name="remarks"></a>Uwagi

Typ `const_pointer` nie może być używany do modyfikacji wartości elementu. [Iterator](#iterator) jest najczęściej używany do uzyskiwania dostępu do elementu deque.

## <a name="const_reference"></a><a name="const_reference"></a> const_reference

Typ, który dostarcza odwołanie do **`const`** elementu przechowywanego w deque do odczytu i wykonywania **`const`** operacji.

```cpp
typedef typename Allocator::const_reference const_reference;
```

### <a name="remarks"></a>Uwagi

Typ `const_reference` nie może być używany do modyfikacji wartości elementu.

### <a name="example"></a>Przykład

```cpp
// deque_const_ref.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> c1;

   c1.push_back( 10 );
   c1.push_back( 20 );

   const deque <int> c2 = c1;
   const int &i = c2.front( );
   const int &j = c2.back( );
   cout << "The first element is " << i << endl;
   cout << "The second element is " << j << endl;

   // The following line would cause an error as c2 is const
   // c2.push_back( 30 );
}
```

```Output
The first element is 10
The second element is 20
```

## <a name="const_reverse_iterator"></a><a name="const_reverse_iterator"></a> const_reverse_iterator

Typ, który dostarcza Iterator dostępu swobodnego, który może odczytać dowolny **`const`** element w deque.

```cpp
typedef std::reverse_iterator<const_iterator> const_reverse_iterator;
```

### <a name="remarks"></a>Uwagi

Typ `const_reverse_iterator` nie może zmodyfikować wartości elementu i służy do iteracji przez deque w odwrocie.

### <a name="example"></a>Przykład

Zapoznaj się z przykładem dla [rbegin](#rbegin) , aby zapoznać się z przykładem sposobu deklarowania iteratora i korzystania z niego.

## <a name="crbegin"></a><a name="crbegin"></a> crbegin —

Zwraca iterator const do pierwszego elementu w odwróconej deque.

```cpp
const_reverse_iterator crbegin() const;
```

### <a name="return-value"></a>Wartość zwracana

Iterator typu const odwrotnie odnoszący się do pierwszego elementu w odwróconej [deque](../standard-library/deque-class.md) lub adresowania ostatniego elementu w odwrót `deque` .

### <a name="remarks"></a>Uwagi

Z wartością zwracaną `crbegin` , `deque` nie można zmodyfikować obiektu.

### <a name="example"></a>Przykład

```cpp
// deque_crbegin.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> v1;
   deque <int>::iterator v1_Iter;
   deque <int>::const_reverse_iterator v1_rIter;

   v1.push_back( 1 );
   v1.push_back( 2 );

   v1_Iter = v1.begin( );
   cout << "The first element of deque is "
        << *v1_Iter << "." << endl;

   v1_rIter = v1.crbegin( );
   cout << "The first element of the reversed deque is "
        << *v1_rIter << "." << endl;
}
```

```Output
The first element of deque is 1.
The first element of the reversed deque is 2.
```

## <a name="crend"></a><a name="crend"></a> crend

Zwraca iterator const, który odnosi się do lokalizacji po ostatnim elemencie w odwróconej deque.

```cpp
const_reverse_iterator crend() const;
```

### <a name="return-value"></a>Wartość zwracana

Iterator typu const odwrotnie dostępu swobodnego, który odnosi się do lokalizacji po ostatnim elemencie w odwróconej [deque](../standard-library/deque-class.md) (lokalizacja, która poprzedza pierwszy element w nieodwróconym deque).

### <a name="remarks"></a>Uwagi

`crend` jest używany z odwróconą opcją `deque` [Array:: cend](../standard-library/array-class-stl.md#cend) jest używana z `deque` .

Po wartości zwracanej `crend` (odpowiednio zmniejszonej) `deque` nie można zmodyfikować obiektu.

`crend` może służyć do sprawdzenia, czy iterator odwrotny osiągnął koniec deque.

Nie można usunąć odwołania do wartości zwracanej przez `crend` .

### <a name="example"></a>Przykład

```cpp
// deque_crend.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> v1;
   deque <int>::const_reverse_iterator v1_rIter;

   v1.push_back( 1 );
   v1.push_back( 2 );

   for ( v1_rIter = v1.rbegin( ) ; v1_rIter != v1.rend( ) ; v1_rIter++ )
      cout << *v1_rIter << endl;
}
```

```Output
2
1
```

## <a name="deque"></a><a name="deque"></a> deque

Konstruuje deque o określonym rozmiarze lub z elementami określonej wartości lub z określonym alokatorem lub jako kopię wszystkich lub części innych deque.

```cpp
deque();

explicit deque(const Allocator& Al);
explicit deque(size_type Count);
deque(size_type Count, const Type& Val);

deque(
    size_type Count,
    const Type& Val,
    const Allocator& Al);

deque(const deque& Right);

template <class InputIterator>
deque(InputIterator First,  InputIterator Last);

template <class InputIterator>
deque(
   InputIterator First,
   InputIterator Last,
   const Allocator& Al);

deque(initializer_list<value_type> IList, const Allocator& Al);
```

### <a name="parameters"></a>Parametry

*Wsp*\
Klasa alokatora do wykorzystania z tym obiektem.

*Liczbą*\
Liczba elementów w skonstruowanej deque.

*Użyte*\
Wartość elementów w skonstruowanej deque.

*Kliknij*\
Deque, którego skonstruowany deque ma być kopia.

*Pierwszego*\
Pozycja pierwszego elementu w zakresie elementów, które mają zostać skopiowane.

*Ostatniego*\
Pozycja pierwszego elementu poza zakresem elementów, które mają zostać skopiowane.

*IList*\
Initializer_list, które mają zostać skopiowane.

### <a name="remarks"></a>Uwagi

Wszystkie konstruktory przechowują obiekt alokatora (*Al*) i inicjują deque.

Pierwsze dwa konstruktory określają pustą początkową deque; Druga z nich określa również typ alokatora ( `_Al` ), który ma być używany.

Trzeci konstruktor określa powtarzanie określonej liczby ( `count` ) elementów wartości domyślnej dla klasy `Type` .

Czwarty i piąty konstruktory określają powtórzenia (*Count*) elementów wartości `val` .

Szósty konstruktor określa kopię deque *po prawej stronie*.

Siedem i ósmej konstruktorów kopiują zakres `[First, Last)` deque.

Siódmy Konstruktor przenosi deque w *prawo*.

Ósmy Konstruktor kopiuje zawartość initializer_list.

Żaden z konstruktorów nie wykonuje żadnych tymczasowych ponownych alokacji.

### <a name="example"></a>Przykład

```cpp
/ compile with: /EHsc
#include <deque>
#include <iostream>
#include <forward_list>

int main()
{
    using namespace std;

    forward_list<int> f1{ 1, 2, 3, 4 };

    f1.insert_after(f1.begin(), { 5, 6, 7, 8 });

    deque <int>::iterator c1_Iter, c2_Iter, c3_Iter, c4_Iter, c5_Iter, c6_Iter;

    // Create an empty deque c0
    deque <int> c0;

    // Create a deque c1 with 3 elements of default value 0
    deque <int> c1(3);

    // Create a deque c2 with 5 elements of value 2
    deque <int> c2(5, 2);

    // Create a deque c3 with 3 elements of value 1 and with the
    // allocator of deque c2
    deque <int> c3(3, 1, c2.get_allocator());

    // Create a copy, deque c4, of deque c2
    deque <int> c4(c2);

    // Create a deque c5 by copying the range c4[ first,  last)
    c4_Iter = c4.begin();
    c4_Iter++;
    c4_Iter++;
    deque <int> c5(c4.begin(), c4_Iter);

    // Create a deque c6 by copying the range c4[ first,  last) and
    // c2 with the allocator of deque
    c4_Iter = c4.begin();
    c4_Iter++;
    c4_Iter++;
    c4_Iter++;
    deque <int> c6(c4.begin(), c4_Iter, c2.get_allocator());

    // Create a deque c8 by copying the contents of an initializer_list
    // using brace initialization
    deque<int> c8({ 1, 2, 3, 4 });

    initializer_list<int> iList{ 5, 6, 7, 8 };
    deque<int> c9( iList);

    cout << "c1 = ";
    for (int i : c1)
        cout << i << " ";
    cout << endl;

    cout << "c2 = ";
    for (int i : c2)
        cout << i << " ";
    cout << endl;

    cout << "c3 = ";
    for (int i : c3)
        cout << i << " ";
    cout << endl;

    cout << "c4 = ";
    for (int i : c4)
        cout << i << " ";
    cout << endl;

    cout << "c5 = ";
    for (int i : c5)
        cout << i << " ";
    cout << endl;

    cout << "c6 = ";
    for (int i : c6)
        cout << i << " ";
    cout << endl;

    // Move deque c6 to deque c7
    deque <int> c7(move(c6));
    deque <int>::iterator c7_Iter;

    cout << "c7 =";
    for (int i : c7)
        cout << i << " ";
    cout << endl;

    cout << "c8 = ";
    for (int i : c8)
        cout << i << " ";
    cout << endl;

    cout << "c9 = ";
    for (int i : c9)
        cout << i << " ";
    cout << endl;

    int x = 3;
}
// deque_deque.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
    using namespace std;
   deque <int>::iterator c1_Iter, c2_Iter, c3_Iter, c4_Iter, c5_Iter, c6_Iter;

    // Create an empty deque c0
    deque <int> c0;

    // Create a deque c1 with 3 elements of default value 0
    deque <int> c1( 3 );

    // Create a deque c2 with 5 elements of value 2
    deque <int> c2( 5, 2 );

    // Create a deque c3 with 3 elements of value 1 and with the
    // allocator of deque c2
    deque <int> c3( 3, 1, c2.get_allocator( ) );

    // Create a copy, deque c4, of deque c2
    deque <int> c4( c2 );

    // Create a deque c5 by copying the range c4[ first,  last)
    c4_Iter = c4.begin( );
    c4_Iter++;
    c4_Iter++;
    deque <int> c5( c4.begin( ), c4_Iter );

    // Create a deque c6 by copying the range c4[ first,  last) and
    // c2 with the allocator of deque
    c4_Iter = c4.begin( );
   c4_Iter++;
   c4_Iter++;
   c4_Iter++;
   deque <int> c6( c4.begin( ), c4_Iter, c2.get_allocator( ) );

    // Create a deque c8 by copying the contents of an initializer_list
    // using brace initialization
    deque<int> c8({ 1, 2, 3, 4 });

        initializer_list<int> iList{ 5, 6, 7, 8 };
    deque<int> c9( iList);

    cout << "c1 = ";
    for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )
        cout << *c1_Iter << " ";
    cout << endl;

    cout << "c2 = ";
    for ( c2_Iter = c2.begin( ); c2_Iter != c2.end( ); c2_Iter++ )
        cout << *c2_Iter << " ";
    cout << endl;

    cout << "c3 = ";
    for ( c3_Iter = c3.begin( ); c3_Iter != c3.end( ); c3_Iter++ )
        cout << *c3_Iter << " ";
    cout << endl;

    cout << "c4 = ";
    for ( c4_Iter = c4.begin( ); c4_Iter != c4.end( ); c4_Iter++ )
        cout << *c4_Iter << " ";
    cout << endl;

    cout << "c5 = ";
    for ( c5_Iter = c5.begin( ); c5_Iter != c5.end( ); c5_Iter++ )
        cout << *c5_Iter << " ";
    cout << endl;

    cout << "c6 = ";
    for ( c6_Iter = c6.begin( ); c6_Iter != c6.end( ); c6_Iter++ )
        cout << *c6_Iter << " ";
    cout << endl;

    // Move deque c6 to deque c7
    deque <int> c7( move(c6) );
    deque <int>::iterator c7_Iter;

    cout << "c7 =" ;
    for ( c7_Iter = c7.begin( ) ; c7_Iter != c7.end( ) ; c7_Iter++ )
        cout << " " << *c7_Iter;
    cout << endl;

    cout << "c8 = ";
    for (int i : c8)
        cout << i << " ";
    cout << endl;

    cout << "c9 = ";
    or (int i : c9)
        cout << i << " ";
    cout << endl;
}
```

## <a name="difference_type"></a><a name="difference_type"></a> difference_type

Typ, który zawiera różnicę między dwoma iteratorami odwołującymi się do elementów w obrębie tego samego deque.

```cpp
typedef typename Allocator::difference_type difference_type;
```

### <a name="remarks"></a>Uwagi

`difference_type`Można również opisać jako liczbę elementów między dwoma wskaźnikami.

### <a name="example"></a>Przykład

```cpp
// deque_diff_type.cpp
// compile with: /EHsc
#include <iostream>
#include <deque>
#include <algorithm>

int main( )
{
   using namespace std;

   deque <int> c1;
   deque <int>::iterator c1_Iter, c2_Iter;

   c1.push_back( 30 );
   c1.push_back( 20 );
   c1.push_back( 30 );
   c1.push_back( 10 );
   c1.push_back( 30 );
   c1.push_back( 20 );

   c1_Iter = c1.begin( );
   c2_Iter = c1.end( );

   deque <int>::difference_type df_typ1, df_typ2, df_typ3;

   df_typ1 = count( c1_Iter, c2_Iter, 10 );
   df_typ2 = count( c1_Iter, c2_Iter, 20 );
   df_typ3 = count( c1_Iter, c2_Iter, 30 );
   cout << "The number '10' is in c1 collection " << df_typ1 << " times.\n";
   cout << "The number '20' is in c1 collection " << df_typ2 << " times.\n";
   cout << "The number '30' is in c1 collection " << df_typ3 << " times.\n";
}
```

```Output
The number '10' is in c1 collection 1 times.
The number '20' is in c1 collection 2 times.
The number '30' is in c1 collection 3 times.
```

## <a name="emplace"></a><a name="emplace"></a> emplace

Wstawia element skonstruowany w miejscu do deque w określonej pozycji.

```cpp
iterator emplace(
    const_iterator _Where,
    Type&& val);
```

### <a name="parameters"></a>Parametry

*_Where*\
Pozycja w [deque](../standard-library/deque-class.md) , w którym wstawiany jest pierwszy element.

*użyte*\
Wartość wstawianego elementu do `deque` .

### <a name="return-value"></a>Wartość zwracana

Funkcja zwraca iterator, który wskazuje na pozycję, gdzie nowy element został wstawiony do deque.

### <a name="remarks"></a>Uwagi

Każda operacja wstawiania może być kosztowna, zobacz, aby zapoznać się z `deque` omówieniem `deque` wydajności.

### <a name="example"></a>Przykład

```cpp
// deque_emplace.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> v1;
   deque <int>::iterator Iter;

   v1.push_back( 10 );
   v1.push_back( 20 );
   v1.push_back( 30 );

   cout << "v1 =" ;
   for ( Iter = v1.begin( ) ; Iter != v1.end( ) ; Iter++ )
      cout << " " << *Iter;
   cout << endl;

// initialize a deque of deques by moving v1
   deque < deque <int> > vv1;

   vv1.emplace( vv1.begin(), move( v1 ) );
   if ( vv1.size( ) != 0 && vv1[0].size( ) != 0 )
      {
      cout << "vv1[0] =";
      for (Iter = vv1[0].begin( ); Iter != vv1[0].end( ); Iter++ )
         cout << " " << *Iter;
      cout << endl;
      }
}
```

```Output
v1 = 10 20 30
vv1[0] = 10 20 30
```

## <a name="emplace_back"></a><a name="emplace_back"></a> emplace_back

Dodaje element skonstruowany w miejscu na końcu deque.

```cpp
void emplace_back(Type&& val);
```

### <a name="parameters"></a>Parametry

*użyte*\
Element dodany na końcu [deque](../standard-library/deque-class.md).

### <a name="example"></a>Przykład

```cpp
// deque_emplace_back.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> v1;

   v1.push_back( 1 );
   if ( v1.size( ) != 0 )
      cout << "Last element: " << v1.back( ) << endl;

   v1.push_back( 2 );
   if ( v1.size( ) != 0 )
      cout << "New last element: " << v1.back( ) << endl;

// initialize a deque of deques by moving v1
   deque < deque <int> > vv1;

   vv1.emplace_back( move( v1 ) );
   if ( vv1.size( ) != 0 && vv1[0].size( ) != 0 )
      cout << "Moved last element: " << vv1[0].back( ) << endl;
}
```

```Output
Last element: 1
New last element: 2
Moved last element: 2
```

## <a name="emplace_front"></a><a name="emplace_front"></a> emplace_front

Dodaje element skonstruowany w miejscu na końcu deque.

```cpp
void emplace_front(Type&& val);
```

### <a name="parameters"></a>Parametry

*użyte*\
Element dodany na początku [deque](../standard-library/deque-class.md).

### <a name="example"></a>Przykład

```cpp
// deque_emplace_front.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> v1;

   v1.push_back( 1 );
   if ( v1.size( ) != 0 )
      cout << "Last element: " << v1.back( ) << endl;

   v1.push_back( 2 );
   if ( v1.size( ) != 0 )
      cout << "New last element: " << v1.back( ) << endl;

// initialize a deque of deques by moving v1
   deque < deque <int> > vv1;

   vv1.emplace_front( move( v1 ) );
   if ( vv1.size( ) != 0 && vv1[0].size( ) != 0 )
      cout << "Moved last element: " << vv1[0].back( ) << endl;
}
```

```Output
Last element: 1
New last element: 2
Moved last element: 2
```

## <a name="empty"></a><a name="empty"></a> ciągiem

Testuje, czy element deque jest pusty.

```cpp
bool empty() const;
```

### <a name="return-value"></a>Wartość zwracana

**`true`** Jeśli deque jest pusty; **`false`** Jeśli deque nie jest pusty.

### <a name="example"></a>Przykład

```cpp
// deque_empty.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> c1;

   c1.push_back( 10 );
   if ( c1.empty( ) )
      cout << "The deque is empty." << endl;
   else
      cout << "The deque is not empty." << endl;
}
```

```Output
The deque is not empty.
```

## <a name="end"></a><a name="end"></a> punktów

Zwraca iterator, który odnosi się do lokalizacji po ostatnim elemencie w deque.

```cpp
const_iterator end() const;

iterator end();
```

### <a name="return-value"></a>Wartość zwracana

Iterator dostępu swobodnego, który odnosi się do lokalizacji po ostatnim elemencie w deque. Jeśli deque jest pusty, a następnie deque:: end = = deque:: BEGIN.

### <a name="remarks"></a>Uwagi

`end` służy do sprawdzania, czy iterator osiągnął koniec deque.

### <a name="example"></a>Przykład

```cpp
// deque_end.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> c1;
   deque <int>::iterator c1_Iter;

   c1.push_back( 10 );
   c1.push_back( 20 );
   c1.push_back( 30 );

   c1_Iter = c1.end( );
   c1_Iter--;
   cout << "The last integer of c1 is " << *c1_Iter << endl;

   c1_Iter--;
   *c1_Iter = 400;
   cout << "The new next-to-last integer of c1 is " << *c1_Iter << endl;

   // If a const iterator had been declared instead with the line:
   // deque <int>::const_iterator c1_Iter;
   // an error would have resulted when inserting the 400

   cout << "The deque is now:";
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )
      cout << " " << *c1_Iter;
}
```

```Output
The last integer of c1 is 30
The new next-to-last integer of c1 is 400
The deque is now: 10 400 30
```

## <a name="erase"></a><a name="erase"></a> Wyłączanie

Usuwa element lub zakres elementów w deque z określonych pozycji.

```cpp
iterator erase(iterator _Where);

iterator erase(iterator first, iterator last);
```

### <a name="parameters"></a>Parametry

*_Where*\
Pozycja elementu, który ma zostać usunięty z deque.

*pierwszego*\
Pozycja pierwszego elementu usuniętego z deque.

*ostatniego*\
Umieść tuż poza ostatnim elementem usuniętym z deque.

### <a name="return-value"></a>Wartość zwracana

Iterator dostępu swobodnego, który wyznacza pierwszy element pozostający poza elementami usuniętymi lub wskaźnikiem do końca deque, jeśli taki element nie istnieje.

### <a name="remarks"></a>Uwagi

`erase` nigdy nie zgłasza wyjątku.

### <a name="example"></a>Przykład

```cpp
// deque_erase.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> c1;
   deque <int>::iterator Iter;

   c1.push_back( 10 );
   c1.push_back( 20 );
   c1.push_back( 30 );
   c1.push_back( 40 );
   c1.push_back( 50 );
   cout << "The initial deque is: ";
   for ( Iter = c1.begin( ); Iter != c1.end( ); Iter++ )
      cout << *Iter << " ";
   cout << endl;
   c1.erase( c1.begin( ) );
   cout << "After erasing the first element, the deque becomes:  ";
   for ( Iter = c1.begin( ); Iter != c1.end( ); Iter++ )
      cout << *Iter << " ";
   cout << endl;
   Iter = c1.begin( );
   Iter++;
   c1.erase( Iter, c1.end( ) );
   cout << "After erasing all elements but the first, deque becomes: ";
   for ( Iter = c1.begin( ); Iter != c1.end( ); Iter++ )
      cout << *Iter << " ";
   cout << endl;
}
```

```Output
The initial deque is: 10 20 30 40 50
After erasing the first element, the deque becomes:  20 30 40 50
After erasing all elements but the first, deque becomes: 20
```

## <a name="front"></a><a name="front"></a> FSB

Zwraca odwołanie do pierwszego elementu w deque.

```cpp
reference front();

const_reference front() const;
```

### <a name="return-value"></a>Wartość zwracana

Jeśli deque jest pusty, zwracany jest niezdefiniowany.

### <a name="remarks"></a>Uwagi

Jeśli wartość zwracana `front` jest przypisana do `const_reference` , obiekt deque nie może być modyfikowany. Jeśli wartość zwracana `front` jest przypisana do `reference` , obiekt deque może być modyfikowany.

Podczas kompilowania przy użyciu [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md) zdefiniowanego jako 1 lub 2, wystąpi błąd czasu wykonywania, jeśli spróbujesz uzyskać dostęp do elementu w pustym deque.  Aby uzyskać więcej informacji, zobacz [sprawdzone Iteratory](../standard-library/checked-iterators.md) .

### <a name="example"></a>Przykład

```cpp
// deque_front.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> c1;

   c1.push_back( 10 );
   c1.push_back( 11 );

   int& i = c1.front( );
   const int& ii = c1.front( );

   cout << "The first integer of c1 is " << i << endl;
   i++;
   cout << "The second integer of c1 is " << ii << endl;
}
```

```Output
The first integer of c1 is 10
The second integer of c1 is 11
```

## <a name="get_allocator"></a><a name="get_allocator"></a> get_allocator

Zwraca kopię obiektu alokatora używanego do konstruowania deque.

```cpp
Allocator get_allocator() const;
```

### <a name="return-value"></a>Wartość zwracana

Alokator używany przez deque.

### <a name="remarks"></a>Uwagi

Przypisania klasy deque określają sposób, w jaki Klasa zarządza magazynem. Domyślne przydzielenie klas kontenerów standardowej biblioteki języka C++ jest wystarczające dla większości potrzeb programistycznych. Pisanie i używanie własnej klasy alokatora jest zaawansowanym tematem języka C++.

### <a name="example"></a>Przykład

```cpp
// deque_get_allocator.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   // The following lines declare objects that use the default allocator.
   deque <int> c1;
   deque <int, allocator<int> > c2 = deque <int, allocator<int> >( allocator<int>( ) );

   // c3 will use the same allocator class as c1
   deque <int> c3( c1.get_allocator( ) );

   deque <int>::allocator_type xlst = c1.get_allocator( );
   // You can now call functions on the allocator class used by c1
}
```

## <a name="insert"></a><a name="insert"></a> wstawienia

Wstawia element lub wiele elementów lub zakres elementów do deque w określonej pozycji.

```cpp
iterator insert(
    const_iterator Where,
    const Type& Val);

iterator insert(
    const_iterator Where,
    Type&& Val);

void insert(
    iterator Where,
    size_type Count,
    const Type& Val);

template <class InputIterator>
void insert(
    iterator Where,
    InputIterator First,
    InputIterator Last);

iterator insert(
    iterator Where,initializer_list<Type>
IList);
```

### <a name="parameters"></a>Parametry

*Miejscu*\
Pozycja w elemencie docelowym deque, w którym wstawiany jest pierwszy element.

*Użyte*\
Wartość elementu wstawianego do deque.

*Liczbą*\
Liczba elementów wstawianych do deque.

*Pierwszego*\
Pozycja pierwszego elementu w zakresie elementów w argumencie deque do skopiowania.

*Ostatniego*\
Pozycja pierwszego elementu poza zakresem elementów w argumencie deque do skopiowania.

*IList*\
Initializer_list elementów do wstawienia.

### <a name="return-value"></a>Wartość zwracana

Pierwsze dwie funkcje INSERT zwracają iterator, który wskazuje na pozycję, w której nowy element został wstawiony do deque.

### <a name="remarks"></a>Uwagi

Każda operacja wstawiania może być kosztowna.

## <a name="iterator"></a><a name="iterator"></a> Iterator

Typ, który dostarcza Iterator dostępu swobodnego, który może odczytać lub zmodyfikować dowolny element w deque.

```cpp
typedef implementation-defined iterator;
```

### <a name="remarks"></a>Uwagi

Typ `iterator` może służyć do modyfikowania wartości elementu.

### <a name="example"></a>Przykład

Zobacz przykład [rozpoczęcia](#begin).

## <a name="max_size"></a><a name="max_size"></a> max_size

Zwraca maksymalną długość deque.

```cpp
size_type max_size() const;
```

### <a name="return-value"></a>Wartość zwracana

Maksymalna możliwa długość deque.

### <a name="example"></a>Przykład

```cpp
// deque_max_size.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> c1;
   deque <int>::size_type i;

   i = c1.max_size( );
   cout << "The maximum possible length of the deque is " << i << "." << endl;
}
```

## <a name="operator"></a><a name="op_at"></a> operator []

Zwraca odwołanie do elementu deque w określonej pozycji.

```cpp
reference operator[](size_type pos);

const_reference operator[](size_type pos) const;
```

### <a name="parameters"></a>Parametry

*Terminal*\
Pozycja elementu deque, do którego ma nastąpić odwołanie.

### <a name="return-value"></a>Wartość zwracana

Odwołanie do elementu, którego pozycja jest określona w argumencie. Jeśli określona pozycja jest większa niż rozmiar deque, wynik jest niezdefiniowany.

### <a name="remarks"></a>Uwagi

Jeśli wartość zwracana `operator[]` jest przypisana do `const_reference` , obiekt deque nie może być modyfikowany. Jeśli wartość zwracana `operator[]` jest przypisana do `reference` , obiekt deque może być modyfikowany.

Podczas kompilowania przy użyciu [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md) zdefiniowanego jako 1 lub 2, wystąpi błąd czasu wykonywania, jeśli spróbujesz uzyskać dostęp do elementu poza granicami deque.  Aby uzyskać więcej informacji, zobacz [sprawdzone Iteratory](../standard-library/checked-iterators.md) .

### <a name="example"></a>Przykład

```cpp
// deque_op_ref.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> c1;

   c1.push_back( 10 );
   c1.push_back( 20 );
   cout << "The first integer of c1 is " << c1[0] << endl;
   int& i = c1[1];
   cout << "The second integer of c1 is " << i << endl;
}
```

```Output
The first integer of c1 is 10
The second integer of c1 is 20
```

## <a name="operator"></a><a name="op_eq"></a> operator =

Zastępuje elementy tego deque za pomocą elementów z innej deque.

```cpp
deque& operator=(const deque& right);

deque& operator=(deque&& right);
```

### <a name="parameters"></a>Parametry

*Kliknij*\
Deque, który dostarcza nową zawartość.

### <a name="remarks"></a>Uwagi

Pierwsze zastąpienie Kopiuje elementy do tego deque z *prawej strony*, źródła przypisania. Drugie zastąpienie powoduje przeniesienie elementów do tego deque z *prawej strony*.

Elementy, które są zawarte w tym deque przed wykonaniem operatora, zostaną usunięte.

### <a name="example"></a>Przykład

```cpp
// deque_operator_as.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>
using namespace std;

typedef deque<int> MyDeque;

template<typename MyDeque> struct S;

template<typename MyDeque> struct S<MyDeque&> {
  static void show( MyDeque& d ) {
    MyDeque::const_iterator iter;
    for (iter = d.cbegin(); iter != d.cend(); iter++)
       cout << *iter << " ";
    cout << endl;
  }
};

template<typename MyDeque> struct S<MyDeque&&> {
  static void show( MyDeque&& d ) {
    MyDeque::const_iterator iter;
    for (iter = d.cbegin(); iter != d.cend(); iter++)
       cout << *iter << " ";
cout << " via unnamed rvalue reference " << endl;
  }
};

int main( )
{
   MyDeque d1, d2;

   d1.push_back(10);
   d1.push_back(20);
   d1.push_back(30);
   d1.push_back(40);
   d1.push_back(50);

   cout << "d1 = " ;
   S<MyDeque&>::show( d1 );

   d2 = d1;
   cout << "d2 = ";
   S<MyDeque&>::show( d2 );

   cout << "     ";
   S<MyDeque&&>::show ( move< MyDeque& > (d1) );
}
```

## <a name="pointer"></a><a name="pointer"></a> przytrzymaj

Udostępnia wskaźnik do elementu w [deque](../standard-library/deque-class.md).

```unstlib
typedef typename Allocator::pointer pointer;
```

### <a name="remarks"></a>Uwagi

Typ `pointer` może służyć do modyfikowania wartości elementu. [Iterator](#iterator) jest najczęściej używany do uzyskiwania dostępu do elementu deque.

## <a name="pop_back"></a><a name="pop_back"></a> pop_back

Usuwa element na końcu deque.

```cpp
void pop_back();
```

### <a name="remarks"></a>Uwagi

Ostatni element nie może być pusty. `pop_back` nigdy nie zgłasza wyjątku.

### <a name="example"></a>Przykład

```cpp
// deque_pop_back.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> c1;

   c1.push_back( 1 );
   c1.push_back( 2 );
   cout << "The first element is: " << c1.front( ) << endl;
   cout << "The last element is: " << c1.back( ) << endl;

   c1.pop_back( );
   cout << "After deleting the element at the end of the deque, the "
      "last element is: " << c1.back( ) << endl;
}
```

```Output
The first element is: 1
The last element is: 2
After deleting the element at the end of the deque, the last element is: 1
```

## <a name="pop_front"></a><a name="pop_front"></a> pop_front

Usuwa element na początku deque.

```cpp
void pop_front();
```

### <a name="remarks"></a>Uwagi

Pierwszy element nie może być pusty. `pop_front` nigdy nie zgłasza wyjątku.

### <a name="example"></a>Przykład

```cpp
// deque_pop_front.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> c1;

   c1.push_back( 1 );
   c1.push_back( 2 );
   cout << "The first element is: " << c1.front( ) << endl;
   cout << "The second element is: " << c1.back( ) << endl;

   c1.pop_front( );
   cout << "After deleting the element at the beginning of the "
      "deque, the first element is: " << c1.front( ) << endl;
}
```

```Output
The first element is: 1
The second element is: 2
After deleting the element at the beginning of the deque, the first element is: 2
```

## <a name="push_back"></a><a name="push_back"></a> push_back

Dodaje element na końcu deque.

```cpp
void push_back(const Type& val);

void push_back(Type&& val);
```

### <a name="parameters"></a>Parametry

*użyte*\
Element dodany na końcu deque.

### <a name="remarks"></a>Uwagi

Jeśli wyjątek jest zgłaszany, deque pozostaje niezmieniona i wyjątek jest ponownie zgłaszany.

## <a name="push_front"></a><a name="push_front"></a> push_front

Dodaje element na początku deque.

```cpp
void push_front(const Type& val);
void push_front(Type&& val);
```

### <a name="parameters"></a>Parametry

*użyte*\
Element dodany na początku deque.

### <a name="remarks"></a>Uwagi

Jeśli wyjątek jest zgłaszany, deque pozostaje niezmieniona i wyjątek jest ponownie zgłaszany.

### <a name="example"></a>Przykład

```cpp
// deque_push_front.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>
#include <string>

int main( )
{
   using namespace std;
   deque <int> c1;

   c1.push_front( 1 );
   if ( c1.size( ) != 0 )
      cout << "First element: " << c1.front( ) << endl;

   c1.push_front( 2 );
   if ( c1.size( ) != 0 )
      cout << "New first element: " << c1.front( ) << endl;

// move initialize a deque of strings
   deque <string> c2;
   string str("a");

   c2.push_front( move( str ) );
   cout << "Moved first element: " << c2.front( ) << endl;
}
```

```Output
First element: 1
New first element: 2
Moved first element: a
```

## <a name="rbegin"></a><a name="rbegin"></a> rbegin

Zwraca iterator do pierwszego elementu w odwróconej deque.

```cpp
const_reverse_iterator rbegin() const;

reverse_iterator rbegin();
```

### <a name="return-value"></a>Wartość zwracana

Iterator odwrotnego dostępu swobodnego, odnoszący się do pierwszego elementu w odwróconej deque lub adresowania ostatniego elementu w nieodwróconym deque.

### <a name="remarks"></a>Uwagi

`rbegin` jest używany z odwróconym dequem, tak jak [BEGIN](#begin) jest używany z deque.

Jeśli wartość zwracana `rbegin` jest przypisana do `const_reverse_iterator` , obiekt deque nie może być modyfikowany. Jeśli wartość zwracana `rbegin` jest przypisana do `reverse_iterator` , obiekt deque może być modyfikowany.

`rbegin` może służyć do iteracji w deque wstecz.

### <a name="example"></a>Przykład

```cpp
// deque_rbegin.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> c1;
   deque <int>::iterator c1_Iter;
   deque <int>::reverse_iterator c1_rIter;

   // If the following line had replaced the line above, an error
   // would have resulted in the line modifying an element
   // (commented below) because the iterator would have been const
   // deque <int>::const_reverse_iterator c1_rIter;

   c1.push_back( 10 );
   c1.push_back( 20 );
   c1.push_back( 30 );

   c1_rIter = c1.rbegin( );
   cout << "Last element in the deque is " << *c1_rIter << "." << endl;

   cout << "The deque contains the elements: ";
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )
      cout << *c1_Iter << " ";
   cout << "in that order.";
   cout << endl;

   // rbegin can be used to iterate through a deque in reverse order
   cout << "The reversed deque is: ";
   for ( c1_rIter = c1.rbegin( ); c1_rIter != c1.rend( ); c1_rIter++ )
      cout << *c1_rIter << " ";
   cout << endl;

   c1_rIter = c1.rbegin( );
   *c1_rIter = 40;  // This would have caused an error if a
                    // const_reverse iterator had been declared as
                    // noted above
   cout << "Last element in deque is now " << *c1_rIter << "." << endl;
}
```

```Output
Last element in the deque is 30.
The deque contains the elements: 10 20 30 in that order.
The reversed deque is: 30 20 10
Last element in deque is now 40.
```

## <a name="reference"></a><a name="reference"></a> odwoła

Typ, który zawiera odwołanie do elementu przechowywanego w deque.

```cpp
typedef typename Allocator::reference reference;
```

### <a name="example"></a>Przykład

```cpp
// deque_reference.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> c1;

   c1.push_back( 10 );
   c1.push_back( 20 );

   const int &i = c1.front( );
   int &j = c1.back( );
   cout << "The first element is " << i << endl;
   cout << "The second element is " << j << endl;
}
```

```Output
The first element is 10
The second element is 20
```

## <a name="rend"></a><a name="rend"></a> rend

Zwraca iterator, który odnosi się do lokalizacji po ostatnim elemencie w odwróconej deque.

```cpp
const_reverse_iterator rend() const;

reverse_iterator rend();
```

### <a name="return-value"></a>Wartość zwracana

Odwrotny iterator dostępu swobodnego, który odnosi się do lokalizacji po ostatnim elemencie w odwróconej deque (lokalizacja, która poprzedza pierwszy element w odwrocie deque).

### <a name="remarks"></a>Uwagi

`rend` jest używany z odwróconym dequem, tak samo jak [koniec](#end) jest używany z deque.

Jeśli wartość zwracana `rend` jest przypisana do `const_reverse_iterator` , obiekt deque nie może być modyfikowany. Jeśli wartość zwracana `rend` jest przypisana do `reverse_iterator` , obiekt deque może być modyfikowany.

`rend` można go użyć do sprawdzenia, czy iterator odwrotny osiągnął koniec jego deque.

Nie można usunąć odwołania do wartości zwracanej przez `rend` .

### <a name="example"></a>Przykład

```cpp
// deque_rend.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;

   deque <int> c1;
   deque <int>::iterator c1_Iter;
   deque <int>::reverse_iterator c1_rIter;
   // If the following line had replaced the line above, an error
   // would have resulted in the line modifying an element
   // (commented below) because the iterator would have been const
   // deque <int>::const_reverse_iterator c1_rIter;

   c1.push_back( 10 );
   c1.push_back( 20 );
   c1.push_back( 30 );

   c1_rIter = c1.rend( );
   c1_rIter --; // Decrementing a reverse iterator moves it forward
                // in the deque (to point to the first element here)
   cout << "The first element in the deque is: " << *c1_rIter << endl;

   cout << "The deque is: ";
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )
      cout << *c1_Iter << " ";
   cout << endl;

   // rend can be used to test if an iteration is through all of
   // the elements of a reversed deque
   cout << "The reversed deque is: ";
   for ( c1_rIter = c1.rbegin( ); c1_rIter != c1.rend( ); c1_rIter++ )
      cout << *c1_rIter << " ";
   cout << endl;

   c1_rIter = c1.rend( );
   c1_rIter--; // Decrementing the reverse iterator moves it backward
               // in the reversed deque (to the last element here)
   *c1_rIter = 40; // This modification of the last element would
                   // have caused an error if a const_reverse
                   // iterator had been declared (as noted above)
   cout << "The modified reversed deque is: ";
   for ( c1_rIter = c1.rbegin( ); c1_rIter != c1.rend( ); c1_rIter++ )
      cout << *c1_rIter << " ";
   cout << endl;
}
```

```Output
The first element in the deque is: 10
The deque is: 10 20 30
The reversed deque is: 30 20 10
The modified reversed deque is: 30 20 40
```

## <a name="resize"></a><a name="resize"></a> Zmień rozmiar

Określa nowy rozmiar deque.

```cpp
void resize(size_type _Newsize);

void resize(size_type _Newsize, Type val);
```

### <a name="parameters"></a>Parametry

*_Newsize*\
Nowy rozmiar deque.

*użyte*\
Wartość nowych elementów, które mają zostać dodane do deque, jeśli nowy rozmiar jest większy niż rozmiar oryginalny. W przypadku pominięcia wartości nowe elementy są przypisywane do wartości domyślnej klasy.

### <a name="remarks"></a>Uwagi

Jeśli rozmiar deque jest mniejszy niż żądany rozmiar, *_Newsize*, elementy są dodawane do deque do momentu osiągnięcia żądanego rozmiaru.

Jeśli rozmiar deque jest większy niż żądany rozmiar, elementy znajdujące się najbliżej końca deque są usuwane do momentu, gdy deque osiągnie rozmiar *_Newsize*.

Jeśli obecny rozmiar deque jest taki sam jak żądany rozmiar, nie jest podejmowana żadna akcja.

[rozmiar](#size) odzwierciedla bieżący rozmiar deque.

### <a name="example"></a>Przykład

```cpp
// deque_resize.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> c1;

   c1.push_back( 10 );
   c1.push_back( 20 );
   c1.push_back( 30 );

   c1.resize( 4,40 );
   cout << "The size of c1 is: " << c1.size( ) << endl;
   cout << "The value of the last element is " << c1.back( ) << endl;

   c1.resize( 5 );
   cout << "The size of c1 is now: " << c1.size( ) << endl;
   cout << "The value of the last element is now " << c1.back( ) << endl;

   c1.resize( 2 );
   cout << "The reduced size of c1 is: " << c1.size( ) << endl;
   cout << "The value of the last element is now " << c1.back( ) << endl;
}
```

```Output
The size of c1 is: 4
The value of the last element is 40
The size of c1 is now: 5
The value of the last element is now 0
The reduced size of c1 is: 2
The value of the last element is now 20
```

## <a name="reverse_iterator"></a><a name="reverse_iterator"></a> reverse_iterator

Typ, który dostarcza Iterator dostępu swobodnego, który może odczytać lub zmodyfikować element w odwróconym deque.

```cpp
typedef std::reverse_iterator<iterator> reverse_iterator;
```

### <a name="remarks"></a>Uwagi

Typ `reverse_iterator` jest używany do iteracji w deque.

### <a name="example"></a>Przykład

Zobacz przykład dla rbegin.

## <a name="shrink_to_fit"></a><a name="shrink_to_fit"></a> shrink_to_fit

Odrzuca nadmiarową pojemność.

```cpp
void shrink_to_fit();
```

### <a name="remarks"></a>Uwagi

Nie istnieje przenośny sposób określania `shrink_to_fit` , czy zmniejsza Magazyn używany przez [deque](../standard-library/deque-class.md).

### <a name="example"></a>Przykład

```cpp
// deque_shrink_to_fit.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> v1;
   //deque <int>::iterator Iter;

   v1.push_back( 1 );
   v1.push_back( 2 );
   cout << "Current size of v1 = "
      << v1.size( ) << endl;
   v1.shrink_to_fit();
   cout << "Current size of v1 = "
      << v1.size( ) << endl;
}
```

```Output
Current size of v1 = 1
Current size of v1 = 1
```

## <a name="size"></a><a name="size"></a> zmienia

Zwraca liczbę elementów w deque.

```cpp
size_type size() const;
```

### <a name="return-value"></a>Wartość zwracana

Bieżąca długość deque.

### <a name="example"></a>Przykład

```cpp
// deque_size.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> c1;
   deque <int>::size_type i;

   c1.push_back( 1 );
   i = c1.size( );
   cout << "The deque length is " << i << "." << endl;

   c1.push_back( 2 );
   i = c1.size( );
   cout << "The deque length is now " << i << "." << endl;
}
```

```Output
The deque length is 1.
The deque length is now 2.
```

## <a name="size_type"></a><a name="size_type"></a> size_type

Typ, który zlicza liczbę elementów w deque.

```cpp
typedef typename Allocator::size_type size_type;
```

### <a name="example"></a>Przykład

Zobacz przykład [rozmiaru](#size).

## <a name="swap"></a><a name="swap"></a> wymiany

Wymienia elementy dwóch deques.

```cpp
void swap(deque<Type, Allocator>& right);

friend void swap(deque<Type, Allocator>& left, deque<Type, Allocator>& right) template <class Type, class Allocator>
void swap(deque<Type, Allocator>& left, deque<Type, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*Kliknij*\
Deque udostępniający elementy, które mają zostać zamienione, lub deque, których elementy mają być wymieniane z tymi deque `left` .

*lewym*\
Element deque, którego elementy mają być wymieniane z tymi, które są deque z *prawej strony*.

### <a name="example"></a>Przykład

```cpp
// deque_swap.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> c1, c2, c3;
   deque <int>::iterator c1_Iter;

   c1.push_back( 1 );
   c1.push_back( 2 );
   c1.push_back( 3 );
   c2.push_back( 10 );
   c2.push_back( 20 );
   c3.push_back( 100 );

   cout << "The original deque c1 is:";
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )
      cout << " " << *c1_Iter;
   cout << endl;

   c1.swap( c2 );

   cout << "After swapping with c2, deque c1 is:";
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )
      cout << " " << *c1_Iter;
   cout << endl;

   swap( c1,c3 );

   cout << "After swapping with c3, deque c1 is:";
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )
      cout << " " << *c1_Iter;
   cout << endl;

   swap<>(c1, c2);
   cout << "After swapping with c2, deque c1 is:";
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )
      cout << " " << *c1_Iter;
   cout << endl;
}
```

```Output
The original deque c1 is: 1 2 3
After swapping with c2, deque c1 is: 10 20
After swapping with c3, deque c1 is: 100
After swapping with c2, deque c1 is: 1 2 3
```

## <a name="value_type"></a><a name="value_type"></a> value_type

Typ, który reprezentuje typ danych przechowywany w deque.

```cpp
typedef typename Allocator::value_type value_type;
```

### <a name="remarks"></a>Uwagi

`value_type` jest synonimem dla parametru szablonu `Type` .

### <a name="example"></a>Przykład

```cpp
// deque_value_type.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>
int main( )
{
   using namespace std;
   deque<int>::value_type AnInt;
   AnInt = 44;
   cout << AnInt << endl;
}
```

```Output
44
```

## <a name="see-also"></a>Zobacz też

[Bezpieczeństwo wątku w standardowej bibliotece języka C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Dokumentacja standardowej biblioteki języka C++](../standard-library/cpp-standard-library-reference.md)
