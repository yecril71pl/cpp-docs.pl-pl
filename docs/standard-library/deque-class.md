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
ms.openlocfilehash: 8a50d04751ac5b4abaf94d0d9fd16f57c6200f66
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62394016"
---
# <a name="deque-class"></a>deque — Klasa

Rozmieszcza elementy danego typu w układzie liniowych i, takich jak wektor, umożliwia szybkiego losowego dostępu do dowolnego elementu i wydajne wstawiania i usuwania tyłu kontenera. Jednak w przeciwieństwie do wektora `deque` klasy obsługuje również wydajne Wstawianie i usuwanie z przodu kontenera.

## <a name="syntax"></a>Składnia

```unstlib
template <class Type, class Allocator =allocator<Type>>
class deque
```

### <a name="parameters"></a>Parametry

*Typ*<br/>
Typ danych elementu, który ma być przechowywany w deque.

*Allocator*<br/>
Typ reprezentujący przechowywany obiekt alokatora, który hermetyzuje szczegóły dotyczące alokacji i dezalokacji pamięci deque. Ten argument jest opcjonalny, a wartość domyślna to **alokatora\<typ >**.

## <a name="remarks"></a>Uwagi

Wybór typu kontenera powinien ogólnie być oparty o typ wyszukiwania i wstawiania wymagany przez aplikację. [Wektory](../standard-library/vector-class.md) powinny być preferowane kontenera do zarządzania sekwencji, gdy jest losowe do dowolnego elementu w warstwie premium i wstawienia i usunięcia elementów tylko wymagane na końcu sekwencji. Wydajność wyświetlenie listy kontenerów jest przełożonego, gdy jest to wydajne wstawienia i usunięcia (w stały czas) w dowolnym miejscu w sekwencji jest w wersji premium. Takich operacji w trakcie sekwencji wymagają kopiuje element i przypisania proporcjonalna do liczby elementów w sekwencji (liniowy czas).

Deque — ponowne przydzielenie występuje, gdy funkcję członkowską należy wstawić taśmie ani wymazać elementy sekwencji:

- Jeśli element jest wstawiany do pustą sekwencją lub jeśli elementu są usuwane, aby pozostawić pustą sekwencją, wtedy Iteratory wcześniej zwrócony przez [rozpocząć](#begin) i [zakończenia](#end) stają się nieprawidłowe.

- Jeśli element zostanie wstawiony na pierwszym miejscu deque, a następnie wszystkie Iteratory, ale żadnych odwołań, które wyznaczają istniejące elementy stają się nieprawidłowe.

- Jeśli element jest wstawiany na końcu deque, następnie [zakończenia](#end) i wszystkie Iteratory, ale żadnych odwołań, które wyznaczają istniejące elementy stają się nieprawidłowe.

- Jeśli elementu są usuwane z przodu deque, tylko że iteratora i odwołania do elementu wymazane stają się nieprawidłowe.

- Jeśli po ostatnim elemencie są usuwane z końca tylko tym iterator do ostatniego elementu w deque — i odwołania do elementu wymazane stają się nieprawidłowe.

W przeciwnym razie wstawiania lub wymazywanie elementu unieważnia wszystkie Iteratory i odwołania.

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[deque —](#deque)|Konstruuje `deque`. Kilka konstruktorów są dostarczane do skonfigurowania nowej zawartości `deque` na różne sposoby: pusty; załadowane z określoną liczbą pustych elementów; zawartość przenoszone lub kopiowane z innego `deque`; zawartość, skopiować lub przenieść za pomocą iteratora; oraz jeden element skopiowane do `deque` `count` razy. Niektóre konstruktory włączyć za pomocą niestandardowego `allocator` do tworzenia elementów.|

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[allocator_type](#allocator_type)|Typ, który reprezentuje `allocator` klasy dla `deque` obiektu.|
|[const_iterator](#const_iterator)|Typ zapewniający iterator dostępu swobodnego, który można dostęp i możliwość odczytywania elementów w `deque` jako `const`|
|[const_pointer](#const_pointer)|Typ, który dostarcza wskaźnik do elementu w `deque` jako `const.`|
|[const_reference](#const_reference)|Typ, który zawiera odwołanie do elementu w `deque` do odczytu i inne operacje jako `const.`|
|[const_reverse_iterator](#const_reverse_iterator)|Typ zapewniający iterator dostępu swobodnego, który można dostęp i możliwość odczytywania elementów w `deque` jako **const**. Deque — zostanie wyświetlony w odwrotnej kolejności. Aby uzyskać więcej informacji, zobacz [reverse_iterator — klasa](../standard-library/reverse-iterator-class.md)|
|[difference_type](#difference_type)|Typ, który zawiera różnicę między dwoma iteratorami dostępu swobodnego, które odwołują się do elementów w tym samym `deque`.|
|[iterator](#iterator)|Typ zapewniający iterator dostępu swobodnego, który może odczytać lub zmodyfikować dowolny element w `deque`.|
|[pointer](#pointer)|Typ, który dostarcza wskaźnik do elementu w `deque`.|
|[Odwołanie](#reference)|Typ, który zawiera odwołanie do elementu przechowywanego w `deque`.|
|[reverse_iterator](#reverse_iterator)|Typ zapewniający iterator dostępu swobodnego, który może odczytać lub zmodyfikować element w `deque`. Deque — zostanie wyświetlony w odwrotnej kolejności.|
|[size_type](#size_type)|Typ, który zlicza liczbę elementów w `deque`.|
|[value_type](#value_type)|Typ, który reprezentuje typ danych przechowywanych w `deque`.|

### <a name="member-functions"></a>Funkcje Członkowskie

|Funkcja elementu członkowskiego|Opis|
|-|-|
|[Przypisz](#assign)|Usuwa elementy z `deque` i kopiuje je do obiektu docelowego nową sekwencję elementów `deque`.|
|[at](#at)|Zwraca odwołanie do elementu w określonej lokalizacji w `deque`.|
|[back](#back)|Zwraca odwołanie do ostatniego elementu `deque`.|
|[begin](#begin)|Zwraca iterator dostępu swobodnego, odnoszący się do pierwszego elementu w `deque`.|
|[cbegin](#cbegin)|Zwraca const iterator do pierwszego elementu w `deque`.|
|[cend](#cend)|Zwraca losową dostępu **const** iteratora, który wskazuje tuż za koniec `deque`.|
|[Usuń zaznaczenie](#clear)|Usuwa wszystkie elementy `deque`.|
|[crbegin](#crbegin)|Zwraca stały iterator dostępu losowego do pierwszego elementu w `deque` wyświetlane w odwrotnej kolejności.|
|[crend](#crend)|Zwraca stały iterator dostępu losowego do pierwszego elementu w `deque` wyświetlane w odwrotnej kolejności.|
|[emplace](#emplace)|Wstawia element skonstruowany w miejscu do `deque` na określonej pozycji.|
|[emplace_back](#emplace_back)|Dodaje element skonstruowany w miejscu do końca `deque`.|
|[emplace_front](#emplace_front)|Dodaje element skonstruowany w miejscu z początkiem `deque`.|
|[pusty](#empty)|Zwraca **true** Jeśli `deque` zawiera zero elementy i **false** zawiera jeden lub więcej elementów.|
|[koniec](#end)|Zwraca iterator dostępu swobodnego, który wskazuje tuż za koniec `deque`.|
|[wymazywanie](#erase)|Usuwa element lub zakres elementów w `deque` z określonych pozycji.|
|[Frontonu](#front)|Zwraca odwołanie do pierwszego elementu w `deque`.|
|[get_allocator](#get_allocator)|Zwraca kopię obiektu `allocator` obiektu, który służy do konstruowania `deque`.|
|[insert](#insert)|Wstawia element, kilka elementów lub szereg elementów do `deque` na określonej pozycji.|
|[max_size](#max_size)|Zwraca wartość maksymalna możliwa długość `deque`.|
|[pop_back](#pop_back)|Usuwa element na końcu `deque`.|
|[pop_front](#pop_front)|Usuwa element na początku `deque`.|
|[push_back](#push_back)|Dodaje element do końca `deque`.|
|[push_front](#push_front)|Dodaje element do początku `deque`.|
|[rbegin](#rbegin)|Zwraca iterator dostępu losowego do pierwszego elementu w odwróconej `deque`.|
|[rend](#rend)|Zwraca iterator dostępu swobodnego, który wskazuje tuż za ostatnim elemencie w odwróconej `deque`.|
|[Zmiana rozmiaru](#resize)|Określa nowy rozmiar `deque`.|
|[shrink_to_fit](#shrink_to_fit)|Odrzuca nadmiarowej pojemności.|
|[Rozmiar](#size)|Zwraca liczbę elementów w `deque`.|
|[swap](#swap)|Zamienia elementy z dwóch `deque`s.|

### <a name="operators"></a>Operatory

|Operator|Opis|
|-|-|
|[operator&#91;&#93;](#op_at)|Zwraca odwołanie do `deque` elementu na określonej pozycji.|
|[operator=](#op_eq)|Zastępuje elementy `deque` kopią innego `deque`.|

## <a name="requirements"></a>Wymagania

**Nagłówek**: \<deque >

## <a name="allocator_type"></a>  deque::allocator_type

Typ, który reprezentuje klasę alokatora dla obiektu deque.

```cpp
typedef Allocator allocator_type;
```

### <a name="remarks"></a>Uwagi

`allocator_type` synonim dla parametru szablonu jest `Allocator`.

### <a name="example"></a>Przykład

Zobacz przykład [get_allocator —](#get_allocator).

## <a name="assign"></a>  deque::ASSIGN

Usuwa elementy z deque i kopiuje nowy zbiór elementów deque docelowej.

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

*pierwszy*<br/>
Pozycja pierwszego elementu w zakresie elementów, które mają być kopiowane z deque argumentu.

*ostatni*<br/>
Pozycja pierwszego elementu poza zakresem elementów, które mają być kopiowane z deque argumentu.

*Liczba*<br/>
Liczba kopii element jest wstawiany do deque.

*Val*<br/>
Wartość elementu jest wstawiany do deque.

*IList*<br/>
Lista initializer_list, jest wstawiany do deque.

### <a name="remarks"></a>Uwagi

Po usuwane są wszelkie elementy istniejących w deque docelowego, `assign` Wstawia określony zakres elementów z oryginalnego deque — lub innych deque — w deque docelowego lub wstawia kopii nowego elementu z określoną wartością do deque docelowej.

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

## <a name="at"></a>  deque::AT

Zwraca odwołanie do elementu w określonej lokalizacji w deque.

```cpp
reference at(size_type pos);

const_reference at(size_type pos) const;
```

### <a name="parameters"></a>Parametry

*punktu sprzedaży*<br/>
Indeks dolny lub numer pozycji elementu odwoływać się w deque.

### <a name="return-value"></a>Wartość zwracana

Jeśli *pos* jest większy niż rozmiar deque, `at` zgłasza wyjątek.

### <a name="return-value"></a>Wartość zwracana

Jeśli wartość zwracaną przez `at` jest przypisany do `const_reference`, nie można zmodyfikować obiektu deque. Jeśli wartość zwracaną przez `at` jest przypisany do `reference`, można zmodyfikować obiekt deque.

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

## <a name="back"></a>  deque::back

Zwraca odwołanie do ostatniego elementu deque.

```cpp
reference back();
const_reference back() const;
```

### <a name="return-value"></a>Wartość zwracana

Ostatniego elementu w deque. Jeśli deque jest pusta, zwracana wartość jest niezdefiniowana.

### <a name="remarks"></a>Uwagi

Jeśli wartość zwracaną przez `back` jest przypisany do `const_reference`, nie można zmodyfikować obiektu deque. Jeśli wartość zwracaną przez `back` jest przypisany do `reference`, można zmodyfikować obiekt deque.

Gdy kompilowany przy użyciu [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md) zdefiniowana jako 1 lub 2, wystąpi błąd czasu wykonywania przy próbie uzyskania dostępu do elementu w deque puste.  Zobacz [Checked Iterators](../standard-library/checked-iterators.md) Aby uzyskać więcej informacji.

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

## <a name="begin"></a>  deque::BEGIN

Zwraca iterator odnoszący się do pierwszego elementu w deque.

```cpp
const_iterator begin() const;
iterator begin();
```

### <a name="return-value"></a>Wartość zwracana

Iterator dostępu swobodnego, odnoszący się do pierwszego elementu w deque lub do lokalizacji następującej po pusty deque.

### <a name="remarks"></a>Uwagi

Jeśli wartość zwracaną przez `begin` jest przypisany do `const_iterator`, nie można zmodyfikować obiektu deque. Jeśli wartość zwracaną przez `begin` jest przypisany do `iterator`, można zmodyfikować obiekt deque.

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

## <a name="cbegin"></a>  deque::cbegin

Zwraca **const** iterator odnoszący się do pierwszego elementu w zakresie.

```cpp
const_iterator cbegin() const;
```

### <a name="return-value"></a>Wartość zwracana

A **const** iteratora dostępu swobodnego, który wskazuje na pierwszy element zakresu lub lokalizację tuż poza końcem pustego zakresu (dla pustego zakresu, `cbegin() == cend()`).

### <a name="remarks"></a>Uwagi

Wartością zwracaną `cbegin`, nie można modyfikować elementów w zakresie.

Można użyć tej funkcji elementu członkowskiego zamiast `begin()` funkcja elementu członkowskiego w celu zagwarantowania, że wartość zwracana jest `const_iterator`. Zazwyczaj jest używana w połączeniu z [automatycznie](../cpp/auto-cpp.md) wpisz słowem kluczowym dedukcji, jak pokazano w poniższym przykładzie. W tym przykładzie należy wziąć pod uwagę `Container` jako modyfikowalny (nie - `const`) kontener dowolnego rodzaju, który obsługuje `begin()` i `cbegin()`.

```cpp
auto i1 = Container.begin();
// i1 is Container<T>::iterator
auto i2 = Container.cbegin();

// i2 is Container<T>::const_iterator
```

## <a name="cend"></a>  deque::cend

Zwraca **const** iterator adresujący lokalizację tuż za ostatnim elementem w zakresie.

```cpp
const_iterator cend() const;
```

### <a name="return-value"></a>Wartość zwracana

Iterator dostępu swobodnego, który wskazuje tuż za koniec zakresu.

### <a name="remarks"></a>Uwagi

`cend` Służy do sprawdzenia, czy iterator minął koniec swojego zakresu.

Można użyć tej funkcji elementu członkowskiego zamiast `end()` funkcja elementu członkowskiego w celu zagwarantowania, że wartość zwracana jest `const_iterator`. Zazwyczaj jest używana w połączeniu z [automatycznie](../cpp/auto-cpp.md) wpisz słowem kluczowym dedukcji, jak pokazano w poniższym przykładzie. W tym przykładzie należy wziąć pod uwagę `Container` jako modyfikowalny (nie - **const**) kontener dowolnego rodzaju, który obsługuje `end()` i `cend()`.

```cpp
auto i1 = Container.end();
// i1 is Container<T>::iterator
auto i2 = Container.cend();

// i2 is Container<T>::const_iterator
```

Wartość zwrócona przez obiekt `cend` nie należy usuwać odwołania.

## <a name="clear"></a>  deque::Clear

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

## <a name="const_iterator"></a>  deque::const_iterator

Typ zapewniający iterator dostępu swobodnego, który można dostęp i możliwość odczytywania **const** elementu w deque.

```cpp
typedef implementation-defined const_iterator;
```

### <a name="remarks"></a>Uwagi

Typ `const_iterator` nie może służyć do modyfikowania wartości elementu.

### <a name="example"></a>Przykład

Zobacz przykład [ponownie](#back).

## <a name="const_pointer"></a>  deque::const_pointer

Zawiera wskaźnik do **const** elementu w deque.

```cpp
typedef typename Allocator::const_pointer const_pointer;
```

### <a name="remarks"></a>Uwagi

Typ `const_pointer` nie może służyć do modyfikowania wartości elementu. [Iteratora](#iterator) jest częściej używana do uzyskania dostępu do elementu deque.

## <a name="const_reference"></a>  deque::const_reference

Typ, który zawiera odwołanie do **const** elementu przechowywanego w deque do odczytu i wykonywania **const** operacji.

```cpp
typedef typename Allocator::const_reference const_reference;
```

### <a name="remarks"></a>Uwagi

Typ `const_reference` nie może służyć do modyfikowania wartości elementu.

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

## <a name="const_reverse_iterator"></a>  deque::const_reverse_iterator

Typ zapewniający iterator dostępu swobodnego, który może odczytać dowolny **const** elementu w deque.

```cpp
typedef std::reverse_iterator<const_iterator> const_reverse_iterator;
```

### <a name="remarks"></a>Uwagi

Typ `const_reverse_iterator` nie można zmodyfikować wartości elementu i jest używany do iterowania po deque w odwrotnej kolejności.

### <a name="example"></a>Przykład

Zobacz przykład [rbegin —](#rbegin) przykładowy sposób deklarowania i użyć iteratora.

## <a name="crbegin"></a>  deque::crbegin

Zwraca const iterator do pierwszego elementu w odwróconym deque.

```cpp
const_reverse_iterator crbegin() const;
```

### <a name="return-value"></a>Wartość zwracana

Stała odwrotnego iteratora dostępu swobodnego, odnoszący się do pierwszego elementu w odwróconej [deque](../standard-library/deque-class.md) lub adresowania, który był ostatnim elementem w nieodwróconej `deque`.

### <a name="remarks"></a>Uwagi

Wartością zwracaną `crbegin`, `deque` nie można zmodyfikować obiektu.

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

## <a name="crend"></a>  deque::crend

Zwraca iterator stałych adresujący lokalizację następującą po ostatnim elemencie w odwróconej deque.

```cpp
const_reverse_iterator crend() const;
```

### <a name="return-value"></a>Wartość zwracana

Stała odwrotnego iteratora dostępu swobodnego, który dotyczy lokalizacji następującej po ostatnim elemencie w odwróconej [deque](../standard-library/deque-class.md) (lokalizacja miał poprzedzony pierwszego elementu w deque nieodwróconej).

### <a name="remarks"></a>Uwagi

`crend` jest używana z odwróconej `deque` podobnie jak [array::cend](../standard-library/array-class-stl.md#cend) jest używana z `deque`.

Wartością zwracaną `crend` (odpowiednio odejmowane) `deque` nie można zmodyfikować obiektu.

`crend` można sprawdzać, czy wsteczny iterator osiągnął koniec swojej deque.

Wartość zwrócona przez obiekt `crend` nie należy usuwać odwołania.

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

## <a name="deque"></a>  deque::deque

Tworzy deque o określonym rozmiarze lub z elementami określonej wartości lub z określonego programu przydzielania lub jako kopię całości lub części niektórych innych deque.

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

|Parametr|Opis|
|-|-|
|*Al*|Klasa alokatora do wykorzystania z tym obiektem.|
|*Liczba*|Liczba elementów w stworzonego elementu deque.|
|*Val*|Wartość elementów w stworzonego elementu deque.|
|*po prawej stronie*|Deque, w której stworzonego elementu deque jest kopią.|
|*pierwszy*|Pozycja pierwszego elementu w zakresie elementów, które mają zostać skopiowane.|
|*ostatni*|Pozycja pierwszego elementu poza zakresem elementów, które mają zostać skopiowane.|
|* IList "| Initializer_list, który ma być skopiowany.|

### <a name="remarks"></a>Uwagi

Wszystkie konstruktory zapisują obiekt programu przydzielania (*Al*) i zainicjować deque.

Dwa pierwsze konstruktory określają pustą deque początkowej; drugi również określa typ programu przydzielania (`_Al`) ma być używany.

Trzeci Konstruktor określa powtórzenie określonej liczby (`count`) elementów wartości domyślnej dla klasy `Type`.

Czwarty i piąty Konstruktor określają powtórzenia (*liczba*) elementów wartości `val`.

Szósty Konstruktor Określa kopię deque *po prawej stronie*.

Siódmym i ósmym miesiącem konstruktory kopiują zakres `[First, Last)` elementu deque.

Siódmego Konstruktor przenosi deque *po prawej stronie*.

Konstruktor ósmego kopiuje zawartość initializer_list.

Żaden z konstruktorów wykonuje żadnych tymczasowych realokacji.

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

## <a name="difference_type"></a>  deque::difference_type

Typ, który zawiera różnicę między dwoma iteratorami odwołującymi się do elementów w obrębie tego samego deque.

```cpp
typedef typename Allocator::difference_type difference_type;
```

### <a name="remarks"></a>Uwagi

Element `difference_type` można również określić jako liczbę elementów między dwa wskaźniki.

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

## <a name="emplace"></a>  deque::emplace

Wstawia element skonstruowany w miejscu do deque na określonej pozycji.

```cpp
iterator emplace(
    const_iterator _Where,
    Type&& val);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|-|-|
|*_Where*|Pozycja w [deque](../standard-library/deque-class.md) polegający na wstawieniu pierwszego elementu.|
|*Val*|Wartość elementu jest wstawiany do `deque`.|

### <a name="return-value"></a>Wartość zwracana

Funkcja zwraca iterator, który wskazuje miejsce, gdy nowy element został wstawiony deque.

### <a name="remarks"></a>Uwagi

Wszelkie operacje wstawiania może być kosztowne, zobacz `deque` dyskusję na temat `deque` wydajności.

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

## <a name="emplace_back"></a>  deque::emplace_back

Dodaje element skonstruowany w miejscu do końca deque.

```cpp
void emplace_back(Type&& val);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|-|-|
|*Val*|Element dodany na końcu [deque](../standard-library/deque-class.md).|

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

## <a name="emplace_front"></a>  deque::emplace_front

Dodaje element skonstruowany w miejscu do końca deque.

```cpp
void emplace_front(Type&& val);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|-|-|
|*Val*|Element dodany do stanu sprzed [deque](../standard-library/deque-class.md).|

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

## <a name="empty"></a>  deque::Empty

Sprawdza, czy deque jest pusty.

```cpp
bool empty() const;
```

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli deque jest pusta. **false** Jeśli deque — nie jest pusty.

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

## <a name="end"></a>  deque::end

Zwraca iterator adresujący lokalizację następującą po ostatnim elemencie w deque.

```cpp
const_iterator end() const;

iterator end();
```

### <a name="return-value"></a>Wartość zwracana

Iterator dostępu swobodnego, który dotyczy lokalizacji następującej po ostatnim elemencie w deque. Jeśli deque jest pusty, a następnie deque::end == deque::begin.

### <a name="remarks"></a>Uwagi

`end` Służy do sprawdzenia, czy iterator osiągnął koniec swojej deque.

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

## <a name="erase"></a>  deque::ERASE

Usuwa element lub zakres elementów w deque z określonych pozycji.

```cpp
iterator erase(iterator _Where);

iterator erase(iterator first, iterator last);
```

### <a name="parameters"></a>Parametry

*_Where*<br/>
Pozycja elementu do usunięcia z deque.

*pierwszy*<br/>
Pozycja pierwszego elementu są usuwane z deque.

*last*<br/>
Pozycja tuż za ostatnim elementem usunięte z deque.

### <a name="return-value"></a>Wartość zwracana

Iterator dostępu swobodnego, który wskazuje na pierwszy element pozostający poza wszelkimi elementami usuniętymi lub wskaźnik do końca deque, jeśli taki element nie istnieje.

### <a name="remarks"></a>Uwagi

`erase` nigdy nie zgłasza wyjątek.

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

## <a name="front"></a>  deque::front

Zwraca odwołanie do pierwszego elementu w deque.

```cpp
reference front();

const_reference front() const;
```

### <a name="return-value"></a>Wartość zwracana

Jeśli deque jest pusta, zwracana wartość jest niezdefiniowana.

### <a name="remarks"></a>Uwagi

Jeśli wartość zwracaną przez `front` jest przypisany do `const_reference`, nie można zmodyfikować obiektu deque. Jeśli wartość zwracaną przez `front` jest przypisany do `reference`, można zmodyfikować obiekt deque.

Gdy kompilowany przy użyciu [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md) zdefiniowana jako 1 lub 2, wystąpi błąd czasu wykonywania przy próbie uzyskania dostępu do elementu w deque puste.  Zobacz [Checked Iterators](../standard-library/checked-iterators.md) Aby uzyskać więcej informacji.

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

## <a name="get_allocator"></a>  deque::get_allocator

Zwraca kopię obiektu programu przydzielania użytego do stworzenia deque.

```cpp
Allocator get_allocator() const;
```

### <a name="return-value"></a>Wartość zwracana

Alokator używany przez deque.

### <a name="remarks"></a>Uwagi

Puli buforów dla klasy deque — Określ, jak klasa zarządza magazynem. Buforów domyślną dostarczony wraz z klasy kontenera standardowej biblioteki języka C++ są wystarczające dla większości potrzeb programowania. Pisanie i przy użyciu klasy alokatora jest temat zaawansowany C++.

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

## <a name="insert"></a>  deque::INSERT

Wstawia element lub szereg elementów lub szereg elementów do deque na określonej pozycji.

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

|Parametr|Opis|
|-|-|
|*Where*|Pozycja w deque docelowej polegający na wstawieniu pierwszego elementu.|
|*Val*|Wartość elementu jest wstawiany do deque.|
|*Liczba*|Liczba elementów jest wstawiany do deque.|
|*pierwszy*|Pozycja pierwszego elementu w zakresie elementów w deque argument, który ma być skopiowany.|
|*ostatni*|Pozycja pierwszego elementu poza zakres elementów w deque argument, który ma być skopiowany.|
|*IList*|Lista initializer_list elementów do wstawienia.|

### <a name="return-value"></a>Wartość zwracana

Wstaw dwa pierwsze zwracają iterator, który wskazuje miejsce, gdy nowy element został wstawiony deque.

### <a name="remarks"></a>Uwagi

Wszelkie operacje wstawiania może być kosztowne.

## <a name="iterator"></a>  deque::iterator

Typ, który dostarcza iterator dostępu swobodnego, który może odczytać lub zmodyfikować dowolny element w deque.

```cpp
typedef implementation-defined iterator;
```

### <a name="remarks"></a>Uwagi

Typ `iterator` może służyć do modyfikowania wartości elementu.

### <a name="example"></a>Przykład

Zobacz przykład [rozpocząć](#begin).

## <a name="max_size"></a>  deque::max_size

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

## <a name="op_at"></a>  deque::operator]

Zwraca odwołanie do elementu deque na określonej pozycji.

```cpp
reference operator[](size_type pos);

const_reference operator[](size_type pos) const;
```

### <a name="parameters"></a>Parametry

*punktu sprzedaży*<br/>
Położenie elementu deque można odwoływać się.

### <a name="return-value"></a>Wartość zwracana

Odwołanie do elementu, w których pozycja jest określona w argumencie. Jeśli określona pozycja jest większy niż rozmiar deque, wynik jest niezdefiniowany.

### <a name="remarks"></a>Uwagi

Jeśli wartość zwracaną przez `operator[]` jest przypisany do `const_reference`, nie można zmodyfikować obiektu deque. Jeśli wartość zwracaną przez `operator[]` jest przypisany do `reference`, można zmodyfikować obiekt deque.

Gdy kompilowany przy użyciu [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md) zdefiniowana jako 1 lub 2, wystąpi błąd czasu wykonywania przy próbie uzyskania dostępu do elementu poza granicami deque.  Zobacz [Checked Iterators](../standard-library/checked-iterators.md) Aby uzyskać więcej informacji.

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

## <a name="op_eq"></a>  deque::operator =

Zastępuje elementy tego deque, korzystając z elementów, które z innego deque.

```cpp
deque& operator=(const deque& right);

deque& operator=(deque&& right);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|-|-|
|*right*|Deque, który zawiera nową zawartość.|

### <a name="remarks"></a>Uwagi

Pierwszy zastąpienie kopiuje elementy do tego deque z *prawo*, źródło przypisania. Drugi zastąpienie przenosi elementy do tego deque z *prawo*.

Elementy, które są zawarte w tym deque, przed wykonaniem operator są usuwane.

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

## <a name="pointer"></a>  deque::Pointer

Zawiera wskaźnik do elementu w [deque](../standard-library/deque-class.md).

```unstlib
typedef typename Allocator::pointer pointer;
```

### <a name="remarks"></a>Uwagi

Typ `pointer` może służyć do modyfikowania wartości elementu. [Iteratora](#iterator) jest częściej używana do uzyskania dostępu do elementu deque.

## <a name="pop_back"></a>  deque::pop_back

Usuwa element na końcu deque.

```cpp
void pop_back();
```

### <a name="remarks"></a>Uwagi

Ostatni element nie może być pusta. `pop_back` nigdy nie zgłasza wyjątek.

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

## <a name="pop_front"></a>  deque::pop_front

Usuwa element na początku deque.

```cpp
void pop_front();
```

### <a name="remarks"></a>Uwagi

Pierwszy element nie może być pusta. `pop_front` nigdy nie zgłasza wyjątek.

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

## <a name="push_back"></a>  deque::push_back

Dodaje element do końca deque.

```cpp
void push_back(const Type& val);

void push_back(Type&& val);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|-|-|
|*Val*|Element dodany na końcu deque.|

### <a name="remarks"></a>Uwagi

Jeśli wyjątek jest zgłaszany, deque pozostanie niezmieniony, a wyjątek jest zgłaszany ponownie.

## <a name="push_front"></a>  deque::push_front

Dodaje element do stanu sprzed deque.

```cpp
void push_front(const Type& val);
void push_front(Type&& val);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|-|-|
|*Val*|Element dodany na początku deque.|

### <a name="remarks"></a>Uwagi

Jeśli wyjątek jest zgłaszany, deque pozostanie niezmieniony, a wyjątek jest zgłaszany ponownie.

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

## <a name="rbegin"></a>  deque::rbegin

Zwraca iterator do pierwszego elementu w odwróconym deque.

```cpp
const_reverse_iterator rbegin() const;

reverse_iterator rbegin();
```

### <a name="return-value"></a>Wartość zwracana

Odwrotnego iteratora dostępu swobodnego odnoszący się do pierwszego elementu w odwróconym deque lub odnoszący się do ostatniego elementu w deque nieodwróconej był.

### <a name="remarks"></a>Uwagi

`rbegin` jest używana z odwróconej deque — podobnie jak [rozpocząć](#begin) jest używana z deque.

Jeśli wartość zwracaną przez `rbegin` jest przypisany do `const_reverse_iterator`, nie można zmodyfikować obiektu deque. Jeśli wartość zwracaną przez `rbegin` jest przypisany do `reverse_iterator`, można zmodyfikować obiekt deque.

`rbegin` może służyć do iterowania po deque Wstecz.

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

## <a name="reference"></a>  deque::Reference

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

## <a name="rend"></a>  deque::rend

Zwraca iterator adresujący lokalizację następującą po ostatnim elemencie w odwróconej deque.

```cpp
const_reverse_iterator rend() const;

reverse_iterator rend();
```

### <a name="return-value"></a>Wartość zwracana

Odwrotnego iteratora dostępu swobodnego, który dotyczy lokalizacji następującej po ostatnim elemencie w odwróconej deque (lokalizacja miał poprzedzony pierwszego elementu w deque nieodwróconej).

### <a name="remarks"></a>Uwagi

`rend` jest używana z odwróconej deque — podobnie jak [zakończenia](#end) jest używana z deque.

Jeśli wartość zwracaną przez `rend` jest przypisany do `const_reverse_iterator`, nie można zmodyfikować obiektu deque. Jeśli wartość zwracaną przez `rend` jest przypisany do `reverse_iterator`, można zmodyfikować obiekt deque.

`rend` może służyć do sprawdzenia, czy wsteczny iterator osiągnął koniec swojej deque.

Wartość zwrócona przez obiekt `rend` nie należy usuwać odwołania.

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

## <a name="resize"></a>  deque::Resize

Określa nowy rozmiar deque.

```cpp
void resize(size_type _Newsize);

void resize(size_type _Newsize, Type val);
```

### <a name="parameters"></a>Parametry

*_Newsize*<br/>
Nowy rozmiar deque.

*Val*<br/>
Wartość nowych elementów, które mają zostać dodane do deque, jeśli nowy rozmiar jest większy, oryginalnym rozmiarze. W przypadku pominięcia wartości, nowym elementom zostanie przypisana wartość domyślna dla klasy.

### <a name="remarks"></a>Uwagi

Jeśli deque rozmiar jest mniejszy niż rozmiar żądanej *_Newsize*, elementy są dodawane do deque, dopóki nie osiągnie żądanego rozmiaru.

Jeśli deque rozmiar jest większy niż wymagany, najbliższe końca deque — elementy zostaną usunięte, dopóki deque osiągnie rozmiar *_Newsize*.

Jeśli obecny rozmiar deque jest taki sam jak żądany rozmiar, nie podjęto żadnej akcji.

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

## <a name="reverse_iterator"></a>  deque::reverse_iterator

Typ, który dostarcza iterator dostępu swobodnego, który może odczytać lub zmodyfikować element w odwróconej deque.

```cpp
typedef std::reverse_iterator<iterator> reverse_iterator;
```

### <a name="remarks"></a>Uwagi

Typ `reverse_iterator` jest używany do iterowania po deque.

### <a name="example"></a>Przykład

Zobacz przykład dotyczący rbegin —.

## <a name="shrink_to_fit"></a>  deque::shrink_to_fit

Odrzuca nadmiarowej pojemności.

```cpp
void shrink_to_fit();
```

### <a name="remarks"></a>Uwagi

Nie istnieje sposób przenośne do określenia, czy `shrink_to_fit` zmniejsza miejsca używanego przez [deque](../standard-library/deque-class.md).

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

## <a name="size"></a>  deque::size

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

## <a name="size_type"></a>  deque::size_type

Typ, który zlicza liczbę elementów w deque.

```cpp
typedef typename Allocator::size_type size_type;
```

### <a name="example"></a>Przykład

Zobacz przykład [rozmiar](#size).

## <a name="swap"></a>  deque::swap

Zamienia elementy z dwóch deques.

```cpp
void swap(deque<Type, Allocator>& right);

friend void swap(deque<Type, Allocator>& left, deque<Type, Allocator>& right) template <class Type, class Allocator>
void swap(deque<Type, Allocator>& left, deque<Type, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*right*<br/>
Deque — zawierająca elementy, które mają być zamienione lub deque, której elementy są wymieniane z tymi deque `left`.

*left*<br/>
Deque, której elementy są wymieniane z tymi deque *prawo*.

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

## <a name="value_type"></a>  deque::value_type

Typ, który reprezentuje typ danych przechowywanych w deque.

```cpp
typedef typename Allocator::value_type value_type;
```

### <a name="remarks"></a>Uwagi

`value_type` synonim dla parametru szablonu jest `Type`.

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

## <a name="see-also"></a>Zobacz także

[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Dokumentacja standardowej biblioteki C++](../standard-library/cpp-standard-library-reference.md)<br/>
