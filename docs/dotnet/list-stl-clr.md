---
title: list (STL/CLR)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- cliext::list
- cliext::list::assign
- cliext::list::assign
- cliext::list::back
- cliext::list::back_item
- cliext::list::begin
- cliext::list::clear
- cliext::list::const_iterator
- cliext::list::const_reference
- cliext::list::const_reverse_iterator
- cliext::list::difference_type
- cliext::list::empty
- cliext::list::end
- cliext::list::erase
- cliext::list::front
- cliext::list::front_item
- cliext::list::generic_container
- cliext::list::generic_iterator
- cliext::list::generic_reverse_iterator
- cliext::list::generic_value
- cliext::list::insert
- cliext::list::iterator
- cliext::list::list
- cliext::list::merge
- cliext::list::operator=
- cliext::list::pop_back
- cliext::list::pop_front
- cliext::list::push_back
- cliext::list::push_front
- cliext::list::rbegin
- cliext::list::reference
- cliext::list::remove
- cliext::list::remove_if
- cliext::list::rend
- cliext::list::resize
- cliext::list::reverse
- cliext::list::reverse_iterator
- cliext::list::size
- cliext::list::size_type
- cliext::list::sort
- cliext::list::splice
- cliext::list::swap
- cliext::list::to_array
- cliext::list::unique
- cliext::list::value_type
- cliext::operator!=(list)
- cliext::operator<(list)
- cliext::operator<=(list)
- cliext::operator==(list)
- cliext::operator>(list)
- cliext::operator>=(list)
helpviewer_keywords:
- <cliext/list> header [STL/CLR]
- list class [STL/CLR]
- <list> header [STL/CLR]
- assign member [STL/CLR]
- assign member [STL/CLR]
- back member [STL/CLR]
- back_item member [STL/CLR]
- begin member [STL/CLR]
- clear member [STL/CLR]
- const_iterator member [STL/CLR]
- const_reference member [STL/CLR]
- const_reverse_iterator member [STL/CLR]
- difference_type member [STL/CLR]
- empty member [STL/CLR]
- end member [STL/CLR]
- erase member [STL/CLR]
- front member [STL/CLR]
- front_item member [STL/CLR]
- generic_container member [STL/CLR]
- generic_iterator member [STL/CLR]
- generic_reverse_iterator member [STL/CLR]
- generic_value member [STL/CLR]
- insert member [STL/CLR]
- iterator member [STL/CLR]
- list member [STL/CLR]
- merge member [STL/CLR]
- operator= member [STL/CLR]
- pop_back member [STL/CLR]
- pop_front member [STL/CLR]
- push_back member [STL/CLR]
- push_front member [STL/CLR]
- rbegin member [STL/CLR]
- reference member [STL/CLR]
- remove member [STL/CLR]
- remove_if member [STL/CLR]
- rend member [STL/CLR]
- resize member [STL/CLR]
- reverse member [STL/CLR]
- reverse_iterator member [STL/CLR]
- size member [STL/CLR]
- size_type member [STL/CLR]
- sort member [STL/CLR]
- splice member [STL/CLR]
- swap member [STL/CLR]
- to_array member [STL/CLR]
- unique member [STL/CLR]
- value_type member [STL/CLR]
- operator!=(list) member [STL/CLR]
- operator<(list) member [STL/CLR]
- operator<=(list) member [STL/CLR]
- operator==(list) member [STL/CLR]
- operator>(list) member [STL/CLR]
- operator>=(list) member [STL/CLR]
ms.assetid: a70c45c8-a257-4f6b-8434-b27ff6685bac
ms.openlocfilehash: 8350e8b7036731cf3e09b9ce26278b2a656d80be
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50569588"
---
# <a name="list-stlclr"></a>list (STL/CLR)

Klasa szablonu opisuje obiekt, który kontroluje różnej długości sekwencje elementów mającego dostęp dwukierunkowy. Korzystasz z kontenera `list` Zarządzanie sekwencji elementów jako dwukierunkowy połączonej listy węzłów, w każdym przechowywania jeden element.

W poniższym opisie `GValue` jest taka sama jak *wartość* o ile nie jest typem odwołania, w którym to przypadku jest `Value^`.

## <a name="syntax"></a>Składnia

```cpp
template<typename Value>
    ref class list
        :   public
        System::ICloneable,
        System::Collections::IEnumerable,
        System::Collections::ICollection,
        System::Collections::Generic::IEnumerable<GValue>,
        System::Collections::Generic::ICollection<GValue>,
        Microsoft::VisualC::StlClr::IList<GValue>
    { ..... };
```

### <a name="parameters"></a>Parametry

*Wartość*<br/>
Typ elementu w kontrolowanej sekwencji.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<cliext — / list >

**Namespace:** cliext —

## <a name="declarations"></a>Deklaracje

|Definicja typu|Opis|
|---------------------|-----------------|
|[list::const_iterator (STL/CLR)](#const_iterator)|Typ iteratora stałego dla kontrolowanej sekwencji.|
|[list::const_reference (STL/CLR)](#const_reference)|Typ stałego odwołania do elementu.|
|[list::const_reverse_iterator (STL/CLR)](#const_reverse_iterator)|Typ iteratora odwrotnego stałego dla kontrolowanej sekwencji.|
|[list::difference_type (STL/CLR)](#difference_type)|Typ odległości ze znakiem między dwoma elementami.|
|[list::generic_container (STL/CLR)](#generic_container)|Typ ogólny interfejs dla kontenera.|
|[list::generic_iterator (STL/CLR)](#generic_iterator)|Typ iteratora dla ogólny interfejs dla kontenera.|
|[list::generic_reverse_iterator (STL/CLR)](#generic_reverse_iterator)|Typ iteratora odwrotnego dla ogólny interfejs dla kontenera.|
|[list::generic_value (STL/CLR)](#generic_value)|Typ elementu dla ogólny interfejs dla kontenera.|
|[list::iterator (STL/CLR)](#iterator)|Typ iteratora dla kontrolowanej sekwencji.|
|[list::reference (STL/CLR)](#reference)|Typ odwołania do elementu.|
|[list::reverse_iterator (STL/CLR)](#reverse_iterator)|Typ iteratora odwrotnego dla kontrolowanej sekwencji.|
|[list::size_type (STL/CLR)](#size_type)|Typ odległości ze znakiem między dwoma elementami.|
|[list::value_type (STL/CLR)](#value_type)|Typ elementu.|

|Funkcja elementów członkowskich|Opis|
|---------------------|-----------------|
|[list::assign (STL/CLR)](#assign)|Zamienia wszystkie elementy.|
|[list::back (STL/CLR)](#back)|Uzyskuje dostęp do ostatniego elementu.|
|[list::begin (STL/CLR)](#begin)|Określa początek kontrolowanej sekwencji.|
|[list::clear (STL/CLR)](#clear)|Usuwa wszystkie elementy.|
|[list::empty (STL/CLR)](#empty)|Sprawdza, czy nie ma żadnych elementów.|
|[list::end (STL/CLR)](#end)|Określa koniec kontrolowanej sekwencji.|
|[list::erase (STL/CLR)](#erase)|Usuwa elementy z określonych pozycji.|
|[list::front (STL/CLR)](#front)|Uzyskuje dostęp do pierwszego elementu.|
|[list::insert (STL/CLR)](#insert)|Dodaje elementy na określonej pozycji.|
|[list::list (STL/CLR)](#list)|Konstruuje obiekt kontenera.|
|[list::merge (STL/CLR)](#merge)|Scala dwa uporządkowane kontrolowanej sekwencji.|
|[list::pop_back (STL/CLR)](#pop_back)|Usuwa ostatni element.|
|[list::pop_front (STL/CLR)](#pop_front)|Usuwa pierwszy element.|
|[list::push_back (STL/CLR)](#push_back)|Dodaje nowy element ostatni.|
|[list::push_front (STL/CLR)](#push_front)|Dodaje nowy element pierwszego.|
|[list::rbegin (STL/CLR)](#rbegin)|Określa początek kontrolowanej sekwencji odwróconej.|
|[list::remove (STL/CLR)](#remove)|Usuwa element z określoną wartością.|
|[list::remove_if (STL/CLR)](#remove_if)|Usuwa elementy, zaliczonych określonego testu.|
|[list::rend (STL/CLR)](#rend)|Określa koniec kontrolowanej sekwencji odwróconej.|
|[list::resize (STL/CLR)](#resize)|Zmiany liczby elementów.|
|[list::reverse (STL/CLR)](#reverse)|Odwraca kontrolowanej sekwencji.|
|[list::size (STL/CLR)](#size)|Liczy liczbę elementów.|
|[list::sort (STL/CLR)](#sort)|Ustala kolejność kontrolowanej sekwencji.|
|[list::splice (STL/CLR)](#splice)|Restitches łącza między węzłami.|
|[list::swap (STL/CLR)](#swap)|Zamienia zawartości dwóch kontenerów.|
|[list::to_array (STL/CLR)](#to_array)|Kopiuje kontrolowanej sekwencji do nowej tablicy.|
|[list::unique (STL/CLR)](#unique)|Usuwa sąsiadujące elementy, które przekazać określonego testu.|

|Właściwość|Opis|
|--------------|-----------------|
|[list::back_item (STL/CLR)](#back_item)|Uzyskuje dostęp do ostatniego elementu.|
|[list::front_item (STL/CLR)](#front_item)|Uzyskuje dostęp do pierwszego elementu.|

|Operator|Opis|
|--------------|-----------------|
|[list::operator= (STL/CLR)](#op_as)|Zastępuje kontrolowanej sekwencji.|
|[operator!= (list) (STL/CLR)](#op_neq)|Określa, czy `list` obiekt nie jest równy innemu `list` obiektu.|
|[operator< (list) (STL/CLR)](#op_lt)|Określa, czy `list` obiekt jest mniejszy niż inny `list` obiektu.|
|[operator<= (list) (STL/CLR)](#op_lteq)|Określa, czy `list` obiekt jest mniejszy niż lub równy innemu `list` obiektu.|
|[operator== (list) (STL/CLR)](#op_eq)|Określa, czy `list` obiekt jest równy innemu `list` obiektu.|
|[operator> (list) (STL/CLR)](#op_gt)|Określa, czy `list` obiekt jest większy niż inny `list` obiektu.|
|[operator>= (list) (STL/CLR)](#op_gteq)|Określa, czy `list` obiekt jest większy niż lub równy innemu `list` obiektu.|

## <a name="interfaces"></a>Interfejsy

|Interface|Opis|
|---------------|-----------------|
|<xref:System.ICloneable>|Duplikowanie obiektów.|
|<xref:System.Collections.IEnumerable>|Przeprowadzaj sekwencjonowanie przez elementy.|
|<xref:System.Collections.ICollection>|Obsługa grupy elementów.|
|<xref:System.Collections.Generic.IEnumerable%601>|Przeprowadzaj Sekwencjonowanie za pośrednictwem typizowanych elementów.|
|<xref:System.Collections.Generic.ICollection%601>|Obsługa grupy typizowanych elementów.|
|IList\<wartość >|Obsługa kontenerów ogólnego.|

## <a name="remarks"></a>Uwagi

Obiekt przydziela i zwalnia pamięć dla sekwencji, który określa, jak poszczególne węzły na liście łączy dwukierunkowy. Go ponownie rozmieszcza elementy, zmieniając linki między węzłami, nigdy, kopiując zawartość jednego węzła do innego. Oznacza to, można wstawić i usuwanie elementów za darmo, bez zakłóceń pozostałe elementy. W związku z tym, lista jest dobrym kandydatem do bazowego kontener dla klasy szablonu [kolejki (STL/CLR)](../dotnet/queue-stl-clr.md) lub klasą szablonu [stosu (STL/CLR)](../dotnet/stack-stl-clr.md).

A `list` obiekt obsługuje Iteratory dwukierunkowe, co oznacza, że użytkownik może przechodzić do sąsiadujących elementów podany iterator, który wskazuje element w kontrolowanej sekwencji. Specjalne węzłem odnosi się do iteratora zwrócony przez [list::end (STL/CLR)](../dotnet/list-end-stl-clr.md)`()`. Można zmniejszyć tego iteratora, aby dotrzeć do ostatniego elementu w kontrolowanej sekwencji, jeśli jest obecny. Inkrementacji iteratora listy, aby dotrzeć do węzła głównego, a następnie porównaj równa `end()`. Ale nie można wyłuskać iteratora zwrócony przez `end()`.

Należy pamiętać, że nie można odwołać się do elementu listy bezpośrednio podanej pozycji liczbowych — wymagającego iteratora dostępu swobodnego. Dlatego jest lista *nie* można używać jako podstawowy kontener dla klasy szablonu [priority_queue — (STL/CLR)](../dotnet/priority-queue-stl-clr.md).

Iterator listy przechowuje dojścia do węzła skojarzonej listy, która z kolei przechowuje dojście do jego skojarzony kontener. Iteratory można użyć tylko w nich obiekty skojarzony kontener. Iterator listy zachowuje ważność tak długo, jak jego węzła skojarzonej listy jest skojarzony z niektórych listy. Ponadto, prawidłowy iteratora jest wyłuskiwania — służy do uzyskiwania dostępu lub zmienić wartości elementu ustanowi — tak długo, jak nie jest równa `end()`.

Wymazywanie lub usunięcie elementu wywołuje destruktor do jego przechowywanej wartości. Niszczenie kontenera usuwa wszystkie elementy. W związku z tym kontener, którego typ elementu jest klasą ref gwarantuje, że żadne elementy on nakreślał kontenera. Należy jednak pamiętać, że kontener dojścia nie *nie* zniszczyć jego elementów.

## <a name="members"></a>Elementy członkowskie

## <a name="assign"></a> list::ASSIGN (STL/CLR)

Zamienia wszystkie elementy.

### <a name="syntax"></a>Składnia

```cpp
void assign(size_type count, value_type val);
template<typename InIt>
    void assign(InIt first, InIt last);
void assign(System::Collections::Generic::IEnumerable<Value>^ right);
```

#### <a name="parameters"></a>Parametry

*Liczba*<br/>
Liczba elementów do wstawienia.

*pierwszy*<br/>
Początek zakresu do wstawienia.

*ostatni*<br/>
Koniec zakresu do wstawienia.

*right*<br/>
Wyliczenie do wstawienia.

*Val*<br/>
Wartość elementu do wstawienia.

### <a name="remarks"></a>Uwagi

Pierwsza funkcja elementu członkowskiego zamienia kontrolowanej sekwencji powtórzenia *liczba* elementów wartości *val*. Umożliwia ona wypełnić kontener z elementami wszystkich mających taką samą wartość.

Jeśli `InIt` typu liczby całkowitej, funkcja drugiego członka zachowuje się taka sama jak `assign((size_type)first, (value_type)last)`. W przeciwnym razie zastępuje kontrolowanej sekwencji za pomocą sekwencji [`first`, `last`). Umożliwia ona wprowadzić kontrolowanej sekwencji kopię innej sekwencji.

Trzecia funkcja członkowska zamienia kontrolowanej sekwencji sekwencji wyznaczonym przez moduł wyliczający *prawo*. Umożliwia ona kopię sekwencji kontrolowanej sekwencji opisanego przez moduł wyliczający.

### <a name="example"></a>Przykład

```cpp
// cliext_list_assign.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // assign a repetition of values
    cliext::list<wchar_t> c2;
    c2.assign(6, L'x');
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // assign an iterator range
    cliext::list<wchar_t>::iterator it = c1.end();
    c2.assign(c1.begin(), --it);
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // assign an enumeration
    c2.assign(   // NOTE: cast is not needed
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c1);
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
x x x x x x
a b
a b c
```

## <a name="back"></a> list::back (STL/CLR)

Uzyskuje dostęp do ostatniego elementu.

### <a name="syntax"></a>Składnia

```cpp
reference back();
```

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca odwołanie do ostatniego elementu w kontrolowanej sekwencji, która musi być niepusta. Umożliwia ona dostęp do ostatniego elementu, gdy wiadomo, że istnieje.

### <a name="example"></a>Przykład

```cpp
// cliext_list_back.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // inspect last item
    System::Console::WriteLine("back() = {0}", c1.back());

    // alter last item and reinspect
    c1.back() = L'x';
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
back() = c
a b x
```

## <a name="back_item"></a> list::back_item (STL/CLR)

Uzyskuje dostęp do ostatniego elementu.

### <a name="syntax"></a>Składnia

```cpp
property value_type back_item;
```

### <a name="remarks"></a>Uwagi

Właściwość uzyskuje dostęp do ostatniego elementu w kontrolowanej sekwencji, która musi być niepusta. Możesz użyć do odczytu lub zapisu ostatniego elementu, gdy wiadomo, że istnieje.

### <a name="example"></a>Przykład

```cpp
// cliext_list_back_item.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // inspect last item
    System::Console::WriteLine("back_item = {0}", c1.back_item);

    // alter last item and reinspect
    c1.back_item = L'x';
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
back_item = c
a b x
```

## <a name="begin"></a> list::BEGIN (STL/CLR)

Określa początek kontrolowanej sekwencji.

### <a name="syntax"></a>Składnia

```cpp
iterator begin();
```

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca iterator dostępu swobodnego, który wyznacza pierwszego elementu w kontrolowanej sekwencji lub tuż za koniec pustą sekwencją. Służy do uzyskiwania iterator, który wyznacza `current` początek kontrolowanej sekwencji, ale jej stan można zmienić, jeśli zmieni się długość kontrolowanej sekwencji.

### <a name="example"></a>Przykład

```cpp
// cliext_list_begin.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // inspect first two items
    cliext::list<wchar_t>::iterator it = c1.begin();
    System::Console::WriteLine("*begin() = {0}", *it);
    System::Console::WriteLine("*++begin() = {0}", *++it);

    // alter first two items and reinspect
    *--it = L'x';
    *++it = L'y';
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
*begin() = a
*++begin() = b
x y c
```

## <a name="clear"></a> list::Clear (STL/CLR)

Usuwa wszystkie elementy.

### <a name="syntax"></a>Składnia

```cpp
void clear();
```

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego skutecznie wywołuje [list::erase (STL/CLR)](../dotnet/list-erase-stl-clr.md) `(` [list::begin (STL/CLR)](../dotnet/list-begin-stl-clr.md) `(),` [list::end (STL/CLR)](../dotnet/list-end-stl-clr.md) `())`. Umożliwia ona upewnij się, że kontrolowanej sekwencji jest pusty.

### <a name="example"></a>Przykład

```cpp
// cliext_list_clear.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // clear the container and reinspect
    c1.clear();
    System::Console::WriteLine("size() = {0}", c1.size());

    // add elements and clear again
    c1.push_back(L'a');
    c1.push_back(L'b');

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

## <a name="const_iterator"></a> list::const_iterator (STL/CLR)

Typ iteratora stałego dla kontrolowanej sekwencji.

### <a name="syntax"></a>Składnia

```cpp
typedef T2 const_iterator;
```

### <a name="remarks"></a>Uwagi

Typ opisuje obiekt nieokreślonego typu `T2` który może służyć jako stały iterator dostępu swobodnego dla kontrolowanej sekwencji.

### <a name="example"></a>Przykład

```cpp
// cliext_list_const_iterator.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c"
    cliext::list<wchar_t>::const_iterator cit = c1.begin();
    for (; cit != c1.end(); ++cit)
        System::Console::Write("{0} ", *cit);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="const_reference"></a> list::const_reference (STL/CLR)

Typ stałego odwołania do elementu.

### <a name="syntax"></a>Składnia

```cpp
typedef value_type% const_reference;
```

### <a name="remarks"></a>Uwagi

Typ opisuje stałe odwołanie do elementu.

### <a name="example"></a>Przykład

```cpp
// cliext_list_const_reference.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a b c"
    cliext::list<wchar_t>::const_iterator cit = c1.begin();
    for (; cit != c1.end(); ++cit)
        {   // get a const reference to an element
        cliext::list<wchar_t>::const_reference cref = *cit;
        System::Console::Write("{0} ", cref);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="const_reverse_iterator"></a> list::const_reverse_iterator (STL/CLR)

Typ iteratora odwrotnego stałego dla kontrolowanej sekwencji...

### <a name="syntax"></a>Składnia

```cpp
typedef T4 const_reverse_iterator;
```

### <a name="remarks"></a>Uwagi

Typ opisuje obiekt nieokreślonego typu `T4` który może służyć jako stałe odwrotnego iteratora dla kontrolowanej sekwencji.

### <a name="example"></a>Przykład

```cpp
// cliext_list_const_reverse_iterator.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c" reversed
    cliext::list<wchar_t>::const_reverse_iterator crit = c1.rbegin();
    cliext::list<wchar_t>::const_reverse_iterator crend = c1.rend();
    for (; crit != crend; ++crit)
        System::Console::Write("{0} ", *crit);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
c b a
```

## <a name="difference_type"></a> list::difference_type (STL/CLR)

Typy odległości ze znakiem między dwoma elementami.

### <a name="syntax"></a>Składnia

```cpp
typedef int difference_type;
```

### <a name="remarks"></a>Uwagi

Typ opisuje liczba element podpisem.

### <a name="example"></a>Przykład

```cpp
// cliext_list_difference_type.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // compute positive difference
    cliext::list<wchar_t>::difference_type diff = 0;
    for (cliext::list<wchar_t>::iterator it = c1.begin();
        it != c1.end(); ++it) ++diff;
    System::Console::WriteLine("end()-begin() = {0}", diff);

    // compute negative difference
    diff = 0;
    for (cliext::list<wchar_t>::iterator it = c1.end();
        it != c1.begin(); --it) --diff;
    System::Console::WriteLine("begin()-end() = {0}", diff);
    return (0);
    }
```

```Output
a b c
end()-begin() = 3
begin()-end() = -3
```

## <a name="empty"></a> list::EMPTY (STL/CLR)

Sprawdza, czy nie ma żadnych elementów.

### <a name="syntax"></a>Składnia

```cpp
bool empty();
```

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca wartość true dla pustą kontrolowaną sekwencję. Jest to równoważne [list::size (STL/CLR)](../dotnet/list-size-stl-clr.md)`() == 0`. Możesz użyć do sprawdzenia, czy lista jest pusta.

### <a name="example"></a>Przykład

```cpp
// cliext_list_empty.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

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

## <a name="end"></a> list::end (STL/CLR)

Określa koniec kontrolowanej sekwencji.

### <a name="syntax"></a>Składnia

```cpp
iterator end();
```

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca iterator dostępu swobodnego, który wskazuje tuż za koniec kontrolowanej sekwencji. Służy do uzyskiwania iterator, który określa koniec kontrolowanej sekwencji; jego stan nie zmieniać, jeśli zmieni się długość kontrolowanej sekwencji.

### <a name="example"></a>Przykład

```cpp
// cliext_list_end.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // inspect last two items
    cliext::list<wchar_t>::iterator it = c1.end();
    --it;
    System::Console::WriteLine("*-- --end() = {0}", *--it);
    System::Console::WriteLine("*--end() = {0}", *++it);

    // alter first two items and reinspect
    *--it = L'x';
    *++it = L'y';
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
*-- --end() = b
*--end() = c
a x y
```

## <a name="erase"></a> list::ERASE (STL/CLR)

Usuwa elementy z określonych pozycji.

### <a name="syntax"></a>Składnia

```cpp
iterator erase(iterator where);
iterator erase(iterator first, iterator last);
```

#### <a name="parameters"></a>Parametry

*pierwszy*<br/>
Początek zakresu, aby wymazać.

*ostatni*<br/>
Koniec zakresu, aby wymazać.

*gdzie*<br/>
Element, aby wymazać.

### <a name="remarks"></a>Uwagi

Pierwsza funkcja członkostwa usuwa element kontrolowanej sekwencji wskazywany przez *gdzie*. Umożliwia ona usunąć pojedynczy element.

Funkcja drugiego członka usuwa elementy kontrolowanej sekwencji w zakresie [`first`, `last`). Umożliwia ona usunąć zero lub więcej elementów sąsiadujących.

Obie funkcje Członkowskie zwracają iterator opisujący pierwszy element pozostający poza wszelkimi elementami usuniętymi lub [list::end (STL/CLR)](../dotnet/list-end-stl-clr.md) `()` jeśli taki element nie istnieje.

Gdy wymazując elementy zależnie od, liczbę kopii elementu jest liniowa w liczbie elementów między końcem wymazywanie a im bliżej siebie końca sekwencji. (Podczas wymazywania jeden lub więcej elementów na końcu sekwencji, nie kopiuje element wykonywane.)

### <a name="example"></a>Przykład

```cpp
// cliext_list_erase.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // erase an element and reinspect
    System::Console::WriteLine("erase(begin()) = {0}",
        *c1.erase(c1.begin()));

    // add elements and display " b c d e"
    c1.push_back(L'd');
    c1.push_back(L'e');
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // erase all but end
    cliext::list<wchar_t>::iterator it = c1.end();
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

## <a name="front"></a> list::Front (STL/CLR)

Uzyskuje dostęp do pierwszego elementu.

### <a name="syntax"></a>Składnia

```cpp
reference front();
```

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca odwołanie do pierwszego elementu w kontrolowanej sekwencji, która musi być niepusta. Możesz użyć do odczytu lub zapisu pierwszego elementu, gdy wiadomo, że istnieje.

### <a name="example"></a>Przykład

```cpp
// cliext_list_front.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // inspect first item
    System::Console::WriteLine("front() = {0}", c1.front());

    // alter first item and reinspect
    c1.front() = L'x';
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
front() = a
x b c
```

## <a name="front_item"></a> list::front_item (STL/CLR)

Uzyskuje dostęp do pierwszego elementu.

### <a name="syntax"></a>Składnia

```cpp
property value_type front_item;
```

### <a name="remarks"></a>Uwagi

Właściwość uzyskuje dostęp do pierwszego elementu w kontrolowanej sekwencji, która musi być niepusta. Możesz użyć do odczytu lub zapisu pierwszego elementu, gdy wiadomo, że istnieje.

### <a name="example"></a>Przykład

```cpp
// cliext_list_front_item.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // inspect first item
    System::Console::WriteLine("front_item = {0}", c1.front_item);

    // alter first item and reinspect
    c1.front_item = L'x';
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
front_item = a
x b c
```

## <a name="generic_container"></a> list::generic_container (STL/CLR)

Typ ogólny interfejs dla kontenera.

### <a name="syntax"></a>Składnia

```cpp
typedef Microsoft::VisualC::StlClr::
    IList<generic_value>
    generic_container;
```

### <a name="remarks"></a>Uwagi

Typ opisuje ogólny interfejs dla tej klasy szablonu w kontenerze.

### <a name="example"></a>Przykład

```cpp
// cliext_list_generic_container.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct a generic container
    cliext::list<wchar_t>::generic_container^ gc1 = %c1;
    for each (wchar_t elem in gc1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // modify generic and display original
    gc1->insert(gc1->end(), L'd');
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // modify original and display generic
    c1.push_back(L'e');

    System::Collections::IEnumerator^ enum1 =
        gc1->GetEnumerator();
    while (enum1->MoveNext())
        System::Console::Write("{0} ", enum1->Current);
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

## <a name="generic_iterator"></a> list::generic_iterator (STL/CLR)

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
// cliext_list_generic_iterator.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct a generic container
    cliext::list<wchar_t>::generic_container^ gc1 = %c1;
    for each (wchar_t elem in gc1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // modify generic and display original
    cliext::list<wchar_t>::generic_iterator gcit = gc1->begin();
    cliext::list<wchar_t>::generic_value gcval = *gcit;
    *++gcit = gcval;
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
a b c
a a c
```

## <a name="generic_reverse_iterator"></a> list::generic_reverse_iterator (STL/CLR)

Typ iteratora odwrotnego do użytku z ogólny interfejs dla kontenera.

### <a name="syntax"></a>Składnia

```cpp
typedef Microsoft::VisualC::StlClr::Generic::
    ReverseBidirectionalIterator<generic_value> generic_reverse_iterator;
```

### <a name="remarks"></a>Uwagi

Typ opisuje iterator odwrotny ogólnego, które mogą być używane z ogólny interfejs dla tej klasy kontenera szablonu.

### <a name="example"></a>Przykład

```cpp
// cliext_list_generic_reverse_iterator.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct a generic container
    cliext::list<wchar_t>::generic_container^ gc1 = %c1;
    for each (wchar_t elem in gc1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // modify generic and display original
    cliext::list<wchar_t>::generic_reverse_iterator gcit = gc1->rbegin();
    cliext::list<wchar_t>::generic_value gcval = *gcit;
    *++gcit = gcval;
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
a b c
a c c
```

## <a name="generic_value"></a> list::generic_value (STL/CLR)

Typ elementu do użycia przy użyciu interfejsu ogólnego dla kontenera.

### <a name="syntax"></a>Składnia

```cpp
typedef GValue generic_value;
```

### <a name="remarks"></a>Uwagi

Typ opisuje obiekt typu `GValue` wartość elementu przechowywane do użytku z ogólny interfejs dla tej klasy kontenera szablonu, który opisuje.

### <a name="example"></a>Przykład

```cpp
// cliext_list_generic_value.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct a generic container
    cliext::list<wchar_t>::generic_container^ gc1 = %c1;
    for each (wchar_t elem in gc1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // modify generic and display original
    cliext::list<wchar_t>::generic_iterator gcit = gc1->begin();
    cliext::list<wchar_t>::generic_value gcval = *gcit;
    *++gcit = gcval;
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
a b c
a a c
```

## <a name="insert"></a> list::INSERT (STL/CLR)

Dodaje elementy na określonej pozycji.

### <a name="syntax"></a>Składnia

```cpp
iterator insert(iterator where, value_type val);
void insert(iterator where, size_type count, value_type val);
template<typename InIt>
    void insert(iterator where, InIt first, InIt last);
void insert(iterator where,
    System::Collections::Generic::IEnumerable<Value>^ right);
```

#### <a name="parameters"></a>Parametry

*Liczba*<br/>
Liczba elementów do wstawienia.

*pierwszy*<br/>
Początek zakresu do wstawienia.

*ostatni*<br/>
Koniec zakresu do wstawienia.

*right*<br/>
Wyliczenie do wstawienia.

*Val*<br/>
Wartość elementu do wstawienia.

*gdzie*<br/>
Miejsce w kontenerze, który będzie wstawiany przed.

### <a name="remarks"></a>Uwagi

Każdy element członkowski funkcji wstawiania przed elementem wskazywany przez *gdzie* w kontrolowanej sekwencji sekwencji określone przez pozostałe argumenty operacji.

Pierwsza funkcja elementu członkowskiego wstawia element z wartością *val* i zwraca iterator, który wyznacza nowo wstawionego elementu. Umożliwia ona Wstaw pojedynczy element przed miejsce wyznaczonym przez iterator.

Funkcja drugiego członka wstawia powtórzenia *liczba* elementów wartości *val*. Umożliwia ona Wstaw zero lub więcej elementów sąsiadujących, które są wszystkie kopie tej samej wartości.

Jeśli `InIt` typu liczby całkowitej, trzecia funkcji członkowska, działa tak samo jak `insert(where, (size_type)first, (value_type)last)`. W przeciwnym razie wstawia sekwencję [`first`, `last`). Umożliwia ona Wstaw zero lub więcej elementów sąsiadujących, skopiowane z innej sekwencji.

Czwarty funkcja elementu członkowskiego wstawia sekwencję wyznaczonym przez *prawo*. Umożliwia ona Wstaw sekwencję opisanego przez moduł wyliczający.

Podczas wstawiania pojedynczy element, liczbę kopii elementu jest liniowa w liczbie elementów od punktu wstawiania i im bliżej siebie końca sekwencji. (Wstawiając na końcu sekwencji jednego lub więcej elementów, nie kopiuje element wykonywane.) Jeśli `InIt` iterator danych wejściowych jest trzecia funkcji członkowska skutecznie wykonuje wstawiania jednej dla każdego elementu w sekwencji. W przeciwnym razie podczas wstawiania `N` elementów na liczbę kopii elementu jest liniowa w `N` plus liczba elementów od punktu wstawiania i im bliżej siebie końca sekwencji.

### <a name="example"></a>Przykład

```cpp
// cliext_list_insert.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // insert a single value using iterator
    cliext::list<wchar_t>::iterator it = c1.begin();
    System::Console::WriteLine("insert(begin()+1, L'x') = {0}",
        *c1.insert(++it, L'x'));
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // insert a repetition of values
    cliext::list<wchar_t> c2;
    c2.insert(c2.begin(), 2, L'y');
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // insert an iterator range
    it = c1.end();
    c2.insert(c2.end(), c1.begin(), --it);
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // insert an enumeration
    c2.insert(c2.begin(),   // NOTE: cast is not needed
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c1);
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // insert a single value using index
    it = c2.begin();
    ++it, ++it, ++it;
    c2.insert(it, L'z');
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    return (0);
    }
```

```Output
a b c
insert(begin()+1, L'x') = x
a x b c
y y
y y a x b
a x b c y y a x b
```

## <a name="iterator"></a> list::iterator (STL/CLR)

Typ iteratora dla kontrolowanej sekwencji.

### <a name="syntax"></a>Składnia

```cpp
typedef T1 iterator;
```

### <a name="remarks"></a>Uwagi

Typ opisuje obiekt nieokreślonego typu `T1` który może służyć jako iterator dostępu swobodnego dla kontrolowanej sekwencji.

### <a name="example"></a>Przykład

```cpp
// cliext_list_iterator.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c"
    cliext::list<wchar_t>::iterator it = c1.begin();
    for (; it != c1.end(); ++it)
        System::Console::Write("{0} ", *it);
    System::Console::WriteLine();

    // alter first element and redisplay
    it = c1.begin();
    *it = L'x';
    for (; it != c1.end(); ++it)
        System::Console::Write("{0} ", *it);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
x b c
```

## <a name="list"></a> list::list (STL/CLR)

Konstruuje obiekt kontenera.

### <a name="syntax"></a>Składnia

```cpp
list();
list(list<Value>% right);
list(list<Value>^ right);
explicit list(size_type count);
list(size_type count, value_type val);
template<typename InIt>
    list(InIt first, InIt last);
list(System::Collections::Generic::IEnumerable<Value>^ right);
```

#### <a name="parameters"></a>Parametry

*Liczba*<br/>
Liczba elementów do wstawienia.

*pierwszy*<br/>
Początek zakresu do wstawienia.

*ostatni*<br/>
Koniec zakresu do wstawienia.

*right*<br/>
Obiekt lub zakresu do wstawienia.

*Val*<br/>
Wartość elementu do wstawienia.

### <a name="remarks"></a>Uwagi

Konstruktor:

`list();`

Inicjuje kontrolowanej sekwencji bez elementów. Umożliwia ona określenie pustą kontrolowaną sekwencję początkowej.

Konstruktor:

`list(list<Value>% right);`

Inicjuje kontrolowanej sekwencji za pomocą sekwencji [`right.begin()`, `right.end()`). Umożliwia ona określenie początkowej kontrolowanej sekwencji, który jest kopią na sekwencję kontrolowaną przez obiekt listy *prawo*.

Konstruktor:

`list(list<Value>^ right);`

Inicjuje kontrolowanej sekwencji za pomocą sekwencji [`right->begin()`, `right->end()`). Umożliwia ona określenie początkowej kontrolowanej sekwencji, który jest kopią na sekwencję kontrolowaną przez obiekt listy, w których dojście jest *prawo*.

Konstruktor:

`explicit list(size_type count);`

Inicjuje kontrolowanej sekwencji za pomocą *liczba* elementów z wartością `value_type()`. Umożliwia ona wypełnić kontener z elementami wszystkich mających wartość domyślną.

Konstruktor:

`list(size_type count, value_type val);`

Inicjuje kontrolowanej sekwencji za pomocą *liczba* elementów z wartością *val*. Umożliwia ona wypełnić kontener z elementami wszystkich mających taką samą wartość.

Konstruktor:

`template<typename InIt>`

`list(InIt first, InIt last);`

Inicjuje kontrolowanej sekwencji za pomocą sekwencji [`first`, `last`). Umożliwia ona Utwórz kopię innej sekwencji kontrolowanej sekwencji.

Konstruktor:

`list(System::Collections::Generic::IEnumerable<Value>^ right);`

Inicjuje kontrolowanej sekwencji za pomocą sekwencji wyznaczonym przez moduł wyliczający *prawo*. Umożliwia ona utworzyć kopię sekwencji innego opisanego przez moduł wyliczający kontrolowanej sekwencji.

### <a name="example"></a>Przykład

```cpp
// cliext_list_construct.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
// construct an empty container
    cliext::list<wchar_t> c1;
    System::Console::WriteLine("size() = {0}", c1.size());

    // construct with a repetition of default values
    cliext::list<wchar_t> c2(3);
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", (int)elem);
    System::Console::WriteLine();

    // construct with a repetition of values
    cliext::list<wchar_t> c3(6, L'x');
    for each (wchar_t elem in c3)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct with an iterator range
    cliext::list<wchar_t>::iterator it = c3.end();
    cliext::list<wchar_t> c4(c3.begin(), --it);
    for each (wchar_t elem in c4)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct with an enumeration
    cliext::list<wchar_t> c5(   // NOTE: cast is not needed
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c3);
    for each (wchar_t elem in c5)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct by copying another container
    cliext::list<wchar_t> c7(c3);
    for each (wchar_t elem in c7)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct by copying a container handle
    cliext::list<wchar_t> c8(%c3);
    for each (wchar_t elem in c8)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    return (0);
    }
```

```Output
size() = 0
0 0 0
x x x x x x
x x x x x
x x x x x x
x x x x x x
x x x x x x
```

## <a name="merge"></a> list::merge (STL/CLR)

Scala dwa uporządkowane kontrolowanej sekwencji.

### <a name="syntax"></a>Składnia

```cpp
void merge(list<Value>% right);
template<typename Pred2>
    void merge(list<Value>% right, Pred2 pred);
```

#### <a name="parameters"></a>Parametry

*P.*<br/>
Moduł porównujący dla pary elementów.

*right*<br/>
Kontener do scalenia w.

### <a name="remarks"></a>Uwagi

Pierwsza funkcja członkostwa usuwa wszystkie elementy z sekwencji kontrolowanej przez *prawo* i umieść je w kontrolowanej sekwencji. Zarówno sekwencji musi być wcześniej uporządkowane według `operator<` — elementy nie musi zmniejszać wartości w czasie za pomocą jednej sekwencji. Wynikowa sekwencja również są uporządkowane według `operator<`. Użyjesz tej funkcji elementu członkowskiego do scalania dwóch sekwencji, które zwiększają wartość w sekwencji, która zwiększa się również w wartości.

Funkcja drugiego członka zachowuje się taka sama jak pierwsza strona, z tą różnicą, że sekwencje są uporządkowane według `pred`  --  `pred(X, Y)` musi mieć wartość false, dla każdego elementu `X` następujący element `Y` w sekwencji. Umożliwia ona scalić dwie sekwencje uporządkowane według funkcji predykatu lub delegata, który określisz.

Zarówno funkcje wykonują stabilne scalania — nie pary elementów w jednym z oryginalnej sekwencji kontrolowanej jest wycofana w wynikowej kontrolowanej sekwencji. Ponadto jeśli pary elementów `X` i `Y` w kontrolowanej sekwencji wynikowy ma równoważną kolejność — `!(X < Y) && !(X < Y)` — element z oryginalnej sekwencji kontrolowanej jest umieszczany przed elementem z sekwencji kontrolowanej przez *prawo*.

### <a name="example"></a>Przykład

```cpp
// cliext_list_merge.cpp
// compile with: /clr
#include <cliext/list>

typedef cliext::list<wchar_t> Mylist;
int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'c');
    c1.push_back(L'e');

    // display initial contents " a c e"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    cliext::list<wchar_t> c2;
    c2.push_back(L'b');
    c2.push_back(L'd');
    c2.push_back(L'f');

    // display initial contents " b d f"
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // merge and display
    cliext::list<wchar_t> c3(c1);
    c3.merge(c2);
    for each (wchar_t elem in c3)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    System::Console::WriteLine("c2.size() = {0}", c2.size());

    // sort descending, merge descending, and redisplay
    c1.sort(cliext::greater<wchar_t>());
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    c3.sort(cliext::greater<wchar_t>());
    for each (wchar_t elem in c3)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    c3.merge(c1, cliext::greater<wchar_t>());
    for each (wchar_t elem in c3)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    System::Console::WriteLine("c1.size() = {0}", c1.size());
    return (0);
    }
```

```Output
a c e
b d f
a b c d e f
c2.size() = 0
e c a
f e d c b a
f e e d c c b a a
c1.size() = 0
```

## <a name="op_as"></a> list::operator = (STL/CLR)

Zastępuje kontrolowanej sekwencji.

### <a name="syntax"></a>Składnia

```
list<Value>% operator=(list<Value>% right);
```

#### <a name="parameters"></a>Parametry

*right*<br/>
Kontener do skopiowania.

### <a name="remarks"></a>Uwagi

Kopiuje operator składowej *prawo* do obiektu, następnie zwraca `*this`. Umożliwia ona Zastąp kopię kontrolowanej sekwencji w kontrolowanej sekwencji *prawo*.

### <a name="example"></a>Przykład

```cpp
// cliext_list_operator_as.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // assign to a new container
    cliext::list<wchar_t> c2;
    c2 = c1;
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
a b c
```

## <a name="pop_back"></a> list::pop_back (STL/CLR)

Usuwa ostatni element.

### <a name="syntax"></a>Składnia

```cpp
void pop_back();
```

### <a name="remarks"></a>Uwagi

Funkcja członkowska usuwa ostatniego elementu w kontrolowanej sekwencji, która musi być niepusta. Umożliwia ona skrócić czas na liście przez jeden element w tle.

### <a name="example"></a>Przykład

```cpp
// cliext_list_pop_back.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // pop an element and redisplay
    c1.pop_back();
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
a b
```

## <a name="pop_front"></a> list::pop_front (STL/CLR)

Usuwa pierwszy element.

### <a name="syntax"></a>Składnia

```cpp
void pop_front();
```

### <a name="remarks"></a>Uwagi

Funkcja członkowska usuwa pierwszego elementu w kontrolowanej sekwencji, która musi być niepusta. Umożliwia ona skrócić czas na liście przez jeden element z przodu.

### <a name="example"></a>Przykład

```cpp
// cliext_list_pop_front.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // pop an element and redisplay
    c1.pop_front();
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
b c
```

## <a name="push_back"></a> list::push_back (STL/CLR)

Dodaje nowy element ostatni.

### <a name="syntax"></a>Składnia

```cpp
void push_back(value_type val);
```

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego wstawia element z wartością `val` na koniec kontrolowanej sekwencji. Możesz użyć do dołączania innego elementu do listy.

### <a name="example"></a>Przykład

```cpp
// cliext_list_push_back.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="push_front"></a> list::push_front (STL/CLR)

Dodaje nowy element pierwszego.

### <a name="syntax"></a>Składnia

```cpp
void push_front(value_type val);
```

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego wstawia element z wartością `val` na początku kontrolowanej sekwencji. Umożliwia ona dołączana do innego elementu do listy.

### <a name="example"></a>Przykład

```cpp
// cliext_list_push_front.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_front(L'a');
    c1.push_front(L'b');
    c1.push_front(L'c');

    // display contents " c b a"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
c b a
```

## <a name="rbegin"></a> list::rbegin (STL/CLR)

Określa początek kontrolowanej sekwencji odwróconej.

### <a name="syntax"></a>Składnia

```cpp
reverse_iterator rbegin();
```

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca odwrotnego iteratora, który wyznacza wartość ostatniego elementu w kontrolowanej sekwencji lub tuż za koniec pustą sekwencją. Dzięki temu wyznacza `beginning` odwrotnej kolejności. Służy do uzyskiwania iterator, który wyznacza `current` początek kontrolowanej sekwencji występuje w odwrotnej kolejności, ale jej stan można zmienić, jeśli zmieni się długość kontrolowanej sekwencji.

### <a name="example"></a>Przykład

```cpp
// cliext_list_rbegin.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // inspect first two items in reversed sequence
    cliext::list<wchar_t>::reverse_iterator rit = c1.rbegin();
    System::Console::WriteLine("*rbegin() = {0}", *rit);
    System::Console::WriteLine("*++rbegin() = {0}", *++rit);

    // alter first two items and reinspect
    *--rit = L'x';
    *++rit = L'y';
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
*rbegin() = c
*++rbegin() = b
a y x
```

## <a name="reference"></a> list::Reference (STL/CLR)

Typ odwołania do elementu.

### <a name="syntax"></a>Składnia

```cpp
typedef value_type% reference;
```

### <a name="remarks"></a>Uwagi

Typ opisuje odwołanie do elementu.

### <a name="example"></a>Przykład

```cpp
// cliext_list_reference.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a b c"
    cliext::list<wchar_t>::iterator it = c1.begin();
    for (; it != c1.end(); ++it)
        {   // get a reference to an element
        cliext::list<wchar_t>::reference ref = *it;
        System::Console::Write("{0} ", ref);
        }
    System::Console::WriteLine();

    // modify contents " a b c"
    for (it = c1.begin(); it != c1.end(); ++it)
        {   // get a reference to an element
        cliext::list<wchar_t>::reference ref = *it;

        ref += (wchar_t)(L'A' - L'a');
        System::Console::Write("{0} ", ref);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
A B C
```

## <a name="remove"></a> list::Remove (STL/CLR)

Usuwa element z określoną wartością.

### <a name="syntax"></a>Składnia

```cpp
void remove(value_type val);
```

#### <a name="parameters"></a>Parametry

*Val*<br/>
Wartość elementu do usunięcia.

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego spowoduje usunięcie elementu w kontrolowanej sekwencji dla którego `((System::Object^)val)->Equals((System::Object^)x)` ma wartość true, (jeśli istnieje). Umożliwia ona wymazać dowolnego elementu z określoną wartością.

### <a name="example"></a>Przykład

```cpp
// cliext_list_remove.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // fail to remove and redisplay
    c1.remove(L'A');
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // remove and redisplay
    c1.remove(L'b');
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
a b c
a c
```

## <a name="remove_if"></a> list::remove_if (STL/CLR)

Usuwa elementy, zaliczonych określonego testu.

### <a name="syntax"></a>Składnia

```cpp
template<typename Pred1>
    void remove_if(Pred1 pred);
```

#### <a name="parameters"></a>Parametry

*P.*<br/>
Test dla elementów do usunięcia.

### <a name="remarks"></a>Uwagi

Funkcja członkowska usuwa w kontrolowanej sekwencji (wymazywanie) każdego elementu `X` dla którego `pred(X)` ma wartość true. Umożliwia ona usunięcie wszystkich elementów, które spełniają warunek, że można określić jako funkcja lub delegata.

### <a name="example"></a>Przykład

```cpp
// cliext_list_remove_if.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'b');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a b b b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // fail to remove and redisplay
    c1.remove_if(cliext::binder2nd<cliext::equal_to<wchar_t> >(
        cliext::equal_to<wchar_t>(), L'd'));
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // remove and redisplay
    c1.remove_if(cliext::binder2nd<cliext::not_equal_to<wchar_t> >(
        cliext::not_equal_to<wchar_t>(), L'b'));
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b b b c
a b b b c
b b b
```

## <a name="rend"></a> list::rend (STL/CLR)

Określa koniec kontrolowanej sekwencji odwróconej.

### <a name="syntax"></a>Składnia

```cpp
reverse_iterator rend();
```

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca odwrotnego iteratora, który wskazuje tuż za początek kontrolowanej sekwencji. Dzięki temu wyznacza `end` odwrotnej kolejności. Służy do uzyskiwania iterator, który wyznacza `current` koniec kontrolowanej sekwencji występuje w odwrotnej kolejności, ale jej stan można zmienić, jeśli zmieni się długość kontrolowanej sekwencji.

### <a name="example"></a>Przykład

```cpp
// cliext_list_rend.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // inspect first two items
    cliext::list<wchar_t>::reverse_iterator rit = c1.rend();
    --rit;
    System::Console::WriteLine("*-- --rend() = {0}", *--rit);
    System::Console::WriteLine("*--rend() = {0}", *++rit);

    // alter first two items and reinspect
    *--rit = L'x';
    *++rit = L'y';
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
*-- --rend() = b
*--rend() = a
y x c
```

## <a name="resize"></a> list::Resize (STL/CLR)

Zmiany liczby elementów.

### <a name="syntax"></a>Składnia

```cpp
void resize(size_type new_size);
void resize(size_type new_size, value_type val);
```

#### <a name="parameters"></a>Parametry

*new_size*<br/>
Nowy rozmiar kontrolowanej sekwencji.

*Val*<br/>
Wartość elementu dopełnienia.

### <a name="remarks"></a>Uwagi

Funkcje elementów członkowskich obu, upewnij się, że [list::size (STL/CLR)](../dotnet/list-size-stl-clr.md) `()` odtąd zwraca *new_size*. Jeśli musi stworzyć kontrolowanej sekwencji dłużej, pierwsza funkcja elementu członkowskiego dołącza elementy z wartością `value_type()`, natomiast funkcja drugiego członka dołącza elementy z wartością *val*. Aby kontrolowanej sekwencji krótszy, oba funkcje Członkowskie skutecznie wymazać po ostatnim elemencie [list::size (STL/CLR)](../dotnet/list-size-stl-clr.md) `() -` `new_size` razy. Służy do Sprawdź, czy kontrolowanej sekwencji ma rozmiar *new_size*, przycinanie lub wypełnienie bieżącej kontrolowanej sekwencji.

### <a name="example"></a>Przykład

```cpp
// cliext_list_resize.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
// construct an empty container and pad with default values
    cliext::list<wchar_t> c1;
    System::Console::WriteLine("size() = {0}", c1.size());
    c1.resize(4);
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", (int)elem);
    System::Console::WriteLine();

    // resize to empty
    c1.resize(0);
    System::Console::WriteLine("size() = {0}", c1.size());

    // resize and pad
    c1.resize(5, L'x');
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
size() = 0
0 0 0 0
size() = 0
x x x x x
```

## <a name="reverse"></a> list::reverse (STL/CLR)

Odwraca kontrolowanej sekwencji.

### <a name="syntax"></a>Składnia

```cpp
void reverse();
```

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego Odwraca kolejność wszystkich elementów w kontrolowanej sekwencji. Umożliwia ona odzwierciedlają listy elementów.

### <a name="example"></a>Przykład

```cpp
// cliext_list_reverse.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // reverse and redisplay
    c1.reverse();
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
c b a
```

## <a name="reverse_iterator"></a> list::reverse_iterator (STL/CLR)

Typ iteratora odwrotnego dla kontrolowanej sekwencji.

### <a name="syntax"></a>Składnia

```cpp
typedef T3 reverse_iterator;
```

### <a name="remarks"></a>Uwagi

Typ opisuje obiekt nieokreślonego typu `T3` który może służyć jako odwrotnego iteratora dla kontrolowanej sekwencji.

### <a name="example"></a>Przykład

```cpp
// cliext_list_reverse_iterator.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c" reversed
    cliext::list<wchar_t>::reverse_iterator rit = c1.rbegin();
    for (; rit != c1.rend(); ++rit)
        System::Console::Write("{0} ", *rit);
    System::Console::WriteLine();

    // alter first element and redisplay
    rit = c1.rbegin();
    *rit = L'x';
    for (; rit != c1.rend(); ++rit)
        System::Console::Write("{0} ", *rit);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
c b a
x b a
```

## <a name="size"></a> list::size (STL/CLR)

Liczy liczbę elementów.

### <a name="syntax"></a>Składnia

```cpp
size_type size();
```

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca długość kontrolowanej sekwencji. Umożliwia ona określenie liczby elementów aktualnie w kontrolowanej sekwencji. Jeśli jest wszystkich interesujących Cię, czy sekwencja ma wartość różną od zera rozmiaru, zobacz [list::empty (STL/CLR)](../dotnet/list-empty-stl-clr.md)`()`.

### <a name="example"></a>Przykład

```cpp
// cliext_list_size.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    System::Console::WriteLine("size() = {0} starting with 3", c1.size());

    // clear the container and reinspect
    c1.clear();
    System::Console::WriteLine("size() = {0} after clearing", c1.size());

    // add elements and clear again
    c1.push_back(L'a');
    c1.push_back(L'b');
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

## <a name="size_type"></a> list::size_type (STL/CLR)

Typ odległości ze znakiem między dwoma elementu.

### <a name="syntax"></a>Składnia

```cpp
typedef int size_type;
```

### <a name="remarks"></a>Uwagi

Typ opisuje liczby nieujemnej wartości elementu.

### <a name="example"></a>Przykład

```cpp
// cliext_list_size_type.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // compute positive difference
    cliext::list<wchar_t>::size_type diff = 0;
    for (cliext::list<wchar_t>::iterator it = c1.begin();
        it != c1.end(); ++it)
        ++diff;
    System::Console::WriteLine("end()-begin() = {0}", diff);
    return (0);
    }
```

```Output
a b c
end()-begin() = 3
```

## <a name="sort"></a> list::sort (STL/CLR)

Ustala kolejność kontrolowanej sekwencji.

### <a name="syntax"></a>Składnia

```cpp
void sort();
template<typename Pred2>
    void sort(Pred2 pred);
```

#### <a name="parameters"></a>Parametry

*P.*<br/>
Moduł porównujący dla pary elementów.

### <a name="remarks"></a>Uwagi

Pierwsza funkcja elementu członkowskiego zmienia kolejność elementów w kontrolowanej sekwencji, dzięki czemu są one uporządkowane według `operator<` — elementy nie obniżaj wartości wraz z sekwencją. Użyjesz tej funkcji elementu członkowskiego do sortowania sekwencji w kolejności rosnącej.

Funkcja drugiego członka zachowuje się taka sama jak pierwsza strona, z tą różnicą, że sekwencja są uporządkowane według `pred`  --  `pred(X, Y)` ma wartość false dla dowolnego elementu `X` następujący element `Y` wynikowe sekwencji. Możesz użyć do sortowania sekwencji w kolejności określonej przez funkcji predykatu lub delegata.

Zarówno funkcje wykonują stabilne sortowanie — nie pary elementów w oryginalnej sekwencji kontrolowanej jest wycofana w wynikowej kontrolowanej sekwencji.

### <a name="example"></a>Przykład

```cpp
// cliext_list_sort.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // sort descending and redisplay
    c1.sort(cliext::greater<wchar_t>());
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // sort ascending and redisplay
    c1.sort();
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
c b a
a b c
```

## <a name="splice"></a> list::splice (STL/CLR)

Restitch łącza między węzłami.

### <a name="syntax"></a>Składnia

```cpp
void splice(iterator where, list<Value>% right);
void splice(iterator where, list<Value>% right,
    iterator first);
void splice(iterator where, list<Value>% right,
    iterator first, iterator last);
```

#### <a name="parameters"></a>Parametry

*pierwszy*<br/>
Początek zakresu do splice.

*ostatni*<br/>
Koniec zakresu splice.

*right*<br/>
Splice — od kontener.

*gdzie*<br/>
Miejsce w kontenerze do splice przed.

### <a name="remarks"></a>Uwagi

Pierwsza funkcja elementu członkowskiego wstawia sekwencji kontrolowanej przez *prawo* przed elementu w kontrolowanej sekwencji wskazywany przez *gdzie*. Powoduje ono także usunięcie wszystkich elementów z *prawo*. (`%right` nie musi być równa `this`.) Umożliwia ona splice — wszystko z jednej listy do innego.

Funkcja drugiego członka usuwa element wskazane przez *pierwszy* w sekwencji kontrolowanej przez *prawo* i wstawia go przed elementu w kontrolowanej sekwencji wskazywany przez *gdzie* . (Jeśli `where` `==` `first` `||` `where` `== ++first`, nie zmienią.) Umożliwia ona splice pojedynczy element jednej listy do innego.

Trzecia funkcja członkowska wstawia Podzakres wyznaczonym przez [`first`, `last`) z sekwencji kontrolowanej przez *prawo* przed elementem w kontrolowanej sekwencji wskazywany przez *gdzie*. Również usunięcie oryginalnego Podzakres z sekwencji kontrolowanej przez *prawo*. (Jeśli `right` `==` `this`, zakres [`first`, `last`) nie może zawierać element wskazane przez *gdzie*.) Umożliwia ona splice podsekwencja zero lub więcej elementów z jednej listy do innego.

### <a name="example"></a>Przykład

```cpp
// cliext_list_splice.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // splice to a new list
    cliext::list<wchar_t> c2;
    c2.splice(c2.begin(), c1);
    System::Console::WriteLine("c1.size() = {0}", c1.size());
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // return one element
    c1.splice(c1.end(), c2, c2.begin());
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // return remaining elements
    c1.splice(c1.begin(), c2, c2.begin(), c2.end());
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    System::Console::WriteLine("c2.size() = {0}", c2.size());
    return (0);
    }
```

```Output
a b c
c1.size() = 0
a b c
a
b c
b c a
c2.size() = 0
```

## <a name="swap"></a> list::swap (STL/CLR)

Zamienia zawartości dwóch kontenerów.

### <a name="syntax"></a>Składnia

```cpp
void swap(list<Value>% right);
```

#### <a name="parameters"></a>Parametry

*right*<br/>
Kontener do wymiany zawartości z.

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zamienia kontrolowanej sekwencji między `*this` i *prawo*. Robi to w stałym czasie i w wyniku weryfikacji zgłasza wyjątek bez wyjątków. Możesz użyć go w prosty sposób do wymiany zawartości dwóch kontenerów.

### <a name="example"></a>Przykład

```cpp
// cliext_list_swap.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct another container with repetition of values
    cliext::list<wchar_t> c2(5, L'x');
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
x x x x x
x x x x x
a b c
```

## <a name="to_array"></a> list::to_array (STL/CLR)

Kopiuje kontrolowanej sekwencji do nowej tablicy.

### <a name="syntax"></a>Składnia

```cpp
cli::array<Value>^ to_array();
```

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca tablicę zawierającą kontrolowanej sekwencji. Umożliwia ona otrzymać kopię kontrolowanej sekwencji w postaci tablicy.

### <a name="example"></a>Przykład

```cpp
// cliext_list_to_array.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // copy the container and modify it
    cli::array<wchar_t>^ a1 = c1.to_array();

    c1.push_back(L'd');
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

## <a name="unique"></a> list::Unique (STL/CLR)

Usuwa sąsiadujące elementy, które przekazać określonego testu.

### <a name="syntax"></a>Składnia

```cpp
void unique();
template<typename Pred2>
    void unique(Pred2 pred);
```

#### <a name="parameters"></a>Parametry

*P.*<br/>
Moduł porównujący dla pary elementów.

### <a name="remarks"></a>Uwagi

Pierwsza funkcja członkostwa usuwa w kontrolowanej sekwencji (wymazywanie) każdego elementu, który porównuje równa jego poprzedzający element — Jeśli element `X` poprzedza element `Y` i `X == Y`, funkcja członkowska usuwa `Y`. Umożliwia ona Usuń wszystkie oprócz jednego kopię każdego podsekwencję sąsiadujące elementy tego porównania równości. Należy pamiętać, że jeśli kontrolowanej sekwencji jest określona, takie jak przez wywołanie metody [list::sort (STL/CLR)](../dotnet/list-sort-stl-clr.md)`()`, funkcja elementu członkowskiego pozostawia tylko elementów z unikatowymi wartościami. (Stąd nazwa).

Funkcja drugiego członka zachowuje się taka sama jak pierwsza strona, z tą różnicą, że spowoduje usunięcie każdego elementu `Y` następującego elementu `X` dla którego `pred(X, Y)`. Umożliwia ona Usuń wszystkie oprócz jednego kopię każdego podsekwencję sąsiadujące elementy, które spełniają wymagania funkcji predykatu lub delegata, który określisz. Należy pamiętać, że jeśli kontrolowanej sekwencji jest określona, takie jak przez wywołanie metody `sort(pred)`, funkcja elementu członkowskiego pozostawia tylko te elementy, które nie mają równoważną kolejność z innymi elementami.

### <a name="example"></a>Przykład

```cpp
// cliext_list_unique.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // display contents after unique
    cliext::list<wchar_t> c2(c1);
    c2.unique();
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // display contents after unique(not_equal_to)
    c2 = c1;
    c2.unique(cliext::not_equal_to<wchar_t>());
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a a b c
a b c
a a
```

## <a name="value_type"></a> list::value_type (STL/CLR)

Typ elementu.

### <a name="syntax"></a>Składnia

```cpp
typedef Value value_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla parametru szablonu *wartość*.

### <a name="example"></a>Przykład

```cpp
// cliext_list_value_type.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c" using value_type
    for (cliext::list<wchar_t>::iterator it = c1.begin();
        it != c1.end(); ++it)
        {   // store element in value_type object
        cliext::list<wchar_t>::value_type val = *it;

        System::Console::Write("{0} ", val);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="op_neq"></a> Operator! = (lista) (STL/CLR)

Lista nie jest równe porównania.

### <a name="syntax"></a>Składnia

```cpp
template<typename Value>
    bool operator!=(list<Value>% left,
        list<Value>% right);
```

#### <a name="parameters"></a>Parametry

*left*<br/>
Po lewej stronie kontenera do porównania.

*right*<br/>
Kontener prawo do porównania.

### <a name="remarks"></a>Uwagi

Funkcja operator zwraca `!(left == right)`. Można go używać do testowania czy *po lewej stronie* nie jest taka sama jak określona *prawo* kiedy dwie listy są w porównaniu element po elemencie.

### <a name="example"></a>Przykład

```cpp
// cliext_list_operator_ne.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // assign to a new container
    cliext::list<wchar_t> c2;
    c2.push_back(L'a');
    c2.push_back(L'b');
    c2.push_back(L'd');

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

## <a name="op_lt"></a> operator&lt; (lista) (STL/CLR)

Lista mniejsza niż porównania.

### <a name="syntax"></a>Składnia

```cpp
template<typename Value>
    bool operator<(list<Value>% left,
        list<Value>% right);
```

#### <a name="parameters"></a>Parametry

*left*<br/>
Po lewej stronie kontenera do porównania.

*right*<br/>
Kontener prawo do porównania.

### <a name="remarks"></a>Uwagi

Operator funkcja zwraca wartość true, jeśli, na najniższą pozycję `i` dla którego `!(right[i] < left[i])` jest również wartość true, który `left[i] < right[i]`. W przeciwnym razie zwraca `left->size() < right->size()` używanej do testowania czy *po lewej stronie* był zamówiony przed *prawo* kiedy dwie listy są w porównaniu element po elemencie.

### <a name="example"></a>Przykład

```cpp
// cliext_list_operator_lt.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // assign to a new container
    cliext::list<wchar_t> c2;
    c2.push_back(L'a');
    c2.push_back(L'b');
    c2.push_back(L'd');

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

## <a name="op_lteq"></a> operator&lt;= (lista) (STL/CLR)

Mniejsze niż lub równe listy porównania.

### <a name="syntax"></a>Składnia

```cpp
template<typename Value>
    bool operator<=(list<Value>% left,
        list<Value>% right);
```

#### <a name="parameters"></a>Parametry

*left*<br/>
Po lewej stronie kontenera do porównania.

*right*<br/>
Kontener prawo do porównania.

### <a name="remarks"></a>Uwagi

Funkcja operator zwraca `!(right < left)`. Można go używać do testowania czy *po lewej stronie* nie są porządkowane po *odpowiednie* kiedy dwie listy są w porównaniu element po elemencie.

### <a name="example"></a>Przykład

```cpp
// cliext_list_operator_le.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // assign to a new container
    cliext::list<wchar_t> c2;
    c2.push_back(L'a');
    c2.push_back(L'b');
    c2.push_back(L'd');

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

## <a name="op_eq"></a> Operator == (lista) (STL/CLR)

Porównanie równego listy.

### <a name="syntax"></a>Składnia

```cpp
template<typename Value>
    bool operator==(list<Value>% left,
        list<Value>% right);
```

#### <a name="parameters"></a>Parametry

*left*<br/>
Po lewej stronie kontenera do porównania.

*right*<br/>
Kontener prawo do porównania.

### <a name="remarks"></a>Uwagi

Funkcja operator zwraca wartość true, tylko wtedy, gdy sekwencje kontrolowane przez *po lewej stronie* i *prawo* tę samą długość, a dla każdej pozycji `i`, `left[i] ==` `right[i]`. Można go używać do testowania czy *po lewej stronie* jest taka sama jak określona *prawo* kiedy dwie listy są w porównaniu element po elemencie.

### <a name="example"></a>Przykład

```cpp
// cliext_list_operator_eq.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // assign to a new container
    cliext::list<wchar_t> c2;
    c2.push_back(L'a');
    c2.push_back(L'b');
    c2.push_back(L'd');

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

## <a name="op_gt"></a> operator&gt; (lista) (STL/CLR)

Lista jest większa niż porównania.

### <a name="syntax"></a>Składnia

```cpp
template<typename Value>
    bool operator>(list<Value>% left,
        list<Value>% right);
```

#### <a name="parameters"></a>Parametry

*left*<br/>
Po lewej stronie kontenera do porównania.

*right*<br/>
Kontener prawo do porównania.

### <a name="remarks"></a>Uwagi

Funkcja operator zwraca `right` `<` `left`. Można go używać do testowania czy *po lewej stronie* są porządkowane po *prawo* kiedy dwie listy są w porównaniu element po elemencie.

### <a name="example"></a>Przykład

```cpp
// cliext_list_operator_gt.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // assign to a new container
    cliext::list<wchar_t> c2;
    c2.push_back(L'a');
    c2.push_back(L'b');
    c2.push_back(L'd');

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

## <a name="op_gteq"></a> operator&gt;= (lista) (STL/CLR)

Lista większa niż lub równe porównania.

### <a name="syntax"></a>Składnia

```cpp
template<typename Value>
    bool operator>=(list<Value>% left,
        list<Value>% right);
```

#### <a name="parameters"></a>Parametry

*left*<br/>
Po lewej stronie kontenera do porównania.

*right*<br/>
Kontener prawo do porównania.

### <a name="remarks"></a>Uwagi

Funkcja operator zwraca `!(left` `<` `right)`. Można go używać do testowania czy *po lewej stronie* nie był zamówiony przed *prawo* kiedy dwie listy są w porównaniu element po elemencie.

### <a name="example"></a>Przykład

```cpp
// cliext_list_operator_ge.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // assign to a new container
    cliext::list<wchar_t> c2;
    c2.push_back(L'a');
    c2.push_back(L'b');
    c2.push_back(L'd');

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