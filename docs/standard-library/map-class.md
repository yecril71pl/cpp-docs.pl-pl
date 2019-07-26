---
title: map — Klasa
ms.date: 10/18/2018
f1_keywords:
- map/std::map
- map/std::map::allocator_type
- map/std::map::const_iterator
- map/std::map::const_pointer
- map/std::map::const_reference
- map/std::map::const_reverse_iterator
- map/std::map::difference_type
- map/std::map::iterator
- map/std::map::key_compare
- map/std::map::key_type
- map/std::map::mapped_type
- map/std::map::pointer
- map/std::map::reference
- map/std::map::reverse_iterator
- map/std::map::size_type
- map/std::map::value_type
- map/std::map::at
- map/std::map::begin
- map/std::map::cbegin
- map/std::map::cend
- map/std::map::clear
- map/std::map::count
- map/std::map::crbegin
- map/std::map::crend
- map/std::map::emplace
- map/std::map::emplace_hint
- map/std::map::empty
- map/std::map::end
- map/std::map::equal_range
- map/std::map::erase
- map/std::map::find
- map/std::map::get_allocator
- map/std::map::insert
- map/std::map::key_comp
- map/std::map::lower_bound
- map/std::map::max_size
- map/std::map::rbegin
- map/std::map::rend
- map/std::map::size
- map/std::map::swap
- map/std::map::upper_bound
- map/std::map::value_comp
helpviewer_keywords:
- std::map [C++]
- std::map [C++], allocator_type
- std::map [C++], const_iterator
- std::map [C++], const_pointer
- std::map [C++], const_reference
- std::map [C++], const_reverse_iterator
- std::map [C++], difference_type
- std::map [C++], iterator
- std::map [C++], key_compare
- std::map [C++], key_type
- std::map [C++], mapped_type
- std::map [C++], pointer
- std::map [C++], reference
- std::map [C++], reverse_iterator
- std::map [C++], size_type
- std::map [C++], value_type
- std::map [C++], at
- std::map [C++], begin
- std::map [C++], cbegin
- std::map [C++], cend
- std::map [C++], clear
- std::map [C++], count
- std::map [C++], crbegin
- std::map [C++], crend
- std::map [C++], emplace
- std::map [C++], emplace_hint
- std::map [C++], empty
- std::map [C++], end
- std::map [C++], equal_range
- std::map [C++], erase
- std::map [C++], find
- std::map [C++], get_allocator
- std::map [C++], insert
- std::map [C++], key_comp
- std::map [C++], lower_bound
- std::map [C++], max_size
- std::map [C++], rbegin
- std::map [C++], rend
- std::map [C++], size
- std::map [C++], swap
- std::map [C++], upper_bound
- std::map [C++], value_comp
ms.assetid: 7876f4c9-ebb4-4878-af1e-09364c43af0a
ms.openlocfilehash: 22bb9d94b4c420419941a5bb7af24009b91f0a54
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68456308"
---
# <a name="map-class"></a>map — Klasa

Używany do przechowywania i pobierania danych z kolekcji, w której każdy element jest parą, która ma zarówno wartość danych, jak i klucz sortowania. Wartość klucza jest unikatowa i jest używana do automatycznego sortowania danych.

Można bezpośrednio zmienić wartość elementu w mapie. Wartość klucza jest stała i nie można jej zmienić. Zamiast tego, wartości kluczy skojarzone ze starymi elementami muszą zostać usunięte, a nowe wartości klucza muszą zostać wstawione dla nowych elementów.

## <a name="syntax"></a>Składnia

```cpp
template <class Key,
    class Type,
    class Traits = less<Key>,
    class Allocator=allocator<pair <const Key, Type>>>
class map;
```

### <a name="parameters"></a>Parametry

*Głównych*\
Typ danych klucza, który ma być przechowywany w mapie.

*Wprowadź*\
Typ danych elementu, który ma być przechowywany w mapie.

*Cech*\
Typ, który dostarcza obiekt funkcji, która może porównać dwie wartości elementów jako klucze sortowania, aby określić ich względną kolejność w mapie. Ten argument jest opcjonalny, a predykat `less<Key>` binarny jest wartością domyślną.

W języku C++ 14 można włączyć wyszukiwanie heterogeniczne, określając predykat > std:: less <, który nie ma parametrów typu. Aby uzyskać więcej informacji, zobacz [Wyszukiwanie heterogeniczne w kontenerach asocjacyjnych](../standard-library/stl-containers.md#sequence_containers)

*Alokator*\
Typ reprezentujący przechowywany obiekt alokatora, który hermetyzuje szczegóły dotyczące alokacji mapy i dezalokacji pamięci. Ten argument jest opcjonalny, a wartość domyślna to `allocator<pair<const Key, Type> >`.

## <a name="remarks"></a>Uwagi

Klasa C++ standardowej mapy biblioteki to:

- Kontenerem o zmiennym rozmiarze, który skutecznie pobiera wartości elementów na podstawie skojarzonych wartości klucza.

- Odwracalny, ponieważ zapewnia dwukierunkowe iteratory do dostępu do jego elementów.

- Posortowana, ponieważ jej elementy są uporządkowane według wartości kluczy zgodnie z określoną funkcją porównywania.

- Unikatowy. ponieważ każdy z jego elementów musi mieć unikatowy klucz.

- Kontenerem skojarzonych par, ponieważ jej wartości danych elementu różnią się od wartości klucza.

- Klasą szablonu, ponieważ funkcjonalność, którą zapewnia, jest generyczna i dlatego niezależna od typu elementu lub klucza. Typy danych, których można użyć dla elementów i kluczy, są określane jako parametry w szablonie klasy wraz z funkcją porównywania oraz alokatorem.

Iterator dostarczony przez klasę mapy jest iteratorem dwukierunkowym, ale funkcje składowe klasy [INSERT](#insert) i [map](#map) mają wersje przyjmujące jako parametry szablonu słabszy iterator danych wejściowych, którego wymagania dotyczące funkcjonalności są mniejsze niż te gwarantowane przez klasę iteratorów dwukierunkowych. Pojęcia innych iteratorów są powiązane przez udoskonalenia w ich funkcjonalnościach. Każde pojęcie iteratora ma swój własny zestaw wymagań, a algorytmy, które z nim pracują, muszą być ograniczone przez te wymagania. Iterator danych wejściowych może zostać wyłuskany, aby odwołać się do jakiegoś obiektu, a także może być zwiększony do następnego iteratora w sekwencji.

Zalecamy, aby wybrać typ kontenera na podstawie rodzaju wyszukiwania i wstawiania, którego wymaga aplikacja. Kontenery asocjacyjne są zoptymalizowane dla operacji wyszukiwania, wstawiania i usuwania. Funkcje elementów członkowskich, które jawnie obsługują te operacje, wykonują je w czasie najgorszego przypadku, który jest proporcjonalny do logarytmu liczby elementów w kontenerze. Wstawianie elementów nie unieważnia iteratorów, a usuwanie elementów unieważnia tylko te iteratory, które w szczególności wskazywały na usunięte elementy.

Zalecamy, aby kontener asocjacyjny z wyboru był mapą, gdy warunki, które kojarzą wartości z kluczami, są spełnione przez aplikację. Model dla tego rodzaju struktury jest uporządkowaną listą jednoznacznie występujących słów kluczowych mających skojarzone wartości ciągów, które zapewniają definicje. Jeśli wyraz ma więcej niż jedną poprawną definicję, tak że klucz nie jest unikatowy, wówczas mapa wielokrotnego dopasowania byłaby kontenerem z wyboru. Jeśli jest przechowywana tylko lista wyrazów, zestaw będzie odpowiednim kontenerem. Jeśli jest dozwolonych wiele wystąpień słów, to zestaw wielokrotny będzie odpowiedni.

Mapa Porządkuje elementy, które kontroluje, przez wywołanie przechowywanego obiektu funkcji typu [key_compare](#key_compare). Ten przechowywany obiekt jest funkcją porównywania, do której uzyskuje się dostęp poprzez wywołanie metody [key_comp](#key_comp) . Ogólnie rzecz biorąc, dowolne dwa dane elementy są porównywane, aby określić, czy jeden z nich jest mniejszy od drugiego lub czy są równoważne. W miarę porównywania wszystkich elementów, tworzona jest uporządkowana sekwencja nierównoważnych elementów.

> [!NOTE]
> Funkcja porównywania jest predykatem binarnym, który wymusza ścisłe słabe porządkowanie w standardowym sensie matematycznym. Predykat binarny f (x, y) jest obiektem funkcji, który ma dwa obiekty argumentu x i y oraz wartość zwracaną **true** lub **false**. Kolejność nałożona na zestaw jest ścisłym nieprawidłowym porządkowaniem, jeśli Predykat binarny jest niezwrotny, niesymetryczny i przechodni oraz jeśli równoważność jest przechodnia, gdzie dwa obiekty x i y są zdefiniowane jako równoważne, gdy zarówno f (x, y), jak i f (y, x) mają **wartość false**. Jeśli silniejszy warunek równości pomiędzy kluczami zastąpi ten równoważności, to porządkowanie będzie całkowite (w sensie, że wszystkie elementy są uporządkowane względem siebie), a dopasowane klucze będą od siebie nieodróżnialne.
>
> W języku c++ 14 można włączyć wyszukiwanie heterogeniczne, określając `std::less<>` predykat `std::greater<>` or, który nie ma parametrów typu. Aby uzyskać więcej informacji, zobacz [Wyszukiwanie heterogeniczne w kontenerach asocjacyjnych](../standard-library/stl-containers.md#sequence_containers)

## <a name="members"></a>Elementy członkowskie

### <a name="constructors"></a>Konstruktorów

|||
|-|-|
|[zmapować](#map)|Tworzy listę o określonym rozmiarze lub z elementami określonej wartości lub z konkretną `allocator` lub jako kopią innej mapy.|

### <a name="typedefs"></a>Typedefs

|||
|-|-|
|[allocator_type](#allocator_type)|Element typedef dla `allocator` klasy obiektu mapy.|
|[const_iterator](#const_iterator)|Element typedef dla iteratora dwukierunkowego, który może odczytać element **const** w mapie.|
|[const_pointer](#const_pointer)|Element typedef dla wskaźnika do elementu **const** w mapie.|
|[const_reference](#const_reference)|Element typedef dla odwołania do elementu **const** przechowywanego w mapie na potrzeby odczytywania i wykonywania operacji **const** .|
|[const_reverse_iterator](#const_reverse_iterator)|Typ, który dostarcza iterator dwukierunkowy, który może odczytać dowolny element **const** w mapie.|
|[difference_type](#difference_type)|Element typedef całkowitoliczbowy ze znakiem dla liczby elementów mapy w zakresie między elementami wskazywanymi przez iteratory.|
|[iterator](#iterator)|Element typedef dla iteratora dwukierunkowego, który może odczytać lub zmodyfikować dowolny element w mapie.|
|[key_compare](#key_compare)|Element typedef dla obiektu funkcji, która może porównać dwa klucze sortowania, aby określić względną kolejność dwóch elementów w mapie.|
|[key_type](#key_type)|Element typedef dla klucza sortowania przechowywanego w każdym elemencie mapy.|
|[mapped_type](#mapped_type)|Element typedef dla danych przechowywanych w każdym elemencie mapy.|
|[pointer](#pointer)|Element typedef dla wskaźnika do elementu **const** w mapie.|
|[Odwołanie](#reference)|Element typedef dla odwołania do elementu przechowywanego w mapie.|
|[reverse_iterator](#reverse_iterator)|Element typedef dla iteratora dwukierunkowego, który może odczytać lub zmodyfikować element w odwróconej mapie.|
|[size_type](#size_type)|Całkowitoliczbowy element typedef bez znaku określający liczbę elementów w mapie.|
|[value_type](#value_type)|Element typedef dla typu obiektu przechowywanego jako element w mapie.|

### <a name="member-functions"></a>Funkcje członkowskie

|Funkcja członkowska|Opis|
|-|-|
|[at](#at)|Wyszukuje element z określoną wartością klucza.|
|[begin](#begin)|Zwraca iterator, który wskazuje na pierwszy element w mapie.|
|[cbegin](#cbegin)|Zwraca iterator const, który wskazuje na pierwszy element w mapie.|
|[cend](#cend)|Zwraca wartość const iteratora poza końcem.|
|[Wyczyść](#clear)|Usuwa wszystkie elementy mapy.|
|[liczbą](#count)|Zwraca liczbę elementów w mapie, których klucz pasuje do klucza określonego w parametrze.|
|[crbegin](#crbegin)|Zwraca iterator const, który wskazuje na pierwszy element w odwróconej mapie.|
|[crend](#crend)|Zwraca iterator const, który wskazuje na lokalizację po ostatnim elemencie w odwróconej mapie.|
|[emplace](#emplace)|Wstawia element skonstruowany w miejscu do mapy.|
|[emplace_hint](#emplace_hint)|Wstawia element skonstruowany w miejscu do mapy, ze wskazówką położenia.|
|[empty](#empty)|Zwraca **wartość true** , jeśli mapa jest pusta.|
|[punktów](#end)|Zwraca iterator poza końcem.|
|[equal_range](#equal_range)|Zwraca parę iteratorów. Pierwszy iterator w parze wskazuje na pierwszy element w a `map` z kluczem, który jest większy niż określony klucz. Drugi iterator w parze wskazuje na pierwszy element w `map` z kluczem, który jest równy lub większy niż klucz.|
|[Wyłączanie](#erase)|Usuwa element lub zakres elementów w mapie z określonych pozycji.|
|[wyświetlić](#find)|Zwraca iterator, który wskazuje na pierwszą lokalizację elementu w mapie, który ma klucz równy określonemu kluczowi.|
|[get_allocator](#get_allocator)|Zwraca kopię `allocator` obiektu, który jest używany do konstruowania mapy.|
|[wstawienia](#insert)|Wstawia element lub zakres elementów do mapy na określonej pozycji.|
|[key_comp](#key_comp)|Zwraca kopię obiektu porównania użytego do uporządkowania kluczy w mapie.|
|[lower_bound](#lower_bound)|Zwraca iterator do pierwszego elementu w mapie, którego wartość klucza jest równa lub większa od określonego klucza.|
|[max_size](#max_size)|Zwraca maksymalną długość mapy.|
|[rbegin](#rbegin)|Zwraca iterator, który wskazuje na pierwszy element w odwróconej mapie.|
|[rend](#rend)|Zwraca iterator, który wskazuje na lokalizację po ostatnim elemencie w odwróconej mapie.|
|[zmienia](#size)|Zwraca liczbę elementów w mapie.|
|[swap](#swap)|Zamienia elementy z dwóch map.|
|[upper_bound](#upper_bound)|Zwraca iterator do pierwszego elementu w mapie, którego wartość klucza jest większa od określonego klucza.|
|[value_comp](#value_comp)|Pobiera kopię obiektu porównania, użytego do uporządkowania wartości elementów w mapie.|

### <a name="operators"></a>Operatory

|||
|-|-|
|[operator&#91;&#93;](#op_at)|Wstawia element do mapy z określoną wartością klucza.|
|[operator=](#op_eq)|Zastępuje elementy mapy kopią innej mapy.|

## <a name="allocator_type"></a>allocator_type

Typ, który reprezentuje klasę alokatora dla obiektu mapy.

```cpp
typedef Allocator allocator_type;
```

### <a name="example"></a>Przykład

Zobacz przykład dla [get_allocator](#get_allocator) , aby zapoznać się z `allocator_type`przykładem, który używa.

## <a name="at"></a>w

Wyszukuje element z określoną wartością klucza.

```cpp
Type& at(const Key& key);

const Type& at(const Key& key) const;
```

### <a name="parameters"></a>Parametry

klucz * \
Wartość klucza do wyszukania.

### <a name="return-value"></a>Wartość zwracana

Odwołanie do wartości danych znalezionego elementu.

### <a name="remarks"></a>Uwagi

Jeśli wartość klucza argumentu nie zostanie znaleziona, funkcja zgłasza obiekt klasy [out_of_range](../standard-library/out-of-range-class.md).

### <a name="example"></a>Przykład

```cpp
// map_at.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

typedef std::map<char, int> Mymap;
int main()
    {
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

// find and show elements
    std::cout << "c1.at('a') == " << c1.at('a') << std::endl;
    std::cout << "c1.at('b') == " << c1.at('b') << std::endl;
    std::cout << "c1.at('c') == " << c1.at('c') << std::endl;

    return (0);
    }
```

## <a name="begin"></a>zaczną

Zwraca iterator odnoszący się do pierwszego elementu na mapie.

```cpp
const_iterator begin() const;

iterator begin();
```

### <a name="return-value"></a>Wartość zwracana

Iterator dwukierunkowy odnoszący się do pierwszego elementu w mapie lub lokalizacji, która pomyślnie ma pustą mapę.

### <a name="example"></a>Przykład

```cpp
// map_begin.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   map <int, int> m1;

   map <int, int> :: iterator m1_Iter;
   map <int, int> :: const_iterator m1_cIter;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 0, 0 ) );
   m1.insert ( Int_Pair ( 1, 1 ) );
   m1.insert ( Int_Pair ( 2, 4 ) );

   m1_cIter = m1.begin ( );
   cout << "The first element of m1 is " << m1_cIter -> first << endl;

   m1_Iter = m1.begin ( );
   m1.erase ( m1_Iter );

   // The following 2 lines would err because the iterator is const
   // m1_cIter = m1.begin ( );
   // m1.erase ( m1_cIter );

   m1_cIter = m1.begin( );
   cout << "The first element of m1 is now " << m1_cIter -> first << endl;
}
```

```Output
The first element of m1 is 0
The first element of m1 is now 1
```

## <a name="cbegin"></a>cbegin

Zwraca iterator **const** , który odnosi się do lokalizacji jedynie poza ostatnim elementem w zakresie.

```cpp
const_iterator cbegin() const;
```

### <a name="return-value"></a>Wartość zwracana

Stały **iterator dwukierunkowy** odnoszący się do pierwszego elementu w zakresie lub lokalizację tuż poza końcem pustego zakresu (dla pustego zakresu `cbegin() == cend()`).

### <a name="remarks"></a>Uwagi

Z wartością `cbegin`zwracaną nie można modyfikować elementów w zakresie.

Można użyć tej funkcji elementu członkowskiego zamiast `begin()` funkcji składowej, aby zagwarantować, że wartość zwracana to. `const_iterator` Zwykle jest używany w połączeniu z słowem kluczowym odejmowania [autotype,](../cpp/auto-cpp.md) jak pokazano w poniższym przykładzie. W tym przykładzie Rozważmy `Container` , że jest to modyfikowalny kontener dowolnego rodzaju, który obsługuje `begin()` i `cbegin()`.

```cpp
auto i1 = Container.begin();
// i1 is Container<T>::iterator
auto i2 = Container.cbegin();

// i2 is Container<T>::const_iterator
```

## <a name="cend"></a>cend

Zwraca iterator **const** , który odnosi się do lokalizacji jedynie poza ostatnim elementem w zakresie.

```cpp
const_iterator cend() const;
```

### <a name="return-value"></a>Wartość zwracana

Kompletny Iterator dostępu **dwukierunkowego** , który wskazuje tuż poza końcem zakresu.

### <a name="remarks"></a>Uwagi

`cend`służy do sprawdzania, czy iterator przeszedł koniec zakresu.

Można użyć tej funkcji elementu członkowskiego zamiast `end()` funkcji składowej, aby zagwarantować, że wartość zwracana to. `const_iterator` Zwykle jest używany w połączeniu z słowem kluczowym odejmowania [autotype,](../cpp/auto-cpp.md) jak pokazano w poniższym przykładzie. W tym przykładzie Rozważmy `Container` , że jest to modyfikowalny kontener dowolnego rodzaju, który obsługuje `end()` i `cend()`.

```cpp
auto i1 = Container.end();
// i1 is Container<T>::iterator
auto i2 = Container.cend();

// i2 is Container<T>::const_iterator
```

Nie można usunąć odwołania `cend` do wartości zwracanej przez.

## <a name="clear"></a>Wyczyść

Usuwa wszystkie elementy mapy.

```cpp
void clear();
```

### <a name="example"></a>Przykład

Poniższy przykład demonstruje użycie funkcji map:: Clear member.

```cpp
// map_clear.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main()
{
    using namespace std;
    map<int, int> m1;
    map<int, int>::size_type i;
    typedef pair<int, int> Int_Pair;

    m1.insert(Int_Pair(1, 1));
    m1.insert(Int_Pair(2, 4));

    i = m1.size();
    cout << "The size of the map is initially "
         << i << "." << endl;

    m1.clear();
    i = m1.size();
    cout << "The size of the map after clearing is "
         << i << "." << endl;
}
```

```Output
The size of the map is initially 2.
The size of the map after clearing is 0.
```

## <a name="const_iterator"></a>const_iterator

Typ, który dostarcza iterator dwukierunkowy, który może odczytać element **const** w mapie.

```cpp
typedef implementation-defined const_iterator;
```

### <a name="remarks"></a>Uwagi

Typ `const_iterator` nie może być używany do modyfikacji wartości elementu.

[](#value_type) `pair` \<  Zdefiniowane przez mapę wskazuje elementy, które są obiektami value_type, które są typu constKey, typ >, którego pierwszy element członkowski jest kluczem do elementu, a drugi element członkowski jest mapowany `const_iterator` Podstawa wymiarowa elementu.

Aby usunąć odwołanie `const_iterator` `cIter` do elementu na mapie, użyj `->` operatora.

Aby uzyskać dostęp do wartości klucza dla elementu, użyj `cIter`\*  ->  **pierwszej**, który jest odpowiednikiem ( `cIter`). **najpierw**.

Aby uzyskać dostęp do wartości mapowanej podstawy dla `cIter`elementu, użyj\*  ->  **sekundy**, który jest odpowiednikiem ( `cIter`). **sekunda**.

### <a name="example"></a>Przykład

Zobacz przykład [rozpoczęcia](#begin) dla przykładu, który używa `const_iterator`.

## <a name="const_pointer"></a>const_pointer

Typ, który dostarcza wskaźnik do elementu **const** w mapie.

```cpp
typedef typename allocator_type::const_pointer const_pointer;
```

### <a name="remarks"></a>Uwagi

Typ `const_pointer` nie może być używany do modyfikacji wartości elementu.

W większości przypadków [iterator](#iterator) powinien być używany do uzyskiwania dostępu do elementów w obiekcie mapy.

## <a name="const_reference"></a>const_reference

Typ, który dostarcza odwołanie do elementu **const** przechowywanego w mapie na potrzeby odczytywania i wykonywania operacji **const** .

```cpp
typedef typename allocator_type::const_reference const_reference;
```

### <a name="example"></a>Przykład

```cpp
// map_const_ref.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   map <int, int> m1;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 1, 10 ) );
   m1.insert ( Int_Pair ( 2, 20 ) );

   // Declare and initialize a const_reference &Ref1
   // to the key of the first element
   const int &Ref1 = ( m1.begin( ) -> first );

   // The following line would cause an error as the
   // non-const_reference cannot be used to access the key
   // int &Ref1 = ( m1.begin( ) -> first );

   cout << "The key of first element in the map is "
        << Ref1 << "." << endl;

   // Declare and initialize a reference &Ref2
   // to the data value of the first element
   int &Ref2 = ( m1.begin( ) -> second );

   cout << "The data value of first element in the map is "
        << Ref2 << "." << endl;
}
```

```Output
The key of first element in the map is 1.
The data value of first element in the map is 10.
```

## <a name="const_reverse_iterator"></a>const_reverse_iterator

Typ, który dostarcza iterator dwukierunkowy, który może odczytać dowolny element **const** w mapie.

```cpp
typedef std::reverse_iterator<const_iterator> const_reverse_iterator;
```

### <a name="remarks"></a>Uwagi

Typ `const_reverse_iterator` nie może zmodyfikować wartości elementu i służy do wykonywania iteracji mapy w odwrotnej postaci.

Zdefiniowane przez mapę wskazuje elementy, które są obiektami [value_type](#value_type), które są typu `pair<const Key, Type>`, którego pierwszy element członkowski jest kluczem do elementu, a drugi element członkowski jest zmapowaną podstawą zawartą w elemencie. `const_reverse_iterator`

Aby usunąć odwołanie `const_reverse_iterator crIter` do elementu na mapie, `->` Użyj operatora.

Aby uzyskać dostęp do wartości klucza dla elementu, użyj `crIter`\*  ->  **pierwszej**, który jest odpowiednikiem ( `crIter`). **najpierw**.

Aby uzyskać dostęp do wartości mapowanej podstawy dla `crIter`elementu, użyj\*  ->  **sekundy**, który jest odpowiednikiem ( `crIter`). **najpierw**.

### <a name="example"></a>Przykład

Zapoznaj się z przykładem dla [rend](#rend) , aby zapoznać się z przykładem sposobu deklarowania i używania `const_reverse_iterator`.

## <a name="count"></a>liczbą

Zwraca liczbę elementów w mapie, których klucz pasuje do klucza określonego przez parametr.

```cpp
size_type count(const Key& key) const;
```

### <a name="parameters"></a>Parametry

*głównych*\
Wartość klucza elementów do dopasowania z mapy.

### <a name="return-value"></a>Wartość zwracana

1, jeśli mapa zawiera element, którego klucz sortowania jest zgodny z kluczem parametru; 0, jeśli mapa nie zawiera elementu z pasującym kluczem.

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca liczbę elementów *x* z zakresu

\[lower_bound (*Key*), upper_bound (*klucz*))

jest to wartość 0 lub 1 w przypadku mapy, która jest unikatowym kontenerem asocjacyjnym.

### <a name="example"></a>Przykład

Poniższy przykład demonstruje użycie funkcji map:: Count.

```cpp
// map_count.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main()
{
    using namespace std;
    map<int, int> m1;
    map<int, int>::size_type i;
    typedef pair<int, int> Int_Pair;

    m1.insert(Int_Pair(1, 1));
    m1.insert(Int_Pair(2, 1));
    m1.insert(Int_Pair(1, 4));
    m1.insert(Int_Pair(2, 1));

    // Keys must be unique in map, so duplicates are ignored
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
The number of elements in m1 with a sort key of 1 is: 1.
The number of elements in m1 with a sort key of 2 is: 1.
The number of elements in m1 with a sort key of 3 is: 0.
```

## <a name="crbegin"></a>crbegin —

Zwraca iterator const odnoszący się do pierwszego elementu w odwróconej mapie.

```cpp
const_reverse_iterator crbegin() const;
```

### <a name="return-value"></a>Wartość zwracana

Stałe odwrotne Iteratory, odnoszące się do pierwszego elementu w odwróconej [mapie](../standard-library/map-class.md) lub adresowania ostatniego elementu w odwrót `map`.

### <a name="remarks"></a>Uwagi

`crbegin`jest używany z odwróconą `map` opcją [BEGIN](#begin) AS `map`jest używana z.

Z wartością `crbegin`zwracaną `map` , nie można zmodyfikować obiektu

`crbegin`może służyć do iteracji `map` w tył.

### <a name="example"></a>Przykład

```cpp
// map_crbegin.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   map <int, int> m1;

   map <int, int> :: const_reverse_iterator m1_crIter;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 1, 10 ) );
   m1.insert ( Int_Pair ( 2, 20 ) );
   m1.insert ( Int_Pair ( 3, 30 ) );

   m1_crIter = m1.crbegin( );
   cout << "The first element of the reversed map m1 is "
        << m1_crIter -> first << "." << endl;
}
```

```Output
The first element of the reversed map m1 is 3.
```

## <a name="crend"></a>crend

Zwraca iterator const, który odnosi się do lokalizacji po ostatnim elemencie w odwróconej mapie.

```cpp
const_reverse_iterator crend() const;
```

### <a name="return-value"></a>Wartość zwracana

Niepowodzenie odwrotnego iteratora dwukierunkowego, który odnosi się do lokalizacji po ostatnim elemencie w odwróconej [mapie](../standard-library/map-class.md) (lokalizacja, która poprzedza pierwszy element w odwrót `map`).

### <a name="remarks"></a>Uwagi

`crend`jest używany z odwróconą mapą, tak jak [koniec](#end) jest używany z `map`.

Z wartością `crend`zwracaną `map` , nie można zmodyfikować obiektu.

`crend`można go użyć do przetestowania, czy iterator odwrotny osiągnął koniec jego `map`.

Nie można usunąć odwołania `crend` do wartości zwracanej przez.

### <a name="example"></a>Przykład

```cpp
// map_crend.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   map <int, int> m1;

   map <int, int> :: const_reverse_iterator m1_crIter;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 1, 10 ) );
   m1.insert ( Int_Pair ( 2, 20 ) );
   m1.insert ( Int_Pair ( 3, 30 ) );

   m1_crIter = m1.crend( );
   m1_crIter--;
   cout << "The last element of the reversed map m1 is "
        << m1_crIter -> first << "." << endl;
}
```

```Output
The last element of the reversed map m1 is 1.
```

## <a name="difference_type"></a>difference_type

Typ liczby całkowitej ze znakiem, który może służyć do reprezentowania liczby elementów mapy w zakresie między elementami wskazywanymi przez Iteratory.

```cpp
typedef allocator_type::difference_type difference_type;
```

### <a name="remarks"></a>Uwagi

`difference_type` Jest typem zwracanym podczas odejmowania lub zwiększania przez Iteratory kontenera. `first` `first` `last`  Jest zazwyczaj używany do reprezentowania liczby elementów w zakresie [First, Last) między iteratorami i, zawiera element wskazywany przez i zakres elementów do, ale nie `difference_type` dołączenie elementu wskazywanego przez `last`.

Należy zauważyć, `difference_type` że chociaż jest dostępny dla wszystkich iteratorów, które spełniają wymagania iteratora danych wejściowych, który obejmuje klasę iteratorów dwukierunkowych obsługiwanych przez kontenery odwracalne, takie jak zestaw, odejmowanie między iteratorami jest tylko obsługiwane przez Iteratory dostępu losowego zapewniane przez kontener dostępu losowego, taki jak wektor.

### <a name="example"></a>Przykład

```cpp
// map_diff_type.cpp
// compile with: /EHsc
#include <iostream>
#include <map>
#include <algorithm>

int main( )
{
   using namespace std;
   map <int, int> m1;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 2, 20 ) );
   m1.insert ( Int_Pair ( 1, 10 ) );
   m1.insert ( Int_Pair ( 3, 20 ) );
   m1.insert ( Int_Pair ( 2, 30 ) );

   map <int, int>::iterator m1_Iter, m1_bIter, m1_eIter;
   m1_bIter = m1.begin( );
   m1_eIter = m1.end( );

   // Count the number of elements in a map
   map <int, int>::difference_type  df_count = 1;
   m1_Iter = m1.begin( );
   while ( m1_Iter != m1_eIter)
   {
      df_count++;
      m1_Iter++;
   }

   cout << "The number of elements in the map m1 is: "
        << df_count << "." << endl;
}
```

```Output
The number of elements in the map m1 is: 4.
```

## <a name="emplace"></a>emplace

Wstawia element skonstruowany w miejscu (nie są wykonywane żadne operacje kopiowania ani przenoszenia) do mapy.

```cpp
template <class... Args>
pair<iterator, bool>
emplace(
    Args&&... args);
```

### <a name="parameters"></a>Parametry

*argumentów*\
Argumenty przekazywane do konstruowania elementu, który ma zostać wstawiony do mapy, chyba że zawiera już element o równoważnej kolejności.

### <a name="return-value"></a>Wartość zwracana

[Para](../standard-library/pair-structure.md) , której składnik **bool** ma wartość true, jeśli wykonano wstawienie, i wartość false, jeśli mapa zawiera już element równoważnej wartości w kolejności. Składnik iteratora pary zwracanych wartości wskazuje nowo wstawiony element, jeśli składnik **bool** ma wartość true lub do istniejącego elementu, jeśli składnik **bool** ma wartość false.

Aby `pair` uzyskać dostęp do składnika `pr`iteratora, użyj `pr.first`;, aby usunąć odwołanie do niego `*pr.first`, użyj. Aby uzyskać dostęp do składnika **bool** , `pr.second`Użyj. Aby zapoznać się z przykładem, zobacz przykładowy kod w dalszej części tego artykułu.

### <a name="remarks"></a>Uwagi

Ta funkcja nie unieważnia iteratorów ani odwołań.

Podczas umieszczanie, jeśli wystąpi wyjątek, stan kontenera nie jest modyfikowany.

[Value_type](#value_type) elementu to para, dzięki czemu wartość elementu będzie to uporządkowana para z pierwszym składnikiem równym wartości klucza i drugi składnik równy wartości danych elementu.

### <a name="example"></a>Przykład

```cpp
// map_emplace.cpp
// compile with: /EHsc
#include <map>
#include <string>
#include <iostream>

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
    map<int, string> m1;

    auto ret = m1.emplace(10, "ten");

    if (!ret.second){
        auto pr = *ret.first;
        cout << "Emplace failed, element with key 10 already exists."
            << endl << "  The existing element is (" << pr.first << ", " << pr.second << ")"
            << endl;
        cout << "map not modified" << endl;
    }
    else{
        cout << "map modified, now contains ";
        print(m1);
    }
    cout << endl;

    ret = m1.emplace(10, "one zero");

    if (!ret.second){
        auto pr = *ret.first;
        cout << "Emplace failed, element with key 10 already exists."
            << endl << "  The existing element is (" << pr.first << ", " << pr.second << ")"
            << endl;
    }
    else{
        cout << "map modified, now contains ";
        print(m1);
    }
    cout << endl;
}
```

## <a name="emplace_hint"></a>emplace_hint

Wstawia element skonstruowany w miejscu (nie są wykonywane żadne operacje kopiowania ani przenoszenia) z wskazówką dotyczącą położenia.

```cpp
template <class... Args>
iterator emplace_hint(
    const_iterator where,
    Args&&... args);
```

### <a name="parameters"></a>Parametry

*argumentów*\
Argumenty przekazywane do konstruowania elementu, który ma zostać wstawiony do mapy, chyba że mapa już zawiera ten element lub, bardziej ogólnie, chyba że zawiera już element, którego klucz jest równoważny uporządkowanie.

*miejscu*\
Miejsce, w którym rozpocznie się wyszukiwanie poprawnego punktu wstawiania. (Jeśli ten punkt bezpośrednio poprzedza miejsce, w *którym*może następować amortyzowany stały czas zamiast czasu logarytmu).

### <a name="return-value"></a>Wartość zwracana

Iterator do nowo wstawionego elementu.

Jeśli wstawianie nie powiodło się, ponieważ element już istnieje, zwraca iterator do istniejącego elementu z jego kluczem.

### <a name="remarks"></a>Uwagi

Ta funkcja nie unieważnia iteratorów ani odwołań.

Podczas umieszczanie, jeśli wystąpi wyjątek, stan kontenera nie jest modyfikowany.

[Value_type](#value_type) elementu to para, dzięki czemu wartość elementu będzie to uporządkowana para z pierwszym składnikiem równym wartości klucza i drugi składnik równy wartości danych elementu.

### <a name="example"></a>Przykład

```cpp
// map_emplace.cpp
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
    map<string, string> m1;

    // Emplace some test data
    m1.emplace("Anna", "Accounting");
    m1.emplace("Bob", "Accounting");
    m1.emplace("Carmine", "Engineering");

    cout << "map starting data: ";
    print(m1);
    cout << endl;

    // Emplace with hint
    // m1.end() should be the "next" element after this emplacement
    m1.emplace_hint(m1.end(), "Doug", "Engineering");

    cout << "map modified, now contains ";
    print(m1);
    cout << endl;
}
```

## <a name="empty"></a>ciągiem

Testuje, czy mapa jest pusta.

```cpp
bool empty() const;
```

### <a name="return-value"></a>Wartość zwracana

**ma wartość true** , jeśli mapa jest pusta; **wartość false** , jeśli mapa jest niepusta.

### <a name="example"></a>Przykład

```cpp
// map_empty.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   map <int, int> m1, m2;

   typedef pair <int, int> Int_Pair;
   m1.insert ( Int_Pair ( 1, 1 ) );

   if ( m1.empty( ) )
      cout << "The map m1 is empty." << endl;
   else
      cout << "The map m1 is not empty." << endl;

   if ( m2.empty( ) )
      cout << "The map m2 is empty." << endl;
   else
      cout << "The map m2 is not empty." << endl;
}
```

```Output
The map m1 is not empty.
The map m2 is empty.
```

## <a name="end"></a>punktów

Zwraca iterator poza końcem.

```cpp
const_iterator end() const;

iterator end();
```

### <a name="return-value"></a>Wartość zwracana

Iterator Past. Jeśli mapa jest pusta, a następnie `map::end() == map::begin()`.

### <a name="remarks"></a>Uwagi

`end`służy do sprawdzania, czy iterator przeszedł koniec jego mapy.

Nie można usunąć odwołania `end` do wartości zwracanej przez.

Aby uzyskać przykład kodu, zobacz [map:: find](#find).

## <a name="equal_range"></a>equal_range

Zwraca parę iteratorów reprezentujących [lower_bound](#lower_bound) klucza i [upper_bound](#upper_bound) klucza.

```cpp
pair <const_iterator, const_iterator> equal_range (const Key& key) const;

pair <iterator, iterator> equal_range (const Key& key);
```

### <a name="parameters"></a>Parametry

*głównych*\
Wartość klucza argumentu do porównania z kluczem sortowania elementu z przeszukiwanej mapy.

### <a name="return-value"></a>Wartość zwracana

Aby uzyskać dostęp do pierwszego iteratora pary `pr` zwracanej przez funkcję członkowską, `pr`Użyj. **najpierw**i aby usunąć odwołanie do dolnego powiązanego iteratora \*, `pr`Użyj (. **pierwszy**). Aby uzyskać dostęp do drugiego iteratora pary `pr` zwracanej przez funkcję członkowską, `pr`Użyj. **drugi**i aby usunąć odwołanie do górnego powiązanego iteratora \*, `pr`Użyj (. **sekundę**).

### <a name="example"></a>Przykład

```cpp
// map_equal_range.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   typedef map <int, int, less<int> > IntMap;
   IntMap m1;
   map <int, int> :: const_iterator m1_RcIter;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 1, 10 ) );
   m1.insert ( Int_Pair ( 2, 20 ) );
   m1.insert ( Int_Pair ( 3, 30 ) );

   pair <IntMap::const_iterator, IntMap::const_iterator> p1, p2;
   p1 = m1.equal_range( 2 );

   cout << "The lower bound of the element with "
        << "a key of 2 in the map m1 is: "
        << p1.first -> second << "." << endl;

   cout << "The upper bound of the element with "
        << "a key of 2 in the map m1 is: "
        << p1.second -> second << "." << endl;

   // Compare the upper_bound called directly
   m1_RcIter = m1.upper_bound( 2 );

   cout << "A direct call of upper_bound( 2 ) gives "
        << m1_RcIter -> second << "," << endl
        << "matching the 2nd element of the pair"
        << " returned by equal_range( 2 )." << endl;

   p2 = m1.equal_range( 4 );

   // If no match is found for the key,
   // both elements of the pair return end( )
   if ( ( p2.first == m1.end( ) ) && ( p2.second == m1.end( ) ) )
      cout << "The map m1 doesn't have an element "
           << "with a key less than 40." << endl;
   else
      cout << "The element of map m1 with a key >= 40 is: "
           << p2.first -> first << "." << endl;
}
```

```Output
The lower bound of the element with a key of 2 in the map m1 is: 20.
The upper bound of the element with a key of 2 in the map m1 is: 30.
A direct call of upper_bound( 2 ) gives 30,
matching the 2nd element of the pair returned by equal_range( 2 ).
The map m1 doesn't have an element with a key less than 40.
```

## <a name="erase"></a>Wyłączanie

Usuwa element lub zakres elementów w mapie z określonych pozycji lub usuwa elementy, które pasują do określonego klucza.

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

*Miejscu*\
Pozycja elementu, który ma zostać usunięty.

*Pierwszego*\
Pozycja pierwszego elementu, który ma zostać usunięty.

*Ostatniego*\
Umieść tuż poza ostatnim elementem, który ma zostać usunięty.

*Głównych*\
Wartość klucza elementów do usunięcia.

### <a name="return-value"></a>Wartość zwracana

W przypadku pierwszych dwóch funkcji składowych iterator dwukierunkowy, który wyznacza pierwszy element, który jest poza wszystkimi elementami usuniętymi lub element, który jest końcem mapy, jeśli taki element nie istnieje.

Dla trzeciej funkcji składowej zwraca liczbę elementów, które zostały usunięte z mapy.

### <a name="example"></a>Przykład

```cpp
// map_erase.cpp
// compile with: /EHsc
#include <map>
#include <string>
#include <iostream>
#include <iterator> // next() and prev() helper functions
#include <utility>  // make_pair()

using namespace std;

using mymap = map<int, string>;

void printmap(const mymap& m) {
    for (const auto& elem : m) {
        cout << " [" << elem.first << ", " << elem.second << "]";
    }
    cout << endl << "size() == " << m.size() << endl << endl;
}

int main()
{
    mymap m1;

    // Fill in some data to test with, one at a time
    m1.insert(make_pair(1, "A"));
    m1.insert(make_pair(2, "B"));
    m1.insert(make_pair(3, "C"));
    m1.insert(make_pair(4, "D"));
    m1.insert(make_pair(5, "E"));

    cout << "Starting data of map m1 is:" << endl;
    printmap(m1);
    // The 1st member function removes an element at a given position
    m1.erase(next(m1.begin()));
    cout << "After the 2nd element is deleted, the map m1 is:" << endl;
    printmap(m1);

    // Fill in some data to test with, one at a time, using an initializer list
    mymap m2
    {
        { 10, "Bob" },
        { 11, "Rob" },
        { 12, "Robert" },
        { 13, "Bert" },
        { 14, "Bobby" }
    };

    cout << "Starting data of map m2 is:" << endl;
    printmap(m2);
    // The 2nd member function removes elements
    // in the range [First, Last)
    m2.erase(next(m2.begin()), prev(m2.end()));
    cout << "After the middle elements are deleted, the map m2 is:" << endl;
    printmap(m2);

    mymap m3;

    // Fill in some data to test with, one at a time, using emplace
    m3.emplace(1, "red");
    m3.emplace(2, "yellow");
    m3.emplace(3, "blue");
    m3.emplace(4, "green");
    m3.emplace(5, "orange");
    m3.emplace(6, "purple");
    m3.emplace(7, "pink");

    cout << "Starting data of map m3 is:" << endl;
    printmap(m3);
    // The 3rd member function removes elements with a given Key
    mymap::size_type count = m3.erase(2);
    // The 3rd member function also returns the number of elements removed
    cout << "The number of elements removed from m3 is: " << count << "." << endl;
    cout << "After the element with a key of 2 is deleted, the map m3 is:" << endl;
    printmap(m3);
}
```

## <a name="find"></a>wyświetlić

Zwraca iterator odwołujący się do lokalizacji elementu w mapie, który ma klucz równoważny do określonego klucza.

```cpp
iterator find(const Key& key);

const_iterator find(const Key& key) const;
```

### <a name="parameters"></a>Parametry

*głównych*\
Wartość klucza do dopasowania przez klucz sortowania elementu z przeszukiwanej mapy.

### <a name="return-value"></a>Wartość zwracana

Iterator, który odwołuje się do lokalizacji elementu z określonym kluczem lub lokalizacji, w której znajduje się ostatni element w mapie (`map::end()`), jeśli nie znaleziono żadnego dopasowania dla klucza.

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca iterator, który odwołuje się do elementu w mapie, którego klucz sortowania jest równoważny z kluczem argumentu w predykacie binarnym, który wywołuje kolejność na podstawie mniejszej niż porównywalności relacji.

Jeśli wartość `find` zwracana jest przypisana `const_iterator`do, obiekt mapy nie może być modyfikowany. Jeśli wartość `find` zwracana jest przypisana `iterator`do, obiekt mapy można zmodyfikować

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
    map<int, string> m1({ { 40, "Zr" }, { 45, "Rh" } });
    cout << "The starting map m1 is (key, value):" << endl;
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

    cout << "The modified map m1 is (key, value):" << endl;
    print_collection(m1);
    cout << endl;
    findit(m1, 45);
    findit(m1, 6);
}
```

## <a name="get_allocator"></a>get_allocator

Zwraca kopię obiektu alokatora używanego do konstruowania mapy.

```cpp
allocator_type get_allocator() const;
```

### <a name="return-value"></a>Wartość zwracana

Alokator używany przez mapę.

### <a name="remarks"></a>Uwagi

Przypisania klasy map określają sposób zarządzania magazynem przez klasę. Domyślne przydzielenie klas kontenerów C++ biblioteki standardowej jest wystarczające dla większości potrzeb programistycznych. Pisanie i używanie własnej klasy alokatora jest zaawansowanym C++ tematem.

### <a name="example"></a>Przykład

```cpp
// map_get_allocator.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   map <int, int>::allocator_type m1_Alloc;
   map <int, int>::allocator_type m2_Alloc;
   map <int, double>::allocator_type m3_Alloc;
   map <int, int>::allocator_type m4_Alloc;

   // The following lines declare objects
   // that use the default allocator.
   map <int, int> m1;
   map <int, int, allocator<int> > m2;
   map <int, double, allocator<double> > m3;

   m1_Alloc = m1.get_allocator( );
   m2_Alloc = m2.get_allocator( );
   m3_Alloc = m3.get_allocator( );

   cout << "The number of integers that can be allocated\n"
        << "before free memory is exhausted: "
        << m2.max_size( ) << ".\n" << endl;

   cout << "The number of doubles that can be allocated\n"
        << "before free memory is exhausted: "
        << m3.max_size( ) <<  ".\n" << endl;

   // The following line creates a map m4
   // with the allocator of map m1.
   map <int, int> m4( less<int>( ), m1_Alloc );

   m4_Alloc = m4.get_allocator( );

   // Two allocators are interchangeable if
   // storage allocated from each can be
   // deallocated with the other
   if( m1_Alloc == m4_Alloc )
   {
      cout << "The allocators are interchangeable." << endl;
   }
   else
   {
      cout << "The allocators are not interchangeable." << endl;
   }
}
```

## <a name="insert"></a>wstawienia

Wstawia element lub zakres elementów do mapy.

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

*Użyte*\
Wartość elementu, który ma zostać wstawiony do mapy, chyba że zawiera już element, którego klucz jest uporządkowany równorzędnie.

*Miejscu*\
Miejsce, w którym rozpocznie się wyszukiwanie poprawnego punktu wstawiania. (Jeśli ten punkt bezpośrednio poprzedza miejsce, w *którym*może następować amortyzowany stały czas zamiast czasu logarytmu).

*ValTy*\
Parametr szablonu, który określa typ argumentu, który może być używany przez mapę do konstruowania elementu [value_type](#value_type), i idealny do przesyłania *dalej jako argument* .

*Pierwszego*\
Pozycja pierwszego elementu, który ma zostać skopiowany.

*Ostatniego*\
Pozycja tuż poza ostatnim elementem, który ma zostać skopiowany.

*InputIterator*\
Argument funkcji szablonu, który spełnia wymagania iteratora [danych wejściowych](../standard-library/input-iterator-tag-struct.md) , który wskazuje elementy typu, które mogą być używane do konstruowania obiektów [value_type](#value_type) .

*IList*\
[Initializer_list](../standard-library/initializer-list.md) , z którego mają zostać skopiowane elementy.

### <a name="return-value"></a>Wartość zwracana

Jednoelementowe funkcje składowe, (1) i (2) zwracają [parę](../standard-library/pair-structure.md) , których składnik **bool** ma wartość true, jeśli wykonano wstawienie, i wartość false, jeśli mapa już zawiera element, którego klucz ma odpowiednik wartości w kolejności. Składnik iteratora pary zwracanych wartości wskazuje nowo wstawiony element, jeśli składnik **bool** ma wartość true lub do istniejącego elementu, jeśli składnik **bool** ma wartość false.

Funkcje członkowskie jednoelementowe z wskazówką, (3) i (4) zwracają iterator, który wskazuje na miejsce, w którym nowy element został wstawiony do mapy lub, jeśli element z równoważnym kluczem już istnieje, do istniejącego elementu.

### <a name="remarks"></a>Uwagi

Ta funkcja nie unieważnia iteratorów, wskaźników ani odwołań.

Podczas wstawiania tylko jednego elementu, jeśli wystąpi wyjątek, stan kontenera nie jest modyfikowany. Podczas wstawiania wielu elementów, jeśli wyjątek jest zgłaszany, kontener pozostaje w nieokreślonym, ale prawidłowym stanie.

Aby `pair` uzyskać dostęp do składnika `pr` iteratora, który jest zwracany przez jednoelementowe funkcje członkowskie, użyj `pr.first`;, aby usunąć odwołanie do iteratora w zwróconej parze, użyj `*pr.first`, dając Ci element. Aby uzyskać dostęp do składnika **bool** , `pr.second`Użyj. Aby zapoznać się z przykładem, zobacz przykładowy kod w dalszej części tego artykułu.

[Value_type](#value_type) kontenera jest elementem TypeDef, który należy do kontenera, a dla mapy, `map<K, V>::value_type` to. `pair<const K, V>` Wartość elementu to uporządkowana para, w której pierwszy składnik jest równy wartości klucza, a drugi składnik jest równy wartości danych elementu.

Zakres funkcji członkowskiej (5) wstawia sekwencji wartości elementów do mapy odpowiadający każdemu elementowi dotyczy iterację w zakresie `[First, Last)`; w związku z tym `Last` nie Pobierz wstawione. Funkcja `end()` elementu członkowskiego kontenera odwołuje się do pozycji tuż po ostatnim elemencie w kontenerze — na przykład, instrukcja `m.insert(v.begin(), v.end());` próbuje wstawić wszystkie elementy `v` do `m`. Wstawiane są tylko elementy, które mają unikatowe wartości z zakresu; duplikaty zostały zignorowane. Aby sprawdzić, które elementy są odrzucane, użyj jednoelementowych `insert`wersji programu.

Funkcja członkowska listy inicjatorów (6) używa elementu [initializer_list](../standard-library/initializer-list.md) do kopiowania elementów do mapy.

Do wstawienia elementu skonstruowanego w miejscu — to znaczy, że nie są wykonywane żadne operacje kopiowania ani przenoszenia — zobacz [map:: emplace](#emplace) i [map:: emplace_hint](#emplace_hint).

### <a name="example"></a>Przykład

```cpp
// map_insert.cpp
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
    map<int, int> m1;
    // call insert(const value_type&) version
    m1.insert({ 1, 10 });
    // call insert(ValTy&&) version
    m1.insert(make_pair(2, 20));

    cout << "The original key and mapped values of m1 are:" << endl;
    print(m1);

    // intentionally attempt a duplicate, single element
    auto ret = m1.insert(make_pair(1, 111));
    if (!ret.second){
        auto pr = *ret.first;
        cout << "Insert failed, element with key value 1 already exists."
            << endl << "  The existing element is (" << pr.first << ", " << pr.second << ")"
            << endl;
    }
    else{
        cout << "The modified key and mapped values of m1 are:" << endl;
        print(m1);
    }
    cout << endl;

    // single element, with hint
    m1.insert(m1.end(), make_pair(3, 30));
    cout << "The modified key and mapped values of m1 are:" << endl;
    print(m1);
    cout << endl;

    // The templatized version inserting a jumbled range
    map<int, int> m2;
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
    map<int, string>  m3;
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

    map<int, int> m4;
    // Insert the elements from an initializer_list
    m4.insert({ { 4, 44 }, { 2, 22 }, { 3, 33 }, { 1, 11 }, { 5, 55 } });
    cout << "After initializer_list insertion, m4 contains:" << endl;
    print(m4);
    cout << endl;
}
```

## <a name="iterator"></a>Iterator

Typ, który dostarcza iterator dwukierunkowy, który może odczytać lub zmodyfikować dowolny element na mapie.

```cpp
typedef implementation-defined iterator;
```

### <a name="remarks"></a>Uwagi

Iterator definiowany przez punkty mapy wskazuje elementy, które są obiektami [value_type](#value_type), które są typu `pair<const Key, Type>`, którego pierwszy element członkowski jest kluczem do elementu, a drugi element członkowski jest zmapowaną podstawą zawartą w elemencie.

Aby usunąć odwołanie do iteratora *ITER* wskazujący element na mapie, użyj `->` operatora.

Aby uzyskać dostęp do wartości klucza dla elementu, użyj `Iter->first`, który jest `(*Iter).first`odpowiednikiem. Aby uzyskać dostęp do wartości mapowanej podstawy dla elementu, użyj `Iter->second`, który jest `(*Iter).second`odpowiednikiem.

### <a name="example"></a>Przykład

Zobacz przykład rozpoczęcia, aby zapoznać [się](#begin) z przykładem sposobu deklarowania `iterator`i używania.

## <a name="key_comp"></a>key_comp

Pobiera kopię obiektu porównania użytego do uporządkowania kluczy w mapie.

```cpp
key_compare key_comp() const;
```

### <a name="return-value"></a>Wartość zwracana

Zwraca obiekt funkcji, którego mapa używa do uporządkowania jej elementów.

### <a name="remarks"></a>Uwagi

Przechowywany obiekt definiuje funkcję członkowską

`bool operator(const Key& left, const Key& right);`

zwraca **wartość true** , `left` Jeśli poprzedza i nie `right` jest równa w kolejności sortowania.

### <a name="example"></a>Przykład

```cpp
// map_key_comp.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;

   map <int, int, less<int> > m1;
   map <int, int, less<int> >::key_compare kc1 = m1.key_comp( ) ;
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

   map <int, int, greater<int> > m2;
   map <int, int, greater<int> >::key_compare kc2 = m2.key_comp( );
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

## <a name="key_compare"></a>key_compare

Typ, który dostarcza obiekt funkcji, który może porównać dwa klucze sortowania, aby określić względną kolejność dwóch elementów na mapie.

```cpp
typedef Traits key_compare;
```

### <a name="remarks"></a>Uwagi

`key_compare`jest synonimem *cech*parametrów szablonu.

Aby uzyskać więcej informacji  o cechach, zobacz temat [Klasa map](../standard-library/map-class.md) .

### <a name="example"></a>Przykład

Zobacz przykład dla [key_comp](#key_comp) , aby zapoznać się z przykładem sposobu deklarowania i używania `key_compare`.

## <a name="key_type"></a>key_type

Typ, który opisuje klucz sortowania przechowywany w każdym elemencie mapy.

```cpp
typedef Key key_type;
```

### <a name="remarks"></a>Uwagi

`key_type`jest synonimem dla *klucza*parametru szablonu.

Aby uzyskać więcej informacji o kluczu, zobacz sekcję Uwagi w temacie [Mapowanie klasy](../standard-library/map-class.md) .

### <a name="example"></a>Przykład

Zobacz przykład dla [value_type](#value_type) , aby zapoznać się z przykładem sposobu deklarowania i używania `key_type`.

## <a name="lower_bound"></a>lower_bound

Zwraca iterator do pierwszego elementu w mapie z wartością klucza, która jest równa lub większa od określonego klucza.

```cpp
iterator lower_bound(const Key& key);

const_iterator lower_bound(const Key& key) const;
```

### <a name="parameters"></a>Parametry

*głównych*\
Wartość klucza argumentu do porównania z kluczem sortowania elementu z przeszukiwanej mapy.

### <a name="return-value"></a>Wartość zwracana

`iterator` Lub`const_iterator` który odnosi się do lokalizacji elementu w mapie, który ma klucz, który jest równy lub większy od klucza argumentu lub który odnosi się do lokalizacji, która kończy ostatni element na mapie, jeśli nie zostanie znaleziony żaden pasujący klucz.

Jeśli wartość `lower_bound` zwracana jest przypisana `const_iterator`do, obiekt mapy nie może być modyfikowany. Jeśli wartość `lower_bound` zwracana jest przypisana `iterator`do, obiekt mapy może być modyfikowany.

### <a name="example"></a>Przykład

```cpp
// map_lower_bound.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   map <int, int> m1;
   map <int, int> :: const_iterator m1_AcIter, m1_RcIter;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 1, 10 ) );
   m1.insert ( Int_Pair ( 2, 20 ) );
   m1.insert ( Int_Pair ( 3, 30 ) );

   m1_RcIter = m1.lower_bound( 2 );
   cout << "The first element of map m1 with a key of 2 is: "
        << m1_RcIter -> second << "." << endl;

   // If no match is found for this key, end( ) is returned
   m1_RcIter = m1. lower_bound ( 4 );

   if ( m1_RcIter == m1.end( ) )
      cout << "The map m1 doesn't have an element "
           << "with a key of 4." << endl;
   else
      cout << "The element of map m1 with a key of 4 is: "
           << m1_RcIter -> second << "." << endl;

   // The element at a specific location in the map can be found
   // using a dereferenced iterator addressing the location
   m1_AcIter = m1.end( );
   m1_AcIter--;
   m1_RcIter = m1. lower_bound ( m1_AcIter -> first );
   cout << "The element of m1 with a key matching "
        << "that of the last element is: "
        << m1_RcIter -> second << "." << endl;
}
```

```Output
The first element of map m1 with a key of 2 is: 20.
The map m1 doesn't have an element with a key of 4.
The element of m1 with a key matching that of the last element is: 30.
```

## <a name="map"></a>zmapować

Tworzy mapę, która jest pusta lub jest kopią całości lub części innej mapy.

```cpp
map();

explicit map(
    const Traits& Comp);

map(
    const Traits& Comp,
    const Allocator& Al);

map(
    const map& Right);

map(
    map&& Right);

map(
    initializer_list<value_type> IList);

map(
    initializer_list<value_type> IList,
    const Traits& Comp);

map(
    initializer_list<value_type> IList,
    const Traits& Comp,
    const Allocator& Allocator);

template <class InputIterator>
map(
    InputIterator First,
    InputIterator Last);

template <class InputIterator>
map(
    InputIterator First,
    InputIterator Last,
    const Traits& Comp);

template <class InputIterator>
map(
    InputIterator First,
    InputIterator Last,
    const Traits& Comp,
    const Allocator& Al);
```

### <a name="parameters"></a>Parametry

*Wsp*\
Klasa alokatora magazynu, która ma być używana dla tego obiektu mapy, która `Allocator`jest domyślna.

*Przepisów*\
Funkcja porównywania typu `const Traits` służąca do porządkowania elementów w mapie, które są `hash_compare`domyślnie.

*Kliknij*\
Mapa, której skonstruowany zestaw ma być kopią.

*Pierwszego*\
Pozycja pierwszego elementu w zakresie elementów, które mają zostać skopiowane.

*Ostatniego*\
Pozycja pierwszego elementu poza zakresem elementów, które mają zostać skopiowane.

*IList*\
Initializer_list, z którego mają zostać skopiowane elementy.

### <a name="remarks"></a>Uwagi

Wszystkie konstruktory przechowują typ obiektu alokatora, który zarządza magazynem pamięci dla mapy i który może być później zwracany przez wywołanie [get_allocator](#get_allocator). Parametr alokatora jest często pomijany w deklaracjach klas i makrach przetwarzania wstępnego służących do podstawiania alternatywnych metod przydzielania.

Wszystkie konstruktory inicjują swoją mapę.

Wszystkie konstruktory przechowują obiekt funkcji typu cech, który jest używany do ustanowienia zamówienia między kluczami mapy i który może być później zwracany przez wywołanie [key_comp](#key_comp).

Pierwsze trzy konstruktory określają pustą mapę początkową, drugą określającą typ funkcji porównywania (*COMP*), która ma zostać użyta w celu ustalenia kolejności elementów i trzeciego jawnie określającego typ alokatora (*Al*), który ma być używany. Słowo kluczowe **Explicit** pomija pewne rodzaje automatycznej konwersji typów.

Czwarty Konstruktor określa kopię mapy *po prawej stronie*.

Piąty Konstruktor określa kopię mapy, przenosząc *prawo*.

Konstruktor szósty, siódmy i ósmy używają initializer_list, z którego można skopiować elementy członkowskie.

Następne trzy konstruktory kopiują zakres `[First, Last)` mapy ze wzrostem jawności w określaniu typu funkcji porównania klasy `Traits` i alokatora.

### <a name="example"></a>Przykład

```cpp
// map_map.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main()
{
    using namespace std;
    typedef pair <int, int> Int_Pair;
    map <int, int>::iterator m1_Iter, m3_Iter, m4_Iter, m5_Iter, m6_Iter, m7_Iter;
    map <int, int, less<int> >::iterator m2_Iter;

    // Create an empty map m0 of key type integer
    map <int, int> m0;

    // Create an empty map m1 with the key comparison
    // function of less than, then insert 4 elements
    map <int, int, less<int> > m1;
    m1.insert(Int_Pair(1, 10));
    m1.insert(Int_Pair(2, 20));
    m1.insert(Int_Pair(3, 30));
    m1.insert(Int_Pair(4, 40));

    // Create an empty map m2 with the key comparison
    // function of greater than, then insert 2 elements
    map <int, int, less<int> > m2;
    m2.insert(Int_Pair(1, 10));
    m2.insert(Int_Pair(2, 20));

    // Create a map m3 with the
    // allocator of map m1
    map <int, int>::allocator_type m1_Alloc;
    m1_Alloc = m1.get_allocator();
    map <int, int> m3(less<int>(), m1_Alloc);
    m3.insert(Int_Pair(3, 30));

    // Create a copy, map m4, of map m1
    map <int, int> m4(m1);

    // Create a map m5 by copying the range m1[ first,  last)
    map <int, int>::const_iterator m1_bcIter, m1_ecIter;
    m1_bcIter = m1.begin();
    m1_ecIter = m1.begin();
    m1_ecIter++;
    m1_ecIter++;
    map <int, int> m5(m1_bcIter, m1_ecIter);

    // Create a map m6 by copying the range m4[ first,  last)
    // and with the allocator of map m2
    map <int, int>::allocator_type m2_Alloc;
    m2_Alloc = m2.get_allocator();
    map <int, int> m6(m4.begin(), ++m4.begin(), less<int>(), m2_Alloc);

    cout << "m1 =";
    for (auto i : m1)
        cout << i.first << " " << i.second << ", ";
    cout << endl;

    cout << "m2 =";
    for(auto i : m2)
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

    // Create a map m7 by moving m5
    cout << "m7 =";
    map<int, int> m7(move(m5));
    for (auto i : m7)
        cout << i.first << " " << i.second << ", ";
    cout << endl;

    // Create a map m8 by copying in an initializer_list
    map<int, int> m8{ { { 1, 1 }, { 2, 2 }, { 3, 3 }, { 4, 4 } } };
    cout << "m8: = ";
    for (auto i : m8)
        cout << i.first << " " << i.second << ", ";
    cout << endl;

    // Create a map m9 with an initializer_list and a comparator
    map<int, int> m9({ { 5, 5 }, { 6, 6 }, { 7, 7 }, { 8, 8 } }, less<int>());
    cout << "m9: = ";
    for (auto i : m9)
        cout << i.first << " " << i.second << ", ";
    cout << endl;

    // Create a map m10 with an initializer_list, a comparator, and an allocator
    map<int, int> m10({ { 9, 9 }, { 10, 10 }, { 11, 11 }, { 12, 12 } }, less<int>(), m9.get_allocator());
    cout << "m10: = ";
    for (auto i : m10)
        cout << i.first << " " << i.second << ", ";
    cout << endl;
}
```

## <a name="mapped_type"></a>mapped_type

Typ, który reprezentuje dane przechowywane na mapie.

```cpp
typedef Type mapped_type;
```

### <a name="remarks"></a>Uwagi

Typ `mapped_type` jest synonimem dla parametru szablonu *typu* klasy.

Aby uzyskać więcej informacji na temat *typu* , zobacz temat [Klasa map](../standard-library/map-class.md) .

### <a name="example"></a>Przykład

Zobacz przykład dla [value_type](#value_type) , aby zapoznać się z przykładem sposobu deklarowania i używania `mapped_type`.

## <a name="max_size"></a>max_size

Zwraca maksymalną długość mapy.

```cpp
size_type max_size() const;
```

### <a name="return-value"></a>Wartość zwracana

Maksymalna możliwa długość mapy.

### <a name="example"></a>Przykład

```cpp
// map_max_size.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   map <int, int> m1;
   map <int, int> :: size_type i;

   i = m1.max_size( );
   cout << "The maximum possible length "
        << "of the map is " << i << "."
        << endl << "(Magnitude is machine specific.)";
}
```

## <a name="op_at"></a>operator []

Wstawia element do mapy z określoną wartością klucza.

```cpp
Type& operator[](const Key& key);

Type& operator[](Key&& key);
```

### <a name="parameters"></a>Parametry

*głównych*\
Wartość klucza elementu, który ma zostać wstawiony.

### <a name="return-value"></a>Wartość zwracana

Odwołanie do wartości danych wstawionego elementu.

### <a name="remarks"></a>Uwagi

Jeśli wartość klucza argumentu nie zostanie znaleziona, zostanie ona wstawiona wraz z wartością domyślną typu danych.

`operator[]`może służyć do wstawiania elementów `m` do mapy, przy użyciu `m[key] = DataValue;` gdzie `DataValue` jest wartością `mapped_type` elementu z kluczową wartością *klucza*.

Podczas używania `operator[]` do wstawiania elementów, zwrócone odwołanie nie wskazuje, czy wstawienie zmienia istniejący element lub tworzy nowy. Funkcje członkowskie [Znajdź](#find) i [Wstaw](#insert) mogą służyć do określenia, czy element z określonym kluczem jest już obecny przed wstawieniem.

### <a name="example"></a>Przykład

```cpp
// map_op_insert.cpp
// compile with: /EHsc
#include <map>
#include <iostream>
#include <string>

int main( )
{
   using namespace std;
   typedef pair <const int, int> cInt2Int;
   map <int, int> m1;
   map <int, int> :: iterator pIter;

   // Insert a data value of 10 with a key of 1
   // into a map using the operator[] member function
   m1[ 1 ] = 10;

   // Compare other ways to insert objects into a map
   m1.insert ( map <int, int> :: value_type ( 2, 20 ) );
   m1.insert ( cInt2Int ( 3, 30 ) );

   cout  << "The keys of the mapped elements are:";
   for ( pIter = m1.begin( ) ; pIter != m1.end( ) ; pIter++ )
      cout << " " << pIter -> first;
   cout << "." << endl;

   cout  << "The values of the mapped elements are:";
   for ( pIter = m1.begin( ) ; pIter != m1.end( ) ; pIter++ )
      cout << " " << pIter -> second;
   cout << "." << endl;

   // If the key already exists, operator[]
   // changes the value of the datum in the element
   m1[ 2 ] = 40;

   // operator[] will also insert the value of the data
   // type's default constructor if the value is unspecified
   m1[5];

   cout  << "The keys of the mapped elements are now:";
   for ( pIter = m1.begin( ) ; pIter != m1.end( ) ; pIter++ )
      cout << " " << pIter -> first;
   cout << "." << endl;

   cout  << "The values of the mapped elements are now:";
   for ( pIter = m1.begin( ) ; pIter != m1.end( ) ; pIter++ )
      cout << " " << pIter -> second;
   cout << "." << endl;

// insert by moving key
    map<string, int> c2;
    string str("abc");
    cout << "c2[move(str)] == " << c2[move(str)] << endl;
    cout << "c2["abc"] == " << c2["abc"] << endl;

    return (0);
}
```

```Output
The keys of the mapped elements are: 1 2 3.
The values of the mapped elements are: 10 20 30.
The keys of the mapped elements are now: 1 2 3 5.
The values of the mapped elements are now: 10 40 30 0.
c2[move(str)] == 0
c2["abc"] == 1
```

## <a name="op_eq"></a>operator =

Zastępuje elementy mapy kopią innej mapy.

```cpp
map& operator=(const map& right);
map& operator=(map&& right);
```

### <a name="parameters"></a>Parametry

*Kliknij*\
[Mapa](../standard-library/map-class.md) jest kopiowana do `map`.

### <a name="remarks"></a>Uwagi

Po wymazaniu wszelkich istniejących elementów w `map`, program `operator=` kopiuje lub przenosi zawartość *bezpośrednio* do mapy.

### <a name="example"></a>Przykład

```cpp
// map_operator_as.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
   {
   using namespace std;
   map<int, int> v1, v2, v3;
   map<int, int>::iterator iter;

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

## <a name="pointer"></a>przytrzymaj

Typ, który dostarcza wskaźnik do elementu w mapie.

```cpp
typedef typename allocator_type::pointer pointer;
```

### <a name="remarks"></a>Uwagi

Typ `pointer` może służyć do modyfikowania wartości elementu.

W większości przypadków [iterator](#iterator) powinien być używany do uzyskiwania dostępu do elementów w obiekcie mapy.

## <a name="rbegin"></a>rbegin

Zwraca iterator odnoszący się do pierwszego elementu w odwróconej mapie.

```cpp
const_reverse_iterator rbegin() const;

reverse_iterator rbegin();
```

### <a name="return-value"></a>Wartość zwracana

Odwrotny iterator dwukierunkowy odnoszący się do pierwszego elementu w odwróconej mapie lub odnoszący się do ostatniego elementu w mapie nieodwróconej.

### <a name="remarks"></a>Uwagi

`rbegin`jest używany z odwróconą mapą, tak jak [początek](#begin) jest używany z mapą.

Jeśli wartość `rbegin` zwracana jest przypisana `const_reverse_iterator`do, obiekt mapy nie może być modyfikowany. Jeśli wartość `rbegin` zwracana jest przypisana `reverse_iterator`do, obiekt mapy można modyfikować.

`rbegin`może służyć do iteracji przez mapę do tyłu.

### <a name="example"></a>Przykład

```cpp
// map_rbegin.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   map <int, int> m1;

   map <int, int> :: iterator m1_Iter;
   map <int, int> :: reverse_iterator m1_rIter;
   map <int, int> :: const_reverse_iterator m1_crIter;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 1, 10 ) );
   m1.insert ( Int_Pair ( 2, 20 ) );
   m1.insert ( Int_Pair ( 3, 30 ) );

   m1_rIter = m1.rbegin( );
   cout << "The first element of the reversed map m1 is "
        << m1_rIter -> first << "." << endl;

   // begin can be used to start an iteration
   // through a map in a forward order
   cout << "The map is: ";
   for ( m1_Iter = m1.begin( ) ; m1_Iter != m1.end( ); m1_Iter++)
      cout << m1_Iter -> first << " ";
      cout << "." << endl;

   // rbegin can be used to start an iteration
   // through a map in a reverse order
   cout << "The reversed map is: ";
   for ( m1_rIter = m1.rbegin( ) ; m1_rIter != m1.rend( ); m1_rIter++)
      cout << m1_rIter -> first << " ";
      cout << "." << endl;

   // A map element can be erased by dereferencing to its key
   m1_rIter = m1.rbegin( );
   m1.erase ( m1_rIter -> first );

   m1_rIter = m1.rbegin( );
   cout << "After the erasure, the first element "
        << "in the reversed map is "
        << m1_rIter -> first << "." << endl;
}
```

```Output
The first element of the reversed map m1 is 3.
The map is: 1 2 3 .
The reversed map is: 3 2 1 .
After the erasure, the first element in the reversed map is 2.
```

## <a name="reference"></a>odwoła

Typ, który zawiera odwołanie do elementu przechowywanego w mapie.

```cpp
typedef typename allocator_type::reference reference;
```

### <a name="example"></a>Przykład

```cpp
// map_reference.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   map <int, int> m1;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 1, 10 ) );
   m1.insert ( Int_Pair ( 2, 20 ) );

   // Declare and initialize a const_reference &Ref1
   // to the key of the first element
   const int &Ref1 = ( m1.begin( ) -> first );

   // The following line would cause an error because the
   // non-const_reference cannot be used to access the key
   // int &Ref1 = ( m1.begin( ) -> first );

   cout << "The key of first element in the map is "
        << Ref1 << "." << endl;

   // Declare and initialize a reference &Ref2
   // to the data value of the first element
   int &Ref2 = ( m1.begin( ) -> second );

   cout << "The data value of first element in the map is "
        << Ref2 << "." << endl;

   //The non-const_reference can be used to modify the
   //data value of the first element
   Ref2 = Ref2 + 5;
   cout << "The modified data value of first element is "
        << Ref2 << "." << endl;
}
```

```Output
The key of first element in the map is 1.
The data value of first element in the map is 10.
The modified data value of first element is 15.
```

## <a name="rend"></a>rend

Zwraca iterator, który odnosi się do lokalizacji po ostatnim elemencie w odwróconej mapie.

```cpp
const_reverse_iterator rend() const;

reverse_iterator rend();
```

### <a name="return-value"></a>Wartość zwracana

Odwrotny iterator dwukierunkowy, który odnosi się do lokalizacji po ostatnim elemencie w odwróconej mapie (lokalizacja, która poprzedza pierwszy element na mapie nieodwróconej).

### <a name="remarks"></a>Uwagi

`rend`jest używany z odwróconą mapą, tak jak [koniec](#end) jest używany z mapą.

Jeśli wartość `rend` zwracana jest przypisana `const_reverse_iterator`do, obiekt mapy nie może być modyfikowany. Jeśli wartość `rend` zwracana jest przypisana `reverse_iterator`do, obiekt mapy można modyfikować.

`rend`można go użyć do przetestowania, czy iterator odwrotny osiągnął koniec jego mapy.

Nie można usunąć odwołania `rend` do wartości zwracanej przez.

### <a name="example"></a>Przykład

```cpp
// map_rend.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   map <int, int> m1;

   map <int, int> :: iterator m1_Iter;
   map <int, int> :: reverse_iterator m1_rIter;
   map <int, int> :: const_reverse_iterator m1_crIter;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 1, 10 ) );
   m1.insert ( Int_Pair ( 2, 20 ) );
   m1.insert ( Int_Pair ( 3, 30 ) );

   m1_rIter = m1.rend( );
   m1_rIter--;
   cout << "The last element of the reversed map m1 is "
        << m1_rIter -> first << "." << endl;

   // begin can be used to start an iteration
   // through a map in a forward order
   cout << "The map is: ";
   for ( m1_Iter = m1.begin( ) ; m1_Iter != m1.end( ); m1_Iter++)
      cout << m1_Iter -> first << " ";
      cout << "." << endl;

   // rbegin can be used to start an iteration
   // through a map in a reverse order
   cout << "The reversed map is: ";
   for ( m1_rIter = m1.rbegin( ) ; m1_rIter != m1.rend( ); m1_rIter++)
      cout << m1_rIter -> first << " ";
      cout << "." << endl;

   // A map element can be erased by dereferencing to its key
   m1_rIter = --m1.rend( );
   m1.erase ( m1_rIter -> first );

   m1_rIter = m1.rend( );
   m1_rIter--;
   cout << "After the erasure, the last element "
        << "in the reversed map is "
        << m1_rIter -> first << "." << endl;
}
```

```Output
The last element of the reversed map m1 is 1.
The map is: 1 2 3 .
The reversed map is: 3 2 1 .
After the erasure, the last element in the reversed map is 2.
```

## <a name="reverse_iterator"></a>reverse_iterator

Typ, który dostarcza iterator dwukierunkowy, który może odczytać lub zmodyfikować element w odwróconej mapie.

```cpp
typedef std::reverse_iterator<iterator> reverse_iterator;
```

### <a name="remarks"></a>Uwagi

Typ `reverse_iterator` nie może zmodyfikować wartości elementu i służy do wykonywania iteracji mapy w odwrotnej postaci.

Zdefiniowane przez mapę wskazuje elementy, które są obiektami [value_type](#value_type), które są typu `pair<const Key, Type>`, którego pierwszy element członkowski jest kluczem do elementu, a drugi element członkowski jest zmapowaną podstawą zawartą w elemencie. `reverse_iterator`

Aby usunąć odwołanie `reverse_iterator` do elementu, *który wskazuje element* na `->` mapie, użyj operatora.

Aby uzyskać dostęp do wartości klucza dla elementu, użyj `rIter`\*  ->  **pierwszej**, który jest odpowiednikiem ( `rIter`). **najpierw**. Aby uzyskać dostęp do wartości mapowanej podstawy dla `rIter`elementu, użyj\*  ->  **sekundy**, który jest odpowiednikiem ( `rIter`). **najpierw**.

### <a name="example"></a>Przykład

Zobacz przykład dla [rbegin](#rbegin) , aby zapoznać się z przykładem sposobu deklarowania i używania `reverse_iterator`.

## <a name="size"></a>zmienia

Zwraca liczbę elementów w mapie.

```cpp
size_type size() const;
```

### <a name="return-value"></a>Wartość zwracana

Bieżąca długość mapy.

### <a name="example"></a>Przykład

Poniższy przykład ilustruje sposób użycia funkcji elementu członkowskiego map:: size.

```cpp
// map_size.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main()
{
    using namespace std;
    map<int, int> m1, m2;
    map<int, int>::size_type i;
    typedef pair<int, int> Int_Pair;

    m1.insert(Int_Pair(1, 1));
    i = m1.size();
    cout << "The map length is " << i << "." << endl;

    m1.insert(Int_Pair(2, 4));
    i = m1.size();
    cout << "The map length is now " << i << "." << endl;
}
```

```Output
The map length is 1.
The map length is now 2.
```

## <a name="size_type"></a>size_type

Typ liczby całkowitej bez znaku, który może reprezentować liczbę elementów w mapie.

```cpp
typedef typename allocator_type::size_type size_type;
```

### <a name="example"></a>Przykład

Zapoznaj się z przykładem dotyczącym [rozmiaru](#size) , aby zapoznać się z `size_type`przykładem sposobu deklarowania i używania.

## <a name="swap"></a>wymiany

Zamienia elementy z dwóch map.

```cpp
void swap(
    map<Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*Kliknij*\
Mapa argumentu dostarczająca elementy do zamiany na mapę docelową.

### <a name="remarks"></a>Uwagi

Funkcja członkowska unieważnia odwołania, wskaźniki lub Iteratory, które wyznaczają elementy w dwóch mapach, których elementy są wymieniane.

### <a name="example"></a>Przykład

```cpp
// map_swap.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   map <int, int> m1, m2, m3;
   map <int, int>::iterator m1_Iter;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 1, 10 ) );
   m1.insert ( Int_Pair ( 2, 20 ) );
   m1.insert ( Int_Pair ( 3, 30 ) );
   m2.insert ( Int_Pair ( 10, 100 ) );
   m2.insert ( Int_Pair ( 20, 200 ) );
   m3.insert ( Int_Pair ( 30, 300 ) );

   cout << "The original map m1 is:";
   for ( m1_Iter = m1.begin( ); m1_Iter != m1.end( ); m1_Iter++ )
      cout << " " << m1_Iter -> second;
   cout   << "." << endl;

   // This is the member function version of swap
   //m2 is said to be the argument map; m1 the target map
   m1.swap( m2 );

   cout << "After swapping with m2, map m1 is:";
   for ( m1_Iter = m1.begin( ); m1_Iter != m1.end( ); m1_Iter++ )
      cout << " " << m1_Iter -> second;
   cout  << "." << endl;

   // This is the specialized template version of swap
   swap( m1, m3 );

   cout << "After swapping with m3, map m1 is:";
   for ( m1_Iter = m1.begin( ); m1_Iter != m1.end( ); m1_Iter++ )
      cout << " " << m1_Iter -> second;
   cout   << "." << endl;
}
```

```Output
The original map m1 is: 10 20 30.
After swapping with m2, map m1 is: 100 200.
After swapping with m3, map m1 is: 300.
```

## <a name="upper_bound"></a>upper_bound

Zwraca iterator do pierwszego elementu w mapie, który ma klucz o wartości większej niż wartość określonego klucza.

```cpp
iterator upper_bound(const Key& key);

const_iterator upper_bound(const Key& key) const;
```

### <a name="parameters"></a>Parametry

*głównych*\
Wartość klucza argumentu do porównania z wartością klucza sortowania elementu z przeszukiwanej mapy.

### <a name="return-value"></a>Wartość zwracana

`iterator` Lub`const_iterator` który odnosi się do lokalizacji elementu w mapie, który ma klucz, który jest większy niż klucz argumentu lub który odnosi się do lokalizacji z ostatnim elementem w mapie, jeśli nie znaleziono pasujących kluczy.

Jeśli wartość zwracana jest przypisana do `const_iterator`, obiekt mapy nie może być modyfikowany. Jeśli wartość zwracana jest przypisana do `iterator`, obiekt mapy może być modyfikowany.

### <a name="example"></a>Przykład

```cpp
// map_upper_bound.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   map <int, int> m1;
   map <int, int> :: const_iterator m1_AcIter, m1_RcIter;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 1, 10 ) );
   m1.insert ( Int_Pair ( 2, 20 ) );
   m1.insert ( Int_Pair ( 3, 30 ) );

   m1_RcIter = m1.upper_bound( 2 );
   cout << "The first element of map m1 with a key "
        << "greater than 2 is: "
        << m1_RcIter -> second << "." << endl;

   // If no match is found for the key, end is returned
   m1_RcIter = m1. upper_bound ( 4 );

   if ( m1_RcIter == m1.end( ) )
      cout << "The map m1 doesn't have an element "
           << "with a key greater than 4." << endl;
   else
      cout << "The element of map m1 with a key > 4 is: "
           << m1_RcIter -> second << "." << endl;

   // The element at a specific location in the map can be found
   // using a dereferenced iterator addressing the location
   m1_AcIter = m1.begin( );
   m1_RcIter = m1. upper_bound ( m1_AcIter -> first );
   cout << "The 1st element of m1 with a key greater than\n"
        << "that of the initial element of m1 is: "
        << m1_RcIter -> second << "." << endl;
}
```

```Output
The first element of map m1 with a key greater than 2 is: 30.
The map m1 doesn't have an element with a key greater than 4.
The 1st element of m1 with a key greater than
that of the initial element of m1 is: 20.
```

## <a name="value_comp"></a>value_comp

Funkcja członkowska zwraca obiekt funkcji, który określa kolejność elementów w mapie, porównując ich wartości klucza.

```cpp
value_compare value_comp() const;
```

### <a name="return-value"></a>Wartość zwracana

Zwraca obiekt funkcji porównywania, który jest wykorzystywany przez mapę do porządkowania jego elementów.

### <a name="remarks"></a>Uwagi

W przypadku mapy *m*, jeśli dwa elementy *E1*(*K1*, *D1*) i *E2*(*K2*, *D2*) są obiektami typu `value_type`, gdzie *K1* i *K1* są swoimi kluczami typu `key_type` i *D1* oraz *D2* są swoimi danymi typu `mapped_type`, `m.key_comp(k1, k2)`a następnie `m.value_comp(e1, e2)` są równoważne. Przechowywany obiekt definiuje funkcję członkowską

`bool operator( value_type& left, value_type& right);`

Zwraca wartość **true** , jeśli wartość `left` klucza poprzedza i nie jest równa wartości `right` klucza w kolejności sortowania.

### <a name="example"></a>Przykład

```cpp
// map_value_comp.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;

   map <int, int, less<int> > m1;
   map <int, int, less<int> >::value_compare vc1 = m1.value_comp( );
   pair< map<int,int>::iterator, bool > pr1, pr2;

   pr1= m1.insert ( map <int, int> :: value_type ( 1, 10 ) );
   pr2= m1.insert ( map <int, int> :: value_type ( 2, 5 ) );

   if( vc1( *pr1.first, *pr2.first ) == true )
   {
      cout << "The element ( 1,10 ) precedes the element ( 2,5 )."
           << endl;
   }
   else
   {
      cout << "The element ( 1,10 ) does not precede the element ( 2,5 )."
           << endl;
   }

   if(vc1( *pr2.first, *pr1.first ) == true )
   {
      cout << "The element ( 2,5 ) precedes the element ( 1,10 )."
           << endl;
   }
   else
   {
      cout << "The element ( 2,5 ) does not precede the element ( 1,10 )."
           << endl;
   }
}
```

```Output
The element ( 1,10 ) precedes the element ( 2,5 ).
The element ( 2,5 ) does not precede the element ( 1,10 ).
```

## <a name="value_type"></a>value_type

Typ obiektu przechowywanego jako element na mapie.

```cpp
typedef pair<const Key, Type> value_type;
```

### <a name="example"></a>Przykład

```cpp
// map_value_type.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   typedef pair <const int, int> cInt2Int;
   map <int, int> m1;
   map <int, int> :: key_type key1;
   map <int, int> :: mapped_type mapped1;
   map <int, int> :: value_type value1;
   map <int, int> :: iterator pIter;

   // value_type can be used to pass the correct type
   // explicitly to avoid implicit type conversion
   m1.insert ( map <int, int> :: value_type ( 1, 10 ) );

   // Compare other ways to insert objects into a map
   m1.insert ( cInt2Int ( 2, 20 ) );
   m1[ 3 ] = 30;

   // Initializing key1 and mapped1
   key1 = ( m1.begin( ) -> first );
   mapped1 = ( m1.begin( ) -> second );

   cout << "The key of first element in the map is "
        << key1 << "." << endl;

   cout << "The data value of first element in the map is "
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

## <a name="see-also"></a>Zobacz także

[Opakowania](../cpp/containers-modern-cpp.md)\
[Bezpieczeństwo wątku w C++ standardowej bibliotece](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Dokumentacja standardowej biblioteki C++](../standard-library/cpp-standard-library-reference.md)
