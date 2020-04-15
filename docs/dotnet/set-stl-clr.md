---
title: set (STL/CLR)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- cliext::set
- cliext::set::begin
- cliext::set::clear
- cliext::set::const_iterator
- cliext::set::const_reference
- cliext::set::const_reverse_iterator
- cliext::set::count
- cliext::set::difference_type
- cliext::set::empty
- cliext::set::end
- cliext::set::equal_range
- cliext::set::erase
- cliext::set::find
- cliext::set::generic_container
- cliext::set::generic_iterator
- cliext::set::generic_reverse_iterator
- cliext::set::generic_value
- cliext::set::insert
- cliext::set::iterator
- cliext::set::key_comp
- cliext::set::key_compare
- cliext::set::key_type
- cliext::set::lower_bound
- cliext::set::make_value
- cliext::set::operator=
- cliext::set::rbegin
- cliext::set::reference
- cliext::set::rend
- cliext::set::reverse_iterator
- cliext::set::set
- cliext::set::size
- cliext::set::size_type
- cliext::set::swap
- cliext::set::to_array
- cliext::set::upper_bound
- cliext::set::value_comp
- cliext::set::value_compare
- cliext::set::value_type
helpviewer_keywords:
- <cliext/set> header [STL/CLR]
- <set> header [STL/CLR]
- set class [STL/CLR]
- operator!= (set) member [STL/CLR]
- operator< (set) member [STL/CLR]
- operator<= (set) member [STL/CLR]
- operator== (set) member [STL/CLR]
- operator> (set) member [STL/CLR]
- operator>= (set) member [STL/CLR]
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
- operator= member [STL/CLR]
- rbegin member [STL/CLR]
- reference member [STL/CLR]
- rend member [STL/CLR]
- reverse_iterator member [STL/CLR]
- set member [STL/CLR]
- size member [STL/CLR]
- size_type member [STL/CLR]
- swap member [STL/CLR]
- to_array member [STL/CLR]
- upper_bound member [STL/CLR]
- value_comp member [STL/CLR]
- value_compare member [STL/CLR]
- value_type member [STL/CLR]
ms.assetid: 27d3628c-741a-43a7-bef1-5085536f679e
ms.openlocfilehash: 38b0a3278efd10ef5cc989a5fc900bf82d377eae
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81320305"
---
# <a name="set-stlclr"></a>set (STL/CLR)

Klasa szablonu opisuje obiekt, który kontroluje sekwencję o różnej długości elementów, która ma dostęp dwukierunkowy. Kontener `set` służy do zarządzania sekwencji elementów jako (prawie) zrównoważone uporządkowane drzewo węzłów, każdy przechowuje jeden element.

W poniższym `GValue` opisie jest `GKey`taka sama jak , która z kolei jest taka sama jak `Key^` *Key,* chyba że ten ostatni jest typem ref, w którym to przypadku jest .

## <a name="syntax"></a>Składnia

```cpp
template<typename Key>
    ref class set
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
Typ kluczowego składnika elementu w kontrolowanej sekwencji.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<cliext/set>

**Obszar nazw:** cliext

## <a name="declarations"></a>Deklaracje

|Definicja typu|Opis|
|---------------------|-----------------|
|[set::const_iterator (STL/CLR)](#const_iterator)|Typ iteratora stałego dla kontrolowanej sekwencji.|
|[set::const_reference (STL/CLR)](#const_reference)|Typ stałego odwołania do elementu.|
|[set::const_reverse_iterator (STL/CLR)](#const_reverse_iterator)|Typ stałego iteratora wstecznego dla kontrolowanej sekwencji.|
|[set::difference_type (STL/CLR)](#difference_type)|Typ (ewentualnie podpisana) odległość między dwoma elementami.|
|[set::generic_container (STL/CLR)](#generic_container)|Typ interfejsu ogólnego kontenera.|
|[set::generic_iterator (STL/CLR)](#generic_iterator)|Typ iteratora dla interfejsu ogólnego kontenera.|
|[set::generic_reverse_iterator (STL/CLR)](#generic_reverse_iterator)|Typ odwrotnego iteratora dla ogólnego interfejsu kontenera.|
|[set::generic_value (STL/CLR)](#generic_value)|Typ elementu dla interfejsu ogólnego kontenera.|
|[set::iterator (STL/CLR)](#iterator)|Typ iteratora dla kontrolowanej sekwencji.|
|[set::key_compare (STL/CLR)](#key_compare)|Pełnomocnik zamawiania dla dwóch kluczy.|
|[set::key_type (STL/CLR)](#key_type)|Typ klucza sortowania.|
|[set::reference (STL/CLR)](#reference)|Typ odwołania do elementu.|
|[set::reverse_iterator (STL/CLR)](#reverse_iterator)|Typ odwrotnego iteratora dla kontrolowanej sekwencji.|
|[set::size_type (STL/CLR)](#size_type)|Typ (nieujemnej) odległości między dwoma elementami.|
|[set::value_compare (STL/CLR)](#value_compare)|Pełnomocnik kolejności dla dwóch wartości elementu.|
|[set::value_type (STL/CLR)](#value_type)|Typ elementu.|

|Funkcja elementów członkowskich|Opis|
|---------------------|-----------------|
|[set::begin (STL/CLR)](#begin)|Określa początek kontrolowanej sekwencji.|
|[set::clear (STL/CLR)](#clear)|Usuwa wszystkie elementy.|
|[set::count (STL/CLR)](#count)|Zlicza elementy pasujące do określonego klucza.|
|[set::empty (STL/CLR)](#empty)|Sprawdza, czy nie ma żadnych elementów.|
|[set::end (STL/CLR)](#end)|Określa koniec kontrolowanej sekwencji.|
|[set::equal_range (STL/CLR)](#equal_range)|Wyszukuje zakres, który odpowiada określonemu kluczowi.|
|[set::erase (STL/CLR)](#erase)|Usuwa elementy z określonych pozycji.|
|[set::find (STL/CLR)](#find)|Wyszukuje element, który odpowiada określonemu kluczowi.|
|[set::insert (STL/CLR)](#insert)|Dodaje elementy.|
|[set::key_comp (STL/CLR)](#key_comp)|Kopiuje pełnomocnika zamówienia dla dwóch kluczy.|
|[set::lower_bound (STL/CLR)](#lower_bound)|Znajduje początek zakresu, który pasuje do określonego klucza.|
|[set::make_value (STL/CLR)](#make_value)|Konstruuje obiekt wartości.|
|[set::rbegin (STL/CLR)](#rbegin)|Wyznacza początek odwróconej kontrolowanej sekwencji.|
|[set::rend (STL/CLR)](#rend)|Wyznacza koniec odwróconej kontrolowanej sekwencji.|
|[set::set (STL/CLR)](#set)|Konstruuje obiekt kontenera.|
|[set::size (STL/CLR)](#size)|Liczy liczbę elementów.|
|[set::swap (STL/CLR)](#swap)|Zamienia zawartości dwóch kontenerów.|
|[set::to_array (STL/CLR)](#to_array)|Kopiuje kontrolowaną sekwencję do nowej tablicy.|
|[set::upper_bound (STL/CLR)](#upper_bound)|Znajduje koniec zakresu, który pasuje do określonego klucza.|
|[set::value_comp (STL/CLR)](#value_comp)|Kopiuje delegata zamawiania dla dwóch wartości elementów.|

|Operator|Opis|
|--------------|-----------------|
|[set::operator= (STL/CLR)](#op_as)|Zastępuje kontrolowaną sekwencję.|
|[operator!= (zestaw) (STL/CLR)](#op_neq)|Określa, czy `set` obiekt nie jest `set` równy innemu obiektowi.|
|[operator< (zestaw) (STL/CLR)](#op_lt)|Określa, czy `set` obiekt jest `set` mniejszy niż inny obiekt.|
|[operator<= (zestaw) (STL/CLR)](#op_lteq)|Określa, czy `set` obiekt jest mniejszy lub `set` równy innemu obiektowi.|
|[operator== (set) (STL/CLR)](#op_eq)|Określa, czy `set` obiekt jest `set` równy innemu obiektowi.|
|[operator> (zestaw) (STL/CLR)](#op_gt)|Określa, czy `set` obiekt jest `set` większy niż inny obiekt.|
|[operator>= (zestaw) (STL/CLR)](#op_gteq)|Określa, czy `set` obiekt jest większy lub `set` równy innemu obiektowi.|

## <a name="interfaces"></a>Interfejsy

|Interface|Opis|
|---------------|-----------------|
|<xref:System.ICloneable>|Duplikowanie obiektu.|
|<xref:System.Collections.IEnumerable>|Sekwencja przez elementy.|
|<xref:System.Collections.ICollection>|Obsługa grupy elementów.|
|<xref:System.Collections.Generic.IEnumerable%601>|Sekwencjonowania za pomocą wpisanych elementów.|
|<xref:System.Collections.Generic.ICollection%601>|Obsługa grupy wpisanych elementów.|
|Klucz\<ITree, wartość>|Obsługa kontenera ogólnego.|

## <a name="remarks"></a>Uwagi

Obiekt przydziela i zwalnia magazyn dla sekwencji, która kontroluje jako poszczególne węzły. Wstawia elementy do (prawie) zrównoważonego drzewa, które przechowuje uporządkowane przez zmianę łączy między węzłami, nigdy nie kopiując zawartość jednego węzła do drugiego. Oznacza to, że można swobodnie wstawiać i usuwać elementy bez zakłócania pozostałych elementów.

Obiekt porządkuji sekwencję, która steruje, wywołując przechowywany obiekt delegata typu [set::key_compare (STL/CLR)](../dotnet/set-key-compare-stl-clr.md). Można określić przechowywany obiekt delegata podczas konstruowania zestawu; Jeśli nie określisz obiektu delegata, `operator<(key_type, key_type)`domyślnym jest porównanie . Dostęp do tego przechowywanego obiektu można uzyskać, wywołując zestaw funkcji [członkowskich::key_comp (STL/CLR).](../dotnet/set-key-comp-stl-clr.md)`()`

Taki obiekt delegata musi nałożyć ścisłą słabą kolejność na klucze typu [zestaw::key_type (STL/CLR)](../dotnet/set-key-type-stl-clr.md). Oznacza to, dla `X` dowolnych dwóch kluczy i: `Y`

`key_comp()(X, Y)`zwraca ten sam wynik logiczny przy każdym wywołaniu.

Jeśli `key_comp()(X, Y)` jest to `key_comp()(Y, X)` prawda, to musi być false.

Jeśli `key_comp()(X, Y)` to prawda, to `X` mówi się, że jest zamawiany przed `Y`.

Jeśli `!key_comp()(X, Y) && !key_comp()(Y, X)` jest to `X` `Y` prawda, a następnie i mówi się, że równoważne zamawiania.

Dla każdego `X` elementu, `Y` który poprzedza `key_comp()(Y, X)` w kontrolowanej sekwencji, jest false. (W przypadku domyślnego obiektu delegata klucze nigdy nie zmniejszają wartości). W przeciwieństwie do [zestawu](../dotnet/set-stl-clr.md)klas `set` szablonów obiekt klasy szablonu nie wymaga, aby klucze dla wszystkich elementów były unikatowe. (Dwa lub więcej kluczy może mieć równoważne kolejność.)

Każdy element służy zarówno jako ey i wartość. Sekwencja jest reprezentowana w sposób, który umożliwia wyszukiwanie, wstawianie i usuwanie dowolnego elementu z liczbą operacji proporcjonalnych do logarytmu liczby elementów w sekwencji (czas logarytmiczny). Ponadto, wstawianie elementu nie unieważnia iteratorów, a usuwanie elementu unieważnia tylko te iteratory, które wskazują na usunięty element.

Zestaw obsługuje dwukierunkowe iteratory, co oznacza, że można przejść do sąsiednich elementów, biorąc pod uwagę iteratora, który wyznacza element w kontrolowanej sekwencji. Specjalny węzeł główny odpowiada iteratorowi zwracany przez [set::end (STL/CLR)](../dotnet/set-end-stl-clr.md)`()`. Można zdymisjonować tego iteratora, aby osiągnąć ostatni element w kontrolowanej sekwencji, jeśli jest obecny. Można przyrost set iteratora, aby dotrzeć do węzła głównego, a następnie porównać `end()`równe . Ale nie można wyłuskać `end()`iteratora zwróconego przez .

Należy zauważyć, że nie można odwoływać się do elementu zestawu bezpośrednio biorąc pod uwagę jego pozycję numeryczną - która wymaga iteratora dostępu losowego.

Iterator zestawu przechowuje dojście do skojarzonego węzła zestawu, który z kolei przechowuje dojście do skojarzonego z nim kontenera. Iteratorów można używać tylko z skojarzonymi obiektami kontenera. Iterator zestawu pozostaje prawidłowy, o ile skojarzony z nim węzeł zestawu jest skojarzony z jakimś zestawem. Co więcej, prawidłowy iterator jest wyłudowywany — można go użyć do uzyskania dostępu lub zmiany wartości `end()`elementu, którą wyznacza - o ile nie jest równa .

Wymazywanie lub usuwanie elementu wywołuje destruktora dla jego przechowywanej wartości. Zniszczenie kontenera powoduje wymazanie wszystkich elementów. W związku z tym kontener, którego typ elementu jest ref klasy zapewnia, że żadne elementy przetrwać kontenera. Należy jednak zauważyć, że kontener uchwytów *nie* niszczy jego elementów.

## <a name="members"></a>Elementy członkowskie

## <a name="setbegin-stlclr"></a><a name="begin"></a>zestaw::begin (STL/CLR)

Określa początek kontrolowanej sekwencji.

### <a name="syntax"></a>Składnia

```cpp
iterator begin();
```

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca dwukierunkowy iterator, który wyznacza pierwszy element kontrolowanej sekwencji lub tuż za końcem pustej sekwencji. Służy do uzyskania iteratora, który `current` wyznacza początek kontrolowanej sekwencji, ale jego stan może ulec zmianie, jeśli zmieni się długość kontrolowanej sekwencji.

### <a name="example"></a>Przykład

```cpp
// cliext_set_begin.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
    Myset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

// display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// inspect first two items
    Myset::iterator it = c1.begin();
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

## <a name="setclear-stlclr"></a><a name="clear"></a>zestaw::wyczyść (STL/CLR)

Usuwa wszystkie elementy.

### <a name="syntax"></a>Składnia

```cpp
void clear();
```

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego skutecznie wywołuje [set::erase (STL/CLR)](../dotnet/set-erase-stl-clr.md) `(` [set::begin (STL/CLR)](../dotnet/set-begin-stl-clr.md) `(),` [set::end (STL/CLR)](../dotnet/set-end-stl-clr.md)`())`. Można go użyć, aby upewnić się, że kontrolowana sekwencja jest pusta.

### <a name="example"></a>Przykład

```cpp
// cliext_set_clear.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
    Myset c1;
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

## <a name="setconst_iterator-stlclr"></a><a name="const_iterator"></a>zestaw::const_iterator (STL/CLR)

Typ iteratora stałego dla kontrolowanej sekwencji.

### <a name="syntax"></a>Składnia

```cpp
typedef T2 const_iterator;
```

### <a name="remarks"></a>Uwagi

Typ opisuje obiekt nieokreślonego typu, `T2` który może służyć jako stały dwukierunkowy iterator dla kontrolowanej sekwencji.

### <a name="example"></a>Przykład

```cpp
// cliext_set_const_iterator.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
    Myset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

// display contents " a b c"
    Myset::const_iterator cit = c1.begin();
    for (; cit != c1.end(); ++cit)
        System::Console::Write("{0} ", *cit);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="setconst_reference-stlclr"></a><a name="const_reference"></a>zestaw::const_reference (STL/CLR)

Typ stałego odwołania do elementu.

### <a name="syntax"></a>Składnia

```cpp
typedef value_type% const_reference;
```

### <a name="remarks"></a>Uwagi

Typ opisuje stałe odwołanie do elementu.

### <a name="example"></a>Przykład

```cpp
// cliext_set_const_reference.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
    Myset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

// display initial contents " a b c"
    Myset::const_iterator cit = c1.begin();
    for (; cit != c1.end(); ++cit)
        {   // get a const reference to an element
        Myset::const_reference cref = *cit;
        System::Console::Write("{0} ", cref);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="setconst_reverse_iterator-stlclr"></a><a name="const_reverse_iterator"></a>zestaw::const_reverse_iterator (STL/CLR)

Typ stałego iteratora wstecznego dla kontrolowanej sekwencji..

### <a name="syntax"></a>Składnia

```cpp
typedef T4 const_reverse_iterator;
```

### <a name="remarks"></a>Uwagi

Typ opisuje obiekt nieokreślonego typu, `T4` który może służyć jako stały iterator odwrotny dla kontrolowanej sekwencji.

### <a name="example"></a>Przykład

```cpp
// cliext_set_const_reverse_iterator.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
    Myset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

// display contents " a b c" reversed
    Myset::const_reverse_iterator crit = c1.rbegin();
    for (; crit != c1.rend(); ++crit)
        System::Console::Write("{0} ", *crit);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
c b a
```

## <a name="setcount-stlclr"></a><a name="count"></a>zestaw::count (STL/CLR)

Wyszukuje liczbę elementów pasujących do określonego klucza.

### <a name="syntax"></a>Składnia

```cpp
size_type count(key_type key);
```

#### <a name="parameters"></a>Parametry

*key*<br/>
Wartość klucza do wyszukania.

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca liczbę elementów w kontrolowanej sekwencji, które mają równoważną kolejność z *kluczem*. Służy do określenia liczby elementów aktualnie w kontrolowanej sekwencji, które pasują do określonego klucza.

### <a name="example"></a>Przykład

```cpp
// cliext_set_count.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
    Myset c1;
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

## <a name="setdifference_type-stlclr"></a><a name="difference_type"></a>zestaw::dfference_type (STL/CLR)

Typy podpisanej odległości między dwoma elementami.

### <a name="syntax"></a>Składnia

```cpp
typedef int difference_type;
```

### <a name="remarks"></a>Uwagi

Typ opisuje prawdopodobnie ujemną liczbę elementów.

### <a name="example"></a>Przykład

```cpp
// cliext_set_difference_type.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
    Myset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

// display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// compute positive difference
    Myset::difference_type diff = 0;
    for (Myset::iterator it = c1.begin(); it != c1.end(); ++it)
        ++diff;
    System::Console::WriteLine("end()-begin() = {0}", diff);

// compute negative difference
    diff = 0;
    for (Myset::iterator it = c1.end(); it != c1.begin(); --it)
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

## <a name="setempty-stlclr"></a><a name="empty"></a>zestaw::empty (STL/CLR)

Sprawdza, czy nie ma żadnych elementów.

### <a name="syntax"></a>Składnia

```cpp
bool empty();
```

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca wartość true dla pustej kontrolowanej sekwencji. Jest odpowiednikiem [zestawu::size (STL/CLR)](../dotnet/set-size-stl-clr.md)`() == 0`. Można go użyć do sprawdzenia, czy zestaw jest pusty.

### <a name="example"></a>Przykład

```cpp
// cliext_set_empty.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
    Myset c1;
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

## <a name="setend-stlclr"></a><a name="end"></a>zestaw::koniec (STL/CLR)

Określa koniec kontrolowanej sekwencji.

### <a name="syntax"></a>Składnia

```cpp
iterator end();
```

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca dwukierunkowy iterator, który wskazuje tuż za końcem kontrolowanej sekwencji. Służy do uzyskania iteratora, który wyznacza koniec kontrolowanej sekwencji; jego stan nie zmienia się, jeśli zmienia się długość kontrolowanej sekwencji.

### <a name="example"></a>Przykład

```cpp
// cliext_set_end.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
    Myset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

// display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// inspect last two items
    Myset::iterator it = c1.end();
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

## <a name="setequal_range-stlclr"></a><a name="equal_range"></a>zestaw::equal_range (STL/CLR)

Wyszukuje zakres, który odpowiada określonemu kluczowi.

### <a name="syntax"></a>Składnia

```cpp
cliext::pair<iterator, iterator> equal_range(key_type key);
```

#### <a name="parameters"></a>Parametry

*key*<br/>
Wartość klucza do wyszukania.

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca parę `cliext::pair<iterator, iterator>(` iteratorów [zestaw::lower_bound (STL/CLR)](../dotnet/set-lower-bound-stl-clr.md) `(key),` [set::upper_bound (STL/CLR)](../dotnet/set-upper-bound-stl-clr.md)`(key))`. Służy do określenia zakresu elementów aktualnie w kontrolowanej sekwencji, które pasują do określonego klucza.

### <a name="example"></a>Przykład

```cpp
// cliext_set_equal_range.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
typedef Myset::pair_iter_iter Pairii;
int main()
    {
    Myset c1;
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

## <a name="seterase-stlclr"></a><a name="erase"></a>zestaw::wymazywanie (STL/CLR)

Usuwa elementy z określonych pozycji.

### <a name="syntax"></a>Składnia

```cpp
iterator erase(iterator where);
iterator erase(iterator first, iterator last);
size_type erase(key_type key)
```

#### <a name="parameters"></a>Parametry

*Pierwszym*<br/>
Początek zakresu do usunięcia.

*key*<br/>
Wartość klucza do usunięcia.

*Ostatnio*<br/>
Koniec zakresu do usunięcia.

*where*<br/>
Element do usunięcia.

### <a name="remarks"></a>Uwagi

Funkcja pierwszego elementu członkowskiego usuwa element kontrolowanej sekwencji wskazywowany przez *where*i zwraca iterator, który wyznacza pierwszy element pozostały poza usuniętym elementem lub [set::end (STL/CLR),](../dotnet/set-end-stl-clr.md) `()` jeśli taki element nie istnieje. Można go użyć do usunięcia pojedynczego elementu.

Funkcja drugiego elementu członkowskiego usuwa elementy kontrolowanej sekwencji w zakresie [`first`, `last`i zwraca iterator, który `end()` wyznacza pierwszy element pozostały poza usunięte elementy lub jeśli taki element nie istnieje.. Służy do usuwania elementów zerowych lub bardziej ciągłych.

Funkcja trzeciego elementu członkowskiego usuwa dowolny element kontrolowanej sekwencji, którego klucz ma równoważną kolejność *do klucza,* i zwraca liczbę usuniętych elementów. Służy do usuwania i zliczania wszystkich elementów, które pasują do określonego klucza.

Każde wymazanie elementu wymaga czasu proporcjonalnego do logarytmu liczby elementów w kontrolowanej sekwencji.

### <a name="example"></a>Przykład

```cpp
// cliext_set_erase.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
    Myset c1;
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
    Myset::iterator it = c1.end();
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

## <a name="setfind-stlclr"></a><a name="find"></a>zestaw::find (STL/CLR)

Wyszukuje element, który odpowiada określonemu kluczowi.

### <a name="syntax"></a>Składnia

```cpp
iterator find(key_type key);
```

#### <a name="parameters"></a>Parametry

*key*<br/>
Wartość klucza do wyszukania.

### <a name="remarks"></a>Uwagi

Jeśli co najmniej jeden element w kontrolowanej sekwencji ma równoważną kolejność z *kluczem,* funkcja elementu członkowskiego zwraca iterator wyznaczający jeden z tych elementów; w przeciwnym razie zwraca [zestaw::end (STL/CLR)](../dotnet/set-end-stl-clr.md)`()`. Służy do zlokalizowania elementu aktualnie w kontrolowanej sekwencji, który pasuje do określonego klucza.

### <a name="example"></a>Przykład

```cpp
// cliext_set_find.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
    Myset c1;
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

## <a name="setgeneric_container-stlclr"></a><a name="generic_container"></a>zestaw::generic_container (STL/CLR)

Typ interfejsu ogólnego kontenera.

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
// cliext_set_generic_container.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
    Myset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// construct a generic container
    Myset::generic_container^ gc1 = %c1;
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

## <a name="setgeneric_iterator-stlclr"></a><a name="generic_iterator"></a>zestaw::generic_iterator (STL/CLR)

Typ iteratora do użycia z interfejsem ogólnym dla kontenera.

### <a name="syntax"></a>Składnia

```cpp
typedef Microsoft::VisualC::StlClr::Generic::
    ContainerBidirectionalIterator<generic_value>
    generic_iterator;
```

### <a name="remarks"></a>Uwagi

Typ opisuje ogólny iterator, który może być używany z interfejsem ogólnym dla tej klasy kontenera szablonu.

### <a name="example"></a>Przykład

```cpp
// cliext_set_generic_iterator.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
    Myset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// construct a generic container
    Myset::generic_container^ gc1 = %c1;
    for each (wchar_t elem in gc1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// get an element and display it
    Myset::generic_iterator gcit = gc1->begin();
    Myset::generic_value gcval = *gcit;
    System::Console::WriteLine("{0} ", gcval);
    return (0);
    }
```

```Output
a b c
a b c
a
```

## <a name="setgeneric_reverse_iterator-stlclr"></a><a name="generic_reverse_iterator"></a>zestaw::generic_reverse_iterator (STL/CLR)

Typ iteratora wstecznego do użycia z interfejsem ogólnym dla kontenera.

### <a name="syntax"></a>Składnia

```cpp
typedef Microsoft::VisualC::StlClr::Generic::
    ReverseRandomAccessIterator<generic_value>
    generic_reverse_iterator;
```

### <a name="remarks"></a>Uwagi

Typ opisuje ogólny iterator odwrotny, który może być używany z interfejsem ogólnym dla tej klasy kontenera szablonu.

### <a name="example"></a>Przykład

```cpp
// cliext_set_generic_reverse_iterator.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
    Myset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// construct a generic container
    Myset::generic_container^ gc1 = %c1;
    for each (wchar_t elem in gc1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// get an element and display it
    Myset::generic_reverse_iterator gcit = gc1->rbegin();
    Myset::generic_value gcval = *gcit;
    System::Console::WriteLine("{0} ", gcval);
    return (0);
    }
```

```Output
a b c
a b c
c
```

## <a name="setgeneric_value-stlclr"></a><a name="generic_value"></a>zestaw::generic_value (STL/CLR)

Typ elementu do użycia z interfejsem ogólnym dla kontenera.

### <a name="syntax"></a>Składnia

```cpp
typedef GValue generic_value;
```

### <a name="remarks"></a>Uwagi

Typ opisuje obiekt typu, `GValue` który opisuje wartość elementu przechowywanego do użytku z interfejsem ogólnym dla tej klasy kontenera szablonu.

### <a name="example"></a>Przykład

```cpp
// cliext_set_generic_value.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
    Myset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// construct a generic container
    Myset::generic_container^ gc1 = %c1;
    for each (wchar_t elem in gc1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// get an element and display it
    Myset::generic_iterator gcit = gc1->begin();
    Myset::generic_value gcval = *gcit;
    System::Console::WriteLine("{0} ", gcval);
    return (0);
    }
```

```Output
a b c
a b c
a
```

## <a name="setinsert-stlclr"></a><a name="insert"></a>zestaw::insert (STL/CLR)

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

*Pierwszym*<br/>
Początek zakresu do wstawienia.

*Ostatnio*<br/>
Koniec zakresu do wstawienia.

*Prawo*<br/>
Wyliczenie do wstawienia.

*Val*<br/>
Wartość klucza do wstawienia.

*where*<br/>
Gdzie w pojemniku wstawić (tylko wskazówka).

### <a name="remarks"></a>Uwagi

Każda z funkcji członkowskich wstawia sekwencję określoną przez pozostałe argumenty.

Pierwsza funkcja elementu członkowskiego stara się wstawić element o *wartości val* `X`i zwraca parę wartości . Jeśli `X.second` jest `X.first` true, wyznacza nowo wstawiony element; w `X.first` przeciwnym razie wyznacza element o równoważnej kolejności, który już istnieje i nie zostanie wstawiony żaden nowy element. Służy do wstawiania pojedynczego elementu.

Druga funkcja elementu członkowskiego wstawia element o *wartości val*, używając *jako* wskazówka (w celu zwiększenia wydajności) i zwraca iterator, który wyznacza nowo wstawiony element. Służy do wstawiania pojedynczego elementu, który może przylegać do elementu, który znasz.

Funkcja trzeciego elementu członkowskiego wstawia sekwencję [`first`, `last`). Służy do wstawiania zero lub więcej elementów skopiowanych z innej sekwencji.

Funkcja czwartego elementu członkowskiego wstawia sekwencję wyznaczoną przez *prawo*. Służy do wstawiania sekwencji opisane przez wyliczacza.

Każde wstawianie elementu wymaga czasu proporcjonalnego do logarytmu liczby elementów w kontrolowanej sekwencji. Wstawianie może wystąpić w zamortyzowanym czasie stałym, jednak biorąc pod uwagę wskazówkę, która wyznacza element przylegający do punktu wstawiania.

### <a name="example"></a>Przykład

```cpp
// cliext_set_insert.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
typedef Myset::pair_iter_bool Pairib;
int main()
    {
    Myset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

// display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// insert a single value, unique and duplicate
    Pairib pair1 = c1.insert(L'x');
    System::Console::WriteLine("insert(L'x') = [{0} {1}]",
        *pair1.first, pair1.second);

    pair1 = c1.insert(L'b');
    System::Console::WriteLine("insert(L'b') = [{0} {1}]",
        *pair1.first, pair1.second);

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
    Myset c2;
    Myset::iterator it = c1.end();
    c2.insert(c1.begin(), --it);
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// insert an enumeration
    Myset c3;
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
insert(L'x') = [x True]
insert(L'b') = [b False]
a b c x
insert(begin(), L'y') = y
a b c x y
a b c x
a b c x y
```

## <a name="setiterator-stlclr"></a><a name="iterator"></a>zestaw::iterator (STL/CLR)

Typ iteratora dla kontrolowanej sekwencji.

### <a name="syntax"></a>Składnia

```cpp
typedef T1 iterator;
```

### <a name="remarks"></a>Uwagi

Typ opisuje obiekt nieokreślonego typu, `T1` który może służyć jako dwukierunkowy iterator dla kontrolowanej sekwencji.

### <a name="example"></a>Przykład

```cpp
// cliext_set_iterator.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
    Myset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

// display contents " a b c"
    Myset::iterator it = c1.begin();
    for (; it != c1.end(); ++it)
        System::Console::Write("{0} ", *it);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="setkey_comp-stlclr"></a><a name="key_comp"></a>zestaw::key_comp (STL/CLR)

Kopiuje pełnomocnika zamówienia dla dwóch kluczy.

### <a name="syntax"></a>Składnia

```cpp
key_compare^key_comp();
```

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca delegata zamawiania używanego do zamawiania kontrolowanej sekwencji. Służy do porównywania dwóch kluczy.

### <a name="example"></a>Przykład

```cpp
// cliext_set_key_comp.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
    Myset c1;
    Myset::key_compare^ kcomp = c1.key_comp();

    System::Console::WriteLine("compare(L'a', L'a') = {0}",
        kcomp(L'a', L'a'));
    System::Console::WriteLine("compare(L'a', L'b') = {0}",
        kcomp(L'a', L'b'));
    System::Console::WriteLine("compare(L'b', L'a') = {0}",
        kcomp(L'b', L'a'));
    System::Console::WriteLine();

// test a different ordering rule
    Myset c2 = cliext::greater<wchar_t>();
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

## <a name="setkey_compare-stlclr"></a><a name="key_compare"></a>zestaw::key_compare (STL/CLR)

Pełnomocnik zamawiania dla dwóch kluczy.

### <a name="syntax"></a>Składnia

```cpp
Microsoft::VisualC::StlClr::BinaryDelegate<GKey, GKey, bool>
    key_compare;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem delegata, który określa kolejność jego kluczowych argumentów.

### <a name="example"></a>Przykład

```cpp
// cliext_set_key_compare.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
    Myset c1;
    Myset::key_compare^ kcomp = c1.key_comp();

    System::Console::WriteLine("compare(L'a', L'a') = {0}",
        kcomp(L'a', L'a'));
    System::Console::WriteLine("compare(L'a', L'b') = {0}",
        kcomp(L'a', L'b'));
    System::Console::WriteLine("compare(L'b', L'a') = {0}",
        kcomp(L'b', L'a'));
    System::Console::WriteLine();

// test a different ordering rule
    Myset c2 = cliext::greater<wchar_t>();
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

## <a name="setkey_type-stlclr"></a><a name="key_type"></a>zestaw::key_type (STL/CLR)

Typ klucza sortowania.

### <a name="syntax"></a>Składnia

```cpp
typedef Key key_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem parametru *szablonu Key*.

### <a name="example"></a>Przykład

```cpp
// cliext_set_key_type.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
    Myset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

// display contents " a b c" using key_type
    for (Myset::iterator it = c1.begin(); it != c1.end(); ++it)
        {   // store element in key_type object
        Myset::key_type val = *it;

        System::Console::Write("{0} ", val);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="setlower_bound-stlclr"></a><a name="lower_bound"></a>zestaw::lower_bound (STL/CLR)

Znajduje początek zakresu, który pasuje do określonego klucza.

### <a name="syntax"></a>Składnia

```cpp
iterator lower_bound(key_type key);
```

#### <a name="parameters"></a>Parametry

*key*<br/>
Wartość klucza do wyszukania.

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego określa `X` pierwszy element w kontrolowanej sekwencji, który ma równoważną kolejność *do klucza*. Jeśli taki element nie istnieje, zwraca [zestaw::end (STL/CLR)](../dotnet/set-end-stl-clr.md)`()`; w przeciwnym razie zwraca iterator, który wyznacza `X`. Służy do zlokalizowania początku sekwencji elementów obecnie w kontrolowanej sekwencji, które pasują do określonego klucza.

### <a name="example"></a>Przykład

```cpp
// cliext_set_lower_bound.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
    Myset c1;
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

## <a name="setmake_value-stlclr"></a><a name="make_value"></a>zestaw::make_value (STL/CLR)

Konstruuje obiekt wartości.

### <a name="syntax"></a>Składnia

```cpp
static value_type make_value(key_type key);
```

#### <a name="parameters"></a>Parametry

*key*<br/>
Wartość klucza do użycia.

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego `value_type` zwraca obiekt, którego *kluczem*jest . Służy do tworzenia obiektu odpowiedniego do użycia z kilkoma innymi funkcjami elementów członkowskich.

### <a name="example"></a>Przykład

```cpp
// cliext_set_make_value.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
    Myset c1;
    c1.insert(Myset::make_value(L'a'));
    c1.insert(Myset::make_value(L'b'));
    c1.insert(Myset::make_value(L'c'));

// display contents " a b c"
    for each (Myset::value_type elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="setoperator-stlclr"></a><a name="op_as"></a>zestaw::operator= (STL/CLR)

Zastępuje kontrolowaną sekwencję.

### <a name="syntax"></a>Składnia

```cpp
set<Key>% operator=(set<Key>% right);
```

#### <a name="parameters"></a>Parametry

*Prawo*<br/>
Kontener do skopiowania.

### <a name="remarks"></a>Uwagi

Operator elementu członkowskiego kopiuje *prawo* `*this`do obiektu, a następnie zwraca . Można go użyć do zastąpienia kontrolowanej sekwencji kopią kontrolowanej sekwencji *w prawej*.

### <a name="example"></a>Przykład

```cpp
// cliext_set_operator_as.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
    Myset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

// display contents " a b c"
    for each (Myset::value_type elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// assign to a new container
    Myset c2;
    c2 = c1;
// display contents " a b c"
    for each (Myset::value_type elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
a b c
```

## <a name="setrbegin-stlclr"></a><a name="rbegin"></a>zestaw::rbegin (STL/CLR)

Wyznacza początek odwróconej kontrolowanej sekwencji.

### <a name="syntax"></a>Składnia

```cpp
reverse_iterator rbegin();
```

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca odwrotnej iteratora, który wyznacza ostatni element kontrolowanej sekwencji lub tuż poza początku pustej sekwencji. W związku z `beginning` tym wyznacza odwrotnej sekwencji. Służy do uzyskania iteratora, który `current` wyznacza początek kontrolowanej sekwencji widoczne w odwrotnej kolejności, ale jego stan może ulec zmianie, jeśli zmienia się długość kontrolowanej sekwencji.

### <a name="example"></a>Przykład

```cpp
// cliext_set_rbegin.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
    Myset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

// display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// inspect first two items in reversed sequence
    Myset::reverse_iterator rit = c1.rbegin();
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

## <a name="setreference-stlclr"></a><a name="reference"></a>zestaw::odwołanie (STL/CLR)

Typ odwołania do elementu.

### <a name="syntax"></a>Składnia

```cpp
typedef value_type% reference;
```

### <a name="remarks"></a>Uwagi

Typ opisuje odwołanie do elementu.

### <a name="example"></a>Przykład

```cpp
// cliext_set_reference.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
    Myset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

// display initial contents " a b c"
    Myset::iterator it = c1.begin();
    for (; it != c1.end(); ++it)
        {   // get a reference to an element
        Myset::reference ref = *it;
        System::Console::Write("{0} ", ref);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="setrend-stlclr"></a><a name="rend"></a>zestaw::rend (STL/CLR)

Wyznacza koniec odwróconej kontrolowanej sekwencji.

### <a name="syntax"></a>Składnia

```cpp
reverse_iterator rend();
```

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca odwrotnej iteratora, który wskazuje tuż poza początek kontrolowanej sekwencji. W związku z `end` tym wyznacza odwrotnej sekwencji. Służy do uzyskania iteratora, który `current` wyznacza koniec kontrolowanej sekwencji widoczne w odwrotnej kolejności, ale jego stan może ulec zmianie, jeśli zmienia się długość kontrolowanej sekwencji.

### <a name="example"></a>Przykład

```cpp
// cliext_set_rend.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
    Myset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

// display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// inspect first two items
    Myset::reverse_iterator rit = c1.rend();
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

## <a name="setreverse_iterator-stlclr"></a><a name="reverse_iterator"></a>zestaw::reverse_iterator (STL/CLR)

Typ odwrotnego iteratora dla kontrolowanej sekwencji.

### <a name="syntax"></a>Składnia

```cpp
typedef T3 reverse_iterator;
```

### <a name="remarks"></a>Uwagi

Typ opisuje obiekt nieokreślonego typu, `T3` który może służyć jako odwrotnej iterator dla kontrolowanej sekwencji.

### <a name="example"></a>Przykład

```cpp
// cliext_set_reverse_iterator.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
    Myset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

// display contents " a b c" reversed
    Myset::reverse_iterator rit = c1.rbegin();
    for (; rit != c1.rend(); ++rit)
        System::Console::Write("{0} ", *rit);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
c b a
```

## <a name="setset-stlclr"></a><a name="set"></a>zestaw::set (STL/CLR)

Konstruuje obiekt kontenera.

### <a name="syntax"></a>Składnia

```cpp
set();
explicit set(key_compare^ pred);
set(set<Key>% right);
set(set<Key>^ right);
template<typename InIter>
    setset(InIter first, InIter last);
template<typename InIter>
    set(InIter first, InIter last,
        key_compare^ pred);
set(System::Collections::Generic::IEnumerable<GValue>^ right);
set(System::Collections::Generic::IEnumerable<GValue>^ right,
    key_compare^ pred);
```

#### <a name="parameters"></a>Parametry

*Pierwszym*<br/>
Początek zakresu do wstawienia.

*Ostatnio*<br/>
Koniec zakresu do wstawienia.

*pred*<br/>
Kolejność predykatu dla kontrolowanej sekwencji.

*Prawo*<br/>
Obiekt lub zakres do wstawienia.

### <a name="remarks"></a>Uwagi

Konstruktor:

`set();`

inicjuje kontrolowaną sekwencję bez elementów, z `key_compare()`domyślnym predykatem porządkowania . Służy do określania pustej początkowej kontrolowanej sekwencji z domyślnym predykasem porządkowym.

Konstruktor:

`explicit set(key_compare^ pred);`

inicjuje kontrolowaną sekwencję bez elementów, z predykatem porządkowania *przed*. Służy do określenia pustej początkowej kontrolowanej sekwencji, z określonym predykatu kolejności.

Konstruktor:

`set(set<Key>% right);`

inicjuje kontrolowaną sekwencję`right.begin()` `right.end()`z sekwencją [ , ), z domyślnym predykatem porządkowania. Służy do określania początkowej kontrolowanej sekwencji, która jest kopią sekwencji kontrolowanej przez *ustawiony obiekt po prawej stronie,* z domyślnym predykatu porządkowania.

Konstruktor:

`set(set<Key>^ right);`

inicjuje kontrolowaną sekwencję`right->begin()` `right->end()`z sekwencją [ , ), z domyślnym predykatem porządkowania. Służy do określania początkowej kontrolowanej sekwencji, która jest kopią sekwencji kontrolowanej przez *ustawiony obiekt po prawej stronie,* z domyślnym predykatu porządkowania.

Konstruktor:

`template<typename InIter> set(InIter first, InIter last);`

inicjuje kontrolowaną sekwencję`first` `last`z sekwencją [ , ), z domyślnym predykatem porządkowania. Służy do sekwencji kontrolowanej kopię innej sekwencji, z domyślnym predykatu zamawiania.

Konstruktor:

`template<typename InIter> set(InIter first, InIter last, key_compare^ pred);`

inicjuje kontrolowaną sekwencję`first` `last`z sekwencją [ , ), z predykatem porządkowania *przed .* Można go użyć, aby kontrolowana sekwencja kopii innej sekwencji, z określonym predykatu kolejności.

Konstruktor:

`set(System::Collections::Generic::IEnumerable<Key>^ right);`

inicjuje kontrolowaną sekwencję z sekwencją wyznaczoną przez *prawo*wylicznika, z domyślnym predykatem porządkowania. Służy do sekwencji kontrolowanej kopię innej sekwencji opisane przez wyliczacza, z domyślnym predykatu porządkowania.

Konstruktor:

`set(System::Collections::Generic::IEnumerable<Key>^ right, key_compare^ pred);`

inicjuje kontrolowaną sekwencję z sekwencją wyznaczoną przez wyliczacz *po prawej stronie,* z predykatem porządkowania *przed .* Służy do sekwencji kontrolowanej kopię innej sekwencji opisane przez wyliczacza, z określonym predykatu kolejności.

### <a name="example"></a>Przykład

```cpp
// cliext_set_construct.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
// construct an empty container
    Myset c1;
    System::Console::WriteLine("size() = {0}", c1.size());

    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// construct with an ordering rule
    Myset c2 = cliext::greater_equal<wchar_t>();
    System::Console::WriteLine("size() = {0}", c2.size());

    c2.insert(c1.begin(), c1.end());
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// construct with an iterator range
    Myset c3(c1.begin(), c1.end());
    for each (wchar_t elem in c3)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// construct with an iterator range and an ordering rule
    Myset c4(c1.begin(), c1.end(),
        cliext::greater_equal<wchar_t>());
    for each (wchar_t elem in c4)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// construct with an enumeration
    Myset c5(   // NOTE: cast is not needed
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c3);
    for each (wchar_t elem in c5)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// construct with an enumeration and an ordering rule
    Myset c6(   // NOTE: cast is not needed
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c3,
            cliext::greater_equal<wchar_t>());
    for each (wchar_t elem in c6)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// construct from a generic container
    Myset c7(c4);
    for each (wchar_t elem in c7)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// construct by copying another container
    Myset c8(%c3);
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

## <a name="setsize-stlclr"></a><a name="size"></a>zestaw::size (STL/CLR)

Liczy liczbę elementów.

### <a name="syntax"></a>Składnia

```cpp
size_type size();
```

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca długość kontrolowanej sekwencji. Służy do określenia liczby elementów aktualnie w kontrolowanej sekwencji. Jeśli zależy Ci tylko na tym, czy sekwencja ma rozmiar niezerowy, zobacz [set::empty (STL/CLR)](../dotnet/set-empty-stl-clr.md)`()`.

### <a name="example"></a>Przykład

```cpp
// cliext_set_size.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
    Myset c1;
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

## <a name="setsize_type-stlclr"></a><a name="size_type"></a>zestaw::size_type (STL/CLR)

Typ podpisanej odległości między dwoma elementami.

### <a name="syntax"></a>Składnia

```cpp
typedef int size_type;
```

### <a name="remarks"></a>Uwagi

Typ opisuje liczbę elementów nieujemnych.

### <a name="example"></a>Przykład

```cpp
// cliext_set_size_type.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
    Myset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

// display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// compute positive difference
    Myset::size_type diff = 0;
    for (Myset::iterator it = c1.begin(); it != c1.end(); ++it)
        ++diff;
    System::Console::WriteLine("end()-begin() = {0}", diff);
    return (0);
    }
```

```Output
a b c
end()-begin() = 3
```

## <a name="setswap-stlclr"></a><a name="swap"></a>zestaw::swap (STL/CLR)

Zamienia zawartości dwóch kontenerów.

### <a name="syntax"></a>Składnia

```cpp
void swap(set<Key>% right);
```

#### <a name="parameters"></a>Parametry

*Prawo*<br/>
Kontener do wymiany zawartości z.

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zamienia kontrolowane `this` sekwencje między i *po prawej stronie*. Robi to w stałym czasie i nie zgłasza żadnych wyjątków. Można go używać jako szybki sposób wymiany zawartości dwóch kontenerów.

### <a name="example"></a>Przykład

```cpp
// cliext_set_swap.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
    Myset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

// display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// construct another container with repetition of values
    Myset c2;
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

## <a name="setto_array-stlclr"></a><a name="to_array"></a>zestaw::to_array (STL/CLR)

Kopiuje kontrolowaną sekwencję do nowej tablicy.

### <a name="syntax"></a>Składnia

```cpp
cli::array<value_type>^ to_array();
```

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca tablicę zawierającą kontrolowaną sekwencję. Służy do uzyskania kopii kontrolowanej sekwencji w formie tablicy.

### <a name="example"></a>Przykład

```cpp
// cliext_set_to_array.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
    Myset c1;
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

## <a name="setupper_bound-stlclr"></a><a name="upper_bound"></a>zestaw::upper_bound (STL/CLR)

Znajduje koniec zakresu, który pasuje do określonego klucza.

### <a name="syntax"></a>Składnia

```cpp
iterator upper_bound(key_type key);
```

#### <a name="parameters"></a>Parametry

*key*<br/>
Wartość klucza do wyszukania.

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego określa `X` ostatni element w kontrolowanej sekwencji, który ma równoważną kolejność *do klucza*. Jeśli taki element nie istnieje `X` lub jeśli jest ostatnim elementem w kontrolowanej sekwencji, zwraca [zestaw::end (STL/CLR)](../dotnet/set-end-stl-clr.md)`()`; w przeciwnym razie zwraca iterator, który `X`wyznacza pierwszy element poza . Służy do zlokalizowania końca sekwencji elementów obecnie w kontrolowanej sekwencji, które pasują do określonego klucza.

### <a name="example"></a>Przykład

```cpp
// cliext_set_upper_bound.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
    Myset c1;
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

## <a name="setvalue_comp-stlclr"></a><a name="value_comp"></a>zestaw::value_comp (STL/CLR)

Kopiuje delegata zamawiania dla dwóch wartości elementów.

### <a name="syntax"></a>Składnia

```cpp
value_compare^ value_comp();
```

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca delegata zamawiania używanego do zamawiania kontrolowanej sekwencji. Służy do porównywania wartości dwóch elementów.

### <a name="example"></a>Przykład

```cpp
// cliext_set_value_comp.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
    Myset c1;
    Myset::value_compare^ kcomp = c1.value_comp();

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

## <a name="setvalue_compare-stlclr"></a><a name="value_compare"></a>zestaw::value_compare (STL/CLR)

Pełnomocnik kolejności dla dwóch wartości elementu.

### <a name="syntax"></a>Składnia

```cpp
Microsoft::VisualC::StlClr::BinaryDelegate<generic_value, generic_value, bool>
    value_compare;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem delegata, który określa kolejność jego argumentów wartości.

### <a name="example"></a>Przykład

```cpp
// cliext_set_value_compare.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
    Myset c1;
    Myset::value_compare^ kcomp = c1.value_comp();

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

## <a name="setvalue_type-stlclr"></a><a name="value_type"></a>zestaw::value_type (STL/CLR)

Typ elementu.

### <a name="syntax"></a>Składnia

```cpp
typedef generic_value value_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem `generic_value`.

### <a name="example"></a>Przykład

```cpp
// cliext_set_value_type.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
    Myset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

// display contents " a b c" using value_type
    for (Myset::iterator it = c1.begin(); it != c1.end(); ++it)
        {   // store element in value_type object
        Myset::value_type val = *it;

        System::Console::Write("{0} ", val);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="operator-set-stlclr"></a><a name="op_neq"></a>operator!= (zestaw) (STL/CLR)

Lista nie równa porównanie.

### <a name="syntax"></a>Składnia

```cpp
template<typename Key>
    bool operator!=(set<Key>% left,
        set<Key>% right);
```

#### <a name="parameters"></a>Parametry

*Lewej*<br/>
Lewy pojemnik do porównania.

*Prawo*<br/>
Odpowiedni pojemnik do porównania.

### <a name="remarks"></a>Uwagi

Funkcja operatora `!(left == right)`zwraca . Służy do testowania, czy *left* nie jest uporządkowany tak samo jak *prawo,* gdy dwa zestawy są porównywane element po elemencie.

### <a name="example"></a>Przykład

```cpp
// cliext_set_operator_ne.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
    Myset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// assign to a new container
    Myset c2;
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

## <a name="operatorlt-set-stlclr"></a><a name="op_lt"></a>operator&lt; (zestaw) (STL/CLR)

Lista mniejsza niż porównanie.

### <a name="syntax"></a>Składnia

```cpp
template<typename Key>
    bool operator<(set<Key>% left,
        set<Key>% right);
```

#### <a name="parameters"></a>Parametry

*Lewej*<br/>
Lewy pojemnik do porównania.

*Prawo*<br/>
Odpowiedni pojemnik do porównania.

### <a name="remarks"></a>Uwagi

Funkcja operatora zwraca wartość true, `i` jeśli `!(right[i] < left[i])` dla najniższej `left[i] < right[i]`pozycji, dla której jest również prawdą, że . W przeciwnym `left->size() < right->size()` razie zwraca używasz go do testowania, czy *left* jest uporządkowany przed *prawym,* gdy dwa zestawy są porównywane element po elemencie.

### <a name="example"></a>Przykład

```cpp
// cliext_set_operator_lt.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
    Myset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// assign to a new container
    Myset c2;
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

## <a name="operatorlt-set-stlclr"></a><a name="op_lteq"></a>operator&lt;= (zestaw) (STL/CLR)

Lista mniej niż lub równe porównanie.

### <a name="syntax"></a>Składnia

```cpp
template<typename Key>
    bool operator<=(set<Key>% left,
        set<Key>% right);
```

#### <a name="parameters"></a>Parametry

*Lewej*<br/>
Lewy pojemnik do porównania.

*Prawo*<br/>
Odpowiedni pojemnik do porównania.

### <a name="remarks"></a>Uwagi

Funkcja operatora `!(right < left)`zwraca . Służy do testowania, czy *left* nie jest uporządkowany po *prawej,* gdy dwa zestawy są porównywane element po elemencie.

### <a name="example"></a>Przykład

```cpp
// cliext_set_operator_le.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
    Myset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// assign to a new container
    Myset c2;
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

## <a name="operator-set-stlclr"></a><a name="op_eq"></a>operator== (zestaw) (STL/CLR)

Lista równego porównania.

### <a name="syntax"></a>Składnia

```cpp
template<typename Key>
    bool operator==(set<Key>% left,
        set<Key>% right);
```

#### <a name="parameters"></a>Parametry

*Lewej*<br/>
Lewy pojemnik do porównania.

*Prawo*<br/>
Odpowiedni pojemnik do porównania.

### <a name="remarks"></a>Uwagi

Funkcja operatora zwraca wartość true tylko wtedy, gdy sekwencje kontrolowane przez `i` *lewą* i *prawą stronę* mają taką samą długość, a dla każdej pozycji `left[i] ==` `right[i]`. Służy do testowania, czy *left* jest uporządkowany tak samo jak *prawo,* gdy dwa zestawy są porównywane element po elemencie.

### <a name="example"></a>Przykład

```cpp
// cliext_set_operator_eq.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
    Myset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// assign to a new container
    Myset c2;
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

## <a name="operatorgt-set-stlclr"></a><a name="op_gt"></a>operator&gt; (zestaw) (STL/CLR)

Lista większa niż porównanie.

### <a name="syntax"></a>Składnia

```cpp
template<typename Key>
    bool operator>(set<Key>% left,
        set<Key>% right);
```

#### <a name="parameters"></a>Parametry

*Lewej*<br/>
Lewy pojemnik do porównania.

*Prawo*<br/>
Odpowiedni pojemnik do porównania.

### <a name="remarks"></a>Uwagi

Funkcja operatora `right` `<` `left`zwraca . Służy do testowania, czy *left* jest uporządkowany po *prawej stronie,* gdy dwa zestawy są porównywane element po elemencie.

### <a name="example"></a>Przykład

```cpp
// cliext_set_operator_gt.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
    Myset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// assign to a new container
    Myset c2;
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

## <a name="operatorgt-set-stlclr"></a><a name="op_gteq"></a>operator&gt;= (zestaw) (STL/CLR)

Lista większa niż lub równe porównanie.

### <a name="syntax"></a>Składnia

```cpp
template<typename Key>
    bool operator>=(set<Key>% left,
        set<Key>% right);
```

#### <a name="parameters"></a>Parametry

*Lewej*<br/>
Lewy pojemnik do porównania.

*Prawo*<br/>
Odpowiedni pojemnik do porównania.

### <a name="remarks"></a>Uwagi

Funkcja operatora `!(left < right)`zwraca . Służy do testowania, czy *left* nie jest uporządkowany przed *prawym,* gdy dwa zestawy są porównywane element po elemencie.

### <a name="example"></a>Przykład

```cpp
// cliext_set_operator_ge.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
    Myset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// assign to a new container
    Myset c2;
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
