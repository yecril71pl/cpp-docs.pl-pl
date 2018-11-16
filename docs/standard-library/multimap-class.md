---
title: multimap — Klasa
ms.date: 10/18/2018
f1_keywords:
- map/std::multimap
- map/std::multimap::allocator_type
- map/std::multimap::const_iterator
- map/std::multimap::const_pointer
- map/std::multimap::const_reference
- map/std::multimap::const_reverse_iterator
- map/std::multimap::difference_type
- map/std::multimap::iterator
- map/std::multimap::key_compare
- map/std::multimap::key_type
- map/std::multimap::mapped_type
- map/std::multimap::pointer
- map/std::multimap::reference
- map/std::multimap::reverse_iterator
- map/std::multimap::size_type
- map/std::multimap::value_type
- map/std::multimap::begin
- map/std::multimap::cbegin
- map/std::multimap::cend
- map/std::multimap::clear
- map/std::multimap::count
- map/std::multimap::crbegin
- map/std::multimap::crend
- map/std::multimap::emplace
- map/std::multimap::emplace_hint
- map/std::multimap::empty
- map/std::multimap::end
- map/std::multimap::equal_range
- map/std::multimap::erase
- map/std::multimap::find
- map/std::multimap::get_allocator
- map/std::multimap::insert
- map/std::multimap::key_comp
- map/std::multimap::lower_bound
- map/std::multimap::max_size
- map/std::multimap::rbegin
- map/std::multimap::rend
- map/std::multimap::size
- map/std::multimap::swap
- map/std::multimap::upper_bound
- map/std::multimap::value_comp
helpviewer_keywords:
- std::multimap [C++]
- std::multimap [C++], allocator_type
- std::multimap [C++], const_iterator
- std::multimap [C++], const_pointer
- std::multimap [C++], const_reference
- std::multimap [C++], const_reverse_iterator
- std::multimap [C++], difference_type
- std::multimap [C++], iterator
- std::multimap [C++], key_compare
- std::multimap [C++], key_type
- std::multimap [C++], mapped_type
- std::multimap [C++], pointer
- std::multimap [C++], reference
- std::multimap [C++], reverse_iterator
- std::multimap [C++], size_type
- std::multimap [C++], value_type
- std::multimap [C++], begin
- std::multimap [C++], cbegin
- std::multimap [C++], cend
- std::multimap [C++], clear
- std::multimap [C++], count
- std::multimap [C++], crbegin
- std::multimap [C++], crend
- std::multimap [C++], emplace
- std::multimap [C++], emplace_hint
- std::multimap [C++], empty
- std::multimap [C++], end
- std::multimap [C++], equal_range
- std::multimap [C++], erase
- std::multimap [C++], find
- std::multimap [C++], get_allocator
- std::multimap [C++], insert
- std::multimap [C++], key_comp
- std::multimap [C++], lower_bound
- std::multimap [C++], max_size
- std::multimap [C++], rbegin
- std::multimap [C++], rend
- std::multimap [C++], size
- std::multimap [C++], swap
- std::multimap [C++], upper_bound
- std::multimap [C++], value_comp
ms.assetid: 8796ae05-37c4-475a-9e61-75fde9d4a463
ms.openlocfilehash: caffa84052f774803b92730f7906bf53cb3c824a
ms.sourcegitcommit: d441305fb19131afbd7fc259d8cda63ea26f2343
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/15/2018
ms.locfileid: "51678525"
---
# <a name="multimap-class"></a>multimap — Klasa

Multimap — klasa standardowej biblioteki języka C++ jest używany do przechowywania i pobierania danych z kolekcji, w której każdy element jest parą, która ma zarówno wartość danych, jak i klucz sortowania. Wartość klucza nie musi unikatowa i jest używana do automatycznego porządkowania danych. Wartość elementu w mapie wielokrotnej, ale nie wartość jego skojarzonego klucza, może być zmieniona bezpośrednio. Zamiast tego, wartości kluczy skojarzone ze starymi elementami muszą zostać usunięte, a nowe wartości klucza skojarzone z nowymi wstawionymi elementami.

## <a name="syntax"></a>Składnia

```cpp
template <class Key,
    class Type,
    class Traits=less <Key>,
    class Allocator=allocator <pair  <const Key, Type>>>
class multimap;
```

### <a name="parameters"></a>Parametry

*Key*<br/>
Typ danych klucza, który ma być przechowywany w mapie wielokrotnej.

*Typ*<br/>
Typ danych elementu, który ma być przechowywany w mapie wielokrotnej.

*Cechy*<br/>
Typ, który dostarcza obiekt funkcji, która może porównać dwie wartości elementów jako klucze sortowania, aby określić ich względną kolejność w mapie wielokrotnej. Predykat dwuelementowy `less<Key>` jest wartością domyślną.

W języku C ++ 14 można włączyć heterogeniczne wyszukiwanie, określając `std::less<>` lub `std::greater<>` predykat, który nie ma parametrów typu. Aby uzyskać więcej informacji, zobacz [heterogeniczne wyszukiwanie w kontenerach asocjacyjnych](../standard-library/stl-containers.md#heterogeneous-lookup-in-associative-containers-c14)

*Allocator*<br/>
Typ reprezentujący przechowywany obiekt alokatora, który hermetyzuje szczegóły dotyczące alokacji mapy i dezalokacji pamięci. Ten argument jest opcjonalny, a wartość domyślna to `allocator<pair <const Key, Type> >`.

## <a name="remarks"></a>Uwagi

Multimap — klasa standardowej biblioteki języka C++ jest

- Kontenerem asocjacyjnym, który jest kontenerem o zmiennym rozmiarze, obsługującym efektywne pobieranie wartości elementu w oparciu o wartość skojarzonego klucza.

- Odwracalny, ponieważ zapewnia dwukierunkowe iteratory do dostępu do jego elementów.

- Posortowany, ponieważ jego elementy są uporządkowane według wartości kluczy w kontenerze zgodnie z określoną funkcją porównywania.

- Wielokrotna, ponieważ jej elementy nie muszą mieć unikatowych kluczy, więc jedna wartość klucza może mieć wiele wartości elementów danych z nią skojarzonych.

- Kontenerem skojarzonych par, ponieważ jej wartości danych elementu różnią się od wartości klucza.

- Klasą szablonu, ponieważ funkcjonalność, którą zapewnia, jest generyczna i dlatego niezależna od określonego typu danych zawartych jako elementy lub klucze. Typy danych, których można użyć dla elementów i kluczy, są zamiast tego określane jako parametry w szablonie klasy, wraz z funkcją porównania oraz alokatorem.

Iterator dostarczony przez klasę mapy jest iteratorem dwukierunkowym, ale funkcje składowych klasy [Wstaw](#insert) i [multimap](#multimap) mają wersje przyjmujące jako parametry szablonu słabszy iterator danych wejściowych, którego wymagania funkcjonalności są mniejsze niż te gwarantowane przez klasę iteratorów dwukierunkowych. Pojęcia innych iteratorów formują rodzinę powiązaną przez udoskonalenia w ich funkcjonalnościach. Każde pojęcie iteratora ma swój własny zestaw wymagań, a algorytmy z nimi pracujące muszą ograniczać swoje założenia co do wymagań dostarczonych przez tego typu iterator. Można założyć, że z iteratora danych wejściowych można usunąć odwołanie, aby odwołać się do obiektu, a także, że może on być zwiększony do następnego iteratora w sekwencji. Jest to minimalny zestaw funkcjonalności, ale jest wystarczający, aby można było mówić znacząco o zakresie iteratorów `[First, Last)` w kontekście funkcji składowych klasy.

Wybór typu kontenera powinien ogólnie być oparty o typ wyszukiwania i wstawiania wymagany przez aplikację. Kontenery asocjacyjne są zoptymalizowane dla operacji wyszukiwania, wstawiania oraz usuwania. Funkcje elementów członkowskich, które jawnie obsługują te operacje, są skuteczne, wykonując je w czasie, który jest średnio proporcjonalny do logarytmu liczby elementów w kontenerze. Wstawianie elementów nie unieważnia iteratorów, a usuwanie elementów unieważnia tylko te iteratory, które w szczególności wskazywały na usunięte elementy.

Mapa wielokrotna powinna być kontenerem asocjacyjnym z wyboru, gdy warunki kojarzenia wartości z kluczami są spełnione przez aplikację. Modelem dla tego typu struktury jest uporządkowana lista słów kluczowych ze skojarzonymi wartościami ciągów, dostarczająca np. definicje, w których słowa nie były zawsze zdefiniowane unikalnie. Jeśli zamiast tego słowa kluczowe zostały unikalnie zdefiniowane, tak że klucze są unikalne, wybranym kontenerem będzie map. Jeśli z drugiej strony, przechowywana była tylko lista wyrazów, poprawnym kontenerem będzie set. Jeżeli zezwolono na wiele wystąpień wyrazów, odpowiednią strukturą kontenera będzie multiset.

Mapa wielokrotna porządkuje sekwencję którą kontroluje, przez wywołanie przechowywanego obiektu funkcji typu [key_compare](#key_compare). Ten przechowywany obiekt jest funkcją porównywania, która może być dostępna poprzez wywołanie funkcji elementu członkowskiego [key_comp](#key_comp). Ogólnie rzecz biorąc, elementy muszą być nieco mniej porównywalne, aby ustalić kolejność: tak aby, mając dowolne dwa elementy, można było określić, czy są one równoważne (w sensie, żaden nie jest mniejszy niż ten drugi) lub, że jeden jest mniejszy niż ten drugi. Skutkuje to ustaleniem kolejności dla elementów nierównoważnych. Ze strony bardziej technicznej, funkcja porównywania jest predykatem binarnym, który wymusza ścisłe słabe porządkowanie w standardowym sensie matematycznym. Binarny predykat `f(x,y)` jest obiektem funkcji, która ma dwa obiekty argumentu `x` i `y` oraz wartość zwracaną true lub false. Kolejność nałożona na zestaw jest ścisłym słabym porządkowaniem, jeśli predykat binarny jest niezwrotny, przeciwsymetryczny i przechodni oraz jeśli równoważność jest przechodnia, gdzie dwa obiekty `x` i `y` są zdefiniowane jako równoważne, gdy oba `f(x,y)`i `f(y,x)` mają wartość false. Jeśli silniejszy warunek równości pomiędzy kluczami zastąpi ten równoważności, to porządkowanie będzie całkowite (w sensie, że wszystkie elementy są uporządkowane względem siebie), a dopasowane klucze będą od siebie nieodróżnialne.

W języku C ++ 14 można włączyć heterogeniczne wyszukiwanie, określając `std::less<>` lub `std::greater<>` predykat, który nie ma parametrów typu. Aby uzyskać więcej informacji, zobacz [heterogeniczne wyszukiwanie w kontenerach asocjacyjnych](../standard-library/stl-containers.md#sequence_containers)

## <a name="members"></a>Elementy członkowskie

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[multimap](#multimap)|Konstruuje `multimap` oznacza to pusta lub czyli kopią całości lub części innej `multimap`.|

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[allocator_type](#allocator_type)|Typ, który reprezentuje `allocator` klasy dla `multimap` obiektu.|
|[const_iterator](#const_iterator)|Typ, który dostarcza iterator dwukierunkowy, który może odczytać **const** element `multimap`.|
|[const_pointer](#const_pointer)|Typ, który dostarcza wskaźnik do **const** element `multimap`.|
|[const_reference](#const_reference)|Typ, który zawiera odwołanie do **const** przechowywanego w `multimap` do odczytu i wykonywania **const** operacji.|
|[const_reverse_iterator](#const_reverse_iterator)|Typ, który dostarcza iterator dwukierunkowy, który może odczytać dowolny **const** element `multimap`.|
|[difference_type](#difference_type)|Typ liczby całkowitej ze znakiem, który może służyć do reprezentowania liczby elementów `multimap` w zakresie pomiędzy elementami wskazywanymi przez Iteratory.|
|[iterator](#iterator)|Typ, który zawiera różnicę między dwoma iteratorami odwołującymi się do elementów w tym samym `multimap`.|
|[key_compare —](#key_compare)|Typ, który dostarcza obiekt funkcji, która może porównać dwa klucze sortowania, aby określić względną kolejność dwóch elementów w `multimap`.|
|[key_type](#key_type)|Typ, który opisuje obiekt klucza sortowania, stanowiący każdy element obiektu `multimap`.|
|[mapped_type](#mapped_type)|Typ, który reprezentuje typ danych przechowywanych w `multimap`.|
|[pointer](#pointer)|Typ, który dostarcza wskaźnik do **const** element `multimap`.|
|[Odwołanie](#reference)|Typ, który zawiera odwołanie do elementu przechowywanego w `multimap`.|
|[reverse_iterator](#reverse_iterator)|Typ, który dostarcza iterator dwukierunkowy, który może odczytać lub zmodyfikować element w odwróconej `multimap`.|
|[size_type](#size_type)|Typ całkowitoliczbowy bez znaku, który dostarcza wskaźnik do **const** element `multimap`.|
|[value_type](#value_type)|Typ, który dostarcza obiekt funkcji, która może porównać dwa elementy jako klucze sortowania, aby określić ich względną kolejność w `multimap`.|

### <a name="member-functions"></a>Funkcje Członkowskie

|Funkcja elementu członkowskiego|Opis|
|-|-|
|[begin](#begin)|Zwraca iterator odnoszący się do pierwszego elementu w `multimap`.|
|[cbegin](#cbegin)|Zwraca iterator stałych adresujący pierwszy element w `multimap`.|
|[cend](#cend)|Zwraca iterator const, który dotyczy lokalizacji następującej po ostatnim elemencie w `multimap`.|
|[Usuń zaznaczenie](#clear)|Usuwa wszystkie elementy `multimap`.|
|[Liczba](#count)|Zwraca liczbę elementów w `multimap` których klucz pasuje do klucza określonego jako parametr.|
|[crbegin](#crbegin)|Zwraca iterator stałych adresujący pierwszy element w odwróconej `multimap`.|
|[crend —](#crend)|Zwraca iterator stałych adresujący lokalizację następującą po ostatnim elemencie w odwróconej `multimap`.|
|[emplace —](#emplace)|Wstawia element skonstruowany w miejscu do `multimap`.|
|[emplace_hint](#emplace_hint)|Wstawia element skonstruowany w miejscu do `multimap`, ze wskazówką położenia|
|[pusty](#empty)|Sprawdza, czy `multimap` jest pusty.|
|[koniec](#end)|Zwraca iterator adresujący lokalizację następującą po ostatnim elemencie w `multimap`.|
|[equal_range](#equal_range)|Wyszukuje zakres elementów, gdzie klucz elementu pasuje do określonej wartości.|
|[wymazywanie](#erase)|Usuwa element lub zakres elementów w `multimap` z określonych pozycji lub usuwa elementy, które odpowiadają określonemu kluczowi.|
|[Znajdź](#find)|Zwraca iterator odnoszący się do pierwszej lokalizacji elementu w `multimap` który ma klucz równoważny z określonym kluczem.|
|[get_allocator](#get_allocator)|Zwraca kopię obiektu `allocator` użytego do stworzenia `multimap`.|
|[Wstaw](#insert)|Wstawia element lub zakres elementów do `multimap`.|
|[key_comp](#key_comp)|Pobiera kopię obiektu porównania użytego do uporządkowania kluczy w `multimap`.|
|[lower_bound](#lower_bound)|Zwraca iterator do pierwszego elementu w `multimap` , wraz z kluczem, który jest równy lub większy od określonego klucza.|
|[max_size](#max_size)|Zwraca maksymalną długość `multimap`.|
|[rbegin](#rbegin)|Zwraca iterator odnoszący się do pierwszego elementu w odwróconej `multimap`.|
|[rend —](#rend)|Zwraca iterator adresujący lokalizację następującą po ostatnim elemencie w odwróconej `multimap`.|
|[Rozmiar](#size)|Zwraca liczbę elementów w `multimap`.|
|[swap](#swap)|Zamienia elementy z dwóch `multimap`s.|
|[upper_bound —](#upper_bound)|Zwraca iterator do pierwszego elementu w `multimap` , wraz z kluczem, który jest większy od określonego klucza.|
|[value_comp](#value_comp)|Funkcja elementu członkowskiego zwraca obiekt funkcji, która określa kolejność elementów w `multimap` przez porównanie ich wartości klucza.|

### <a name="operators"></a>Operatory

|Operator|Opis|
|-|-|
|[operator=](#op_eq)|Zastępuje elementy `multimap` kopią innego `multimap`.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<mapy >

**Namespace:** standardowe

( **Klucz**, **wartość**) pary są przechowywane w mapie wielokrotnej jako obiekty typu `pair`. Klasa pary wymaga nagłówka \<Narzędzia >, który jest automatycznie dołączany przez \<map >.

## <a name="allocator_type"></a>  multimap::allocator_type

Typ, który reprezentuje klasę alokatora dla obiektu multimap.

```cpp
typedef Allocator allocator_type;
```

### <a name="example"></a>Przykład

Zobacz przykład [get_allocator —](#get_allocator) dla przykłady dotyczące używania `allocator_type`.

## <a name="begin"></a>  multimap::BEGIN

Zwraca iterator adresujący pierwszy element w mapie wielokrotnej.

```cpp
const_iterator begin() const;

iterator begin();
```

### <a name="return-value"></a>Wartość zwracana

Iterator dwukierunkowy odnoszący się do pierwszego elementu w mapie wielokrotnej lub lokalizacji następującej po multimap puste.

### <a name="example"></a>Przykład

```cpp
// multimap_begin.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   multimap <int, int> m1;

   multimap <int, int> :: iterator m1_Iter;
   multimap <int, int> :: const_iterator m1_cIter;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 0, 0 ) );
   m1.insert ( Int_Pair ( 1, 1 ) );
   m1.insert ( Int_Pair ( 2, 4 ) );

   m1_cIter = m1.begin ( );
   cout << "The first element of m1 is " << m1_cIter -> first << endl;

   m1_Iter = m1.begin ( );
   m1.erase ( m1_Iter );

   // The following 2 lines would err as the iterator is const
   // m1_cIter = m1.begin ( );
   // m1.erase ( m1_cIter );

   m1_cIter = m1.begin( );
   cout << "First element of m1 is now " << m1_cIter -> first << endl;
}
```

```Output
The first element of m1 is 0
First element of m1 is now 1
```

## <a name="cbegin"></a>  multimap::cbegin

Zwraca **const** iterator odnoszący się do pierwszego elementu w zakresie.

```cpp
const_iterator cbegin() const;
```

### <a name="return-value"></a>Wartość zwracana

A **const** iterator dostępu dwukierunkowego, który wskazuje na pierwszy element zakresu lub lokalizację tuż poza końcem pustego zakresu (dla pustego zakresu, `cbegin() == cend()`).

### <a name="remarks"></a>Uwagi

Wartością zwracaną `cbegin`, nie można modyfikować elementów w zakresie.

Można użyć tej funkcji elementu członkowskiego zamiast `begin()` funkcja elementu członkowskiego w celu zagwarantowania, że wartość zwracana jest `const_iterator`. Zazwyczaj jest używana w połączeniu z [automatycznie](../cpp/auto-cpp.md) wpisz słowem kluczowym dedukcji, jak pokazano w poniższym przykładzie. W tym przykładzie należy wziąć pod uwagę `Container` jako modyfikowalny (nie - **const**) kontener dowolnego rodzaju, który obsługuje `begin()` i `cbegin()`.

```cpp
auto i1 = Container.begin();
// i1 is Container<T>::iterator
auto i2 = Container.cbegin();

// i2 is Container<T>::const_iterator
```

## <a name="cend"></a>  multimap::cend

Zwraca **const** iterator adresujący lokalizację tuż za ostatnim elementem w zakresie.

```cpp
const_iterator cend() const;
```

### <a name="return-value"></a>Wartość zwracana

A **const** iterator dostępu dwukierunkowego, który wskazuje tuż za koniec zakresu.

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

## <a name="clear"></a>  multimap::Clear

Usuwa wszystkie elementy mapie wielokrotnej.

```cpp
void clear();
```

### <a name="example"></a>Przykład

Poniższy przykład demonstruje użycie multimap::clear funkcja elementu członkowskiego.

```cpp
// multimap_clear.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   multimap<int, int> m1;
   multimap<int, int>::size_type i;
   typedef pair<int, int> Int_Pair;

   m1.insert(Int_Pair(1, 1));
   m1.insert(Int_Pair(2, 4));

   i = m1.size();
   cout << "The size of the multimap is initially "
        << i << "." << endl;

   m1.clear();
   i = m1.size();
   cout << "The size of the multimap after clearing is "
        << i << "." << endl;
}
```

```Output
The size of the multimap is initially 2.
The size of the multimap after clearing is 0.
```

## <a name="const_iterator"></a>  multimap::const_iterator

Typ, który dostarcza iterator dwukierunkowy, który może odczytać **const** element w mapie wielokrotnej.

```cpp
typedef implementation-defined const_iterator;
```

### <a name="remarks"></a>Uwagi

Typ `const_iterator` nie może służyć do modyfikowania wartości elementu.

`const_iterator` Zdefiniowane przez multimap — punkty do obiektów [value_type](#value_type), które są typu `pair<const Key, Type>`. Wartość klucza jest dostępna za pośrednictwem pary pierwszego elementu członkowskiego, a wartość elementu zmapowanego jest dostępna za pośrednictwem drugiego elementu członkowskiego pary.

Próbę `const_iterator` *cIter* wskazuje element w mapie wielokrotnej, użyj **->** operatora.

Aby uzyskać dostęp do wartości klucza dla elementu, należy użyć `cIter->first`, który jest odpowiednikiem `(*cIter).first`. Aby uzyskać dostęp do wartości zamapowanego datum dla elementu, należy użyć `cIter->second`, który jest odpowiednikiem `(*cIter).second`.

### <a name="example"></a>Przykład

Zobacz przykład [rozpocząć](#begin) dla przykłady dotyczące używania `const_iterator`.

## <a name="const_pointer"></a>  multimap::const_pointer

Typ, który dostarcza wskaźnik do **const** element w mapie wielokrotnej.

```cpp
typedef typename allocator_type::const_pointer const_pointer;
```

### <a name="remarks"></a>Uwagi

Typ `const_pointer` nie może służyć do modyfikowania wartości elementu.

W większości przypadków [iteratora](#iterator) powinien być używany do uzyskania dostępu do elementów w obiekcie multimap.

## <a name="const_reference"></a>  multimap::const_reference

Typ, który zawiera odwołanie do **const** elementu przechowywanego w mapie wielokrotnej do odczytu i wykonywania **const** operacji.

```cpp
typedef typename allocator_type::const_reference const_reference;
```

### <a name="example"></a>Przykład

```cpp
// multimap_const_ref.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   multimap <int, int> m1;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 1, 10 ) );
   m1.insert ( Int_Pair ( 2, 20 ) );

   // Declare and initialize a const_reference &Ref1
   // to the key of the first element
   const int &Ref1 = ( m1.begin( ) -> first );

   // The following line would cause an error because the
   // non-const_reference cannot be used to access the key
   // int &Ref1 = ( m1.begin( ) -> first );

   cout << "The key of the first element in the multimap is "
        << Ref1 << "." << endl;

   // Declare and initialize a reference &Ref2
   // to the data value of the first element
   int &Ref2 = ( m1.begin( ) -> second );

   cout << "The data value of the first element in the multimap is "
        << Ref2 << "." << endl;
}
```

```Output
The key of the first element in the multimap is 1.
The data value of the first element in the multimap is 10.
```

## <a name="const_reverse_iterator"></a>  multimap::const_reverse_iterator

Typ, który dostarcza iterator dwukierunkowy, który może odczytać dowolny **const** element w mapie wielokrotnej.

```cpp
typedef std::reverse_iterator<const_iterator> const_reverse_iterator;
```

### <a name="remarks"></a>Uwagi

Typ `const_reverse_iterator` nie można zmodyfikować wartości elementu i jest używany do iterowania po multimap w odwrotnej kolejności.

`const_reverse_iterator` Zdefiniowane przez multimap — punkty do obiektów [value_type](#value_type), które są typu `pair<const Key, Type>`. Wartość klucza jest dostępna za pośrednictwem pary pierwszego elementu członkowskiego, a wartość elementu zmapowanego jest dostępna za pośrednictwem drugiego elementu członkowskiego pary.

Próbę `const_reverse_iterator` *crIter* wskazuje element w mapie wielokrotnej, użyj **->** operatora.

Aby uzyskać dostęp do wartości klucza dla elementu, należy użyć `crIter->first`, który jest odpowiednikiem `(*crIter).first`. Aby uzyskać dostęp do wartości zamapowanego datum dla elementu, należy użyć `crIter->second`, który jest odpowiednikiem `(*crIter).first`.

### <a name="example"></a>Przykład

Zobacz przykład [rend —](#rend) przykładowy sposób deklarowania i użyj `const_reverse_iterator`.

## <a name="count"></a>  multimap::Count

Zwraca liczbę elementów w mapie wielokrotnej, których klucze odpowiadają kluczowi określony parametr.

```cpp
size_type count(const Key& key) const;
```

### <a name="parameters"></a>Parametry

*Klucz*<br/>
Klucz elementy, które mają być dopasowywane w mapie wielokrotnej.

### <a name="return-value"></a>Wartość zwracana

Liczba elementów, których klucze sortowania, zgodny z kluczem parametru; 0, jeśli Mapa wielokrotna nie zawierają element z kluczem dopasowania.

### <a name="remarks"></a>Uwagi

Element członkowski funkcji zwraca liczbę elementów w zakresie

\[ lower_bound (*klucz*), upper_bound (*klucz*))

które mają wartość klucza *klucz*.

### <a name="example"></a>Przykład

Poniższy przykład demonstruje użycie multimap::count funkcja elementu członkowskiego.

```cpp
// multimap_count.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
    using namespace std;
    multimap<int, int> m1;
    multimap<int, int>::size_type i;
    typedef pair<int, int> Int_Pair;

    m1.insert(Int_Pair(1, 1));
    m1.insert(Int_Pair(2, 1));
    m1.insert(Int_Pair(1, 4));
    m1.insert(Int_Pair(2, 1));

    // Elements do not need to have unique keys in multimap,
    // so duplicates are allowed and counted
    i = m1.count(1);
    cout << "The number of elements in m1 with a sort key of 1 is: "
         << i << "." << endl;

    i = m1.count(2);
    cout << "The number of elements in m1 with a sort key of 2 is: "
         << i << "." << endl;

    i = m1.count(3);
    cout << "The number of elements in m1 with a sort key of 3 is: "
         << i << "." << endl;
}
```

```Output
The number of elements in m1 with a sort key of 1 is: 2.
The number of elements in m1 with a sort key of 2 is: 2.
The number of elements in m1 with a sort key of 3 is: 0.
```

## <a name="crbegin"></a>  multimap::crbegin

Zwraca iterator stałych adresujący pierwszy element w odwróconej mapie wielokrotnej.

```cpp
const_reverse_iterator crbegin() const;
```

### <a name="return-value"></a>Wartość zwracana

Stała odwrotnego iterator dwukierunkowy odnoszący się do pierwszego elementu w odwróconej [multimap](../standard-library/multimap-class.md) lub adresowania, który był ostatnim elementem w nieodwróconej `multimap`.

### <a name="remarks"></a>Uwagi

`crbegin` jest używana z odwróconej `multimap` podobnie jak [rozpocząć](#begin) jest używana z `multimap`.

Wartością zwracaną `crbegin`, `multimap` nie można zmodyfikować obiektu.

`crbegin` może służyć do iterowania po `multimap` Wstecz.

### <a name="example"></a>Przykład

```cpp
// multimap_crbegin.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   multimap <int, int> m1;

   multimap <int, int> :: const_reverse_iterator m1_crIter;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 1, 10 ) );
   m1.insert ( Int_Pair ( 2, 20 ) );
   m1.insert ( Int_Pair ( 3, 30 ) );

   m1_crIter = m1.crbegin( );
   cout << "The first element of the reversed multimap m1 is "
        << m1_crIter -> first << "." << endl;
}
```

```Output
The first element of the reversed multimap m1 is 3.
```

## <a name="crend"></a>  multimap::crend

Zwraca iterator stałych adresujący lokalizację następującą po ostatnim elemencie w odwróconej mapie wielokrotnej.

```cpp
const_reverse_iterator crend() const;
```

### <a name="return-value"></a>Wartość zwracana

Stała odwrotnego iteratora dwukierunkowego, który dotyczy lokalizacji następującej po ostatnim elemencie w odwróconej [multimap](../standard-library/multimap-class.md) (miejsca przed pierwszym elementem w nieodwróconej `multimap`).

### <a name="remarks"></a>Uwagi

`crend` jest używana z odwróconej `multimap` podobnie jak [multimap::end](#end) jest używana z `multimap`.

Wartością zwracaną `crend`, `multimap` nie można zmodyfikować obiektu.

`crend` można sprawdzać, czy wsteczny iterator osiągnął koniec swojej `multimap`.

Wartość zwrócona przez obiekt `crend` nie należy usuwać odwołania.

### <a name="example"></a>Przykład

```cpp
// multimap_crend.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   multimap <int, int> m1;

   multimap <int, int> :: const_reverse_iterator m1_crIter;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 1, 10 ) );
   m1.insert ( Int_Pair ( 2, 20 ) );
   m1.insert ( Int_Pair ( 3, 30 ) );

   m1_crIter = m1.crend( );
   m1_crIter--;
   cout << "The last element of the reversed multimap m1 is "
        << m1_crIter -> first << "." << endl;
}
```

```Output
The last element of the reversed multimap m1 is 1.
```

## <a name="difference_type"></a>  multimap::difference_type

Typ liczby całkowitej ze znakiem, który może służyć do reprezentowania liczby elementów w mapie wielokrotnej w zakresie pomiędzy elementami wskazywanymi przez Iteratory.

```cpp
typedef typename allocator_type::difference_type difference_type;
```

### <a name="remarks"></a>Uwagi

`difference_type` Jest typ zwracany, jeśli odjęcie lub inkrementacji poprzez Iteratory kontenera. `difference_type` Jest zazwyczaj używany do reprezentowania liczby elementów w zakresie [*pierwszy*, *ostatniego*) między Iteratory `first` i `last`, zawiera element wskazane przez `first` i zakres elementów do, z wyjątkiem element wskazywany przez `last`.

Należy pamiętać, że chociaż `difference_type` jest dostępna dla wszystkich iteratorów, które spełniają wymagania iteratora danych wejściowych zawiera klasę iteratorów dwukierunkowych obsługiwane przez odwracalnego kontenerów, takie jak zestaw, odejmowania między Iteratory są tylko obsługiwane przez Iteratory dostępu swobodnego, dostarczone przez kontener dostępu swobodnego, takich jak wektora.

### <a name="example"></a>Przykład

```cpp
// multimap_diff_type.cpp
// compile with: /EHsc
#include <iostream>
#include <map>
#include <algorithm>

int main( )
{
   using namespace std;
   multimap <int, int> m1;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 2, 20 ) );
   m1.insert ( Int_Pair ( 1, 10 ) );
   m1.insert ( Int_Pair ( 3, 20 ) );

   // The following will insert as multimap keys are not unique
   m1.insert ( Int_Pair ( 2, 30 ) );

   multimap <int, int>::iterator m1_Iter, m1_bIter, m1_eIter;
   m1_bIter = m1.begin( );
   m1_eIter = m1.end( );

   // Count the number of elements in a multimap
   multimap <int, int>::difference_type  df_count = 0;
   m1_Iter = m1.begin( );
   while ( m1_Iter != m1_eIter )
   {
      df_count++;
      m1_Iter++;
   }

   cout << "The number of elements in the multimap m1 is: "
        << df_count << "." << endl;
}
```

```Output
The number of elements in the multimap m1 is: 4.
```

## <a name="emplace"></a>  multimap::emplace

Wstawia element skonstruowany w miejscu (nie kopiowania lub przenoszenia operacji).

```cpp
template <class... Args>
iterator emplace(Args&&... args);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|-|-|
|*argumenty*|Argumenty przekazywane do konstruowania element do wstawienia w mapie wielokrotnej.|

### <a name="return-value"></a>Wartość zwracana

Iterator do nowo wstawionego elementu.

### <a name="remarks"></a>Uwagi

Nie odwołania do elementów kontenera nie są unieważniane przez tę funkcję, ale może unieważnić, wszystkie Iteratory do kontenera.

Jeśli wyjątek jest zgłaszany podczas wstawiania, kontener pozostanie niezmieniony, a wyjątek jest zgłaszany ponownie.

[Value_type](../standard-library/map-class.md#value_type) elementu jest parą, tak aby wartość elementu zostanie uporządkowana para z pierwszym składnikiem równa wartości klucza i składnik sekundy wartości danych elementu.

### <a name="example"></a>Przykład

```cpp
// multimap_emplace.cpp
// compile with: /EHsc
#include <map>
#include <string>
#include <iostream>

using namespace std;

template <typename M> void print(const M& m) {
    cout << m.size() << " elements: " << endl;

    for (const auto& p : m) {
        cout << "(" << p.first <<  "," << p.second << ") ";
    }

    cout << endl;
}

int main()
{
    multimap<string, string> m1;

    m1.emplace("Anna", "Accounting");
    m1.emplace("Bob", "Accounting");
    m1.emplace("Carmine", "Engineering");

    cout << "multimap modified, now contains ";
    print(m1);
    cout << endl;

    m1.emplace("Bob", "Engineering");

    cout << "multimap modified, now contains ";
    print(m1);
    cout << endl;
}
```

## <a name="emplace_hint"></a>  multimap::emplace_hint

Wstawia element skonstruowany w miejscu (nie kopiowania lub przenoszenia operacji), ze wskazówką położenia.

```cpp
template <class... Args>
iterator emplace_hint(
    const_iterator where,
    Args&&... args);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|-|-|
|*argumenty*|Argumenty przekazywane do konstruowania element do wstawienia w mapie wielokrotnej.|
|*gdzie*|Miejsce, aby rozpocząć wyszukiwanie poprawne punktu wstawiania. (Jeśli danego punktu bezpośrednio poprzedza *gdzie*, wstawiania może wystąpić w amortyzowanym stałym czasie zamiast czasu logarytmicznych.)|

### <a name="return-value"></a>Wartość zwracana

Iterator do nowo wstawionego elementu.

### <a name="remarks"></a>Uwagi

Nie odwołania do elementów kontenera nie są unieważniane przez tę funkcję, ale może unieważnić, wszystkie Iteratory do kontenera.

Podczas umieszczanie Jeśli wyjątek jest zgłaszany, stan kontenera nie jest modyfikowany.

[Value_type](../standard-library/map-class.md#value_type) elementu jest parą, tak aby wartość elementu zostanie uporządkowana para z pierwszym składnikiem równa wartości klucza i składnik sekundy wartości danych elementu.

Dla przykładu kodu zobacz [map::emplace_hint](../standard-library/map-class.md#emplace_hint).

## <a name="empty"></a>  multimap::Empty

Sprawdza, czy mapa wielokrotna jest pusty.

```cpp
bool empty() const;
```

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli mapa wielokrotna jest pusta. **false** przypadku niepustych mapie wielokrotnej.

### <a name="example"></a>Przykład

```cpp
// multimap_empty.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   multimap <int, int> m1, m2;

   typedef pair <int, int> Int_Pair;
   m1.insert ( Int_Pair ( 1, 1 ) );

   if ( m1.empty( ) )
      cout << "The multimap m1 is empty." << endl;
   else
      cout << "The multimap m1 is not empty." << endl;

   if ( m2.empty( ) )
      cout << "The multimap m2 is empty." << endl;
   else
      cout << "The multimap m2 is not empty." << endl;
}
```

```Output
The multimap m1 is not empty.
The multimap m2 is empty.
```

## <a name="end"></a>  multimap::end

Zwraca iterator poza końcem.

```cpp
const_iterator end() const;

iterator end();
```

### <a name="return-value"></a>Wartość zwracana

Iterator przeszłości zakończenia. Jeśli mapa wielokrotna jest pusta, następnie `multimap::end() == multimap::begin()`.

### <a name="remarks"></a>Uwagi

**koniec** służy do sprawdzenia, czy iterator minął koniec jego multimap.

Wartość zwrócona przez obiekt **zakończenia** nie należy usuwać odwołania.

Dla przykładu kodu zobacz [multimap::find](#find).

## <a name="equal_range"></a>  multimap::equal_range

Wyszukuje zakres elementów, gdzie klucz elementu pasuje do określonej wartości.

```cpp
pair <const_iterator, const_iterator> equal_range (const Key& key) const;

pair <iterator, iterator> equal_range (const Key& key);
```

### <a name="parameters"></a>Parametry

*Klucz*<br/>
Argument klucza, który ma zostać porównane z klucza sortowania elementu w mapie wielokrotnej wyszukiwany.

### <a name="return-value"></a>Wartość zwracana

Parę iteratorów tak, aby był pierwszym [lower_bound](#lower_bound) klucz, a drugi jest [upper_bound](#upper_bound) klucza.

Pierwszym iteratorem pary dostęp do `pr` zwróconą przez funkcję elementu członkowskiego, użyj `pr`. **pierwszy** wyłuskać iteratora dolną granicę użyj \*( `pr`. **najpierw**). Aby uzyskać dostęp drugi iterator w parze `pr` zwróconą przez funkcję elementu członkowskiego, użyj `pr`. **drugi** wyłuskać iteratora górną granicę użyj \*( `pr`. **Po drugie**).

### <a name="example"></a>Przykład

```cpp
// multimap_equal_range.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   typedef multimap <int, int, less<int> > IntMMap;
   IntMMap m1;
   multimap <int, int> :: const_iterator m1_RcIter;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 1, 10 ) );
   m1.insert ( Int_Pair ( 2, 20 ) );
   m1.insert ( Int_Pair ( 3, 30 ) );

   pair <IntMMap::const_iterator, IntMMap::const_iterator> p1, p2;
   p1 = m1.equal_range( 2 );

   cout << "The lower bound of the element with "
        << "a key of 2 in the multimap m1 is: "
        << p1.first -> second << "." << endl;

   cout << "The upper bound of the element with "
        << "a key of 2 in the multimap m1 is: "
        << p1.second -> second << "." << endl;

   // Compare the upper_bound called directly
   m1_RcIter = m1.upper_bound( 2 );

   cout << "A direct call of upper_bound( 2 ) gives "
        << m1_RcIter -> second << "," << endl
        << "matching the 2nd element of the pair "
        << "returned by equal_range( 2 )." << endl;

   p2 = m1.equal_range( 4 );

   // If no match is found for the key,
   // both elements of the pair return end( )
   if ( ( p2.first == m1.end( ) ) && ( p2.second == m1.end( ) ) )
      cout << "The multimap m1 doesn't have an element "
           << "with a key less than 4." << endl;
   else
      cout << "The element of multimap m1 with a key >= 40 is: "
           << p1.first -> first << "." << endl;
}
```

```Output
The lower bound of the element with a key of 2 in the multimap m1 is: 20.
The upper bound of the element with a key of 2 in the multimap m1 is: 30.
A direct call of upper_bound( 2 ) gives 30,
matching the 2nd element of the pair returned by equal_range( 2 ).
The multimap m1 doesn't have an element with a key less than 4.
```

## <a name="erase"></a>  multimap::ERASE

Usuwa element lub zakres elementów w mapie wielokrotnej z określonych pozycji lub usuwa elementy, które odpowiadają określonemu kluczowi.

```cpp
iterator erase(
    const_iterator Where);

iterator erase(
    const_iterator First,
    const_iterator Last);

size_type erase(
    const key_type& Key);
```

### <a name="parameters"></a>Parametry

*Where*<br/>
Pozycja elementu, który ma zostać usunięty.

*pierwszy*<br/>
Pozycja pierwszego elementu do usunięcia.

*ostatni*<br/>
Pozycja tuż za ostatni element do usunięcia.

*Key*<br/>
Klucz elementów do usunięcia.

### <a name="return-value"></a>Wartość zwracana

Pierwsze dwie funkcje Członkowskie, aby uzyskać iteratora dwukierunkowego, określa pierwszy element pozostający poza wszelkimi elementami usuniętymi lub element, który jest końcem mapy, jeśli taki element nie istnieje.

Dla trzeciego funkcja elementu członkowskiego zwraca liczbę elementów, które zostały usunięte w mapie wielokrotnej.

### <a name="remarks"></a>Uwagi

Dla przykładu kodu zobacz [map::erase](../standard-library/map-class.md#erase).

## <a name="find"></a>  multimap::Find

Zwraca iterator, który odwołuje się do pierwszej lokalizacji elementu w mapie wielokrotnej, który ma klucz równoważny z określonym kluczem.

```cpp
iterator find(const Key& key);

const_iterator find(const Key& key) const;
```

### <a name="parameters"></a>Parametry

*Klucz*<br/>
Wartość klucza, które mają być dopasowywane o klucz sortowania elementu w mapie wielokrotnej wyszukiwany.

### <a name="return-value"></a>Wartość zwracana

Iterator, który odwołuje się do lokalizacji elementu z określonym kluczem lub lokalizację po ostatnim elemencie w mapie wielokrotnej (`multimap::end()`) Jeśli nie zostanie znalezione dopasowanie dla klucza.

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca iterator, który odwołuje się do elementu w mapie wielokrotnej, którego klucz sortowania jest odpowiednikiem klucza argumentu w obszarze predykat binarny, który wymusza kolejność oparte na mniej niż porównywalności relacji.

Jeśli wartość zwracaną przez `find` jest przypisany do `const_iterator`, nie można zmodyfikować obiektu multimap. Jeśli wartość zwracaną przez `find` jest przypisany do `iterator`, można zmodyfikować obiekt multimap.

### <a name="example"></a>Przykład

```cpp
// compile with: /EHsc /W4 /MTd
#include <map>
#include <iostream>
#include <vector>
#include <string>
#include <utility>  // make_pair()

using namespace std;

template <typename A, typename B> void print_elem(const pair<A, B>& p) {
    cout << "(" << p.first << ", " << p.second << ") ";
}

template <typename T> void print_collection(const T& t) {
    cout << t.size() << " elements: ";

    for (const auto& p : t) {
        print_elem(p);
    }
    cout << endl;
}

template <typename C, class T> void findit(const C& c, T val) {
    cout << "Trying find() on value " << val << endl;
    auto result = c.find(val);
    if (result != c.end()) {
        cout << "Element found: "; print_elem(*result); cout << endl;
    } else {
        cout << "Element not found." << endl;
    }
}

int main()
{
    multimap<int, string> m1({ { 40, "Zr" }, { 45, "Rh" } });
    cout << "The starting multimap m1 is (key, value):" << endl;
    print_collection(m1);

    vector<pair<int, string>> v;
    v.push_back(make_pair(43, "Tc"));
    v.push_back(make_pair(41, "Nb"));
    v.push_back(make_pair(46, "Pd"));
    v.push_back(make_pair(42, "Mo"));
    v.push_back(make_pair(44, "Ru"));
    v.push_back(make_pair(44, "Ru")); // attempt a duplicate

    cout << "Inserting the following vector data into m1:" << endl;
    print_collection(v);

    m1.insert(v.begin(), v.end());

    cout << "The modified multimap m1 is (key, value):" << endl;
    print_collection(m1);
    cout << endl;
    findit(m1, 45);
    findit(m1, 6);
}
```

## <a name="get_allocator"></a>  multimap::get_allocator

Zwraca kopię obiektu programu przydzielania użytego do stworzenia mapie wielokrotnej.

```cpp
allocator_type get_allocator() const;
```

### <a name="return-value"></a>Wartość zwracana

Alokator używany w mapie wielokrotnej.

### <a name="remarks"></a>Uwagi

Puli buforów dla klasy multimap — Określ, jak klasa zarządza magazynem. Buforów domyślną dostarczony wraz z klasy kontenera standardowej biblioteki języka C++ są wystarczające dla większości potrzeb programowania. Pisanie i przy użyciu klasy alokatora jest temat zaawansowany C++.

### <a name="example"></a>Przykład

```cpp
// multimap_get_allocator.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   multimap <int, int>::allocator_type m1_Alloc;
   multimap <int, int>::allocator_type m2_Alloc;
   multimap <int, double>::allocator_type m3_Alloc;
   multimap <int, int>::allocator_type m4_Alloc;

   // The following lines declare objects
   // that use the default allocator.
   multimap <int, int> m1;
   multimap <int, int, allocator<int> > m2;
   multimap <int, double, allocator<double> > m3;

   m1_Alloc = m1.get_allocator( );
   m2_Alloc = m2.get_allocator( );
   m3_Alloc = m3.get_allocator( );

   cout << "The number of integers that can be allocated"
        << endl << "before free memory is exhausted: "
        << m2.max_size( ) << ".\n" << endl;

   cout << "The number of doubles that can be allocated"
        << endl << "before free memory is exhausted: "
        << m3.max_size( ) <<  ".\n" << endl;

   // The following line creates a multimap m4
   // with the allocator of multimap m1.
   map <int, int> m4( less<int>( ), m1_Alloc );

   m4_Alloc = m4.get_allocator( );

   // Two allocators are interchangeable if
   // storage allocated from each can be
   // deallocated via the other
   if( m1_Alloc == m4_Alloc )
   {
      cout << "The allocators are interchangeable."
           << endl;
   }
   else
   {
      cout << "The allocators are not interchangeable."
           << endl;
   }
}
```

## <a name="insert"></a>  multimap::INSERT

Wstawia element lub zakres elementów w mapie wielokrotnej.

```cpp
// (1) single element
pair<iterator, bool> insert(
    const value_type& Val);

// (2) single element, perfect forwarded
template <class ValTy>
pair<iterator, bool>
insert(
    ValTy&& Val);

// (3) single element with hint
iterator insert(
    const_iterator Where,
    const value_type& Val);

// (4) single element, perfect forwarded, with hint
template <class ValTy>
iterator insert(
    const_iterator Where,
    ValTy&& Val);

// (5) range
template <class InputIterator>
void insert(
    InputIterator First,
    InputIterator Last);

// (6) initializer list
void insert(
    initializer_list<value_type>
IList);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|-|-|
|*Val*|Wartość elementu do wstawienia w mapie wielokrotnej.|
|*Where*|Miejsce, aby rozpocząć wyszukiwanie poprawne punktu wstawiania. (Jeśli danego punktu bezpośrednio poprzedza *gdzie*, wstawiania może wystąpić w amortyzowanym stałym czasie zamiast czasu logarytmicznych.)|
|*ValTy*|Parametr szablonu określający typ argumentu, który mapy służy do konstruowania elementu [value_type](../standard-library/map-class.md#value_type)i przekazuje doskonałe rozwiązanie *Val* jako argument.|
|*pierwszy*|Pozycja pierwszego elementu, który ma być skopiowany.|
|*ostatni*|Pozycja tuż za ostatnim elementem do skopiowania.|
|*InputIterator*|Argument funkcji szablonu, który spełnia wymagania [iterator danych wejściowych](../standard-library/input-iterator-tag-struct.md) wskazującej elementów typu, który może służyć do konstruowania [value_type](../standard-library/map-class.md#value_type) obiektów.|
|*IList*|[Initializer_list](../standard-library/initializer-list.md) z którego można skopiować elementy.|

### <a name="return-value"></a>Wartość zwracana

Funkcje elementów członkowskich pojedynczego elementu Wstawianie (1) i (2), zwracają iterator do miejsca, w których dodano nowy element w mapie wielokrotnej.

Funkcje Członkowskie jednego elementu za pomocą wskazówki, (3) i (4) zwraca iterator, który wskazuje miejsce, w którym dodano nowy element w mapie wielokrotnej.

### <a name="remarks"></a>Uwagi

Nie wskaźników lub odwołań są unieważniane przez tę funkcję, ale może unieważnić, wszystkie Iteratory do kontenera.

Podczas wstawiania tylko jeden element Jeśli wyjątek jest zgłaszany, stan kontenera nie jest modyfikowany. Podczas wstawiania wielu elementów jeśli wyjątek jest zgłaszany, kontener pozostanie w stanie nieokreślony, ale prawidłowe.

[Value_type](../standard-library/map-class.md#value_type) kontenera jest typedef, który należy do kontenera i mapy, `multimap<K, V>::value_type` jest `pair<const K, V>`. Wartość elementu jest uporządkowana para, w której pierwszy składnik jest równa wartości klucza i drugi składnik jest równa wartości danych elementu.

Zakres funkcji składowej (5) wstawia sekwencję wartości elementu w mapie wielokrotnej, która odnosi się do każdego elementu kierowanego przez iterator w zakresie `[First, Last)`; w związku z tym, *ostatniego* nie uzyskać wstawiony. Funkcja elementu członkowskiego kontenera `end()` odwołuje się do pozycji zaraz po ostatnim elemencie w kontenerze — na przykład instrukcja `m.insert(v.begin(), v.end());` wstawia wszystkie elementy `v` do `m`.

(6) używa funkcji elementu członkowskiego listy inicjatorów [initializer_list](../standard-library/initializer-list.md) można skopiować elementów do mapy.

Do wstawienia element skonstruowany w miejscu — oznacza to, że są wykonywane żadne operacje kopiowania lub przenoszenia — zobacz [multimap::emplace](#emplace) i [multimap::emplace_hint](#emplace_hint).

### <a name="example"></a>Przykład

```cpp
// multimap_insert.cpp
// compile with: /EHsc
#include <map>
#include <iostream>
#include <string>
#include <vector>
#include <utility>  // make_pair()

using namespace std;

template <typename M> void print(const M& m) {
    cout << m.size() << " elements: ";

    for (const auto& p : m) {
        cout << "(" << p.first << ", " << p.second << ") ";
    }

    cout << endl;
}

int main()
{

    // insert single values
    multimap<int, int> m1;
    // call insert(const value_type&) version
    m1.insert({ 1, 10 });
    // call insert(ValTy&&) version
    m1.insert(make_pair(2, 20));

    cout << "The original key and mapped values of m1 are:" << endl;
    print(m1);

    // intentionally attempt a duplicate, single element
    m1.insert(make_pair(1, 111));

    cout << "The modified key and mapped values of m1 are:" << endl;
    print(m1);

    // single element, with hint
    m1.insert(m1.end(), make_pair(3, 30));
    cout << "The modified key and mapped values of m1 are:" << endl;
    print(m1);
    cout << endl;

    // The templatized version inserting a jumbled range
    multimap<int, int> m2;
    vector<pair<int, int>> v;
    v.push_back(make_pair(43, 294));
    v.push_back(make_pair(41, 262));
    v.push_back(make_pair(45, 330));
    v.push_back(make_pair(42, 277));
    v.push_back(make_pair(44, 311));

    cout << "Inserting the following vector data into m2:" << endl;
    print(v);

    m2.insert(v.begin(), v.end());

    cout << "The modified key and mapped values of m2 are:" << endl;
    print(m2);
    cout << endl;

    // The templatized versions move-constructing elements
    multimap<int, string>  m3;
    pair<int, string> ip1(475, "blue"), ip2(510, "green");

    // single element
    m3.insert(move(ip1));
    cout << "After the first move insertion, m3 contains:" << endl;
    print(m3);

    // single element with hint
    m3.insert(m3.end(), move(ip2));
    cout << "After the second move insertion, m3 contains:" << endl;
    print(m3);
    cout << endl;

    multimap<int, int> m4;
    // Insert the elements from an initializer_list
    m4.insert({ { 4, 44 }, { 2, 22 }, { 3, 33 }, { 1, 11 }, { 5, 55 } });
    cout << "After initializer_list insertion, m4 contains:" << endl;
    print(m4);
    cout << endl;
}
```

## <a name="iterator"></a>  multimap::iterator

Typ, który dostarcza iterator dwukierunkowy, który może odczytać lub zmodyfikować dowolny element w mapie wielokrotnej.

```cpp
typedef implementation-defined iterator;
```

### <a name="remarks"></a>Uwagi

`iterator` Zdefiniowane przez multimap — punkty do obiektów [value_type](#value_type), które są typu `pair<const Key, Type>`. Wartość klucza jest dostępna za pośrednictwem pary pierwszego elementu członkowskiego, a wartość elementu zmapowanego jest dostępna za pośrednictwem drugiego elementu członkowskiego pary.

Próbę `iterator` *Iter* wskazuje element w mapie wielokrotnej, użyj **->** operatora.

Aby uzyskać dostęp do wartości klucza dla elementu, należy użyć `Iter->first`, który jest odpowiednikiem `(*Iter).first`. Aby uzyskać dostęp do wartości zamapowanego datum dla elementu, należy użyć `Iter->second`, który jest odpowiednikiem `(*Iter).second`.

Typ `iterator` może służyć do modyfikowania wartości elementu.

### <a name="example"></a>Przykład

Zobacz przykład [rozpocząć](#begin) przykładowy sposób deklarowania i użyj `iterator`.

## <a name="key_comp"></a>  multimap::key_comp

Pobiera kopię obiektu porównania użytego do uporządkowania kluczy w mapie wielokrotnej.

```cpp
key_compare key_comp() const;
```

### <a name="return-value"></a>Wartość zwracana

Zwraca obiekt funkcji, mapa wielokrotna używa do porządkowania jego elementów.

### <a name="remarks"></a>Uwagi

Przechowywany obiekt definiuje funkcję członka

`bool operator( const Key& x, const Key& y);`

które zwraca wartość true, jeśli *x* ściśle poprzedza *y* w porządku sortowania.

### <a name="example"></a>Przykład

```cpp
// multimap_key_comp.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;

   multimap <int, int, less<int> > m1;
   multimap <int, int, less<int> >::key_compare kc1 = m1.key_comp( ) ;
   bool result1 = kc1( 2, 3 ) ;
   if( result1 == true )
   {
      cout << "kc1( 2,3 ) returns value of true, "
           << "where kc1 is the function object of m1."
           << endl;
   }
   else
   {
      cout << "kc1( 2,3 ) returns value of false "
           << "where kc1 is the function object of m1."
           << endl;
   }

   multimap <int, int, greater<int> > m2;
   multimap <int, int, greater<int> >::key_compare kc2 = m2.key_comp( );
   bool result2 = kc2( 2, 3 ) ;
   if( result2 == true )
   {
      cout << "kc2( 2,3 ) returns value of true, "
           << "where kc2 is the function object of m2."
           << endl;
   }
   else
   {
      cout << "kc2( 2,3 ) returns value of false, "
           << "where kc2 is the function object of m2."
           << endl;
   }
}
```

```Output
kc1( 2,3 ) returns value of true, where kc1 is the function object of m1.
kc2( 2,3 ) returns value of false, where kc2 is the function object of m2.
```

## <a name="key_compare"></a>  multimap::key_compare

Typ, który dostarcza obiekt funkcji, która może porównać dwa klucze sortowania, aby określić względną kolejność dwóch elementów w mapie wielokrotnej.

```cpp
typedef Traits key_compare;
```

### <a name="remarks"></a>Uwagi

`key_compare` synonim dla parametru szablonu jest `Traits`.

Aby uzyskać więcej informacji na temat `Traits` zobacz [multimap — klasa](../standard-library/multimap-class.md) tematu.

### <a name="example"></a>Przykład

Zobacz przykład [key_comp](#key_comp) przykładowy sposób deklarowania i użyj `key_compare`.

## <a name="key_type"></a>  multimap::key_type

Typ, który opisuje obiekt klucza sortowania, stanowiący każdy element w mapie wielokrotnej.

```cpp
typedef Key key_type;
```

### <a name="remarks"></a>Uwagi

`key_type` synonim dla parametru szablonu jest `Key`.

Aby uzyskać więcej informacji na temat `Key`, zobacz sekcję Uwagi [multimap — klasa](../standard-library/multimap-class.md) tematu.

### <a name="example"></a>Przykład

Zobacz przykład [value_type](#value_type) przykładowy sposób deklarowania i użyj `key_type`.

## <a name="lower_bound"></a>  multimap::lower_bound

Zwraca iterator do pierwszego elementu w mapie wielokrotnej, za pomocą klucza, który jest równy lub większy od określonego klucza.

```cpp
iterator lower_bound(const Key& key);

const_iterator lower_bound(const Key& key) const;
```

### <a name="parameters"></a>Parametry

*Klucz*<br/>
Argument klucza, który ma zostać porównane z klucza sortowania elementu w mapie wielokrotnej wyszukiwany.

### <a name="return-value"></a>Wartość zwracana

Iterator lub `const_iterator` czy adresy lokalizację elementu w mapie wielokrotnej, że za pomocą klucza, który jest równy lub większy niż określony klucz argument lub który zapewnia lokalizację po ostatnim elemencie w mapie wielokrotnej, jeśli nie są takie same znajduje się dla klucza.

Jeśli wartość zwracaną przez `lower_bound` jest przypisany do `const_iterator`, nie można zmodyfikować obiektu multimap. Jeśli wartość zwracaną przez `lower_bound` jest przypisany do **iteratora**, można zmodyfikować obiekt multimap.

### <a name="example"></a>Przykład

```cpp
// multimap_lower_bound.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   multimap <int, int> m1;
   multimap <int, int> :: const_iterator m1_AcIter, m1_RcIter;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 1, 10 ) );
   m1.insert ( Int_Pair ( 2, 20 ) );
   m1.insert ( Int_Pair ( 3, 20 ) );
   m1.insert ( Int_Pair ( 3, 30 ) );

   m1_RcIter = m1.lower_bound( 2 );
   cout << "The element of multimap m1 with a key of 2 is: "
        << m1_RcIter -> second << "." << endl;

   m1_RcIter = m1.lower_bound( 3 );
   cout << "The first element of multimap m1 with a key of 3 is: "
        << m1_RcIter -> second << "." << endl;

   // If no match is found for the key, end( ) is returned
   m1_RcIter = m1.lower_bound( 4 );

   if ( m1_RcIter == m1.end( ) )
      cout << "The multimap m1 doesn't have an element "
              << "with a key of 4." << endl;
   else
      cout << "The element of multimap m1 with a key of 4 is: "
                << m1_RcIter -> second << "." << endl;

   // The element at a specific location in the multimap can be
   // found using a dereferenced iterator addressing the location
   m1_AcIter = m1.end( );
   m1_AcIter--;
   m1_RcIter = m1.lower_bound( m1_AcIter -> first );
   cout << "The first element of m1 with a key matching\n"
        << "that of the last element is: "
        << m1_RcIter -> second << "." << endl;

   // Note that the first element with a key equal to
   // the key of the last element is not the last element
   if ( m1_RcIter == --m1.end( ) )
      cout << "This is the last element of multimap m1."
           << endl;
   else
      cout << "This is not the last element of multimap m1."
           << endl;
}
```

```Output
The element of multimap m1 with a key of 2 is: 20.
The first element of multimap m1 with a key of 3 is: 20.
The multimap m1 doesn't have an element with a key of 4.
The first element of m1 with a key matching
that of the last element is: 20.
This is not the last element of multimap m1.
```

## <a name="mapped_type"></a>  multimap::mapped_type

Typ, który reprezentuje typ danych przechowywanych w mapie wielokrotnej.

```cpp
typedef Type mapped_type;
```

### <a name="remarks"></a>Uwagi

`mapped_type` synonim dla parametru szablonu jest `Type`.

Aby uzyskać więcej informacji na temat `Type` zobacz [multimap — klasa](../standard-library/multimap-class.md) tematu.

### <a name="example"></a>Przykład

Zobacz przykład [value_type](#value_type) przykładowy sposób deklarowania i użyj `key_type`.

## <a name="max_size"></a>  multimap::max_size

Zwraca maksymalną długość w mapie wielokrotnej.

```cpp
size_type max_size() const;
```

### <a name="return-value"></a>Wartość zwracana

Maksymalna możliwa długość mapie wielokrotnej.

### <a name="example"></a>Przykład

```cpp
// multimap_max_size.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   multimap <int, int> m1;
   multimap <int, int> :: size_type i;

   i = m1.max_size( );
   cout << "The maximum possible length "
        << "of the multimap is " << i << "." << endl;
}
```

## <a name="multimap"></a>  multimap::multimap

Tworzy multimap, który jest pusty lub jest kopią całości lub części niektórych innych multimap.

```cpp
multimap();

explicit multimap(
    const Traits& Comp);

multimap(
    const Traits& Comp,
    const Allocator& Al);

map(
    const multimap& Right);

multimap(
    multimap&& Right);

multimap(
    initializer_list<value_type> IList);

multimap(
    initializer_list<value_type> IList,
    const Compare& Comp);

multimap(
    initializer_list<value_type> IList,
    const Compare& Comp,
    const Allocator& Al);

template <class InputIterator>
multimap(
    InputIterator First,
    InputIterator Last);

template <class InputIterator>
multimap(
    InputIterator First,
    InputIterator Last,
    const Traits& Comp);

template <class InputIterator>
multimap(
    InputIterator First,
    InputIterator Last,
    const Traits& Comp,
    const Allocator& Al);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|-|-|
|*Al*|Klasa alokatora magazynu, która ma być używany dla tego obiektu multimap, która domyślnie alokatora.|
|*Comp*|Funkcja porównywania typu `constTraits` porządkowania elementów w mapie, którego wartość domyślna to `Traits`.|
|*po prawej stronie*|Mapa, w której zestaw zbudowany jest kopią.|
|*pierwszy*|Pozycja pierwszego elementu w zakresie elementów, które mają zostać skopiowane.|
|*ostatni*|Pozycja pierwszego elementu poza zakresem elementów, które mają zostać skopiowane.|
|*IList*|Lista initializer_list, z której mają być skopiowane elementy.|

### <a name="remarks"></a>Uwagi

Wszystkie konstruktory zapisują obiekt alokatora, który zarządza przechowywania w pamięci na mapie wielokrotnej, a które później mogą być zwracane przez wywołanie metody typu [get_allocator —](#get_allocator). Parametr alokatora jest często pomijane w deklaracji klasy i wstępnego przetwarzania makra używane do zastąpienia buforów alternatywne.

Wszystkie konstruktory inicjują ich w mapie wielokrotnej.

Wszystkie konstruktory zapisują obiekt funkcyjny tego typu `Traits` który jest używany do ustanawiania kolejność kluczy w mapie wielokrotnej i które później mogą być zwracane przez wywołanie metody [key_comp](#key_comp).

Pierwsze trzy konstruktory Określ pusty multimap początkowej, drugi określając typ funkcji porównywania (*Comp*) ma być używany, ustalając kolejność elementów, a trzeci, jawnie określając alokator wpisz (*Al*) ma być używany. Słowo kluczowe **jawne** powoduje pominięcie niektórych rodzajów konwersji typu automatyczne.

Czwarty Konstruktor Określa kopię Mapa wielokrotna *po prawej stronie*.

Piąty Konstruktor Określa kopię Mapa wielokrotna, przenosząc *po prawej stronie*.

Szóstego, siódmy i ósmy konstruktory kopiują członkowie initializer_list.

Następne trzy konstruktory kopiują zakres `[First, Last)` mapy uwzględni się rosnącą explicitness, określając typ funkcji porównywania klasy `Traits` oraz alokatorem.

### <a name="example"></a>Przykład

```cpp
// multimap_ctor.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main()
{
    using namespace std;
    typedef pair <int, int> Int_Pair;

    // Create an empty multimap m0 of key type integer
    multimap <int, int> m0;

    // Create an empty multimap m1 with the key comparison
    // function of less than, then insert 4 elements
    multimap <int, int, less<int> > m1;
    m1.insert(Int_Pair(1, 10));
    m1.insert(Int_Pair(2, 20));
    m1.insert(Int_Pair(3, 30));
    m1.insert(Int_Pair(4, 40));

    // Create an empty multimap m2 with the key comparison
    // function of greater than, then insert 2 elements
    multimap <int, int, less<int> > m2;
    m2.insert(Int_Pair(1, 10));
    m2.insert(Int_Pair(2, 20));

    // Create a multimap m3 with the
    // allocator of multimap m1
    multimap <int, int>::allocator_type m1_Alloc;
    m1_Alloc = m1.get_allocator();
    multimap <int, int> m3(less<int>(), m1_Alloc);
    m3.insert(Int_Pair(3, 30));

    // Create a copy, multimap m4, of multimap m1
    multimap <int, int> m4(m1);

    // Create a multimap m5 by copying the range m1[ first,  last)
    multimap <int, int>::const_iterator m1_bcIter, m1_ecIter;
    m1_bcIter = m1.begin();
    m1_ecIter = m1.begin();
    m1_ecIter++;
    m1_ecIter++;
    multimap <int, int> m5(m1_bcIter, m1_ecIter);

    // Create a multimap m6 by copying the range m4[ first,  last)
    // and with the allocator of multimap m2
    multimap <int, int>::allocator_type m2_Alloc;
    m2_Alloc = m2.get_allocator();
    multimap <int, int> m6(m4.begin(), ++m4.begin(), less<int>(), m2_Alloc);

    cout << "m1 =";
    for (auto i : m1)
        cout << i.first << " " << i.second << ", ";
    cout << endl;

    cout << "m2 =";
    for (auto i : m2)
        cout << i.first << " " << i.second << ", ";
    cout << endl;

    cout << "m3 =";
    for (auto i : m3)
        cout << i.first << " " << i.second << ", ";
    cout << endl;

    cout << "m4 =";
    for (auto i : m4)
        cout << i.first << " " << i.second << ", ";
    cout << endl;

    cout << "m5 =";
    for (auto i : m5)
        cout << i.first << " " << i.second << ", ";
    cout << endl;

    cout << "m6 =";
    for (auto i : m6)
        cout << i.first << " " << i.second << ", ";
    cout << endl;

    // Create a multimap m8 by copying in an initializer_list
    multimap<int, int> m8{ { { 1, 1 }, { 2, 2 }, { 3, 3 }, { 4, 4 } } };
    cout << "m8: = ";
    for (auto i : m8)
        cout << i.first << " " << i.second << ", ";
    cout << endl;

    // Create a multimap m9 with an initializer_list and a comparator
    multimap<int, int> m9({ { 5, 5 }, { 6, 6 }, { 7, 7 }, { 8, 8 } }, less<int>());
    cout << "m9: = ";
    for (auto i : m9)
        cout << i.first << " " << i.second << ", ";
    cout << endl;

    // Create a multimap m10 with an initializer_list, a comparator, and an allocator
    multimap<int, int> m10({ { 9, 9 }, { 10, 10 }, { 11, 11 }, { 12, 12 } }, less<int>(), m9.get_allocator());
    cout << "m10: = ";
    for (auto i : m10)
        cout << i.first << " " << i.second << ", ";
    cout << endl;

}
```

## <a name="op_eq"></a>  multimap::operator =

Zastępuje kopię innej multimap elementów w mapie wielokrotnej.

```cpp
multimap& operator=(const multimap& right);

multimap& operator=(multimap&& right);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|-|-|
|*right*|[Multimap](../standard-library/multimap-class.md) są kopiowane do `multimap`.|

### <a name="remarks"></a>Uwagi

Po wymazaniu wszelkie elementy istniejących w `multimap`, `operator=` kopiuje lub przenosi zawartość *prawo* do `multimap`.

### <a name="example"></a>Przykład

```cpp
// multimap_operator_as.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
   {
   using namespace std;
   multimap<int, int> v1, v2, v3;
   multimap<int, int>::iterator iter;

   v1.insert(pair<int, int>(1, 10));

   cout << "v1 = " ;
   for (iter = v1.begin(); iter != v1.end(); iter++)
      cout << iter->second << " ";
   cout << endl;

   v2 = v1;
   cout << "v2 = ";
   for (iter = v2.begin(); iter != v2.end(); iter++)
      cout << iter->second << " ";
   cout << endl;

// move v1 into v2
   v2.clear();
   v2 = move(v1);
   cout << "v2 = ";
   for (iter = v2.begin(); iter != v2.end(); iter++)
      cout << iter->second << " ";
   cout << endl;
   }
```

## <a name="pointer"></a>  multimap::Pointer

Typ, który dostarcza wskaźnik do elementu w mapie wielokrotnej.

```cpp
typedef typename allocator_type::pointer pointer;
```

### <a name="remarks"></a>Uwagi

Typ `pointer` może służyć do modyfikowania wartości elementu.

W większości przypadków [iteratora](#iterator) powinien być używany do uzyskania dostępu do elementów w obiekcie multimap.

## <a name="rbegin"></a>  multimap::rbegin

Zwraca iterator adresujący pierwszy element w odwróconej mapie wielokrotnej.

```cpp
const_reverse_iterator rbegin() const;

reverse_iterator rbegin();
```

### <a name="return-value"></a>Wartość zwracana

Odwrotny iterator dwukierunkowy odnoszący się do pierwszego elementu w odwróconej mapie wielokrotnej lub adresowania, który był ostatnim elementem w mapie wielokrotnej nieodwróconej.

### <a name="remarks"></a>Uwagi

`rbegin` jest używana z odwróconej mapie wielokrotnej podobnie jak [rozpocząć](#begin) jest używana z mapie wielokrotnej.

Jeśli wartość zwracaną przez `rbegin` jest przypisany do `const_reverse_iterator`, wówczas nie można zmodyfikować obiektu multimap. Jeśli wartość zwracaną przez `rbegin` jest przypisany do `reverse_iterator`, a następnie można zmodyfikować obiekt multimap.

`rbegin` może służyć do iterowania po Mapa wielokrotna Wstecz.

### <a name="example"></a>Przykład

```cpp
// multimap_rbegin.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   multimap <int, int> m1;

   multimap <int, int> :: iterator m1_Iter;
   multimap <int, int> :: reverse_iterator m1_rIter;
   multimap <int, int> :: const_reverse_iterator m1_crIter;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 1, 10 ) );
   m1.insert ( Int_Pair ( 2, 20 ) );
   m1.insert ( Int_Pair ( 3, 30 ) );

   m1_rIter = m1.rbegin( );
   cout << "The first element of the reversed multimap m1 is "
        << m1_rIter -> first << "." << endl;

   // begin can be used to start an iteration
   // through a multimap in a forward order
   cout << "The multimap is: ";
   for ( m1_Iter = m1.begin( ) ; m1_Iter != m1.end( ); m1_Iter++)
      cout << m1_Iter -> first << " ";
      cout << "." << endl;

   // rbegin can be used to start an iteration
   // through a multimap in a reverse order
   cout << "The reversed multimap is: ";
   for ( m1_rIter = m1.rbegin( ) ; m1_rIter != m1.rend( ); m1_rIter++)
      cout << m1_rIter -> first << " ";
      cout << "." << endl;

   // A multimap element can be erased by dereferencing its key
   m1_rIter = m1.rbegin( );
   m1.erase ( m1_rIter -> first );

   m1_rIter = m1.rbegin( );
   cout << "After the erasure, the first element "
        << "in the reversed multimap is "
        << m1_rIter -> first << "." << endl;
}
```

```Output
The first element of the reversed multimap m1 is 3.
The multimap is: 1 2 3 .
The reversed multimap is: 3 2 1 .
After the erasure, the first element in the reversed multimap is 2.
```

## <a name="reference"></a>  multimap::Reference

Typ, który zawiera odwołanie do elementu przechowywanego w mapie wielokrotnej.

```cpp
typedef typename allocator_type::reference reference;
```

### <a name="example"></a>Przykład

```cpp
// multimap_ref.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   multimap <int, int> m1;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 1, 10 ) );
   m1.insert ( Int_Pair ( 2, 20 ) );

   // Declare and initialize a const_reference &Ref1
   // to the key of the first element
   const int &Ref1 = ( m1.begin( ) -> first );

   // The following line would cause an error because the
   // non-const_reference cannot be used to access the key
   // int &Ref1 = ( m1.begin( ) -> first );

   cout << "The key of first element in the multimap is "
        << Ref1 << "." << endl;

   // Declare and initialize a reference &Ref2
   // to the data value of the first element
   int &Ref2 = ( m1.begin( ) -> second );

   cout << "The data value of first element in the multimap is "
        << Ref2 << "." << endl;

   // The non-const_reference can be used to modify the
   // data value of the first element
   Ref2 = Ref2 + 5;
   cout << "The modified data value of first element is "
        << Ref2 << "." << endl;
}
```

```Output
The key of first element in the multimap is 1.
The data value of first element in the multimap is 10.
The modified data value of first element is 15.
```

## <a name="rend"></a>  multimap::rend

Zwraca iterator adresujący lokalizację następującą po ostatnim elemencie w odwróconej mapie wielokrotnej.

```cpp
const_reverse_iterator rend() const;

reverse_iterator rend();
```

### <a name="return-value"></a>Wartość zwracana

Odwrotny iterator dwukierunkowy odnoszący się do lokalizacji następującej po ostatnim elemencie w odwróconej mapie wielokrotnej (miejsca przed pierwszego elementu w mapie wielokrotnej nieodwróconej).

### <a name="remarks"></a>Uwagi

`rend` jest używana z odwróconej mapie wielokrotnej podobnie jak [zakończenia](../standard-library/map-class.md#end) jest używana z mapie wielokrotnej.

Jeśli wartość zwracaną przez `rend` jest przypisany do `const_reverse_iterator`, wówczas nie można zmodyfikować obiektu multimap. Jeśli wartość zwracaną przez `rend` jest przypisany do `reverse_iterator`, a następnie można zmodyfikować obiekt multimap.

`rend` można sprawdzać, czy wsteczny iterator osiągnął koniec swojej multimap.

Wartość zwrócona przez obiekt `rend` nie należy usuwać odwołania.

### <a name="example"></a>Przykład

```cpp
// multimap_rend.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   multimap <int, int> m1;

   multimap <int, int> :: iterator m1_Iter;
   multimap <int, int> :: reverse_iterator m1_rIter;
   multimap <int, int> :: const_reverse_iterator m1_crIter;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 1, 10 ) );
   m1.insert ( Int_Pair ( 2, 20 ) );
   m1.insert ( Int_Pair ( 3, 30 ) );

   m1_rIter = m1.rend( );
   m1_rIter--;
   cout << "The last element of the reversed multimap m1 is "
        << m1_rIter -> first << "." << endl;

   // begin can be used to start an iteration
   // through a multimap in a forward order
   cout << "The multimap is: ";
   for ( m1_Iter = m1.begin( ) ; m1_Iter != m1.end( ); m1_Iter++)
      cout << m1_Iter -> first << " ";
      cout << "." << endl;

   // rbegin can be used to start an iteration
   // through a multimap in a reverse order
   cout << "The reversed multimap is: ";
   for ( m1_rIter = m1.rbegin( ) ; m1_rIter != m1.rend( ); m1_rIter++)
      cout << m1_rIter -> first << " ";
      cout << "." << endl;

   // A multimap element can be erased by dereferencing to its key
   m1_rIter = --m1.rend( );
   m1.erase ( m1_rIter -> first );

   m1_rIter = m1.rend( );
   m1_rIter--;
   cout << "After the erasure, the last element "
        << "in the reversed multimap is "
        << m1_rIter -> first << "." << endl;
}
```

```Output
The last element of the reversed multimap m1 is 1.
The multimap is: 1 2 3 .
The reversed multimap is: 3 2 1 .
After the erasure, the last element in the reversed multimap is 2.
```

## <a name="reverse_iterator"></a>  multimap::reverse_iterator

Typ, który dostarcza iterator dwukierunkowy, który może odczytać lub zmodyfikować element w odwróconej mapie wielokrotnej.

```cpp
typedef std::reverse_iterator<iterator> reverse_iterator;
```

### <a name="remarks"></a>Uwagi

Typ `reverse_iterator` jest używany do iterowania po multimap w odwrotnej kolejności.

`reverse_iterator` Zdefiniowane przez multimap — punkty do obiektów [value_type](#value_type), które są typu `pair<const Key, Type>`. Wartość klucza jest dostępna za pośrednictwem pary pierwszego elementu członkowskiego, a wartość elementu zmapowanego jest dostępna za pośrednictwem drugiego elementu członkowskiego pary.

Próbę `reverse_iterator` *rIter* wskazuje element w mapie wielokrotnej, użyj **->** operatora.

Aby uzyskać dostęp do wartości klucza dla elementu, należy użyć `rIter->first`, który jest odpowiednikiem `(*rIter).first`. Aby uzyskać dostęp do wartości zamapowanego datum dla elementu, należy użyć `rIter->second`, który jest odpowiednikiem `(*rIter).second`.

### <a name="example"></a>Przykład

Zobacz przykład [rbegin —](#rbegin) przykładowy sposób deklarowania i użyj `reverse_iterator`.

## <a name="size"></a>  multimap::size

Zwraca liczbę elementów w mapie wielokrotnej.

```cpp
size_type size() const;
```

### <a name="return-value"></a>Wartość zwracana

Bieżąca długość w mapie wielokrotnej.

### <a name="example"></a>Przykład

Poniższy przykład demonstruje użycie multimap::size funkcja elementu członkowskiego.

```cpp
// multimap_size.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main()
{
    using namespace std;
    multimap<int, int> m1, m2;
    multimap<int, int>::size_type i;
    typedef pair<int, int> Int_Pair;

    m1.insert(Int_Pair(1, 1));
    i = m1.size();
    cout << "The multimap length is " << i << "." << endl;

    m1.insert(Int_Pair(2, 4));
    i = m1.size();
    cout << "The multimap length is now " << i << "." << endl;
}
```

```Output
The multimap length is 1.
The multimap length is now 2.
```

## <a name="size_type"></a>  multimap::size_type

Typ całkowitoliczbowy bez znaku, który zlicza liczbę elementów w mapie wielokrotnej.

```cpp
typedef typename allocator_type::size_type size_type;
```

### <a name="example"></a>Przykład

Zobacz przykład [rozmiar](#size) przykładem sposobu deklarowanie i użycie `size_type`

## <a name="swap"></a>  multimap::swap

Zamienia elementy z dwóch multimaps.

```cpp
void swap(
    multimap<Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*right*<br/>
Multimap, zawierająca elementy, które mają być zamienione lub multimap, której elementy są wymieniane z tymi Mapa wielokrotna `left`.

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego powoduje unieważnienie nie odwołania wskaźniki i Iteratory, które wyznaczają elementy w dwóch multimaps, której elementy są wymianie.

### <a name="example"></a>Przykład

```cpp
// multimap_swap.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   multimap <int, int> m1, m2, m3;
   multimap <int, int>::iterator m1_Iter;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 1, 10 ) );
   m1.insert ( Int_Pair ( 2, 20 ) );
   m1.insert ( Int_Pair ( 3, 30 ) );
   m2.insert ( Int_Pair ( 10, 100 ) );
   m2.insert ( Int_Pair ( 20, 200 ) );
   m3.insert ( Int_Pair ( 30, 300 ) );

   cout << "The original multimap m1 is:";
   for ( m1_Iter = m1.begin( ); m1_Iter != m1.end( ); m1_Iter++ )
      cout << " " << m1_Iter -> second;
   cout   << "." << endl;

   // This is the member function version of swap
   m1.swap( m2 );

   cout << "After swapping with m2, multimap m1 is:";
   for ( m1_Iter = m1.begin( ); m1_Iter != m1.end( ); m1_Iter++ )
      cout << " " << m1_Iter -> second;
   cout  << "." << endl;

   // This is the specialized template version of swap
   swap( m1, m3 );

   cout << "After swapping with m3, multimap m1 is:";
   for ( m1_Iter = m1.begin( ); m1_Iter != m1.end( ); m1_Iter++ )
      cout << " " << m1_Iter -> second;
   cout   << "." << endl;
}
```

```Output
The original multimap m1 is: 10 20 30.
After swapping with m2, multimap m1 is: 100 200.
After swapping with m3, multimap m1 is: 300.
```

## <a name="upper_bound"></a>  multimap::upper_bound

Zwraca iterator do pierwszego elementu w mapie wielokrotnej, za pomocą klucza, który jest większy od określonego klucza.

```cpp
iterator upper_bound(const Key& key);

const_iterator upper_bound(const Key& key) const;
```

### <a name="parameters"></a>Parametry

*Klucz*<br/>
Argument klucza, który ma zostać porównane z klucza sortowania elementu w mapie wielokrotnej wyszukiwany.

### <a name="return-value"></a>Wartość zwracana

Iterator lub `const_iterator` czy adresy lokalizację elementu w mapie wielokrotnej, że za pomocą klucza, który jest większy niż określony klucz argument lub który zapewnia lokalizację po ostatnim elemencie w mapie wielokrotnej, jeśli nie są takie same znajduje się dla klucza.

Jeśli wartość zwracana jest przypisany do `const_iterator`, nie można zmodyfikować obiektu multimap. Jeśli wartość zwracana jest przypisany do `iterator`, można zmodyfikować obiekt multimap.

### <a name="example"></a>Przykład

```cpp
// multimap_upper_bound.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   multimap <int, int> m1;
   multimap <int, int> :: const_iterator m1_AcIter, m1_RcIter;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 1, 10 ) );
   m1.insert ( Int_Pair ( 2, 20 ) );
   m1.insert ( Int_Pair ( 3, 30 ) );
   m1.insert ( Int_Pair ( 3, 40 ) );

   m1_RcIter = m1.upper_bound( 1 );
   cout << "The 1st element of multimap m1 with "
        << "a key greater than 1 is: "
        << m1_RcIter -> second << "." << endl;

   m1_RcIter = m1.upper_bound( 2 );
   cout << "The first element of multimap m1 with a key "
        << " greater than 2 is: "
        << m1_RcIter -> second << "." << endl;

   // If no match is found for the key, end( ) is returned
   m1_RcIter = m1.lower_bound( 4 );

   if ( m1_RcIter == m1.end( ) )
      cout << "The multimap m1 doesn't have an element "
           << "with a key of 4." << endl;
   else
      cout << "The element of multimap m1 with a key of 4 is: "
           << m1_RcIter -> second << "." << endl;

   // The element at a specific location in the multimap can be
   // found using a dereferenced iterator addressing the location
   m1_AcIter = m1.begin( );
   m1_RcIter = m1.upper_bound( m1_AcIter -> first );
   cout << "The first element of m1 with a key greater than\n"
        << "that of the initial element of m1 is: "
        << m1_RcIter -> second << "." << endl;
}
```

```Output
The 1st element of multimap m1 with a key greater than 1 is: 20.
The first element of multimap m1 with a key  greater than 2 is: 30.
The multimap m1 doesn't have an element with a key of 4.
The first element of m1 with a key greater than
that of the initial element of m1 is: 20.
```

## <a name="value_comp"></a>  multimap::value_comp

Funkcja elementu członkowskiego zwraca obiekt funkcji, która określa kolejność elementów w mapie wielokrotnej przez porównanie ich wartości klucza.

```cpp
value_compare value_comp() const;
```

### <a name="return-value"></a>Wartość zwracana

Zwraca obiekt funkcji porównywania, mapa wielokrotna używa do porządkowania jego elementów.

### <a name="remarks"></a>Uwagi

Na mapie wielokrotnej *m*, jeśli dwa elementy *e1*(*k1*, *d1*) i *e2*(*k2*, *d2*) są obiektami typu `value_type`, gdzie *k1* i *k2* są dla nich kluczami typu `key_type` i *d1*  i *d2* są ich dane typu `mapped_type`, następnie `m.value_comp(e1, e2)` jest odpowiednikiem `m.key_comp(k1, k2)`.

### <a name="example"></a>Przykład

```cpp
// multimap_value_comp.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;

   multimap <int, int, less<int> > m1;
   multimap <int, int, less<int> >::value_compare vc1 = m1.value_comp( );
   multimap<int,int>::iterator Iter1, Iter2;

   Iter1= m1.insert ( multimap <int, int> :: value_type ( 1, 10 ) );
   Iter2= m1.insert ( multimap <int, int> :: value_type ( 2, 5 ) );

   if( vc1( *Iter1, *Iter2 ) == true )
   {
      cout << "The element ( 1,10 ) precedes the element ( 2,5 )."
           << endl;
   }
   else
   {
      cout << "The element ( 1,10 ) does "
           << "not precede the element ( 2,5 )."
           << endl;
   }

   if( vc1( *Iter2, *Iter1 ) == true )
   {
      cout << "The element ( 2,5 ) precedes the element ( 1,10 )."
           << endl;
   }
   else
   {
      cout << "The element ( 2,5 ) does "
           << "not precede the element ( 1,10 )."
           << endl;
   }
}
```

```Output
The element ( 1,10 ) precedes the element ( 2,5 ).
The element ( 2,5 ) does not precede the element ( 1,10 ).
```

## <a name="value_type"></a>  multimap::value_type

Typ, który reprezentuje typ obiektu przechowywanego jako element w mapie.

```cpp
typedef pair<const Key, Type> value_type;
```

### <a name="example"></a>Przykład

```cpp
// multimap_value_type.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   typedef pair <const int, int> cInt2Int;
   multimap <int, int> m1;
   multimap <int, int> :: key_type key1;
   multimap <int, int> :: mapped_type mapped1;
   multimap <int, int> :: value_type value1;
   multimap <int, int> :: iterator pIter;

   // value_type can be used to pass the correct type
   // explicitly to avoid implicit type conversion
   m1.insert ( multimap <int, int> :: value_type ( 1, 10 ) );

   // Compare another way to insert objects into a hash_multimap
   m1.insert ( cInt2Int ( 2, 20 ) );

   // Initializing key1 and mapped1
   key1 = ( m1.begin( ) -> first );
   mapped1 = ( m1.begin( ) -> second );

   cout << "The key of first element in the multimap is "
        << key1 << "." << endl;

   cout << "The data value of first element in the multimap is "
        << mapped1 << "." << endl;

   // The following line would cause an error because
   // the value_type is not assignable
   // value1 = cInt2Int ( 4, 40 );

   cout  << "The keys of the mapped elements are:";
   for ( pIter = m1.begin( ) ; pIter != m1.end( ) ; pIter++ )
      cout << " " << pIter -> first;
   cout << "." << endl;

   cout  << "The values of the mapped elements are:";
   for ( pIter = m1.begin( ) ; pIter != m1.end( ) ; pIter++ )
      cout << " " << pIter -> second;
   cout << "." << endl;
}
```

```Output
The key of first element in the multimap is 1.
The data value of first element in the multimap is 10.
The keys of the mapped elements are: 1 2.
The values of the mapped elements are: 10 20.
```

## <a name="see-also"></a>Zobacz także

[Kontenery](../cpp/containers-modern-cpp.md)<br/>
[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Dokumentacja standardowej biblioteki C++](../standard-library/cpp-standard-library-reference.md)<br/>
