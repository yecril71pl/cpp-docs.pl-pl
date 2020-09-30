---
title: multimap (STL/CLR)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- cliext::multimap
- cliext::multimap::begin
- cliext::multimap::clear
- cliext::multimap::const_iterator
- cliext::multimap::const_reference
- cliext::multimap::const_reverse_iterator
- cliext::multimap::count
- cliext::multimap::difference_type
- cliext::multimap::empty
- cliext::multimap::end
- cliext::multimap::equal_range
- cliext::multimap::erase
- cliext::multimap::find
- cliext::multimap::generic_container
- cliext::multimap::generic_iterator
- cliext::multimap::generic_reverse_iterator
- cliext::multimap::generic_value
- cliext::multimap::insert
- cliext::multimap::iterator
- cliext::multimap::key_comp
- cliext::multimap::key_compare
- cliext::multimap::key_type
- cliext::multimap::lower_bound
- cliext::multimap::make_value
- cliext::multimap::mapped_type
- cliext::multimap::multimap
- cliext::multimap::operator=
- cliext::multimap::rbegin
- cliext::multimap::reference
- cliext::multimap::rend
- cliext::multimap::reverse_iterator
- cliext::multimap::size
- cliext::multimap::size_type
- cliext::multimap::swap
- cliext::multimap::to_array
- cliext::multimap::upper_bound
- cliext::multimap::value_comp
- cliext::multimap::value_compare
- cliext::multimap::value_type
- cliext::mutlimap::operator!=
- cliext::mutlimap::operator<
- cliext::mutlimap::operator<=
- cliext::mutlimap::operator==
- cliext::mutlimap::operator>
- cliext::mutlimap::operator>=
helpviewer_keywords:
- <map> header [STL/CLR]
- <cliext/map> header [STL/CLR]
- multimap class [STL/CLR]
- begin member [STL/CLR]
- clear member [STL/CLR]
- const_iterator member [STL/CLR]
- const_reference member [STL/CLR]
- const_reverse_iterator member [STL/CLR]
- count member [STL/CLR]
- difference_type member [STL/CLR]
- empty member [STL/CLR]
- end member [STL/CLR]
- equal_range member [STL/CLR]
- erase member [STL/CLR]
- find member [STL/CLR]
- generic_container member [STL/CLR]
- generic_iterator member [STL/CLR]
- generic_reverse_iterator member [STL/CLR]
- generic_value member [STL/CLR]
- insert member [STL/CLR]
- iterator member [STL/CLR]
- key_comp member [STL/CLR]
- key_compare member [STL/CLR]
- key_type member [STL/CLR]
- lower_bound member [STL/CLR]
- make_value member [STL/CLR]
- mapped_type member [STL/CLR]
- multimap member [STL/CLR]
- operator= member [STL/CLR]
- rbegin member [STL/CLR]
- reference member [STL/CLR]
- rend member [STL/CLR]
- reverse_iterator member [STL/CLR]
- size member [STL/CLR]
- size_type member [STL/CLR]
- swap member [STL/CLR]
- to_array member [STL/CLR]
- upper_bound member [STL/CLR]
- value_comp member [STL/CLR]
- value_compare member [STL/CLR]
- value_type member [STL/CLR]
- operator!= member [STL/CLR]
- operator< member [STL/CLR]
- operator<= member [STL/CLR]
- operator== member [STL/CLR]
- operator> member [STL/CLR]
- operator>= member [STL/CLR]
ms.assetid: 3dfe329d-a078-462a-b050-7999ce6110ad
ms.openlocfilehash: 6bdd9b308a4917fde7de7b97ed7b9f7cfc8519a9
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/29/2020
ms.locfileid: "91508560"
---
# <a name="multimap-stlclr"></a>multimap (STL/CLR)

Klasa szablonu opisuje obiekt, który kontroluje różnej długości sekwencje elementów, które mają dostęp dwukierunkowy. Kontener służy `multimap` do zarządzania sekwencją elementów jako (niemal) uporządkowanym drzewem węzłów, każdy z nich przechowujący jeden element. Element składa się z klucza, do porządkowania sekwencji i mapowanej wartości, która jest przypisana do przebiegu.

W poniższym opisie `GValue` jest taka sama jak:

`Microsoft::VisualC::StlClr::GenericPair<GKey, GMapped>`

gdzie:

`GKey` jest taka sama jak *klucz* , chyba że ostatni jest typem ref, w takim przypadku jest `Key^`

`GMapped` jest taka sama jak *zamapowana* , chyba że jest to typ referencyjny, w tym przypadku jest to `Mapped^`

## <a name="syntax"></a>Składnia

```cpp
template<typename Key,
    typename Mapped>
    ref class multimap
        :   public
        System::ICloneable,
        System::Collections::IEnumerable,
        System::Collections::ICollection,
        System::Collections::Generic::IEnumerable<GValue>,
        System::Collections::Generic::ICollection<GValue>,
        System::Collections::Generic::IList<GValue>,
        Microsoft::VisualC::StlClr::ITree<Gkey, GValue>
    { ..... };
```

### <a name="parameters"></a>Parametry

*Klucz*<br/>
Typ składnika klucza elementu w kontrolowanej sekwencji.

*Mapped*<br/>
Typ dodatkowego składnika elementu w kontrolowanej sekwencji.

## <a name="requirements"></a>Wymagania

**Nagłówek:**\<cliext/map>

**Przestrzeń nazw:** cliext

## <a name="declarations"></a>Deklaracje

|Definicja typu|Opis|
|---------------------|-----------------|
|[multimap::const_iterator (STL/CLR)](#const_iterator)|Typ iteratora stałego dla kontrolowanej sekwencji.|
|[multimap::const_reference (STL/CLR)](#const_reference)|Typ stałego odwołania do elementu.|
|[multimap::const_reverse_iterator (STL/CLR)](#const_reverse_iterator)|Typ iteratora stałego zwrotnego dla kontrolowanej sekwencji.|
|[multimap::difference_type (STL/CLR)](#difference_type)|Typ (prawdopodobnie podpisany) odległości między dwoma elementami.|
|[multimap::generic_container (STL/CLR)](#generic_container)|Typ interfejsu generycznego dla kontenera.|
|[multimap::generic_iterator (STL/CLR)](#generic_iterator)|Typ iteratora dla interfejsu generycznego dla kontenera.|
|[multimap::generic_reverse_iterator (STL/CLR)](#generic_reverse_iterator)|Typ iteratora odwrotnego dla interfejsu generycznego dla kontenera.|
|[multimap::generic_value (STL/CLR)](#generic_value)|Typ elementu dla interfejsu generycznego dla kontenera.|
|[multimap::iterator (STL/CLR)](#iterator)|Typ iteratora dla kontrolowanej sekwencji.|
|[multimap::key_compare (STL/CLR)](#key_compare)|Delegat porządkowania dla dwóch kluczy.|
|[multimap::key_type (STL/CLR)](#key_type)|Typ klucza sortowania.|
|[multimap::mapped_type (STL/CLR)](#mapped_type)|Typ mapowanej wartości skojarzonej z poszczególnymi kluczami.|
|[multimap::reference (STL/CLR)](#reference)|Typ odwołania do elementu.|
|[multimap::reverse_iterator (STL/CLR)](#reverse_iterator)|Typ iteratora odwrotnego dla kontrolowanej sekwencji.|
|[multimap::size_type (STL/CLR)](#size_type)|Typ (nieujemnej) odległości między dwoma elementami.|
|[multimap::value_compare (STL/CLR)](#value_compare)|Delegat porządkowania dla dwóch wartości elementów.|
|[multimap::value_type (STL/CLR)](#value_type)|Typ elementu.|

|Funkcja elementów członkowskich|Opis|
|---------------------|-----------------|
|[multimap::begin (STL/CLR)](#begin)|Określa początek kontrolowanej sekwencji.|
|[multimap::clear (STL/CLR)](#clear)|Usuwa wszystkie elementy.|
|[multimap::count (STL/CLR)](#count)|Zlicza elementy pasujące do określonego klucza.|
|[multimap::empty (STL/CLR)](#empty)|Sprawdza, czy nie ma żadnych elementów.|
|[multimap::end (STL/CLR)](#end)|Określa koniec kontrolowanej sekwencji.|
|[multimap::equal_range (STL/CLR)](#equal_range)|Wyszukuje zakres, który odpowiada określonemu kluczowi.|
|[multimap::erase (STL/CLR)](#erase)|Usuwa elementy z określonych pozycji.|
|[multimap::find (STL/CLR)](#find)|Wyszukuje element, który odpowiada określonemu kluczowi.|
|[multimap::insert (STL/CLR)](#insert)|Dodaje elementy.|
|[multimap::key_comp (STL/CLR)](#key_comp)|Kopiuje delegata porządkowania dla dwóch kluczy.|
|[multimap::lower_bound (STL/CLR)](#lower_bound)|Znajduje początek zakresu, który odpowiada określonemu kluczowi.|
|[multimap::make_value (STL/CLR)](#make_value)|Konstruuje obiekt wartości.|
|[multimap::multimap (STL/CLR)](#multimap)|Konstruuje obiekt kontenera.|
|[multimap::rbegin (STL/CLR)](#rbegin)|Określa początek odwróconej sekwencji kontrolowanej.|
|[multimap::rend (STL/CLR)](#rend)|Określa koniec odwróconej kontrolowanej sekwencji.|
|[multimap::size (STL/CLR)](#size)|Liczy liczbę elementów.|
|[multimap::swap (STL/CLR)](#swap)|Zamienia zawartości dwóch kontenerów.|
|[multimap::to_array (STL/CLR)](#to_array)|Kopiuje przekontrolowaną sekwencję do nowej tablicy.|
|[multimap::upper_bound (STL/CLR)](#upper_bound)|Znajduje koniec zakresu, który odpowiada określonemu kluczowi.|
|[multimap::value_comp (STL/CLR)](#value_comp)|Kopiuje delegata porządkowania dla dwóch wartości elementów.|

|Operator|Opis|
|--------------|-----------------|
|[multimap::operator= (STL/CLR)](#op_as)|Zastępuje kontrolowaną sekwencję.|
|[operator!= (multimap) (STL/CLR)](#op_neq)|Określa, czy `multimap` obiekt nie jest równy innemu `multimap` obiektowi.|
|[< operatora (multimap) (STL/CLR)](#op_lt)|Określa, czy `multimap` obiekt jest mniejszy niż inny `multimap` obiekt.|
|[operator<= (multimap) (STL/CLR)](#op_lteq)|Określa, czy `multimap` obiekt jest mniejszy niż lub równy innemu `multimap` obiektowi.|
|[operator = = (multimap) (STL/CLR)](#op_eq)|Określa, czy `multimap` obiekt jest równy innemu `multimap` obiektowi.|
|[> operatora (multimap) (STL/CLR)](#op_gt)|Określa, czy `multimap` obiekt jest większy niż inny `multimap` obiekt.|
|[operator>= (multimap) (STL/CLR)](#op_gteq)|Określa, czy `multimap` obiekt jest większy lub równy innemu `multimap` obiektowi.|

## <a name="interfaces"></a>Interfejsy

|Interfejs|Opis|
|---------------|-----------------|
|<xref:System.ICloneable>|Duplikowanie obiektu.|
|<xref:System.Collections.IEnumerable>|Sekwencja przez elementy.|
|<xref:System.Collections.ICollection>|Obsługa grupy elementów.|
|<xref:System.Collections.Generic.IEnumerable%601>|Sekwencja przez wpisane elementy.|
|<xref:System.Collections.Generic.ICollection%601>|Obsługuj grupę wpisanych elementów.|
|ITree\<Key, Value>|Obsługa kontenera ogólnego.|

## <a name="remarks"></a>Uwagi

Obiekt przydziela i zwalnia magazyn dla sekwencji, która kontroluje jako pojedyncze węzły. Wstawia elementy do (niemal) zrównoważonego drzewa, które zachowuje uporządkowane przez zmianę linków między węzłami, a nigdy przez kopiowanie zawartości jednego węzła do drugiego. Oznacza to, że można wstawiać i usuwać elementy swobodnie bez zakłócania pozostałych elementów.

Obiekt porządkuje sekwencję, która kontroluje, wywołując zapisany obiekt delegata typu [multimap:: key_compare (STL/CLR)](#key_compare). Można określić przechowywany obiekt delegowany podczas konstruowania multimap; Jeśli określisz brak obiektu delegowanego, wartością domyślną jest porównanie `operator<(key_type, key_type)` . Dostęp do tego przechowywanego obiektu można uzyskać, wywołując funkcję członkowską [multimap:: key_comp (STL/CLR)](#key_comp) `()` .

Taki obiekt delegata musi nałożyć ścisłe słabe porządkowanie dla kluczy typu [multimap:: key_type (STL/CLR)](#key_type). Oznacza to, że dla dowolnych dwóch kluczy `X` i `Y` :

`key_comp()(X, Y)` zwraca ten sam wynik Boolean dla każdego wywołania.

Jeśli `key_comp()(X, Y)` ma wartość true, a następnie `key_comp()(Y, X)` musi mieć wartość false.

Jeśli `key_comp()(X, Y)` ma wartość true, `X` to przed `Y` .

Jeśli `!key_comp()(X, Y) && !key_comp()(Y, X)` ma wartość true, wówczas `X` i `Y` są określane jako równoważne porządkowanie.

Dla każdego elementu `X` , który poprzedza `Y` w kontrolowanej sekwencji, `key_comp()(Y, X)` ma wartość false. (Dla domyślnego obiektu delegowanego klucze nigdy nie zmniejszają wartości). W przeciwieństwie do [mapy klas szablonu (STL/CLR)](../dotnet/map-stl-clr.md), obiekt klasy szablonu nie `multimap` wymaga, aby klucze dla wszystkich elementów były unikatowe. (Co najmniej dwa klucze mogą mieć równoważne porządkowanie).

Każdy element zawiera oddzielny klucz i zamapowane wartości. Sekwencja jest reprezentowana w sposób, który pozwala na wyszukiwanie, wstawianie i usuwanie dowolnego elementu z liczbą operacji proporcjonalnie do logarytmu liczby elementów w sekwencji (czas logarytmu). Ponadto, wstawianie elementu nie unieważnia iteratorów, a usuwanie elementu unieważnia tylko te iteratory, które wskazują na usunięty element.

Multimap obsługuje Iteratory dwukierunkowe, co oznacza, że można przechodzić do sąsiadujących elementów przy użyciu iteratora, który wyznacza element w kontrolowanej sekwencji. Specjalny węzeł główny odpowiada iteratorowi zwróconemu przez [multimap:: end (STL/CLR)](#end) `()` . Można zmniejszyć ten iterator, aby dotrzeć do ostatniego elementu w kontrolowanej sekwencji, jeśli jest obecny. Można zwiększyć iterator multimap, aby dotrzeć do węzła głównego. następnie będzie on porównywany z równą `end()` . Ale nie można usunąć odwołania do iteratora zwróconego przez `end()` .

Należy zauważyć, że nie można odwołać się do elementu multimap bezpośrednio przy użyciu jego pozycji liczbowej — który wymaga iteratora dostępu swobodnego.

Iterator multimap przechowuje uchwyt do skojarzonego z nim węzła multimap, który z kolei przechowuje dojście do skojarzonego kontenera. Iteratorów można używać tylko ze skojarzonymi obiektami kontenera. Iterator multimap pozostaje prawidłowy, dopóki jego skojarzony węzeł multimap jest skojarzony z niektórymi multimap. Ponadto prawidłowy iterator jest dereferencable — można go użyć w celu uzyskania dostępu do lub zmiany wartości elementu, który wyznacza, tak długo, jak nie jest równa `end()` .

Wymazywanie lub usuwanie elementu wywołuje destruktor dla jego przechowywanej wartości. Niszczenie kontenera powoduje wymazanie wszystkich elementów. W tym celu kontener, którego typem elementu jest Klasa ref, zapewnia, że żadne elementy nie wyprowadzą kontenera. Należy jednak zauważyć, że kontener dojść *nie* niszczy swoich elementów.

## <a name="members"></a>Elementy członkowskie

## <a name="multimapbegin-stlclr"></a><a name="begin"></a> multimap:: begin (STL/CLR)

Określa początek kontrolowanej sekwencji.

### <a name="syntax"></a>Składnia

```cpp
iterator begin();
```

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca iterator dwukierunkowy, który wyznacza pierwszy element kontrolowanej sekwencji lub tuż poza końcem pustej sekwencji. Służy do uzyskania iteratora, który wyznacza `current` początek kontrolowanej sekwencji, ale jego stan może ulec zmianie w przypadku zmiany długości kontrolowanej sekwencji.

### <a name="example"></a>Przykład

```cpp
// cliext_multimap_begin.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::multimap<wchar_t, int> Mymultimap;
int main()
    {
    Mymultimap c1;
    c1.insert(Mymultimap::make_value(L'a', 1));
    c1.insert(Mymultimap::make_value(L'b', 2));
    c1.insert(Mymultimap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymultimap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // inspect first two items
    Mymultimap::iterator it = c1.begin();
    System::Console::WriteLine("*begin() = [{0} {1}]",
        it->first, it->second);
    ++it;
    System::Console::WriteLine("*++begin() = [{0} {1}]",
        it->first, it->second);
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
*begin() = [a 1]
*++begin() = [b 2]
```

## <a name="multimapclear-stlclr"></a><a name="clear"></a> multimap:: Clear (STL/CLR)

Usuwa wszystkie elementy.

### <a name="syntax"></a>Składnia

```cpp
void clear();
```

### <a name="remarks"></a>Uwagi

Funkcja członkowska skutecznie wywołuje [multimap:: Erase (STL/CLR)](#erase) `(` [multimap:: begin (STL/CLR)](#begin) `(),` [multimap:: end (STL/CLR)](#end) `())` . Jest on używany do upewnienia się, że kontrolowana sekwencja jest pusta.

### <a name="example"></a>Przykład

```cpp
// cliext_multimap_clear.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::multimap<wchar_t, int> Mymultimap;
int main()
    {
    Mymultimap c1;
    c1.insert(Mymultimap::make_value(L'a', 1));
    c1.insert(Mymultimap::make_value(L'b', 2));
    c1.insert(Mymultimap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymultimap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // clear the container and reinspect
    c1.clear();
    System::Console::WriteLine("size() = {0}", c1.size());

    c1.insert(Mymultimap::make_value(L'a', 1));
    c1.insert(Mymultimap::make_value(L'b', 2));

    // display contents " [a 1] [b 2]"
    for each (Mymultimap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();
    c1.clear();
    System::Console::WriteLine("size() = {0}", c1.size());
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
size() = 0
[a 1] [b 2]
size() = 0
```

## <a name="multimapconst_iterator-stlclr"></a><a name="const_iterator"></a> multimap:: const_iterator (STL/CLR)

Typ iteratora stałego dla kontrolowanej sekwencji.

### <a name="syntax"></a>Składnia

```cpp
typedef T2 const_iterator;
```

### <a name="remarks"></a>Uwagi

Typ opisuje obiekt nieokreślonego typu `T2` , który może obsłużyć jako stały iterator dwukierunkowy dla kontrolowanej sekwencji.

### <a name="example"></a>Przykład

```cpp
// cliext_multimap_const_iterator.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::multimap<wchar_t, int> Mymultimap;
int main()
    {
    Mymultimap c1;
    c1.insert(Mymultimap::make_value(L'a', 1));
    c1.insert(Mymultimap::make_value(L'b', 2));
    c1.insert(Mymultimap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    Mymultimap::const_iterator cit = c1.begin();
    for (; cit != c1.end(); ++cit)
        System::Console::Write("[{0} {1}] ", cit->first, cit->second);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
```

## <a name="multimapconst_reference-stlclr"></a><a name="const_reference"></a> multimap:: const_reference (STL/CLR)

Typ stałego odwołania do elementu.

### <a name="syntax"></a>Składnia

```cpp
typedef value_type% const_reference;
```

### <a name="remarks"></a>Uwagi

Typ opisuje stałe odwołanie do elementu.

### <a name="example"></a>Przykład

```cpp
// cliext_multimap_const_reference.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::multimap<wchar_t, int> Mymultimap;
int main()
    {
    Mymultimap c1;
    c1.insert(Mymultimap::make_value(L'a', 1));
    c1.insert(Mymultimap::make_value(L'b', 2));
    c1.insert(Mymultimap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    Mymultimap::const_iterator cit = c1.begin();
    for (; cit != c1.end(); ++cit)
        {   // get a const reference to an element
        Mymultimap::const_reference cref = *cit;
        System::Console::Write("[{0} {1}] ", cref->first, cref->second);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
```

## <a name="multimapconst_reverse_iterator-stlclr"></a><a name="const_reverse_iterator"></a> multimap:: const_reverse_iterator (STL/CLR)

Typ iteratora stałego zwrotnego dla kontrolowanej sekwencji.

### <a name="syntax"></a>Składnia

```cpp
typedef T4 const_reverse_iterator;
```

### <a name="remarks"></a>Uwagi

Typ opisuje obiekt nieokreślonego typu `T4` , który może być używany jako ciągły iterator odwrotny dla kontrolowanej sekwencji.

### <a name="example"></a>Przykład

```cpp
// cliext_multimap_const_reverse_iterator.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::multimap<wchar_t, int> Mymultimap;
int main()
    {
    Mymultimap c1;
    c1.insert(Mymultimap::make_value(L'a', 1));
    c1.insert(Mymultimap::make_value(L'b', 2));
    c1.insert(Mymultimap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]" reversed
    Mymultimap::const_reverse_iterator crit = c1.rbegin();
    for (; crit != c1.rend(); ++crit)
        System::Console::Write("[{0} {1}] ", crit->first, crit->second);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
[c 3] [b 2] [a 1]
```

## <a name="multimapcount-stlclr"></a><a name="count"></a> multimap:: Count (STL/CLR)

Wyszukuje liczbę elementów pasujących do określonego klucza.

### <a name="syntax"></a>Składnia

```cpp
size_type count(key_type key);
```

#### <a name="parameters"></a>Parametry

*głównych*<br/>
Wartość klucza do wyszukania.

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca liczbę elementów w kontrolowanej sekwencji, które mają równoważną kolejność z *kluczem*. Służy do określania liczby elementów aktualnie w kontrolowanej sekwencji, która pasuje do określonego klucza.

### <a name="example"></a>Przykład

```cpp
// cliext_multimap_count.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::multimap<wchar_t, int> Mymultimap;
int main()
    {
    Mymultimap c1;
    c1.insert(Mymultimap::make_value(L'a', 1));
    c1.insert(Mymultimap::make_value(L'b', 2));
    c1.insert(Mymultimap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymultimap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    System::Console::WriteLine("count(L'A') = {0}", c1.count(L'A'));
    System::Console::WriteLine("count(L'b') = {0}", c1.count(L'b'));
    System::Console::WriteLine("count(L'C') = {0}", c1.count(L'C'));
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
count(L'A') = 0
count(L'b') = 1
count(L'C') = 0
```

## <a name="multimapdifference_type-stlclr"></a><a name="difference_type"></a> multimap::d ifference_type (STL/CLR)

Typy podpisanej odległości między dwoma elementami.

### <a name="syntax"></a>Składnia

```cpp
typedef int difference_type;
```

### <a name="remarks"></a>Uwagi

Typ opisuje prawdopodobnie ujemną liczbę elementów.

### <a name="example"></a>Przykład

```cpp
// cliext_multimap_difference_type.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::multimap<wchar_t, int> Mymultimap;
int main()
    {
    Mymultimap c1;
    c1.insert(Mymultimap::make_value(L'a', 1));
    c1.insert(Mymultimap::make_value(L'b', 2));
    c1.insert(Mymultimap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymultimap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // compute positive difference
    Mymultimap::difference_type diff = 0;
    for (Mymultimap::iterator it = c1.begin(); it != c1.end(); ++it)
        ++diff;
    System::Console::WriteLine("end()-begin() = {0}", diff);

    // compute negative difference
    diff = 0;
    for (Mymultimap::iterator it = c1.end(); it != c1.begin(); --it)
        --diff;
    System::Console::WriteLine("begin()-end() = {0}", diff);
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
end()-begin() = 3
begin()-end() = -3
```

## <a name="multimapempty-stlclr"></a><a name="empty"></a> multimap:: empty (STL/CLR)

Sprawdza, czy nie ma żadnych elementów.

### <a name="syntax"></a>Składnia

```cpp
bool empty();
```

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca wartość true dla pustej kontrolowanej sekwencji. Jest równoważne [multimap:: size (STL/CLR)](#size) `() == 0` . Służy do sprawdzania, czy multimap jest pusty.

### <a name="example"></a>Przykład

```cpp
// cliext_multimap_empty.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::multimap<wchar_t, int> Mymultimap;
int main()
    {
    Mymultimap c1;
    c1.insert(Mymultimap::make_value(L'a', 1));
    c1.insert(Mymultimap::make_value(L'b', 2));
    c1.insert(Mymultimap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymultimap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();
    System::Console::WriteLine("size() = {0}", c1.size());
    System::Console::WriteLine("empty() = {0}", c1.empty());

    // clear the container and reinspect
    c1.clear();
    System::Console::WriteLine("size() = {0}", c1.size());
    System::Console::WriteLine("empty() = {0}", c1.empty());
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
size() = 3
empty() = False
size() = 0
empty() = True
```

## <a name="multimapend-stlclr"></a><a name="end"></a> multimap:: end (STL/CLR)

Określa koniec kontrolowanej sekwencji.

### <a name="syntax"></a>Składnia

```cpp
iterator end();
```

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca iterator dwukierunkowy, który wskazuje tuż poza końcem kontrolowanej sekwencji. Służy do uzyskania iteratora, który wyznacza koniec kontrolowanej sekwencji; jego stan nie zmienia się w przypadku zmiany długości kontrolowanej sekwencji.

### <a name="example"></a>Przykład

```cpp
// cliext_multimap_end.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::multimap<wchar_t, int> Mymultimap;
int main()
    {
    Mymultimap c1;
    c1.insert(Mymultimap::make_value(L'a', 1));
    c1.insert(Mymultimap::make_value(L'b', 2));
    c1.insert(Mymultimap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymultimap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // inspect last two items
    Mymultimap::iterator it = c1.end();
    --it;
    --it;
    System::Console::WriteLine("*-- --end() = [{0} {1}]",
        it->first, it->second);
    ++it;
    System::Console::WriteLine("*--end() = [{0} {1}]",
        it->first, it->second);
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
*-- --end() = [b 2]
*--end() = [c 3]
```

## <a name="multimapequal_range-stlclr"></a><a name="equal_range"></a> multimap:: equal_range (STL/CLR)

Wyszukuje zakres, który odpowiada określonemu kluczowi.

### <a name="syntax"></a>Składnia

```cpp
pair_iter_iter equal_range(key_type _Keyval);
```

#### <a name="parameters"></a>Parametry

*_Keyval*<br/>
Wartość klucza do wyszukania.

### <a name="remarks"></a>Uwagi

Metoda zwraca parę iteratorów `-` [multimap:: lower_bound (STL/CLR)](#lower_bound) `(_Keyval),` [multimap:: upper_bound (STL/CLR)](#upper_bound) `(_Keyval)` . Służy do określania zakresu elementów aktualnie w kontrolowanej sekwencji, która pasuje do określonego klucza.

### <a name="example"></a>Przykład

```cpp
// cliext_multimap_equal_range.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::multimap<wchar_t, int> Mymultimap;
typedef Mymultimap::pair_iter_iter Pairii;
int main()
    {
    Mymultimap c1;
    c1.insert(Mymultimap::make_value(L'a', 1));
    c1.insert(Mymultimap::make_value(L'b', 2));
    c1.insert(Mymultimap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymultimap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // display results of failed search
    Pairii pair1 = c1.equal_range(L'x');
    System::Console::WriteLine("equal_range(L'x') empty = {0}",
        pair1.first == pair1.second);

    // display results of successful search
    pair1 = c1.equal_range(L'b');
    for (; pair1.first != pair1.second; ++pair1.first)
        System::Console::Write("[{0} {1}] ",
            pair1.first->first, pair1.first->second);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
equal_range(L'x') empty = True
[b 2]
```

## <a name="multimaperase-stlclr"></a><a name="erase"></a> multimap:: Erase (STL/CLR)

Usuwa elementy z określonych pozycji.

### <a name="syntax"></a>Składnia

```cpp
iterator erase(iterator where);
iterator erase(iterator first, iterator last);
bool erase(key_type key)
```

#### <a name="parameters"></a>Parametry

*pierwszego*<br/>
Początek zakresu do wymazania.

*głównych*<br/>
Wartość klucza do wymazania.

*ostatniego*<br/>
Koniec zakresu do wymazania.

*gdzie*<br/>
Element do wymazania.

### <a name="remarks"></a>Uwagi

Pierwsza funkcja członkowska usuwa element kontrolowanej sekwencji wskazywany przez *WHERE*, a zwraca iterator, który wyznacza pierwszy element, który został poza elementem usunięty, lub [multimap:: end (STL/CLR)](#end) , `()` Jeśli taki element nie istnieje. Służy do usuwania pojedynczego elementu.

Druga funkcja członkowska usuwa elementy z kontrolowanej sekwencji z zakresu [ `first` , `last` ) i zwraca iterator, który wyznacza pierwszy element pozostały poza elementami usuniętymi lub `end()` Jeśli taki element nie istnieje. Jest on używany do usuwania elementów sąsiadujących lub więcej.

Trzecia funkcja członkowska usuwa każdy element kontrolowanej sekwencji, którego klucz ma równoważne porządkowanie do *klucza*i zwraca liczbę usuniętych elementów. Służy do usuwania i zliczania wszystkich elementów, które pasują do określonego klucza.

Każdy element wymazuje czas proporcjonalny do logarytmu liczby elementów w kontrolowanej sekwencji.

### <a name="example"></a>Przykład

```cpp
// cliext_multimap_erase.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::multimap<wchar_t, int> Mymultimap;
int main()
    {
    cliext::multimap<wchar_t, int> c1;
    c1.insert(cliext::multimap<wchar_t, int>::make_value(L'a', 1));
    c1.insert(cliext::multimap<wchar_t, int>::make_value(L'b', 2));
    c1.insert(cliext::multimap<wchar_t, int>::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (cliext::multimap<wchar_t, int>::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // erase an element and reinspect
    cliext::multimap<wchar_t, int>::iterator it =
        c1.erase(c1.begin());
    System::Console::WriteLine("erase(begin()) = [{0} {1}]",
        it->first, it->second);

    // add elements and display " b c d e"
    c1.insert(cliext::multimap<wchar_t, int>::make_value(L'd', 4));
    c1.insert(cliext::multimap<wchar_t, int>::make_value(L'e', 5));
    for each (cliext::multimap<wchar_t, int>::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // erase all but end
    it = c1.end();
    it = c1.erase(c1.begin(), --it);
    System::Console::WriteLine("erase(begin(), end()-1) = [{0} {1}]",
        it->first, it->second);
    System::Console::WriteLine("size() = {0}", c1.size());

    // erase end
    System::Console::WriteLine("erase(L'x') = {0}", c1.erase(L'x'));
    System::Console::WriteLine("erase(L'e') = {0}", c1.erase(L'e'));
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
erase(begin()) = [b 2]
[b 2] [c 3] [d 4] [e 5]
erase(begin(), end()-1) = [e 5]
size() = 1
erase(L'x') = 0
erase(L'e') = 1
```

## <a name="multimapfind-stlclr"></a><a name="find"></a> multimap:: Find (STL/CLR)

Wyszukuje element, który odpowiada określonemu kluczowi.

### <a name="syntax"></a>Składnia

```cpp
iterator find(key_type key);
```

#### <a name="parameters"></a>Parametry

*głównych*<br/>
Wartość klucza do wyszukania.

### <a name="remarks"></a>Uwagi

Jeśli co najmniej jeden element w kontrolowanej sekwencji ma równoważne porządkowanie z *kluczem*, funkcja członkowska zwraca iterator wyznaczający jeden z tych elementów. w przeciwnym razie zwraca [multimap:: end (STL/CLR)](#end) `()` . Służy do lokalizowania elementu w kontrolowanej sekwencji, który odpowiada określonemu kluczowi.

### <a name="example"></a>Przykład

```cpp
// cliext_multimap_find.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::multimap<wchar_t, int> Mymultimap;
int main()
    {
    Mymultimap c1;
    c1.insert(Mymultimap::make_value(L'a', 1));
    c1.insert(Mymultimap::make_value(L'b', 2));
    c1.insert(Mymultimap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymultimap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    System::Console::WriteLine("find {0} = {1}",
        L'A', c1.find(L'A') != c1.end());

    Mymultimap::iterator it = c1.find(L'b');
    System::Console::WriteLine("find {0} = [{1} {2}]",
        L'b', it->first, it->second);

    System::Console::WriteLine("find {0} = {1}",
        L'C', c1.find(L'C') != c1.end());
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
find A = False
find b = [b 2]
find C = False
```

## <a name="multimapgeneric_container-stlclr"></a><a name="generic_container"></a> multimap:: generic_container (STL/CLR)

Typ interfejsu generycznego dla kontenera.

### <a name="syntax"></a>Składnia

```cpp
typedef Microsoft::VisualC::StlClr::
    ITree<GKey, GValue>
    generic_container;
```

### <a name="remarks"></a>Uwagi

Typ opisuje ogólny interfejs dla tej klasy kontenera szablonu.

### <a name="example"></a>Przykład

```cpp
// cliext_multimap_generic_container.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::multimap<wchar_t, int> Mymultimap;
int main()
    {
    Mymultimap c1;
    c1.insert(Mymultimap::make_value(L'a', 1));
    c1.insert(Mymultimap::make_value(L'b', 2));
    c1.insert(Mymultimap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymultimap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // construct a generic container
    Mymultimap::generic_container^ gc1 = %c1;
    for each (Mymultimap::value_type elem in gc1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // modify generic and display original
    gc1->insert(Mymultimap::make_value(L'd', 4));
    for each (Mymultimap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // modify original and display generic
    c1.insert(Mymultimap::make_value(L'e', 5));
    for each (Mymultimap::value_type elem in gc1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
[a 1] [b 2] [c 3]
[a 1] [b 2] [c 3] [d 4]
[a 1] [b 2] [c 3] [d 4] [e 5]
```

## <a name="multimapgeneric_iterator-stlclr"></a><a name="generic_iterator"></a> multimap:: generic_iterator (STL/CLR)

Typ iteratora do użycia z interfejsem ogólnym dla kontenera.

### <a name="syntax"></a>Składnia

```cpp
typedef Microsoft::VisualC::StlClr::Generic::
    ContainerBidirectionalIterator<generic_value>
    generic_iterator;
```

### <a name="remarks"></a>Uwagi

Typ opisuje iterator ogólny, który może być używany z interfejsem ogólnym dla tej klasy kontenera szablonu.

### <a name="example"></a>Przykład

```cpp
// cliext_multimap_generic_iterator.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::multimap<wchar_t, int> Mymultimap;
int main()
    {
    Mymultimap c1;
    c1.insert(Mymultimap::make_value(L'a', 1));
    c1.insert(Mymultimap::make_value(L'b', 2));
    c1.insert(Mymultimap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymultimap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // construct a generic container
    Mymultimap::generic_container^ gc1 = %c1;
    for each (Mymultimap::value_type elem in gc1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // get an element and display it
    Mymultimap::generic_iterator gcit = gc1->begin();
    Mymultimap::generic_value gcval = *gcit;
    System::Console::Write("[{0} {1}] ", gcval->first, gcval->second);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
[a 1] [b 2] [c 3]
[a 1]
```

## <a name="multimapgeneric_reverse_iterator-stlclr"></a><a name="generic_reverse_iterator"></a> multimap:: generic_reverse_iterator (STL/CLR)

Typ iteratora odwrotnego do użycia z interfejsem ogólnym dla kontenera.

### <a name="syntax"></a>Składnia

```cpp
typedef Microsoft::VisualC::StlClr::Generic::
    ReverseRandomAccessIterator<generic_value>
    generic_reverse_iterator;
```

### <a name="remarks"></a>Uwagi

Typ opisuje ogólny iterator odwrotny, który może być używany z ogólnym interfejsem klasy kontenera tego szablonu.

### <a name="example"></a>Przykład

```cpp
// cliext_multimap_generic_reverse_iterator.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::multimap<wchar_t, int> Mymultimap;
int main()
    {
    Mymultimap c1;
    c1.insert(Mymultimap::make_value(L'a', 1));
    c1.insert(Mymultimap::make_value(L'b', 2));
    c1.insert(Mymultimap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymultimap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // construct a generic container
    Mymultimap::generic_container^ gc1 = %c1;
    for each (Mymultimap::value_type elem in gc1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // get an element and display it
    Mymultimap::generic_reverse_iterator gcit = gc1->rbegin();
    Mymultimap::generic_value gcval = *gcit;
    System::Console::WriteLine("[{0} {1}] ", gcval->first, gcval->second);
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
[a 1] [b 2] [c 3]
[c 3]
```

## <a name="multimapgeneric_value-stlclr"></a><a name="generic_value"></a> multimap:: generic_value (STL/CLR)

Typ elementu do użycia z interfejsem ogólnym dla kontenera.

### <a name="syntax"></a>Składnia

```cpp
typedef GValue generic_value;
```

### <a name="remarks"></a>Uwagi

Typ opisuje obiekt typu `GValue` , który opisuje wartość przechowywanego elementu do użycia z interfejsem ogólnym dla tej klasy kontenera szablonu.

### <a name="example"></a>Przykład

```cpp
// cliext_multimap_generic_value.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::multimap<wchar_t, int> Mymultimap;
int main()
    {
    Mymultimap c1;
    c1.insert(Mymultimap::make_value(L'a', 1));
    c1.insert(Mymultimap::make_value(L'b', 2));
    c1.insert(Mymultimap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymultimap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // construct a generic container
    Mymultimap::generic_container^ gc1 = %c1;
    for each (Mymultimap::value_type elem in gc1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // get an element and display it
    Mymultimap::generic_iterator gcit = gc1->begin();
    Mymultimap::generic_value gcval = *gcit;
    System::Console::WriteLine("[{0} {1}] ", gcval->first, gcval->second);
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
[a 1] [b 2] [c 3]
[a 1]
```

## <a name="multimapinsert-stlclr"></a><a name="insert"></a> multimap:: Insert (STL/CLR)

Dodaje elementy.

### <a name="syntax"></a>Składnia

```cpp
iterator insert(value_type val);
iterator insert(iterator where, value_type val);
template<typename InIter>
    void insert(InIter first, InIter last);
void insert(System::Collections::Generic::IEnumerable<value_type>^ right);
```

#### <a name="parameters"></a>Parametry

*pierwszego*<br/>
Początek zakresu do wstawienia.

*ostatniego*<br/>
Koniec zakresu do wstawienia.

*Kliknij*<br/>
Wyliczenie do wstawienia.

*użyte*<br/>
Wartość klucza do wstawienia.

*gdzie*<br/>
Gdzie w kontenerze do wstawienia (tylko Wskazówka).

### <a name="remarks"></a>Uwagi

Każda funkcja członkowska wstawia sekwencję określoną przez pozostałe operandy.

Pierwsza funkcja członkowska wstawia element z wartością *Val*i zwraca iterator, który wyznacza nowo wstawiony element. Służy do wstawiania pojedynczego elementu.

Druga funkcja członkowska wstawia element z wartością *Val*przy użyciu instrukcji *WHERE* jako wskazówkę (w celu zwiększenia wydajności) i zwraca iterator, który wyznacza nowo wstawiony element. Służy do wstawiania pojedynczego elementu, który może być przyległy do elementu, który znasz.

Trzecia funkcja członkowska wstawia sekwencję [ `first` , `last` ). Służy do wstawiania elementów, które zostały skopiowane z innej sekwencji.

Czwarta funkcja członkowska wstawia sekwencję wydaną po *prawej stronie*. Służy do wstawiania sekwencji opisanej przez moduł wyliczający.

Każde wstawienie elementu ma czas proporcjonalny do logarytmu liczby elementów w kontrolowanej sekwencji. Wstawianie może odbywać się w amortyzowanym stałym czasie, Jednakże z uwzględnieniem wskazówki, która wyznacza element przyległy do punktu wstawiania.

### <a name="example"></a>Przykład

```cpp
// cliext_multimap_insert.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::multimap<wchar_t, int> Mymultimap;
int main()
    {
    Mymultimap c1;
    c1.insert(Mymultimap::make_value(L'a', 1));
    c1.insert(Mymultimap::make_value(L'b', 2));
    c1.insert(Mymultimap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymultimap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // insert a single value, unique and duplicate
    Mymultimap::iterator it =
        c1.insert(Mymultimap::make_value(L'x', 24));
    System::Console::WriteLine("insert([L'x' 24]) = [{0} {1}]",
        it->first, it->second);

    it = c1.insert(Mymultimap::make_value(L'b', 2));
    System::Console::WriteLine("insert([L'b' 2]) = [{0} {1}]",
        it->first, it->second);

    for each (Mymultimap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // insert a single value with hint
    it = c1.insert(c1.begin(), Mymultimap::make_value(L'y', 25));
    System::Console::WriteLine("insert(begin(), [L'y' 25]) = [{0} {1}]",
        it->first, it->second);
    for each (Mymultimap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // insert an iterator range
    Mymultimap c2;
    it = c1.end();
    c2.insert(c1.begin(), --it);
    for each (Mymultimap::value_type elem in c2)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // insert an enumeration
    Mymultimap c3;
    c3.insert(   // NOTE: cast is not needed
        (System::Collections::Generic::
            IEnumerable<Mymultimap::value_type>^)%c1);
    for each (Mymultimap::value_type elem in c3)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
insert([L'x' 24]) = [x 24]
insert([L'b' 2]) = [b 2]
[a 1] [b 2] [b 2] [c 3] [x 24]
insert(begin(), [L'y' 25]) = [y 25]
[a 1] [b 2] [b 2] [c 3] [x 24] [y 25]
[a 1] [b 2] [b 2] [c 3] [x 24]
[a 1] [b 2] [b 2] [c 3] [x 24] [y 25]
```

## <a name="multimapiterator-stlclr"></a><a name="iterator"></a> multimap:: iterator (STL/CLR)

Typ iteratora dla kontrolowanej sekwencji.

### <a name="syntax"></a>Składnia

```cpp
typedef T1 iterator;
```

### <a name="remarks"></a>Uwagi

Typ opisuje obiekt nieokreślonego typu `T1` , który może obsłużyć iterator dwukierunkowy dla kontrolowanej sekwencji.

### <a name="example"></a>Przykład

```cpp
// cliext_multimap_iterator.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::multimap<wchar_t, int> Mymultimap;
int main()
    {
    Mymultimap c1;
    c1.insert(Mymultimap::make_value(L'a', 1));
    c1.insert(Mymultimap::make_value(L'b', 2));
    c1.insert(Mymultimap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    Mymultimap::iterator it = c1.begin();
    for (; it != c1.end(); ++it)
        System::Console::Write("[{0} {1}] ", it->first, it->second);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
```

## <a name="multimapkey_comp-stlclr"></a><a name="key_comp"></a> multimap:: key_comp (STL/CLR)

Kopiuje delegata porządkowania dla dwóch kluczy.

### <a name="syntax"></a>Składnia

```cpp
key_compare^key_comp();
```

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca delegat porządkowania używany do uporządkowania kontrolowanej sekwencji. Służy do porównywania dwóch kluczy.

### <a name="example"></a>Przykład

```cpp
// cliext_multimap_key_comp.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::multimap<wchar_t, int> Mymultimap;
int main()
    {
    Mymultimap c1;
    Mymultimap::key_compare^ kcomp = c1.key_comp();

    System::Console::WriteLine("compare(L'a', L'a') = {0}",
        kcomp(L'a', L'a'));
    System::Console::WriteLine("compare(L'a', L'b') = {0}",
        kcomp(L'a', L'b'));
    System::Console::WriteLine("compare(L'b', L'a') = {0}",
        kcomp(L'b', L'a'));
    System::Console::WriteLine();

    // test a different ordering rule
    Mymultimap c2 = cliext::greater<wchar_t>();
    kcomp = c2.key_comp();

    System::Console::WriteLine("compare(L'a', L'a') = {0}",
        kcomp(L'a', L'a'));
    System::Console::WriteLine("compare(L'a', L'b') = {0}",
        kcomp(L'a', L'b'));
    System::Console::WriteLine("compare(L'b', L'a') = {0}",
        kcomp(L'b', L'a'));
    return (0);
    }
```

```Output
compare(L'a', L'a') = False
compare(L'a', L'b') = True
compare(L'b', L'a') = False

compare(L'a', L'a') = False
compare(L'a', L'b') = False
compare(L'b', L'a') = True
```

## <a name="multimapkey_compare-stlclr"></a><a name="key_compare"></a> multimap:: key_compare (STL/CLR)

Delegat porządkowania dla dwóch kluczy.

### <a name="syntax"></a>Składnia

```cpp
Microsoft::VisualC::StlClr::BinaryDelegate<GKey, GKey, bool>
    key_compare;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla delegata, który określa kolejność argumentów klucza.

### <a name="example"></a>Przykład

```cpp
// cliext_multimap_key_compare.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::multimap<wchar_t, int> Mymultimap;
int main()
    {
    Mymultimap c1;
    Mymultimap::key_compare^ kcomp = c1.key_comp();

    System::Console::WriteLine("compare(L'a', L'a') = {0}",
        kcomp(L'a', L'a'));
    System::Console::WriteLine("compare(L'a', L'b') = {0}",
        kcomp(L'a', L'b'));
    System::Console::WriteLine("compare(L'b', L'a') = {0}",
        kcomp(L'b', L'a'));
    System::Console::WriteLine();

    // test a different ordering rule
    Mymultimap c2 = cliext::greater<wchar_t>();
    kcomp = c2.key_comp();

    System::Console::WriteLine("compare(L'a', L'a') = {0}",
        kcomp(L'a', L'a'));
    System::Console::WriteLine("compare(L'a', L'b') = {0}",
        kcomp(L'a', L'b'));
    System::Console::WriteLine("compare(L'b', L'a') = {0}",
        kcomp(L'b', L'a'));
    return (0);
    }
```

```Output
compare(L'a', L'a') = False
compare(L'a', L'b') = True
compare(L'b', L'a') = False

compare(L'a', L'a') = False
compare(L'a', L'b') = False
compare(L'b', L'a') = True
```

## <a name="multimapkey_type-stlclr"></a><a name="key_type"></a> multimap:: key_type (STL/CLR)

Typ klucza sortowania.

### <a name="syntax"></a>Składnia

```cpp
typedef Key key_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla *klucza*parametru szablonu.

### <a name="example"></a>Przykład

```cpp
// cliext_multimap_key_type.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::multimap<wchar_t, int> Mymultimap;
int main()
    {
    Mymultimap c1;
    c1.insert(Mymultimap::make_value(L'a', 1));
    c1.insert(Mymultimap::make_value(L'b', 2));
    c1.insert(Mymultimap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]" using key_type
    for (Mymultimap::iterator it = c1.begin(); it != c1.end(); ++it)
        {   // store element in key_type object
        Mymultimap::key_type val = it->first;

        System::Console::Write("{0} ", val);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="multimaplower_bound-stlclr"></a><a name="lower_bound"></a> multimap:: lower_bound (STL/CLR)

Znajduje początek zakresu, który odpowiada określonemu kluczowi.

### <a name="syntax"></a>Składnia

```cpp
iterator lower_bound(key_type key);
```

#### <a name="parameters"></a>Parametry

*głównych*<br/>
Wartość klucza do wyszukania.

### <a name="remarks"></a>Uwagi

Funkcja członkowska określa pierwszy element `X` w kontrolowanej sekwencji, który ma równoważne porządkowanie do *klucza*. Jeśli taki element nie istnieje, zwraca [multimap:: end (STL/CLR)](#end) `()` ; w przeciwnym razie zwraca iterator, który wyznacza `X` . Służy do lokalizowania początku sekwencji elementów aktualnie w kontrolowanej sekwencji, która pasuje do określonego klucza.

### <a name="example"></a>Przykład

```cpp
// cliext_multimap_lower_bound.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::multimap<wchar_t, int> Mymultimap;
int main()
    {
    Mymultimap c1;
    c1.insert(Mymultimap::make_value(L'a', 1));
    c1.insert(Mymultimap::make_value(L'b', 2));
    c1.insert(Mymultimap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymultimap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    System::Console::WriteLine("lower_bound(L'x')==end() = {0}",
        c1.lower_bound(L'x') == c1.end());

    Mymultimap::iterator it = c1.lower_bound(L'a');
    System::Console::WriteLine("*lower_bound(L'a') = [{0} {1}]",
        it->first, it->second);
    it = c1.lower_bound(L'b');
    System::Console::WriteLine("*lower_bound(L'b') = [{0} {1}]",
        it->first, it->second);
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
lower_bound(L'x')==end() = True
*lower_bound(L'a') = [a 1]
*lower_bound(L'b') = [b 2]
```

## <a name="multimapmake_value-stlclr"></a><a name="make_value"></a> multimap:: make_value (STL/CLR)

Konstruuje obiekt wartości.

### <a name="syntax"></a>Składnia

```cpp
static value_type make_value(key_type key, mapped_type mapped);
```

#### <a name="parameters"></a>Parametry

*głównych*<br/>
Wartość klucza do użycia.

*mapowane*<br/>
Mapowana wartość do wyszukania.

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca `value_type` obiekt, którego klucz jest *kluczem* i którego zmapowana wartość jest *zamapowana*. Służy do redagowania obiektu odpowiedniego do użycia z kilkoma innymi funkcjami składowymi.

### <a name="example"></a>Przykład

```cpp
// cliext_multimap_make_value.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::multimap<wchar_t, int> Mymultimap;
int main()
    {
    Mymultimap c1;
    c1.insert(Mymultimap::make_value(L'a', 1));
    c1.insert(Mymultimap::make_value(L'b', 2));
    c1.insert(Mymultimap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymultimap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
```

## <a name="multimapmapped_type-stlclr"></a><a name="mapped_type"></a> multimap:: mapped_type (STL/CLR)

Typ mapowanej wartości skojarzonej z poszczególnymi kluczami.

### <a name="syntax"></a>Składnia

```cpp
typedef Mapped mapped_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla *zamapowanego*parametru szablonu.

### <a name="example"></a>Przykład

```cpp
// cliext_multimap_mapped_type.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::multimap<wchar_t, int> Mymultimap;
int main()
    {
    Mymultimap c1;
    c1.insert(Mymultimap::make_value(L'a', 1));
    c1.insert(Mymultimap::make_value(L'b', 2));
    c1.insert(Mymultimap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]" using mapped_type
    for (Mymultimap::iterator it = c1.begin(); it != c1.end(); ++it)
        {   // store element in mapped_type object
        Mymultimap::mapped_type val = it->second;

        System::Console::Write("{0} ", val);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
1 2 3
```

## <a name="multimapmultimap-stlclr"></a><a name="multimap"></a> multimap:: multimap (STL/CLR)

Konstruuje obiekt kontenera.

### <a name="syntax"></a>Składnia

```cpp
multimap();
explicit multimap(key_compare^ pred);
multimap(multimap<Key, Mapped>% right);
multimap(multimap<Key, Mapped>^ right);
template<typename InIter>
    multimapmultimap(InIter first, InIter last);
template<typename InIter>
    multimap(InIter first, InIter last,
        key_compare^ pred);
multimap(System::Collections::Generic::IEnumerable<GValue>^ right);
multimap(System::Collections::Generic::IEnumerable<GValue>^ right,
    key_compare^ pred);
```

#### <a name="parameters"></a>Parametry

*pierwszego*<br/>
Początek zakresu do wstawienia.

*ostatniego*<br/>
Koniec zakresu do wstawienia.

*pred*<br/>
Predykat porządkowania dla kontrolowanej sekwencji.

*Kliknij*<br/>
Obiekt lub zakres do wstawienia.

### <a name="remarks"></a>Uwagi

Konstruktor:

`multimap();`

Inicjuje kontrolowaną sekwencję bez elementów z domyślnym predykatem kolejności `key_compare()` . Służy do określania pustej początkowej kontrolowanej sekwencji przy użyciu domyślnego predykatu porządkowania.

Konstruktor:

`explicit multimap(key_compare^ pred);`

Inicjuje kontrolowaną sekwencję bez elementów z predykatem porządkowania *pred*. Służy do określania pustej początkowej kontrolowanej sekwencji z określonym predykatem kolejności.

Konstruktor:

`multimap(multimap<Key, Mapped>% right);`

Inicjuje kontrolowaną sekwencję z sekwencją [ `right.begin()` , `right.end()` ) z domyślnym predykatem kolejności. Służy do określenia początkowej kontrolowanej sekwencji, która jest kopią sekwencji kontrolowanej *przez obiekt multimap*z zastosowaniem domyślnego predykatu kolejności.

Konstruktor:

`multimap(multimap<Key, Mapped>^ right);`

Inicjuje kontrolowaną sekwencję z sekwencją [ `right->begin()` , `right->end()` ) z domyślnym predykatem kolejności. Służy do określenia początkowej kontrolowanej sekwencji, która jest kopią sekwencji kontrolowanej *przez obiekt multimap*z zastosowaniem domyślnego predykatu kolejności.

Konstruktor:

`template<typename InIter> multimap(InIter first, InIter last);`

Inicjuje kontrolowaną sekwencję z sekwencją [ `first` , `last` ) z domyślnym predykatem kolejności. Służy do Przekształć sekwencję na kopię innej sekwencji z domyślnym predykatem kolejności.

Konstruktor:

`template<typename InIter> multimap(InIter first, InIter last, key_compare^ pred);`

Inicjuje kontrolowaną sekwencję z sekwencją [ `first` , `last` ) z predykatem porządkowania *pred*. Służy do Przekształć sekwencję na kopię innej sekwencji z określonym predykatem kolejności.

Konstruktor:

`multimap(System::Collections::Generic::IEnumerable<Key>^ right);`

Inicjuje kontrolowaną sekwencję z sekwencją wyznaczonej przez moduł wyliczający *po prawej stronie*przy użyciu domyślnego predykatu porządkowania. Jest on używany do kontrolowania kontrolowanej sekwencji kopii kolejnej sekwencji opisanej przez moduł wyliczający z domyślnym predykatem kolejności.

Konstruktor:

`multimap(System::Collections::Generic::IEnumerable<Key>^ right, key_compare^ pred);`

Inicjuje kontrolowaną sekwencję z sekwencją wyznaczonej przez moduł wyliczający *po prawej stronie*z predykatem porządkowania *pred*. Jest on używany do kontrolowania kontrolowanej sekwencji kopii kolejnej sekwencji opisanej przez moduł wyliczający z określonym predykatem kolejności.

### <a name="example"></a>Przykład

```cpp
// cliext_multimap_construct.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::multimap<wchar_t, int> Mymultimap;
int main()
    {
// construct an empty container
    Mymultimap c1;
    System::Console::WriteLine("size() = {0}", c1.size());

    c1.insert(Mymultimap::make_value(L'a', 1));
    c1.insert(Mymultimap::make_value(L'b', 2));
    c1.insert(Mymultimap::make_value(L'c', 3));
    for each (Mymultimap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // construct with an ordering rule
    Mymultimap c2 = cliext::greater_equal<wchar_t>();
    System::Console::WriteLine("size() = {0}", c2.size());

    c2.insert(c1.begin(), c1.end());
    for each (Mymultimap::value_type elem in c2)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // construct with an iterator range
    Mymultimap c3(c1.begin(), c1.end());
    for each (Mymultimap::value_type elem in c3)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // construct with an iterator range and an ordering rule
    Mymultimap c4(c1.begin(), c1.end(),
        cliext::greater_equal<wchar_t>());
    for each (Mymultimap::value_type elem in c4)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // construct with an enumeration
    Mymultimap c5(   // NOTE: cast is not needed
        (System::Collections::Generic::IEnumerable<
            Mymultimap::value_type>^)%c3);
    for each (Mymultimap::value_type elem in c5)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // construct with an enumeration and an ordering rule
    Mymultimap c6(   // NOTE: cast is not needed
        (System::Collections::Generic::IEnumerable<
            Mymultimap::value_type>^)%c3,
                cliext::greater_equal<wchar_t>());
    for each (Mymultimap::value_type elem in c6)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // construct by copying another container
    Mymultimap c7(c4);
    for each (Mymultimap::value_type elem in c7)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // construct by copying a container handle
    Mymultimap c8(%c3);
    for each (Mymultimap::value_type elem in c8)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
size() = 0
[a 1] [b 2] [c 3]
size() = 0
[c 3] [b 2] [a 1]
[a 1] [b 2] [c 3]
[c 3] [b 2] [a 1]
[a 1] [b 2] [c 3]
[c 3] [b 2] [a 1]
[c 3] [b 2] [a 1]
[a 1] [b 2] [c 3]
```

## <a name="multimapoperator-stlclr"></a><a name="op_as"></a> multimap:: operator = (STL/CLR)

Zastępuje kontrolowaną sekwencję.

### <a name="syntax"></a>Składnia

```cpp
multimap<Key, Mapped>% operator=(multimap<Key, Mapped>% right);
```

#### <a name="parameters"></a>Parametry

*Kliknij*<br/>
Kontener do skopiowania.

### <a name="remarks"></a>Uwagi

Operator elementu członkowskiego kopiuje *prawo* do obiektu, a następnie zwraca **`*this`** . Służy do zastępowania kontrolowanej sekwencji kopią kontrolowanej sekwencji *po prawej stronie*.

### <a name="example"></a>Przykład

```cpp
// cliext_multimap_operator_as.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::multimap<wchar_t, int> Mymultimap;
int main()
    {
    Mymultimap c1;
    c1.insert(Mymultimap::make_value(L'a', 1));
    c1.insert(Mymultimap::make_value(L'b', 2));
    c1.insert(Mymultimap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymultimap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // assign to a new container
    Mymultimap c2;
    c2 = c1;
// display contents " [a 1] [b 2] [c 3]"
    for each (Mymultimap::value_type elem in c2)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
[a 1] [b 2] [c 3]
```

## <a name="multimaprbegin-stlclr"></a><a name="rbegin"></a> multimap:: rbegin (STL/CLR)

Określa początek odwróconej sekwencji kontrolowanej.

### <a name="syntax"></a>Składnia

```cpp
reverse_iterator rbegin();
```

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca iterator odwrotny, który wyznacza ostatni element kontrolowanej sekwencji lub tuż poza początkiem pustej sekwencji. W związku z tym określa `beginning` odwrotną sekwencję. Służy do uzyskania iteratora, który wyznacza `current` początek kontrolowanej sekwencji widoczny w kolejności odwrotnej, ale jego stan może ulec zmianie w przypadku zmiany długości kontrolowanej sekwencji.

### <a name="example"></a>Przykład

```cpp
// cliext_multimap_rbegin.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::multimap<wchar_t, int> Mymultimap;
int main()
    {
    Mymultimap c1;
    c1.insert(Mymultimap::make_value(L'a', 1));
    c1.insert(Mymultimap::make_value(L'b', 2));
    c1.insert(Mymultimap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymultimap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // inspect first two items in reversed sequence
    Mymultimap::reverse_iterator rit = c1.rbegin();
    System::Console::WriteLine("*rbegin() = [{0} {1}]",
        rit->first, rit->second);
    ++rit;
    System::Console::WriteLine("*++rbegin() = [{0} {1}]",
        rit->first, rit->second);
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
*rbegin() = [c 3]
*++rbegin() = [b 2]
```

## <a name="multimapreference-stlclr"></a><a name="reference"></a> multimap:: Reference (STL/CLR)

Typ odwołania do elementu.

### <a name="syntax"></a>Składnia

```cpp
typedef value_type% reference;
```

### <a name="remarks"></a>Uwagi

Typ opisuje odwołanie do elementu.

### <a name="example"></a>Przykład

```cpp
// cliext_multimap_reference.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::multimap<wchar_t, int> Mymultimap;
int main()
    {
    Mymultimap c1;
    c1.insert(Mymultimap::make_value(L'a', 1));
    c1.insert(Mymultimap::make_value(L'b', 2));
    c1.insert(Mymultimap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    Mymultimap::iterator it = c1.begin();
    for (; it != c1.end(); ++it)
        {   // get a reference to an element
        Mymultimap::reference ref = *it;
        System::Console::Write("[{0} {1}] ", ref->first, ref->second);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
```

## <a name="multimaprend-stlclr"></a><a name="rend"></a> multimap:: rend (STL/CLR)

Określa koniec odwróconej kontrolowanej sekwencji.

### <a name="syntax"></a>Składnia

```cpp
reverse_iterator rend();
```

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca iterator odwrotny, który wskazuje tuż poza początkiem kontrolowanej sekwencji. W związku z tym określa `end` odwrotną sekwencję. Służy do uzyskania iteratora, który wyznacza `current` koniec kontrolowanej sekwencji widoczny w odwrotnej kolejności, ale jego stan może ulec zmianie w przypadku zmiany długości kontrolowanej sekwencji.

### <a name="example"></a>Przykład

```cpp
// cliext_multimap_rend.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::multimap<wchar_t, int> Mymultimap;
int main()
    {
    Mymultimap c1;
    c1.insert(Mymultimap::make_value(L'a', 1));
    c1.insert(Mymultimap::make_value(L'b', 2));
    c1.insert(Mymultimap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymultimap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // inspect first two items in reversed sequence
    Mymultimap::reverse_iterator rit = c1.rend();
    --rit;
    --rit;
    System::Console::WriteLine("*-- --rend() = [{0} {1}]",
        rit->first, rit->second);
    ++rit;
    System::Console::WriteLine("*--rend() = [{0} {1}]",
        rit->first, rit->second);
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
*-- --rend() = [b 2]
*--rend() = [a 1]
```

## <a name="multimapreverse_iterator-stlclr"></a><a name="reverse_iterator"></a> multimap:: reverse_iterator (STL/CLR)

Typ iteratora odwrotnego dla kontrolowanej sekwencji.

### <a name="syntax"></a>Składnia

```cpp
typedef T3 reverse_iterator;
```

### <a name="remarks"></a>Uwagi

Typ opisuje obiekt nieokreślonego typu `T3` , który może być używany jako iterator odwrotny dla kontrolowanej sekwencji.

### <a name="example"></a>Przykład

```cpp
// cliext_multimap_reverse_iterator.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::multimap<wchar_t, int> Mymultimap;
int main()
    {
    Mymultimap c1;
    c1.insert(Mymultimap::make_value(L'a', 1));
    c1.insert(Mymultimap::make_value(L'b', 2));
    c1.insert(Mymultimap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]" reversed
    Mymultimap::reverse_iterator rit = c1.rbegin();
    for (; rit != c1.rend(); ++rit)
        System::Console::Write("[{0} {1}] ", rit->first, rit->second);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
[c 3] [b 2] [a 1]
```

## <a name="multimapsize-stlclr"></a><a name="size"></a> multimap:: size (STL/CLR)

Liczy liczbę elementów.

### <a name="syntax"></a>Składnia

```cpp
size_type size();
```

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca długość kontrolowanej sekwencji. Służy do określania liczby elementów aktualnie w kontrolowanej sekwencji. Jeśli dowiesz się, czy sekwencja ma rozmiar różny od zera, zobacz [multimap:: empty (STL/CLR)](#empty) `()` .

### <a name="example"></a>Przykład

```cpp
// cliext_multimap_size.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::multimap<wchar_t, int> Mymultimap;
int main()
    {
    Mymultimap c1;
    c1.insert(Mymultimap::make_value(L'a', 1));
    c1.insert(Mymultimap::make_value(L'b', 2));
    c1.insert(Mymultimap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymultimap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // clear the container and reinspect
    c1.clear();
    System::Console::WriteLine("size() = {0} after clearing", c1.size());

    // add elements and clear again
    c1.insert(Mymultimap::make_value(L'd', 4));
    c1.insert(Mymultimap::make_value(L'e', 5));
    System::Console::WriteLine("size() = {0} after adding 2", c1.size());
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
size() = 0 after clearing
size() = 2 after adding 2
```

## <a name="multimapsize_type-stlclr"></a><a name="size_type"></a> multimap:: size_type (STL/CLR)

Typ podpisanej odległości między dwoma elementami.

### <a name="syntax"></a>Składnia

```cpp
typedef int size_type;
```

### <a name="remarks"></a>Uwagi

Typ opisuje nieujemną liczbę elementów.

### <a name="example"></a>Przykład

```cpp
// cliext_multimap_size_type.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::multimap<wchar_t, int> Mymultimap;
int main()
    {
    Mymultimap c1;
    c1.insert(Mymultimap::make_value(L'a', 1));
    c1.insert(Mymultimap::make_value(L'b', 2));
    c1.insert(Mymultimap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymultimap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // compute positive difference
    Mymultimap::size_type diff = 0;
    for (Mymultimap::iterator it = c1.begin(); it != c1.end(); ++it)
        ++diff;
    System::Console::WriteLine("end()-begin() = {0}", diff);
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
end()-begin() = 3
```

## <a name="multimapswap-stlclr"></a><a name="swap"></a> multimap:: swap (STL/CLR)

Zamienia zawartości dwóch kontenerów.

### <a name="syntax"></a>Składnia

```cpp
void swap(multimap<Key, Mapped>% right);
```

#### <a name="parameters"></a>Parametry

*Kliknij*<br/>
Kontener, za pomocą którego ma zostać zamieniony zawartość.

### <a name="remarks"></a>Uwagi

Funkcja członkowska zamienia kontrolowane sekwencje między **`this`** i *po prawej*. Robi to w stałym czasie i nie zgłasza wyjątków. Jest ona używana jako Szybka metoda wymiany zawartości dwóch kontenerów.

### <a name="example"></a>Przykład

```cpp
// cliext_multimap_swap.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::multimap<wchar_t, int> Mymultimap;
int main()
    {
    Mymultimap c1;
    c1.insert(Mymultimap::make_value(L'a', 1));
    c1.insert(Mymultimap::make_value(L'b', 2));
    c1.insert(Mymultimap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymultimap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // construct another container with repetition of values
    Mymultimap c2;
    c2.insert(Mymultimap::make_value(L'd', 4));
    c2.insert(Mymultimap::make_value(L'e', 5));
    c2.insert(Mymultimap::make_value(L'f', 6));
    for each (Mymultimap::value_type elem in c2)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // swap and redisplay
    c1.swap(c2);
    for each (Mymultimap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    for each (Mymultimap::value_type elem in c2)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
[d 4] [e 5] [f 6]
[d 4] [e 5] [f 6]
[a 1] [b 2] [c 3]
```

## <a name="multimapto_array-stlclr"></a><a name="to_array"></a> multimap:: to_array (STL/CLR)

Kopiuje przekontrolowaną sekwencję do nowej tablicy.

### <a name="syntax"></a>Składnia

```cpp
cli::array<value_type>^ to_array();
```

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca tablicę zawierającą kontrolowaną sekwencję. Służy do uzyskania kopii kontrolowanej sekwencji w formularzu tablicowym.

### <a name="example"></a>Przykład

```cpp
// cliext_multimap_to_array.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::multimap<wchar_t, int> Mymultimap;
int main()
    {
    Mymultimap c1;
    c1.insert(Mymultimap::make_value(L'a', 1));
    c1.insert(Mymultimap::make_value(L'b', 2));
    c1.insert(Mymultimap::make_value(L'c', 3));

    // copy the container and modify it
    cli::array<Mymultimap::value_type>^ a1 = c1.to_array();

    c1.insert(Mymultimap::make_value(L'd', 4));
    for each (Mymultimap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // display the earlier array copy
    for each (Mymultimap::value_type elem in a1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3] [d 4]
[a 1] [b 2] [c 3]
```

## <a name="multimapupper_bound-stlclr"></a><a name="upper_bound"></a> multimap:: upper_bound (STL/CLR)

Znajduje koniec zakresu, który odpowiada określonemu kluczowi.

### <a name="syntax"></a>Składnia

```cpp
iterator upper_bound(key_type key);
```

#### <a name="parameters"></a>Parametry

*głównych*<br/>
Wartość klucza do wyszukania.

### <a name="remarks"></a>Uwagi

Funkcja członkowska określa ostatni element `X` w kontrolowanej sekwencji, który ma równoważne porządkowanie do *klucza*. Jeśli taki element nie istnieje lub `X` jest ostatnim elementem w kontrolowanej sekwencji, zwraca [multimap:: end (STL/CLR)](#end) `()` ; w przeciwnym razie zwraca iterator, który wyznacza pierwszy element poza `X` . Służy do lokalizowania końca sekwencji elementów aktualnie w kontrolowanej sekwencji, która pasuje do określonego klucza.

### <a name="example"></a>Przykład

```cpp
// cliext_multimap_upper_bound.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::multimap<wchar_t, int> Mymultimap;
int main()
    {
    Mymultimap c1;
    c1.insert(Mymultimap::make_value(L'a', 1));
    c1.insert(Mymultimap::make_value(L'b', 2));
    c1.insert(Mymultimap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymultimap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    System::Console::WriteLine("upper_bound(L'x')==end() = {0}",
        c1.upper_bound(L'x') == c1.end());

    Mymultimap::iterator it = c1.upper_bound(L'a');
    System::Console::WriteLine("*upper_bound(L'a') = [{0} {1}]",
        it->first, it->second);
    it = c1.upper_bound(L'b');
    System::Console::WriteLine("*upper_bound(L'b') = [{0} {1}]",
        it->first, it->second);
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
upper_bound(L'x')==end() = True
*upper_bound(L'a') = [b 2]
*upper_bound(L'b') = [c 3]
```

## <a name="multimapvalue_comp-stlclr"></a><a name="value_comp"></a> multimap:: value_comp (STL/CLR)

Kopiuje delegata porządkowania dla dwóch wartości elementów.

### <a name="syntax"></a>Składnia

```cpp
value_compare^ value_comp();
```

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca delegat porządkowania używany do uporządkowania kontrolowanej sekwencji. Służy do porównywania dwóch wartości elementów.

### <a name="example"></a>Przykład

```cpp
// cliext_multimap_value_comp.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymultimap;
int main()
    {
    Mymultimap c1;
    Mymultimap::value_compare^ kcomp = c1.value_comp();

    System::Console::WriteLine("compare([L'a', 1], [L'a', 1]) = {0}",
        kcomp(Mymultimap::make_value(L'a', 1),
            Mymultimap::make_value(L'a', 1)));
    System::Console::WriteLine("compare([L'a', 1], [L'b', 2]) = {0}",
        kcomp(Mymultimap::make_value(L'a', 1),
            Mymultimap::make_value(L'b', 2)));
    System::Console::WriteLine("compare([L'b', 2], [L'a', 1]) = {0}",
        kcomp(Mymultimap::make_value(L'b', 2),
            Mymultimap::make_value(L'a', 1)));
    System::Console::WriteLine();
    return (0);
    }
```

```Output
compare([L'a', 1], [L'a', 1]) = False
compare([L'a', 1], [L'b', 2]) = True
compare([L'b', 2], [L'a', 1]) = False
```

## <a name="multimapvalue_compare-stlclr"></a><a name="value_compare"></a> multimap:: value_compare (STL/CLR)

Delegat porządkowania dla dwóch wartości elementów.

### <a name="syntax"></a>Składnia

```cpp
Microsoft::VisualC::StlClr::BinaryDelegate<generic_value, generic_value, bool>
    value_compare;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla delegata, który określa kolejność argumentów wartości.

### <a name="example"></a>Przykład

```cpp
// cliext_multimap_value_compare.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymultimap;
int main()
    {
    Mymultimap c1;
    Mymultimap::value_compare^ kcomp = c1.value_comp();

    System::Console::WriteLine("compare([L'a', 1], [L'a', 1]) = {0}",
        kcomp(Mymultimap::make_value(L'a', 1),
            Mymultimap::make_value(L'a', 1)));
    System::Console::WriteLine("compare([L'a', 1], [L'b', 2]) = {0}",
        kcomp(Mymultimap::make_value(L'a', 1),
            Mymultimap::make_value(L'b', 2)));
    System::Console::WriteLine("compare([L'b', 2], [L'a', 1]) = {0}",
        kcomp(Mymultimap::make_value(L'b', 2),
            Mymultimap::make_value(L'a', 1)));
    System::Console::WriteLine();
    return (0);
    }
```

```Output
compare([L'a', 1], [L'a', 1]) = False
compare([L'a', 1], [L'b', 2]) = True
compare([L'b', 2], [L'a', 1]) = False
```

## <a name="multimapvalue_type-stlclr"></a><a name="value_type"></a> multimap:: value_type (STL/CLR)

Typ elementu.

### <a name="syntax"></a>Składnia

```cpp
typedef generic_value value_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla `generic_value` .

### <a name="example"></a>Przykład

```cpp
// cliext_multimap_value_type.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::multimap<wchar_t, int> Mymultimap;
int main()
    {
    Mymultimap c1;
    c1.insert(Mymultimap::make_value(L'a', 1));
    c1.insert(Mymultimap::make_value(L'b', 2));
    c1.insert(Mymultimap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]" using value_type
    for (Mymultimap::iterator it = c1.begin(); it != c1.end(); ++it)
        {   // store element in value_type object
        Mymultimap::value_type val = *it;
        System::Console::Write("[{0} {1}] ", val->first, val->second);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
```

## <a name="operator-multimap-stlclr"></a><a name="op_neq"></a> operator! = (multimap) (STL/CLR)

Nierówne porównanie.

### <a name="syntax"></a>Składnia

```cpp
template<typename Key,
    typename Mapped>
    bool operator!=(multimap<Key, Mapped>% left,
        multimap<Key, Mapped>% right);
```

#### <a name="parameters"></a>Parametry

*lewym*<br/>
Lewy kontener do porównania.

*Kliknij*<br/>
Prawy kontener do porównania.

### <a name="remarks"></a>Uwagi

Funkcja operatora zwraca wartość `!(left == right)` . Służy do sprawdzania, czy *lewo* nie jest uporządkowane *tak samo, jak w* przypadku porównywania dwóch map elementów według elementu.

### <a name="example"></a>Przykład

```cpp
// cliext_multimap_operator_ne.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::multimap<wchar_t, int> Mymultimap;
int main()
    {
    Mymultimap c1;
    c1.insert(Mymultimap::make_value(L'a', 1));
    c1.insert(Mymultimap::make_value(L'b', 2));
    c1.insert(Mymultimap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymultimap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // assign to a new container
    Mymultimap c2;
    c2.insert(Mymultimap::make_value(L'a', 1));
    c2.insert(Mymultimap::make_value(L'b', 2));
    c2.insert(Mymultimap::make_value(L'd', 4));

    // display contents " [a 1] [b 2] [d 4]"
    for each (Mymultimap::value_type elem in c2)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    System::Console::WriteLine("[a b c] != [a b c] is {0}",
        c1 != c1);
    System::Console::WriteLine("[a b c] != [a b d] is {0}",
        c1 != c2);
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
[a 1] [b 2] [d 4]
[a b c] != [a b c] is False
[a b c] != [a b d] is True
```

## <a name="operatorlt-multimap-stlclr"></a><a name="op_lt"></a> operator &lt; (multimap) (STL/CLR)

Lista jest mniejsza niż porównanie.

### <a name="syntax"></a>Składnia

```cpp
template<typename Key,
    typename Mapped>
    bool operator<(multimap<Key, Mapped>% left,
        multimap<Key, Mapped>% right);
```

#### <a name="parameters"></a>Parametry

*lewym*<br/>
Lewy kontener do porównania.

*Kliknij*<br/>
Prawy kontener do porównania.

### <a name="remarks"></a>Uwagi

Funkcja operator zwraca wartość true, jeśli dla najniższej pozycji `i` `!(right[i] < left[i])` ma również wartość true `left[i] < right[i]` . W przeciwnym razie zwraca go przy `left->size() < right->size()` użyciu, aby sprawdzić, czy *lewo* jest uporządkowane przed *prawem* , gdy dwa mapowania są porównywane elementów według elementu.

### <a name="example"></a>Przykład

```cpp
// cliext_multimap_operator_lt.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::multimap<wchar_t, int> Mymultimap;
int main()
    {
    Mymultimap c1;
    c1.insert(Mymultimap::make_value(L'a', 1));
    c1.insert(Mymultimap::make_value(L'b', 2));
    c1.insert(Mymultimap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymultimap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // assign to a new container
    Mymultimap c2;
    c2.insert(Mymultimap::make_value(L'a', 1));
    c2.insert(Mymultimap::make_value(L'b', 2));
    c2.insert(Mymultimap::make_value(L'd', 4));

    // display contents " [a 1] [b 2] [d 4]"
    for each (Mymultimap::value_type elem in c2)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    System::Console::WriteLine("[a b c] < [a b c] is {0}",
        c1 < c1);
    System::Console::WriteLine("[a b c] < [a b d] is {0}",
        c1 < c2);
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
[a 1] [b 2] [d 4]
[a b c] < [a b c] is False
[a b c] < [a b d] is True
```

## <a name="operatorlt-multimap-stlclr"></a><a name="op_lteq"></a> operator &lt; = (multimap) (STL/CLR)

Lista jest mniejsza niż lub równa.

### <a name="syntax"></a>Składnia

```cpp
template<typename Key,
    typename Mapped>
    bool operator<=(multimap<Key, Mapped>% left,
        multimap<Key, Mapped>% right);
```

#### <a name="parameters"></a>Parametry

*lewym*<br/>
Lewy kontener do porównania.

*Kliknij*<br/>
Prawy kontener do porównania.

### <a name="remarks"></a>Uwagi

Funkcja operatora zwraca wartość `!(right < left)` . Służy do sprawdzania *, czy nie* jest on uporządkowany po *prawej stronie* , gdy dwa mapowania są porównywane elementów według elementu.

### <a name="example"></a>Przykład

```cpp
// cliext_multimap_operator_le.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::multimap<wchar_t, int> Mymultimap;
int main()
    {
    Mymultimap c1;
    c1.insert(Mymultimap::make_value(L'a', 1));
    c1.insert(Mymultimap::make_value(L'b', 2));
    c1.insert(Mymultimap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymultimap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // assign to a new container
    Mymultimap c2;
    c2.insert(Mymultimap::make_value(L'a', 1));
    c2.insert(Mymultimap::make_value(L'b', 2));
    c2.insert(Mymultimap::make_value(L'd', 4));

    // display contents " [a 1] [b 2] [d 4]"
    for each (Mymultimap::value_type elem in c2)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    System::Console::WriteLine("[a b c] <= [a b c] is {0}",
        c1 <= c1);
    System::Console::WriteLine("[a b d] <= [a b c] is {0}",
        c2 <= c1);
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
[a 1] [b 2] [d 4]
[a b c] <= [a b c] is True
[a b d] <= [a b c] is False
```

## <a name="operator-multimap-stlclr"></a><a name="op_eq"></a> operator = = (multimap) (STL/CLR)

Wyświetl równe porównanie.

### <a name="syntax"></a>Składnia

```cpp
template<typename Key,
    typename Mapped>
    bool operator==(multimap<Key, Mapped>% left,
        multimap<Key, Mapped>% right);
```

#### <a name="parameters"></a>Parametry

*lewym*<br/>
Lewy kontener do porównania.

*Kliknij*<br/>
Prawy kontener do porównania.

### <a name="remarks"></a>Uwagi

Funkcja operator zwraca wartość true tylko wtedy, gdy sekwencje sterowane przez *lewo* i *prawo* mają taką samą długość i, dla każdej pozycji `i` `left[i] ==` `right[i]` . Służy do sprawdzania, czy *lewa* jest uporządkowana tak samo jak *w przypadku* porównywania dwóch map elementów według elementu.

### <a name="example"></a>Przykład

```cpp
// cliext_multimap_operator_eq.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::multimap<wchar_t, int> Mymultimap;
int main()
    {
    Mymultimap c1;
    c1.insert(Mymultimap::make_value(L'a', 1));
    c1.insert(Mymultimap::make_value(L'b', 2));
    c1.insert(Mymultimap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymultimap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // assign to a new container
    Mymultimap c2;
    c2.insert(Mymultimap::make_value(L'a', 1));
    c2.insert(Mymultimap::make_value(L'b', 2));
    c2.insert(Mymultimap::make_value(L'd', 4));

    // display contents " [a 1] [b 2] [d 4]"
    for each (Mymultimap::value_type elem in c2)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    System::Console::WriteLine("[a b c] == [a b c] is {0}",
        c1 == c1);
    System::Console::WriteLine("[a b c] == [a b d] is {0}",
        c1 == c2);
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
[a 1] [b 2] [d 4]
[a b c] == [a b c] is True
[a b c] == [a b d] is False
```

## <a name="operatorgt-multimap-stlclr"></a><a name="op_gt"></a> operator &gt; (multimap) (STL/CLR)

Lista większa niż porównanie.

### <a name="syntax"></a>Składnia

```cpp
template<typename Key,
    typename Mapped>
    bool operator>(multimap<Key, Mapped>% left,
        multimap<Key, Mapped>% right);
```

#### <a name="parameters"></a>Parametry

*lewym*<br/>
Lewy kontener do porównania.

*Kliknij*<br/>
Prawy kontener do porównania.

### <a name="remarks"></a>Uwagi

Funkcja operatora zwraca wartość `right` `<` `left` . Służy do sprawdzania, czy *lewa* jest uporządkowana po *prawej stronie* , gdy dwa mapowania są porównywane elementów według elementu.

### <a name="example"></a>Przykład

```cpp
// cliext_multimap_operator_gt.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::multimap<wchar_t, int> Mymultimap;
int main()
    {
    Mymultimap c1;
    c1.insert(Mymultimap::make_value(L'a', 1));
    c1.insert(Mymultimap::make_value(L'b', 2));
    c1.insert(Mymultimap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymultimap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // assign to a new container
    Mymultimap c2;
    c2.insert(Mymultimap::make_value(L'a', 1));
    c2.insert(Mymultimap::make_value(L'b', 2));
    c2.insert(Mymultimap::make_value(L'd', 4));

    // display contents " [a 1] [b 2] [d 4]"
    for each (Mymultimap::value_type elem in c2)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    System::Console::WriteLine("[a b c] > [a b c] is {0}",
        c1 > c1);
    System::Console::WriteLine("[a b d] > [a b c] is {0}",
        c2 > c1);
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
[a 1] [b 2] [d 4]
[a b c] > [a b c] is False
[a b d] > [a b c] is True
```

## <a name="operatorgt-multimap-stlclr"></a><a name="op_gteq"></a> operator &gt; = (multimap) (STL/CLR)

Lista jest większa lub równa porównaniu.

### <a name="syntax"></a>Składnia

```cpp
template<typename Key,
    typename Mapped>
    bool operator>=(multimap<Key, Mapped>% left,
        multimap<Key, Mapped>% right);
```

#### <a name="parameters"></a>Parametry

*lewym*<br/>
Lewy kontener do porównania.

*Kliknij*<br/>
Prawy kontener do porównania.

### <a name="remarks"></a>Uwagi

Funkcja operatora zwraca wartość `!(left` `<` `right)` . Służy do sprawdzania *, czy nie* jest on uporządkowany przed *uprawnieniem* , gdy dwa mapowania są porównywane elementów według elementu.

### <a name="example"></a>Przykład

```cpp
// cliext_multimap_operator_ge.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::multimap<wchar_t, int> Mymultimap;
int main()
    {
    Mymultimap c1;
    c1.insert(Mymultimap::make_value(L'a', 1));
    c1.insert(Mymultimap::make_value(L'b', 2));
    c1.insert(Mymultimap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymultimap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // assign to a new container
    Mymultimap c2;
    c2.insert(Mymultimap::make_value(L'a', 1));
    c2.insert(Mymultimap::make_value(L'b', 2));
    c2.insert(Mymultimap::make_value(L'd', 4));

    // display contents " [a 1] [b 2] [d 4]"
    for each (Mymultimap::value_type elem in c2)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    System::Console::WriteLine("[a b c] >= [a b c] is {0}",
        c1 >= c1);
    System::Console::WriteLine("[a b c] >= [a b d] is {0}",
        c1 >= c2);
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
[a 1] [b 2] [d 4]
[a b c] >= [a b c] is True
[a b c] >= [a b d] is False
```
