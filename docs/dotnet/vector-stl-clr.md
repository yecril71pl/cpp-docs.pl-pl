---
title: vector (STL/CLR)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- cliext::vector
- cliext::vector::assign
- cliext::vector::at
- cliext::vector::back
- cliext::vector::back_item
- cliext::vector::begin
- cliext::vector::capacity
- cliext::vector::clear
- cliext::vector::const_iterator
- cliext::vector::const_reference
- cliext::vector::const_reverse_iterator
- cliext::vector::difference_type
- cliext::vector::empty
- cliext::vector::end
- cliext::vector::erase
- cliext::vector::front
- cliext::vector::front_item
- cliext::vector::generic_container
- cliext::vector::generic_iterator
- cliext::vector::generic_reverse_iterator
- cliext::vector::generic_value
- cliext::vector::insert
- cliext::vector::iterator
- cliext::vector::operator=
- cliext::vector::operator
- cliext::vector::pop_back
- cliext::vector::push_back
- cliext::vector::rbegin
- cliext::vector::reference
- cliext::vector::rend
- cliext::vector::reserve
- cliext::vector::resize
- cliext::vector::reverse_iterator
- cliext::vector::size
- cliext::vector::size_type
- cliext::vector::swap
- cliext::vector::to_array
- cliext::vector::value_type
- cliext::vector::vector
helpviewer_keywords:
- vector class [STL/CLR]
- <cliext/vector> header [STL/CLR]
- <vector> header [STL/CLR]
- operator!= member [STL/CLR]
- operator< member [STL/CLR]
- operator<= member [STL/CLR]
- operator== member [STL/CLR]
- operator> (vector) member [STL/CLR]
- operator>= member [STL/CLR]
- assign member [STL/CLR]
- at member [STL/CLR]
- back member [STL/CLR]
- back_item member [STL/CLR]
- begin member [STL/CLR]
- capacity member [STL/CLR]
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
- operator= member [STL/CLR]
- operator member [STL/CLR]
- pop_back member [STL/CLR]
- push_back member [STL/CLR]
- rbegin member [STL/CLR]
- reference member [STL/CLR]
- rend member [STL/CLR]
- reserve member [STL/CLR]
- resize member [STL/CLR]
- reverse_iterator member [STL/CLR]
- size member [STL/CLR]
- size_type member [STL/CLR]
- swap member [STL/CLR]
- to_array member [STL/CLR]
- value_type member [STL/CLR]
- vector member [STL/CLR]
ms.assetid: f90060d5-097a-4e9d-9a26-a634b5b9c6c2
ms.openlocfilehash: c6a001797e90bd7381358abb16612926442e8d9f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371822"
---
# <a name="vector-stlclr"></a>vector (STL/CLR)

Klasa szablonu opisuje obiekt, który kontroluje sekwencję o różnej długości elementów, która ma dostęp losowy. Kontener `vector` służy do zarządzania sekwencji elementów jako ciągły blok magazynu. Blok jest implementowany jako tablica, która rośnie na żądanie.

W poniższym `GValue` opisie jest taka sama jak *Wartość,* chyba że `Value^`ten ostatni jest typem ref, w którym to przypadku jest .

## <a name="syntax"></a>Składnia

```cpp
template<typename Value>
    ref class vector
        :   public
        System::ICloneable,
        System::Collections::IEnumerable,
        System::Collections::ICollection,
        System::Collections::Generic::IEnumerable<GValue>,
        System::Collections::Generic::ICollection<GValue>,
        System::Collections::Generic::IList<GValue>,
        Microsoft::VisualC::StlClr::IVector<GValue>
    { ..... };
```

### <a name="parameters"></a>Parametry

*Wartość*<br/>
Typ elementu w kontrolowanej sekwencji.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<cliext/vector>

**Obszar nazw:** cliext

## <a name="declarations"></a>Deklaracje

|Definicja typu|Opis|
|---------------------|-----------------|
|[vector::const_iterator (STL/CLR)](#const_iterator)|Typ iteratora stałego dla kontrolowanej sekwencji.|
|[vector::const_reference (STL/CLR)](#const_reference)|Typ stałego odwołania do elementu.|
|[vector::const_reverse_iterator (STL/CLR)](#const_reverse_iterator)|Typ stałego iteratora wstecznego dla kontrolowanej sekwencji.|
|[vector::difference_type (STL/CLR)](#difference_type)|Typ odległości ze znakiem między dwoma elementami.|
|[vector::generic_container (STL/CLR)](#generic_container)|Typ interfejsu ogólnego kontenera.|
|[vector::generic_iterator (STL/CLR)](#generic_iterator)|Typ iteratora dla interfejsu ogólnego kontenera.|
|[vector::generic_reverse_iterator (STL/CLR)](#generic_reverse_iterator)|Typ odwrotnego iteratora dla ogólnego interfejsu kontenera.|
|[vector::generic_value (STL/CLR)](#generic_value)|Typ elementu dla interfejsu ogólnego kontenera.|
|[vector::iterator (STL/CLR)](#iterator)|Typ iteratora dla kontrolowanej sekwencji.|
|[vector::reference (STL/CLR)](#reference)|Typ odwołania do elementu.|
|[vector::reverse_iterator (STL/CLR)](#reverse_iterator)|Typ odwrotnego iteratora dla kontrolowanej sekwencji.|
|[vector::size_type (STL/CLR)](#size_type)|Typ odległości ze znakiem między dwoma elementami.|
|[vector::value_type (STL/CLR)](#value_type)|Typ elementu.|

|Funkcja elementów członkowskich|Opis|
|---------------------|-----------------|
|[vector::assign (STL/CLR)](#assign)|Zastępuje wszystkie elementy.|
|[vector::at (STL/CLR)](#at)|Uzyskuje dostęp do elementu w określonym położeniu.|
|[vector::back (STL/CLR)](#back)|Uzyskuje dostęp do ostatniego elementu.|
|[vector::begin (STL/CLR)](#begin)|Określa początek kontrolowanej sekwencji.|
|[vector::capacity (STL/CLR)](#capacity)|Raportuje rozmiar przydzielonego magazynu dla kontenera.|
|[vector::clear (STL/CLR)](#clear)|Usuwa wszystkie elementy.|
|[vector::empty (STL/CLR)](#empty)|Sprawdza, czy nie ma żadnych elementów.|
|[vector::end (STL/CLR)](#end)|Określa koniec kontrolowanej sekwencji.|
|[vector::erase (STL/CLR)](#erase)|Usuwa elementy z określonych pozycji.|
|[vector::front (STL/CLR)](#front)|Uzyskuje dostęp do pierwszego elementu.|
|[vector::insert (STL/CLR)](#insert)|Dodaje elementy w określonym położeniu.|
|[vector::pop_back (STL/CLR)](#pop_back)|Usuwa ostatni element.|
|[vector::push_back (STL/CLR)](#push_back)|Dodaje nowy ostatni element.|
|[vector::rbegin (STL/CLR)](#rbegin)|Wyznacza początek odwróconej kontrolowanej sekwencji.|
|[vector::rend (STL/CLR)](#rend)|Wyznacza koniec odwróconej kontrolowanej sekwencji.|
|[vector::reserve (STL/CLR)](#reserve)|Zapewnia minimalną pojemność wzrostu kontenera.|
|[vector::resize (STL/CLR)](#resize)|Zmienia liczbę elementów.|
|[vector::size (STL/CLR)](#size)|Liczy liczbę elementów.|
|[vector::swap (STL/CLR)](#swap)|Zamienia zawartości dwóch kontenerów.|
|[vector::to_array (STL/CLR)](#to_array)|Kopiuje kontrolowaną sekwencję do nowej tablicy.|
|[vector::vector (STL/CLR)](#vector)|Konstruuje obiekt kontenera.|

|Właściwość|Opis|
|--------------|-----------------|
|[vector::back_item (STL/CLR)](#back_item)|Uzyskuje dostęp do ostatniego elementu.|
|[vector::front_item (STL/CLR)](#front_item)|Uzyskuje dostęp do pierwszego elementu.|

|Operator|Opis|
|--------------|-----------------|
|[vector::operator= (STL/CLR)](#op_as)|Zastępuje kontrolowaną sekwencję.|
|[vector::operator(STL/CLR)](#op)|Uzyskuje dostęp do elementu w określonym położeniu.|
|[operator!= (wektor) (STL/CLR)](#op_neq)|Określa, czy `vector` obiekt nie jest `vector` równy innemu obiektowi.|
|[operator< (wektor) (STL/CLR)](#op_lt)|Określa, czy `vector` obiekt jest `vector` mniejszy niż inny obiekt.|
|[operator<= (wektor) (STL/CLR)](#op_lteq)|Określa, czy `vector` obiekt jest mniejszy lub `vector` równy innemu obiektowi.|
|[operator== (wektor) (STL/CLR)](#op_eq)|Określa, czy `vector` obiekt jest `vector` równy innemu obiektowi.|
|[operator> (vector) (STL/CLR)](#op_gt)|Określa, czy `vector` obiekt jest `vector` większy niż inny obiekt.|
|[operator>= (wektor) (STL/CLR)](#op_gteq)|Określa, czy `vector` obiekt jest większy lub `vector` równy innemu obiektowi.|

## <a name="interfaces"></a>Interfejsy

|Interface|Opis|
|---------------|-----------------|
|<xref:System.ICloneable>|Duplikowanie obiektu.|
|<xref:System.Collections.IEnumerable>|Sekwencja przez elementy.|
|<xref:System.Collections.ICollection>|Obsługa grupy elementów.|
|<xref:System.Collections.Generic.IEnumerable%601>|Sekwencjonowania za pomocą wpisanych elementów.|
|<xref:System.Collections.Generic.ICollection%601>|Obsługa grupy wpisanych elementów.|
|<xref:System.Collections.Generic.IList%601>|Obsługa uporządkowanej grupy wpisanych elementów.|
|Wartość<IVector\>|Obsługa kontenera ogólnego.|

## <a name="remarks"></a>Uwagi

Obiekt przydziela i zwalnia magazyn dla sekwencji kontroluje za pośrednictwem przechowywanej tablicy *Value* elementów, która rośnie na żądanie. Wzrost odbywa się w taki sposób, że koszt dołączania nowego elementu jest amortyzowany stały czas. Innymi słowy koszt dodawania elementów na końcu nie zwiększa się średnio, ponieważ długość kontrolowanej sekwencji staje się większa. W związku z tym wektor jest dobrym kandydatem do kontenera bazowego dla stosu klasy [szablonu (STL/CLR)](../dotnet/stack-stl-clr.md).

Obsługuje `vector` iteratory dostępu losowego, co oznacza, że można odwoływać się do elementu bezpośrednio biorąc pod uwagę `size() - 1` jego położenie numeryczne, licząc od zera dla pierwszego (przedni) element, do ostatniego (z tyłu) elementu. Oznacza to również, że wektor jest dobrym kandydatem do kontenera bazowego dla priority_queue klasy szablonu [(STL/CLR).](../dotnet/priority-queue-stl-clr.md)

Iterator wektorowy przechowuje dojście do skojarzonego obiektu wektorowego wraz z odchylenia elementu, który wyznacza. Iteratorów można używać tylko z skojarzonymi obiektami kontenera. Odchylenie elementu wektorowego jest taka sama jak jego położenie.

Wstawianie lub wymazywanie elementów można zmienić wartość elementu przechowywane w danej pozycji, więc wartość wyznaczona przez iteratora może również ulec zmianie. (Kontener może być konieczności kopiowania elementów w górę lub w dół, aby utworzyć otwór przed wstawieniem lub wypełnić otwór po wymazaniu). Niemniej jednak iterator wektorowy pozostaje ważny tak długo, jak `[0, size()]`długo jego odchylenie znajduje się w zakresie. Co więcej, prawidłowy iterator pozostaje niedoścignialny - można go użyć, aby uzyskać dostęp lub zmienić wartość `size()`elementu, którą wyznacza - tak długo, jak jego odchylenie nie jest równe .

Wymazywanie lub usuwanie elementu wywołuje destruktora dla jego przechowywanej wartości. Zniszczenie kontenera powoduje wymazanie wszystkich elementów. W związku z tym kontener, którego typ elementu jest ref klasy zapewnia, że żadne elementy przetrwać kontenera. Należy jednak zauważyć, że kontener uchwytów nie niszczy jego elementów.

## <a name="members"></a>Elementy członkowskie

## <a name="vectorassign-stlclr"></a><a name="assign"></a>wektor::assign (STL/CLR)

Zastępuje wszystkie elementy.

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

*Pierwszym*<br/>
Początek zakresu do wstawienia.

*Ostatnio*<br/>
Koniec zakresu do wstawienia.

*Prawo*<br/>
Wyliczenie do wstawienia.

*Val*<br/>
Wartość elementu do wstawienia.

### <a name="remarks"></a>Uwagi

Pierwsza funkcja elementu członkowskiego zastępuje kontrolowaną sekwencję powtórzeniem elementów *zliczania* wartości *val*. Służy do wypełnienia kontenera z elementów o tej samej wartości.

Jeśli `InIt` jest typem liczby całkowitej, druga funkcja `assign((size_type)first, (value_type)last)`elementu członkowskiego zachowuje się tak samo jak . W przeciwnym razie zastępuje kontrolowaną sekwencję sekwencją [`first`, `last`). Można go użyć, aby kontrolowana sekwencja skopiować inną sekwencję.

Funkcja trzeciego elementu członkowskiego zastępuje kontrolowaną sekwencję sekwencją wyznaczoną przez wyliczacz *po prawej stronie*. Można go użyć, aby kontrolowana sekwencja kopii sekwencji opisane przez wyliczacza.

### <a name="example"></a>Przykład

```cpp
// cliext_vector_assign.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// assign a repetition of values
    cliext::vector<wchar_t> c2;
    c2.assign(6, L'x');
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// assign an iterator range
    c2.assign(c1.begin(), c1.end() - 1);
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

## <a name="vectorat-stlclr"></a><a name="at"></a>wektor::at (STL/CLR)

Uzyskuje dostęp do elementu w określonym położeniu.

### <a name="syntax"></a>Składnia

```cpp
reference at(size_type pos);
```

#### <a name="parameters"></a>Parametry

*Poz*<br/>
Położenie elementu dostępu.

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca odwołanie do elementu kontrolowanej sekwencji w pozycji *poz*. Służy do odczytu lub zapisu elementu, którego pozycja znasz.

### <a name="example"></a>Przykład

```cpp
// cliext_vector_at.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display contents " a b c" using at
    for (int i = 0; i < c1.size(); ++i)
        System::Console::Write("{0} ", c1.at(i));
    System::Console::WriteLine();

// change an entry and redisplay
    c1.at(1) = L'x';
    for (int i = 0; i < c1.size(); ++i)
        System::Console::Write("{0} ", c1[i]);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
a x c
```

## <a name="vectorback-stlclr"></a><a name="back"></a>wektor::powrót (STL/CLR)

Uzyskuje dostęp do ostatniego elementu.

### <a name="syntax"></a>Składnia

```cpp
reference back();
```

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca odwołanie do ostatniego elementu kontrolowanej sekwencji, która musi być niepuściła. Służy do uzyskania dostępu do ostatniego elementu, gdy wiesz, że istnieje.

### <a name="example"></a>Przykład

```cpp
// cliext_vector_back.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
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

## <a name="vectorback_item-stlclr"></a><a name="back_item"></a>wektor::back_item (STL/CLR)

Uzyskuje dostęp do ostatniego elementu.

### <a name="syntax"></a>Składnia

```cpp
property value_type back_item;
```

### <a name="remarks"></a>Uwagi

Właściwość uzyskuje dostęp do ostatniego elementu kontrolowanej sekwencji, która musi być niepusta. Służy do odczytu lub zapisu ostatniego elementu, gdy wiesz, że istnieje.

### <a name="example"></a>Przykład

```cpp
// cliext_vector_back_item.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
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

## <a name="vectorbegin-stlclr"></a><a name="begin"></a>wektor::begin (STL/CLR)

Określa początek kontrolowanej sekwencji.

### <a name="syntax"></a>Składnia

```cpp
iterator begin();
```

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca iteratora dostępu losowego, który wyznacza pierwszy element kontrolowanej sekwencji lub tuż za końcem pustej sekwencji. Służy do uzyskania iteratora, który `current` wyznacza początek kontrolowanej sekwencji, ale jego stan może ulec zmianie, jeśli zmieni się długość kontrolowanej sekwencji.

### <a name="example"></a>Przykład

```cpp
// cliext_vector_begin.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// inspect first two items
    cliext::vector<wchar_t>::iterator it = c1.begin();
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

## <a name="vectorcapacity-stlclr"></a><a name="capacity"></a>wektor::pojemność (STL/CLR)

Raportuje rozmiar przydzielonego magazynu dla kontenera.

### <a name="syntax"></a>Składnia

```cpp
size_type capacity();
```

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca magazyn przydzielony obecnie do przechowywania kontrolowanej sekwencji, wartość co najmniej tak dużą jak [wektor::size (STL/CLR)](../dotnet/vector-size-stl-clr.md)`()`. Można go użyć do określenia, ile kontener może rosnąć, zanim musi ponownie przydzielić magazyn dla kontrolowanej sekwencji.

### <a name="example"></a>Przykład

```cpp
// cliext_vector_capacity.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display initial contents " a b c"
    for (int i = 0; i < c1.size(); ++i)
        System::Console::Write("{0} ", c1.at(i));
    System::Console::WriteLine();

// increase capacity
    cliext::vector<wchar_t>::size_type cap = c1.capacity();
    System::Console::WriteLine("capacity() = {0}, ok = {1}",
        cap, c1.size() <= cap);
    c1.reserve(cap + 5);
    System::Console::WriteLine("capacity() = {0}, ok = {1}",
        c1.capacity(), cap + 5 <= c1.capacity());
    return (0);
    }
```

```Output
a b c
capacity() = 4, ok = True
capacity() = 9, ok = True
```

## <a name="vectorclear-stlclr"></a><a name="clear"></a>wektor::clear (STL/CLR)

Usuwa wszystkie elementy.

### <a name="syntax"></a>Składnia

```cpp
void clear();
```

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego skutecznie wywołuje [wektor::erase (STL/CLR)](../dotnet/vector-erase-stl-clr.md) `(` [wektor::begin (STL/CLR)](../dotnet/vector-begin-stl-clr.md) `(),` [wektor::end (STL/CLR)](../dotnet/vector-end-stl-clr.md)`())`. Można go użyć, aby upewnić się, że kontrolowana sekwencja jest pusta.

### <a name="example"></a>Przykład

```cpp
// cliext_vector_clear.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
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

## <a name="vectorconst_iterator-stlclr"></a><a name="const_iterator"></a>wektor::const_iterator (STL/CLR)

Typ iteratora stałego dla kontrolowanej sekwencji.

### <a name="syntax"></a>Składnia

```cpp
typedef T2 const_iterator;
```

### <a name="remarks"></a>Uwagi

Typ opisuje obiekt nieokreślonego typu, `T2` który może służyć jako stały iterator dostępu losowego dla kontrolowanej sekwencji.

### <a name="example"></a>Przykład

```cpp
// cliext_vector_const_iterator.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display contents " a b c"
    cliext::vector<wchar_t>::const_iterator cit = c1.begin();
    for (; cit != c1.end(); ++cit)
        System::Console::Write("{0} ", *cit);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="vectorconst_reference-stlclr"></a><a name="const_reference"></a>wektor::const_reference (STL/CLR)

Typ stałego odwołania do elementu.

### <a name="syntax"></a>Składnia

```cpp
typedef value_type% const_reference;
```

### <a name="remarks"></a>Uwagi

Typ opisuje stałe odwołanie do elementu.

### <a name="example"></a>Przykład

```cpp
// cliext_vector_const_reference.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display initial contents " a b c"
    cliext::vector<wchar_t>::const_iterator cit = c1.begin();
    for (; cit != c1.end(); ++cit)
        {   // get a const reference to an element
        cliext::vector<wchar_t>::const_reference cref = *cit;
        System::Console::Write("{0} ", cref);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="vectorconst_reverse_iterator-stlclr"></a><a name="const_reverse_iterator"></a>wektor::const_reverse_iterator (STL/CLR)

Typ stałego iteratora wstecznego dla kontrolowanej sekwencji..

### <a name="syntax"></a>Składnia

```cpp
typedef T4 const_reverse_iterator;
```

### <a name="remarks"></a>Uwagi

Typ opisuje obiekt nieokreślonego typu, `T4` który może służyć jako stały iterator odwrotny dla kontrolowanej sekwencji.

### <a name="example"></a>Przykład

```cpp
// cliext_vector_const_reverse_iterator.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display contents " a b c" reversed
    cliext::vector<wchar_t>::const_reverse_iterator crit = c1.rbegin();
    cliext::vector<wchar_t>::const_reverse_iterator crend = c1.rend();
    for (; crit != crend; ++crit)
        System::Console::Write("{0} ", *crit);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
c b a
```

## <a name="vectordifference_type-stlclr"></a><a name="difference_type"></a>wektor::dfference_type (STL/CLR)

Typy podpisanej odległości między dwoma elementami.

### <a name="syntax"></a>Składnia

```cpp
typedef int difference_type;
```

### <a name="remarks"></a>Uwagi

Typ opisuje liczbę podpisanych elementów.

### <a name="example"></a>Przykład

```cpp
// cliext_vector_difference_type.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// compute positive difference
    cliext::vector<wchar_t>::difference_type diff = 0;
    for (cliext::vector<wchar_t>::iterator it = c1.begin();
        it != c1.end(); ++it) ++diff;
    System::Console::WriteLine("end()-begin() = {0}", diff);

// compute negative difference
    diff = 0;
    for (cliext::vector<wchar_t>::iterator it = c1.end();
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

## <a name="vectorempty-stlclr"></a><a name="empty"></a>wektor::empty (STL/CLR)

Sprawdza, czy nie ma żadnych elementów.

### <a name="syntax"></a>Składnia

```cpp
bool empty();
```

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca wartość true dla pustej kontrolowanej sekwencji. Jest odpowiednikiem [wektora::size (STL/CLR)](../dotnet/vector-size-stl-clr.md)`() == 0`. Służy do testowania, czy wektor jest pusty.

### <a name="example"></a>Przykład

```cpp
// cliext_vector_empty.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
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

## <a name="vectorend-stlclr"></a><a name="end"></a>wektor::end (STL/CLR)

Określa koniec kontrolowanej sekwencji.

### <a name="syntax"></a>Składnia

```cpp
iterator end();
```

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca iteratora dostępu losowego, który wskazuje tuż za końcem kontrolowanej sekwencji. Służy do uzyskania iteratora, który `current` wyznacza koniec kontrolowanej sekwencji, ale jego stan może ulec zmianie, jeśli zmieni się długość kontrolowanej sekwencji.

### <a name="example"></a>Przykład

```cpp
// cliext_vector_end.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// inspect last two items
    cliext::vector<wchar_t>::iterator it = c1.end();
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

## <a name="vectorerase-stlclr"></a><a name="erase"></a>wektor::wymazywanie (STL/CLR)

Usuwa elementy z określonych pozycji.

### <a name="syntax"></a>Składnia

```cpp
iterator erase(iterator where);
iterator erase(iterator first, iterator last);
```

#### <a name="parameters"></a>Parametry

*Pierwszym*<br/>
Początek zakresu do usunięcia.

*Ostatnio*<br/>
Koniec zakresu do usunięcia.

*where*<br/>
Element do usunięcia.

### <a name="remarks"></a>Uwagi

Funkcja pierwszego elementu członkowskiego usuwa element kontrolowanej sekwencji wskazywu, na *który*. Można go użyć do usunięcia pojedynczego elementu.

Funkcja drugiego elementu członkowskiego usuwa elementy kontrolowanej sekwencji w zakresie [`first`, `last`). Służy do usuwania elementów zerowych lub bardziej ciągłych.

Obie funkcje członkowskie zwracają iteratora, który wyznacza pierwszy element pozostały poza wszystkie elementy usunięte lub [wektor::end (STL/CLR),](../dotnet/vector-end-stl-clr.md) `()` jeśli taki element nie istnieje.

Podczas wymazywania elementów liczba kopii elementów jest liniowa w liczbie elementów między końcem wymazywania a zbliżającym się końcem sekwencji. (Podczas wymazywania jednego lub więcej elementów na obu końcach sekwencji nie występują żadne kopie elementów).

### <a name="example"></a>Przykład

```cpp
// cliext_vector_erase.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
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
    cliext::vector<wchar_t>::iterator it = c1.end();
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

## <a name="vectorfront-stlclr"></a><a name="front"></a>wektor::przód (STL/CLR)

Uzyskuje dostęp do pierwszego elementu.

### <a name="syntax"></a>Składnia

```cpp
reference front();
```

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca odwołanie do pierwszego elementu kontrolowanej sekwencji, która musi być niepusta. Służy do odczytu lub zapisu pierwszego elementu, gdy wiesz, że istnieje.

### <a name="example"></a>Przykład

```cpp
// cliext_vector_front.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
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

## <a name="vectorfront_item-stlclr"></a><a name="front_item"></a>wektor::front_item (STL/CLR)

Uzyskuje dostęp do pierwszego elementu.

### <a name="syntax"></a>Składnia

```cpp
property value_type front_item;
```

### <a name="remarks"></a>Uwagi

Właściwość uzyskuje dostęp do pierwszego elementu kontrolowanej sekwencji, która musi być niepuste. Służy do odczytu lub zapisu pierwszego elementu, gdy wiesz, że istnieje.

### <a name="example"></a>Przykład

```cpp
// cliext_vector_front_item.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
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

## <a name="vectorgeneric_container-stlclr"></a><a name="generic_container"></a>wektor::generic_container (STL/CLR)

Typ interfejsu ogólnego kontenera.

### <a name="syntax"></a>Składnia

```cpp
typedef Microsoft::VisualC::StlClr::
    IVector<generic_value>
    generic_container;
```

### <a name="remarks"></a>Uwagi

Typ opisuje ogólny interfejs dla tej klasy kontenera szablonu.

### <a name="example"></a>Przykład

```cpp
// cliext_vector_generic_container.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// construct a generic container
    cliext::vector<wchar_t>::generic_container^ gc1 = %c1;
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

## <a name="vectorgeneric_iterator-stlclr"></a><a name="generic_iterator"></a>wektor::generic_iterator (STL/CLR)

Typ iteratora do użycia z interfejsem ogólnym dla kontenera.

### <a name="syntax"></a>Składnia

```cpp
typedef Microsoft::VisualC::StlClr::Generic::
    ContainerRandomAccessIterator<generic_value>
    generic_iterator;
```

### <a name="remarks"></a>Uwagi

Typ opisuje ogólny iterator, który może być używany z interfejsem ogólnym dla tej klasy kontenera szablonu.

### <a name="example"></a>Przykład

```cpp
// cliext_vector_generic_iterator.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// construct a generic container
    cliext::vector<wchar_t>::generic_container^ gc1 = %c1;
    for each (wchar_t elem in gc1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// modify generic and display original
    cliext::vector<wchar_t>::generic_iterator gcit = gc1->begin();
    cliext::vector<wchar_t>::generic_value gcval = *gcit;
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

## <a name="vectorgeneric_reverse_iterator-stlclr"></a><a name="generic_reverse_iterator"></a>wektor::generic_reverse_iterator (STL/CLR)

Typ iteratora wstecznego do użycia z interfejsem ogólnym dla kontenera.

### <a name="syntax"></a>Składnia

```cpp
typedef Microsoft::VisualC::StlClr::Generic::
    ReverseRandomAccessIterator<generic_value> generic_reverse_iterator;
```

### <a name="remarks"></a>Uwagi

Typ opisuje ogólny iterator odwrotny, który może być używany z interfejsem ogólnym dla tej klasy kontenera szablonu.

### <a name="example"></a>Przykład

```cpp
// cliext_vector_generic_reverse_iterator.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// construct a generic container
    cliext::vector<wchar_t>::generic_container^ gc1 = %c1;
    for each (wchar_t elem in gc1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// modify generic and display original
    cliext::vector<wchar_t>::generic_reverse_iterator gcit = gc1->rbegin();
    cliext::vector<wchar_t>::generic_value gcval = *gcit;
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

## <a name="vectorgeneric_value-stlclr"></a><a name="generic_value"></a>wektor::generic_value (STL/CLR)

Typ elementu do użycia z interfejsem ogólnym dla kontenera.

### <a name="syntax"></a>Składnia

```cpp
typedef GValue generic_value;
```

### <a name="remarks"></a>Uwagi

Typ opisuje obiekt typu, `GValue` który opisuje wartość elementu przechowywanego do użytku z interfejsem ogólnym dla tej klasy kontenera szablonu.

### <a name="example"></a>Przykład

```cpp
// cliext_vector_generic_value.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// construct a generic container
    cliext::vector<wchar_t>::generic_container^ gc1 = %c1;
    for each (wchar_t elem in gc1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// modify generic and display original
    cliext::vector<wchar_t>::generic_iterator gcit = gc1->begin();
    cliext::vector<wchar_t>::generic_value gcval = *gcit;
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

## <a name="vectorinsert-stlclr"></a><a name="insert"></a>wektor::insert (STL/CLR)

Dodaje elementy w określonym położeniu.

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

*Pierwszym*<br/>
Początek zakresu do wstawienia.

*Ostatnio*<br/>
Koniec zakresu do wstawienia.

*Prawo*<br/>
Wyliczenie do wstawienia.

*Val*<br/>
Wartość elementu do wstawienia.

*where*<br/>
Gdzie w pojemniku wstawić przed.

### <a name="remarks"></a>Uwagi

Każda z funkcji elementów członkowskich wstawia, przed elementem wskazanym przez *where* in the controlled sequence, sekwencja określona przez pozostałe argumenty.

Pierwsza funkcja elementu członkowskiego wstawia element o *wartości val* i zwraca iterator, który wyznacza nowo wstawiony element. Służy do wstawiania pojedynczego elementu przed miejscem wyznaczonym przez iteratora.

Druga funkcja elementu członkowskiego wstawia powtórzenie elementów *zliczania* *wartości val*. Służy do wstawiania zero lub więcej ciągłych elementów, które są wszystkie kopie tej samej wartości.

Jeśli `InIt` jest typem liczby całkowitej, funkcja trzeciego `insert(where, (size_type)first, (value_type)last)`elementu członkowskiego zachowuje się tak samo jak . W przeciwnym razie wstawia sekwencję [`first`, `last`). Służy do wstawiania zero lub więcej elementów ciągłych skopiowanych z innej sekwencji.

Funkcja czwartego elementu członkowskiego wstawia sekwencję wyznaczoną przez *prawo*. Służy do wstawiania sekwencji opisane przez wyliczacza.

Podczas wstawiania pojedynczego elementu liczba kopii elementów jest liniowa w liczbie elementów między punktem wstawiania a zbliżającym się końcem sekwencji. (Podczas wstawiania jednego lub więcej elementów na obu końcach sekwencji nie występują żadne kopie elementów). Jeśli `InIt` jest iteratorem wejściowym, funkcja trzeciego elementu członkowskiego skutecznie wykonuje pojedyncze wstawianie dla każdego elementu w sekwencji. W przeciwnym razie `N` podczas wstawiania elementów liczba `N` kopii elementów jest liniowa oraz liczba elementów między punktem wstawiania a zbliżającym się końcem sekwencji.

### <a name="example"></a>Przykład

```cpp
// cliext_vector_insert.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// insert a single value using iterator
    cliext::vector<wchar_t>::iterator it = c1.begin();
    System::Console::WriteLine("insert(begin()+1, L'x') = {0}",
        *c1.insert(++it, L'x'));
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// insert a repetition of values
    cliext::vector<wchar_t> c2;
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

## <a name="vectoriterator-stlclr"></a><a name="iterator"></a>wektor::iterator (STL/CLR)

Typ iteratora dla kontrolowanej sekwencji.

### <a name="syntax"></a>Składnia

```cpp
typedef T1 iterator;
```

### <a name="remarks"></a>Uwagi

Typ opisuje obiekt nieokreślonego typu, `T1` który może służyć jako iterator dostępu losowego dla kontrolowanej sekwencji.

### <a name="example"></a>Przykład

```cpp
// cliext_vector_iterator.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display contents " a b c"
    cliext::vector<wchar_t>::iterator it = c1.begin();
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

## <a name="vectoroperator-stlclr"></a><a name="op_as"></a>wektor::operator= (STL/CLR)

Zastępuje kontrolowaną sekwencję.

### <a name="syntax"></a>Składnia

```cpp
vector<Value>% operator=(vector<Value>% right);
```

#### <a name="parameters"></a>Parametry

*Prawo*<br/>
Kontener do skopiowania.

### <a name="remarks"></a>Uwagi

Operator elementu członkowskiego kopiuje *prawo* `*this`do obiektu, a następnie zwraca . Można go użyć do zastąpienia kontrolowanej sekwencji kopią kontrolowanej sekwencji *w prawej*.

### <a name="example"></a>Przykład

```cpp
// cliext_vector_operator_as.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// assign to a new container
    cliext::vector<wchar_t> c2;
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

## <a name="vectoroperatorstlclr"></a><a name="op"></a>wektor::operator(STL/CLR)

Uzyskuje dostęp do elementu w określonym położeniu.

### <a name="syntax"></a>Składnia

```cpp
reference operator[](size_type pos);
```

#### <a name="parameters"></a>Parametry

*Poz*<br/>
Położenie elementu dostępu.

### <a name="remarks"></a>Uwagi

Operator elementu członkowskiego zwraca referene do elementu w pozycji *pos*. Służy do uzyskiwania dostępu do elementu, którego pozycję znasz.

### <a name="example"></a>Przykład

```cpp
// cliext_vector_operator_sub.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display contents " a b c" using subscripting
    for (int i = 0; i < c1.size(); ++i)
        System::Console::Write("{0} ", c1[i]);
    System::Console::WriteLine();

// change an entry and redisplay
    c1[1] = L'x';
    for (int i = 0; i < c1.size(); ++i)
        System::Console::Write("{0} ", c1[i]);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
a x c
```

## <a name="vectorpop_back-stlclr"></a><a name="pop_back"></a>wektor::pop_back (STL/CLR)

Usuwa ostatni element.

### <a name="syntax"></a>Składnia

```cpp
void pop_back();
```

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego usuwa ostatni element kontrolowanej sekwencji, który musi być niepuste. Można go użyć, aby skrócić wektor o jeden element z tyłu.

### <a name="example"></a>Przykład

```cpp
// cliext_vector_pop_back.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
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

## <a name="vectorpush_back-stlclr"></a><a name="push_back"></a>wektor::push_back (STL/CLR)

Dodaje nowy ostatni element.

### <a name="syntax"></a>Składnia

```cpp
void push_back(value_type val);
```

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego wstawia `val` element o wartości na końcu kontrolowanej sekwencji. Służy do dołączania innego elementu do wektora.

### <a name="example"></a>Przykład

```cpp
// cliext_vector_push_back.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
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

## <a name="vectorrbegin-stlclr"></a><a name="rbegin"></a>wektor::rbegin (STL/CLR)

Wyznacza początek odwróconej kontrolowanej sekwencji.

### <a name="syntax"></a>Składnia

```cpp
reverse_iterator rbegin();
```

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca odwrotnej iteratora, który wyznacza ostatni element kontrolowanej sekwencji lub tuż poza początku pustej sekwencji. W związku z `beginning` tym wyznacza odwrotnej sekwencji. Służy do uzyskania iteratora, który `current` wyznacza początek kontrolowanej sekwencji widoczne w odwrotnej kolejności, ale jego stan może ulec zmianie, jeśli zmienia się długość kontrolowanej sekwencji.

### <a name="example"></a>Przykład

```cpp
// cliext_vector_rbegin.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// inspect first two items in reversed sequence
    cliext::vector<wchar_t>::reverse_iterator rit = c1.rbegin();
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

## <a name="vectorreference-stlclr"></a><a name="reference"></a>wektor::odwołanie (STL/CLR)

Typ odwołania do elementu.

### <a name="syntax"></a>Składnia

```cpp
typedef value_type% reference;
```

### <a name="remarks"></a>Uwagi

Typ opisuje odwołanie do elementu.

### <a name="example"></a>Przykład

```cpp
// cliext_vector_reference.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display initial contents " a b c"
    cliext::vector<wchar_t>::iterator it = c1.begin();
    for (; it != c1.end(); ++it)
        {   // get a reference to an element
        cliext::vector<wchar_t>::reference ref = *it;
        System::Console::Write("{0} ", ref);
        }
    System::Console::WriteLine();

// modify contents " a b c"
    for (it = c1.begin(); it != c1.end(); ++it)
        {   // get a reference to an element
        cliext::vector<wchar_t>::reference ref = *it;

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

## <a name="vectorrend-stlclr"></a><a name="rend"></a>wektor::rend (STL/CLR)

Wyznacza koniec odwróconej kontrolowanej sekwencji.

### <a name="syntax"></a>Składnia

```cpp
reverse_iterator rend();
```

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca odwrotnej iteratora, który wskazuje tuż poza początek kontrolowanej sekwencji. W związku z `end` tym wyznacza odwrotnej sekwencji. Służy do uzyskania iteratora, który `current` wyznacza koniec kontrolowanej sekwencji widoczne w odwrotnej kolejności, ale jego stan może ulec zmianie, jeśli zmienia się długość kontrolowanej sekwencji.

### <a name="example"></a>Przykład

```cpp
// cliext_vector_rend.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// inspect first two items
    cliext::vector<wchar_t>::reverse_iterator rit = c1.rend();
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

## <a name="vectorreserve-stlclr"></a><a name="reserve"></a>wektor::rezerwa (STL/CLR)

Zapewnia minimalną pojemność wzrostu kontenera.

### <a name="syntax"></a>Składnia

```cpp
void reserve(size_type count);
```

#### <a name="parameters"></a>Parametry

*Liczba*<br/>
Nowa minimalna pojemność kontenera.

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego `capacity()` zapewnia, że odtąd zwraca co najmniej *liczyć*. Można go użyć, aby upewnić się, że kontener nie trzeba ponownie przydzielać magazynu dla kontrolowanej sekwencji, dopóki nie wzrosła do określonego rozmiaru.

### <a name="example"></a>Przykład

```cpp
// cliext_vector_reserve.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display initial contents " a b c"
    for (int i = 0; i < c1.size(); ++i)
        System::Console::Write("{0} ", c1.at(i));
    System::Console::WriteLine();

// increase capacity
    cliext::vector<wchar_t>::size_type cap = c1.capacity();
    System::Console::WriteLine("capacity() = {0}, ok = {1}",
        cap, c1.size() <= cap);
    c1.reserve(cap + 5);
    System::Console::WriteLine("capacity() = {0}, ok = {1}",
        c1.capacity(), cap + 5 <= c1.capacity());
    return (0);
    }
```

```Output
a b c
capacity() = 4, ok = True
capacity() = 9, ok = True
```

## <a name="vectorresize-stlclr"></a><a name="resize"></a>wektor::resize (STL/CLR)

Zmienia liczbę elementów.

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

Funkcje członkowskie zapewniają, że [wektor::size (STL/CLR)](../dotnet/vector-size-stl-clr.md) `()` zwraca *new_size*. Jeśli musi wydłużyć kontrolowaną sekwencję, pierwsza `value_type()`funkcja elementu członkowskiego dołącza elementy z wartością, podczas gdy druga funkcja elementu członkowskiego dołącza elementy o *wartości val*. Aby skrócenie kontrolowanej sekwencji, obie funkcje członkowskie skutecznie wymazały [czasy ostatniego elementu::size (STL/CLR).](../dotnet/vector-size-stl-clr.md) `() -` `new_size` Można go użyć, aby upewnić się, że kontrolowana sekwencja ma rozmiar *new_size*, przycinanie lub dopełnianie bieżącej kontrolowanej sekwencji.

### <a name="example"></a>Przykład

```cpp
// cliext_vector_resize.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
// construct an empty container and pad with default values
    cliext::vector<wchar_t> c1;
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

## <a name="vectorreverse_iterator-stlclr"></a><a name="reverse_iterator"></a>wektor::reverse_iterator (STL/CLR)

Typ odwrotnego iteratora dla kontrolowanej sekwencji.

### <a name="syntax"></a>Składnia

```cpp
typedef T3 reverse_iterator;
```

### <a name="remarks"></a>Uwagi

Typ opisuje obiekt nieokreślonego typu, `T3` który może służyć jako odwrotnej iterator dla kontrolowanej sekwencji.

### <a name="example"></a>Przykład

```cpp
// cliext_vector_reverse_iterator.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display contents " a b c" reversed
    cliext::vector<wchar_t>::reverse_iterator rit = c1.rbegin();
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

## <a name="vectorsize-stlclr"></a><a name="size"></a>wektor::size (STL/CLR)

Liczy liczbę elementów.

### <a name="syntax"></a>Składnia

```cpp
size_type size();
```

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca długość kontrolowanej sekwencji. Służy do określenia liczby elementów aktualnie w kontrolowanej sekwencji. Jeśli zależy Ci tylko na tym, czy sekwencja ma rozmiar niezerowy, zobacz [wektor::empty (STL/CLR)](../dotnet/vector-empty-stl-clr.md)`()`.

### <a name="example"></a>Przykład

```cpp
// cliext_vector_size.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
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

## <a name="vectorsize_type-stlclr"></a><a name="size_type"></a>wektor::size_type (STL/CLR)

Typ odległości ze znakiem między dwoma elementami.

### <a name="syntax"></a>Składnia

```cpp
typedef int size_type;
```

### <a name="remarks"></a>Uwagi

Typ opisuje liczbę elementów nieujemnych.

### <a name="example"></a>Przykład

```cpp
// cliext_vector_size_type.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// compute positive difference
    cliext::vector<wchar_t>::size_type diff = c1.end() - c1.begin();
    System::Console::WriteLine("end()-begin() = {0}", diff);
    return (0);
    }
```

```Output
a b c
end()-begin() = 3
```

## <a name="vectorswap-stlclr"></a><a name="swap"></a>wektor::swap (STL/CLR)

Zamienia zawartości dwóch kontenerów.

### <a name="syntax"></a>Składnia

```cpp
void swap(vector<Value>% right);
```

#### <a name="parameters"></a>Parametry

*Prawo*<br/>
Kontener do wymiany zawartości z.

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zamienia kontrolowane `*this` sekwencje między i *po prawej stronie*. Robi to w stałym czasie i nie zgłasza żadnych wyjątków. Można go używać jako szybki sposób wymiany zawartości dwóch kontenerów.

### <a name="example"></a>Przykład

```cpp
// cliext_vector_swap.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// construct another container with repetition of values
    cliext::vector<wchar_t> c2(5, L'x');
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

## <a name="vectorto_array-stlclr"></a><a name="to_array"></a>wektor::to_array (STL/CLR)

Kopiuje kontrolowaną sekwencję do nowej tablicy.

### <a name="syntax"></a>Składnia

```cpp
cli::array<Value>^ to_array();
```

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca tablicę zawierającą kontrolowaną sekwencję. Służy do uzyskania kopii kontrolowanej sekwencji w formie tablicy.

### <a name="example"></a>Przykład

```cpp
// cliext_vector_to_array.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
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

## <a name="vectorvalue_type-stlclr"></a><a name="value_type"></a>wektor::value_type (STL/CLR)

Typ elementu.

### <a name="syntax"></a>Składnia

```cpp
typedef Value value_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem parametru szablonu *Value*.

### <a name="example"></a>Przykład

```cpp
// cliext_vector_value_type.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display contents " a b c" using value_type
    for (cliext::vector<wchar_t>::iterator it = c1.begin();
        it != c1.end(); ++it)
        {   // store element in value_type object
        cliext::vector<wchar_t>::value_type val = *it;

        System::Console::Write("{0} ", val);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="vectorvector-stlclr"></a><a name="vector"></a>wektor::wektor (STL/CLR)

Konstruuje obiekt kontenera.

### <a name="syntax"></a>Składnia

```cpp
vector();
vector(vector<Value>% right);
vector(vector<Value>^ right);
explicit vector(size_type count);
vector(size_type count, value_type val);
template<typename InIt>
    vector(InIt first, InIt last);
vector(System::Collections::Generic::IEnumerable<Value>^ right);
```

#### <a name="parameters"></a>Parametry

*Liczba*<br/>
Liczba elementów do wstawienia.

*Pierwszym*<br/>
Początek zakresu do wstawienia.

*Ostatnio*<br/>
Koniec zakresu do wstawienia.

*Prawo*<br/>
Obiekt lub zakres do wstawienia.

*Val*<br/>
Wartość elementu do wstawienia.

### <a name="remarks"></a>Uwagi

Konstruktor:

`vector();`

inicjuje kontrolowaną sekwencję bez elementów. Służy do określania pustej początkowej kontrolowanej sekwencji.

Konstruktor:

`vector(vector<Value>% right);`

inicjuje kontrolowaną sekwencję`right.begin()` `right.end()`z sekwencją [ , ). Służy do określenia początkowej kontrolowanej sekwencji, która jest kopią sekwencji kontrolowanej przez obiekt wektorowy *po prawej stronie*.

Konstruktor:

`vector(vector<Value>^ right);`

inicjuje kontrolowaną sekwencję`right->begin()` `right->end()`z sekwencją [ , ). Służy do określenia początkowej kontrolowanej sekwencji, która jest kopią sekwencji kontrolowanej przez obiekt wektorowy, którego uchwyt jest *właściwy*.

Konstruktor:

`explicit vector(size_type count);`

inicjuje kontrolowaną sekwencję z `value_type()`elementami *zliczania* każdego z wartością . Służy do wypełnienia kontenera z elementów wszystkich o wartości domyślnej.

Konstruktor:

`vector(size_type count, value_type val);`

inicjuje kontrolowaną sekwencję z elementami *zliczania* każdego z *wartością val*. Służy do wypełnienia kontenera z elementów o tej samej wartości.

Konstruktor:

`template<typename InIt>`

`vector(InIt first, InIt last);`

inicjuje kontrolowaną sekwencję`first` `last`z sekwencją [ , ). Można go użyć, aby kontrolowana sekwencja była kopią innej sekwencji.

Konstruktor:

`vector(System::Collections::Generic::IEnumerable<Value>^ right);`

inicjuje kontrolowaną sekwencję z sekwencją wyznaczoną przez *prawo*wylicznika . Można go użyć, aby kontrolowana sekwencja kopii innej sekwencji opisane przez wyliczacza.

### <a name="example"></a>Przykład

```cpp
// cliext_vector_construct.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
// construct an empty container
    cliext::vector<wchar_t> c1;
    System::Console::WriteLine("size() = {0}", c1.size());

// construct with a repetition of default values
    cliext::vector<wchar_t> c2(3);
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", (int)elem);
    System::Console::WriteLine();

// construct with a repetition of values
    cliext::vector<wchar_t> c3(6, L'x');
    for each (wchar_t elem in c3)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// construct with an iterator range
    cliext::vector<wchar_t>::iterator it = c3.end();
    cliext::vector<wchar_t> c4(c3.begin(), --it);
    for each (wchar_t elem in c4)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// construct with an enumeration
    cliext::vector<wchar_t> c5(   // NOTE: cast is not needed
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c3);
    for each (wchar_t elem in c5)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// construct by copying another container
    cliext::vector<wchar_t> c7(c3);
    for each (wchar_t elem in c7)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// construct by copying a container handle
    cliext::vector<wchar_t> c8(%c3);
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

## <a name="operator-vector-stlclr"></a><a name="op_neq"></a>operator!= (wektor) (STL/CLR)

Wektor nie jest równe porównanie.

### <a name="syntax"></a>Składnia

```cpp
template<typename Value>
    bool operator!=(vector<Value>% left,
        vector<Value>% right);
```

#### <a name="parameters"></a>Parametry

*Lewej*<br/>
Lewy pojemnik do porównania.

*Prawo*<br/>
Odpowiedni pojemnik do porównania.

### <a name="remarks"></a>Uwagi

Funkcja operatora `!(left == right)`zwraca . Służy do testowania, czy *left* nie jest uporządkowany tak samo jak *prawo,* gdy dwa wektory są porównywane element po elemencie.

### <a name="example"></a>Przykład

```cpp
// cliext_vector_operator_ne.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// assign to a new container
    cliext::vector<wchar_t> c2;
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

## <a name="operatorlt-vector-stlclr"></a><a name="op_lt"></a>operator&lt; (wektor) (STL/CLR)

Wektor mniej niż porównanie.

### <a name="syntax"></a>Składnia

```cpp
template<typename Value>
    bool operator<(vector<Value>% left,
        vector<Value>% right);
```

#### <a name="parameters"></a>Parametry

*Lewej*<br/>
Lewy pojemnik do porównania.

*Prawo*<br/>
Odpowiedni pojemnik do porównania.

### <a name="remarks"></a>Uwagi

Funkcja operatora zwraca wartość true, `i` jeśli `!(right[i] < left[i])` dla najniższej `left[i] < right[i]`pozycji, dla której jest również prawdą, że . W przeciwnym `left->size() < right->size()` razie zwraca Używasz go do testowania, czy *left* jest uporządkowany przed *prawo,* gdy dwa wektory są porównywane element po elemencie.

### <a name="example"></a>Przykład

```cpp
// cliext_vector_operator_lt.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// assign to a new container
    cliext::vector<wchar_t> c2;
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

## <a name="operatorlt-vector-stlclr"></a><a name="op_lteq"></a>operator&lt;= (wektor) (STL/CLR)

Wektor mniejsze niż lub równe porównanie.

### <a name="syntax"></a>Składnia

```cpp
template<typename Value>
    bool operator<=(vector<Value>% left,
        vector<Value>% right);
```

#### <a name="parameters"></a>Parametry

*Lewej*<br/>
Lewy pojemnik do porównania.

*Prawo*<br/>
Odpowiedni pojemnik do porównania.

### <a name="remarks"></a>Uwagi

Funkcja operatora `!(right < left)`zwraca . Służy do testowania, czy *left* nie jest uporządkowany po *prawej stronie,* gdy dwa wektory są porównywane element po elemencie.

### <a name="example"></a>Przykład

```cpp
// cliext_vector_operator_le.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// assign to a new container
    cliext::vector<wchar_t> c2;
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

## <a name="operator-vector-stlclr"></a><a name="op_eq"></a>operator== (wektor) (STL/CLR)

Wektor równe porównanie.

### <a name="syntax"></a>Składnia

```cpp
template<typename Value>
    bool operator==(vector<Value>% left,
        vector<Value>% right);
```

#### <a name="parameters"></a>Parametry

*Lewej*<br/>
Lewy pojemnik do porównania.

*Prawo*<br/>
Odpowiedni pojemnik do porównania.

### <a name="remarks"></a>Uwagi

Funkcja operatora zwraca wartość true tylko wtedy, gdy sekwencje kontrolowane przez `i` *lewą* i *prawą stronę* mają taką samą długość, a dla każdej pozycji `left[i] ==` `right[i]`. Służy do testowania, czy *left* jest uporządkowany tak samo jak *prawo,* gdy dwa wektory są porównywane element po elemencie.

### <a name="example"></a>Przykład

```cpp
// cliext_vector_operator_eq.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// assign to a new container
    cliext::vector<wchar_t> c2;
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

## <a name="operatorgt-vector-stlclr"></a><a name="op_gt"></a>operator&gt; (wektor) (STL/CLR)

Wektor większy niż porównanie.

### <a name="syntax"></a>Składnia

```cpp
template<typename Value>
    bool operator>(vector<Value>% left,
        vector<Value>% right);
```

#### <a name="parameters"></a>Parametry

*Lewej*<br/>
Lewy pojemnik do porównania.

*Prawo*<br/>
Odpowiedni pojemnik do porównania.

### <a name="remarks"></a>Uwagi

Funkcja operatora `right` `<` `left`zwraca . Służy do testowania, czy *left* jest uporządkowany po *prawej stronie,* gdy dwa wektory są porównywane element po elemencie.

### <a name="example"></a>Przykład

```cpp
// cliext_vector_operator_gt.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// assign to a new container
    cliext::vector<wchar_t> c2;
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

## <a name="operatorgt-vector-stlclr"></a><a name="op_gteq"></a>operator&gt;= (wektor) (STL/CLR)

Wektor większe niż lub równe porównanie.

### <a name="syntax"></a>Składnia

```cpp
template<typename Value>
    bool operator>=(vector<Value>% left,
        vector<Value>% right);
```

#### <a name="parameters"></a>Parametry

*Lewej*<br/>
Lewy pojemnik do porównania.

*Prawo*<br/>
Odpowiedni pojemnik do porównania.

### <a name="remarks"></a>Uwagi

Funkcja operatora `!(left < right)`zwraca . Służy do testowania, czy *left* nie jest uporządkowany przed *prawo,* gdy dwa wektory są porównywane element po elemencie.

### <a name="example"></a>Przykład

```cpp
// cliext_vector_operator_ge.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// assign to a new container
    cliext::vector<wchar_t> c2;
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
