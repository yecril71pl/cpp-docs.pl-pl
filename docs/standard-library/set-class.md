---
title: set — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- set/std::set
- set/std::set::allocator_type
- set/std::set::const_iterator
- set/std::set::const_pointer
- set/std::set::const_reference
- set/std::set::const_reverse_iterator
- set/std::set::difference_type
- set/std::set::iterator
- set/std::set::key_compare
- set/std::set::key_type
- set/std::set::pointer
- set/std::set::reference
- set/std::set::reverse_iterator
- set/std::set::size_type
- set/std::set::value_compare
- set/std::set::value_type
- set/std::set::begin
- set/std::set::cbegin
- set/std::set::cend
- set/std::set::clear
- set/std::set::count
- set/std::set::crbegin
- set/std::set::crend
- set/std::set::emplace
- set/std::set::emplace_hint
- set/std::set::empty
- set/std::set::end
- set/std::set::equal_range
- set/std::set::erase
- set/std::set::find
- set/std::set::get_allocator
- set/std::set::insert
- set/std::set::key_comp
- set/std::set::lower_bound
- set/std::set::max_size
- set/std::set::rbegin
- set/std::set::rend
- set/std::set::size
- set/std::set::swap
- set/std::set::upper_bound
- set/std::set::value_comp
dev_langs:
- C++
helpviewer_keywords:
- std::set [C++]
- std::set [C++], allocator_type
- std::set [C++], const_iterator
- std::set [C++], const_pointer
- std::set [C++], const_reference
- std::set [C++], const_reverse_iterator
- std::set [C++], difference_type
- std::set [C++], iterator
- std::set [C++], key_compare
- std::set [C++], key_type
- std::set [C++], pointer
- std::set [C++], reference
- std::set [C++], reverse_iterator
- std::set [C++], size_type
- std::set [C++], value_compare
- std::set [C++], value_type
- std::set [C++], begin
- std::set [C++], cbegin
- std::set [C++], cend
- std::set [C++], clear
- std::set [C++], count
- std::set [C++], crbegin
- std::set [C++], crend
- std::set [C++], emplace
- std::set [C++], emplace_hint
- std::set [C++], empty
- std::set [C++], end
- std::set [C++], equal_range
- std::set [C++], erase
- std::set [C++], find
- std::set [C++], get_allocator
- std::set [C++], insert
- std::set [C++], key_comp
- std::set [C++], lower_bound
- std::set [C++], max_size
- std::set [C++], rbegin
- std::set [C++], rend
- std::set [C++], size
- std::set [C++], swap
- std::set [C++], upper_bound
- std::set [C++], value_comp
ms.assetid: 8991f9aa-5509-4440-adc1-371512d32018
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4c22a260130d38a4ed1dfbf1a49bbc5d670357c3
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33865736"
---
# <a name="set-class"></a>set — Klasa

Zestaw klas kontenera standardowa biblioteka C++ jest używany do przechowywania i pobierania danych z kolekcji, w której wartości elementy zawarte są unikatowe i służyć jako wartości klucza, zgodnie z którymi automatycznie porządkowania danych. Nie można bezpośrednio zmienić wartości elementu w zestawie. Zamiast tego musisz usunąć stare wartości i wstawić elementy z nowymi wartościami.

## <a name="syntax"></a>Składnia

```cpp
template <class Key,
    class Traits=less<Key>,
    class Allocator=allocator<Key>>
class set
```

### <a name="parameters"></a>Parametry

`Key` Typ danych elementu mają być przechowywane w zestawie.

`Traits` Typ, który udostępnia obiekt funkcji, które można porównać dwóch wartości elementu jako klucze sortowania, aby określić ich kolejność względne w zestawie. Ten argument jest opcjonalny i binarne predykatu **mniej**  *\<klucza >* jest wartością domyślną.

W języku C ++ 14 można włączyć heterogenicznych wyszukiwania, określając `std::less<>` lub `std::greater<>` predykatu, który nie ma typu parametrów. Aby uzyskać więcej informacji, zobacz [heterogenicznych wyszukiwanie w kontenerach asocjacyjnej](../standard-library/stl-containers.md#sequence_containers)

`Allocator` Typ reprezentujący obiekt alokatora przechowywane, który hermetyzuje informacje szczegółowe o alokacji i cofania alokacji pamięci z zestawu. Ten argument jest opcjonalny, a wartość domyślna to **alokatora ***\<klucza >.*

## <a name="remarks"></a>Uwagi

Standardowa biblioteka C++ zestaw jest:

- Kontenerem asocjacyjnym, który jest kontenerem o zmiennym rozmiarze, obsługującym efektywne pobieranie wartości elementu w oparciu o wartość skojarzonego klucza. Ponadto, jest prostym kontenerem asocjacyjnym, ponieważ jego wartości elementu są jego wartościami klucza.

- Odwracalny, ponieważ zapewnia dwukierunkowy iterator do dostępu do jego elementów.

- Posortowany, ponieważ jego elementy są uporządkowane według wartości kluczy w kontenerze zgodnie z określoną funkcją porównywania.

- Unikatowy w tym sensie, że każdy z jego elementów musi mieć unikatowy klucz. Ponieważ zestaw jest również prostym kontenerem asocjacyjnym, jego elementy są również unikatowe.

Zestaw jest też opisany jako klasa szablonu, ponieważ funkcjonalność, którą zapewnia, jest generyczna i dlatego niezależna od określonego typu danych zawartych jako elementy. Typ danych, który ma być użyty, jest zamiast tego określony jako parametr w klasie szablonu wraz z funkcją porównania i alokatorem.

Wybór typu kontenera powinien ogólnie być oparty o typ wyszukiwania i wstawiania wymagany przez aplikację. Kontenery asocjacyjne są zoptymalizowane dla operacji wyszukiwania, wstawiania oraz usuwania. Funkcje elementów członkowskich, które jawnie obsługują te operacje, są skuteczne, wykonując je w czasie, który jest średnio proporcjonalny do logarytmu liczby elementów w kontenerze. Wstawianie elementów nie unieważnia iteratorów, a usuwanie elementów unieważnia tylko te iteratory, które w szczególności wskazywały na usunięte elementy.

Zestaw powinien być kontenerem asocjacyjnym z wyboru, gdy warunki kojarzenia wartości z kluczami są spełnione przez aplikację. Elementy zestawu są unikatowe i służą jako ich własne klucze sortowania. Model dla tego typu konstrukcji jest uporządkowaną listą, np. wyrazów, w których wyrazy mogą występować tylko raz. Jeżeli zezwolono na wiele wystąpień wyrazów, odpowiednią strukturą kontenera będzie multiset. Gdyby wartości potrzebowały dołączenia do listy unikatowych słów kluczowych, mapa byłaby odpowiednią strukturą zawierającą te dane. Gdyby natomiast klucze nie były unikatowe, mapa wielokrotna byłaby kontenerem z wyboru.

Zestaw porządkuje sekwencji kontroluje przez wywołanie metody typu obiektu przechowywanej funkcji [key_compare](#key_compare). Ten obiekt przechowywanych jest funkcja porównanie, które mogą być używane przez wywołanie funkcji Członkowskich [key_comp](#key_comp). Ogólnie rzecz biorąc, elementy muszą być nieco mniej porównywalne, aby ustalić kolejność, tak aby, mając dowolne dwa elementy, można było określić, czy są one równoważne (w sensie, żaden nie jest mniejszy niż ten drugi) lub, że jeden jest mniejszy niż ten drugi. Skutkuje to ustaleniem kolejności dla elementów nierównoważnych. Ze strony bardziej technicznej, funkcja porównywania jest predykatem binarnym, który wymusza ścisłe słabe porządkowanie w standardowym sensie matematycznym. Predykat binarne *f*( *x, y*) jest obiektem funkcji, która ma dwa obiekty argument *x* i *y* i zwracana wartość  **wartość true,** lub **false**. Kolejność na zestaw jest niska strict, porządkowanie, jeśli binarne predykat jest niezwrotne antysymetryczne dają w wyniku i przechodnie i jeśli równoważność przechodnie, gdy dwa obiekty *x* i *y* są zdefiniowane jako gdy równoważne zarówno *f*( *x, y*) i *f*( *y, x*) to wartość false. Jeśli silniejszy warunek równości pomiędzy kluczami zastąpi ten równoważności, to porządkowanie będzie całkowite (w sensie, że wszystkie elementy są uporządkowane względem siebie), a dopasowane klucze będą od siebie nieodróżnialne.

W języku C ++ 14 można włączyć heterogenicznych wyszukiwania, określając `std::less<>` lub `std::greater<>` predykatu, który nie ma typu parametrów. Aby uzyskać więcej informacji, zobacz [heterogenicznych wyszukiwanie w kontenerach asocjacyjnej](../standard-library/stl-containers.md#sequence_containers)

Iterator udostępnianym przez klasę zestawu jest iteratora dwukierunkowego, ale funkcje Członkowskie klas [Wstaw](#insert) i [ustawić](#set) wersje przyjmować jako parametry szablonu słabszych iteratora wejściowych, którego wymagania funkcji są minimalne więcej niż gwarantowane przez klasę Iteratory dwukierunkowego. Pojęcia innych iteratorów formują rodzinę powiązaną przez udoskonalenia w ich funkcjonalnościach. Każde pojęcie iteratora ma swój własny zestaw wymagań, a algorytmy z nimi pracujące muszą ograniczać swoje założenia co do wymagań dostarczonych przez tego typu iterator. Można założyć, że z iteratora danych wejściowych można usunąć odwołanie, aby odwołać się do obiektu, a także, że może on być zwiększony do następnego iteratora w sekwencji. Jest to minimalny zestaw funkcji, ale jest wystarczające, aby można było uzyskać wiarygodny porozmawiać na temat zakresu Iteratory [ `First`, `Last`) w kontekście funkcji członkowskich tej klasy.

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[set](#set)|Konstruuje zestaw, który jest pusty lub jest kopią całości lub części innego zestawu.|

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[allocator_type](#allocator_type)|Typ reprezentujący `allocator` klasy dla obiekt zestawu.|
|[const_iterator](#const_iterator)|Typ, który udostępnia iteratora dwukierunkowego, który może odczytać `const` element w zestawie.|
|[const_pointer](#const_pointer)|Typ, który dostarcza wskaźnik do `const` element w zestawie.|
|[const_reference](#const_reference)|Typ, który zawiera odwołanie do `const` element przechowywane w zestawie do odczytu i wykonywania `const` operacji.|
|[const_reverse_iterator](#const_reverse_iterator)|Typ, który udostępnia iteratora dwukierunkowego, który może odczytać `const` element w zestawie.|
|[difference_type](#difference_type)|Typ liczby całkowitej ze znakiem, który może służyć do reprezentowania liczby elementów zestawu w zakresie pomiędzy elementami wskazywanymi przez iteratory.|
|[iterator](#iterator)|Typ, który dostarcza iterator dwukierunkowy do odczytu i modyfikacji dowolnego elementu w zestawie.|
|[key_compare](#key_compare)|Typ, który dostarcza obiekt funkcji, która może porównać dwa klucze sortowania, aby określić względną kolejność dwóch elementów w zestawie.|
|[key_type](#key_type)|Typ opisuje obiekt zapisany jako element zestawu w charakterze klucza sortowania.|
|[pointer](#pointer)|Typ, który dostarcza wskaźnik do elementu w zestawie.|
|[Odwołanie](#reference)|Typ, który zawiera odwołanie do elementu przechowywanego w zestawie.|
|[reverse_iterator](#reverse_iterator)|Typ, który dostarcza iterator dwukierunkowy do odczytu i modyfikacji elementu w odwróconym zestawie.|
|[size_type](#size_type)|Typ całkowitoliczbowy bez znaku, który może reprezentować liczbę elementów w zestawie.|
|[value_compare —](#value_compare)|Typ, który dostarcza obiekt funkcji, która może porównać dwa elementy jako klucze sortowania, aby określić ich względną kolejność w zestawie.|
|[value_type](#value_type)|Typ opisuje obiekt zapisany jako element zestawu w charakterze wartości.|

### <a name="member-functions"></a>Funkcje Członkowskie

|Funkcja członkowska|Opis|
|-|-|
|[begin](#begin)|Zwraca iterator, który dotyczy pierwszego elementu w zestawie.|
|[cbegin](#cbegin)|Zwraca iterator const, który dotyczy pierwszego elementu w zestawie.|
|[cend](#cend)|Zwraca iterator const, który dotyczy lokalizacji następującej po ostatnim elemencie w zestawie.|
|[Wyczyść](#clear)|Usuwa wszystkie elementy zestawu.|
|[Liczba](#count)|Zwraca liczbę elementów w zestawie, których klucz pasuje do klucza określonego jako parametr.|
|[crbegin](#rbegin)|Zwraca iterator const, który dotyczy pierwszego elementu w odwróconym zestawie.|
|[crend](#rend)|Zwraca iterator const, który dotyczy lokalizacji następującej po ostatnim elemencie w odwróconym zestawie.|
|[emplace](#emplace)|Wstawia element skonstruowany w miejscu do zestawu.|
|[emplace_hint](#emplace_hint)|Wstawia element skonstruowany w miejscu do zestawu, ze wskazówką położenia.|
|[pusty](#empty)|Sprawdza, czy zestaw jest pusty.|
|[Koniec](#end)|Zwraca iterator odnoszący się do lokalizacji następującej po ostatnim elemencie w zestawie.|
|[equal_range](#equal_range)|Zwraca parę iteratorów odpowiednio do pierwszego elementu w zestawie przy użyciu klucza, który jest większy niż określony klucz, i do pierwszego elementu w zestawie przy użyciu klucza, który jest równy lub większy niż ten klucz.|
|[wymazywanie](#erase)|Usuwa element lub zakres elementów w zestawie z określonych pozycji lub usuwa elementy, które odpowiadają określonemu kluczowi.|
|[Znajdź](#find)|Zwraca iterator odnoszący się do pierwszej lokalizacji elementu w zestawie, który ma klucz równoważny z określonym kluczem.|
|[get_allocator](#get_allocator)|Zwraca kopię `allocator` obiekt używany do utworzenia zestawu.|
|[Wstaw](#insert)|Wstawia element lub zakres elementów do zestawu.|
|[key_comp](#key_comp)|Pobiera kopię obiektu porównania użytego do uporządkowania kluczy w zestawie.|
|[lower_bound](#lower_bound)|Zwraca iterator do pierwszego elementu w zestawie, z kluczem, który jest równy lub większy od określonego klucza.|
|[max_size](#max_size)|Zwraca maksymalną długość zestawu.|
|[rbegin](#rbegin)|Zwraca iterator odnoszący się do pierwszego elementu w odwróconym zestawie.|
|[rend](#rend)|Zwraca iterator odnoszący się do lokalizacji następującej po ostatnim elemencie w odwróconym zestawie.|
|[Rozmiar](#size)|Zwraca liczbę elementów w zestawie.|
|[swap](#swap)|Zamienia elementy z dwóch zestawów.|
|[upper_bound](#upper_bound)|Zwraca iterator do pierwszego elementu w zestawie z kluczem, który jest większy od określonego klucza.|
|[value_comp](#value_comp)|Pobiera kopię obiektu porównania, użytego do uporządkowania wartości elementów w zestawie.|

### <a name="operators"></a>Operatory

|Operator|Opis|
|-|-|
|[operator=](#op_eq)|Zastępuje elementy zestawu kopią innego zestawu.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<ustawić >

**Namespace:** Standard

## <a name="allocator_type"></a>  set::allocator_type

Typ, który reprezentuje klasę alokatora dla obiekt zestawu.

```cpp
typedef Allocator allocator_type;
```

### <a name="remarks"></a>Uwagi

**allocator_type** jest synonimem parametru szablonu [alokatora](../standard-library/set-class.md).

Zwraca obiektu funkcja używaną do porządkowania jego elementów zestaw wielokrotny, który jest parametr szablonu `Allocator`.

Aby uzyskać więcej informacji na temat `Allocator`, zobacz sekcję uwag [Ustaw klasy](../standard-library/set-class.md) tematu.

### <a name="example"></a>Przykład

Zobacz przykład [get_allocator](#get_allocator) na przykład, który używa `allocator_type`.

## <a name="begin"></a>  set::BEGIN

Zwraca iterator, który dotyczy pierwszego elementu w zestawie.

```cpp
const_iterator begin() const;

iterator begin();
```

### <a name="return-value"></a>Wartość zwracana

Iterator dwukierunkowego, adresowania pierwszym elementem w zestawie lub lokalizacji pomyślne pustego zestawu.

### <a name="remarks"></a>Uwagi

Jeśli wartość zwracana **rozpocząć** jest przypisany do `const_iterator`, nie można zmodyfikować elementów w obiekcie zestawu. Jeśli wartość zwracana **rozpocząć** jest przypisany do **iterator**, elementów w obiekcie zestawu może być modyfikowany.

### <a name="example"></a>Przykład

```cpp
// set_begin.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   set <int> s1;
   set <int>::iterator s1_Iter;
   set <int>::const_iterator s1_cIter;

   s1.insert( 1 );
   s1.insert( 2 );
   s1.insert( 3 );

   s1_Iter = s1.begin( );
   cout << "The first element of s1 is " << *s1_Iter << endl;

   s1_Iter = s1.begin( );
   s1.erase( s1_Iter );

   // The following 2 lines would err because the iterator is const
   // s1_cIter = s1.begin( );
   // s1.erase( s1_cIter );

   s1_cIter = s1.begin( );
   cout << "The first element of s1 is now " << *s1_cIter << endl;
}
```

```Output
The first element of s1 is 1
The first element of s1 is now 2
```

## <a name="cbegin"></a>  set::cbegin

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

## <a name="cend"></a>  set::cend

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

## <a name="clear"></a>  set::Clear

Usuwa wszystkie elementy zestawu.

```cpp
void clear();
```

### <a name="example"></a>Przykład

```cpp
// set_clear.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   set <int> s1;

   s1.insert( 1 );
   s1.insert( 2 );

   cout << "The size of the set is initially " << s1.size( )
        << "." << endl;

   s1.clear( );
   cout << "The size of the set after clearing is "
        << s1.size( ) << "." << endl;
}
```

```Output
The size of the set is initially 2.
The size of the set after clearing is 0.
```

## <a name="const_iterator"></a>  set::const_iterator

Typ, który udostępnia iteratora dwukierunkowego, który może odczytać **const** element w zestawie.

```cpp
typedef implementation-defined const_iterator;
```

### <a name="remarks"></a>Uwagi

Typ `const_iterator` nie może służyć do modyfikowania wartości elementu.

### <a name="example"></a>Przykład

Zobacz przykład [rozpocząć](#begin) na przykład, który używa `const_iterator`.

## <a name="const_pointer"></a>  set::const_pointer

Typ, który dostarcza wskaźnik do **const** element w zestawie.

```cpp
typedef typename allocator_type::const_pointer const_pointer;
```

### <a name="remarks"></a>Uwagi

Typ `const_pointer` nie może służyć do modyfikowania wartości elementu.

W większości przypadków [const_iterator](#const_iterator) mają być używane do uzyskania dostępu do elementów w obiektu stałego zestawu.

## <a name="const_reference"></a>  set::const_reference

Typ, który zawiera odwołanie do **const** element przechowywane w zestawie do odczytu i wykonywania **const** operacji.

```cpp
typedef typename allocator_type::const_reference const_reference;
```

### <a name="example"></a>Przykład

```cpp
// set_const_ref.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   set <int> s1;

   s1.insert( 10 );
   s1.insert( 20 );

   // Declare and initialize a const_reference &Ref1
   // to the 1st element
   const int &Ref1 = *s1.begin( );

   cout << "The first element in the set is "
        << Ref1 << "." << endl;

   // The following line would cause an error because the
   // const_reference cannot be used to modify the set
   // Ref1 = Ref1 + 5;
}
```

```Output
The first element in the set is 10.
```

## <a name="const_reverse_iterator"></a>  set::const_reverse_iterator

Typ, który udostępnia iteratora dwukierunkowego, który może odczytać **const** element w zestawie.

```cpp
typedef std::reverse_iterator<const_iterator> const_reverse_iterator;
```

### <a name="remarks"></a>Uwagi

Typ `const_reverse_iterator` nie można zmodyfikować wartości elementu i umożliwia iterację zestaw odwrotnie.

### <a name="example"></a>Przykład

Zobacz przykład [rend](#rend) przykład sposobu deklarowanie i użycie `const_reverse_iterator`.

## <a name="count"></a>  set::Count

Zwraca liczbę elementów w zestawie, których klucz pasuje do klucza określonego jako parametr.

```cpp
size_type count(const Key& key) const;
```

### <a name="parameters"></a>Parametry

`key` Klucz elementu do dopasowania z zestawu.

### <a name="return-value"></a>Wartość zwracana

1, jeśli zestaw zawiera element, którego klucz sortowania pasuje do parametru klucza. 0, jeśli zestaw nie zawiera element z odpowiedniego klucza.

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca liczbę elementów w następującym zakresie:

[ `lower_bound` (_ *Klucza* ), `upper_bound` (\_ *klucza* )).

### <a name="example"></a>Przykład

W poniższym przykładzie pokazano użycie funkcji członkowskiej set::count.

```cpp
// set_count.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main()
{
    using namespace std;
    set<int> s1;
    set<int>::size_type i;

    s1.insert(1);
    s1.insert(1);

    // Keys must be unique in set, so duplicates are ignored
    i = s1.count(1);
    cout << "The number of elements in s1 with a sort key of 1 is: "
         << i << "." << endl;

    i = s1.count(2);
    cout << "The number of elements in s1 with a sort key of 2 is: "
         << i << "." << endl;
}
```

```Output
The number of elements in s1 with a sort key of 1 is: 1.
The number of elements in s1 with a sort key of 2 is: 0.
```

## <a name="crbegin"></a>  set::crbegin

Zwraca iterator const, który dotyczy pierwszego elementu w odwróconym zestawie.

```cpp
const_reverse_iterator crbegin() const;
```

### <a name="return-value"></a>Wartość zwracana

Stała wstecznego iteratora dwukierunkowego adresowania pierwszym elementem w zestawie odwróconej lub adresowania, jaki był ostatni element w zestawie stałe.

### <a name="remarks"></a>Uwagi

`crbegin` jest używany z zestawem odwróconej podobnie jak [rozpocząć](#begin) jest używany z zestawem.

Z wartością zwracaną z `crbegin`, nie można zmodyfikować obiektu zestawu.

### <a name="example"></a>Przykład

```cpp
// set_crbegin.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   set <int> s1;
   set <int>::const_reverse_iterator s1_crIter;

   s1.insert( 10 );
   s1.insert( 20 );
   s1.insert( 30 );

   s1_crIter = s1.crbegin( );
   cout << "The first element in the reversed set is "
        << *s1_crIter << "." << endl;
}
```

```Output
The first element in the reversed set is 30.
```

## <a name="crend"></a>  set::crend

Zwraca iterator const, który dotyczy lokalizacji następującej po ostatnim elemencie w odwróconym zestawie.

```cpp
const_reverse_iterator crend() const;
```

### <a name="return-value"></a>Wartość zwracana

Stała wstecznego iteratora dwukierunkowego, którego dotyczy lokalizacji pomyślne ostatnim elementem w zestawie odwróconej (lokalizacja miał przed pierwszym elementem w zestawie stałe).

### <a name="remarks"></a>Uwagi

`crend` jest używany z zestawem odwróconej podobnie jak [zakończenia](#end) jest używany z zestawem.

Z wartością zwracaną z `crend`, nie można zmodyfikować obiektu zestawu. Wartość zwrócona przez `crend` nie powinny być wyłuskiwany.

`crend` można sprawdzać, czy odwrotnej iteratora osiągnął koniec jej zestawu.

### <a name="example"></a>Przykład

```cpp
// set_crend.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main() {
   using namespace std;
   set <int> s1;
   set <int>::const_reverse_iterator s1_crIter;

   s1.insert( 10 );
   s1.insert( 20 );
   s1.insert( 30 );

   s1_crIter = s1.crend( );
   s1_crIter--;
   cout << "The last element in the reversed set is "
        << *s1_crIter << "." << endl;
}
```

## <a name="difference_type"></a>  set::difference_type

Typ liczby całkowitej ze znakiem, który może służyć do reprezentowania liczby elementów zestawu w zakresie pomiędzy elementami wskazywanymi przez iteratory.

```cpp
typedef typename allocator_type::difference_type difference_type;
```

### <a name="remarks"></a>Uwagi

`difference_type` Jest typ zwracany, gdy odjęcie lub zwiększanie za pośrednictwem Iteratory kontenera. `difference_type` Jest zwykle używana do reprezentowania liczba elementów w zakresie *[Imię, nazwisko)* między Iteratory `first` i `last`, zawiera element wskazywana przez `first` i zakresu elementy do, z wyjątkiem, element wskazywana przez `last`.

Należy pamiętać, że chociaż `difference_type` jest dostępna dla wszystkich Iteratory, które spełniają wymagania iterację wejściowy zawiera klasę Iteratory dwukierunkowego obsługiwane przez kontenery odwracalny, takich jak zestaw, odejmowania między Iteratory jest tylko obsługiwane przez Iteratory dostępie swobodnym udostępniane przez kontener dostępie swobodnym, takich jak wektorowa.

### <a name="example"></a>Przykład

```cpp
// set_diff_type.cpp
// compile with: /EHsc
#include <iostream>
#include <set>
#include <algorithm>

int main( )
{
   using namespace std;

   set <int> s1;
   set <int>::iterator s1_Iter, s1_bIter, s1_eIter;

   s1.insert( 20 );
   s1.insert( 10 );
   s1.insert( 20 );   // won't insert as set elements are unique

   s1_bIter = s1.begin( );
   s1_eIter = s1.end( );

   set <int>::difference_type   df_typ5, df_typ10, df_typ20;

   df_typ5 = count( s1_bIter, s1_eIter, 5 );
   df_typ10 = count( s1_bIter, s1_eIter, 10 );
   df_typ20 = count( s1_bIter, s1_eIter, 20 );

   // the keys, and hence the elements of a set are unique,
   // so there is at most one of a given value
   cout << "The number '5' occurs " << df_typ5
        << " times in set s1.\n";
   cout << "The number '10' occurs " << df_typ10
        << " times in set s1.\n";
   cout << "The number '20' occurs " << df_typ20
        << " times in set s1.\n";

   // count the number of elements in a set
   set <int>::difference_type  df_count = 0;
   s1_Iter = s1.begin( );
   while ( s1_Iter != s1_eIter)
   {
      df_count++;
      s1_Iter++;
   }

   cout << "The number of elements in the set s1 is: "
        << df_count << "." << endl;
}
```

```Output
The number '5' occurs 0 times in set s1.
The number '10' occurs 1 times in set s1.
The number '20' occurs 1 times in set s1.
The number of elements in the set s1 is: 2.
```

## <a name="emplace"></a>  set::emplace

Wstawia element skonstruowane w miejscu (nie ma operacji kopiowania lub przenoszenia są wykonywane).

```cpp
template <class... Args>
pair<iterator, bool>
emplace(
    Args&&... args);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|-|-|
|`args`|Argumenty przekazane do skonstruowania elementu do wstawienia do zestawu, chyba że już zawiera element, którego wartość ekwiwalentnie porządkowania.|

### <a name="return-value"></a>Wartość zwracana

A [pary](../standard-library/pair-structure.md) którego składnik bool zwraca wartość PRAWDA, jeśli dokonano wstawiania i wartość false, jeśli mapy już zawiera element, którego wartość ma odpowiadające wartości w kolejności. Składnik iteratora pary wartości zwracanej zwraca adres, gdy nowy element wstawione (Jeśli składnik wartość logiczna ma wartość true) lub którym element został już znajduje się (Jeśli składnik wartość logiczna ma wartość false).

### <a name="remarks"></a>Uwagi

Brak Iteratory lub odwołania jest nieważnych przez tę funkcję.

Podczas umieszczanie Jeśli wyjątek jest zgłaszany, stan kontenera nie jest modyfikowany.

### <a name="example"></a>Przykład

```cpp
// set_emplace.cpp
// compile with: /EHsc
#include <set>
#include <string>
#include <iostream>

using namespace std;

template <typename S> void print(const S& s) {
    cout << s.size() << " elements: ";

    for (const auto& p : s) {
        cout << "(" << p << ") ";
    }

    cout << endl;
}

int main()
{
    set<string> s1;

    auto ret = s1.emplace("ten");

    if (!ret.second){
        cout << "Emplace failed, element with value \"ten\" already exists."
            << endl << "  The existing element is (" << *ret.first << ")"
            << endl;
        cout << "set not modified" << endl;
    }
    else{
        cout << "set modified, now contains ";
        print(s1);
    }
    cout << endl;

    ret = s1.emplace("ten");

    if (!ret.second){
        cout << "Emplace failed, element with value \"ten\" already exists."
            << endl << "  The existing element is (" << *ret.first << ")"
            << endl;
    }
    else{
        cout << "set modified, now contains ";
        print(s1);
    }
    cout << endl;
}

```

## <a name="emplace_hint"></a>  set::emplace_hint

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
|`args`|Argumenty przekazane do skonstruowania elementu do wstawienia do zestawu, chyba że zestaw zawiera już ten element lub ogólnie rzecz biorąc, chyba że jest on już zawiera element, którego wartość ekwiwalentnie porządkowania.|
|`where`|Miejsce, aby rozpocząć wyszukiwanie poprawny punkt wstawiania. (Jeśli bezpośrednio przed tym punktem `where`, wstawiania może wystąpić w czasie stałej amortyzowanego, zamiast logarytmicznej czasu.)|

### <a name="return-value"></a>Wartość zwracana

Iteratora do nowo wstawiony element.

Jeśli wstawiania nie powiodła się, ponieważ istnieje już element, zwraca iteratora do istniejącego elementu.

### <a name="remarks"></a>Uwagi

Brak Iteratory lub odwołania jest nieważnych przez tę funkcję.

Podczas umieszczanie Jeśli wyjątek jest zgłaszany, stan kontenera nie jest modyfikowany.

### <a name="example"></a>Przykład

```cpp
// set_emplace.cpp
// compile with: /EHsc
#include <set>
#include <string>
#include <iostream>

using namespace std;

template <typename S> void print(const S& s) {
    cout << s.size() << " elements: " << endl;

    for (const auto& p : s) {
        cout << "(" << p <<  ") ";
    }

    cout << endl;
}

int main()
{
    set<string> s1;

    // Emplace some test data
    s1.emplace("Anna");
    s1.emplace("Bob");
    s1.emplace("Carmine");

    cout << "set starting data: ";
    print(s1);
    cout << endl;

    // Emplace with hint
    // s1.end() should be the "next" element after this emplacement
    s1.emplace_hint(s1.end(), "Doug");

    cout << "set modified, now contains ";
    print(s1);
    cout << endl;
}

```

## <a name="empty"></a>  set::Empty

Sprawdza, czy zestaw jest pusty.

```cpp
bool empty() const;
```

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli zestaw jest pusta. **false** Jeśli zestaw jest niepusty.

### <a name="example"></a>Przykład

```cpp
// set_empty.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   set <int> s1, s2;
   s1.insert ( 1 );

   if ( s1.empty( ) )
      cout << "The set s1 is empty." << endl;
   else
      cout << "The set s1 is not empty." << endl;

   if ( s2.empty( ) )
      cout << "The set s2 is empty." << endl;
   else
      cout << "The set s2 is not empty." << endl;
}
```

```Output
The set s1 is not empty.
The set s2 is empty.
```

## <a name="end"></a>  set::end

Zwraca iterator poza końcem.

```cpp
const_iterator end() const;


iterator end();
```

### <a name="return-value"></a>Wartość zwracana

Iterator przeszłości end. Jeśli zestaw jest pusta, następnie `set::end() == set::begin()`.

### <a name="remarks"></a>Uwagi

**końcowy** używany do sprawdzania, czy iteratora osiągnęła koniec jej zestawu.

Wartość zwrócona przez **zakończenia** nie powinny być wyłuskiwany.

Na przykład kod, zobacz [set::find](#find).

## <a name="equal_range"></a>  set::equal_range

Zwraca parę Iteratory odpowiednio do pierwszego elementu w zestawie przy użyciu klucza, która jest mniejsza niż określony klucz i pierwszym elementem w zestawie za pomocą klucza, która jest większa niż klucz.

```cpp
pair <const_iterator, const_iterator> equal_range (const Key& key) const;

pair <iterator, iterator> equal_range (const Key& key);
```

### <a name="parameters"></a>Parametry

`key` Klucz argumentu, który ma zostać porównane z klucza sortowania z zestawu, w którym wykonywane jest Wyszukiwanie elementu.

### <a name="return-value"></a>Wartość zwracana

Para Iteratory, w których pierwsza to [lower_bound](#lower_bound) klucz, a drugi jest [upper_bound](#upper_bound) klucza.

Pierwszy iteratora pary dostępu do `pr` zwracane przez funkcję elementu członkowskiego, użyj `pr`. **pierwszy**i aby usunąć odwołania do iteratora dolnej granicy, należy użyć \*( `pr`. **najpierw**). Drugi iteratora pary dostępu do `pr` zwracane przez funkcję elementu członkowskiego, użyj `pr`. **drugi**i aby usunąć odwołania do iteratora górnej granicy, należy użyć \*( `pr`. **drugi**).

### <a name="example"></a>Przykład

```cpp
// set_equal_range.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   typedef set<int, less< int > > IntSet;
   IntSet s1;
   set <int, less< int > > :: const_iterator s1_RcIter;

   s1.insert( 10 );
   s1.insert( 20 );
   s1.insert( 30 );

   pair <IntSet::const_iterator, IntSet::const_iterator> p1, p2;
   p1 = s1.equal_range( 20 );

   cout << "The upper bound of the element with "
        << "a key of 20 in the set s1 is: "
        << *(p1.second) << "." << endl;

   cout << "The lower bound of the element with "
        << "a key of 20 in the set s1 is: "
        << *(p1.first) << "." << endl;

   // Compare the upper_bound called directly
   s1_RcIter = s1.upper_bound( 20 );
   cout << "A direct call of upper_bound( 20 ) gives "
        << *s1_RcIter << "," << endl
        << "matching the 2nd element of the pair"
        << " returned by equal_range( 20 )." << endl;

   p2 = s1.equal_range( 40 );

   // If no match is found for the key,
   // both elements of the pair return end( )
   if ( ( p2.first == s1.end( ) ) && ( p2.second == s1.end( ) ) )
      cout << "The set s1 doesn't have an element "
           << "with a key less than 40." << endl;
   else
      cout << "The element of set s1 with a key >= 40 is: "
           << *(p1.first) << "." << endl;
}
```

```Output
The upper bound of the element with a key of 20 in the set s1 is: 30.
The lower bound of the element with a key of 20 in the set s1 is: 20.
A direct call of upper_bound( 20 ) gives 30,
matching the 2nd element of the pair returned by equal_range( 20 ).
The set s1 doesn't have an element with a key less than 40.
```

## <a name="erase"></a>  set::ERASE

Usuwa element lub zakres elementów w zestawie z określonych pozycji lub usuwa elementy, które odpowiadają określonemu kluczowi.

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

`Key` Wartość klucza elementu do usunięcia.

### <a name="return-value"></a>Wartość zwracana

Dla pierwszego funkcji dwóch elementów członkowskich iteratora dwukierunkowego który wyznacza pierwszy element pozostałych poza wszelkie elementy usunięte lub element, który nie zawiera żadnego takiego elementu sygnalizuje koniec zestawu.

Dla innych funkcji członkowskiej zwraca liczbę elementów, które zostały usunięte z zestawu.

### <a name="remarks"></a>Uwagi

### <a name="example"></a>Przykład

```cpp
// set_erase.cpp
// compile with: /EHsc
#include <set>
#include <string>
#include <iostream>
#include <iterator> // next() and prev() helper functions

using namespace std;

using myset = set<string>;

void printset(const myset& s) {
    for (const auto& iter : s) {
        cout << " [" << iter << "]";
    }
    cout << endl << "size() == " << s.size() << endl << endl;
}

int main()
{
    myset s1;

    // Fill in some data to test with, one at a time
    s1.insert("Bob");
    s1.insert("Robert");
    s1.insert("Bert");
    s1.insert("Rob");
    s1.insert("Bobby");

    cout << "Starting data of set s1 is:" << endl;
    printset(s1);
    // The 1st member function removes an element at a given position
    s1.erase(next(s1.begin()));
    cout << "After the 2nd element is deleted, the set s1 is:" << endl;
    printset(s1);

    // Fill in some data to test with, one at a time, using an intializer list
    myset s2{ "meow", "hiss", "purr", "growl", "yowl" };

    cout << "Starting data of set s2 is:" << endl;
    printset(s2);
    // The 2nd member function removes elements
    // in the range [First, Last)
    s2.erase(next(s2.begin()), prev(s2.end()));
    cout << "After the middle elements are deleted, the set s2 is:" << endl;
    printset(s2);

    myset s3;

    // Fill in some data to test with, one at a time, using emplace
    s3.emplace("C");
    s3.emplace("C#");
    s3.emplace("D");
    s3.emplace("D#");
    s3.emplace("E");
    s3.emplace("E#");
    s3.emplace("F");
    s3.emplace("F#");
    s3.emplace("G");
    s3.emplace("G#");
    s3.emplace("A");
    s3.emplace("A#");
    s3.emplace("B");

    cout << "Starting data of set s3 is:" << endl;
    printset(s3);
    // The 3rd member function removes elements with a given Key
    myset::size_type count = s3.erase("E#");
    // The 3rd member function also returns the number of elements removed
    cout << "The number of elements removed from s3 is: " << count << "." << endl;
    cout << "After the element with a key of \"E#\" is deleted, the set s3 is:" << endl;
    printset(s3);
}

```

## <a name="find"></a>  set::Find

Zwraca iteratora odnoszący się do lokalizacji elementu w zestawie, który ma klucz równoważne z określonym kluczem.

```cpp
iterator find(const Key& key);


const_iterator find(const Key& key) const;
```

### <a name="parameters"></a>Parametry

`key` Wartość klucza do dopasowania za pomocą klucza sortowania z zestawu, w którym wykonywane jest Wyszukiwanie elementu.

### <a name="return-value"></a>Wartość zwracana

Iteratora odnoszący się do lokalizacji element z określonym kluczem lub lokalizacji pomyślne ostatnim elementem w zestawie ( `set::end()`) Jeśli nie znaleziono klucza.

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca iteratora odnoszący się do elementu w zestawie, którego klucz jest równoważne argumentowi `key` w obszarze binarny predykatu wywołujące kolejność oparte na mniej niż porównywalności relacji.

Jeśli wartość zwracana **znaleźć** jest przypisany do **const_iterator**, nie można zmodyfikować obiektu zestawu. Jeśli wartość zwracana **znaleźć** jest przypisany do **iterator**, można zmodyfikować obiektu zestawu

### <a name="example"></a>Przykład

```cpp
// compile with: /EHsc /W4 /MTd
#include <set>
#include <iostream>
#include <vector>
#include <string>

using namespace std;

template <typename T> void print_elem(const T& t) {
    cout << "(" << t << ") ";
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
    set<int> s1({ 40, 45 });
    cout << "The starting set s1 is: " << endl;
    print_collection(s1);

    vector<int> v;
    v.push_back(43);
    v.push_back(41);
    v.push_back(46);
    v.push_back(42);
    v.push_back(44);
    v.push_back(44); // attempt a duplicate

    cout << "Inserting the following vector data into s1: " << endl;
    print_collection(v);

    s1.insert(v.begin(), v.end());

    cout << "The modified set s1 is: " << endl;
    print_collection(s1);
    cout << endl;
    findit(s1, 45);
    findit(s1, 6);
}

```

## <a name="get_allocator"></a>  set::get_allocator

Zwraca kopię obiektu alokatora użyty do utworzenia zestawu.

```cpp
allocator_type get_allocator() const;
```

### <a name="return-value"></a>Wartość zwracana

Program przydzielania używane przez zestaw do zarządzania pamięci, która jest parametr szablonu `Allocator`.

Aby uzyskać więcej informacji na temat `Allocator`, zobacz sekcję uwag [Ustaw klasy](../standard-library/set-class.md) tematu.

### <a name="remarks"></a>Uwagi

Allocators — dla klasy zestawu Określ zarządzaniu klasę magazynu. Allocators — domyślna dostarczony wraz z klasy kontenerów standardowa biblioteka C++ wystarcza w wielu zastosowaniach programowania. Pisanie i przy użyciu klasy alokatora jest temat zaawansowany C++.

### <a name="example"></a>Przykład

```cpp
// set_get_allocator.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   set <int>::allocator_type s1_Alloc;
   set <int>::allocator_type s2_Alloc;
   set <double>::allocator_type s3_Alloc;
   set <int>::allocator_type s4_Alloc;

   // The following lines declare objects
   // that use the default allocator.
   set <int> s1;
   set <int, allocator<int> > s2;
   set <double, allocator<double> > s3;

   s1_Alloc = s1.get_allocator( );
   s2_Alloc = s2.get_allocator( );
   s3_Alloc = s3.get_allocator( );

   cout << "The number of integers that can be allocated"
        << endl << "before free memory is exhausted: "
        << s2.max_size( ) << "." << endl;

   cout << "\nThe number of doubles that can be allocated"
        << endl << "before free memory is exhausted: "
        << s3.max_size( ) <<  "." << endl;

   // The following line creates a set s4
   // with the allocator of multiset s1.
   set <int> s4( less<int>( ), s1_Alloc );

   s4_Alloc = s4.get_allocator( );

   // Two allocators are interchangeable if
   // storage allocated from each can be
   // deallocated by the other
   if( s1_Alloc == s4_Alloc )
   {
      cout << "\nThe allocators are interchangeable."
           << endl;
   }
   else
   {
      cout << "\nThe allocators are not interchangeable."
           << endl;
   }
}
```

## <a name="insert"></a>  set::INSERT

Wstawia element lub zakres elementów do zestawu.

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
|`Val`|Wartość elementu do wstawienia do zestawu, chyba że już zawiera element, którego wartość ekwiwalentnie porządkowania.|
|`Where`|Miejsce, aby rozpocząć wyszukiwanie poprawny punkt wstawiania. (Jeśli bezpośrednio przed tym punktem `Where`, wstawiania może wystąpić w czasie stałej amortyzowanego, zamiast logarytmicznej czasu.)|
|`ValTy`|Parametr szablonu, który określa typ argumentu, który zestaw można używać do tworzenia elementu [value_type](../standard-library/map-class.md#value_type), a idealnych przekazuje `Val` jako argument.|
|`First`|Pozycja pierwszego elementu do skopiowania.|
|`Last`|Pozycja poza ostatni element do skopiowania.|
|`InputIterator`|Argument funkcji szablonu, który spełnia wymagania [wejściowych iteratora](../standard-library/input-iterator-tag-struct.md) wskazującego elementów typu, który może służyć do utworzenia [value_type](../standard-library/map-class.md#value_type) obiektów.|
|`IList`|[Initializer_list](../standard-library/initializer-list.md) z którego można skopiować elementów.|

### <a name="return-value"></a>Wartość zwracana

Funkcje Członkowskie pojedynczego elementu (1) i (2) zwracają [pary](../standard-library/pair-structure.md) którego `bool` składnika ma wartość true, jeśli dokonano wstawiania i wartość false, jeśli zestaw zawierają już element o równoważnej wartości w kolejności. Składnik iteratora pary wartość zwracaną wskazuje element nowo wstawionej Jeśli `bool` składnik jest wartość PRAWDA lub do istniejącego elementu Jeśli `bool` składników ma wartość false.

Funkcje Członkowskie pojedynczego elementu z wskazówki, (3) i (4) zwraca iteratora wskazującą położenie w przypadku, gdy nowy element została umieszczona w zestawie lub, jeśli element z kluczem odpowiednik już istnieje, do istniejącego elementu.

### <a name="remarks"></a>Uwagi

Nie Iteratory, wskaźniki lub odwołania jest nieważnych przez tę funkcję.

Podczas wstawiania tylko jednego elementu jeśli wyjątek jest zgłaszany, stan kontenera nie jest modyfikowany. Podczas wstawiania wiele elementów jeśli wyjątek kontenera pozostaje w stanie nieokreślony, ale prawidłowy.

Aby uzyskać dostęp do składnika iteratora `pair` `pr` który jest zwracany za pomocą funkcji pojedynczego elementu członkowskiego, użyj `pr.first`; aby wyłuskania iteratora w pary zwrócone, użyj `*pr.first`, umożliwiając elementu. Aby uzyskać dostęp do `bool` składnika, użyj `pr.second`. Na przykład zobacz przykładowy kod w dalszej części tego artykułu.

[Value_type](../standard-library/map-class.md#value_type) kontenera jest element typedef, który należy do kontenera i zestawu `set<V>::value_type` jest typem `const V`.

Zakres funkcji członkowskiej (5) wstawia sekwencji wartości elementów do zestawu, który odpowiada każdy element dotyczy iterację w zakresie `[First, Last)`; w związku z tym `Last` nie Pobierz wstawione. Funkcja członkowska kontenera `end()` odwołuje się do położenia zaraz po ostatnim elementem w kontenerze — na przykład instrukcja `s.insert(v.begin(), v.end());` próba wstawienia wszystkie elementy `v` do `s`. Tylko elementy, które mają unikatowe wartości w zakresie są wstawiane; duplikaty są ignorowane. Aby sprawdzić, które elementy zostały odrzucone, użyj wersji pojedynczego elementu `insert`.

(6) używa funkcji członkowskiej liście inicjatorów [initializer_list](../standard-library/initializer-list.md) można skopiować elementów do zestawu.

Do wstawienia elementu w miejscu skonstruować — to znaczy są wykonywane żadne operacje kopiowania lub przenoszenia — zobacz [set::emplace](#emplace) i [set::emplace_hint](#emplace_hint).

### <a name="example"></a>Przykład

```cpp
// set_insert.cpp
// compile with: /EHsc
#include <set>
#include <iostream>
#include <string>
#include <vector>

using namespace std;

template <typename S> void print(const S& s) {
    cout << s.size() << " elements: ";

    for (const auto& p : s) {
        cout << "(" << p << ") ";
    }

    cout << endl;
}

int main()
{

    // insert single values
    set<int> s1;
    // call insert(const value_type&) version
    s1.insert({ 1, 10 });
    // call insert(ValTy&&) version
    s1.insert(20);

    cout << "The original set values of s1 are:" << endl;
    print(s1);

    // intentionally attempt a duplicate, single element
    auto ret = s1.insert(1);
    if (!ret.second){
        auto elem = *ret.first;
        cout << "Insert failed, element with value 1 already exists."
            << endl << "  The existing element is (" << elem << ")"
            << endl;
    }
    else{
        cout << "The modified set values of s1 are:" << endl;
        print(s1);
    }
    cout << endl;

    // single element, with hint
    s1.insert(s1.end(), 30);
    cout << "The modified set values of s1 are:" << endl;
    print(s1);
    cout << endl;

    // The templatized version inserting a jumbled range
    set<int> s2;
    vector<int> v;
    v.push_back(43);
    v.push_back(294);
    v.push_back(41);
    v.push_back(330);
    v.push_back(42);
    v.push_back(45);

    cout << "Inserting the following vector data into s2:" << endl;
    print(v);

    s2.insert(v.begin(), v.end());

    cout << "The modified set values of s2 are:" << endl;
    print(s2);
    cout << endl;

    // The templatized versions move-constructing elements
    set<string>  s3;
    string str1("blue"), str2("green");

    // single element
    s3.insert(move(str1));
    cout << "After the first move insertion, s3 contains:" << endl;
    print(s3);

    // single element with hint
    s3.insert(s3.end(), move(str2));
    cout << "After the second move insertion, s3 contains:" << endl;
    print(s3);
    cout << endl;

    set<int> s4;
    // Insert the elements from an initializer_list
    s4.insert({ 4, 44, 2, 22, 3, 33, 1, 11, 5, 55 });
    cout << "After initializer_list insertion, s4 contains:" << endl;
    print(s4);
    cout << endl;
}

```

## <a name="iterator"></a>  set::iterator

Typ, który zapewnia stałą [iteratora dwukierunkowego](../standard-library/bidirectional-iterator-tag-struct.md) który może odczytywać dowolny element w zestawie.

```cpp
typedef implementation-defined iterator;
```

### <a name="example"></a>Przykład

Zobacz przykład [rozpocząć](#begin) przykład sposobu deklarowanie i użycie **iterator**.

## <a name="key_comp"></a>  set::key_comp

Pobiera kopię obiektu porównania użytego do uporządkowania kluczy w zestawie.

```cpp
key_compare key_comp() const;
```

### <a name="return-value"></a>Wartość zwracana

Zwraca obiekt funkcji, który używa zestawu do porządkowania jego elementów, czyli parametru szablonu `Traits`.

Aby uzyskać więcej informacji na temat `Traits` zobacz [Ustaw klasy](../standard-library/set-class.md) tematu.

### <a name="remarks"></a>Uwagi

Obiekt przechowywanych definiuje funkcję elementu członkowskiego:

**bool operator()**( **const klucza &**`_xVal`, **const klucza &**`_yVal`);

która zwraca **true** Jeśli `_xVal` poprzedza i nie jest równa `_yVal` w kolejności sortowania.

Należy pamiętać, że oba [key_compare](#key_compare) i [value_compare](#value_compare) są synonimy dla parametru szablonu **cech**. Oba typy są dostępne dla zestawu i zestawów wielokrotnych klas, gdy są identyczne, aby zapewnić zgodność z mapy i klasy multimap — gdy są różne.

### <a name="example"></a>Przykład

```cpp
// set_key_comp.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;

   set <int, less<int> > s1;
   set<int, less<int> >::key_compare kc1 = s1.key_comp( ) ;
   bool result1 = kc1( 2, 3 ) ;
   if( result1 == true )
   {
      cout << "kc1( 2,3 ) returns value of true, "
           << "where kc1 is the function object of s1."
           << endl;
   }
   else
   {
      cout << "kc1( 2,3 ) returns value of false "
           << "where kc1 is the function object of s1."
           << endl;
   }

   set <int, greater<int> > s2;
   set<int, greater<int> >::key_compare kc2 = s2.key_comp( ) ;
   bool result2 = kc2( 2, 3 ) ;
   if(result2 == true)
   {
      cout << "kc2( 2,3 ) returns value of true, "
           << "where kc2 is the function object of s2."
           << endl;
   }
   else
   {
      cout << "kc2( 2,3 ) returns value of false, "
           << "where kc2 is the function object of s2."
           << endl;
   }
}
```

```Output
kc1( 2,3 ) returns value of true, where kc1 is the function object of s1.
kc2( 2,3 ) returns value of false, where kc2 is the function object of s2.
```

## <a name="key_compare"></a>  set::key_compare

Typ, który dostarcza obiekt funkcji, która może porównać dwa klucze sortowania, aby określić względną kolejność dwóch elementów w zestawie.

```cpp
typedef Traits key_compare;
```

### <a name="remarks"></a>Uwagi

`key_compare` synonim parametru szablonu jest `Traits`.

Aby uzyskać więcej informacji na temat `Traits` zobacz [Ustaw klasy](../standard-library/set-class.md) tematu.

Należy pamiętać, że oba `key_compare` i [value_compare](#value_compare) są synonimy dla parametru szablonu **cech**. Oba typy są dostępne dla zestawu i zestawów wielokrotnych klas, gdy są identyczne, aby zapewnić zgodność z mapy i klasy multimap — gdy są różne.

### <a name="example"></a>Przykład

Zobacz przykład [key_comp](#key_comp) przykład sposobu deklarowanie i użycie `key_compare`.

## <a name="key_type"></a>  set::key_type

Typ, który opisuje obiekt zapisany jako elementu zestawu w charakterze klucza sortowania.

```cpp
typedef Key key_type;
```

### <a name="remarks"></a>Uwagi

`key_type` synonim parametru szablonu jest `Key`.

Aby uzyskać więcej informacji na temat `Key`, zobacz sekcję uwag [Ustaw klasy](../standard-library/set-class.md) tematu.

Należy pamiętać, że oba `key_type` i [value_type](#value_type) są synonimy dla parametru szablonu **klucza**. Oba typy są dostępne dla zestawu i zestawów wielokrotnych klas, gdy są identyczne, aby zapewnić zgodność z mapy i klasy multimap — gdy są różne.

### <a name="example"></a>Przykład

Zobacz przykład [value_type](#value_type) przykład sposobu deklarowanie i użycie `key_type`.

## <a name="lower_bound"></a>  set::lower_bound

Zwraca iterator do pierwszego elementu w zestawie, z kluczem, który jest równy lub większy od określonego klucza.

```cpp
const_iterator lower_bound(const Key& key) const;

iterator lower_bound(const Key& key);
```

### <a name="parameters"></a>Parametry

`key` Klucz argumentu, który ma zostać porównane z klucza sortowania z zestawu, w którym wykonywane jest Wyszukiwanie elementu.

### <a name="return-value"></a>Wartość zwracana

Iterator lub `const_iterator` czy adresy lokalizacji elementu w zestawie, że za pomocą klucza, która jest równa lub większa niż klucz argumentu lub który adresów lokalizacji pomyślne ostatnim elementem w zestawie, jeśli nie są zgodne znajduje się dla klucza.

### <a name="example"></a>Przykład

```cpp
// set_lower_bound.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   set <int> s1;
   set <int> :: const_iterator s1_AcIter, s1_RcIter;

   s1.insert( 10 );
   s1.insert( 20 );
   s1.insert( 30 );

   s1_RcIter = s1.lower_bound( 20 );
   cout << "The element of set s1 with a key of 20 is: "
        << *s1_RcIter << "." << endl;

   s1_RcIter = s1.lower_bound( 40 );

   // If no match is found for the key, end( ) is returned
   if ( s1_RcIter == s1.end( ) )
      cout << "The set s1 doesn't have an element "
           << "with a key of 40." << endl;
   else
      cout << "The element of set s1 with a key of 40 is: "
           << *s1_RcIter << "." << endl;

   // The element at a specific location in the set can be found
   // by using a dereferenced iterator that addresses the location
   s1_AcIter = s1.end( );
   s1_AcIter--;
   s1_RcIter = s1.lower_bound( *s1_AcIter );
   cout << "The element of s1 with a key matching "
        << "that of the last element is: "
        << *s1_RcIter << "." << endl;
}
```

```Output
The element of set s1 with a key of 20 is: 20.
The set s1 doesn't have an element with a key of 40.
The element of s1 with a key matching that of the last element is: 30.
```

## <a name="max_size"></a>  set::max_size

Zwraca maksymalną długość zestawu.

```cpp
size_type max_size() const;
```

### <a name="return-value"></a>Wartość zwracana

Maksymalna długość możliwe zestawu.

### <a name="example"></a>Przykład

```cpp
// set_max_size.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   set <int> s1;
   set <int>::size_type i;

   i = s1.max_size( );
   cout << "The maximum possible length "
        << "of the set is " << i << "." << endl;
}
```

## <a name="op_eq"></a>  set::operator =

Zastępuje elementy to `set` za pomocą elementów z innej `set`.

```cpp
set& operator=(const set& right);

set& operator=(set&& right);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|-|-|
|`right`|`set` Dostarczanie nowych elementów do przypisania do tego `set`.|

### <a name="remarks"></a>Uwagi

Pierwszą wersję `operator=` używa [odwołania do wartości](../cpp/lvalue-reference-declarator-amp.md) dla `right`, aby skopiować elementy z `right` tej `set`.

Druga wersja używa [odwołania do wartości](../cpp/rvalue-reference-declarator-amp-amp.md) w prawo. Powoduje przeniesienie elementy z `right` tej `set`.

Wszystkie elementy w tym `set` przed wykonaniem funkcji operatora zostaną odrzucone.

### <a name="example"></a>Przykład

```cpp
// set_operator_as.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
   {
   using namespace std;
   set<int> v1, v2, v3;
   set<int>::iterator iter;

   v1.insert(10);

   cout << "v1 = " ;
   for (iter = v1.begin(); iter != v1.end(); iter++)
      cout << *iter << " ";
   cout << endl;

   v2 = v1;
   cout << "v2 = ";
   for (iter = v2.begin(); iter != v2.end(); iter++)
      cout << *iter << " ";
   cout << endl;

// move v1 into v2
   v2.clear();
   v2 = move(v1);
   cout << "v2 = ";
   for (iter = v2.begin(); iter != v2.end(); iter++)
      cout << *iter << " ";
   cout << endl;
   }
```

## <a name="pointer"></a>  set::Pointer

Typ, który dostarcza wskaźnik do elementu w zestawie.

```cpp
typedef typename allocator_type::pointer pointer;
```

### <a name="remarks"></a>Uwagi

Typ **wskaźnika** może służyć do modyfikowania wartości elementu.

W większości przypadków [iterator](#iterator) mają być używane do uzyskania dostępu do elementów w obiekcie zestawu.

## <a name="rbegin"></a>  set::rbegin

Zwraca iterator odnoszący się do pierwszego elementu w odwróconym zestawie.

```cpp
const_reverse_iterator rbegin() const;

reverse_iterator rbegin();
```

### <a name="return-value"></a>Wartość zwracana

Iterator odwrotnej dwukierunkowego adresowania pierwszym elementem w zestawie odwróconej lub adresowania, jaki był ostatni element w zestawie stałe.

### <a name="remarks"></a>Uwagi

`rbegin` jest używany z zestawem odwróconej podobnie jak [rozpocząć](#begin) jest używany z zestawem.

Jeśli wartość zwracana `rbegin` jest przypisany do `const_reverse_iterator`, a następnie obiektu zestawu nie może być modyfikowany. Jeśli wartość zwracana `rbegin` jest przypisany do `reverse_iterator`, a następnie można zmodyfikować obiektu zestawu.

`rbegin` może służyć do zapewnienia iteracji w zestawie.

### <a name="example"></a>Przykład

```cpp
// set_rbegin.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   set <int> s1;
   set <int>::iterator s1_Iter;
   set <int>::reverse_iterator s1_rIter;

   s1.insert( 10 );
   s1.insert( 20 );
   s1.insert( 30 );

   s1_rIter = s1.rbegin( );
   cout << "The first element in the reversed set is "
        << *s1_rIter << "." << endl;

   // begin can be used to start an iteration
   // throught a set in a forward order
   cout << "The set is:";
   for ( s1_Iter = s1.begin( ) ; s1_Iter != s1.end( ); s1_Iter++ )
      cout << " " << *s1_Iter;
   cout << endl;

   // rbegin can be used to start an iteration
   // throught a set in a reverse order
   cout << "The reversed set is:";
   for ( s1_rIter = s1.rbegin( ) ; s1_rIter != s1.rend( ); s1_rIter++ )
      cout << " " << *s1_rIter;
   cout << endl;

   // A set element can be erased by dereferencing to its key
   s1_rIter = s1.rbegin( );
   s1.erase ( *s1_rIter );

   s1_rIter = s1.rbegin( );
   cout << "After the erasure, the first element "
        << "in the reversed set is "<< *s1_rIter << "." << endl;
}
```

```Output
The first element in the reversed set is 30.
The set is: 10 20 30
The reversed set is: 30 20 10
After the erasure, the first element in the reversed set is 20.
```

## <a name="reference"></a>  set::Reference

Typ, który zawiera odwołanie do elementu przechowywanego w zestawie.

```cpp
typedef typename allocator_type::reference reference;
```

### <a name="example"></a>Przykład

```cpp
// set_reference.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   set <int> s1;

   s1.insert( 10 );
   s1.insert( 20 );

   // Declare and initialize a reference &Ref1 to the 1st element
   const int &Ref1 = *s1.begin( );

   cout << "The first element in the set is "
        << Ref1 << "." << endl;
}
```

```Output
The first element in the set is 10.
```

## <a name="rend"></a>  set::rend

Zwraca iterator odnoszący się do lokalizacji następującej po ostatnim elemencie w odwróconym zestawie.

```cpp
const_reverse_iterator rend() const;

reverse_iterator rend();
```

### <a name="return-value"></a>Wartość zwracana

Iterator odwrotnej dwukierunkowego, którego dotyczy lokalizacji pomyślne ostatnim elementem w zestawie odwróconej (lokalizacja miał przed pierwszym elementem w zestawie stałe).

### <a name="remarks"></a>Uwagi

`rend` jest używany z zestawem odwróconej podobnie jak [zakończenia](#end) jest używany z zestawem.

Jeśli wartość zwracana `rend` jest przypisany do `const_reverse_iterator`, a następnie obiektu zestawu nie może być modyfikowany. Jeśli wartość zwracana `rend` jest przypisany do `reverse_iterator`, a następnie można zmodyfikować obiektu zestawu. Wartość zwrócona przez `rend` nie powinny być wyłuskiwany.

`rend` można sprawdzać, czy odwrotnej iteratora osiągnął koniec jej zestawu.

### <a name="example"></a>Przykład

```cpp
// set_rend.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main() {
   using namespace std;
   set <int> s1;
   set <int>::iterator s1_Iter;
   set <int>::reverse_iterator s1_rIter;
   set <int>::const_reverse_iterator s1_crIter;

   s1.insert( 10 );
   s1.insert( 20 );
   s1.insert( 30 );

   s1_rIter = s1.rend( );
   s1_rIter--;
   cout << "The last element in the reversed set is "
        << *s1_rIter << "." << endl;

   // end can be used to terminate an iteration
   // throught a set in a forward order
   cout << "The set is: ";
   for ( s1_Iter = s1.begin( ) ; s1_Iter != s1.end( ); s1_Iter++ )
      cout << *s1_Iter << " ";
   cout << "." << endl;

   // rend can be used to terminate an iteration
   // throught a set in a reverse order
   cout << "The reversed set is: ";
   for ( s1_rIter = s1.rbegin( ) ; s1_rIter != s1.rend( ); s1_rIter++ )
      cout << *s1_rIter << " ";
   cout << "." << endl;

   s1_rIter = s1.rend( );
   s1_rIter--;
   s1.erase ( *s1_rIter );

   s1_rIter = s1.rend( );
   --s1_rIter;
   cout << "After the erasure, the last element in the "
        << "reversed set is " << *s1_rIter << "." << endl;
}
```

## <a name="reverse_iterator"></a>  set::reverse_iterator

Typ, który dostarcza iterator dwukierunkowy do odczytu i modyfikacji elementu w odwróconym zestawie.

```cpp
typedef std::reverse_iterator<iterator> reverse_iterator;
```

### <a name="remarks"></a>Uwagi

Typ `reverse_iterator` umożliwia iterację zestaw odwrotnie.

### <a name="example"></a>Przykład

Zobacz przykład [rbegin](#rbegin) przykład sposobu deklarowanie i użycie `reverse_iterator`.

## <a name="set"></a>  set::set

Konstruuje zestaw, który jest pusty lub jest kopią całości lub części innego zestawu.

```cpp
set();

explicit set(
    const Traits& Comp);

set(
    const Traits& Comp,
    const Allocator& Al);

set(
    const set& Right);

set(
    set&& Right);

set(
    initializer_list<Type> IList);

set(
    initializer_list<Type> IList,
    const Compare& Comp);

set(
    initializer_list<Type> IList,
    const Compare& Comp,
    const Allocator& Al);


template <class InputIterator>
set(
 InputIterator First,
    InputIterator Last);

template <class InputIterator>
set(
 InputIterator First,
    InputIterator Last,
    const Traits& Comp);

template <class InputIterator>
set(
 InputIterator First,
    InputIterator Last,
    const Traits& Comp,
    const Allocator& Al);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|-|-|
|`Al`|Klasa przydzielania magazynu do użycia dla tego obiektu zestawu, który domyślnie **alokatora**.|
|`Comp`|Funkcja porównywania typu `const Traits` porządkowania elementów w zestawie, która domyślnie określa `Compare`.|
|`Rght`|Zestaw skonstruowane zestawu ma być kopii.|
|`First`|Pozycja pierwszego elementu w zakresie elementów do skopiowania.|
|`Last`|Pozycja pierwszego elementu poza zakres elementów do skopiowania.|
|`IList`|Lista initializer_list, z której mają być skopiowane elementy.|

### <a name="remarks"></a>Uwagi

Typ obiektu przydzielania, który zarządza przechowywania w pamięci dla zestawu i że później może być zwracany przez wywołanie metody przechowywania wszystkie konstruktory [get_allocator](#get_allocator). Parametr przydzielania jest często pomijany w deklaracjach klas i przetwarzania wstępnego makra używany do zastąpienia alternatywnych allocators —.

Wszystkie konstruktory zainicjować ich zestawów.

Wszystkie konstruktory przechowywania obiektem funkcji typu **cech** używany do ustanawiania zamówienia wśród kluczy zestawu i że później może być zwracany przez wywołanie metody [key_comp](#key_comp).

Pierwsze trzy konstruktorów Określ pusty zestaw początkowy, drugi określający typ porównania funkcji ( `comp`) do użycia w ustalaniu kolejności elementów i trzeci jawne określenie programu przydzielania wpisz ( `al`) jako używane. Słowo kluczowe **jawne** pomija określonych rodzajów typu automatycznej konwersji.

Konstruktor czwarty Określa kopię zestawu `right`.

Konstruktory trzech kolejnych Użyj initializer_list, aby określić elementy.

Konstruktory trzech kolejnych skopiuj zakres [ `first`, `last`) zestawu z rosnącym explicitness określania typu porównanie funkcji klasy **cech** i **alokatora**.

Konstruktor ósmego Określa kopię zestawu przez przeniesienie `right`.

### <a name="example"></a>Przykład

```cpp
// set_set.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main()
{
    using namespace std;

    // Create an empty set s0 of key type integer
    set <int> s0;

    // Create an empty set s1 with the key comparison
    // function of less than, then insert 4 elements
    set <int, less<int> > s1;
    s1.insert(10);
    s1.insert(20);
    s1.insert(30);
    s1.insert(40);

    // Create an empty set s2 with the key comparison
    // function of less than, then insert 2 elements
    set <int, less<int> > s2;
    s2.insert(10);
    s2.insert(20);

    // Create a set s3 with the
    // allocator of set s1
    set <int>::allocator_type s1_Alloc;
    s1_Alloc = s1.get_allocator();
    set <int> s3(less<int>(), s1_Alloc);
    s3.insert(30);

    // Create a copy, set s4, of set s1
    set <int> s4(s1);

    // Create a set s5 by copying the range s1[ first,  last)
    set <int>::const_iterator s1_bcIter, s1_ecIter;
    s1_bcIter = s1.begin();
    s1_ecIter = s1.begin();
    s1_ecIter++;
    s1_ecIter++;
    set <int> s5(s1_bcIter, s1_ecIter);

    // Create a set s6 by copying the range s4[ first,  last)
    // and with the allocator of set s2
    set <int>::allocator_type s2_Alloc;
    s2_Alloc = s2.get_allocator();
    set <int> s6(s4.begin(), ++s4.begin(), less<int>(), s2_Alloc);

    cout << "s1 =";
    for (auto i : s1)
        cout << " " << i;
    cout << endl;

    cout << "s2 = " << *s2.begin() << " " << *++s2.begin() << endl;

    cout << "s3 =";
    for (auto i : s3)
        cout << " " << i;
    cout << endl;

    cout << "s4 =";
    for (auto i : s4)
        cout << " " << i;
    cout << endl;

    cout << "s5 =";
    for (auto i : s5)
        cout << " " << i;
    cout << endl;

    cout << "s6 =";
    for (auto i : s6)
        cout << " " << i;
    cout << endl;

    // Create a set by moving s5
    set<int> s7(move(s5));
    cout << "s7 =";
    for (auto i : s7)
        cout << " " << i;
    cout << endl;

    // Create a set with an initializer_list
    cout << "s8 =";
    set<int> s8{ { 1, 2, 3, 4 } };
    for (auto i : s8)
        cout << " " << i;
    cout << endl;

    cout << "s9 =";
    set<int> s9{ { 5, 6, 7, 8 }, less<int>() };
    for (auto i : s9)
        cout << " " << i;
    cout << endl;

    cout << "s10 =";
    set<int> s10{ { 10, 20, 30, 40 }, less<int>(), s9.get_allocator() };
    for (auto i : s10)
        cout << " " << i;
    cout << endl;
}

```

```Output
s1 = 10 20 30 40s2 = 10 20s3 = 30s4 = 10 20 30 40s5 = 10 20s6 = 10s7 = 10 20s8 = 1 2 3 4s9 = 5 6 7 8s10 = 10 20 30 40
```

## <a name="size"></a>  set::size

Zwraca liczbę elementów w zestawie.

```cpp
size_type size() const;
```

### <a name="return-value"></a>Wartość zwracana

Bieżąca długość zestawu.

### <a name="example"></a>Przykład

```cpp
// set_size.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   set <int> s1;
   set <int> :: size_type i;

   s1.insert( 1 );
   i = s1.size( );
   cout << "The set length is " << i << "." << endl;

   s1.insert( 2 );
   i = s1.size( );
   cout << "The set length is now " << i << "." << endl;
}
```

```Output
The set length is 1.
The set length is now 2.
```

## <a name="size_type"></a>  set::size_type

Typ całkowitoliczbowy bez znaku, który może reprezentować liczbę elementów w zestawie.

```cpp
typedef typename allocator_type::size_type size_type;
```

### <a name="example"></a>Przykład

Zobacz przykład [rozmiar](#size) przykład sposobu deklarowanie i użycie `size_type`

## <a name="swap"></a>  set::swap

Zamienia elementy z dwóch zestawów.

```cpp
void swap(
    set<Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parametry

`right` Ustaw argument ustawić dostarczanie elementy zamianę z elementem docelowym.

### <a name="remarks"></a>Uwagi

Funkcja członkowska unieważnia nie odwołań, wskaźniki lub Iteratory, które określają elementów w dwóch zestawów, której elementy są wymieniane.

### <a name="example"></a>Przykład

```cpp
// set_swap.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   set <int> s1, s2, s3;
   set <int>::iterator s1_Iter;

   s1.insert( 10 );
   s1.insert( 20 );
   s1.insert( 30 );
   s2.insert( 100 );
   s2.insert( 200 );
   s3.insert( 300 );

   cout << "The original set s1 is:";
   for ( s1_Iter = s1.begin( ); s1_Iter != s1.end( ); s1_Iter++ )
      cout << " " << *s1_Iter;
   cout   << "." << endl;

   // This is the member function version of swap
   s1.swap( s2 );

   cout << "After swapping with s2, list s1 is:";
   for ( s1_Iter = s1.begin( ); s1_Iter != s1.end( ); s1_Iter++ )
      cout << " " << *s1_Iter;
   cout  << "." << endl;

   // This is the specialized template version of swap
   swap( s1, s3 );

   cout << "After swapping with s3, list s1 is:";
   for ( s1_Iter = s1.begin( ); s1_Iter != s1.end( ); s1_Iter++ )
      cout << " " << *s1_Iter;
   cout   << "." << endl;
}
```

```Output
The original set s1 is: 10 20 30.
After swapping with s2, list s1 is: 100 200.
After swapping with s3, list s1 is: 300.
```

## <a name="upper_bound"></a>  set::upper_bound

Zwraca iteratora pierwszy element w zestawie który za pomocą klucza, który jest większy niż określony klucz.

```cpp
const_iterator upper_bound(const Key& key) const;

iterator upper_bound(const Key& key);
```

### <a name="parameters"></a>Parametry

`key` Klucz argumentu, który ma zostać porównane z klucza sortowania z zestawu, w którym wykonywane jest Wyszukiwanie elementu.

### <a name="return-value"></a>Wartość zwracana

**Iterator** lub `const_iterator` czy adresy lokalizacji elementu w zestawie, że za pomocą klucza jest większa niż klucz argumentu, lub że adresów lokalizacji pomyślne ostatnim elementem w zestawie, jeśli nie są zgodne znajduje się dla klucza.

### <a name="example"></a>Przykład

```cpp
// set_upper_bound.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   set <int> s1;
   set <int> :: const_iterator s1_AcIter, s1_RcIter;

   s1.insert( 10 );
   s1.insert( 20 );
   s1.insert( 30 );

   s1_RcIter = s1.upper_bound( 20 );
   cout << "The first element of set s1 with a key greater "
        << "than 20 is: " << *s1_RcIter << "." << endl;

   s1_RcIter = s1.upper_bound( 30 );

   // If no match is found for the key, end( ) is returned
   if ( s1_RcIter == s1.end( ) )
      cout << "The set s1 doesn't have an element "
           << "with a key greater than 30." << endl;
   else
      cout << "The element of set s1 with a key > 40 is: "
           << *s1_RcIter << "." << endl;

   // The element at a specific location in the set can be found
   // by using a dereferenced iterator addressing the location
   s1_AcIter = s1.begin( );
   s1_RcIter = s1.upper_bound( *s1_AcIter );
   cout << "The first element of s1 with a key greater than"
        << endl << "that of the initial element of s1 is: "
        << *s1_RcIter << "." << endl;
}
```

```Output
The first element of set s1 with a key greater than 20 is: 30.
The set s1 doesn't have an element with a key greater than 30.
The first element of s1 with a key greater than
that of the initial element of s1 is: 20.
```

## <a name="value_comp"></a>  set::value_comp

Pobiera kopię obiektu porównania, użytego do uporządkowania wartości elementów w zestawie.

```cpp
value_compare value_comp() const;
```

### <a name="return-value"></a>Wartość zwracana

Zwraca obiekt funkcji, który używa zestawu do porządkowania jego elementów, czyli parametru szablonu `Traits`.

Aby uzyskać więcej informacji na temat `Traits` zobacz [Ustaw klasy](../standard-library/set-class.md) tematu.

### <a name="remarks"></a>Uwagi

Obiekt przechowywanych definiuje funkcję elementu członkowskiego:

**bool operator**( **const klucza &**`_xVal`, **const klucza &**`_yVal`);

która zwraca **true** Jeśli `_xVal` poprzedza i nie jest równa `_yVal` w kolejności sortowania.

Należy pamiętać, że oba [value_compare](#value_compare) i [key_compare](#key_compare) są synonimy dla parametru szablonu **cech**. Oba typy są dostępne dla zestawu i zestawów wielokrotnych klas, gdy są identyczne, aby zapewnić zgodność z mapy i klasy multimap — gdy są różne.

### <a name="example"></a>Przykład

```cpp
// set_value_comp.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;

   set <int, less<int> > s1;
   set <int, less<int> >::value_compare vc1 = s1.value_comp( );
   bool result1 = vc1( 2, 3 );
   if( result1 == true )
   {
      cout << "vc1( 2,3 ) returns value of true, "
           << "where vc1 is the function object of s1."
           << endl;
   }
   else
   {
      cout << "vc1( 2,3 ) returns value of false, "
           << "where vc1 is the function object of s1."
           << endl;
   }

   set <int, greater<int> > s2;
   set<int, greater<int> >::value_compare vc2 = s2.value_comp( );
   bool result2 = vc2( 2, 3 );
   if( result2 == true )
   {
      cout << "vc2( 2,3 ) returns value of true, "
           << "where vc2 is the function object of s2."
           << endl;
   }
   else
   {
      cout << "vc2( 2,3 ) returns value of false, "
           << "where vc2 is the function object of s2."
           << endl;
   }
}
```

```Output
vc1( 2,3 ) returns value of true, where vc1 is the function object of s1.
vc2( 2,3 ) returns value of false, where vc2 is the function object of s2.
```

## <a name="value_compare"></a>  set::value_compare

Typ, który udostępnia obiekt funkcji, które można porównać dwóch wartości elementu, aby ustalić ich względne kolejności w zestawie.

```cpp
typedef key_compare value_compare;
```

### <a name="remarks"></a>Uwagi

`value_compare` synonim parametru szablonu jest `Traits`.

Aby uzyskać więcej informacji na temat `Traits` zobacz [Ustaw klasy](../standard-library/set-class.md) tematu.

Należy pamiętać, że oba [key_compare](#key_compare) i **value_compare** są synonimy dla parametru szablonu **cech**. Oba typy są dostępne dla zestawu i zestawów wielokrotnych klas, gdy są identyczne, aby zapewnić zgodność z mapy i klasy multimap — gdy są różne.

### <a name="example"></a>Przykład

Zobacz przykład [value_comp](#value_comp) przykład sposobu deklarowanie i użycie `value_compare`.

## <a name="value_type"></a>  set::value_type

Typ, który opisuje obiekt zapisany jako elementu zestawu jako wartość.

```cpp
typedef Key value_type;
```

### <a name="remarks"></a>Uwagi

`value_type` synonim parametru szablonu jest `Key`.

Aby uzyskać więcej informacji na temat `Key`, zobacz sekcję uwag [Ustaw klasy](../standard-library/set-class.md) tematu.

Należy pamiętać, że oba [key_type](#key_type) i `value_type` są synonimy dla parametru szablonu **klucza**. Oba typy są dostępne dla zestawu i zestawów wielokrotnych klas, gdy są identyczne, aby zapewnić zgodność z mapy i klasy multimap — gdy są różne.

### <a name="example"></a>Przykład

```cpp
// set_value_type.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   set <int> s1;
   set <int>::iterator s1_Iter;

   set <int>::value_type svt_Int;   // Declare value_type
   svt_Int = 10;            // Initialize value_type

   set <int> :: key_type skt_Int;   // Declare key_type
   skt_Int = 20;             // Initialize key_type

   s1.insert( svt_Int );         // Insert value into s1
   s1.insert( skt_Int );         // Insert key into s1

   // A set accepts key_types or value_types as elements
   cout << "The set has elements:";
   for ( s1_Iter = s1.begin( ) ; s1_Iter != s1.end( ); s1_Iter++)
      cout << " " << *s1_Iter;
   cout << "." << endl;
}
```

```Output
The set has elements: 10 20.
```

## <a name="see-also"></a>Zobacz także

[\<Ustaw >](../standard-library/set.md)<br/>
[Kontenery](../cpp/containers-modern-cpp.md)<br/>
[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Dokumentacja standardowej biblioteki C++](../standard-library/cpp-standard-library-reference.md)<br/>
