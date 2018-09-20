---
title: multiset (STL/CLR) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: d3d0fce8629a96ec7b83df4e4a244d1012743eeb
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46376691"
---
# <a name="multiset-stlclr"></a>multiset (STL/CLR)

Klasa szablonu opisuje obiekt, który kontroluje różnej długości sekwencje elementów mającego dostęp dwukierunkowy. Korzystasz z kontenera `multiset` Zarządzanie sekwencji elementów jako drzewo uporządkowane (prawie) o zrównoważonym obciążeniu węzłów, w każdym przechowywania jeden element.

W poniższym opisie `GValue` jest taka sama jak `GKey`, który z kolei jest taka sama jak *klucz* o ile nie jest typem odwołania, w którym to przypadku jest `Key^`.

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

*Key*<br/>
Typ kluczowy składnik elementu w kontrolowanej sekwencji.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<cliext — / set >

**Namespace:** cliext —

## <a name="declarations"></a>Deklaracje

|Definicja typu|Opis|
|---------------------|-----------------|
|[multiset::const_iterator (STL/CLR)](#const_iterator)|Typ iteratora stałego dla kontrolowanej sekwencji.|
|[multiset::const_reference (STL/CLR)](#const_reference)|Typ stałego odwołania do elementu.|
|[multiset::const_reverse_iterator (STL/CLR)](#const_reverse_iterator)|Typ iteratora odwrotnego stałego dla kontrolowanej sekwencji.|
|[multiset::difference_type (STL/CLR)](#difference_type)|Typ (prawdopodobnie odległości ze znakiem) między dwoma elementami.|
|[multiset::generic_container (STL/CLR)](#generic_container)|Typ ogólny interfejs dla kontenera.|
|[multiset::generic_iterator (STL/CLR)](#generic_iterator)|Typ iteratora dla ogólny interfejs dla kontenera.|
|[multiset::generic_reverse_iterator (STL/CLR)](#generic_reverse_iterator)|Typ iteratora odwrotnego dla ogólny interfejs dla kontenera.|
|[multiset::generic_value (STL/CLR)](#generic_value)|Typ elementu dla ogólny interfejs dla kontenera.|
|[multiset::iterator (STL/CLR)](#iterator)|Typ iteratora dla kontrolowanej sekwencji.|
|[multiset::key_compare (STL/CLR)](#key_compare)|Szeregowania delegat dla obiektu dwa klucze.|
|[multiset::key_type (STL/CLR)](#key_type)|Typ klucza sortowania.|
|[multiset::reference (STL/CLR)](#reference)|Typ odwołania do elementu.|
|[multiset::reverse_iterator (STL/CLR)](#reverse_iterator)|Typ iteratora odwrotnego dla kontrolowanej sekwencji.|
|[multiset::size_type (STL/CLR)](#size_type)|Typ odległości (wartość nieujemną) między dwoma elementami.|
|[multiset::value_compare (STL/CLR)](#value_compare)|Szeregowania delegat dla obiektu dwie wartości elementów.|
|[multiset::value_type (STL/CLR)](#value_type)|Typ elementu.|

|Funkcja elementów członkowskich|Opis|
|---------------------|-----------------|
|[multiset::begin (STL/CLR)](#begin)|Określa początek kontrolowanej sekwencji.|
|[multiset::clear (STL/CLR)](#clear)|Usuwa wszystkie elementy.|
|[multiset::count (STL/CLR)](#count)|Liczba elementów pasujących do określonego klucza.|
|[multiset::empty (STL/CLR)](#empty)|Sprawdza, czy nie ma żadnych elementów.|
|[multiset::end (STL/CLR)](#end)|Określa koniec kontrolowanej sekwencji.|
|[multiset::equal_range (STL/CLR)](#equal_range)|Wyszukuje zakres, który odpowiada określonemu kluczowi.|
|[multiset::erase (STL/CLR)](#erase)|Usuwa elementy z określonych pozycji.|
|[multiset::find (STL/CLR)](#find)|Wyszukuje element, który odpowiada określonemu kluczowi.|
|[multiset::insert (STL/CLR)](#insert)|Dodaje elementy.|
|[multiset::key_comp (STL/CLR)](#key_comp)|Kopiuje szeregowania delegata dwa klucze.|
|[multiset::lower_bound (STL/CLR)](#lower_bound)|Znajduje początek zakresu, który odpowiada określonemu kluczowi.|
|[multiset::make_value (STL/CLR)](#make_value)|Tworzy obiekt wartości.|
|[multiset::multiset (STL/CLR)](#multiset)|Konstruuje obiekt kontenera.|
|[multiset::rbegin (STL/CLR)](#rbegin)|Określa początek kontrolowanej sekwencji odwróconej.|
|[multiset::rend (STL/CLR)](#rend)|Określa koniec kontrolowanej sekwencji odwróconej.|
|[multiset::size (STL/CLR)](#size)|Liczy liczbę elementów.|
|[multiset::swap (STL/CLR)](#swap)|Zamienia zawartości dwóch kontenerów.|
|[multiset::to_array (STL/CLR)](#to_array)|Kopiuje kontrolowanej sekwencji do nowej tablicy.|
|[multiset::upper_bound (STL/CLR)](#upper_bound)|Znajduje koniec zakresu, który odpowiada określonemu kluczowi.|
|[multiset::value_comp (STL/CLR)](#value_comp)|Kopiuje szeregowania delegata dwie wartości elementów.|

|Operator|Opis|
|--------------|-----------------|
|[multiset::operator= (STL/CLR)](#op_as)|Zastępuje kontrolowanej sekwencji.|
|[operator!= (multiset) (STL/CLR)](#op_neq)|Określa, czy `multiset` obiekt nie jest równy innemu `multiset` obiektu.|
|[operator< (multiset) (STL/CLR)](#op_lt)|Określa, czy `multiset` obiekt jest mniejszy niż inny `multiset` obiektu.|
|[operator<= (multiset) (STL/CLR)](#op_lteq)|Określa, czy `multiset` obiekt jest mniejszy niż lub równy innemu `multiset` obiektu.|
|[operator== (multiset) (STL/CLR)](#op_eq)|Określa, czy `multiset` obiekt jest równy innemu `multiset` obiektu.|
|[operator> (multiset) (STL/CLR)](#op_gt)|Określa, czy `multiset` obiekt jest większy niż inny `multiset` obiektu.|
|[operator>= (multiset) (STL/CLR)](#op_gteq)|Określa, czy `multiset` obiekt jest większy niż lub równy innemu `multiset` obiektu.|

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

Obiekt porządkuje sekwencję którą kontroluje, przez wywołanie obiektu przechowywanej delegat typu [multiset::key_compare (STL/CLR)](../dotnet/multiset-key-compare-stl-clr.md). Można określić obiektu delegowanego przechowywanych podczas konstruowania multiset; Jeśli obiekt delegowany nie zostanie określony, wartością domyślną jest porównanie `operator<(key_type, key_type)`. Ten przechowywany obiekt jest dostępu przez wywołanie funkcji elementu członkowskiego [multiset::key_comp (STL/CLR)](../dotnet/multiset-key-comp-stl-clr.md)`()`.

Obiektu delegowanego musi powodować ścisłe słabe porządkowanie na kluczach typu [multiset::key_type (STL/CLR)](../dotnet/multiset-key-type-stl-clr.md). Oznacza to, dla dowolnego dwa klucze `X` i `Y`:

`key_comp()(X, Y)` Zwraca wynik tego samego typu Boolean przy każdym wywołaniu.

Jeśli `key_comp()(X, Y)` ma wartość true, następnie `key_comp()(Y, X)` musi mieć wartość false.

Jeśli `key_comp()(X, Y)` ma wartość true, następnie `X` jest nazywany jest umieszczane przed `Y`.

Jeśli `!key_comp()(X, Y) && !key_comp()(Y, X)` ma wartość true, następnie `X` i `Y` są określane jako mają równoważną kolejność.

Dla każdego elementu `X` , który poprzedza `Y` w kontrolowanej sekwencji `key_comp()(Y, X)` ma wartość false. (Dla domyślnego obiektu delegowanego klucze nigdy nie zmniejszenie wartości.) W odróżnieniu od klasy szablonu [Ustaw (STL/CLR)](../dotnet/set-stl-clr.md), obiekt klasy szablonu `multiset` nie wymaga ona, że klucze dla wszystkich elementów są unikatowe. (Dwa lub więcej klucze mają równoważną kolejność.)

Każdy element służy jako klucza i wartości. Sekwencja jest reprezentowana w sposób, który zezwala wyszukiwania, wstawiania i usuwania dowolnego elementu z wielu operacji proporcjonalny do logarytmu liczby elementów w sekwencji (czas logarytmicznej). Ponadto, wstawianie elementu nie unieważnia iteratorów, a usuwanie elementu unieważnia tylko te iteratory, które wskazują na usunięty element.

Zestaw wielokrotny obsługują Iteratory dwukierunkowe, co oznacza, że użytkownik może przechodzić do sąsiadujących elementów podany iterator, który wskazuje element w kontrolowanej sekwencji. Specjalne węzłem odnosi się do iteratora zwrócony przez [multiset::end (STL/CLR)](../dotnet/multiset-end-stl-clr.md)`()`. Można zmniejszyć tego iteratora, aby dotrzeć do ostatniego elementu w kontrolowanej sekwencji, jeśli jest obecny. Inkrementacji zestawów wielokrotnych iteratora, aby dotrzeć do węzła głównego, a następnie porównaj równa `end()`. Ale nie można wyłuskać iteratora zwrócony przez `end()`.

Należy pamiętać, że nie można odwołać się do elementów zestawów wielokrotnych bezpośrednio podanej pozycji liczbowych — wymagającego iteratora dostępu swobodnego.

Multiset — iteratora przechowuje dojście do jego skojarzony węzeł zestaw wielokrotny, który z kolei przechowuje dojście do jego skojarzony kontener. Iteratory można użyć tylko w nich obiekty skojarzony kontener. Multiset — iteratora zachowuje ważność tak długo, jak jego skojarzony węzeł zestawów wielokrotnych jest skojarzony z niektórych multiset. Ponadto, prawidłowy iteratora jest wyłuskiwania — służy do uzyskiwania dostępu lub zmienić wartości elementu ustanowi — tak długo, jak nie jest równa `end()`.

Wymazywanie lub usunięcie elementu wywołuje destruktor do jego przechowywanej wartości. Niszczenie kontenera usuwa wszystkie elementy. W związku z tym kontener, którego typ elementu jest klasą ref gwarantuje, że żadne elementy on nakreślał kontenera. Należy jednak pamiętać, że kontener dojścia nie *nie* zniszczyć jego elementów.

## <a name="members"></a>Elementy członkowskie

## <a name="begin"></a> multiset::BEGIN (STL/CLR)

Określa początek kontrolowanej sekwencji.

### <a name="syntax"></a>Składnia

```cpp
iterator begin();
```

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca iteratora dwukierunkowego, który wyznacza pierwszego elementu w kontrolowanej sekwencji lub tuż za koniec pustą sekwencją. Służy do uzyskiwania iterator, który wyznacza `current` początek kontrolowanej sekwencji, ale jej stan można zmienić, jeśli zmieni się długość kontrolowanej sekwencji.

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

## <a name="clear"></a> multiset::Clear (STL/CLR)

Usuwa wszystkie elementy.

### <a name="syntax"></a>Składnia

```cpp
void clear();
```

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego skutecznie wywołuje [multiset::erase (STL/CLR)](../dotnet/multiset-erase-stl-clr.md) `(` [multiset::begin (STL/CLR)](../dotnet/multiset-begin-stl-clr.md) `(),` [multiset::end (STL/CLR)](../dotnet/multiset-end-stl-clr.md) `())`. Umożliwia ona upewnij się, że kontrolowanej sekwencji jest pusty.

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

## <a name="const_iterator"></a> multiset::const_iterator (STL/CLR)

Typ iteratora stałego dla kontrolowanej sekwencji.

### <a name="syntax"></a>Składnia

```cpp
typedef T2 const_iterator;
```

### <a name="remarks"></a>Uwagi

Typ opisuje obiekt nieokreślonego typu `T2` który może służyć jako iterator dwukierunkowy stałe dla kontrolowanej sekwencji.

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

## <a name="const_reference"></a> multiset::const_reference (STL/CLR)

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

## <a name="const_reverse_iterator"></a> multiset::const_reverse_iterator (STL/CLR)

Typ iteratora odwrotnego stałego dla kontrolowanej sekwencji...

### <a name="syntax"></a>Składnia

```cpp
typedef T4 const_reverse_iterator;
```

### <a name="remarks"></a>Uwagi

Typ opisuje obiekt nieokreślonego typu `T4` który może służyć jako stałe odwrotnego iteratora dla kontrolowanej sekwencji.

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

## <a name="count"></a> multiset::Count (STL/CLR)

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

## <a name="difference_type"></a> multiset::difference_type (STL/CLR)

Typy odległości ze znakiem między dwoma elementami.

### <a name="syntax"></a>Składnia

```cpp
typedef int difference_type;
```

### <a name="remarks"></a>Uwagi

Typ opisuje liczba element prawdopodobnie ujemna.

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

## <a name="empty"></a> multiset::EMPTY (STL/CLR)

Sprawdza, czy nie ma żadnych elementów.

### <a name="syntax"></a>Składnia

```cpp
bool empty();
```

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca wartość true dla pustą kontrolowaną sekwencję. Jest to równoważne [multiset::size (STL/CLR)](../dotnet/multiset-size-stl-clr.md)`() == 0`. Możesz użyć do sprawdzenia, czy zestaw wielokrotny jest pusty.

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

## <a name="end"></a> multiset::end (STL/CLR)

Określa koniec kontrolowanej sekwencji.

### <a name="syntax"></a>Składnia

```cpp
iterator end();
```

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca iterator dwukierunkowy, który wskazuje tuż za koniec kontrolowanej sekwencji. Służy do uzyskiwania iterator, który określa koniec kontrolowanej sekwencji; jego stan nie zmieniać, jeśli zmieni się długość kontrolowanej sekwencji.

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

## <a name="equal_range"></a> multiset::equal_range (STL/CLR)

Wyszukuje zakres, który odpowiada określonemu kluczowi.

### <a name="syntax"></a>Składnia

```cpp
cliext::pair<iterator, iterator> equal_range(key_type key);
```

#### <a name="parameters"></a>Parametry

*Klucz*<br/>
Wartość klucza do wyszukania.

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca parę iteratorów `cliext::pair<iterator, iterator>(` [multiset::lower_bound (STL/CLR)](../dotnet/multiset-lower-bound-stl-clr.md) `(key),` [multiset::upper_bound (STL/CLR)](../dotnet/multiset-upper-bound-stl-clr.md)`(key))`. Możesz użyć do określenia zakresu elementów aktualnie w kontrolowanej sekwencji, które odpowiadają określonemu kluczowi.

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

## <a name="erase"></a> multiset::ERASE (STL/CLR)

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

Pierwsza funkcja członkostwa usuwa element kontrolowanej sekwencji wskazywany przez *gdzie*i zwraca iterator opisujący pierwszy element pozostający poza elementem, który został usunięty, lub [multiset::end (STL / CLR)](../dotnet/multiset-end-stl-clr.md) `()` jeśli taki element nie istnieje. Umożliwia ona usunąć pojedynczy element.

Funkcja drugiego członka usuwa elementy kontrolowanej sekwencji w zakresie [`first`, `last`) i zwraca iterator opisujący pierwszy element pozostający poza wszelkimi elementami usuniętymi lub `end()` jeśli taki element nie istnieje... Umożliwia ona usunąć zero lub więcej elementów sąsiadujących.

Trzecia funkcja członkowska usuwa jakiegokolwiek elementu w kontrolowanej sekwencji, których klucz ma równoważną kolejność do *klucz*i zwraca liczbę elementów usuniętych. Możesz użyć do usunięcia, a liczba wszystkich elementów, które odpowiadają określonemu kluczowi.

Każdy element wymazywania czasochłonne proporcjonalny do logarytmu liczby elementów w kontrolowanej sekwencji.

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

## <a name="find"></a> multiset::Find (STL/CLR)

Wyszukuje element, który odpowiada określonemu kluczowi.

### <a name="syntax"></a>Składnia

```cpp
iterator find(key_type key);
```

#### <a name="parameters"></a>Parametry

*Klucz*<br/>
Wartość klucza do wyszukania.

### <a name="remarks"></a>Uwagi

Jeśli co najmniej jednego elementu w kontrolowanej sekwencji ma równoważną kolejność z *klucz*, funkcja elementu członkowskiego zwraca iterację, wyznaczanie jednego z tych elementów; w przeciwnym razie zwraca [multiset::end (STL/CLR)](../dotnet/multiset-end-stl-clr.md) `()`. Umożliwia ona obecnie Znajdź element w kontrolowanej sekwencji, który odpowiada określonemu kluczowi.

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

## <a name="generic_container"></a> multiset::generic_container (STL/CLR)

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

## <a name="generic_iterator"></a> multiset::generic_iterator (STL/CLR)

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

## <a name="generic_reverse_iterator"></a> multiset::generic_reverse_iterator (STL/CLR)

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

## <a name="generic_value"></a> multiset::generic_value (STL/CLR)

Typ elementu do użycia przy użyciu interfejsu ogólnego dla kontenera.

### <a name="syntax"></a>Składnia

```cpp
typedef GValue generic_value;
```

### <a name="remarks"></a>Uwagi

Typ opisuje obiekt typu `GValue` wartość elementu przechowywane do użytku z ogólny interfejs dla tej klasy kontenera szablonu, który opisuje.

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

## <a name="insert"></a> multiset::INSERT (STL/CLR)

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

Pierwsza funkcja elementu członkowskiego wstawia element z wartością *val*i zwraca iterator, który wyznacza nowo wstawionego elementu. Umożliwia ona wstawić jeden element.

Funkcja drugiego członka wstawia element z wartością *val*przy użyciu *gdzie* jako wskazówkę (Aby poprawić wydajność) i zwraca iterator, który wyznacza nowo wstawionego elementu. Umożliwia ona Wstaw pojedynczy element, który może być w przylegającymi do elementu, które znasz.

Trzecia funkcja członkowska wstawia sekwencję [`first`, `last`). Umożliwia ona Wstawianie zero lub więcej elementów, skopiowane z innej sekwencji.

Czwarty funkcja elementu członkowskiego wstawia sekwencję wyznaczonym przez *prawo*. Umożliwia ona Wstaw sekwencję opisanego przez moduł wyliczający.

Każdy element wstawiania czasochłonne proporcjonalny do logarytmu liczby elementów w kontrolowanej sekwencji. Wstawiania może wystąpić w amortyzowanym stałym czasie, jednak podane wskazówkę, opisująca element przylegające do punktu wstawiania.

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

## <a name="iterator"></a> multiset::iterator (STL/CLR)

Typ iteratora dla kontrolowanej sekwencji.

### <a name="syntax"></a>Składnia

```cpp
typedef T1 iterator;
```

### <a name="remarks"></a>Uwagi

Typ opisuje obiekt nieokreślonego typu `T1` który może służyć jako iterator dwukierunkowy dla kontrolowanej sekwencji.

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

## <a name="key_comp"></a> multiset::key_comp (STL/CLR)

Kopiuje szeregowania delegata dwa klucze.

### <a name="syntax"></a>Składnia

```cpp
key_compare^key_comp();
```

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca szeregowania obiektu delegowanego porządkowania kontrolowanej sekwencji. Umożliwia ona porównać dwa klucze.

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

## <a name="key_compare"></a> multiset::key_compare (STL/CLR)

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

## <a name="key_type"></a> multiset::key_type (STL/CLR)

Typ klucza sortowania.

### <a name="syntax"></a>Składnia

```cpp
typedef Key key_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla parametru szablonu *klucz*.

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

## <a name="lower_bound"></a> multiset::lower_bound (STL/CLR)

Znajduje początek zakresu, który odpowiada określonemu kluczowi.

### <a name="syntax"></a>Składnia

```cpp
iterator lower_bound(key_type key);
```

#### <a name="parameters"></a>Parametry

*Klucz*<br/>
Wartość klucza do wyszukania.

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego Określa pierwszy element `X` w kontrolowanej sekwencji, która ma równoważną kolejność, tak aby *klucz*. Jeśli taki element nie istnieje, zwraca [multiset::end (STL/CLR)](../dotnet/multiset-end-stl-clr.md)`()`; w przeciwnym razie zwraca iterator, który wyznacza `X`. Umożliwia ona obecnie zlokalizuj na początku sekwencji elementów w kontrolowanej sekwencji, które odpowiadają określonemu kluczowi.

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

## <a name="make_value"></a> multiset::make_value (STL/CLR)

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

## <a name="multiset"></a> multiset::multiset (STL/CLR)

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

`multiset();`

Inicjuje kontrolowanej sekwencji bez elementów z domyślną kolejność predykatu `key_compare()`. Umożliwia ona określenie początkowej pustą kontrolowaną sekwencję, przy użyciu domyślnego porządkowanie predykat.

Konstruktor:

`explicit multiset(key_compare^ pred);`

Inicjuje kontrolowanej sekwencji bez elementów, z predykatem szeregowania *pred*. Umożliwia ona określenie początkowej pustą kontrolowaną sekwencję, z określonym predykatem szeregowania.

Konstruktor:

`multiset(multiset<Key>% right);`

Inicjuje kontrolowanej sekwencji za pomocą sekwencji [`right.begin()`, `right.end()`), przy użyciu domyślnego porządkowanie predykat. Umożliwia ona określenie początkowej kontrolowanej sekwencji, który jest kopią na sekwencję kontrolowaną przez obiekt multiset — *prawo*, przy użyciu domyślnego porządkowanie predykat.

Konstruktor:

`multiset(multiset<Key>^ right);`

Inicjuje kontrolowanej sekwencji za pomocą sekwencji [`right->begin()`, `right->end()`), przy użyciu domyślnego porządkowanie predykat. Umożliwia ona określenie początkowej kontrolowanej sekwencji, który jest kopią na sekwencję kontrolowaną przez obiekt multiset — *prawo*, przy użyciu domyślnego porządkowanie predykat.

Konstruktor:

`template<typename InIter> multiset(InIter first, InIter last);`

Inicjuje kontrolowanej sekwencji za pomocą sekwencji [`first`, `last`), przy użyciu domyślnego porządkowanie predykat. Umożliwia ona Utwórz kopię innej sekwencji kontrolowanej sekwencji z domyślną kolejność predykat.

Konstruktor:

`template<typename InIter> multiset(InIter first, InIter last, key_compare^ pred);`

Inicjuje kontrolowanej sekwencji za pomocą sekwencji [`first`, `last`), z predykatem szeregowania *pred*. Umożliwia ona utworzyć kopię sekwencji inny określony predykat szeregowania kontrolowanej sekwencji.

Konstruktor:

`multiset(System::Collections::Generic::IEnumerable<Key>^ right);`

Inicjuje kontrolowanej sekwencji za pomocą sekwencji wyznaczonym przez moduł wyliczający *prawo*, przy użyciu domyślnego porządkowanie predykat. Umożliwia ona Utwórz kopię innej sekwencji opisanego przez moduł wyliczający z domyślną kolejność predykat w kontrolowanej sekwencji.

Konstruktor:

`multiset(System::Collections::Generic::IEnumerable<Key>^ right, key_compare^ pred);`

Inicjuje kontrolowanej sekwencji za pomocą sekwencji wyznaczonym przez moduł wyliczający *prawo*, z predykatem szeregowania *pred*. Umożliwia ona utworzyć kopię sekwencji innego opisanego przez moduł wyliczający, z określonym predykatem szeregowania kontrolowanej sekwencji.

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

## <a name="op_as"></a> multiset::operator = (STL/CLR)

Zastępuje kontrolowanej sekwencji.

### <a name="syntax"></a>Składnia

```cpp
multiset<Key>% operator=(multiset<Key>% right);
```

#### <a name="parameters"></a>Parametry

*right*<br/>
Kontener do skopiowania.

### <a name="remarks"></a>Uwagi

Kopiuje operator składowej *prawo* do obiektu, następnie zwraca `*this`. Umożliwia ona Zastąp kopię kontrolowanej sekwencji w kontrolowanej sekwencji *prawo*.

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

## <a name="rbegin"></a> multiset::rbegin (STL/CLR)

Określa początek kontrolowanej sekwencji odwróconej.

### <a name="syntax"></a>Składnia

```cpp
reverse_iterator rbegin();
```

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca odwrotnego iteratora, który wyznacza wartość ostatniego elementu w kontrolowanej sekwencji lub tuż za koniec pustą sekwencją. Dzięki temu wyznacza `beginning` odwrotnej kolejności. Służy do uzyskiwania iterator, który wyznacza `current` początek kontrolowanej sekwencji występuje w odwrotnej kolejności, ale jej stan można zmienić, jeśli zmieni się długość kontrolowanej sekwencji.

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

## <a name="reference"></a> multiset::Reference (STL/CLR)

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

## <a name="rend"></a> multiset::rend (STL/CLR)

Określa koniec kontrolowanej sekwencji odwróconej.

### <a name="syntax"></a>Składnia

```cpp
reverse_iterator rend();
```

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca odwrotnego iteratora, który wskazuje tuż za początek kontrolowanej sekwencji. Dzięki temu wyznacza `end` odwrotnej kolejności. Służy do uzyskiwania iterator, który wyznacza `current` koniec kontrolowanej sekwencji występuje w odwrotnej kolejności, ale jej stan można zmienić, jeśli zmieni się długość kontrolowanej sekwencji.

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

## <a name="reverse_iterator"></a> multiset::reverse_iterator (STL/CLR)

Typ iteratora odwrotnego dla kontrolowanej sekwencji.

### <a name="syntax"></a>Składnia

```cpp
typedef T3 reverse_iterator;
```

### <a name="remarks"></a>Uwagi

Typ opisuje obiekt nieokreślonego typu `T3` który może służyć jako odwrotnego iteratora dla kontrolowanej sekwencji.

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

## <a name="size"></a> multiset::size (STL/CLR)

Liczy liczbę elementów.

### <a name="syntax"></a>Składnia

```cpp
size_type size();
```

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca długość kontrolowanej sekwencji. Umożliwia ona określenie liczby elementów aktualnie w kontrolowanej sekwencji. Jeśli jest wszystkich interesujących Cię, czy sekwencja ma wartość różną od zera rozmiaru, zobacz [multiset::empty (STL/CLR)](../dotnet/multiset-empty-stl-clr.md)`()`.

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

## <a name="size_type"></a> multiset::size_type (STL/CLR)

Typ odległości ze znakiem między dwoma elementu.

### <a name="syntax"></a>Składnia

```cpp
typedef int size_type;
```

### <a name="remarks"></a>Uwagi

Typ opisuje liczby nieujemnej wartości elementu.

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

## <a name="swap"></a> multiset::swap (STL/CLR)

Zamienia zawartości dwóch kontenerów.

### <a name="syntax"></a>Składnia

```cpp
void swap(multiset<Key>% right);
```

#### <a name="parameters"></a>Parametry

*right*<br/>
Kontener do wymiany zawartości z.

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zamienia kontrolowanej sekwencji między `this` i *prawo*. Robi to w stałym czasie i w wyniku weryfikacji zgłasza wyjątek bez wyjątków. Możesz użyć go w prosty sposób do wymiany zawartości dwóch kontenerów.

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

## <a name="to_array"></a> multiset::to_array (STL/CLR)

Kopiuje kontrolowanej sekwencji do nowej tablicy.

### <a name="syntax"></a>Składnia

```cpp
cli::array<value_type>^ to_array();
```

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca tablicę zawierającą kontrolowanej sekwencji. Umożliwia ona otrzymać kopię kontrolowanej sekwencji w postaci tablicy.

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

## <a name="upper_bound"></a> multiset::upper_bound (STL/CLR)

Znajduje koniec zakresu, który odpowiada określonemu kluczowi.

### <a name="syntax"></a>Składnia

```cpp
iterator upper_bound(key_type key);
```

#### <a name="parameters"></a>Parametry

*Klucz*<br/>
Wartość klucza do wyszukania.

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego określa po ostatnim elemencie `X` w kontrolowanej sekwencji, która ma równoważną kolejność, tak aby *klucz*. Jeśli taki element nie istnieje lub `X` jest ostatnim elementem w kontrolowanej sekwencji, funkcja zwraca [multiset::end (STL/CLR)](../dotnet/multiset-end-stl-clr.md)`()`; w przeciwnym razie zwraca iterator, który wyznacza pierwszego elementu poza `X`. Umożliwia ona obecnie Znajdź koniec sekwencji elementów w kontrolowanej sekwencji, które odpowiadają określonemu kluczowi.

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

## <a name="value_comp"></a> multiset::value_comp (STL/CLR)

Kopiuje szeregowania delegata dwie wartości elementów.

### <a name="syntax"></a>Składnia

```cpp
value_compare^ value_comp();
```

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca szeregowania obiektu delegowanego porządkowania kontrolowanej sekwencji. Umożliwia ona porównać dwie wartości elementów.

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

## <a name="value_compare"></a> multiset::value_compare (STL/CLR)

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

## <a name="value_type"></a> multiset::value_type (STL/CLR)

Typ elementu.

### <a name="syntax"></a>Składnia

```cpp
typedef generic_value value_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla `generic_value`.

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

## <a name="op_neq"></a> Operator! = (multiset) (STL/CLR)

Lista nie jest równe porównania.

### <a name="syntax"></a>Składnia

```cpp
template<typename Key>
    bool operator!=(multiset<Key>% left,
        multiset<Key>% right);
```

#### <a name="parameters"></a>Parametry

*left*<br/>
Po lewej stronie kontenera do porównania.

*right*<br/>
Kontener prawo do porównania.

### <a name="remarks"></a>Uwagi

Funkcja operator zwraca `!(left == right)`. Używanej do testowania czy *po lewej stronie* nie jest taka sama jak określona *prawo* po dwóch multisets są w porównaniu element po elemencie.

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

## <a name="op_lt"></a> operator&lt; (multiset) (STL/CLR)

Lista mniejsza niż porównania.

### <a name="syntax"></a>Składnia

```cpp
template<typename Key>
    bool operator<(multiset<Key>% left,
        multiset<Key>% right);
```

#### <a name="parameters"></a>Parametry

*left*<br/>
Po lewej stronie kontenera do porównania.

*right*<br/>
Kontener prawo do porównania.

### <a name="remarks"></a>Uwagi

Operator funkcja zwraca wartość true, jeśli, na najniższą pozycję `i` dla którego `!(right[i] < left[i])` jest również wartość true, który `left[i] < right[i]`. W przeciwnym razie zwraca `left->size() < right->size()` używanej do testowania czy *po lewej stronie* był zamówiony przed *prawo* po dwóch multisets są w porównaniu element po elemencie.

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

## <a name="op_lteq"></a> operator&lt;= (multiset) (STL/CLR)

Mniejsze niż lub równe listy porównania.

### <a name="syntax"></a>Składnia

```cpp
template<typename Key>
    bool operator<=(multiset<Key>% left,
        multiset<Key>% right);
```

#### <a name="parameters"></a>Parametry

*left*<br/>
Po lewej stronie kontenera do porównania.

*right*<br/>
Kontener prawo do porównania.

### <a name="remarks"></a>Uwagi

Funkcja operator zwraca `!(right < left)`. Używanej do testowania czy *po lewej stronie* nie są porządkowane po *prawo* po dwóch multisets są w porównaniu element po elemencie.

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

## <a name="op_eq"></a> Operator == (multiset) (STL/CLR)

Porównanie równego listy.

### <a name="syntax"></a>Składnia

```cpp
template<typename Key>
    bool operator==(multiset<Key>% left,
        multiset<Key>% right);
```

#### <a name="parameters"></a>Parametry

*left*<br/>
Po lewej stronie kontenera do porównania.

*right*<br/>
Kontener prawo do porównania.

### <a name="remarks"></a>Uwagi

Funkcja operator zwraca wartość true, tylko wtedy, gdy sekwencje kontrolowane przez *po lewej stronie* i *prawo* tę samą długość, a dla każdej pozycji `i`, `left[i] ==` `right[i]`. Używanej do testowania czy *po lewej stronie* jest taka sama jak określona *prawo* po dwóch multisets są w porównaniu element po elemencie.

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

## <a name="op_gt"></a> operator&gt; (multiset) (STL/CLR)

Lista jest większa niż porównania.

### <a name="syntax"></a>Składnia

```cpp
template<typename Key>
    bool operator>(multiset<Key>% left,
        multiset<Key>% right);
```

#### <a name="parameters"></a>Parametry

*left*<br/>
Po lewej stronie kontenera do porównania.

*right*<br/>
Kontener prawo do porównania.

### <a name="remarks"></a>Uwagi

Funkcja operator zwraca `right` `<` `left`. Używanej do testowania czy *po lewej stronie* są porządkowane po *prawo* po dwóch multisets są w porównaniu element po elemencie.

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

## <a name="op_gteq"></a> operator&gt;= (multiset) (STL/CLR)

Lista większa niż lub równe porównania.

### <a name="syntax"></a>Składnia

```cpp
template<typename Key>
    bool operator>=(multiset<Key>% left,
        multiset<Key>% right);
```

#### <a name="parameters"></a>Parametry

*left*<br/>
Po lewej stronie kontenera do porównania.

*right*<br/>
Kontener prawo do porównania.

### <a name="remarks"></a>Uwagi

Funkcja operator zwraca `!(left < right)`. Można go używać do testowania czy *po lewej stronie* nie był zamówiony przed *prawo* po dwóch multisets są w porównaniu element po elemencie.

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