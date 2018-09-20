---
title: Ustaw (STL/CLR) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::set
- cliext::operator!=
- cliext::operator<
- cliext::operator<=
- cliext::operator==
- cliext::operator>
- cliext::operator>=
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 45f72561875e5f0f7ad3f714e09d67825b48089e
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46399499"
---
# <a name="set-stlclr"></a>set (STL/CLR)

Klasa szablonu opisuje obiekt, który kontroluje różnej długości sekwencje elementów mającego dostęp dwukierunkowy. Korzystasz z kontenera `set` Zarządzanie sekwencji elementów jako drzewo uporządkowane (prawie) o zrównoważonym obciążeniu węzłów, w każdym przechowywania jeden element.

W poniższym opisie `GValue` jest taka sama jak `GKey`, który z kolei jest taka sama jak *klucz* o ile nie jest typem odwołania, w którym to przypadku jest `Key^`.

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

*Key*<br/>
Typ kluczowy składnik elementu w kontrolowanej sekwencji.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<cliext — / set >

**Namespace:** cliext —

## <a name="declarations"></a>Deklaracje

|Definicja typu|Opis|
|---------------------|-----------------|
|[set::const_iterator (STL/CLR)](#const_iterator)|Typ iteratora stałego dla kontrolowanej sekwencji.|
|[set::const_reference (STL/CLR)](#const_reference)|Typ stałego odwołania do elementu.|
|[set::const_reverse_iterator (STL/CLR)](#const_reverse_iterator)|Typ iteratora odwrotnego stałego dla kontrolowanej sekwencji.|
|[set::difference_type (STL/CLR)](#difference_type)|Typ (prawdopodobnie odległości ze znakiem) między dwoma elementami.|
|[set::generic_container (STL/CLR)](#generic_container)|Typ ogólny interfejs dla kontenera.|
|[set::generic_iterator (STL/CLR)](#generic_iterator)|Typ iteratora dla ogólny interfejs dla kontenera.|
|[set::generic_reverse_iterator (STL/CLR)](#generic_reverse_iterator)|Typ iteratora odwrotnego dla ogólny interfejs dla kontenera.|
|[set::generic_value (STL/CLR)](#generic_value)|Typ elementu dla ogólny interfejs dla kontenera.|
|[set::iterator (STL/CLR)](#iterator)|Typ iteratora dla kontrolowanej sekwencji.|
|[set::key_compare (STL/CLR)](#key_compare)|Szeregowania delegat dla obiektu dwa klucze.|
|[set::key_type (STL/CLR)](#key_type)|Typ klucza sortowania.|
|[set::reference (STL/CLR)](#reference)|Typ odwołania do elementu.|
|[set::reverse_iterator (STL/CLR)](#reverse_iterator)|Typ iteratora odwrotnego dla kontrolowanej sekwencji.|
|[set::size_type (STL/CLR)](#size_type)|Typ odległości (wartość nieujemną) między dwoma elementami.|
|[set::value_compare (STL/CLR)](#value_compare)|Szeregowania delegat dla obiektu dwie wartości elementów.|
|[set::value_type (STL/CLR)](#value_type)|Typ elementu.|

|Funkcja elementów członkowskich|Opis|
|---------------------|-----------------|
|[set::begin (STL/CLR)](#begin)|Określa początek kontrolowanej sekwencji.|
|[set::clear (STL/CLR)](#clear)|Usuwa wszystkie elementy.|
|[set::count (STL/CLR)](#count)|Liczba elementów pasujących do określonego klucza.|
|[set::empty (STL/CLR)](#empty)|Sprawdza, czy nie ma żadnych elementów.|
|[set::end (STL/CLR)](#end)|Określa koniec kontrolowanej sekwencji.|
|[set::equal_range (STL/CLR)](#equal_range)|Wyszukuje zakres, który odpowiada określonemu kluczowi.|
|[set::erase (STL/CLR)](#erase)|Usuwa elementy z określonych pozycji.|
|[set::find (STL/CLR)](#find)|Wyszukuje element, który odpowiada określonemu kluczowi.|
|[set::insert (STL/CLR)](#insert)|Dodaje elementy.|
|[set::key_comp (STL/CLR)](#key_comp)|Kopiuje szeregowania delegata dwa klucze.|
|[set::lower_bound (STL/CLR)](#lower_bound)|Znajduje początek zakresu, który odpowiada określonemu kluczowi.|
|[set::make_value (STL/CLR)](#make_value)|Tworzy obiekt wartości.|
|[set::rbegin (STL/CLR)](#rbegin)|Określa początek kontrolowanej sekwencji odwróconej.|
|[set::rend (STL/CLR)](#rend)|Określa koniec kontrolowanej sekwencji odwróconej.|
|[set::set (STL/CLR)](#set)|Konstruuje obiekt kontenera.|
|[set::size (STL/CLR)](#size)|Liczy liczbę elementów.|
|[set::swap (STL/CLR)](#swap)|Zamienia zawartości dwóch kontenerów.|
|[set::to_array (STL/CLR)](#to_array)|Kopiuje kontrolowanej sekwencji do nowej tablicy.|
|[set::upper_bound (STL/CLR)](#upper_bound)|Znajduje koniec zakresu, który odpowiada określonemu kluczowi.|
|[set::value_comp (STL/CLR)](#value_comp)|Kopiuje szeregowania delegata dwie wartości elementów.|

|Operator|Opis|
|--------------|-----------------|
|[set::operator= (STL/CLR)](#op_as)|Zastępuje kontrolowanej sekwencji.|
|[operator!= (set) (STL/CLR)](#op_neq)|Określa, czy `set` obiekt nie jest równy innemu `set` obiektu.|
|[operator< (set) (STL/CLR)](#op_lt)|Określa, czy `set` obiekt jest mniejszy niż inny `set` obiektu.|
|[operator<= (set) (STL/CLR)](#op_lteq)|Określa, czy `set` obiekt jest mniejszy niż lub równy innemu `set` obiektu.|
|[operator== (set) (STL/CLR)](#op_eq)|Określa, czy `set` obiekt jest równy innemu `set` obiektu.|
|[operator> (set) (STL/CLR)](#op_gt)|Określa, czy `set` obiekt jest większy niż inny `set` obiektu.|
|[operator>= (set) (STL/CLR)](#op_gteq)|Określa, czy `set` obiekt jest większy niż lub równy innemu `set` obiektu.|

## <a name="interfaces"></a>Interfejsy

|Interface|Opis|
|---------------|-----------------|
|<xref:System.ICloneable>|Duplikowanie obiektów.|
|<xref:System.Collections.IEnumerable>|Przeprowadzaj sekwencjonowanie przez elementy.|
|<xref:System.Collections.ICollection>|Obsługa grupy elementów.|
|<xref:System.Collections.Generic.IEnumerable%601>|Przeprowadzaj Sekwencjonowanie za pośrednictwem typizowanych elementów.|
|<xref:System.Collections.Generic.ICollection%601>|Obsługa grupy typizowanych elementów.|
|ITree\<klucz, wartość >|Obsługa kontenerów ogólnego.|

## <a name="remarks"></a>Uwagi

Obiekt przydziela i zwalnia pamięć dla sekwencji, który określa, jak poszczególne węzły. Wstawia elementy do drzewa (prawie) o zrównoważonym obciążeniu, który utrzymuje uporządkowanym, zmieniając linki między węzłami, nigdy, kopiując zawartość jednego węzła do innego. Oznacza to, można wstawić i usuwanie elementów za darmo, bez zakłóceń pozostałe elementy.

Obiekt porządkuje sekwencję którą kontroluje, przez wywołanie obiektu przechowywanej delegat typu [set::key_compare (STL/CLR)](../dotnet/set-key-compare-stl-clr.md). Można określić obiektu delegowanego przechowywane, podczas tworzenia zestawu; Jeśli obiekt delegowany nie zostanie określony, wartością domyślną jest porównanie `operator<(key_type, key_type)`. Ten przechowywany obiekt jest dostępu przez wywołanie funkcji elementu członkowskiego [set::key_comp (STL/CLR)](../dotnet/set-key-comp-stl-clr.md)`()`.

Obiektu delegowanego musi powodować ścisłe słabe porządkowanie na kluczach typu [set::key_type (STL/CLR)](../dotnet/set-key-type-stl-clr.md). Oznacza to, dla dowolnego dwa klucze `X` i `Y`:

`key_comp()(X, Y)` Zwraca wynik tego samego typu Boolean przy każdym wywołaniu.

Jeśli `key_comp()(X, Y)` ma wartość true, następnie `key_comp()(Y, X)` musi mieć wartość false.

Jeśli `key_comp()(X, Y)` ma wartość true, następnie `X` jest nazywany jest umieszczane przed `Y`.

Jeśli `!key_comp()(X, Y) && !key_comp()(Y, X)` ma wartość true, następnie `X` i `Y` są określane jako mają równoważną kolejność.

Dla każdego elementu `X` , który poprzedza `Y` w kontrolowanej sekwencji `key_comp()(Y, X)` ma wartość false. (Dla domyślnego obiektu delegowanego klucze nigdy nie zmniejszenie wartości.) W odróżnieniu od klasy szablonu [ustaw](../dotnet/set-stl-clr.md), obiekt klasy szablonu `set` nie wymaga ona, że klucze dla wszystkich elementów są unikatowe. (Dwa lub więcej klucze mają równoważną kolejność.)

Każdy element służy jako klucza i wartości. Sekwencja jest reprezentowana w sposób, który zezwala wyszukiwania, wstawiania i usuwania dowolnego elementu z wielu operacji proporcjonalny do logarytmu liczby elementów w sekwencji (czas logarytmicznej). Ponadto, wstawianie elementu nie unieważnia iteratorów, a usuwanie elementu unieważnia tylko te iteratory, które wskazują na usunięty element.

Obsługuje zestaw dwukierunkowe Iteratory, co oznacza, że użytkownik może przechodzić do sąsiadujących elementów podany iterator, który wskazuje element w kontrolowanej sekwencji. Specjalne węzłem odnosi się do iteratora zwrócony przez [set::end (STL/CLR)](../dotnet/set-end-stl-clr.md)`()`. Można zmniejszyć tego iteratora, aby dotrzeć do ostatniego elementu w kontrolowanej sekwencji, jeśli jest obecny. Inkrementacji iteratora zestawu, aby dotrzeć do węzła głównego, a następnie porównać równa `end()`. Ale nie można wyłuskać iteratora zwrócony przez `end()`.

Należy pamiętać, że nie można odwołać się do elementu zestawu bezpośrednio podanej pozycji liczbowych — wymagającego iteratora dostępu swobodnego.

Iterator Ustaw przechowuje dojścia do węzła skojarzony zestaw, który z kolei przechowuje dojście do jego skojarzony kontener. Iteratory można użyć tylko w nich obiekty skojarzony kontener. Iterator Ustaw zachowuje ważność tak długo, jak jego skojarzony zestaw węzła jest skojarzony z niektórych zestaw. Ponadto, prawidłowy iteratora jest wyłuskiwania — służy do uzyskiwania dostępu lub zmienić wartości elementu ustanowi — tak długo, jak nie jest równa `end()`.

Wymazywanie lub usunięcie elementu wywołuje destruktor do jego przechowywanej wartości. Niszczenie kontenera usuwa wszystkie elementy. W związku z tym kontener, którego typ elementu jest klasą ref gwarantuje, że żadne elementy on nakreślał kontenera. Należy jednak pamiętać, że kontener dojścia nie *nie* zniszczyć jego elementów.

## <a name="members"></a>Elementy członkowskie

## <a name="begin"></a>set::BEGIN (STL/CLR)

Określa początek kontrolowanej sekwencji.

### <a name="syntax"></a>Składnia

```cpp
iterator begin();
```

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca iteratora dwukierunkowego, który wyznacza pierwszego elementu w kontrolowanej sekwencji lub tuż za koniec pustą sekwencją. Służy do uzyskiwania iterator, który wyznacza `current` początek kontrolowanej sekwencji, ale jej stan można zmienić, jeśli zmieni się długość kontrolowanej sekwencji.

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

## <a name="clear"></a>set::Clear (STL/CLR)

Usuwa wszystkie elementy.

### <a name="syntax"></a>Składnia

```cpp
void clear();
```

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego skutecznie wywołuje [set::erase (STL/CLR)](../dotnet/set-erase-stl-clr.md) `(` [set::begin (STL/CLR)](../dotnet/set-begin-stl-clr.md) `(),` [set::end (STL/CLR)](../dotnet/set-end-stl-clr.md) `())`. Umożliwia ona upewnij się, że kontrolowanej sekwencji jest pusty.

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

## <a name="const_iterator"></a>set::const_iterator (STL/CLR)

Typ iteratora stałego dla kontrolowanej sekwencji.

### <a name="syntax"></a>Składnia

```cpp
typedef T2 const_iterator;
```

### <a name="remarks"></a>Uwagi

Typ opisuje obiekt nieokreślonego typu `T2` który może służyć jako iterator dwukierunkowy stałe dla kontrolowanej sekwencji.

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

## <a name="const_reference"></a>set::const_reference (STL/CLR)

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

## <a name="const_reverse_iterator"></a>set::const_reverse_iterator (STL/CLR)

Typ iteratora odwrotnego stałego dla kontrolowanej sekwencji...

### <a name="syntax"></a>Składnia

```cpp
typedef T4 const_reverse_iterator;
```

### <a name="remarks"></a>Uwagi

Typ opisuje obiekt nieokreślonego typu `T4` który może służyć jako stałe odwrotnego iteratora dla kontrolowanej sekwencji.

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

## <a name="count"></a>set::Count (STL/CLR)

Wyszukuje liczbę elementów pasujących do określonego klucza.

### <a name="syntax"></a>Składnia

```cpp
size_type count(key_type key);
```

#### <a name="parameters"></a>Parametry

*Klucz*<br/>
Wartość klucza do wyszukania.

### <a name="remarks"></a>Uwagi

Element członkowski funkcji zwraca liczbę elementów w kontrolowanej sekwencji, które mają równoważną kolejność z *klucz*. Umożliwia ona określenie liczby elementów aktualnie w kontrolowanej sekwencji, które odpowiadają określonemu kluczowi.

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

## <a name="difference_type"></a>set::difference_type (STL/CLR)

Typy odległości ze znakiem między dwoma elementami.

### <a name="syntax"></a>Składnia

```cpp
typedef int difference_type;
```

### <a name="remarks"></a>Uwagi

Typ opisuje liczba element prawdopodobnie ujemna.

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

## <a name="empty"></a>set::EMPTY (STL/CLR)

Sprawdza, czy nie ma żadnych elementów.

### <a name="syntax"></a>Składnia

```cpp
bool empty();
```

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca wartość true dla pustą kontrolowaną sekwencję. Jest to równoważne [set::size (STL/CLR)](../dotnet/set-size-stl-clr.md)`() == 0`. Możesz użyć do sprawdzenia, czy zestaw jest pusty.

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

## <a name="end"></a>set::end (STL/CLR)

Określa koniec kontrolowanej sekwencji.

### <a name="syntax"></a>Składnia

```cpp
iterator end();
```

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca iterator dwukierunkowy, który wskazuje tuż za koniec kontrolowanej sekwencji. Służy do uzyskiwania iterator, który określa koniec kontrolowanej sekwencji; jego stan nie zmieniać, jeśli zmieni się długość kontrolowanej sekwencji.

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

## <a name="equal_range"></a>set::equal_range (STL/CLR)

Wyszukuje zakres, który odpowiada określonemu kluczowi.

### <a name="syntax"></a>Składnia

```cpp
cliext::pair<iterator, iterator> equal_range(key_type key);
```

#### <a name="parameters"></a>Parametry

*Klucz*<br/>
Wartość klucza do wyszukania.

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca parę iteratorów `cliext::pair<iterator, iterator>(` [set::lower_bound (STL/CLR)](../dotnet/set-lower-bound-stl-clr.md) `(key),` [set::upper_bound (STL/CLR)](../dotnet/set-upper-bound-stl-clr.md)`(key))`. Możesz użyć do określenia zakresu elementów aktualnie w kontrolowanej sekwencji, które odpowiadają określonemu kluczowi.

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

## <a name="erase"></a>set::ERASE (STL/CLR)

Usuwa elementy z określonych pozycji.

### <a name="syntax"></a>Składnia

```cpp
iterator erase(iterator where);
iterator erase(iterator first, iterator last);
size_type erase(key_type key)
```

#### <a name="parameters"></a>Parametry

*pierwszy*<br/>
Początek zakresu, aby wymazać.

*Klucz*<br/>
Wartość klucza do wymazania.

*ostatni*<br/>
Koniec zakresu, aby wymazać.

*gdzie*<br/>
Element, aby wymazać.

### <a name="remarks"></a>Uwagi

Pierwsza funkcja członkostwa usuwa element kontrolowanej sekwencji wskazywany przez *gdzie*i zwraca iterator opisujący pierwszy element pozostający poza elementem, który został usunięty, lub [set::end (STL/CLR) ](../dotnet/set-end-stl-clr.md) `()` jeśli taki element nie istnieje. Umożliwia ona usunąć pojedynczy element.

Funkcja drugiego członka usuwa elementy kontrolowanej sekwencji w zakresie [`first`, `last`) i zwraca iterator opisujący pierwszy element pozostający poza wszelkimi elementami usuniętymi lub `end()` jeśli taki element nie istnieje... Umożliwia ona usunąć zero lub więcej elementów sąsiadujących.

Trzecia funkcja członkowska usuwa jakiegokolwiek elementu w kontrolowanej sekwencji, których klucz ma równoważną kolejność do *klucz*i zwraca liczbę elementów usuniętych. Możesz użyć do usunięcia, a liczba wszystkich elementów, które odpowiadają określonemu kluczowi.

Każdy element wymazywania czasochłonne proporcjonalny do logarytmu liczby elementów w kontrolowanej sekwencji.

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

## <a name="find"></a>set::Find (STL/CLR)

Wyszukuje element, który odpowiada określonemu kluczowi.

### <a name="syntax"></a>Składnia

```cpp
iterator find(key_type key);
```

#### <a name="parameters"></a>Parametry

*Klucz*<br/>
Wartość klucza do wyszukania.

### <a name="remarks"></a>Uwagi

Jeśli co najmniej jednego elementu w kontrolowanej sekwencji ma równoważną kolejność z *klucz*, funkcja elementu członkowskiego zwraca iterację, wyznaczanie jednego z tych elementów; w przeciwnym razie zwraca [set::end (STL/CLR)](../dotnet/set-end-stl-clr.md)`()`. Umożliwia ona obecnie Znajdź element w kontrolowanej sekwencji, który odpowiada określonemu kluczowi.

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

## <a name="generic_container"></a>set::generic_container (STL/CLR)

Typ ogólny interfejs dla kontenera.

### <a name="syntax"></a>Składnia

```cpp
typedef Microsoft::VisualC::StlClr::
    ITree<GKey, GValue>
    generic_container;
```

### <a name="remarks"></a>Uwagi

Typ opisuje ogólny interfejs dla tej klasy szablonu w kontenerze.

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

## <a name="generic_iterator"></a> set::generic_iterator (STL/CLR)

Typ iteratora do użytku z ogólny interfejs dla kontenera.

### <a name="syntax"></a>Składnia

```cpp
typedef Microsoft::VisualC::StlClr::Generic::
    ContainerBidirectionalIterator<generic_value>
    generic_iterator;
```

### <a name="remarks"></a>Uwagi

Typ opisuje iterator ogólny, który mogą być używane z ogólny interfejs dla tej klasy szablonu w kontenerze.

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

## <a name="generic_reverse_iterator"></a> set::generic_reverse_iterator (STL/CLR)

Typ iteratora odwrotnego do użytku z ogólny interfejs dla kontenera.

### <a name="syntax"></a>Składnia

```cpp
typedef Microsoft::VisualC::StlClr::Generic::
    ReverseRandomAccessIterator<generic_value>
    generic_reverse_iterator;
```

### <a name="remarks"></a>Uwagi

Typ opisuje iterator odwrotny ogólnego, które mogą być używane z ogólny interfejs dla tej klasy kontenera szablonu.

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

## <a name="generic_value"></a> set::generic_value (STL/CLR)

Typ elementu do użycia przy użyciu interfejsu ogólnego dla kontenera.

### <a name="syntax"></a>Składnia

```cpp
typedef GValue generic_value;
```

### <a name="remarks"></a>Uwagi

Typ opisuje obiekt typu `GValue` wartość elementu przechowywane do użytku z ogólny interfejs dla tej klasy kontenera szablonu, który opisuje.

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

## <a name="insert"></a> set::INSERT (STL/CLR)

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

*pierwszy*<br/>
Początek zakresu do wstawienia.

*ostatni*<br/>
Koniec zakresu do wstawienia.

*right*<br/>
Wyliczenie do wstawienia.

*Val*<br/>
Wartość klucza do wstawienia.

*gdzie*<br/>
Miejsce w kontenerze, aby wstawić (tylko wskazówki).

### <a name="remarks"></a>Uwagi

Każda z tych funkcji elementu członkowskiego wstawia sekwencję określone przez pozostałe argumenty operacji.

Pierwsza funkcja elementu członkowskiego usiłują Wstaw element z wartością *val*i zwraca parę wartości `X`. Jeśli `X.second` ma wartość true, `X.first` wyznacza nowo wstawionego elementu; w przeciwnym razie `X.first` wskazuje element ekwiwalent kolejność, która już istnieje i nie nowy element zostanie wstawiony. Umożliwia ona wstawić jeden element.

Funkcja drugiego członka wstawia element z wartością *val*przy użyciu *gdzie* jako wskazówkę (Aby poprawić wydajność) i zwraca iterator, który wyznacza nowo wstawionego elementu. Umożliwia ona Wstaw pojedynczy element, który może być w przylegającymi do elementu, które znasz.

Trzecia funkcja członkowska wstawia sekwencję [`first`, `last`). Umożliwia ona Wstawianie zero lub więcej elementów, skopiowane z innej sekwencji.

Czwarty funkcja elementu członkowskiego wstawia sekwencję wyznaczonym przez *prawo*. Umożliwia ona Wstaw sekwencję opisanego przez moduł wyliczający.

Każdy element wstawiania czasochłonne proporcjonalny do logarytmu liczby elementów w kontrolowanej sekwencji. Wstawiania może wystąpić w amortyzowanym stałym czasie, jednak podane wskazówkę, opisująca element przylegające do punktu wstawiania.

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

## <a name="iterator"></a> set::iterator (STL/CLR)

Typ iteratora dla kontrolowanej sekwencji.

### <a name="syntax"></a>Składnia

```cpp
typedef T1 iterator;
```

### <a name="remarks"></a>Uwagi

Typ opisuje obiekt nieokreślonego typu `T1` który może służyć jako iterator dwukierunkowy dla kontrolowanej sekwencji.

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

## <a name="key_comp"></a> set::key_comp (STL/CLR)

Kopiuje szeregowania delegata dwa klucze.

### <a name="syntax"></a>Składnia

```cpp
key_compare^key_comp();
```

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca szeregowania obiektu delegowanego porządkowania kontrolowanej sekwencji. Umożliwia ona porównać dwa klucze.

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

## <a name="key_compare"></a> set::key_compare (STL/CLR)

Szeregowania delegat dla obiektu dwa klucze.

### <a name="syntax"></a>Składnia

```cpp
Microsoft::VisualC::StlClr::BinaryDelegate<GKey, GKey, bool>
    key_compare;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla delegata, która określa kolejność argumentów klucza.

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

## <a name="key_type"></a> set::key_type (STL/CLR)

Typ klucza sortowania.

### <a name="syntax"></a>Składnia

```cpp
typedef Key key_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla parametru szablonu *klucz*.

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

## <a name="lower_bound"></a> set::lower_bound (STL/CLR)

Znajduje początek zakresu, który odpowiada określonemu kluczowi.

### <a name="syntax"></a>Składnia

```cpp
iterator lower_bound(key_type key);
```

#### <a name="parameters"></a>Parametry

*Klucz*<br/>
Wartość klucza do wyszukania.

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego Określa pierwszy element `X` w kontrolowanej sekwencji, która ma równoważną kolejność, tak aby *klucz*. Jeśli taki element nie istnieje, zwraca [set::end (STL/CLR)](../dotnet/set-end-stl-clr.md)`()`; w przeciwnym razie zwraca iterator, który wyznacza `X`. Umożliwia ona obecnie zlokalizuj na początku sekwencji elementów w kontrolowanej sekwencji, które odpowiadają określonemu kluczowi.

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

## <a name="make_value"></a> set::make_value (STL/CLR)

Tworzy obiekt wartości.

### <a name="syntax"></a>Składnia

```cpp
static value_type make_value(key_type key);
```

#### <a name="parameters"></a>Parametry

*Klucz*<br/>
Wartość klucza do użycia.

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca `value_type` obiektu, którego klucz jest *klucz*. Możesz użyć do redagowania odpowiedni do użytku z wielu innych funkcji Członkowskich obiektu.

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

## <a name="op_as"></a> set::operator = (STL/CLR)

Zastępuje kontrolowanej sekwencji.

### <a name="syntax"></a>Składnia

```cpp
set<Key>% operator=(set<Key>% right);
```

#### <a name="parameters"></a>Parametry

*right*<br/>
Kontener do skopiowania.

### <a name="remarks"></a>Uwagi

Kopiuje operator składowej *prawo* do obiektu, następnie zwraca `*this`. Umożliwia ona Zastąp kopię kontrolowanej sekwencji w kontrolowanej sekwencji *prawo*.

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

## <a name="rbegin"></a> set::rbegin (STL/CLR)

Określa początek kontrolowanej sekwencji odwróconej.

### <a name="syntax"></a>Składnia

```cpp
reverse_iterator rbegin();
```

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca odwrotnego iteratora, który wyznacza wartość ostatniego elementu w kontrolowanej sekwencji lub tuż za koniec pustą sekwencją. Dzięki temu wyznacza `beginning` odwrotnej kolejności. Służy do uzyskiwania iterator, który wyznacza `current` początek kontrolowanej sekwencji występuje w odwrotnej kolejności, ale jej stan można zmienić, jeśli zmieni się długość kontrolowanej sekwencji.

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

## <a name="reference"></a> set::Reference (STL/CLR)

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

## <a name="rend"></a> set::rend (STL/CLR)

Określa koniec kontrolowanej sekwencji odwróconej.

### <a name="syntax"></a>Składnia

```cpp
reverse_iterator rend();
```

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca odwrotnego iteratora, który wskazuje tuż za początek kontrolowanej sekwencji. Dzięki temu wyznacza `end` odwrotnej kolejności. Służy do uzyskiwania iterator, który wyznacza `current` koniec kontrolowanej sekwencji występuje w odwrotnej kolejności, ale jej stan można zmienić, jeśli zmieni się długość kontrolowanej sekwencji.

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

## <a name="reverse_iterator"></a> set::reverse_iterator (STL/CLR)

Typ iteratora odwrotnego dla kontrolowanej sekwencji.

### <a name="syntax"></a>Składnia

```cpp
typedef T3 reverse_iterator;
```

### <a name="remarks"></a>Uwagi

Typ opisuje obiekt nieokreślonego typu `T3` który może służyć jako odwrotnego iteratora dla kontrolowanej sekwencji.

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

## <a name="set"></a> set::set (STL/CLR)

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

*pierwszy*<br/>
Początek zakresu do wstawienia.

*ostatni*<br/>
Koniec zakresu do wstawienia.

*P.*<br/>
Kolejność predykat dla kontrolowanej sekwencji.

*right*<br/>
Obiekt lub zakresu do wstawienia.

### <a name="remarks"></a>Uwagi

Konstruktor:

`set();`

Inicjuje kontrolowanej sekwencji bez elementów z domyślną kolejność predykatu `key_compare()`. Umożliwia ona określenie początkowej pustą kontrolowaną sekwencję, przy użyciu domyślnego porządkowanie predykat.

Konstruktor:

`explicit set(key_compare^ pred);`

Inicjuje kontrolowanej sekwencji bez elementów, z predykatem szeregowania *pred*. Umożliwia ona określenie początkowej pustą kontrolowaną sekwencję, z określonym predykatem szeregowania.

Konstruktor:

`set(set<Key>% right);`

Inicjuje kontrolowanej sekwencji za pomocą sekwencji [`right.begin()`, `right.end()`), przy użyciu domyślnego porządkowanie predykat. Umożliwia ona określenie początkowej kontrolowanej sekwencji, który jest kopią na sekwencję kontrolowaną przez obiekt zestawu *prawo*, przy użyciu domyślnego porządkowanie predykat.

Konstruktor:

`set(set<Key>^ right);`

Inicjuje kontrolowanej sekwencji za pomocą sekwencji [`right->begin()`, `right->end()`), przy użyciu domyślnego porządkowanie predykat. Umożliwia ona określenie początkowej kontrolowanej sekwencji, który jest kopią na sekwencję kontrolowaną przez obiekt zestawu *prawo*, przy użyciu domyślnego porządkowanie predykat.

Konstruktor:

`template<typename InIter> set(InIter first, InIter last);`

Inicjuje kontrolowanej sekwencji za pomocą sekwencji [`first`, `last`), przy użyciu domyślnego porządkowanie predykat. Umożliwia ona Utwórz kopię innej sekwencji kontrolowanej sekwencji z domyślną kolejność predykat.

Konstruktor:

`template<typename InIter> set(InIter first, InIter last, key_compare^ pred);`

Inicjuje kontrolowanej sekwencji za pomocą sekwencji [`first`, `last`), z predykatem szeregowania *pred*. Umożliwia ona utworzyć kopię sekwencji inny określony predykat szeregowania kontrolowanej sekwencji.

Konstruktor:

`set(System::Collections::Generic::IEnumerable<Key>^ right);`

Inicjuje kontrolowanej sekwencji za pomocą sekwencji wyznaczonym przez moduł wyliczający *prawo*, przy użyciu domyślnego porządkowanie predykat. Umożliwia ona Utwórz kopię innej sekwencji opisanego przez moduł wyliczający z domyślną kolejność predykat w kontrolowanej sekwencji.

Konstruktor:

`set(System::Collections::Generic::IEnumerable<Key>^ right, key_compare^ pred);`

Inicjuje kontrolowanej sekwencji za pomocą sekwencji wyznaczonym przez moduł wyliczający *prawo*, z predykatem szeregowania *pred*. Umożliwia ona utworzyć kopię sekwencji innego opisanego przez moduł wyliczający, z określonym predykatem szeregowania kontrolowanej sekwencji.

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

## <a name="size"></a> set::size (STL/CLR)

Liczy liczbę elementów.

### <a name="syntax"></a>Składnia

```cpp
size_type size();
```

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca długość kontrolowanej sekwencji. Umożliwia ona określenie liczby elementów aktualnie w kontrolowanej sekwencji. Jeśli jest wszystkich interesujących Cię, czy sekwencja ma wartość różną od zera rozmiaru, zobacz [set::empty (STL/CLR)](../dotnet/set-empty-stl-clr.md)`()`.

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

## <a name="size_type"></a> set::size_type (STL/CLR)

Typ odległości ze znakiem między dwoma elementu.

### <a name="syntax"></a>Składnia

```cpp
typedef int size_type;
```

### <a name="remarks"></a>Uwagi

Typ opisuje liczby nieujemnej wartości elementu.

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

## <a name="swap"></a> set::swap (STL/CLR)

Zamienia zawartości dwóch kontenerów.

### <a name="syntax"></a>Składnia

```cpp
void swap(set<Key>% right);
```

#### <a name="parameters"></a>Parametry

*right*<br/>
Kontener do wymiany zawartości z.

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zamienia kontrolowanej sekwencji między `this` i *prawo*. Robi to w stałym czasie i w wyniku weryfikacji zgłasza wyjątek bez wyjątków. Możesz użyć go w prosty sposób do wymiany zawartości dwóch kontenerów.

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

## <a name="to_array"></a> set::to_array (STL/CLR)

Kopiuje kontrolowanej sekwencji do nowej tablicy.

### <a name="syntax"></a>Składnia

```cpp
cli::array<value_type>^ to_array();
```

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca tablicę zawierającą kontrolowanej sekwencji. Umożliwia ona otrzymać kopię kontrolowanej sekwencji w postaci tablicy.

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

## <a name="upper_bound"></a> set::upper_bound (STL/CLR)

Znajduje koniec zakresu, który odpowiada określonemu kluczowi.

### <a name="syntax"></a>Składnia

```cpp
iterator upper_bound(key_type key);
```

#### <a name="parameters"></a>Parametry

*Klucz*<br/>
Wartość klucza do wyszukania.

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego określa po ostatnim elemencie `X` w kontrolowanej sekwencji, która ma równoważną kolejność, tak aby *klucz*. Jeśli taki element nie istnieje lub `X` jest ostatnim elementem w kontrolowanej sekwencji, funkcja zwraca [set::end (STL/CLR)](../dotnet/set-end-stl-clr.md)`()`; w przeciwnym razie zwraca iterator, który wyznacza pierwszego elementu poza `X`. Umożliwia ona obecnie Znajdź koniec sekwencji elementów w kontrolowanej sekwencji, które odpowiadają określonemu kluczowi.

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

## <a name="value_comp"></a> set::value_comp (STL/CLR)

Kopiuje szeregowania delegata dwie wartości elementów.

### <a name="syntax"></a>Składnia

```cpp
value_compare^ value_comp();
```

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca szeregowania obiektu delegowanego porządkowania kontrolowanej sekwencji. Umożliwia ona porównać dwie wartości elementów.

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

## <a name="value_compare"></a> set::value_compare (STL/CLR)

Szeregowania delegat dla obiektu dwie wartości elementów.

### <a name="syntax"></a>Składnia

```cpp
Microsoft::VisualC::StlClr::BinaryDelegate<generic_value, generic_value, bool>
    value_compare;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla delegata, który określa kolejność wartości argumentów.

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

## <a name="value_type"></a> set::value_type (STL/CLR)

Typ elementu.

### <a name="syntax"></a>Składnia

```cpp
typedef generic_value value_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla `generic_value`.

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

## <a name="op_neq"></a> Operator! = (set) (STL/CLR)

Lista nie jest równe porównania.

### <a name="syntax"></a>Składnia

```cpp
template<typename Key>
    bool operator!=(set<Key>% left,
        set<Key>% right);
```

#### <a name="parameters"></a>Parametry

*left*<br/>
Po lewej stronie kontenera do porównania.

*right*<br/>
Kontener prawo do porównania.

### <a name="remarks"></a>Uwagi

Funkcja operator zwraca `!(left == right)`. Można go używać do testowania czy *po lewej stronie* nie jest taka sama jak określona *prawo* kiedy dwa zestawy są w porównaniu element po elemencie.

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

## <a name="op_lt"></a> operator&lt; (set) (STL/CLR)

Lista mniejsza niż porównania.

### <a name="syntax"></a>Składnia

```cpp
template<typename Key>
    bool operator<(set<Key>% left,
        set<Key>% right);
```

#### <a name="parameters"></a>Parametry

*left*<br/>
Po lewej stronie kontenera do porównania.

*right*<br/>
Kontener prawo do porównania.

### <a name="remarks"></a>Uwagi

Operator funkcja zwraca wartość true, jeśli, na najniższą pozycję `i` dla którego `!(right[i] < left[i])` jest również wartość true, który `left[i] < right[i]`. W przeciwnym razie zwraca `left->size() < right->size()` używanej do testowania czy *po lewej stronie* był zamówiony przed *prawo* kiedy dwa zestawy są w porównaniu element po elemencie.

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

## <a name="op_lteq"></a> operator&lt;= (set) (STL/CLR)

Mniejsze niż lub równe listy porównania.

### <a name="syntax"></a>Składnia

```cpp
template<typename Key>
    bool operator<=(set<Key>% left,
        set<Key>% right);
```

#### <a name="parameters"></a>Parametry

*left*<br/>
Po lewej stronie kontenera do porównania.

*right*<br/>
Kontener prawo do porównania.

### <a name="remarks"></a>Uwagi

Funkcja operator zwraca `!(right < left)`. Można go używać do testowania czy *po lewej stronie* nie są porządkowane po *prawo* kiedy dwa zestawy są w porównaniu element po elemencie.

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

## <a name="op_eq"></a> Operator == (set) (STL/CLR)

Porównanie równego listy.

### <a name="syntax"></a>Składnia

```cpp
template<typename Key>
    bool operator==(set<Key>% left,
        set<Key>% right);
```

#### <a name="parameters"></a>Parametry

*left*<br/>
Po lewej stronie kontenera do porównania.

*right*<br/>
Kontener prawo do porównania.

### <a name="remarks"></a>Uwagi

Funkcja operator zwraca wartość true, tylko wtedy, gdy sekwencje kontrolowane przez *po lewej stronie* i *prawo* tę samą długość, a dla każdej pozycji `i`, `left[i] ==` `right[i]`. Można go używać do testowania czy *po lewej stronie* jest taka sama jak określona *prawo* kiedy dwa zestawy są w porównaniu element po elemencie.

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

## <a name="op_gt"></a> operator&gt; (set) (STL/CLR)

Lista jest większa niż porównania.

### <a name="syntax"></a>Składnia

```cpp
template<typename Key>
    bool operator>(set<Key>% left,
        set<Key>% right);
```

#### <a name="parameters"></a>Parametry

*left*<br/>
Po lewej stronie kontenera do porównania.

*right*<br/>
Kontener prawo do porównania.

### <a name="remarks"></a>Uwagi

Funkcja operator zwraca `right` `<` `left`. Można go używać do testowania czy *po lewej stronie* są porządkowane po *prawo* kiedy dwa zestawy są w porównaniu element po elemencie.

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

## <a name="op_gteq"></a> operator&gt;= (set) (STL/CLR)

Lista większa niż lub równe porównania.

### <a name="syntax"></a>Składnia

```cpp
template<typename Key>
    bool operator>=(set<Key>% left,
        set<Key>% right);
```

#### <a name="parameters"></a>Parametry

*left*<br/>
Po lewej stronie kontenera do porównania.

*right*<br/>
Kontener prawo do porównania.

### <a name="remarks"></a>Uwagi

Funkcja operator zwraca `!(left < right)`. Można go używać do testowania czy *po lewej stronie* nie był zamówiony przed *prawo* kiedy dwa zestawy są w porównaniu element po elemencie.

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