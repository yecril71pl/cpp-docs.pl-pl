---
title: multimap — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 25dffabfe01bb68af180d67b5b47dfee44ce30ff
ms.sourcegitcommit: 39585672df8874fb5df4e70de97cd7f328fe9880
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2018
ms.locfileid: "34153148"
---
# <a name="multimap-class"></a>multimap — Klasa

Standardowa biblioteka C++ multimap — klasa jest używana do przechowywania i pobierania danych z kolekcji, w którym każdy element jest parę ma wartość danych oraz klucza sortowania. Wartość klucza nie musi unikatowa i jest używana do automatycznego porządkowania danych. Wartość elementu w mapie wielokrotnej, ale nie wartość jego skojarzonego klucza, może być zmieniona bezpośrednio. Zamiast tego, wartości kluczy skojarzone ze starymi elementami muszą zostać usunięte, a nowe wartości klucza skojarzone z nowymi wstawionymi elementami.

## <a name="syntax"></a>Składnia

```cpp
template <class Key,
    class Type,
    class Traits=less <Key>,
    class Allocator=allocator <pair  <const Key, Type>>>
class multimap;
```

### <a name="parameters"></a>Parametry

`Key` Typ danych klucza, które mają być przechowywane w multimap.

`Type` Typ danych elementu mają być przechowywane w multimap.

`Traits` Typ, który udostępnia obiekt funkcji, które można porównać dwóch wartości elementu jako klucze sortowania w celu ustalenia, ich kolejność względną multimap. Predykat binarne `less<Key>` jest wartością domyślną.

W języku C ++ 14 można włączyć heterogenicznych wyszukiwania, określając `std::less<>` lub `std::greater<>` predykatu, który nie ma typu parametrów. Aby uzyskać więcej informacji, zobacz [heterogenicznych wyszukiwanie w kontenerach asocjacyjnej](../standard-library/stl-containers.md#heterogeneous-lookup-in-associative-containers-c14)

`Allocator` Typ reprezentujący obiekt alokatora przechowywane, który hermetyzuje informacje szczegółowe o mapy alokacji i cofania alokacji pamięci. Ten argument jest opcjonalny, a wartość domyślna to `allocator<pair <const Key, Type> >`.

## <a name="remarks"></a>Uwagi

Multimap — klasa standardowa biblioteka C++

- Kontenerem asocjacyjnym, który jest kontenerem o zmiennym rozmiarze, obsługującym efektywne pobieranie wartości elementu w oparciu o wartość skojarzonego klucza.

- Odwracalny, ponieważ zapewnia dwukierunkowe iteratory do dostępu do jego elementów.

- Posortowany, ponieważ jego elementy są uporządkowane według wartości kluczy w kontenerze zgodnie z określoną funkcją porównywania.

- Wielokrotna, ponieważ jej elementy nie muszą mieć unikatowych kluczy, więc jedna wartość klucza może mieć wiele wartości elementów danych z nią skojarzonych.

- Kontenerem skojarzonych par, ponieważ jej wartości danych elementu różnią się od wartości klucza.

- Klasą szablonu, ponieważ funkcjonalność, którą zapewnia, jest generyczna i dlatego niezależna od określonego typu danych zawartych jako elementy lub klucze. Typy danych, których można użyć dla elementów i kluczy, są zamiast tego określane jako parametry w szablonie klasy, wraz z funkcją porównania oraz alokatorem.

Iterator udostępnianym przez klasę mapy jest iteratora dwukierunkowego, ale funkcje Członkowskie klas [Wstaw](#insert) i [multimap](#multimap) wersje przyjmować jako parametry szablonu słabszych iteratora wejściowych, którego wymagania funkcji są minimalne więcej niż gwarantowane przez klasę Iteratory dwukierunkowego. Pojęcia innych iteratorów formują rodzinę powiązaną przez udoskonalenia w ich funkcjonalnościach. Każde pojęcie iteratora ma swój własny zestaw wymagań, a algorytmy z nimi pracujące muszą ograniczać swoje założenia co do wymagań dostarczonych przez tego typu iterator. Można założyć, że z iteratora danych wejściowych można usunąć odwołanie, aby odwołać się do obiektu, a także, że może on być zwiększony do następnego iteratora w sekwencji. Jest to minimalny zestaw funkcji, ale jest wystarczające, aby można było uzyskać wiarygodny porozmawiać na temat zakresu Iteratory `[First, Last)` w kontekście funkcji członkowskich tej klasy.

Wybór typu kontenera powinien ogólnie być oparty o typ wyszukiwania i wstawiania wymagany przez aplikację. Kontenery asocjacyjne są zoptymalizowane dla operacji wyszukiwania, wstawiania oraz usuwania. Funkcje elementów członkowskich, które jawnie obsługują te operacje, są skuteczne, wykonując je w czasie, który jest średnio proporcjonalny do logarytmu liczby elementów w kontenerze. Wstawianie elementów nie unieważnia iteratorów, a usuwanie elementów unieważnia tylko te iteratory, które w szczególności wskazywały na usunięte elementy.

Mapa wielokrotna powinna być kontenerem asocjacyjnym z wyboru, gdy warunki kojarzenia wartości z kluczami są spełnione przez aplikację. Modelem dla tego typu struktury jest uporządkowana lista słów kluczowych ze skojarzonymi wartościami ciągów, dostarczająca np. definicje, w których słowa nie były zawsze zdefiniowane unikalnie. Jeśli zamiast tego słowa kluczowe zostały unikalnie zdefiniowane, tak że klucze są unikalne, wybranym kontenerem będzie map. Jeśli z drugiej strony, przechowywana była tylko lista wyrazów, poprawnym kontenerem będzie set. Jeżeli zezwolono na wiele wystąpień wyrazów, odpowiednią strukturą kontenera będzie multiset.

Multimap porządkuje sekwencji kontroluje przez wywołanie metody typu obiektu przechowywanej funkcji [key_compare](#key_compare). Ten obiekt przechowywanych jest funkcja porównanie, które mogą być używane przez wywołanie funkcji Członkowskich [key_comp](#key_comp). Ogólnie rzecz biorąc, elementy muszą być nieco mniej porównywalne, aby ustalić kolejność: tak aby, mając dowolne dwa elementy, można było określić, czy są one równoważne (w sensie, żaden nie jest mniejszy niż ten drugi) lub, że jeden jest mniejszy niż ten drugi. Skutkuje to ustaleniem kolejności dla elementów nierównoważnych. Ze strony bardziej technicznej, funkcja porównywania jest predykatem binarnym, który wymusza ścisłe słabe porządkowanie w standardowym sensie matematycznym. Predykat binarne `f(x,y)` jest obiektem funkcji, która ma dwa obiekty argument `x` i `y` i wartością zwracaną wartość PRAWDA lub FAŁSZ. Kolejność na zestaw jest niska strict, porządkowanie, jeśli binarne predykat jest niezwrotne antysymetryczne dają w wyniku i przechodnie i jeśli równoważność przechodnie, gdy dwa obiekty `x` i `y` są zdefiniowane jako równoważne, gdy oba `f(x,y)`i `f(y,x)` są wartość false. Jeśli silniejszy warunek równości pomiędzy kluczami zastąpi ten równoważności, to porządkowanie będzie całkowite (w sensie, że wszystkie elementy są uporządkowane względem siebie), a dopasowane klucze będą od siebie nieodróżnialne.

W języku C ++ 14 można włączyć heterogenicznych wyszukiwania, określając `std::less<>` lub `std::greater<>` predykatu, który nie ma typu parametrów. Aby uzyskać więcej informacji, zobacz [heterogenicznych wyszukiwanie w kontenerach asocjacyjnej](../standard-library/stl-containers.md#sequence_containers)

## <a name="members"></a>Elementy członkowskie

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[multimap](#multimap)|Konstruuje `multimap` jest pusta lub oznacza to kopie wszystkich lub niektórych innych części `multimap`.|

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[allocator_type](#allocator_type)|Typ reprezentujący `allocator` klasy dla `multimap` obiektu.|
|[const_iterator](#const_iterator)|Typ, który udostępnia iteratora dwukierunkowego, który może odczytać `const` element `multimap`.|
|[const_pointer](#const_pointer)|Typ, który dostarcza wskaźnik do `const` element `multimap`.|
|[const_reference](#const_reference)|Typ, który zawiera odwołanie do `const` element przechowywane w `multimap` do odczytu i wykonywania `const` operacji.|
|[const_reverse_iterator](#const_reverse_iterator)|Typ, który udostępnia iteratora dwukierunkowego, który może odczytać `const` element `multimap`.|
|[difference_type](#difference_type)|Wpisz liczbę całkowitą ze znakiem, służący do reprezentowania liczbę elementów `multimap` w zakresie między elementami wskazywana przez Iteratory.|
|[iterator](#iterator)|Typ, który zawiera różnicę między dwoma Iteratory, które odwołują się do elementów w tym samym `multimap`.|
|[key_compare](#key_compare)|Typ, który zawiera obiekt funkcji, które można porównać dwa klucze sortowania, aby określić względną kolejność dwóch elementów w `multimap`.|
|[key_type](#key_type)|Typ, który opisuje obiektu klucza sortowania, który stanowi każdy element `multimap`.|
|[mapped_type](#mapped_type)|Typ reprezentujący typ danych przechowywanych w `multimap`.|
|[pointer](#pointer)|Typ, który dostarcza wskaźnik do `const` element `multimap`.|
|[Odwołanie](#reference)|Typ, który zawiera odwołanie do elementu przechowywane w `multimap`.|
|[reverse_iterator](#reverse_iterator)|Typ, który udostępnia iteratora dwukierunkowego, które mogą odczytywać lub modyfikować elementu w odwróconej `multimap`.|
|[size_type](#size_type)|Typu Liczba całkowita bez znaku, który dostarcza wskaźnik do `const` element `multimap`.|
|[value_type](#value_type)|Typ, który zawiera obiekt funkcji, który można porównać dwóch elementów jako klucze sortowania, aby określić ich kolejność względne w `multimap`.|

### <a name="member-functions"></a>Funkcje Członkowskie

|Funkcja członkowska|Opis|
|-|-|
|[begin](#begin)|Zwraca iteratora adresowania pierwszym elementem w `multimap`.|
|[cbegin](#cbegin)|Zwraca const iteratora adresowania pierwszym elementem w `multimap`.|
|[cend](#cend)|Zwraca iteratora const, który dotyczy lokalizacji pomyślne ostatnim elementem w `multimap`.|
|[Wyczyść](#clear)|Usuwa wszystkie elementy `multimap`.|
|[Liczba](#count)|Zwraca liczbę elementów w `multimap` którego klucz odpowiada parametr określony klucz.|
|[crbegin](#crbegin)|Zwraca const iteratora adresowania pierwszym elementem w odwróconej `multimap`.|
|[crend](#crend)|Zwraca iteratora const, który dotyczy lokalizacji pomyślne ostatnim elementem w odwrotnej `multimap`.|
|[emplace](#emplace)|Wstawia element w miejscu do skonstruować `multimap`.|
|[emplace_hint](#emplace_hint)|Wstawia element w miejscu do skonstruować `multimap`, ze wskazówką umieszczania|
|[pusty](#empty)|Sprawdza, czy `multimap` jest pusta.|
|[Koniec](#end)|Zwraca iteratora, którego dotyczy lokalizacji pomyślne ostatnim elementem w `multimap`.|
|[equal_range](#equal_range)|Wyszukuje zakres elementów, gdzie klucz elementu pasuje do określonej wartości.|
|[wymazywanie](#erase)|Usuwa element lub zakresu elementów `multimap` z określonych pozycji lub usuwa elementy zgodne z określonym kluczem.|
|[Znajdź](#find)|Zwraca iteratora adresowania lokalizację pierwszego elementu w `multimap` mający klucz równoważne z określonym kluczem.|
|[get_allocator](#get_allocator)|Zwraca kopię `allocator` użyty do utworzenia obiektu `multimap`.|
|[Wstaw](#insert)|Wstawia element lub zakres elementów do `multimap`.|
|[key_comp](#key_comp)|Pobiera kopię porównania obiekt używany do kolejność kluczy w `multimap`.|
|[lower_bound](#lower_bound)|Zwraca pierwszy element w iteratora `multimap` który za pomocą klucza, który jest równy lub większy niż określony klucz.|
|[max_size](#max_size)|Zwraca maksymalną długość `multimap`.|
|[rbegin](#rbegin)|Zwraca iteratora adresowania pierwszym elementem w odwróconej `multimap`.|
|[rend](#rend)|Zwraca iteratora, którego dotyczy lokalizacji pomyślne ostatnim elementem w odwróconej `multimap`.|
|[Rozmiar](#size)|Zwraca liczbę elementów w `multimap`.|
|[swap](#swap)|Zamienia elementy dwóch `multimap`s.|
|[upper_bound](#upper_bound)|Zwraca pierwszy element w iteratora `multimap` który za pomocą klucza, który jest większy niż określony klucz.|
|[value_comp](#value_comp)|Funkcja członkowska zwraca obiekt funkcji, który określa kolejność elementów `multimap` porównując wartości klucza.|

### <a name="operators"></a>Operatory

|Operator|Opis|
|-|-|
|[operator=](#op_eq)|Zastępuje elementy `multimap` z kopią innego `multimap`.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<mapy >

**Namespace:** Standard

( **Klucza**, **wartość**) pary są przechowywane w multimap jako obiekty typu `pair`. Klasa pary wymaga nagłówka \<narzędzie >, który jest automatycznie uwzględniany przez \<mapy >.

## <a name="allocator_type"></a>  multimap::allocator_type

Typ, który reprezentuje klasę alokatora dla obiekt multimap —.

```cpp
typedef Allocator allocator_type;
```

### <a name="example"></a>Przykład

Zobacz przykład [get_allocator](#get_allocator) na przykład za pomocą `allocator_type`.

## <a name="begin"></a>  multimap::BEGIN

Zwraca adresowania pierwszego elementu w multimap iteratora.

```cpp
const_iterator begin() const;

iterator begin();
```

### <a name="return-value"></a>Wartość zwracana

Adresowanie pierwszego elementu w multimap lub lokalizacji pomyślne pusty multimap iteratora dwukierunkowego.

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

Zwraca `const` iteratora, którego dotyczy pierwszy element w zakresie.

```cpp
const_iterator cbegin() const;
```

### <a name="return-value"></a>Wartość zwracana

A `const` iteratora dwukierunkowego dostępu, wskazujące na pierwszym elementem w zakresie lub lokalizacji bezpośrednio po zakończeniu pustego zakresu (dla pustego zakresu, `cbegin() == cend()`).

### <a name="remarks"></a>Uwagi

Z wartością zwracaną z `cbegin`, elementy w zakresie nie może być modyfikowany.

Można użyć funkcji członkowskiej zamiast `begin()` funkcji członkowskiej, aby zagwarantować, że jest zwracana wartość `const_iterator`. Zazwyczaj jest używany w połączeniu z [automatycznie](../cpp/auto-cpp.md) wpisz słowo kluczowe wnioskowanie, jak pokazano w poniższym przykładzie. W tym przykładzie należy wziąć pod uwagę `Container` do można modyfikować (z systemem innym niż `const`) kontenera dowolnego rodzaju, który obsługuje `begin()` i `cbegin()`.

```cpp
auto i1 = Container.begin();
// i1 is Container<T>::iterator
auto i2 = Container.cbegin();

// i2 is Container<T>::const_iterator
```

## <a name="cend"></a>  multimap::cend

Zwraca `const` iteratora, którego dotyczy lokalizacji bezpośrednio po ostatnim elementem w zakresie.

```cpp
const_iterator cend() const;
```

### <a name="return-value"></a>Wartość zwracana

A `const` iteratora dwukierunkowego dostępu, który wskazuje poza koniec zakresu.

### <a name="remarks"></a>Uwagi

`cend` Służy do sprawdzenia, czy iteratora osiągnęła koniec zakresu.

Można użyć funkcji członkowskiej zamiast `end()` funkcji członkowskiej, aby zagwarantować, że jest zwracana wartość `const_iterator`. Zazwyczaj jest używany w połączeniu z [automatycznie](../cpp/auto-cpp.md) wpisz słowo kluczowe wnioskowanie, jak pokazano w poniższym przykładzie. W tym przykładzie należy wziąć pod uwagę `Container` do można modyfikować (z systemem innym niż `const`) kontenera dowolnego rodzaju, który obsługuje `end()` i `cend()`.

```cpp
auto i1 = Container.end();
// i1 is Container<T>::iterator
auto i2 = Container.cend();

// i2 is Container<T>::const_iterator
```

Wartość zwrócona przez `cend` nie powinny być wyłuskiwany.

## <a name="clear"></a>  multimap::Clear

Usuwa wszystkie elementy multimap.

```cpp
void clear();
```

### <a name="example"></a>Przykład

W poniższym przykładzie pokazano użycie funkcji członkowskiej multimap::clear.

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

Typ, który udostępnia iteratora dwukierunkowego, który może odczytać **const** element multimap.

```cpp
typedef implementation-defined const_iterator;
```

### <a name="remarks"></a>Uwagi

Typ `const_iterator` nie może służyć do modyfikowania wartości elementu.

`const_iterator` Zdefiniowany przez multimap — punkty do obiektów [value_type](#value_type), które są typu `pair` * \< * **const klucza**, **Typu *** >*. Wartość klucza jest dostępna za pośrednictwem pierwszego pary elementu członkowskiego i wartość mapowanego elementu jest dostępna za pośrednictwem drugiego elementu członkowskiego pary.

Aby usunąć odwołania do `const_iterator` `cIter` wskazuje element w multimap, użyj **->** operatora.

Aby uzyskać dostęp do wartości klucza dla elementu, użyj `cIter`  ->  **pierwszy**, który jest odpowiednikiem (\* `cIter`). **pierwszy**. Aby uzyskać dostęp do wartości zamapowanych punktu odniesienia dla elementu, użyj `cIter`  ->  **drugi**, który jest odpowiednikiem (\* `cIter`). **drugi**.

### <a name="example"></a>Przykład

Zobacz przykład [rozpocząć](#begin) na przykład za pomocą `const_iterator`.

## <a name="const_pointer"></a>  multimap::const_pointer

Typ, który dostarcza wskaźnik do **const** element multimap.

```cpp
typedef typename allocator_type::const_pointer const_pointer;
```

### <a name="remarks"></a>Uwagi

Typ `const_pointer` nie może służyć do modyfikowania wartości elementu.

W większości przypadków [iterator](#iterator) mają być używane do uzyskania dostępu do elementów w obiekcie multimap —.

## <a name="const_reference"></a>  multimap::const_reference

Typ, który zawiera odwołanie do **const** element przechowywane w multimap do odczytu i wykonywania **const** operacji.

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

Typ, który udostępnia iteratora dwukierunkowego, który może odczytać **const** element multimap.

```cpp
typedef std::reverse_iterator<const_iterator> const_reverse_iterator;
```

### <a name="remarks"></a>Uwagi

Typ `const_reverse_iterator` nie można zmodyfikować wartości elementu i umożliwia iterację multimap odwrotnie.

`const_reverse_iterator` Zdefiniowany przez multimap — punkty do obiektów [value_type](#value_type), które są typu `pair` * \< * **const klucza**, **Typu *** >*. Wartość klucza jest dostępna za pośrednictwem pierwszego pary elementu członkowskiego i wartość mapowanego elementu jest dostępna za pośrednictwem drugiego elementu członkowskiego pary.

Aby usunąć odwołania do `const_reverse_iterator` `crIter` wskazuje element w multimap, użyj **->** operatora.

Aby uzyskać dostęp do wartości klucza dla elementu, użyj `crIter`  ->  **pierwszy**, który jest odpowiednikiem (\* `crIter`). **pierwszy**. Aby uzyskać dostęp do wartości zamapowanych punktu odniesienia dla elementu, użyj `crIter`  ->  **drugi**, który jest odpowiednikiem (\* `crIter`). **pierwszy**.

### <a name="example"></a>Przykład

Zobacz przykład [rend](#rend) przykład sposobu deklarowanie i użycie `const_reverse_iterator`.

## <a name="count"></a>  multimap::Count

Zwraca liczbę elementów w multimap, którego klucze pasują do siebie klucza określony przez parametr.

```cpp
size_type count(const Key& key) const;
```

### <a name="parameters"></a>Parametry

`key` Klucz elementu do dopasowania z multimap.

### <a name="return-value"></a>Wartość zwracana

Liczba elementów, których klucze sortowania zgodny z kluczem parametru; 0, jeśli multimap nie zawiera element z kluczem dopasowania.

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca liczbę elementów w zakresie

[ `lower_bound` (_ *Klucza* ), `upper_bound` (\_ *klucza* ))

które mają wartość klucza `key`.

### <a name="example"></a>Przykład

W poniższym przykładzie pokazano użycie funkcji członkowskiej multimap::count.

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

Zwraca const iteratora adresowania pierwszego elementu w multimap odwróconej.

```cpp
const_reverse_iterator crbegin() const;
```

### <a name="return-value"></a>Wartość zwracana

Stała wstecznego iteratora dwukierunkowego adresowania pierwszym elementem w odwróconej [multimap](../standard-library/multimap-class.md) lub adresowania co była ostatnim elementem w stałe `multimap`.

### <a name="remarks"></a>Uwagi

`crbegin` jest używany z odwróconej `multimap` podobnie jak [rozpocząć](#begin) jest używany z `multimap`.

Z wartością zwracaną z `crbegin`, `multimap` obiektu nie może być modyfikowany.

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

Zwraca iteratora const, który dotyczy lokalizacji pomyślne wykonanie ostatniego elementu w odwróconej multimap.

```cpp
const_reverse_iterator crend() const;
```

### <a name="return-value"></a>Wartość zwracana

Stała wstecznego iteratora dwukierunkowego, który dotyczy lokalizacji pomyślne ostatnim elementem w odwrotnej [multimap](../standard-library/multimap-class.md) (lokalizacji, która ma przed pierwszym elementem w stałe `multimap`).

### <a name="remarks"></a>Uwagi

`crend` jest używany z odwróconej `multimap` podobnie jak [multimap::end](#end) jest używany z `multimap`.

Z wartością zwracaną z `crend`, `multimap` obiektu nie może być modyfikowany.

`crend` można sprawdzać, czy odwrotnej iteratora osiągnął koniec jego `multimap`.

Wartość zwrócona przez `crend` nie powinny być wyłuskiwany.

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

Typ liczbę całkowitą ze znakiem, który może służyć do reprezentowania liczba elementów multimap w zakresie między elementami wskazywana przez Iteratory.

```cpp
typedef typename allocator_type::difference_type difference_type;
```

### <a name="remarks"></a>Uwagi

`difference_type` Jest typ zwracany, gdy odjęcie lub zwiększanie za pośrednictwem Iteratory kontenera. `difference_type` Jest zwykle używana do reprezentowania liczba elementów w zakresie [*pierwszy*, *ostatniego*) między Iteratory `first` i `last`, zawiera element wskazywał przez `first` i zakres elementów do, ale nie w tym elemencie wskazywana przez `last`.

Należy pamiętać, że chociaż `difference_type` jest dostępna dla wszystkich Iteratory, które spełniają wymagania iterację wejściowy zawiera klasę Iteratory dwukierunkowego obsługiwane przez kontenery odwracalny, takich jak zestaw, odejmowania między Iteratory jest tylko obsługiwane przez Iteratory dostępie swobodnym udostępniane przez kontener dostępie swobodnym, takich jak wektorowa.

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

Wstawia element skonstruowane w miejscu (nie ma operacji kopiowania lub przenoszenia są wykonywane).

```cpp
template <class... Args>
iterator emplace(Args&&... args);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|-|-|
|`args`|Argumenty przekazane do skonstruowania elementu można wstawiać do multimap.|

### <a name="return-value"></a>Wartość zwracana

Iteratora do nowo wstawiony element.

### <a name="remarks"></a>Uwagi

Nie odwołania do elementów kontenera jest nieważnych przez tę funkcję, ale może unieważnić wszystkie Iteratory do kontenera.

Jeśli podczas wstawiania jest zgłaszany wyjątek, kontener pozostaje niezmieniony i jest zgłoszony wyjątek.

[Value_type](../standard-library/map-class.md#value_type) elementu jest parę, tak, aby wartość elementu uporządkowanej pary z pierwszym składnikiem równa wartości klucza i drugi składnik wartość danych elementu.

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

Wstawia element skonstruowane w miejscu (nie ma operacji kopiowania lub przenoszenia są wykonywane), ze wskazówką umieszczania.

```cpp
template <class... Args>
iterator emplace_hint(
    const_iterator where,
    Args&&... args);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|-|-|
|`args`|Argumenty przekazane do skonstruowania elementu można wstawiać do multimap.|
|`where`|Miejsce, aby rozpocząć wyszukiwanie poprawny punkt wstawiania. (Jeśli bezpośrednio przed tym punktem `where`, wstawiania może wystąpić w czasie stałej amortyzowanego, zamiast logarytmicznej czasu.)|

### <a name="return-value"></a>Wartość zwracana

Iteratora do nowo wstawiony element.

### <a name="remarks"></a>Uwagi

Nie odwołania do elementów kontenera jest nieważnych przez tę funkcję, ale może unieważnić wszystkie Iteratory do kontenera.

Podczas umieszczanie Jeśli wyjątek jest zgłaszany, stan kontenera nie jest modyfikowany.

[Value_type](../standard-library/map-class.md#value_type) elementu jest parę, tak, aby wartość elementu uporządkowanej pary z pierwszym składnikiem równa wartości klucza i drugi składnik wartość danych elementu.

Na przykład kod, zobacz [map::emplace_hint](../standard-library/map-class.md#emplace_hint).

## <a name="empty"></a>  multimap::Empty

Testy, jeśli multimap jest pusta.

```cpp
bool empty() const;
```

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli multimap jest pusta. **false** Jeśli multimap nie jest pusty.

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

Iterator przeszłości end. Jeśli multimap jest pusta, następnie `multimap::end() == multimap::begin()`.

### <a name="remarks"></a>Uwagi

**końcowy** używany do sprawdzania, czy iteratora osiągnęła koniec jego multimap.

Wartość zwrócona przez **zakończenia** nie powinny być wyłuskiwany.

Na przykład kod, zobacz [multimap::find](#find).

## <a name="equal_range"></a>  multimap::equal_range

Wyszukuje zakres elementów, gdzie klucz elementu pasuje do określonej wartości.

```cpp
pair <const_iterator, const_iterator> equal_range (const Key& key) const;

pair <iterator, iterator> equal_range (const Key& key);
```

### <a name="parameters"></a>Parametry

`key` Klucz argumentu, który ma zostać porównane z klucza sortowania z elementem z multimap przeszukiwany.

### <a name="return-value"></a>Wartość zwracana

Para Iteratory tak, aby był pierwszy [lower_bound](#lower_bound) klucz, a drugi jest [upper_bound](#upper_bound) klucza.

Pierwszy iteratora pary dostępu do `pr` zwracane przez funkcję elementu członkowskiego, użyj `pr`. **pierwszy** i aby usunąć odwołania do iteratora dolnej granicy, należy użyć \*( `pr`. **najpierw**). Drugi iteratora pary dostępu do `pr` zwracane przez funkcję elementu członkowskiego, użyj `pr`. **drugi** i aby usunąć odwołania do iteratora górnej granicy, należy użyć \*( `pr`. **drugi**).

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
        << " matching the 2nd element of the pair"
        << " returned by equal_range( 2 )." << endl;

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

Usuwa element lub zakres elementów w multimap z określonych pozycji lub usuwa elementy zgodne z określonym kluczem.

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

`Where` Położenie elementu do usunięcia.

`First` Pozycja pierwszego elementu do usunięcia.

`Last` Pozycja poza ostatni element do usunięcia.

`Key` Klucz elementu do usunięcia.

### <a name="return-value"></a>Wartość zwracana

Dla pierwszego funkcji dwóch elementów członkowskich iteratora dwukierunkowego który wyznacza pierwszy element pozostałych poza wszelkie elementy usunięte lub element, który nie zawiera żadnego takiego elementu sygnalizuje koniec mapy.

Dla innych funkcji członkowskiej zwraca liczbę elementów, które zostały usunięte z multimap.

### <a name="remarks"></a>Uwagi

Na przykład kod, zobacz [map::erase](../standard-library/map-class.md#erase).

## <a name="find"></a>  multimap::Find

Zwraca iterację odwołuje się do lokalizacji pierwszego elementu w multimap, który ma klucz równoważne z określonym kluczem.

```cpp
iterator find(const Key& key);


const_iterator find(const Key& key) const;
```

### <a name="parameters"></a>Parametry

`key` Wartość klucza do dopasowania za pomocą klucza sortowania z elementem z multimap przeszukiwany.

### <a name="return-value"></a>Wartość zwracana

Iteratora odnoszący się do lokalizacji element z określonym kluczem lub lokalizacji pomyślne wykonanie ostatniego elementu w multimap ( `multimap::end()`) Jeśli nie znaleziono klucza.

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca iterację odwołuje się do elementu w multimap, którego klucz sortowania jest odpowiednikiem klucza argument w predykat binarne wywołujące kolejność oparte na mniej niż porównywalności relacji.

Jeśli wartość zwracana **znaleźć** jest przypisany do **const_iterator**, multimap — obiektu nie może być modyfikowany. Jeśli wartość zwracana **znaleźć** jest przypisany do **iterator**, multimap — obiekt może być modyfikowany.

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

Zwraca kopię obiektu alokatora użyta do skonstruowania multimap.

```cpp
allocator_type get_allocator() const;
```

### <a name="return-value"></a>Wartość zwracana

Allocator — używane przez multimap.

### <a name="remarks"></a>Uwagi

Allocators — dla klasy multimap — Określ zarządzaniu klasę magazynu. Allocators — domyślna dostarczony wraz z klasy kontenerów standardowa biblioteka C++ są wystarczające dla większości potrzeb programowania. Pisanie i przy użyciu klasy alokatora jest temat zaawansowany C++.

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

Wstawia element lub zakres elementów do multimap.

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
|`Val`|Wartość elementu ma zostać wstawiony do multimap.|
|`Where`|Miejsce, aby rozpocząć wyszukiwanie poprawny punkt wstawiania. (Jeśli bezpośrednio przed tym punktem `Where`, wstawiania może wystąpić w czasie stałej amortyzowanego, zamiast logarytmicznej czasu.)|
|`ValTy`|Parametr szablonu, który określa typ argumentu, który mapy można używać do tworzenia elementu [value_type](../standard-library/map-class.md#value_type), a idealnych przekazuje `Val` jako argument.|
|`First`|Pozycja pierwszego elementu do skopiowania.|
|`Last`|Pozycja poza ostatni element do skopiowania.|
|`InputIterator`|Argument funkcji szablonu, który spełnia wymagania [wejściowych iteratora](../standard-library/input-iterator-tag-struct.md) wskazującego elementów typu, który może służyć do utworzenia [value_type](../standard-library/map-class.md#value_type) obiektów.|
|`IList`|[Initializer_list](../standard-library/initializer-list.md) z którego można skopiować elementów.|

### <a name="return-value"></a>Wartość zwracana

Funkcje Członkowskie jednym elementu wstawienie (1) i (2) zwraca iteratora miejsce, w którym wstawiono nowy element do multimap.

Funkcje Członkowskie pojedynczego elementu z wskazówki, (3) i (4) zwraca wskazującą położenie, w którym wstawiono nowy element do multimap iteratora.

### <a name="remarks"></a>Uwagi

Brak wskaźniki lub odwołania jest nieważnych przez tę funkcję, ale może unieważnić wszystkie Iteratory do kontenera.

Podczas wstawiania tylko jednego elementu jeśli wyjątek jest zgłaszany, stan kontenera nie jest modyfikowany. Podczas wstawiania wiele elementów jeśli wyjątek kontenera pozostaje w stanie nieokreślony, ale prawidłowy.

[Value_type](../standard-library/map-class.md#value_type) kontenera jest element typedef, który należy do kontenera i mapy, `multimap<K, V>::value_type` jest `pair<const K, V>`. Wartość elementu jest uporządkowana pary, w którym znajduje się pierwszy składnik jest równa wartości klucza, a drugi składnik jest równa wartości danych elementu.

Zakres funkcji członkowskiej (5) wstawia sekwencji wartości elementów do multimap, odpowiadający każdemu elementowi dotyczy iterację w zakresie `[First, Last)`; w związku z tym `Last` nie Pobierz wstawione. Funkcja członkowska kontenera `end()` odwołuje się do położenia zaraz po ostatnim elementem w kontenerze — na przykład instrukcja `m.insert(v.begin(), v.end());` wstawia wszystkie elementy `v` do `m`.

(6) używa funkcji członkowskiej liście inicjatorów [initializer_list](../standard-library/initializer-list.md) skopiuj elementy do mapy.

Do wstawienia elementu w miejscu skonstruować — to znaczy są wykonywane żadne operacje kopiowania lub przenoszenia — zobacz [multimap::emplace](#emplace) i [multimap::emplace_hint](#emplace_hint).

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

Typ, który udostępnia iteratora dwukierunkowego, które mogą odczytywać lub modyfikować dowolny element w multimap.

```cpp
typedef implementation-defined iterator;
```

### <a name="remarks"></a>Uwagi

**Iteratora** zdefiniowany przez multimap — punkty do obiektów [value_type](#value_type), które są typu `pair` * \< * **const klucza**, **Typu *** >*. Wartość klucza jest dostępna za pośrednictwem pierwszego pary elementu członkowskiego i wartość mapowanego elementu jest dostępna za pośrednictwem drugiego elementu członkowskiego pary.

Aby usunąć odwołania do **iterator** `Iter` wskazuje element w multimap, użyj **->** operatora.

Aby uzyskać dostęp do wartości klucza dla elementu, użyj `Iter`  ->  **pierwszy**, który jest odpowiednikiem (\* `Iter`). **pierwszy**. Aby uzyskać dostęp do wartości zamapowanych punktu odniesienia dla elementu, użyj `Iter`  ->  **drugi**, który jest odpowiednikiem (\* `Iter`). **drugi**.

Typ **iterator** może służyć do modyfikowania wartości elementu.

### <a name="example"></a>Przykład

Zobacz przykład [rozpocząć](#begin) przykład sposobu deklarowanie i użycie **iterator**.

## <a name="key_comp"></a>  multimap::key_comp

Pobiera kopię obiektu porównania używany kolejność kluczy w multimap.

```cpp
key_compare key_comp() const;
```

### <a name="return-value"></a>Wartość zwracana

Zwraca obiekt funkcja multimap używa do porządkowania jej elementów.

### <a name="remarks"></a>Uwagi

Obiekt przechowywanych definiuje funkcję elementu członkowskiego

**bool operator**( **const klucza &** *x*, **const klucza &** *y*);

która zwraca wartość true, jeśli *x* ściśle poprzedza *y* w kolejności sortowania.

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

Typ, który udostępnia obiekt funkcji, które można porównać dwa klucze sortowania w celu ustalenia względną kolejność dwóch elementów multimap.

```cpp
typedef Traits key_compare;
```

### <a name="remarks"></a>Uwagi

**key_compare** jest synonimem parametru szablonu `Traits`.

Aby uzyskać więcej informacji na temat `Traits` zobacz [multimap — klasa](../standard-library/multimap-class.md) tematu.

### <a name="example"></a>Przykład

Zobacz przykład [key_comp](#key_comp) przykład sposobu deklarowanie i użycie `key_compare`.

## <a name="key_type"></a>  multimap::key_type

Typ, który opisuje obiektu klucza sortowania, który stanowi każdy element multimap.

```cpp
typedef Key key_type;
```

### <a name="remarks"></a>Uwagi

**key_type** jest synonimem parametru szablonu `Key`.

Aby uzyskać więcej informacji na temat `Key`, zobacz sekcję uwag [multimap — klasa](../standard-library/multimap-class.md) tematu.

### <a name="example"></a>Przykład

Zobacz przykład [value_type](#value_type) przykład sposobu deklarowanie i użycie `key_type`.

## <a name="lower_bound"></a>  multimap::lower_bound

Zwraca iteratora do pierwszego elementu w multimap który za pomocą klucza, który jest równy lub większy niż określony klucz.

```cpp
iterator lower_bound(const Key& key);

const_iterator lower_bound(const Key& key) const;
```

### <a name="parameters"></a>Parametry

`key` Klucz argumentu, który ma zostać porównane z klucza sortowania z elementem z multimap przeszukiwany.

### <a name="return-value"></a>Wartość zwracana

Iterator lub `const_iterator` czy adresy lokalizacji elementu w multimap, że za pomocą klucza, która jest równa lub większa niż klucz argumentu, lub który adresów lokalizacji pomyślne ostatniego elementu w multimap, jeśli nie są zgodne znajduje się dla klucza.

Jeśli wartość zwracana `lower_bound` jest przypisany do `const_iterator`, multimap — obiektu nie może być modyfikowany. Jeśli wartość zwracana `lower_bound` jest przypisany do **iterator**, multimap — obiekt może być modyfikowany.

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

Typ, który reprezentuje typ danych przechowywanych w multimap.

```cpp
typedef Type mapped_type;
```

### <a name="remarks"></a>Uwagi

`mapped_type` synonim parametru szablonu jest `Type`.

Aby uzyskać więcej informacji na temat `Type` zobacz [multimap — klasa](../standard-library/multimap-class.md) tematu.

### <a name="example"></a>Przykład

Zobacz przykład [value_type](#value_type) przykład sposobu deklarowanie i użycie `key_type`.

## <a name="max_size"></a>  multimap::max_size

Zwraca maksymalną długość multimap.

```cpp
size_type max_size() const;
```

### <a name="return-value"></a>Wartość zwracana

Maksymalna długość możliwe multimap.

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

Tworzy multimap, który jest pusta lub kopii całości lub części niektóre inne multimap.

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
|`Al`|Klasa przydzielania magazynu do użycia dla tego obiektu multimap —, która domyślnie określa przydzielania.|
|`Comp`|Funkcja porównywania typu **constTraits** porządkowania elementów w tablicy, która domyślnie określa **cech**.|
|`Right`|Mapy skonstruowane zestawu ma być kopii.|
|`First`|Pozycja pierwszego elementu w zakresie elementów do skopiowania.|
|`Last`|Pozycja pierwszego elementu poza zakres elementów do skopiowania.|
|`IList`|Lista initializer_list, z której mają być skopiowane elementy.|

### <a name="remarks"></a>Uwagi

Typ obiektu przydzielania, który zarządza przechowywania w pamięci dla multimap i który później może być zwracany przez wywołanie metody przechowywania wszystkie konstruktory [get_allocator](#get_allocator). Parametr przydzielania jest często pomijany w deklaracjach klas i przetwarzania wstępnego makra używany do zastąpienia alternatywnych allocators —.

Wszystkie konstruktory zainicjować ich multimap.

Wszystkie konstruktory przechowywania obiektem funkcji typu `Traits` używany do ustanawiania zamówienia wśród kluczy multimap i który później może być zwracany przez wywołanie metody [key_comp](#key_comp).

Pierwsze trzy konstruktorów Określ pusty multimap początkowej, drugi określający typ porównania funkcji ( `Comp`) do użycia w ustalaniu kolejności elementów i trzeci jawne określenie programu przydzielania wpisz ( `Al`) do można użyć. Słowo kluczowe `explicit` pomija określonych rodzajów typu automatycznej konwersji.

Konstruktor czwarty Określa kopię multimap `Right`.

Konstruktor piątej Określa kopię multimap przenosząc `Right`.

Szóstego, siódmego i ósmego członkami initializer_list kopiowanie konstruktorów.

Konstruktory trzech kolejnych skopiuj zakres `[First, Last)` mapy rosnącymi explicitness określania typu porównanie funkcji klasy **cech** i przydzielania.

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
    // function of geater than, then insert 2 elements
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

Zamienia elementy multimap kopię multimap innego.

```cpp
multimap& operator=(const multimap& right);

multimap& operator=(multimap&& right);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|-|-|
|`right`|[Multimap](../standard-library/multimap-class.md) kopiowane do `multimap`.|

### <a name="remarks"></a>Uwagi

Po wykonaniu elementy w `multimap`, `operator=` albo kopiuje lub przenosi zawartość `right` do `multimap`.

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

Typ, który dostarcza wskaźnik do elementu w multimap.

```cpp
typedef typename allocator_type::pointer pointer;
```

### <a name="remarks"></a>Uwagi

Typ **wskaźnika** może służyć do modyfikowania wartości elementu.

W większości przypadków [iterator](#iterator) mają być używane do uzyskania dostępu do elementów w obiekcie multimap —.

## <a name="rbegin"></a>  multimap::rbegin

Zwraca iteratora adresowania pierwszego elementu w multimap odwróconej.

```cpp
const_reverse_iterator rbegin() const;

reverse_iterator rbegin();
```

### <a name="return-value"></a>Wartość zwracana

Iterator odwrotnej dwukierunkowego adresowania pierwszego elementu w odwróconej multimap lub adresowania, jaki był ostatni element w multimap stałe.

### <a name="remarks"></a>Uwagi

`rbegin` jest używany z odwróconej multimap podobnie jak [rozpocząć](#begin) jest używany z multimap.

Jeśli wartość zwracana `rbegin` jest przypisany do `const_reverse_iterator`, a następnie obiektu multimap — nie można modyfikować. Jeśli wartość zwracana `rbegin` jest przypisany do `reverse_iterator`, a następnie można zmodyfikować obiektu multimap —.

`rbegin` może służyć do iterowania po multimap Wstecz.

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
   // throught a multimap in a forward order
   cout << "The multimap is: ";
   for ( m1_Iter = m1.begin( ) ; m1_Iter != m1.end( ); m1_Iter++)
      cout << m1_Iter -> first << " ";
      cout << "." << endl;

   // rbegin can be used to start an iteration
   // throught a multimap in a reverse order
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

Typ, który zawiera odwołanie do elementu przechowywane w multimap.

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

Zwraca, którego dotyczy lokalizacji pomyślne wykonanie ostatniego elementu w odwróconej multimap iteratora.

```cpp
const_reverse_iterator rend() const;

reverse_iterator rend();
```

### <a name="return-value"></a>Wartość zwracana

Iterator odwrotnej dwukierunkowego, którego dotyczy lokalizacji pomyślne wykonanie ostatniego elementu w odwróconej multimap (lokalizacja miał przed pierwszym elementem w stałe multimap).

### <a name="remarks"></a>Uwagi

`rend` jest używany z odwróconej multimap podobnie jak [zakończenia](../standard-library/map-class.md#end) jest używany z multimap.

Jeśli wartość zwracana `rend` jest przypisany do `const_reverse_iterator`, a następnie obiektu multimap — nie można modyfikować. Jeśli wartość zwracana `rend` jest przypisany do `reverse_iterator`, a następnie można zmodyfikować obiektu multimap —.

`rend` można sprawdzać, czy osiągnął koniec jego multimap odwrotnej iteratora.

Wartość zwrócona przez `rend` nie powinny być wyłuskiwany.

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
   // throught a multimap in a forward order
   cout << "The multimap is: ";
   for ( m1_Iter = m1.begin( ) ; m1_Iter != m1.end( ); m1_Iter++)
      cout << m1_Iter -> first << " ";
      cout << "." << endl;

   // rbegin can be used to start an iteration
   // throught a multimap in a reverse order
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

Typ, który udostępnia iteratora dwukierunkowego, które mogą odczytywać lub modyfikować elementu w multimap odwróconej.

```cpp
typedef std::reverse_iterator<iterator> reverse_iterator;
```

### <a name="remarks"></a>Uwagi

Typ `reverse_iterator` umożliwia iterację multimap odwrotnie.

`reverse_iterator` Zdefiniowany przez multimap — punkty do obiektów [value_type](#value_type), które są typu `pair` * \< * **const klucza**, **Typu *** >*. Wartość klucza jest dostępna za pośrednictwem pierwszego pary elementu członkowskiego i wartość mapowanego elementu jest dostępna za pośrednictwem drugiego elementu członkowskiego pary.

Aby usunąć odwołania do `reverse_iterator` `rIter` wskazuje element w multimap, użyj -> — operator.

Aby uzyskać dostęp do wartości klucza dla elementu, użyj `rIter`  ->  **pierwszy**, który jest odpowiednikiem (\* `rIter`). **pierwszy**. Aby uzyskać dostęp do wartości zamapowanych punktu odniesienia dla elementu, użyj `rIter`  ->  **drugi**, który jest odpowiednikiem (\* `rIter`). **pierwszy**.

### <a name="example"></a>Przykład

Zobacz przykład [rbegin](#rbegin) przykład sposobu deklarowanie i użycie `reverse_iterator`.

## <a name="size"></a>  multimap::size

Zwraca liczbę elementów w multimap.

```cpp
size_type size() const;
```

### <a name="return-value"></a>Wartość zwracana

Bieżąca długość multimap.

### <a name="example"></a>Przykład

W poniższym przykładzie pokazano użycie funkcji członkowskiej multimap::size.

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

Typ liczby całkowitej bez znaku, które zlicza liczbę elementów w multimap.

```cpp
typedef typename allocator_type::size_type size_type;
```

### <a name="example"></a>Przykład

Zobacz przykład [rozmiar](#size) przykład sposobu deklarowanie i użycie `size_type`

## <a name="swap"></a>  multimap::swap

Zamienia multimaps dwa elementy.

```cpp
void swap(
    multimap<Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parametry

`right` Multimap dostarczanie elementy zamianę lub multimap, której elementy są wymienianych z tymi multimap `left`.

### <a name="remarks"></a>Uwagi

Funkcja członkowska unieważnia nie odwołań, wskaźniki lub Iteratory, które określają elementów w dwóch multimaps, której elementy są wymieniane.

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

Zwraca iteratora do pierwszego elementu w multimap który za pomocą klucza, który jest większy niż określony klucz.

```cpp
iterator upper_bound(const Key& key);

const_iterator upper_bound(const Key& key) const;
```

### <a name="parameters"></a>Parametry

`key` Klucz argumentu, który ma zostać porównane z klucza sortowania z elementem z multimap przeszukiwany.

### <a name="return-value"></a>Wartość zwracana

Iterator lub `const_iterator` czy adresy lokalizacji elementu w multimap, że za pomocą klucza jest większa niż klucz argumentu, lub że adresów lokalizacji pomyślne ostatniego elementu w multimap, jeśli nie są zgodne znajduje się dla klucza.

Jeśli wartość zwracana jest przypisany do `const_iterator`, multimap — obiektu nie może być modyfikowany. Jeśli wartość zwracana jest przypisany do **iterator**, multimap — obiekt może być modyfikowany.

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
   // found using a derefenced iterator addressing the location
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

Funkcja członkowska zwraca obiekt funkcji, który określa kolejność elementów w multimap porównując wartości klucza.

```cpp
value_compare value_comp() const;
```

### <a name="return-value"></a>Wartość zwracana

Zwraca obiekt funkcja porównania multimap używa do porządkowania jej elementów.

### <a name="remarks"></a>Uwagi

Dla multimap *m*, jeśli dwa elementy *e*1 ( *k*1, *d*1) i *e*2 ( *k*2, `d`2) obiekty typu `value_type`, gdzie *k*1 i *k*2 są ich kluczy typu `key_type` i `d`1 i `d`2 są dane typu `mapped_type`, następnie *m.*`value_comp`( *e*1, *e*2) jest odpowiednikiem *m.* `key_comp` ( *k*1, *k*2).

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

Typ, który reprezentuje typ obiektu przechowywane jako element na mapie.

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
   // explicitely to avoid implicit type conversion
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

[\<Mapa > elementy członkowskie](http://msdn.microsoft.com/en-us/7e8f0bc2-6034-40f6-9d14-76d4cef86308)<br/>
[Kontenery](../cpp/containers-modern-cpp.md)<br/>
[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Dokumentacja standardowej biblioteki C++](../standard-library/cpp-standard-library-reference.md)<br/>
