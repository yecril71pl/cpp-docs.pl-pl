---
title: map (STL/CLR)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- cliext::map
- cliext::map::begin
- cliext::map::clear
- cliext::map::const_iterator
- cliext::map::const_reference
- cliext::map::const_reverse_iterator
- cliext::map::count
- cliext::map::difference_type
- cliext::map::empty
- cliext::map::end
- cliext::map::equal_range
- cliext::map::erase
- cliext::map::find
- cliext::map::generic_container
- cliext::map::generic_iterator
- cliext::map::generic_reverse_iterator
- cliext::map::generic_value
- cliext::map::insert
- cliext::map::iterator
- cliext::map::key_comp
- cliext::map::key_compare
- cliext::map::key_type
- cliext::map::lower_bound
- cliext::map::make_value
- cliext::map::map
- cliext::map::mapped_type
- cliext::map::operator=
- cliext::map::operator
- cliext::map::rbegin
- cliext::map::reference
- cliext::map::rend
- cliext::map::reverse_iterator
- cliext::map::size
- cliext::map::size_type
- cliext::map::swap
- cliext::map::to_array
- cliext::map::upper_bound
- cliext::map::value_comp
- cliext::map::value_compare
- cliext::map::value_type
- cliext::operator!= (map)
- cliext::operator< (map)
- cliext::operator<= (map)
- cliext::operator== (map)
- cliext::operator> (map)
- cliext::operator>= (map)
helpviewer_keywords:
- <map> header [STL/CLR]
- map class [STL/CLR]
- <cliext/map> header [STL/CLR]
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
- map member [STL/CLR]
- mapped_type member [STL/CLR]
- operator= member [STL/CLR]
- operator member [STL/CLR]
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
- operator!= (map) member [STL/CLR]
- operator< (map) member [STL/CLR]
- operator<= (map) member [STL/CLR]
- operator== (map) member [STL/CLR]
- operator> (map) member [STL/CLR]
- operator>= (map) member [STL/CLR]
ms.assetid: 8b0a7764-b5e4-4175-a802-82b72eb8662a
ms.openlocfilehash: cd06942d3795dda9e6c6aaa8794957018fa96ace
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87216378"
---
# <a name="map-stlclr"></a>map (STL/CLR)

Klasa szablonu opisuje obiekt, który kontroluje różnej długości sekwencje elementów, które mają dostęp dwukierunkowy. Kontener służy `map` do zarządzania sekwencją elementów jako (niemal) uporządkowanym drzewem węzłów, każdy z nich przechowujący jeden element. Element składa się z klucza, do porządkowania sekwencji i mapowanej wartości, która jest przypisana do przebiegu.

W poniższym opisie `GValue` jest taka sama jak:

`Microsoft::VisualC::StlClr::GenericPair<GKey, GMapped>`

gdzie:

`GKey`jest taka sama jak *klucz* , chyba że ostatni jest typem ref, w takim przypadku jest`Key^`

`GMapped`jest taka sama jak *zamapowana* , chyba że jest to typ referencyjny, w tym przypadku jest to`Mapped^`

## <a name="syntax"></a>Składnia

```cpp
template<typename Key,
    typename Mapped>
    ref class map
        :   public
        System::ICloneable,
        System::Collections::IEnumerable,
        System::Collections::ICollection,
        System::Collections::Generic::IEnumerable<GValue>,
        System::Collections::Generic::ICollection<GValue>,
        System::Collections::Generic::IList<GValue>,
        System::Collections::Generic::IDictionary<Gkey, GMapped>,
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
|[map::const_iterator (STL/CLR)](#const_iterator)|Typ iteratora stałego dla kontrolowanej sekwencji.|
|[map::const_reference (STL/CLR)](#const_reference)|Typ stałego odwołania do elementu.|
|[map::const_reverse_iterator (STL/CLR)](#const_reverse_iterator)|Typ iteratora stałego zwrotnego dla kontrolowanej sekwencji.|
|[map::difference_type (STL/CLR)](#difference_type)|Typ (prawdopodobnie podpisany) odległości między dwoma elementami.|
|[map::generic_container (STL/CLR)](#generic_container)|Typ interfejsu generycznego dla kontenera.|
|[map::generic_iterator (STL/CLR)](#generic_iterator)|Typ iteratora dla interfejsu generycznego dla kontenera.|
|[map::generic_reverse_iterator (STL/CLR)](#generic_reverse_iterator)|Typ iteratora odwrotnego dla interfejsu generycznego dla kontenera.|
|[map::generic_value (STL/CLR)](#generic_value)|Typ elementu dla interfejsu generycznego dla kontenera.|
|[map::iterator (STL/CLR)](#iterator)|Typ iteratora dla kontrolowanej sekwencji.|
|[map::key_compare (STL/CLR)](#key_compare)|Delegat porządkowania dla dwóch kluczy.|
|[map::key_type (STL/CLR)](#key_type)|Typ klucza sortowania.|
|[map::mapped_type (STL/CLR)](#mapped_type)|Typ mapowanej wartości skojarzonej z poszczególnymi kluczami.|
|[map::reference (STL/CLR)](#reference)|Typ odwołania do elementu.|
|[map::reverse_iterator (STL/CLR)](#reverse_iterator)|Typ iteratora odwrotnego dla kontrolowanej sekwencji.|
|[map::size_type (STL/CLR)](#size_type)|Typ (nieujemnej) odległości między dwoma elementami.|
|[map::value_compare (STL/CLR)](#value_compare)|Delegat porządkowania dla dwóch wartości elementów.|
|[map::value_type (STL/CLR)](#value_type)|Typ elementu.|

|Funkcja elementów członkowskich|Opis|
|---------------------|-----------------|
|[map::begin (STL/CLR)](#begin)|Określa początek kontrolowanej sekwencji.|
|[map::clear (STL/CLR)](#clear)|Usuwa wszystkie elementy.|
|[map::count (STL/CLR)](#count)|Zlicza elementy pasujące do określonego klucza.|
|[map::empty (STL/CLR)](#empty)|Sprawdza, czy nie ma żadnych elementów.|
|[map::end (STL/CLR)](#end)|Określa koniec kontrolowanej sekwencji.|
|[map::equal_range (STL/CLR)](#equal_range)|Wyszukuje zakres, który odpowiada określonemu kluczowi.|
|[map::erase (STL/CLR)](#erase)|Usuwa elementy z określonych pozycji.|
|[map::find (STL/CLR)](#find)|Wyszukuje element, który odpowiada określonemu kluczowi.|
|[map::insert (STL/CLR)](#insert)|Dodaje elementy.|
|[map::key_comp (STL/CLR)](#key_comp)|Kopiuje delegata porządkowania dla dwóch kluczy.|
|[map::lower_bound (STL/CLR)](#lower_bound)|Znajduje początek zakresu, który odpowiada określonemu kluczowi.|
|[map::make_value (STL/CLR)](#make_value)|Konstruuje obiekt wartości.|
|[map::map (STL/CLR)](#map)|Konstruuje obiekt kontenera.|
|[map::rbegin (STL/CLR)](#rbegin)|Określa początek odwróconej sekwencji kontrolowanej.|
|[map::rend (STL/CLR)](#rend)|Określa koniec odwróconej kontrolowanej sekwencji.|
|[map::size (STL/CLR)](#size)|Liczy liczbę elementów.|
|[map::swap (STL/CLR)](#swap)|Zamienia zawartości dwóch kontenerów.|
|[map::to_array (STL/CLR)](#to_array)|Kopiuje przekontrolowaną sekwencję do nowej tablicy.|
|[map::upper_bound (STL/CLR)](#upper_bound)|Znajduje koniec zakresu, który odpowiada określonemu kluczowi.|
|[map::value_comp (STL/CLR)](#value_comp)|Kopiuje delegata porządkowania dla dwóch wartości elementów.|

|Operator|Opis|
|--------------|-----------------|
|[map::operator= (STL/CLR)](#op_as)|Zastępuje kontrolowaną sekwencję.|
|[map::operator(STL/CLR)](#op)|Mapuje klucz do skojarzonej mapowanej wartości.|
|[operator! = (map) (STL/CLR)](#op_neq)|Określa, czy `map` obiekt nie jest równy innemu `map` obiektowi.|
|[< operatora (map) (STL/CLR)](#op_lt)|Określa, czy `map` obiekt jest mniejszy niż inny `map` obiekt.|
|[operator<= (map) (STL/CLR)](#op_lteq)|Określa, czy `map` obiekt jest mniejszy niż lub równy innemu `map` obiektowi.|
|[operator = = (map) (STL/CLR)](#op_eq)|Określa, czy `map` obiekt jest równy innemu `map` obiektowi.|
|[> operatora (map) (STL/CLR)](#op_gt)|Określa, czy `map` obiekt jest większy niż inny `map` obiekt.|
|[operator>= (map) (STL/CLR)](#op_gteq)|Określa, czy `map` obiekt jest większy lub równy innemu `map` obiektowi.|

## <a name="interfaces"></a>Interfejsy

|Interfejs|Opis|
|---------------|-----------------|
|<xref:System.ICloneable>|Duplikowanie obiektu.|
|<xref:System.Collections.IEnumerable>|Sekwencja przez elementy.|
|<xref:System.Collections.ICollection>|Obsługa grupy elementów.|
|<xref:System.Collections.Generic.IEnumerable%601>|Sekwencja przez wpisane elementy.|
|<xref:System.Collections.Generic.ICollection%601>|Obsługuj grupę wpisanych elementów.|
|<xref:System.Collections.Generic.IDictionary%602>|Obsługuj grupę par {Key, Value}.|
|ITree<klucz, wartość>|Obsługa kontenera ogólnego.|

## <a name="remarks"></a>Uwagi

Obiekt przydziela i zwalnia magazyn dla sekwencji, która kontroluje jako pojedyncze węzły. Wstawia elementy do (niemal) zrównoważonego drzewa, które zachowuje uporządkowane przez zmianę linków między węzłami, a nigdy przez kopiowanie zawartości jednego węzła do drugiego. Oznacza to, że można wstawiać i usuwać elementy swobodnie bez zakłócania pozostałych elementów.

Obiekt porządkuje sekwencję, która kontroluje, wywołując zapisany obiekt delegata typu [map:: key_compare (STL/CLR)](../dotnet/map-key-compare-stl-clr.md). Podczas konstruowania mapy można określić przechowywany obiekt delegowany. Jeśli określisz brak obiektu delegowanego, wartością domyślną jest porównanie `operator<(key_type, key_type)` . Dostęp do tego przechowywanego obiektu można uzyskać, wywołując mapę funkcji składowej [:: key_comp (STL/CLR)](../dotnet/map-key-comp-stl-clr.md) `()` .

Taki obiekt delegata musi nałożyć ścisłe słabe porządkowanie dla kluczy typu [map:: key_type (STL/CLR)](../dotnet/map-key-type-stl-clr.md). Oznacza to, że dla dowolnych dwóch kluczy `X` i `Y` :

`key_comp()(X, Y)`zwraca ten sam wynik Boolean dla każdego wywołania.

Jeśli `key_comp()(X, Y)` ma wartość true, a następnie `key_comp()(Y, X)` musi mieć wartość false.

Jeśli `key_comp()(X, Y)` ma wartość true, `X` to przed `Y` .

Jeśli `!key_comp()(X, Y) && !key_comp()(Y, X)` ma wartość true, wówczas `X` i `Y` są określane jako równoważne porządkowanie.

Dla każdego elementu `X` , który poprzedza `Y` w kontrolowanej sekwencji, `key_comp()(Y, X)` ma wartość false. (Dla domyślnego obiektu delegowanego klucze nigdy nie zmniejszają wartości). W przeciwieństwie do [mapy](../dotnet/map-stl-clr.md)klas szablonu, obiekt klasy szablonu `map` nie wymaga, aby klucze dla wszystkich elementów były unikatowe. (Co najmniej dwa klucze mogą mieć równoważne porządkowanie).

Każdy element zawiera oddzielny klucz i zamapowane wartości. Sekwencja jest reprezentowana w sposób, który pozwala na wyszukiwanie, wstawianie i usuwanie dowolnego elementu z liczbą operacji proporcjonalnie do logarytmu liczby elementów w sekwencji (czas logarytmu). Ponadto, wstawianie elementu nie unieważnia iteratorów, a usuwanie elementu unieważnia tylko te iteratory, które wskazują na usunięty element.

Mapa obsługuje Iteratory dwukierunkowe, co oznacza, że można przechodzić do sąsiadujących elementów przy użyciu iteratora, który wyznacza element w kontrolowanej sekwencji. Specjalny węzeł główny odpowiada iteratorowi zwróconemu przez [map:: end (STL/CLR)](../dotnet/map-end-stl-clr.md) `()` . Można zmniejszyć ten iterator, aby dotrzeć do ostatniego elementu w kontrolowanej sekwencji, jeśli jest obecny. Można zwiększyć iterator mapy w celu uzyskania dostępu do węzła głównego, a następnie będzie on porównywany z równą `end()` . Ale nie można usunąć odwołania do iteratora zwróconego przez `end()` .

Należy zauważyć, że nie można odwołać się do elementu mapy bezpośrednio przy użyciu jego pozycji liczbowej — który wymaga iteratora dostępu swobodnego.

Iterator mapy przechowuje uchwyt do skojarzonego z nim węzła mapy, który z kolei przechowuje dojście do skojarzonego kontenera. Iteratorów można używać tylko ze skojarzonymi obiektami kontenera. Iterator mapy pozostaje prawidłowy, tak długo, jak skojarzony węzeł mapy jest skojarzony z niepewną mapą. Ponadto prawidłowy iterator jest dereferencable — można go użyć w celu uzyskania dostępu do lub zmiany wartości elementu, który wyznacza, tak długo, jak nie jest równa `end()` .

Wymazywanie lub usuwanie elementu wywołuje destruktor dla jego przechowywanej wartości. Niszczenie kontenera powoduje wymazanie wszystkich elementów. W tym celu kontener, którego typem elementu jest Klasa ref, zapewnia, że żadne elementy nie wyprowadzą kontenera. Należy jednak zauważyć, że kontener dojść *nie* niszczy swoich elementów.

## <a name="members"></a>Elementy członkowskie

## <a name="mapbegin-stlclr"></a><a name="begin"></a>map:: begin (STL/CLR)

Określa początek kontrolowanej sekwencji.

### <a name="syntax"></a>Składnia

```cpp
iterator begin();
```

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca iterator dwukierunkowy, który wyznacza pierwszy element kontrolowanej sekwencji lub tuż poza końcem pustej sekwencji. Służy do uzyskania iteratora, który wyznacza `current` początek kontrolowanej sekwencji, ale jego stan może ulec zmianie w przypadku zmiany długości kontrolowanej sekwencji.

### <a name="example"></a>Przykład

```cpp
// cliext_map_begin.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));
    c1.insert(Mymap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // inspect first two items
    Mymap::iterator it = c1.begin();
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

## <a name="mapclear-stlclr"></a><a name="clear"></a>map:: Clear (STL/CLR)

Usuwa wszystkie elementy.

### <a name="syntax"></a>Składnia

```cpp
void clear();
```

### <a name="remarks"></a>Uwagi

Funkcja członkowska skutecznie wywołuje mapowanie [:: Erase (STL/CLR)](../dotnet/map-erase-stl-clr.md) `(` [map:: begin (STL/CLR)](../dotnet/map-begin-stl-clr.md) `(),` [map:: end (STL/CLR)](../dotnet/map-end-stl-clr.md) `())` . Jest on używany do upewnienia się, że kontrolowana sekwencja jest pusta.

### <a name="example"></a>Przykład

```cpp
// cliext_map_clear.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));
    c1.insert(Mymap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // clear the container and reinspect
    c1.clear();
    System::Console::WriteLine("size() = {0}", c1.size());

    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));

    // display contents " [a 1] [b 2]"
    for each (Mymap::value_type elem in c1)
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

## <a name="mapconst_iterator-stlclr"></a><a name="const_iterator"></a>map:: const_iterator (STL/CLR)

Typ iteratora stałego dla kontrolowanej sekwencji.

### <a name="syntax"></a>Składnia

```cpp
typedef T2 const_iterator;
```

### <a name="remarks"></a>Uwagi

Typ opisuje obiekt nieokreślonego typu `T2` , który może obsłużyć jako stały iterator dwukierunkowy dla kontrolowanej sekwencji.

### <a name="example"></a>Przykład

```cpp
// cliext_map_const_iterator.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));
    c1.insert(Mymap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    Mymap::const_iterator cit = c1.begin();
    for (; cit != c1.end(); ++cit)
        System::Console::Write("[{0} {1}] ", cit->first, cit->second);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
```

## <a name="mapconst_reference-stlclr"></a><a name="const_reference"></a>map:: const_reference (STL/CLR)

Typ stałego odwołania do elementu.

### <a name="syntax"></a>Składnia

```cpp
typedef value_type% const_reference;
```

### <a name="remarks"></a>Uwagi

Typ opisuje stałe odwołanie do elementu.

### <a name="example"></a>Przykład

```cpp
// cliext_map_const_reference.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));
    c1.insert(Mymap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    Mymap::const_iterator cit = c1.begin();
    for (; cit != c1.end(); ++cit)
        {   // get a const reference to an element
        Mymap::const_reference cref = *cit;
        System::Console::Write("[{0} {1}] ", cref->first, cref->second);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
```

## <a name="mapconst_reverse_iterator-stlclr"></a><a name="const_reverse_iterator"></a>map:: const_reverse_iterator (STL/CLR)

Typ iteratora stałego zwrotnego dla kontrolowanej sekwencji.

### <a name="syntax"></a>Składnia

```cpp
typedef T4 const_reverse_iterator;
```

### <a name="remarks"></a>Uwagi

Typ opisuje obiekt nieokreślonego typu `T4` , który może być używany jako ciągły iterator odwrotny dla kontrolowanej sekwencji.

### <a name="example"></a>Przykład

```cpp
// cliext_map_const_reverse_iterator.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));
    c1.insert(Mymap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]" reversed
    Mymap::const_reverse_iterator crit = c1.rbegin();
    for (; crit != c1.rend(); ++crit)
        System::Console::Write("[{0} {1}] ", crit->first, crit->second);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
[c 3] [b 2] [a 1]
```

## <a name="mapcount-stlclr"></a><a name="count"></a>map:: Count (STL/CLR)

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
// cliext_map_count.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));
    c1.insert(Mymap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymap::value_type elem in c1)
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

## <a name="mapdifference_type-stlclr"></a><a name="difference_type"></a>map::d ifference_type (STL/CLR)

Typy podpisanej odległości między dwoma elementami.

### <a name="syntax"></a>Składnia

```cpp
typedef int difference_type;
```

### <a name="remarks"></a>Uwagi

Typ opisuje prawdopodobnie ujemną liczbę elementów.

### <a name="example"></a>Przykład

```cpp
// cliext_map_difference_type.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));
    c1.insert(Mymap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // compute positive difference
    Mymap::difference_type diff = 0;
    for (Mymap::iterator it = c1.begin(); it != c1.end(); ++it)
        ++diff;
    System::Console::WriteLine("end()-begin() = {0}", diff);

    // compute negative difference
    diff = 0;
    for (Mymap::iterator it = c1.end(); it != c1.begin(); --it)
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

## <a name="mapempty-stlclr"></a><a name="empty"></a>map:: empty (STL/CLR)

Sprawdza, czy nie ma żadnych elementów.

### <a name="syntax"></a>Składnia

```cpp
bool empty();
```

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca wartość true dla pustej kontrolowanej sekwencji. Jest to odpowiednik [mapy:: size (STL/CLR)](../dotnet/map-size-stl-clr.md) `() == 0` . Służy do sprawdzania, czy mapa jest pusta.

### <a name="example"></a>Przykład

```cpp
// cliext_map_empty.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));
    c1.insert(Mymap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymap::value_type elem in c1)
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

## <a name="mapend-stlclr"></a><a name="end"></a>map:: end (STL/CLR)

Określa koniec kontrolowanej sekwencji.

### <a name="syntax"></a>Składnia

```cpp
iterator end();
```

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca iterator dwukierunkowy, który wskazuje tuż poza końcem kontrolowanej sekwencji. Służy do uzyskania iteratora, który wyznacza koniec kontrolowanej sekwencji; jego stan nie zmienia się w przypadku zmiany długości kontrolowanej sekwencji.

### <a name="example"></a>Przykład

```cpp
// cliext_map_end.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));
    c1.insert(Mymap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // inspect last two items
    Mymap::iterator it = c1.end();
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

## <a name="mapequal_range-stlclr"></a><a name="equal_range"></a>map:: equal_range (STL/CLR)

Wyszukuje zakres, który odpowiada określonemu kluczowi.

### <a name="syntax"></a>Składnia

```cpp
cliext::pair<iterator, iterator> equal_range(key_type key);
```

#### <a name="parameters"></a>Parametry

*głównych*<br/>
Wartość klucza do wyszukania.

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca parę iteratorów `cliext::pair<iterator, iterator>(` [map:: lower_bound (STL/CLR)](../dotnet/map-lower-bound-stl-clr.md) `(key),` [map:: upper_bound (STL/CLR)](../dotnet/map-upper-bound-stl-clr.md) `(key))` . Służy do określania zakresu elementów aktualnie w kontrolowanej sekwencji, która pasuje do określonego klucza.

### <a name="example"></a>Przykład

```cpp
// cliext_map_equal_range.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
typedef Mymap::pair_iter_iter Pairii;
int main()
    {
    Mymap c1;
    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));
    c1.insert(Mymap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymap::value_type elem in c1)
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

## <a name="maperase-stlclr"></a><a name="erase"></a>map:: Erase (STL/CLR)

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

*miejscu*<br/>
Element do wymazania.

### <a name="remarks"></a>Uwagi

Pierwsza funkcja członkowska usuwa element kontrolowanej sekwencji wskazywany przez *WHERE*, a zwraca iterator, który wyznacza pierwszy element, który został poza elementem usunięty, lub [map:: end (STL/CLR)](../dotnet/map-end-stl-clr.md) , `()` Jeśli taki element nie istnieje. Służy do usuwania pojedynczego elementu.

Druga funkcja członkowska usuwa elementy z kontrolowanej sekwencji z zakresu [ `first` , `last` ) i zwraca iterator, który wyznacza pierwszy element pozostały poza elementami usuniętymi lub `end()` Jeśli taki element nie istnieje. Jest on używany do usuwania elementów sąsiadujących lub więcej.

Trzecia funkcja członkowska usuwa każdy element kontrolowanej sekwencji, którego klucz ma równoważne porządkowanie do *klucza*i zwraca liczbę usuniętych elementów. Służy do usuwania i zliczania wszystkich elementów, które pasują do określonego klucza.

Każdy element wymazuje czas proporcjonalny do logarytmu liczby elementów w kontrolowanej sekwencji.

### <a name="example"></a>Przykład

```cpp
// cliext_map_erase.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    cliext::map<wchar_t, int> c1;
    c1.insert(cliext::map<wchar_t, int>::make_value(L'a', 1));
    c1.insert(cliext::map<wchar_t, int>::make_value(L'b', 2));
    c1.insert(cliext::map<wchar_t, int>::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (cliext::map<wchar_t, int>::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // erase an element and reinspect
    cliext::map<wchar_t, int>::iterator it =
        c1.erase(c1.begin());
    System::Console::WriteLine("erase(begin()) = [{0} {1}]",
        it->first, it->second);

    // add elements and display " b c d e"
    c1.insert(cliext::map<wchar_t, int>::make_value(L'd', 4));
    c1.insert(cliext::map<wchar_t, int>::make_value(L'e', 5));
    for each (cliext::map<wchar_t, int>::value_type elem in c1)
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

## <a name="mapfind-stlclr"></a><a name="find"></a>map:: Find (STL/CLR)

Wyszukuje element, który odpowiada określonemu kluczowi.

### <a name="syntax"></a>Składnia

```cpp
iterator find(key_type key);
```

#### <a name="parameters"></a>Parametry

*głównych*<br/>
Wartość klucza do wyszukania.

### <a name="remarks"></a>Uwagi

Jeśli co najmniej jeden element w kontrolowanej sekwencji ma równoważne porządkowanie z *kluczem*, funkcja członkowska zwraca iterator wyznaczający jeden z tych elementów. w przeciwnym razie zwraca [mapę:: end (STL/CLR)](../dotnet/map-end-stl-clr.md) `()` . Służy do lokalizowania elementu w kontrolowanej sekwencji, który odpowiada określonemu kluczowi.

### <a name="example"></a>Przykład

```cpp
// cliext_map_find.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));
    c1.insert(Mymap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    System::Console::WriteLine("find {0} = {1}",
        L'A', c1.find(L'A') != c1.end());

    Mymap::iterator it = c1.find(L'b');
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

## <a name="mapgeneric_container-stlclr"></a><a name="generic_container"></a>map:: generic_container (STL/CLR)

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
// cliext_map_generic_container.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));
    c1.insert(Mymap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // construct a generic container
    Mymap::generic_container^ gc1 = %c1;
    for each (Mymap::value_type elem in gc1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // modify generic and display original
    gc1->insert(Mymap::make_value(L'd', 4));
    for each (Mymap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // modify original and display generic
    c1.insert(Mymap::make_value(L'e', 5));
    for each (Mymap::value_type elem in gc1)
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

## <a name="mapgeneric_iterator-stlclr"></a><a name="generic_iterator"></a>map:: generic_iterator (STL/CLR)

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
// cliext_map_generic_iterator.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));
    c1.insert(Mymap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // construct a generic container
    Mymap::generic_container^ gc1 = %c1;
    for each (Mymap::value_type elem in gc1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // get an element and display it
    Mymap::generic_iterator gcit = gc1->begin();
    Mymap::generic_value gcval = *gcit;
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

## <a name="mapgeneric_reverse_iterator-stlclr"></a><a name="generic_reverse_iterator"></a>map:: generic_reverse_iterator (STL/CLR)

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
// cliext_map_generic_reverse_iterator.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));
    c1.insert(Mymap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // construct a generic container
    Mymap::generic_container^ gc1 = %c1;
    for each (Mymap::value_type elem in gc1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // get an element and display it
    Mymap::generic_reverse_iterator gcit = gc1->rbegin();
    Mymap::generic_value gcval = *gcit;
    System::Console::WriteLine("[{0} {1}] ", gcval->first, gcval->second);
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
[a 1] [b 2] [c 3]
[c 3]
```

## <a name="mapgeneric_value-stlclr"></a><a name="generic_value"></a>map:: generic_value (STL/CLR)

Typ elementu do użycia z interfejsem ogólnym dla kontenera.

### <a name="syntax"></a>Składnia

```cpp
typedef GValue generic_value;
```

### <a name="remarks"></a>Uwagi

Typ opisuje obiekt typu `GValue` , który opisuje wartość przechowywanego elementu do użycia z interfejsem ogólnym dla tej klasy kontenera szablonu.

### <a name="example"></a>Przykład

```cpp
// cliext_map_generic_value.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));
    c1.insert(Mymap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // construct a generic container
    Mymap::generic_container^ gc1 = %c1;
    for each (Mymap::value_type elem in gc1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // get an element and display it
    Mymap::generic_iterator gcit = gc1->begin();
    Mymap::generic_value gcval = *gcit;
    System::Console::WriteLine("[{0} {1}] ", gcval->first, gcval->second);
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
[a 1] [b 2] [c 3]
[a 1]
```

## <a name="mapinsert-stlclr"></a><a name="insert"></a>map:: Insert (STL/CLR)

Dodaje elementy.

### <a name="syntax"></a>Składnia

```cpp
cliext::pair<iterator, bool> insert(value_type val);
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

*miejscu*<br/>
Gdzie w kontenerze do wstawienia (tylko Wskazówka).

### <a name="remarks"></a>Uwagi

Każda funkcja członkowska wstawia sekwencję określoną przez pozostałe operandy.

Pierwsza funkcja członkowska przedsięwzięciach do wstawienia elementu z wartością *Val*i zwraca parę wartości `X` . Jeśli `X.second` ma wartość true, `X.first` oznacza nowo wstawiony element; w przeciwnym razie `X.first` oznacza element o równoważnej kolejności, która już istnieje, a nowy element nie zostanie wstawiony. Służy do wstawiania pojedynczego elementu.

Druga funkcja członkowska wstawia element z wartością *Val*przy użyciu instrukcji *WHERE* jako wskazówkę (w celu zwiększenia wydajności) i zwraca iterator, który wyznacza nowo wstawiony element. Służy do wstawiania pojedynczego elementu, który może być przyległy do elementu, który znasz.

Trzecia funkcja członkowska wstawia sekwencję [ `first` , `last` ). Służy do wstawiania elementów, które zostały skopiowane z innej sekwencji.

Czwarta funkcja członkowska wstawia sekwencję wydaną po *prawej stronie*. Służy do wstawiania sekwencji opisanej przez moduł wyliczający.

Każde wstawienie elementu ma czas proporcjonalny do logarytmu liczby elementów w kontrolowanej sekwencji. Wstawianie może odbywać się w amortyzowanym stałym czasie, Jednakże z uwzględnieniem wskazówki, która wyznacza element przyległy do punktu wstawiania.

### <a name="example"></a>Przykład

```cpp
// cliext_map_insert.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
typedef Mymap::pair_iter_bool Pairib;
int main()
    {
    Mymap c1;
    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));
    c1.insert(Mymap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // insert a single value, unique and duplicate
// insert a single value, success and failure
    Pairib pair1 = c1.insert(Mymap::make_value(L'x', 24));
    System::Console::WriteLine("insert([L'x' 24]) = [[{0} {1}] {2}]",
        pair1.first->first, pair1.first->second, pair1.second);

    pair1 = c1.insert(Mymap::make_value(L'b', 2));
    System::Console::WriteLine("insert([L'b' 2]) = [[{0} {1}] {2}]",
        pair1.first->first, pair1.first->second, pair1.second);

    for each (Mymap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // insert a single value with hint
    Mymap::iterator it =
        c1.insert(c1.begin(), Mymap::make_value(L'y', 25));
    System::Console::WriteLine("insert(begin(), [L'y' 25]) = [{0} {1}]",
        it->first, it->second);
    for each (Mymap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // insert an iterator range
    Mymap c2;
    it = c1.end();
    c2.insert(c1.begin(), --it);
    for each (Mymap::value_type elem in c2)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // insert an enumeration
    Mymap c3;
    c3.insert(   // NOTE: cast is not needed
        (System::Collections::Generic::
            IEnumerable<Mymap::value_type>^)%c1);
    for each (Mymap::value_type elem in c3)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
insert([L'x' 24]) = [[x 24] True]
insert([L'b' 2]) = [[b 2] False]
[a 1] [b 2] [c 3] [x 24]
insert(begin(), [L'y' 25]) = [y 25]
[a 1] [b 2] [c 3] [x 24] [y 25]
[a 1] [b 2] [c 3] [x 24]
[a 1] [b 2] [c 3] [x 24] [y 25]
```

## <a name="mapiterator-stlclr"></a><a name="iterator"></a>map:: iterator (STL/CLR)

Typ iteratora dla kontrolowanej sekwencji.

### <a name="syntax"></a>Składnia

```cpp
typedef T1 iterator;
```

### <a name="remarks"></a>Uwagi

Typ opisuje obiekt nieokreślonego typu `T1` , który może obsłużyć iterator dwukierunkowy dla kontrolowanej sekwencji.

### <a name="example"></a>Przykład

```cpp
// cliext_map_iterator.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));
    c1.insert(Mymap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    Mymap::iterator it = c1.begin();
    for (; it != c1.end(); ++it)
        System::Console::Write("[{0} {1}] ", it->first, it->second);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
```

## <a name="mapkey_comp-stlclr"></a><a name="key_comp"></a>map:: key_comp (STL/CLR)

Kopiuje delegata porządkowania dla dwóch kluczy.

### <a name="syntax"></a>Składnia

```cpp
key_compare^key_comp();
```

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca delegat porządkowania używany do uporządkowania kontrolowanej sekwencji. Służy do porównywania dwóch kluczy.

### <a name="example"></a>Przykład

```cpp
// cliext_map_key_comp.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    Mymap::key_compare^ kcomp = c1.key_comp();

    System::Console::WriteLine("compare(L'a', L'a') = {0}",
        kcomp(L'a', L'a'));
    System::Console::WriteLine("compare(L'a', L'b') = {0}",
        kcomp(L'a', L'b'));
    System::Console::WriteLine("compare(L'b', L'a') = {0}",
        kcomp(L'b', L'a'));
    System::Console::WriteLine();

    // test a different ordering rule
    Mymap c2 = cliext::greater<wchar_t>();
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

## <a name="mapkey_compare-stlclr"></a><a name="key_compare"></a>map:: key_compare (STL/CLR)

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
// cliext_map_key_compare.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    Mymap::key_compare^ kcomp = c1.key_comp();

    System::Console::WriteLine("compare(L'a', L'a') = {0}",
        kcomp(L'a', L'a'));
    System::Console::WriteLine("compare(L'a', L'b') = {0}",
        kcomp(L'a', L'b'));
    System::Console::WriteLine("compare(L'b', L'a') = {0}",
        kcomp(L'b', L'a'));
    System::Console::WriteLine();

    // test a different ordering rule
    Mymap c2 = cliext::greater<wchar_t>();
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

## <a name="mapkey_type-stlclr"></a><a name="key_type"></a>map:: key_type (STL/CLR)

Typ klucza sortowania.

### <a name="syntax"></a>Składnia

```cpp
typedef Key key_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla *klucza*parametru szablonu.

### <a name="example"></a>Przykład

```cpp
// cliext_map_key_type.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));
    c1.insert(Mymap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]" using key_type
    for (Mymap::iterator it = c1.begin(); it != c1.end(); ++it)
        {   // store element in key_type object
        Mymap::key_type val = it->first;

        System::Console::Write("{0} ", val);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="maplower_bound-stlclr"></a><a name="lower_bound"></a>map:: lower_bound (STL/CLR)

Znajduje początek zakresu, który odpowiada określonemu kluczowi.

### <a name="syntax"></a>Składnia

```cpp
iterator lower_bound(key_type key);
```

#### <a name="parameters"></a>Parametry

*głównych*<br/>
Wartość klucza do wyszukania.

### <a name="remarks"></a>Uwagi

Funkcja członkowska określa pierwszy element `X` w kontrolowanej sekwencji, który ma równoważne porządkowanie do *klucza*. Jeśli taki element nie istnieje, zwraca [Mapowanie:: end (STL/CLR)](../dotnet/map-end-stl-clr.md) `()` ; w przeciwnym razie zwraca iterator, który wyznacza `X` . Służy do lokalizowania początku sekwencji elementów aktualnie w kontrolowanej sekwencji, która pasuje do określonego klucza.

### <a name="example"></a>Przykład

```cpp
// cliext_map_lower_bound.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));
    c1.insert(Mymap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    System::Console::WriteLine("lower_bound(L'x')==end() = {0}",
        c1.lower_bound(L'x') == c1.end());

    Mymap::iterator it = c1.lower_bound(L'a');
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

## <a name="mapmake_value-stlclr"></a><a name="make_value"></a>map:: make_value (STL/CLR)

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
// cliext_map_make_value.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));
    c1.insert(Mymap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
```

## <a name="mapmap-stlclr"></a><a name="map"></a>map:: map (STL/CLR)

Konstruuje obiekt kontenera.

### <a name="syntax"></a>Składnia

```cpp
map();
explicit map(key_compare^ pred);
map(map<Key, Mapped>% right);
map(map<Key, Mapped>^ right);
template<typename InIter>
    mapmap(InIter first, InIter last);
template<typename InIter>
    map(InIter first, InIter last,
        key_compare^ pred);
map(System::Collections::Generic::IEnumerable<GValue>^ right);
map(System::Collections::Generic::IEnumerable<GValue>^ right,
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

`map();`

Inicjuje kontrolowaną sekwencję bez elementów z domyślnym predykatem kolejności `key_compare()` . Służy do określania pustej początkowej kontrolowanej sekwencji przy użyciu domyślnego predykatu porządkowania.

Konstruktor:

`explicit map(key_compare^ pred);`

Inicjuje kontrolowaną sekwencję bez elementów z predykatem porządkowania *pred*. Służy do określania pustej początkowej kontrolowanej sekwencji z określonym predykatem kolejności.

Konstruktor:

`map(map<Key, Mapped>% right);`

Inicjuje kontrolowaną sekwencję z sekwencją [ `right.begin()` , `right.end()` ) z domyślnym predykatem kolejności. Służy do określenia początkowej kontrolowanej sekwencji, która jest kopią sekwencji kontrolowanej *przez obiekt mapy*, z domyślnym predykatem kolejności.

Konstruktor:

`map(map<Key, Mapped>^ right);`

Inicjuje kontrolowaną sekwencję z sekwencją [ `right->begin()` , `right->end()` ) z domyślnym predykatem kolejności. Służy do określenia początkowej kontrolowanej sekwencji, która jest kopią sekwencji kontrolowanej *przez obiekt mapy*, z domyślnym predykatem kolejności.

Konstruktor:

`template<typename InIter> map(InIter first, InIter last);`

Inicjuje kontrolowaną sekwencję z sekwencją [ `first` , `last` ) z domyślnym predykatem kolejności. Służy do Przekształć sekwencję na kopię innej sekwencji z domyślnym predykatem kolejności.

Konstruktor:

`template<typename InIter> map(InIter first, InIter last, key_compare^ pred);`

Inicjuje kontrolowaną sekwencję z sekwencją [ `first` , `last` ) z predykatem porządkowania *pred*. Służy do Przekształć sekwencję na kopię innej sekwencji z określonym predykatem kolejności.

Konstruktor:

`map(System::Collections::Generic::IEnumerable<Key>^ right);`

Inicjuje kontrolowaną sekwencję z sekwencją wyznaczonej przez moduł wyliczający *po prawej stronie*przy użyciu domyślnego predykatu porządkowania. Jest on używany do kontrolowania kontrolowanej sekwencji kopii kolejnej sekwencji opisanej przez moduł wyliczający z domyślnym predykatem kolejności.

Konstruktor:

`map(System::Collections::Generic::IEnumerable<Key>^ right, key_compare^ pred);`

Inicjuje kontrolowaną sekwencję z sekwencją wyznaczonej przez moduł wyliczający *po prawej stronie*z predykatem porządkowania *pred*. Jest on używany do kontrolowania kontrolowanej sekwencji kopii kolejnej sekwencji opisanej przez moduł wyliczający z określonym predykatem kolejności.

### <a name="example"></a>Przykład

```cpp
// cliext_map_construct.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
// construct an empty container
    Mymap c1;
    System::Console::WriteLine("size() = {0}", c1.size());

    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));
    c1.insert(Mymap::make_value(L'c', 3));
    for each (Mymap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // construct with an ordering rule
    Mymap c2 = cliext::greater_equal<wchar_t>();
    System::Console::WriteLine("size() = {0}", c2.size());

    c2.insert(c1.begin(), c1.end());
    for each (Mymap::value_type elem in c2)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // construct with an iterator range
    Mymap c3(c1.begin(), c1.end());
    for each (Mymap::value_type elem in c3)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // construct with an iterator range and an ordering rule
    Mymap c4(c1.begin(), c1.end(),
        cliext::greater_equal<wchar_t>());
    for each (Mymap::value_type elem in c4)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // construct with an enumeration
    Mymap c5(   // NOTE: cast is not needed
        (System::Collections::Generic::IEnumerable<
            Mymap::value_type>^)%c3);
    for each (Mymap::value_type elem in c5)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // construct with an enumeration and an ordering rule
    Mymap c6(   // NOTE: cast is not needed
        (System::Collections::Generic::IEnumerable<
            Mymap::value_type>^)%c3,
                cliext::greater_equal<wchar_t>());
    for each (Mymap::value_type elem in c6)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // construct by copying another container
    Mymap c7(c4);
    for each (Mymap::value_type elem in c7)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // construct by copying a container handle
    Mymap c8(%c3);
    for each (Mymap::value_type elem in c8)
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

## <a name="mapmapped_type-stlclr"></a><a name="mapped_type"></a>map:: mapped_type (STL/CLR)

Typ mapowanej wartości skojarzonej z poszczególnymi kluczami.

### <a name="syntax"></a>Składnia

```cpp
typedef Mapped mapped_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla *zamapowanego*parametru szablonu.

### <a name="example"></a>Przykład

```cpp
// cliext_map_mapped_type.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));
    c1.insert(Mymap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]" using mapped_type
    for (Mymap::iterator it = c1.begin(); it != c1.end(); ++it)
        {   // store element in mapped_type object
        Mymap::mapped_type val = it->second;

        System::Console::Write("{0} ", val);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
1 2 3
```

## <a name="mapoperator-stlclr"></a><a name="op_as"></a>map:: operator = (STL/CLR)

Zastępuje kontrolowaną sekwencję.

### <a name="syntax"></a>Składnia

```cpp
map<Key, Mapped>% operator=(map<Key, Mapped>% right);
```

#### <a name="parameters"></a>Parametry

*Kliknij*<br/>
Kontener do skopiowania.

### <a name="remarks"></a>Uwagi

Operator elementu członkowskiego kopiuje *prawo* do obiektu, a następnie zwraca **`*this`** . Służy do zastępowania kontrolowanej sekwencji kopią kontrolowanej sekwencji *po prawej stronie*.

### <a name="example"></a>Przykład

```cpp
// cliext_map_operator_as.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));
    c1.insert(Mymap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // assign to a new container
    Mymap c2;
    c2 = c1;
    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymap::value_type elem in c2)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
[a 1] [b 2] [c 3]
```

## <a name="mapoperatorstlclr"></a><a name="op"></a>map:: operator (STL/CLR)

Mapuje klucz do skojarzonej mapowanej wartości.

### <a name="syntax"></a>Składnia

```cpp
mapped_type operator[](key_type key);
```

#### <a name="parameters"></a>Parametry

*głównych*<br/>
Wartość klucza do wyszukania.

### <a name="remarks"></a>Uwagi

Funkcja członkowska przedsięwzięciach, aby znaleźć element o równoważnej kolejności do *klucza*. Jeśli zostanie znaleziony, zwraca skojarzoną wartość zmapowaną; w przeciwnym razie wstawia `value_type(key, mapped_type())` i zwraca skojarzoną (domyślną) wartość zmapowaną. Służy do wyszukiwania zamapowanej wartości przy użyciu skojarzonego klucza lub do upewnienia się, że wpis istnieje dla klucza, jeśli nie zostanie znaleziony.

### <a name="example"></a>Przykład

```cpp
// cliext_map_operator_sub.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));
    c1.insert(Mymap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    System::Console::WriteLine("c1[{0}] = {1}",
        L'A', c1[L'A']);
    System::Console::WriteLine("c1[{0}] = {1}",
        L'b', c1[L'b']);

    // redisplay altered contents
    for each (Mymap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // alter mapped values and redisplay
    c1[L'A'] = 10;
    c1[L'c'] = 13;
    for each (Mymap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
c1[A] = 0
c1[b] = 2
[A 0] [a 1] [b 2] [c 3]
[A 10] [a 1] [b 2] [c 13]
```

## <a name="maprbegin-stlclr"></a><a name="rbegin"></a>map:: rbegin (STL/CLR)

Określa początek odwróconej sekwencji kontrolowanej.

### <a name="syntax"></a>Składnia

```cpp
reverse_iterator rbegin();
```

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca iterator odwrotny, który wyznacza ostatni element kontrolowanej sekwencji lub tuż poza początkiem pustej sekwencji. W związku z tym określa `beginning` odwrotną sekwencję. Służy do uzyskania iteratora, który wyznacza `current` początek kontrolowanej sekwencji widoczny w kolejności odwrotnej, ale jego stan może ulec zmianie w przypadku zmiany długości kontrolowanej sekwencji.

### <a name="example"></a>Przykład

```cpp
// cliext_map_rbegin.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));
    c1.insert(Mymap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // inspect first two items in reversed sequence
    Mymap::reverse_iterator rit = c1.rbegin();
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

## <a name="mapreference-stlclr"></a><a name="reference"></a>map:: Reference (STL/CLR)

Typ odwołania do elementu.

### <a name="syntax"></a>Składnia

```cpp
typedef value_type% reference;
```

### <a name="remarks"></a>Uwagi

Typ opisuje odwołanie do elementu.

### <a name="example"></a>Przykład

```cpp
// cliext_map_reference.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));
    c1.insert(Mymap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    Mymap::iterator it = c1.begin();
    for (; it != c1.end(); ++it)
        {   // get a reference to an element
        Mymap::reference ref = *it;
        System::Console::Write("[{0} {1}] ", ref->first, ref->second);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
```

## <a name="maprend-stlclr"></a><a name="rend"></a>map:: rend (STL/CLR)

Określa koniec odwróconej kontrolowanej sekwencji.

### <a name="syntax"></a>Składnia

```cpp
reverse_iterator rend();
```

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca iterator odwrotny, który wskazuje tuż poza początkiem kontrolowanej sekwencji. W związku z tym określa `end` odwrotną sekwencję. Służy do uzyskania iteratora, który wyznacza `current` koniec kontrolowanej sekwencji widoczny w odwrotnej kolejności, ale jego stan może ulec zmianie w przypadku zmiany długości kontrolowanej sekwencji.

### <a name="example"></a>Przykład

```cpp
// cliext_map_rend.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));
    c1.insert(Mymap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // inspect first two items in reversed sequence
    Mymap::reverse_iterator rit = c1.rend();
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

## <a name="mapreverse_iterator-stlclr"></a><a name="reverse_iterator"></a>map:: reverse_iterator (STL/CLR)

Typ iteratora odwrotnego dla kontrolowanej sekwencji.

### <a name="syntax"></a>Składnia

```
typedef T3 reverse_iterator;
```

### <a name="remarks"></a>Uwagi

Typ opisuje obiekt nieokreślonego typu `T3` , który może być używany jako iterator odwrotny dla kontrolowanej sekwencji.

### <a name="example"></a>Przykład

```cpp
// cliext_map_reverse_iterator.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));
    c1.insert(Mymap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]" reversed
    Mymap::reverse_iterator rit = c1.rbegin();
    for (; rit != c1.rend(); ++rit)
        System::Console::Write("[{0} {1}] ", rit->first, rit->second);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
[c 3] [b 2] [a 1]
```

## <a name="mapsize-stlclr"></a><a name="size"></a>map:: size (STL/CLR)

Liczy liczbę elementów.

### <a name="syntax"></a>Składnia

```cpp
size_type size();
```

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca długość kontrolowanej sekwencji. Służy do określania liczby elementów aktualnie w kontrolowanej sekwencji. Jeśli dowiesz się, czy sekwencja ma rozmiar różny od zera, zobacz [map:: empty (STL/CLR)](../dotnet/map-empty-stl-clr.md) `()` .

### <a name="example"></a>Przykład

```cpp
// cliext_map_size.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));
    c1.insert(Mymap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // clear the container and reinspect
    c1.clear();
    System::Console::WriteLine("size() = {0} after clearing", c1.size());

    // add elements and clear again
    c1.insert(Mymap::make_value(L'd', 4));
    c1.insert(Mymap::make_value(L'e', 5));
    System::Console::WriteLine("size() = {0} after adding 2", c1.size());
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
size() = 0 after clearing
size() = 2 after adding 2
```

## <a name="mapsize_type-stlclr"></a><a name="size_type"></a>map:: size_type (STL/CLR)

Typ podpisanej odległości między dwoma elementami.

### <a name="syntax"></a>Składnia

```cpp
typedef int size_type;
```

### <a name="remarks"></a>Uwagi

Typ opisuje nieujemną liczbę elementów.

### <a name="example"></a>Przykład

```cpp
// cliext_map_size_type.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));
    c1.insert(Mymap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // compute positive difference
    Mymap::size_type diff = 0;
    for (Mymap::iterator it = c1.begin(); it != c1.end(); ++it)
        ++diff;
    System::Console::WriteLine("end()-begin() = {0}", diff);
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
end()-begin() = 3
```

## <a name="mapswap-stlclr"></a><a name="swap"></a>map:: swap (STL/CLR)

Zamienia zawartości dwóch kontenerów.

### <a name="syntax"></a>Składnia

```cpp
void swap(map<Key, Mapped>% right);
```

#### <a name="parameters"></a>Parametry

*Kliknij*<br/>
Kontener, za pomocą którego ma zostać zamieniony zawartość.

### <a name="remarks"></a>Uwagi

Funkcja członkowska zamienia kontrolowane sekwencje między **`this`** i *po prawej*. Robi to w stałym czasie i nie zgłasza wyjątków. Jest ona używana jako Szybka metoda wymiany zawartości dwóch kontenerów.

### <a name="example"></a>Przykład

```cpp
// cliext_map_swap.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));
    c1.insert(Mymap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // construct another container with repetition of values
    Mymap c2;
    c2.insert(Mymap::make_value(L'd', 4));
    c2.insert(Mymap::make_value(L'e', 5));
    c2.insert(Mymap::make_value(L'f', 6));
    for each (Mymap::value_type elem in c2)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // swap and redisplay
    c1.swap(c2);
    for each (Mymap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    for each (Mymap::value_type elem in c2)
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

## <a name="mapto_array-stlclr"></a><a name="to_array"></a>map:: to_array (STL/CLR)

Kopiuje przekontrolowaną sekwencję do nowej tablicy.

### <a name="syntax"></a>Składnia

```cpp
cli::array<value_type>^ to_array();
```

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca tablicę zawierającą kontrolowaną sekwencję. Służy do uzyskania kopii kontrolowanej sekwencji w formularzu tablicowym.

### <a name="example"></a>Przykład

```cpp
// cliext_map_to_array.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));
    c1.insert(Mymap::make_value(L'c', 3));

    // copy the container and modify it
    cli::array<Mymap::value_type>^ a1 = c1.to_array();

    c1.insert(Mymap::make_value(L'd', 4));
    for each (Mymap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // display the earlier array copy
    for each (Mymap::value_type elem in a1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3] [d 4]
[a 1] [b 2] [c 3]
```

## <a name="mapupper_bound-stlclr"></a><a name="upper_bound"></a>map:: upper_bound (STL/CLR)

Znajduje koniec zakresu, który odpowiada określonemu kluczowi.

### <a name="syntax"></a>Składnia

```cpp
iterator upper_bound(key_type key);
```

#### <a name="parameters"></a>Parametry

*głównych*<br/>
Wartość klucza do wyszukania.

### <a name="remarks"></a>Uwagi

Funkcja członkowska określa ostatni element `X` w kontrolowanej sekwencji, który ma równoważne porządkowanie do *klucza*. Jeśli taki element nie istnieje lub `X` jest ostatnim elementem w kontrolowanej sekwencji, zwraca [Mapowanie:: end (STL/CLR)](../dotnet/map-end-stl-clr.md) `()` ; w przeciwnym razie zwraca iterator, który wyznacza pierwszy element poza `X` . Służy do lokalizowania końca sekwencji elementów aktualnie w kontrolowanej sekwencji, która pasuje do określonego klucza.

### <a name="example"></a>Przykład

```cpp
// cliext_map_upper_bound.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));
    c1.insert(Mymap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    System::Console::WriteLine("upper_bound(L'x')==end() = {0}",
        c1.upper_bound(L'x') == c1.end());

    Mymap::iterator it = c1.upper_bound(L'a');
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

## <a name="mapvalue_comp-stlclr"></a><a name="value_comp"></a>map:: value_comp (STL/CLR)

Kopiuje delegata porządkowania dla dwóch wartości elementów.

### <a name="syntax"></a>Składnia

```cpp
value_compare^ value_comp();
```

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca delegat porządkowania używany do uporządkowania kontrolowanej sekwencji. Służy do porównywania dwóch wartości elementów.

### <a name="example"></a>Przykład

```cpp
// cliext_map_value_comp.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    Mymap::value_compare^ kcomp = c1.value_comp();

    System::Console::WriteLine("compare([L'a', 1], [L'a', 1]) = {0}",
        kcomp(Mymap::make_value(L'a', 1),
            Mymap::make_value(L'a', 1)));
    System::Console::WriteLine("compare([L'a', 1], [L'b', 2]) = {0}",
        kcomp(Mymap::make_value(L'a', 1),
            Mymap::make_value(L'b', 2)));
    System::Console::WriteLine("compare([L'b', 2], [L'a', 1]) = {0}",
        kcomp(Mymap::make_value(L'b', 2),
            Mymap::make_value(L'a', 1)));
    System::Console::WriteLine();
    return (0);
    }
```

```Output
compare([L'a', 1], [L'a', 1]) = False
compare([L'a', 1], [L'b', 2]) = True
compare([L'b', 2], [L'a', 1]) = False
```

## <a name="mapvalue_compare-stlclr"></a><a name="value_compare"></a>map:: value_compare (STL/CLR)

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
// cliext_map_value_compare.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    Mymap::value_compare^ kcomp = c1.value_comp();

    System::Console::WriteLine("compare([L'a', 1], [L'a', 1]) = {0}",
        kcomp(Mymap::make_value(L'a', 1),
            Mymap::make_value(L'a', 1)));
    System::Console::WriteLine("compare([L'a', 1], [L'b', 2]) = {0}",
        kcomp(Mymap::make_value(L'a', 1),
            Mymap::make_value(L'b', 2)));
    System::Console::WriteLine("compare([L'b', 2], [L'a', 1]) = {0}",
        kcomp(Mymap::make_value(L'b', 2),
            Mymap::make_value(L'a', 1)));
    System::Console::WriteLine();
    return (0);
    }
```

```Output
compare([L'a', 1], [L'a', 1]) = False
compare([L'a', 1], [L'b', 2]) = True
compare([L'b', 2], [L'a', 1]) = False
```

## <a name="mapvalue_type-stlclr"></a><a name="value_type"></a>map:: value_type (STL/CLR)

Typ elementu.

### <a name="syntax"></a>Składnia

```cpp
typedef generic_value value_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla `generic_value` .

### <a name="example"></a>Przykład

```cpp
// cliext_map_value_type.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));
    c1.insert(Mymap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]" using value_type
    for (Mymap::iterator it = c1.begin(); it != c1.end(); ++it)
        {   // store element in value_type object
        Mymap::value_type val = *it;
        System::Console::Write("[{0} {1}] ", val->first, val->second);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
```

## <a name="operator-map-stlclr"></a><a name="op_neq"></a>operator! = (map) (STL/CLR)

Nierówne porównanie.

### <a name="syntax"></a>Składnia

```cpp
template<typename Key,
    typename Mapped>
    bool operator!=(map<Key, Mapped>% left,
        map<Key, Mapped>% right);
```

#### <a name="parameters"></a>Parametry

*lewym*<br/>
Lewy kontener do porównania.

*Kliknij*<br/>
Prawy kontener do porównania.

### <a name="remarks"></a>Uwagi

Funkcja operatora zwraca wartość `!(left == right)` . Służy do sprawdzania, czy nie *jest on* uporządkowany *tak samo jak w* przypadku porównywania dwóch map przez element.

### <a name="example"></a>Przykład

```cpp
// cliext_map_operator_ne.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));
    c1.insert(Mymap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // assign to a new container
    Mymap c2;
    c2.insert(Mymap::make_value(L'a', 1));
    c2.insert(Mymap::make_value(L'b', 2));
    c2.insert(Mymap::make_value(L'd', 4));

    // display contents " [a 1] [b 2] [d 4]"
    for each (Mymap::value_type elem in c2)
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

## <a name="operatorlt-map-stlclr"></a><a name="op_lt"></a>operator &lt; (map) (STL/CLR)

Lista jest mniejsza niż porównanie.

### <a name="syntax"></a>Składnia

```cpp
template<typename Key,
    typename Mapped>
    bool operator<(map<Key, Mapped>% left,
        map<Key, Mapped>% right);
```

#### <a name="parameters"></a>Parametry

*lewym*<br/>
Lewy kontener do porównania.

*Kliknij*<br/>
Prawy kontener do porównania.

### <a name="remarks"></a>Uwagi

Funkcja operator zwraca wartość true, jeśli dla najniższej pozycji `i` `!(right[i] < left[i])` ma również wartość true `left[i] < right[i]` . W przeciwnym razie zwraca go przy `left->size() < right->size()` użyciu, aby sprawdzić, czy *lewa* jest uporządkowana przed *prawem* , gdy dwie mapy są porównywane elementów według elementu.

### <a name="example"></a>Przykład

```cpp
// cliext_map_operator_lt.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));
    c1.insert(Mymap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // assign to a new container
    Mymap c2;
    c2.insert(Mymap::make_value(L'a', 1));
    c2.insert(Mymap::make_value(L'b', 2));
    c2.insert(Mymap::make_value(L'd', 4));

    // display contents " [a 1] [b 2] [d 4]"
    for each (Mymap::value_type elem in c2)
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

## <a name="operatorlt-map-stlclr"></a><a name="op_lteq"></a>operator &lt; = (map) (STL/CLR)

Lista jest mniejsza niż lub równa.

### <a name="syntax"></a>Składnia

```cpp
template<typename Key,
    typename Mapped>
    bool operator<=(map<Key, Mapped>% left,
        map<Key, Mapped>% right);
```

#### <a name="parameters"></a>Parametry

*lewym*<br/>
Lewy kontener do porównania.

*Kliknij*<br/>
Prawy kontener do porównania.

### <a name="remarks"></a>Uwagi

Funkcja operatora zwraca wartość `!(right < left)` . Służy do sprawdzania, czy nie *jest on* uporządkowany po *prawej stronie* , gdy dwie mapy są porównywane elementów według elementu.

### <a name="example"></a>Przykład

```cpp
// cliext_map_operator_le.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));
    c1.insert(Mymap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // assign to a new container
    Mymap c2;
    c2.insert(Mymap::make_value(L'a', 1));
    c2.insert(Mymap::make_value(L'b', 2));
    c2.insert(Mymap::make_value(L'd', 4));

    // display contents " [a 1] [b 2] [d 4]"
    for each (Mymap::value_type elem in c2)
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

## <a name="operator-map-stlclr"></a><a name="op_eq"></a>operator = = (map) (STL/CLR)

Wyświetl równe porównanie.

### <a name="syntax"></a>Składnia

```cpp
template<typename Key,
    typename Mapped>
    bool operator==(map<Key, Mapped>% left,
        map<Key, Mapped>% right);
```

#### <a name="parameters"></a>Parametry

*lewym*<br/>
Lewy kontener do porównania.

*Kliknij*<br/>
Prawy kontener do porównania.

### <a name="remarks"></a>Uwagi

Funkcja operator zwraca wartość true tylko wtedy, gdy sekwencje sterowane przez *lewo* i *prawo* mają taką samą długość i, dla każdej pozycji `i` `left[i] ==` `right[i]` . Służy do sprawdzania, czy *lewa* jest uporządkowana tak samo jak *w przypadku* porównywania dwóch map przez element.

### <a name="example"></a>Przykład

```cpp
// cliext_map_operator_eq.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));
    c1.insert(Mymap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // assign to a new container
    Mymap c2;
    c2.insert(Mymap::make_value(L'a', 1));
    c2.insert(Mymap::make_value(L'b', 2));
    c2.insert(Mymap::make_value(L'd', 4));

    // display contents " [a 1] [b 2] [d 4]"
    for each (Mymap::value_type elem in c2)
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

## <a name="operatorgt-map-stlclr"></a><a name="op_gt"></a>operator &gt; (map) (STL/CLR)

Lista większa niż porównanie.

### <a name="syntax"></a>Składnia

```cpp
template<typename Key,
    typename Mapped>
    bool operator>(map<Key, Mapped>% left,
        map<Key, Mapped>% right);
```

#### <a name="parameters"></a>Parametry

*lewym*<br/>
Lewy kontener do porównania.

*Kliknij*<br/>
Prawy kontener do porównania.

### <a name="remarks"></a>Uwagi

Funkcja operatora zwraca wartość `right` `<` `left` . Służy do sprawdzania, czy *lewa* jest uporządkowana po *prawej stronie* , gdy dwie mapy są porównywane elementów według elementu.

### <a name="example"></a>Przykład

```cpp
// cliext_map_operator_gt.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));
    c1.insert(Mymap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // assign to a new container
    Mymap c2;
    c2.insert(Mymap::make_value(L'a', 1));
    c2.insert(Mymap::make_value(L'b', 2));
    c2.insert(Mymap::make_value(L'd', 4));

    // display contents " [a 1] [b 2] [d 4]"
    for each (Mymap::value_type elem in c2)
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

## <a name="operatorgt-map-stlclr"></a><a name="op_gteq"></a>operator &gt; = (map) (STL/CLR)

Lista jest większa lub równa porównaniu.

### <a name="syntax"></a>Składnia

```cpp
template<typename Key,
    typename Mapped>
    bool operator>=(map<Key, Mapped>% left,
        map<Key, Mapped>% right);
```

#### <a name="parameters"></a>Parametry

*lewym*<br/>
Lewy kontener do porównania.

*Kliknij*<br/>
Prawy kontener do porównania.

### <a name="remarks"></a>Uwagi

Funkcja operatora zwraca wartość `!(left` `<` `right)` . Służy do sprawdzania, czy nie *jest on* uporządkowany przed *prawem* , gdy dwie mapy są porównywane elementów według elementu.

### <a name="example"></a>Przykład

```cpp
// cliext_map_operator_ge.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));
    c1.insert(Mymap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // assign to a new container
    Mymap c2;
    c2.insert(Mymap::make_value(L'a', 1));
    c2.insert(Mymap::make_value(L'b', 2));
    c2.insert(Mymap::make_value(L'd', 4));

    // display contents " [a 1] [b 2] [d 4]"
    for each (Mymap::value_type elem in c2)
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
