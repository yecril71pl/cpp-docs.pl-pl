---
title: multiset (STL/CLR)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- cliext::multiset
- cliext::multiset::begin
- cliext::multiset::clear
- cliext::multiset::const_iterator
- cliext::multiset::const_reference
- cliext::multiset::const_reverse_iterator
- cliext::multiset::count
- cliext::multiset::difference_type
- cliext::multiset::empty
- cliext::multiset::end
- cliext::multiset::equal_range
- cliext::multiset::erase
- cliext::multiset::find
- cliext::multiset::generic_container
- cliext::multiset::generic_iterator
- cliext::multiset::generic_reverse_iterator
- cliext::multiset::generic_value
- cliext::multiset::insert
- cliext::multiset::iterator
- cliext::multiset::key_comp
- cliext::multiset::key_compare
- cliext::multiset::key_type
- cliext::multiset::lower_bound
- cliext::multiset::make_value
- cliext::multiset::multiset
- cliext::multiset::operator=
- cliext::multiset::rbegin
- cliext::multiset::reference
- cliext::multiset::rend
- cliext::multiset::reverse_iterator
- cliext::multiset::size
- cliext::multiset::size_type
- cliext::multiset::swap
- cliext::multiset::to_array
- cliext::multiset::upper_bound
- cliext::multiset::value_comp
- cliext::multiset::value_compare
- cliext::multiset::value_type
- cliext::multiset::operator!=
- cliext::multiset::operator<
- cliext::multiset::operator<=
- cliext::multiset::operator==
- cliext::multiset::operator>
- cliext::multiset::operator>=
helpviewer_keywords:
- <cliext/set> header [STL/CLR]
- <set> header [STL/CLR]
- multiset class [STL/CLR]
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
- operator!= member [STL/CLR]
- operator< member [STL/CLR]
- operator<= member [STL/CLR]
- operator== member [STL/CLR]
- operator> member [STL/CLR]
- operator>= member [STL/CLR]
ms.assetid: 7c46e2b4-cd88-49b7-a9e6-63ad5ae7feb5
ms.openlocfilehash: a6bb7a262df21a835f1e870f2bce29480467c543
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/29/2020
ms.locfileid: "91508542"
---
# <a name="multiset-stlclr"></a>multiset (STL/CLR)

Klasa szablonu opisuje obiekt, który kontroluje różnej długości sekwencje elementów, które mają dostęp dwukierunkowy. Kontener służy `multiset` do zarządzania sekwencją elementów jako (niemal) uporządkowanym drzewem węzłów, każdy z nich przechowujący jeden element.

W poniższym opisie `GValue` jest taka sama jak `GKey` , która z kolei jest taka sama jak *klucz* , chyba że ostatni jest typem ref, w takim przypadku jest to `Key^` .

## <a name="syntax"></a>Składnia

```cpp
template<typename Key>
    ref class multiset
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

## <a name="requirements"></a>Wymagania

**Nagłówek:**\<cliext/set>

**Przestrzeń nazw:** cliext

## <a name="declarations"></a>Deklaracje

|Definicja typu|Opis|
|---------------------|-----------------|
|[multiset::const_iterator (STL/CLR)](#const_iterator)|Typ iteratora stałego dla kontrolowanej sekwencji.|
|[multiset::const_reference (STL/CLR)](#const_reference)|Typ stałego odwołania do elementu.|
|[multiset::const_reverse_iterator (STL/CLR)](#const_reverse_iterator)|Typ iteratora stałego zwrotnego dla kontrolowanej sekwencji.|
|[multiset::difference_type (STL/CLR)](#difference_type)|Typ (prawdopodobnie podpisany) odległości między dwoma elementami.|
|[multiset::generic_container (STL/CLR)](#generic_container)|Typ interfejsu generycznego dla kontenera.|
|[multiset::generic_iterator (STL/CLR)](#generic_iterator)|Typ iteratora dla interfejsu generycznego dla kontenera.|
|[multiset::generic_reverse_iterator (STL/CLR)](#generic_reverse_iterator)|Typ iteratora odwrotnego dla interfejsu generycznego dla kontenera.|
|[multiset::generic_value (STL/CLR)](#generic_value)|Typ elementu dla interfejsu generycznego dla kontenera.|
|[multiset::iterator (STL/CLR)](#iterator)|Typ iteratora dla kontrolowanej sekwencji.|
|[multiset::key_compare (STL/CLR)](#key_compare)|Delegat porządkowania dla dwóch kluczy.|
|[multiset::key_type (STL/CLR)](#key_type)|Typ klucza sortowania.|
|[multiset::reference (STL/CLR)](#reference)|Typ odwołania do elementu.|
|[multiset::reverse_iterator (STL/CLR)](#reverse_iterator)|Typ iteratora odwrotnego dla kontrolowanej sekwencji.|
|[multiset::size_type (STL/CLR)](#size_type)|Typ (nieujemnej) odległości między dwoma elementami.|
|[multiset::value_compare (STL/CLR)](#value_compare)|Delegat porządkowania dla dwóch wartości elementów.|
|[multiset::value_type (STL/CLR)](#value_type)|Typ elementu.|

|Funkcja elementów członkowskich|Opis|
|---------------------|-----------------|
|[multiset::begin (STL/CLR)](#begin)|Określa początek kontrolowanej sekwencji.|
|[multiset::clear (STL/CLR)](#clear)|Usuwa wszystkie elementy.|
|[multiset::count (STL/CLR)](#count)|Zlicza elementy pasujące do określonego klucza.|
|[multiset::empty (STL/CLR)](#empty)|Sprawdza, czy nie ma żadnych elementów.|
|[multiset::end (STL/CLR)](#end)|Określa koniec kontrolowanej sekwencji.|
|[multiset::equal_range (STL/CLR)](#equal_range)|Wyszukuje zakres, który odpowiada określonemu kluczowi.|
|[multiset::erase (STL/CLR)](#erase)|Usuwa elementy z określonych pozycji.|
|[multiset::find (STL/CLR)](#find)|Wyszukuje element, który odpowiada określonemu kluczowi.|
|[multiset::insert (STL/CLR)](#insert)|Dodaje elementy.|
|[multiset::key_comp (STL/CLR)](#key_comp)|Kopiuje delegata porządkowania dla dwóch kluczy.|
|[multiset::lower_bound (STL/CLR)](#lower_bound)|Znajduje początek zakresu, który odpowiada określonemu kluczowi.|
|[multiset::make_value (STL/CLR)](#make_value)|Konstruuje obiekt wartości.|
|[multiset::multiset (STL/CLR)](#multiset)|Konstruuje obiekt kontenera.|
|[multiset::rbegin (STL/CLR)](#rbegin)|Określa początek odwróconej sekwencji kontrolowanej.|
|[multiset::rend (STL/CLR)](#rend)|Określa koniec odwróconej kontrolowanej sekwencji.|
|[multiset::size (STL/CLR)](#size)|Liczy liczbę elementów.|
|[multiset::swap (STL/CLR)](#swap)|Zamienia zawartości dwóch kontenerów.|
|[multiset::to_array (STL/CLR)](#to_array)|Kopiuje przekontrolowaną sekwencję do nowej tablicy.|
|[multiset::upper_bound (STL/CLR)](#upper_bound)|Znajduje koniec zakresu, który odpowiada określonemu kluczowi.|
|[multiset::value_comp (STL/CLR)](#value_comp)|Kopiuje delegata porządkowania dla dwóch wartości elementów.|

|Operator|Opis|
|--------------|-----------------|
|[multiset::operator= (STL/CLR)](#op_as)|Zastępuje kontrolowaną sekwencję.|
|[operator! = (zestaw wielokrotny) (STL/CLR)](#op_neq)|Określa, czy `multiset` obiekt nie jest równy innemu `multiset` obiektowi.|
|[< operatora (zestaw wielokrotny) (STL/CLR)](#op_lt)|Określa, czy `multiset` obiekt jest mniejszy niż inny `multiset` obiekt.|
|[operator<= (zestaw wielokrotny) (STL/CLR)](#op_lteq)|Określa, czy `multiset` obiekt jest mniejszy niż lub równy innemu `multiset` obiektowi.|
|[operator = = (zestaw wielokrotny) (STL/CLR)](#op_eq)|Określa, czy `multiset` obiekt jest równy innemu `multiset` obiektowi.|
|[operator> (multiset) (STL/CLR)](#op_gt)|Określa, czy `multiset` obiekt jest większy niż inny `multiset` obiekt.|
|[operator>= (zestaw wielokrotny) (STL/CLR)](#op_gteq)|Określa, czy `multiset` obiekt jest większy lub równy innemu `multiset` obiektowi.|

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

Obiekt porządkuje sekwencję, która kontroluje, wywołując zapisany obiekt delegata typu zestaw [wielokrotny:: key_compare (STL/CLR)](#key_compare). Można określić przechowywany obiekt delegowany podczas konstruowania zestawu wielokrotnego. Jeśli określisz brak obiektu delegowanego, wartością domyślną jest porównanie `operator<(key_type, key_type)` . Dostęp do tego przechowywanego obiektu można uzyskać, wywołując funkcję składową zestawu [wielokrotnego:: key_comp (STL/CLR)](#key_comp) `()` .

Taki obiekt delegata musi nałożyć ścisłe słabe porządkowanie dla kluczy typu zestaw [wielokrotny:: key_type (STL/CLR)](#key_type). Oznacza to, że dla dowolnych dwóch kluczy `X` i `Y` :

`key_comp()(X, Y)` zwraca ten sam wynik Boolean dla każdego wywołania.

Jeśli `key_comp()(X, Y)` ma wartość true, a następnie `key_comp()(Y, X)` musi mieć wartość false.

Jeśli `key_comp()(X, Y)` ma wartość true, `X` to przed `Y` .

Jeśli `!key_comp()(X, Y) && !key_comp()(Y, X)` ma wartość true, wówczas `X` i `Y` są określane jako równoważne porządkowanie.

Dla każdego elementu `X` , który poprzedza `Y` w kontrolowanej sekwencji, `key_comp()(Y, X)` ma wartość false. (Dla domyślnego obiektu delegowanego klucze nigdy nie zmniejszają wartości). W przeciwieństwie do [zestawu klas szablonu (STL/CLR)](../dotnet/set-stl-clr.md)obiekt klasy szablonu nie `multiset` wymaga, aby klucze dla wszystkich elementów były unikatowe. (Co najmniej dwa klucze mogą mieć równoważne porządkowanie).

Każdy element służy jako EY i wartość. Sekwencja jest reprezentowana w sposób, który pozwala na wyszukiwanie, wstawianie i usuwanie dowolnego elementu z liczbą operacji proporcjonalnie do logarytmu liczby elementów w sekwencji (czas logarytmu). Ponadto, wstawianie elementu nie unieważnia iteratorów, a usuwanie elementu unieważnia tylko te iteratory, które wskazują na usunięty element.

Zestaw wielokrotny obsługuje Iteratory dwukierunkowe, co oznacza, że można przechodzić do sąsiednich elementów przy użyciu iteratora, który wyznacza element w kontrolowanej sekwencji. Specjalny węzeł główny odpowiada iteratorowi zwróconemu przez zestaw [wielokrotny:: end (STL/CLR)](#end) `()` . Można zmniejszyć ten iterator, aby dotrzeć do ostatniego elementu w kontrolowanej sekwencji, jeśli jest obecny. Można zwiększyć iterator zestawu wielokrotnego w celu uzyskania dostępu do węzła głównego, a następnie będzie on porównywany z równą `end()` . Ale nie można usunąć odwołania do iteratora zwróconego przez `end()` .

Należy zauważyć, że nie można odwołać się do elementu zestaw wielokrotny bezpośrednio przy użyciu pozycji liczbowej — który wymaga iteratora dostępu swobodnego.

Iterator zestawu wielokrotnego przechowuje dojście do skojarzonego z nim węzła zestawu wielokrotnego, który z kolei przechowuje dojście do skojarzonego kontenera. Iteratorów można używać tylko ze skojarzonymi obiektami kontenera. Iterator zestawu wielokrotnego pozostaje prawidłowy, dopóki jego skojarzony węzeł z zestawem wielokrotnym jest skojarzony z jakimś zestawem wielokrotnym. Ponadto prawidłowy iterator jest dereferencable — można go użyć w celu uzyskania dostępu do lub zmiany wartości elementu, który wyznacza, tak długo, jak nie jest równa `end()` .

Wymazywanie lub usuwanie elementu wywołuje destruktor dla jego przechowywanej wartości. Niszczenie kontenera powoduje wymazanie wszystkich elementów. W tym celu kontener, którego typem elementu jest Klasa ref, zapewnia, że żadne elementy nie wyprowadzą kontenera. Należy jednak zauważyć, że kontener dojść *nie* niszczy swoich elementów.

## <a name="members"></a>Elementy członkowskie

## <a name="multisetbegin-stlclr"></a><a name="begin"></a> zestaw wielokrotny:: begin (STL/CLR)

Określa początek kontrolowanej sekwencji.

### <a name="syntax"></a>Składnia

```cpp
iterator begin();
```

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca iterator dwukierunkowy, który wyznacza pierwszy element kontrolowanej sekwencji lub tuż poza końcem pustej sekwencji. Służy do uzyskania iteratora, który wyznacza `current` początek kontrolowanej sekwencji, ale jego stan może ulec zmianie w przypadku zmiany długości kontrolowanej sekwencji.

### <a name="example"></a>Przykład

```cpp
// cliext_multiset_begin.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // inspect first two items
    Mymultiset::iterator it = c1.begin();
    System::Console::WriteLine("*begin() = {0}", *it);
    System::Console::WriteLine("*++begin() = {0}", *++it);
    return (0);
    }
```

```Output
a b c
*begin() = a
*++begin() = b
```

## <a name="multisetclear-stlclr"></a><a name="clear"></a> wielokrotne:: Clear (STL/CLR)

Usuwa wszystkie elementy.

### <a name="syntax"></a>Składnia

```cpp
void clear();
```

### <a name="remarks"></a>Uwagi

Funkcja członkowska skutecznie wywołuje zestaw wielokrotny [:: Erase (STL/CLR)](#erase) `(` [wielokrotne:: begin (STL/CLR)](#begin) zestaw `(),` [wielokrotny:: end (STL/CLR)](#end) `())` . Jest on używany do upewnienia się, że kontrolowana sekwencja jest pusta.

### <a name="example"></a>Przykład

```cpp
// cliext_multiset_clear.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // clear the container and reinspect
    c1.clear();
    System::Console::WriteLine("size() = {0}", c1.size());

    // add elements and clear again
    c1.insert(L'a');
    c1.insert(L'b');

    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    c1.clear();
    System::Console::WriteLine("size() = {0}", c1.size());
    return (0);
    }
```

```Output
a b c
size() = 0
a b
size() = 0
```

## <a name="multisetconst_iterator-stlclr"></a><a name="const_iterator"></a> zestaw wielokrotny:: const_iterator (STL/CLR)

Typ iteratora stałego dla kontrolowanej sekwencji.

### <a name="syntax"></a>Składnia

```cpp
typedef T2 const_iterator;
```

### <a name="remarks"></a>Uwagi

Typ opisuje obiekt nieokreślonego typu `T2` , który może obsłużyć jako stały iterator dwukierunkowy dla kontrolowanej sekwencji.

### <a name="example"></a>Przykład

```cpp
// cliext_multiset_const_iterator.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display contents " a b c"
    Mymultiset::const_iterator cit = c1.begin();
    for (; cit != c1.end(); ++cit)
        System::Console::Write("{0} ", *cit);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="multisetconst_reference-stlclr"></a><a name="const_reference"></a> zestaw wielokrotny:: const_reference (STL/CLR)

Typ stałego odwołania do elementu.

### <a name="syntax"></a>Składnia

```cpp
typedef value_type% const_reference;
```

### <a name="remarks"></a>Uwagi

Typ opisuje stałe odwołanie do elementu.

### <a name="example"></a>Przykład

```cpp
// cliext_multiset_const_reference.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    Mymultiset::const_iterator cit = c1.begin();
    for (; cit != c1.end(); ++cit)
        {   // get a const reference to an element
        Mymultiset::const_reference cref = *cit;
        System::Console::Write("{0} ", cref);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="multisetconst_reverse_iterator-stlclr"></a><a name="const_reverse_iterator"></a> zestaw wielokrotny:: const_reverse_iterator (STL/CLR)

Typ iteratora stałego zwrotnego dla kontrolowanej sekwencji.

### <a name="syntax"></a>Składnia

```cpp
typedef T4 const_reverse_iterator;
```

### <a name="remarks"></a>Uwagi

Typ opisuje obiekt nieokreślonego typu `T4` , który może być używany jako ciągły iterator odwrotny dla kontrolowanej sekwencji.

### <a name="example"></a>Przykład

```cpp
// cliext_multiset_const_reverse_iterator.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display contents " a b c" reversed
    Mymultiset::const_reverse_iterator crit = c1.rbegin();
    for (; crit != c1.rend(); ++crit)
        System::Console::Write("{0} ", *crit);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
c b a
```

## <a name="multisetcount-stlclr"></a><a name="count"></a> wielokrotne:: Count (STL/CLR)

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
// cliext_multiset_count.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    System::Console::WriteLine("count(L'A') = {0}", c1.count(L'A'));
    System::Console::WriteLine("count(L'b') = {0}", c1.count(L'b'));
    System::Console::WriteLine("count(L'C') = {0}", c1.count(L'C'));
    return (0);
    }
```

```Output
a b c
count(L'A') = 0
count(L'b') = 1
count(L'C') = 0
```

## <a name="multisetdifference_type-stlclr"></a><a name="difference_type"></a> zestaw wielokrotny::d ifference_type (STL/CLR)

Typy podpisanej odległości między dwoma elementami.

### <a name="syntax"></a>Składnia

```cpp
typedef int difference_type;
```

### <a name="remarks"></a>Uwagi

Typ opisuje prawdopodobnie ujemną liczbę elementów.

### <a name="example"></a>Przykład

```cpp
// cliext_multiset_difference_type.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // compute positive difference
    Mymultiset::difference_type diff = 0;
    for (Mymultiset::iterator it = c1.begin(); it != c1.end(); ++it)
        ++diff;
    System::Console::WriteLine("end()-begin() = {0}", diff);

    // compute negative difference
    diff = 0;
    for (Mymultiset::iterator it = c1.end(); it != c1.begin(); --it)
        --diff;
    System::Console::WriteLine("begin()-end() = {0}", diff);
    return (0);
    }
```

```Output
a b c
end()-begin() = 3
begin()-end() = -3
```

## <a name="multisetempty-stlclr"></a><a name="empty"></a> wielokrotne:: empty (STL/CLR)

Sprawdza, czy nie ma żadnych elementów.

### <a name="syntax"></a>Składnia

```cpp
bool empty();
```

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca wartość true dla pustej kontrolowanej sekwencji. Jest odpowiednikiem zestawu [wielokrotnego:: size (STL/CLR)](#size) `() == 0` . Służy do sprawdzania, czy zestaw wielokrotny jest pusty.

### <a name="example"></a>Przykład

```cpp
// cliext_multiset_empty.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
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
a b c
size() = 3
empty() = False
size() = 0
empty() = True
```

## <a name="multisetend-stlclr"></a><a name="end"></a> wielokrotne:: end (STL/CLR)

Określa koniec kontrolowanej sekwencji.

### <a name="syntax"></a>Składnia

```cpp
iterator end();
```

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca iterator dwukierunkowy, który wskazuje tuż poza końcem kontrolowanej sekwencji. Służy do uzyskania iteratora, który wyznacza koniec kontrolowanej sekwencji; jego stan nie zmienia się w przypadku zmiany długości kontrolowanej sekwencji.

### <a name="example"></a>Przykład

```cpp
// cliext_multiset_end.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // inspect last two items
    Mymultiset::iterator it = c1.end();
    --it;
    System::Console::WriteLine("*-- --end() = {0}", *--it);
    System::Console::WriteLine("*--end() = {0}", *++it);
    return (0);
    }
```

```Output
a b c
*-- --end() = b
*--end() = c
```

## <a name="multisetequal_range-stlclr"></a><a name="equal_range"></a> zestaw wielokrotny:: equal_range (STL/CLR)

Wyszukuje zakres, który odpowiada określonemu kluczowi.

### <a name="syntax"></a>Składnia

```cpp
cliext::pair<iterator, iterator> equal_range(key_type key);
```

#### <a name="parameters"></a>Parametry

*głównych*<br/>
Wartość klucza do wyszukania.

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca parę iteratorów `cliext::pair<iterator, iterator>(` [wielokrotnych:: lower_bound (STL/CLR)](#lower_bound) zestaw `(key),` [wielokrotny:: upper_bound (STL/CLR)](#upper_bound) `(key))` . Służy do określania zakresu elementów aktualnie w kontrolowanej sekwencji, która pasuje do określonego klucza.

### <a name="example"></a>Przykład

```cpp
// cliext_multiset_equal_range.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
typedef Mymultiset::pair_iter_iter Pairii;
int main()
    {
    Mymultiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // display results of failed search
    Pairii pair1 = c1.equal_range(L'x');
    System::Console::WriteLine("equal_range(L'x') empty = {0}",
        pair1.first == pair1.second);

    // display results of successful search
    pair1 = c1.equal_range(L'b');
    for (; pair1.first != pair1.second; ++pair1.first)
        System::Console::Write("{0} ", *pair1.first);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
equal_range(L'x') empty = True
b
```

## <a name="multiseterase-stlclr"></a><a name="erase"></a> wielokrotne:: Erase (STL/CLR)

Usuwa elementy z określonych pozycji.

### <a name="syntax"></a>Składnia

```cpp
iterator erase(iterator where);
iterator erase(iterator first, iterator last);
size_type erase(key_type key)
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

Pierwsza funkcja członkowska usuwa element kontrolowanej sekwencji wskazywany przez *WHERE*, a zwraca iterator, który wyznacza pierwszy element, który został poza elementem usunięty lub zestaw [wielokrotny:: end (STL/CLR)](#end) , `()` Jeśli taki element nie istnieje. Służy do usuwania pojedynczego elementu.

Druga funkcja członkowska usuwa elementy z kontrolowanej sekwencji z zakresu [ `first` , `last` ) i zwraca iterator, który wyznacza pierwszy element pozostały poza elementami usuniętymi lub `end()` Jeśli taki element nie istnieje. Jest on używany do usuwania elementów sąsiadujących lub więcej.

Trzecia funkcja członkowska usuwa każdy element kontrolowanej sekwencji, którego klucz ma równoważne porządkowanie do *klucza*i zwraca liczbę usuniętych elementów. Służy do usuwania i zliczania wszystkich elementów, które pasują do określonego klucza.

Każdy element wymazuje czas proporcjonalny do logarytmu liczby elementów w kontrolowanej sekwencji.

### <a name="example"></a>Przykład

```cpp
// cliext_multiset_erase.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // erase an element and reinspect
    System::Console::WriteLine("erase(begin()) = {0}",
        *c1.erase(c1.begin()));

    // add elements and display " b c d e"
    c1.insert(L'd');
    c1.insert(L'e');
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // erase all but end
    Mymultiset::iterator it = c1.end();
    System::Console::WriteLine("erase(begin(), end()-1) = {0}",
        *c1.erase(c1.begin(), --it));
    System::Console::WriteLine("size() = {0}", c1.size());
    return (0);
    }
```

```Output
a b c
erase(begin()) = b
b c d e
erase(begin(), end()-1) = e
size() = 1
```

## <a name="multisetfind-stlclr"></a><a name="find"></a> wielokrotne:: Find (STL/CLR)

Wyszukuje element, który odpowiada określonemu kluczowi.

### <a name="syntax"></a>Składnia

```cpp
iterator find(key_type key);
```

#### <a name="parameters"></a>Parametry

*głównych*<br/>
Wartość klucza do wyszukania.

### <a name="remarks"></a>Uwagi

Jeśli co najmniej jeden element w kontrolowanej sekwencji ma równoważne porządkowanie z *kluczem*, funkcja członkowska zwraca iterator wyznaczający jeden z tych elementów. w przeciwnym razie zwraca zestaw [wielokrotny:: end (STL/CLR)](#end) `()` . Służy do lokalizowania elementu w kontrolowanej sekwencji, który odpowiada określonemu kluczowi.

### <a name="example"></a>Przykład

```cpp
// cliext_multiset_find.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    System::Console::WriteLine("find {0} = {1}",
        L'A', c1.find(L'A') != c1.end());
    System::Console::WriteLine("find {0} = {1}",
        L'b', *c1.find(L'b'));
    System::Console::WriteLine("find {0} = {1}",
        L'C', c1.find(L'C') != c1.end());
    return (0);
    }
```

```Output
a b c
find A = False
find b = b
find C = False
```

## <a name="multisetgeneric_container-stlclr"></a><a name="generic_container"></a> zestaw wielokrotny:: generic_container (STL/CLR)

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
// cliext_multiset_generic_container.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct a generic container
    Mymultiset::generic_container^ gc1 = %c1;
    for each (wchar_t elem in gc1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // modify generic and display original
    gc1->insert(L'd');
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // modify original and display generic
    c1.insert(L'e');
    for each (wchar_t elem in gc1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
a b c
a b c d
a b c d e
```

## <a name="multisetgeneric_iterator-stlclr"></a><a name="generic_iterator"></a> zestaw wielokrotny:: generic_iterator (STL/CLR)

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
// cliext_multiset_generic_iterator.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct a generic container
    Mymultiset::generic_container^ gc1 = %c1;
    for each (wchar_t elem in gc1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // get an element and display it
    Mymultiset::generic_iterator gcit = gc1->begin();
    Mymultiset::generic_value gcval = *gcit;
    System::Console::WriteLine("{0} ", gcval);
    return (0);
    }
```

```Output
a b c
a b c
a
```

## <a name="multisetgeneric_reverse_iterator-stlclr"></a><a name="generic_reverse_iterator"></a> zestaw wielokrotny:: generic_reverse_iterator (STL/CLR)

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
// cliext_multiset_generic_reverse_iterator.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct a generic container
    Mymultiset::generic_container^ gc1 = %c1;
    for each (wchar_t elem in gc1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // get an element and display it
    Mymultiset::generic_reverse_iterator gcit = gc1->rbegin();
    Mymultiset::generic_value gcval = *gcit;
    System::Console::WriteLine("{0} ", gcval);
    return (0);
    }
```

```Output
a b c
a b c
c
```

## <a name="multisetgeneric_value-stlclr"></a><a name="generic_value"></a> zestaw wielokrotny:: generic_value (STL/CLR)

Typ elementu do użycia z interfejsem ogólnym dla kontenera.

### <a name="syntax"></a>Składnia

```cpp
typedef GValue generic_value;
```

### <a name="remarks"></a>Uwagi

Typ opisuje obiekt typu `GValue` , który opisuje wartość przechowywanego elementu do użycia z interfejsem ogólnym dla tej klasy kontenera szablonu.

### <a name="example"></a>Przykład

```cpp
// cliext_multiset_generic_value.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct a generic container
    Mymultiset::generic_container^ gc1 = %c1;
    for each (wchar_t elem in gc1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // get an element and display it
    Mymultiset::generic_iterator gcit = gc1->begin();
    Mymultiset::generic_value gcval = *gcit;
    System::Console::WriteLine("{0} ", gcval);
    return (0);
    }
```

```Output
a b c
a b c
a
```

## <a name="multisetinsert-stlclr"></a><a name="insert"></a> wielokrotne:: Insert (STL/CLR)

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
// cliext_multiset_insert.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // insert a single value, unique and duplicate
    System::Console::WriteLine("insert(L'x') = {0}",
        *c1.insert(L'x'));

    System::Console::WriteLine("insert(L'b') = {0}",
        *c1.insert(L'b'));

    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // insert a single value with hint
    System::Console::WriteLine("insert(begin(), L'y') = {0}",
        *c1.insert(c1.begin(), L'y'));
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // insert an iterator range
    Mymultiset c2;
    Mymultiset::iterator it = c1.end();
    c2.insert(c1.begin(), --it);
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // insert an enumeration
    Mymultiset c3;
    c3.insert(   // NOTE: cast is not needed
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c1);
    for each (wchar_t elem in c3)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
insert(L'x') = x
insert(L'b') = b
a b b c x
insert(begin(), L'y') = y
a b b c x y
a b b c x
a b b c x y
```

## <a name="multisetiterator-stlclr"></a><a name="iterator"></a> zestaw wielokrotny:: iterator (STL/CLR)

Typ iteratora dla kontrolowanej sekwencji.

### <a name="syntax"></a>Składnia

```cpp
typedef T1 iterator;
```

### <a name="remarks"></a>Uwagi

Typ opisuje obiekt nieokreślonego typu `T1` , który może obsłużyć iterator dwukierunkowy dla kontrolowanej sekwencji.

### <a name="example"></a>Przykład

```cpp
// cliext_multiset_iterator.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display contents " a b c"
    Mymultiset::iterator it = c1.begin();
    for (; it != c1.end(); ++it)
        System::Console::Write("{0} ", *it);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="multisetkey_comp-stlclr"></a><a name="key_comp"></a> zestaw wielokrotny:: key_comp (STL/CLR)

Kopiuje delegata porządkowania dla dwóch kluczy.

### <a name="syntax"></a>Składnia

```cpp
key_compare^key_comp();
```

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca delegat porządkowania używany do uporządkowania kontrolowanej sekwencji. Służy do porównywania dwóch kluczy.

### <a name="example"></a>Przykład

```cpp
// cliext_multiset_key_comp.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
    Mymultiset::key_compare^ kcomp = c1.key_comp();

    System::Console::WriteLine("compare(L'a', L'a') = {0}",
        kcomp(L'a', L'a'));
    System::Console::WriteLine("compare(L'a', L'b') = {0}",
        kcomp(L'a', L'b'));
    System::Console::WriteLine("compare(L'b', L'a') = {0}",
        kcomp(L'b', L'a'));
    System::Console::WriteLine();

    // test a different ordering rule
    Mymultiset c2 = cliext::greater<wchar_t>();
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

## <a name="multisetkey_compare-stlclr"></a><a name="key_compare"></a> zestaw wielokrotny:: key_compare (STL/CLR)

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
// cliext_multiset_key_compare.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
    Mymultiset::key_compare^ kcomp = c1.key_comp();

    System::Console::WriteLine("compare(L'a', L'a') = {0}",
        kcomp(L'a', L'a'));
    System::Console::WriteLine("compare(L'a', L'b') = {0}",
        kcomp(L'a', L'b'));
    System::Console::WriteLine("compare(L'b', L'a') = {0}",
        kcomp(L'b', L'a'));
    System::Console::WriteLine();

    // test a different ordering rule
    Mymultiset c2 = cliext::greater<wchar_t>();
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

## <a name="multisetkey_type-stlclr"></a><a name="key_type"></a> zestaw wielokrotny:: key_type (STL/CLR)

Typ klucza sortowania.

### <a name="syntax"></a>Składnia

```cpp
typedef Key key_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla *klucza*parametru szablonu.

### <a name="example"></a>Przykład

```cpp
// cliext_multiset_key_type.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display contents " a b c" using key_type
    for (Mymultiset::iterator it = c1.begin(); it != c1.end(); ++it)
        {   // store element in key_type object
        Mymultiset::key_type val = *it;

        System::Console::Write("{0} ", val);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="multisetlower_bound-stlclr"></a><a name="lower_bound"></a> zestaw wielokrotny:: lower_bound (STL/CLR)

Znajduje początek zakresu, który odpowiada określonemu kluczowi.

### <a name="syntax"></a>Składnia

```cpp
iterator lower_bound(key_type key);
```

#### <a name="parameters"></a>Parametry

*głównych*<br/>
Wartość klucza do wyszukania.

### <a name="remarks"></a>Uwagi

Funkcja członkowska określa pierwszy element `X` w kontrolowanej sekwencji, który ma równoważne porządkowanie do *klucza*. Jeśli taki element nie istnieje, zwraca zestaw [wielokrotny:: end (STL/CLR)](#end) `()` ; w przeciwnym razie zwraca iterator, który wyznacza `X` . Służy do lokalizowania początku sekwencji elementów aktualnie w kontrolowanej sekwencji, która pasuje do określonego klucza.

### <a name="example"></a>Przykład

```cpp
// cliext_multiset_lower_bound.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    System::Console::WriteLine("lower_bound(L'x')==end() = {0}",
        c1.lower_bound(L'x') == c1.end());

    System::Console::WriteLine("*lower_bound(L'a') = {0}",
        *c1.lower_bound(L'a'));
    System::Console::WriteLine("*lower_bound(L'b') = {0}",
        *c1.lower_bound(L'b'));
    return (0);
    }
```

```Output
a b c
lower_bound(L'x')==end() = True
*lower_bound(L'a') = a
*lower_bound(L'b') = b
```

## <a name="multisetmake_value-stlclr"></a><a name="make_value"></a> zestaw wielokrotny:: make_value (STL/CLR)

Konstruuje obiekt wartości.

### <a name="syntax"></a>Składnia

```cpp
static value_type make_value(key_type key);
```

#### <a name="parameters"></a>Parametry

*głównych*<br/>
Wartość klucza do użycia.

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca `value_type` obiekt, którego klucz jest *kluczem*. Służy do redagowania obiektu odpowiedniego do użycia z kilkoma innymi funkcjami składowymi.

### <a name="example"></a>Przykład

```cpp
// cliext_multiset_make_value.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
    c1.insert(Mymultiset::make_value(L'a'));
    c1.insert(Mymultiset::make_value(L'b'));
    c1.insert(Mymultiset::make_value(L'c'));

    // display contents " a b c"
    for each (Mymultiset::value_type elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="multisetmultiset-stlclr"></a><a name="multiset"></a> wielokrotne:: zestaw wielokrotny (STL/CLR)

Konstruuje obiekt kontenera.

### <a name="syntax"></a>Składnia

```cpp
multiset();
explicit multiset(key_compare^ pred);
multiset(multiset<Key>% right);
multiset(multiset<Key>^ right);
template<typename InIter>
    multisetmultiset(InIter first, InIter last);
template<typename InIter>
    multiset(InIter first, InIter last,
        key_compare^ pred);
multiset(System::Collections::Generic::IEnumerable<GValue>^ right);
multiset(System::Collections::Generic::IEnumerable<GValue>^ right,
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

`multiset();`

Inicjuje kontrolowaną sekwencję bez elementów z domyślnym predykatem kolejności `key_compare()` . Służy do określania pustej początkowej kontrolowanej sekwencji przy użyciu domyślnego predykatu porządkowania.

Konstruktor:

`explicit multiset(key_compare^ pred);`

Inicjuje kontrolowaną sekwencję bez elementów z predykatem porządkowania *pred*. Służy do określania pustej początkowej kontrolowanej sekwencji z określonym predykatem kolejności.

Konstruktor:

`multiset(multiset<Key>% right);`

Inicjuje kontrolowaną sekwencję z sekwencją [ `right.begin()` , `right.end()` ) z domyślnym predykatem kolejności. Służy do określenia początkowej kontrolowanej sekwencji, która jest kopią sekwencji kontrolowanej *przez obiekt zestawu*wielokrotnego z zastosowaniem domyślnego predykatu kolejności.

Konstruktor:

`multiset(multiset<Key>^ right);`

Inicjuje kontrolowaną sekwencję z sekwencją [ `right->begin()` , `right->end()` ) z domyślnym predykatem kolejności. Służy do określenia początkowej kontrolowanej sekwencji, która jest kopią sekwencji kontrolowanej *przez obiekt zestawu*wielokrotnego z zastosowaniem domyślnego predykatu kolejności.

Konstruktor:

`template<typename InIter> multiset(InIter first, InIter last);`

Inicjuje kontrolowaną sekwencję z sekwencją [ `first` , `last` ) z domyślnym predykatem kolejności. Służy do Przekształć sekwencję na kopię innej sekwencji z domyślnym predykatem kolejności.

Konstruktor:

`template<typename InIter> multiset(InIter first, InIter last, key_compare^ pred);`

Inicjuje kontrolowaną sekwencję z sekwencją [ `first` , `last` ) z predykatem porządkowania *pred*. Służy do Przekształć sekwencję na kopię innej sekwencji z określonym predykatem kolejności.

Konstruktor:

`multiset(System::Collections::Generic::IEnumerable<Key>^ right);`

Inicjuje kontrolowaną sekwencję z sekwencją wyznaczonej przez moduł wyliczający *po prawej stronie*przy użyciu domyślnego predykatu porządkowania. Jest on używany do kontrolowania kontrolowanej sekwencji kopii kolejnej sekwencji opisanej przez moduł wyliczający z domyślnym predykatem kolejności.

Konstruktor:

`multiset(System::Collections::Generic::IEnumerable<Key>^ right, key_compare^ pred);`

Inicjuje kontrolowaną sekwencję z sekwencją wyznaczonej przez moduł wyliczający *po prawej stronie*z predykatem porządkowania *pred*. Jest on używany do kontrolowania kontrolowanej sekwencji kopii kolejnej sekwencji opisanej przez moduł wyliczający z określonym predykatem kolejności.

### <a name="example"></a>Przykład

```cpp
// cliext_multiset_construct.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
// construct an empty container
    Mymultiset c1;
    System::Console::WriteLine("size() = {0}", c1.size());

    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct with an ordering rule
    Mymultiset c2 = cliext::greater_equal<wchar_t>();
    System::Console::WriteLine("size() = {0}", c2.size());

    c2.insert(c1.begin(), c1.end());
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct with an iterator range
    Mymultiset c3(c1.begin(), c1.end());
    for each (wchar_t elem in c3)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct with an iterator range and an ordering rule
    Mymultiset c4(c1.begin(), c1.end(),
        cliext::greater_equal<wchar_t>());
    for each (wchar_t elem in c4)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct with an enumeration
    Mymultiset c5(   // NOTE: cast is not needed
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c3);
    for each (wchar_t elem in c5)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct with an enumeration and an ordering rule
    Mymultiset c6(   // NOTE: cast is not needed
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c3,
            cliext::greater_equal<wchar_t>());
    for each (wchar_t elem in c6)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct from a generic container
    Mymultiset c7(c4);
    for each (wchar_t elem in c7)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct by copying another container
    Mymultiset c8(%c3);
    for each (wchar_t elem in c8)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
size() = 0
a b c
size() = 0
c b a
a b c
c b a
a b c
c b a
c b a
a b c
```

## <a name="multisetoperator-stlclr"></a><a name="op_as"></a> wielokrotne:: operator = (STL/CLR)

Zastępuje kontrolowaną sekwencję.

### <a name="syntax"></a>Składnia

```cpp
multiset<Key>% operator=(multiset<Key>% right);
```

#### <a name="parameters"></a>Parametry

*Kliknij*<br/>
Kontener do skopiowania.

### <a name="remarks"></a>Uwagi

Operator elementu członkowskiego kopiuje *prawo* do obiektu, a następnie zwraca **`*this`** . Służy do zastępowania kontrolowanej sekwencji kopią kontrolowanej sekwencji *po prawej stronie*.

### <a name="example"></a>Przykład

```cpp
// cliext_multiset_operator_as.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display contents " a b c"
    for each (Mymultiset::value_type elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // assign to a new container
    Mymultiset c2;
    c2 = c1;
// display contents " a b c"
    for each (Mymultiset::value_type elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
a b c
```

## <a name="multisetrbegin-stlclr"></a><a name="rbegin"></a> zestaw wielokrotny:: rbegin (STL/CLR)

Określa początek odwróconej sekwencji kontrolowanej.

### <a name="syntax"></a>Składnia

```cpp
reverse_iterator rbegin();
```

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca iterator odwrotny, który wyznacza ostatni element kontrolowanej sekwencji lub tuż poza początkiem pustej sekwencji. W związku z tym określa `beginning` odwrotną sekwencję. Służy do uzyskania iteratora, który wyznacza `current` początek kontrolowanej sekwencji widoczny w kolejności odwrotnej, ale jego stan może ulec zmianie w przypadku zmiany długości kontrolowanej sekwencji.

### <a name="example"></a>Przykład

```cpp
// cliext_multiset_rbegin.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // inspect first two items in reversed sequence
    Mymultiset::reverse_iterator rit = c1.rbegin();
    System::Console::WriteLine("*rbegin() = {0}", *rit);
    System::Console::WriteLine("*++rbegin() = {0}", *++rit);
    return (0);
    }
```

```Output
a b c
*rbegin() = c
*++rbegin() = b
```

## <a name="multisetreference-stlclr"></a><a name="reference"></a> wielokrotne:: Reference (STL/CLR)

Typ odwołania do elementu.

### <a name="syntax"></a>Składnia

```cpp
typedef value_type% reference;
```

### <a name="remarks"></a>Uwagi

Typ opisuje odwołanie do elementu.

### <a name="example"></a>Przykład

```cpp
// cliext_multiset_reference.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    Mymultiset::iterator it = c1.begin();
    for (; it != c1.end(); ++it)
        {   // get a reference to an element
        Mymultiset::reference ref = *it;
        System::Console::Write("{0} ", ref);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="multisetrend-stlclr"></a><a name="rend"></a> zestaw wielokrotny:: rend (STL/CLR)

Określa koniec odwróconej kontrolowanej sekwencji.

### <a name="syntax"></a>Składnia

```cpp
reverse_iterator rend();
```

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca iterator odwrotny, który wskazuje tuż poza początkiem kontrolowanej sekwencji. W związku z tym określa `end` odwrotną sekwencję. Służy do uzyskania iteratora, który wyznacza `current` koniec kontrolowanej sekwencji widoczny w odwrotnej kolejności, ale jego stan może ulec zmianie w przypadku zmiany długości kontrolowanej sekwencji.

### <a name="example"></a>Przykład

```cpp
// cliext_multiset_rend.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // inspect first two items
    Mymultiset::reverse_iterator rit = c1.rend();
    --rit;
    System::Console::WriteLine("*-- --rend() = {0}", *--rit);
    System::Console::WriteLine("*--rend() = {0}", *++rit);
    return (0);
    }
```

```Output
a b c
*-- --rend() = b
*--rend() = a
```

## <a name="multisetreverse_iterator-stlclr"></a><a name="reverse_iterator"></a> zestaw wielokrotny:: reverse_iterator (STL/CLR)

Typ iteratora odwrotnego dla kontrolowanej sekwencji.

### <a name="syntax"></a>Składnia

```cpp
typedef T3 reverse_iterator;
```

### <a name="remarks"></a>Uwagi

Typ opisuje obiekt nieokreślonego typu `T3` , który może być używany jako iterator odwrotny dla kontrolowanej sekwencji.

### <a name="example"></a>Przykład

```cpp
// cliext_multiset_reverse_iterator.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display contents " a b c" reversed
    Mymultiset::reverse_iterator rit = c1.rbegin();
    for (; rit != c1.rend(); ++rit)
        System::Console::Write("{0} ", *rit);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
c b a
```

## <a name="multisetsize-stlclr"></a><a name="size"></a> wielokrotne:: size (STL/CLR)

Liczy liczbę elementów.

### <a name="syntax"></a>Składnia

```cpp
size_type size();
```

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca długość kontrolowanej sekwencji. Służy do określania liczby elementów aktualnie w kontrolowanej sekwencji. Jeśli dowiesz się, czy sekwencja ma rozmiar różny od zera, zobacz zestaw [wielokrotny:: empty (STL/CLR)](#empty) `()` .

### <a name="example"></a>Przykład

```cpp
// cliext_multiset_size.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    System::Console::WriteLine("size() = {0} starting with 3", c1.size());

    // clear the container and reinspect
    c1.clear();
    System::Console::WriteLine("size() = {0} after clearing", c1.size());

    // add elements and clear again
    c1.insert(L'a');
    c1.insert(L'b');
    System::Console::WriteLine("size() = {0} after adding 2", c1.size());
    return (0);
    }
```

```Output
a b c
size() = 3 starting with 3
size() = 0 after clearing
size() = 2 after adding 2
```

## <a name="multisetsize_type-stlclr"></a><a name="size_type"></a> zestaw wielokrotny:: size_type (STL/CLR)

Typ podpisanej odległości między dwoma elementami.

### <a name="syntax"></a>Składnia

```cpp
typedef int size_type;
```

### <a name="remarks"></a>Uwagi

Typ opisuje nieujemną liczbę elementów.

### <a name="example"></a>Przykład

```cpp
// cliext_multiset_size_type.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // compute positive difference
    Mymultiset::size_type diff = 0;
    for (Mymultiset::iterator it = c1.begin(); it != c1.end(); ++it)
        ++diff;
    System::Console::WriteLine("end()-begin() = {0}", diff);
    return (0);
    }
```

```Output
a b c
end()-begin() = 3
```

## <a name="multisetswap-stlclr"></a><a name="swap"></a> wielokrotne:: swap (STL/CLR)

Zamienia zawartości dwóch kontenerów.

### <a name="syntax"></a>Składnia

```cpp
void swap(multiset<Key>% right);
```

#### <a name="parameters"></a>Parametry

*Kliknij*<br/>
Kontener, za pomocą którego ma zostać zamieniony zawartość.

### <a name="remarks"></a>Uwagi

Funkcja członkowska zamienia kontrolowane sekwencje między **`this`** i *po prawej*. Robi to w stałym czasie i nie zgłasza wyjątków. Jest ona używana jako Szybka metoda wymiany zawartości dwóch kontenerów.

### <a name="example"></a>Przykład

```cpp
// cliext_multiset_swap.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct another container with repetition of values
    Mymultiset c2;
    c2.insert(L'd');
    c2.insert(L'e');
    c2.insert(L'f');
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // swap and redisplay
    c1.swap(c2);
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
d e f
d e f
a b c
```

## <a name="multisetto_array-stlclr"></a><a name="to_array"></a> zestaw wielokrotny:: to_array (STL/CLR)

Kopiuje przekontrolowaną sekwencję do nowej tablicy.

### <a name="syntax"></a>Składnia

```cpp
cli::array<value_type>^ to_array();
```

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca tablicę zawierającą kontrolowaną sekwencję. Służy do uzyskania kopii kontrolowanej sekwencji w formularzu tablicowym.

### <a name="example"></a>Przykład

```cpp
// cliext_multiset_to_array.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // copy the container and modify it
    cli::array<wchar_t>^ a1 = c1.to_array();

    c1.insert(L'd');
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // display the earlier array copy
    for each (wchar_t elem in a1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c d
a b c
```

## <a name="multisetupper_bound-stlclr"></a><a name="upper_bound"></a> zestaw wielokrotny:: upper_bound (STL/CLR)

Znajduje koniec zakresu, który odpowiada określonemu kluczowi.

### <a name="syntax"></a>Składnia

```cpp
iterator upper_bound(key_type key);
```

#### <a name="parameters"></a>Parametry

*głównych*<br/>
Wartość klucza do wyszukania.

### <a name="remarks"></a>Uwagi

Funkcja członkowska określa ostatni element `X` w kontrolowanej sekwencji, który ma równoważne porządkowanie do *klucza*. Jeśli taki element nie istnieje lub `X` jest ostatnim elementem w kontrolowanej sekwencji, zwraca zestaw [wielokrotny:: end (STL/CLR)](#end) `()` ; w przeciwnym razie zwraca iterator, który wyznacza pierwszy element poza `X` . Służy do lokalizowania końca sekwencji elementów aktualnie w kontrolowanej sekwencji, która pasuje do określonego klucza.

### <a name="example"></a>Przykład

```cpp
// cliext_multiset_upper_bound.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    System::Console::WriteLine("upper_bound(L'x')==end() = {0}",
        c1.upper_bound(L'x') == c1.end());

    System::Console::WriteLine("*upper_bound(L'a') = {0}",
        *c1.upper_bound(L'a'));
    System::Console::WriteLine("*upper_bound(L'b') = {0}",
        *c1.upper_bound(L'b'));
    return (0);
    }
```

```Output
a b c
upper_bound(L'x')==end() = True
*upper_bound(L'a') = b
*upper_bound(L'b') = c
```

## <a name="multisetvalue_comp-stlclr"></a><a name="value_comp"></a> zestaw wielokrotny:: value_comp (STL/CLR)

Kopiuje delegata porządkowania dla dwóch wartości elementów.

### <a name="syntax"></a>Składnia

```cpp
value_compare^ value_comp();
```

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca delegat porządkowania używany do uporządkowania kontrolowanej sekwencji. Służy do porównywania dwóch wartości elementów.

### <a name="example"></a>Przykład

```cpp
// cliext_multiset_value_comp.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
    Mymultiset::value_compare^ kcomp = c1.value_comp();

    System::Console::WriteLine("compare(L'a', L'a') = {0}",
        kcomp(L'a', L'a'));
    System::Console::WriteLine("compare(L'a', L'b') = {0}",
        kcomp(L'a', L'b'));
    System::Console::WriteLine("compare(L'b', L'a') = {0}",
        kcomp(L'b', L'a'));
    System::Console::WriteLine();
    return (0);
    }
```

```Output
compare(L'a', L'a') = False
compare(L'a', L'b') = True
compare(L'b', L'a') = False
```

## <a name="multisetvalue_compare-stlclr"></a><a name="value_compare"></a> zestaw wielokrotny:: value_compare (STL/CLR)

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
// cliext_multiset_value_compare.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
    Mymultiset::value_compare^ kcomp = c1.value_comp();

    System::Console::WriteLine("compare(L'a', L'a') = {0}",
        kcomp(L'a', L'a'));
    System::Console::WriteLine("compare(L'a', L'b') = {0}",
        kcomp(L'a', L'b'));
    System::Console::WriteLine("compare(L'b', L'a') = {0}",
        kcomp(L'b', L'a'));
    System::Console::WriteLine();
    return (0);
    }
```

```Output
compare(L'a', L'a') = False
compare(L'a', L'b') = True
compare(L'b', L'a') = False
```

## <a name="multisetvalue_type-stlclr"></a><a name="value_type"></a> zestaw wielokrotny:: value_type (STL/CLR)

Typ elementu.

### <a name="syntax"></a>Składnia

```cpp
typedef generic_value value_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla `generic_value` .

### <a name="example"></a>Przykład

```cpp
// cliext_multiset_value_type.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display contents " a b c" using value_type
    for (Mymultiset::iterator it = c1.begin(); it != c1.end(); ++it)
        {   // store element in value_type object
        Mymultiset::value_type val = *it;

        System::Console::Write("{0} ", val);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="operator-multiset-stlclr"></a><a name="op_neq"></a> operator! = (zestaw wielokrotny) (STL/CLR)

Nierówne porównanie.

### <a name="syntax"></a>Składnia

```cpp
template<typename Key>
    bool operator!=(multiset<Key>% left,
        multiset<Key>% right);
```

#### <a name="parameters"></a>Parametry

*lewym*<br/>
Lewy kontener do porównania.

*Kliknij*<br/>
Prawy kontener do porównania.

### <a name="remarks"></a>Uwagi

Funkcja operatora zwraca wartość `!(left == right)` . Służy do sprawdzania, czy *lewo* nie jest uporządkowane *tak samo, jak w* przypadku porównywania dwóch zestawów wielozbiorówowych elementów według elementu.

### <a name="example"></a>Przykład

```cpp
// cliext_multiset_operator_ne.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // assign to a new container
    Mymultiset c2;
    c2.insert(L'a');
    c2.insert(L'b');
    c2.insert(L'd');

    // display contents " a b d"
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    System::Console::WriteLine("[a b c] != [a b c] is {0}",
        c1 != c1);
    System::Console::WriteLine("[a b c] != [a b d] is {0}",
        c1 != c2);
    return (0);
    }
```

```Output
a b c
a b d
[a b c] != [a b c] is False
[a b c] != [a b d] is True
```

## <a name="operatorlt-multiset-stlclr"></a><a name="op_lt"></a> operator &lt; (zestaw wielokrotny) (STL/CLR)

Lista jest mniejsza niż porównanie.

### <a name="syntax"></a>Składnia

```cpp
template<typename Key>
    bool operator<(multiset<Key>% left,
        multiset<Key>% right);
```

#### <a name="parameters"></a>Parametry

*lewym*<br/>
Lewy kontener do porównania.

*Kliknij*<br/>
Prawy kontener do porównania.

### <a name="remarks"></a>Uwagi

Funkcja operator zwraca wartość true, jeśli dla najniższej pozycji `i` `!(right[i] < left[i])` ma również wartość true `left[i] < right[i]` . W przeciwnym razie zwraca go przy `left->size() < right->size()` użyciu, aby sprawdzić, czy *lewo* jest uporządkowane przed *prawem* , gdy dwa zestawy wielozbiorowe są porównywane elementów według elementu.

### <a name="example"></a>Przykład

```cpp
// cliext_multiset_operator_lt.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // assign to a new container
    Mymultiset c2;
    c2.insert(L'a');
    c2.insert(L'b');
    c2.insert(L'd');

    // display contents " a b d"
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    System::Console::WriteLine("[a b c] < [a b c] is {0}",
        c1 < c1);
    System::Console::WriteLine("[a b c] < [a b d] is {0}",
        c1 < c2);
    return (0);
    }
```

```Output
a b c
a b d
[a b c] < [a b c] is False
[a b c] < [a b d] is True
```

## <a name="operatorlt-multiset-stlclr"></a><a name="op_lteq"></a> operator &lt; = (zestaw wielokrotny) (STL/CLR)

Lista jest mniejsza niż lub równa.

### <a name="syntax"></a>Składnia

```cpp
template<typename Key>
    bool operator<=(multiset<Key>% left,
        multiset<Key>% right);
```

#### <a name="parameters"></a>Parametry

*lewym*<br/>
Lewy kontener do porównania.

*Kliknij*<br/>
Prawy kontener do porównania.

### <a name="remarks"></a>Uwagi

Funkcja operatora zwraca wartość `!(right < left)` . Służy do sprawdzania *, czy nie* jest on uporządkowany po *prawej stronie* , gdy dwa zestawy wielozbiorowe są porównywane elementów według elementu.

### <a name="example"></a>Przykład

```cpp
// cliext_multiset_operator_le.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // assign to a new container
    Mymultiset c2;
    c2.insert(L'a');
    c2.insert(L'b');
    c2.insert(L'd');

    // display contents " a b d"
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    System::Console::WriteLine("[a b c] <= [a b c] is {0}",
        c1 <= c1);
    System::Console::WriteLine("[a b d] <= [a b c] is {0}",
        c2 <= c1);
    return (0);
    }
```

```Output
a b c
a b d
[a b c] <= [a b c] is True
[a b d] <= [a b c] is False
```

## <a name="operator-multiset-stlclr"></a><a name="op_eq"></a> operator = = (zestaw wielokrotny) (STL/CLR)

Wyświetl równe porównanie.

### <a name="syntax"></a>Składnia

```cpp
template<typename Key>
    bool operator==(multiset<Key>% left,
        multiset<Key>% right);
```

#### <a name="parameters"></a>Parametry

*lewym*<br/>
Lewy kontener do porównania.

*Kliknij*<br/>
Prawy kontener do porównania.

### <a name="remarks"></a>Uwagi

Funkcja operator zwraca wartość true tylko wtedy, gdy sekwencje sterowane przez *lewo* i *prawo* mają taką samą długość i, dla każdej pozycji `i` `left[i] ==` `right[i]` . Służy do sprawdzania, czy *lewa* jest uporządkowana *tak samo jak w* przypadku porównywania dwóch zestawów wielozbiorówowych elementów według elementu.

### <a name="example"></a>Przykład

```cpp
// cliext_multiset_operator_eq.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // assign to a new container
    Mymultiset c2;
    c2.insert(L'a');
    c2.insert(L'b');
    c2.insert(L'd');

    // display contents " a b d"
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    System::Console::WriteLine("[a b c] == [a b c] is {0}",
        c1 == c1);
    System::Console::WriteLine("[a b c] == [a b d] is {0}",
        c1 == c2);
    return (0);
    }
```

```Output
a b c
a b d
[a b c] == [a b c] is True
[a b c] == [a b d] is False
```

## <a name="operatorgt-multiset-stlclr"></a><a name="op_gt"></a> operator &gt; (zestaw wielokrotny) (STL/CLR)

Lista większa niż porównanie.

### <a name="syntax"></a>Składnia

```cpp
template<typename Key>
    bool operator>(multiset<Key>% left,
        multiset<Key>% right);
```

#### <a name="parameters"></a>Parametry

*lewym*<br/>
Lewy kontener do porównania.

*Kliknij*<br/>
Prawy kontener do porównania.

### <a name="remarks"></a>Uwagi

Funkcja operatora zwraca wartość `right` `<` `left` . Służy do sprawdzania, czy *lewa* jest uporządkowana po *prawej stronie* , gdy dwa zestawy wielozbiorowe są porównywane elementów według elementu.

### <a name="example"></a>Przykład

```cpp
// cliext_multiset_operator_gt.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // assign to a new container
    Mymultiset c2;
    c2.insert(L'a');
    c2.insert(L'b');
    c2.insert(L'd');

    // display contents " a b d"
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    System::Console::WriteLine("[a b c] > [a b c] is {0}",
        c1 > c1);
    System::Console::WriteLine("[a b d] > [a b c] is {0}",
        c2 > c1);
    return (0);
    }
```

```Output
a b c
a b d
[a b c] > [a b c] is False
[a b d] > [a b c] is True
```

## <a name="operatorgt-multiset-stlclr"></a><a name="op_gteq"></a> operator &gt; = (zestaw wielokrotny) (STL/CLR)

Lista jest większa lub równa porównaniu.

### <a name="syntax"></a>Składnia

```cpp
template<typename Key>
    bool operator>=(multiset<Key>% left,
        multiset<Key>% right);
```

#### <a name="parameters"></a>Parametry

*lewym*<br/>
Lewy kontener do porównania.

*Kliknij*<br/>
Prawy kontener do porównania.

### <a name="remarks"></a>Uwagi

Funkcja operatora zwraca wartość `!(left < right)` . Służy do sprawdzania, czy nie *jest on* uporządkowany przed *prawem* , gdy dwa zestawy wielozbiorowe są porównywane elementów według elementu.

### <a name="example"></a>Przykład

```cpp
// cliext_multiset_operator_ge.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // assign to a new container
    Mymultiset c2;
    c2.insert(L'a');
    c2.insert(L'b');
    c2.insert(L'd');

    // display contents " a b d"
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    System::Console::WriteLine("[a b c] >= [a b c] is {0}",
        c1 >= c1);
    System::Console::WriteLine("[a b c] >= [a b d] is {0}",
        c1 >= c2);
    return (0);
    }
```

```Output
a b c
a b d
[a b c] >= [a b c] is True
[a b c] >= [a b d] is False
```
