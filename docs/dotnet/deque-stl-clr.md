---
title: deque (STL/CLR)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- cliext::deque
- cliext::deque::assign
- cliext::deque::at
- cliext::deque::back
- cliext::deque::back_item
- cliext::deque::begin
- cliext::deque::clear
- cliext::deque::const_iterator
- cliext::deque::const_reference
- cliext::deque::const_reverse_iterator
- cliext::deque::deque
- cliext::deque::difference_type
- cliext::deque::empty
- cliext::deque::end
- cliext::deque::erase
- cliext::deque::front
- cliext::deque::front_item
- cliext::deque::generic_container
- cliext::deque::generic_iterator
- cliext::deque::generic_reverse_iterator
- cliext::deque::generic_value
- cliext::deque::insert
- cliext::deque::iterator
- cliext::deque::operator!=
- cliext::deque::operator[]
- cliext::deque::pop_back
- cliext::deque::pop_front
- cliext::deque::push_back
- cliext::deque::push_front
- cliext::deque::rbegin
- cliext::deque::reference
- cliext::deque::rend
- cliext::deque::resize
- cliext::deque::reverse_iterator
- cliext::deque::size
- cliext::deque::size_type
- cliext::deque::swap
- cliext::deque::to_array
- cliext::deque::value_type
- cliext::deque::operator<
- cliext::deque::operator<=
- cliext::deque::operator=
- cliext::deque::operator==
- cliext::deque::operator>
- cliext::deque::operator>=
helpviewer_keywords:
- deque class [STL/CLR]
- <deque> header [STL/CLR]
- <cliext/deque> header [STL/CLR]
- assign member [STL/CLR]
- assign member [STL/CLR]
- at member [STL/CLR]
- back member [STL/CLR]
- back_item member [STL/CLR]
- begin member [STL/CLR]
- clear member [STL/CLR]
- const_iterator member [STL/CLR]
- const_reference member [STL/CLR]
- const_reverse_iterator member [STL/CLR]
- deque member [STL/CLR]
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
- operator!= member [STL/CLR]
- operator member [] [STL/CLR]
- pop_back member [STL/CLR]
- pop_front member [STL/CLR]
- push_back member [STL/CLR]
- push_front member [STL/CLR]
- rbegin member [STL/CLR]
- reference member [STL/CLR]
- rend member [STL/CLR]
- resize member [STL/CLR]
- reverse_iterator member [STL/CLR]
- size member [STL/CLR]
- size_type member [STL/CLR]
- swap member [STL/CLR]
- to_array member [STL/CLR]
- value_type member [STL/CLR]
- operator< member [STL/CLR]
- operator<= member [STL/CLR]
- operator= member [STL/CLR]
- operator== member [STL/CLR]
- operator> member [STL/CLR]
- operator>= member [STL/CLR]
ms.assetid: dd669da3-3c0e-45e9-8596-f6b483720941
ms.openlocfilehash: 74fb98d99e0aba94c40dce9ad1bcd6af83394231
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80208773"
---
# <a name="deque-stlclr"></a>deque (STL/CLR)

Klasa szablonu opisuje obiekt, który kontroluje różnej długości sekwencje elementów, które mają dostęp losowy. `deque` kontenera służy do zarządzania sekwencją elementów, które przypominają ciągły blok magazynu, ale mogą rosnąć lub zmniejszać się na końcu bez konieczności kopiowania pozostałych elementów. W ten sposób można zaimplementować wydajnie `double-ended queue`. (W związku z tym nazwa).

W poniższym opisie `GValue` jest taka sama jak `Value`, chyba że ostatni jest typem ref, w takim przypadku jest `Value^`.

## <a name="syntax"></a>Składnia

```cpp
template<typename Value>
    ref class deque
        :   public
        System::ICloneable,
        System::Collections::IEnumerable,
        System::Collections::ICollection,
        System::Collections::Generic::IEnumerable<GValue>,
        System::Collections::Generic::ICollection<GValue>,
        System::Collections::Generic::IList<GValue>,
        Microsoft::VisualC::StlClr::IDeque<GValue>
    { ..... };
```

### <a name="parameters"></a>Parametry

*GValue*<br/>
Typ ogólny elementu w kontrolowanej sekwencji.

*Wartość*<br/>
Typ elementu w kontrolowanej sekwencji.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<cliext/deque >

**Przestrzeń nazw:** cliext

## <a name="declarations"></a>Deklaracje

|Definicja typu|Opis|
|---------------------|-----------------|
|[deque::const_iterator (STL/CLR)](#const_iterator)|Typ iteratora stałego dla kontrolowanej sekwencji.|
|[deque::const_reference (STL/CLR)](#const_reference)|Typ stałego odwołania do elementu.|
|[deque::const_reverse_iterator (STL/CLR)](#const_reverse_iterator)|Typ iteratora stałego zwrotnego dla kontrolowanej sekwencji.|
|[deque::difference_type (STL/CLR)](#difference_type)|Typ odległości ze znakiem między dwoma elementami.|
|[deque::generic_container (STL/CLR)](#generic_container)|Typ interfejsu generycznego dla kontenera.|
|[deque::generic_iterator (STL/CLR)](#generic_iterator)|Typ iteratora dla interfejsu generycznego dla kontenera.|
|[deque::generic_reverse_iterator (STL/CLR)](#generic_reverse_iterator)|Typ iteratora odwrotnego dla interfejsu generycznego dla kontenera.|
|[deque::generic_value (STL/CLR)](#generic_value)|Typ elementu dla interfejsu generycznego dla kontenera.|
|[deque::iterator (STL/CLR)](#iterator)|Typ iteratora dla kontrolowanej sekwencji.|
|[deque::reference (STL/CLR)](#reference)|Typ odwołania do elementu.|
|[deque::reverse_iterator (STL/CLR)](#reverse_iterator)|Typ iteratora odwrotnego dla kontrolowanej sekwencji.|
|[deque::size_type (STL/CLR)](#size_type)|Typ odległości ze znakiem między dwoma elementami.|
|[deque::value_type (STL/CLR)](#value_type)|Typ elementu.|

|Funkcja elementów członkowskich|Opis|
|---------------------|-----------------|
|[deque::assign (STL/CLR)](#assign)|Zamienia wszystkie elementy.|
|[deque::at (STL/CLR)](#at)|Uzyskuje dostęp do elementu w określonej pozycji.|
|[deque::back (STL/CLR)](#back)|Uzyskuje dostęp do ostatniego elementu.|
|[deque::begin (STL/CLR)](#begin)|Określa początek kontrolowanej sekwencji.|
|[deque::clear (STL/CLR)](#clear)|Usuwa wszystkie elementy.|
|[deque::deque (STL/CLR)](#deque)|Konstruuje obiekt kontenera.|
|[deque::empty (STL/CLR)](#empty)|Sprawdza, czy nie ma żadnych elementów.|
|[deque::end (STL/CLR)](#end)|Określa koniec kontrolowanej sekwencji.|
|[deque::erase (STL/CLR)](#erase)|Usuwa elementy z określonych pozycji.|
|[deque::front (STL/CLR)](#front)|Uzyskuje dostęp do pierwszego elementu.|
|[deque::insert (STL/CLR)](#insert)|Dodaje elementy w określonej pozycji.|
|[deque::pop_back (STL/CLR)](#pop_back)|Usuwa ostatni element.|
|[deque::pop_front (STL/CLR)](#pop_front)|Usuwa pierwszy element.|
|[deque::push_back (STL/CLR)](#push_back)|Dodaje nowy ostatni element.|
|[deque::push_front (STL/CLR)](#push_front)|Dodaje nowy pierwszy element.|
|[deque::rbegin (STL/CLR)](#rbegin)|Określa początek odwróconej sekwencji kontrolowanej.|
|[deque::rend (STL/CLR)](#rend)|Określa koniec odwróconej kontrolowanej sekwencji.|
|[deque::resize (STL/CLR)](#resize)|Zmienia liczbę elementów.|
|[deque::size (STL/CLR)](#size)|Liczy liczbę elementów.|
|[deque::swap (STL/CLR)](#swap)|Zamienia zawartości dwóch kontenerów.|
|[deque::to_array (STL/CLR)](#to_array)|Kopiuje przekontrolowaną sekwencję do nowej tablicy.|

|Właściwość|Opis|
|--------------|-----------------|
|[deque::back_item (STL/CLR)](#back_item)|Uzyskuje dostęp do ostatniego elementu.|
|[deque::front_item (STL/CLR)](#front_item)|Uzyskuje dostęp do pierwszego elementu.|

|Operator|Opis|
|--------------|-----------------|
|[deque::operator!= (STL/CLR)](#op_neq)|Określa, czy dwa obiekty `deque` nie są równe.|
|[deque::operator(STL/CLR)](#operator)|Uzyskuje dostęp do elementu w określonej pozycji.|
|[operator< (deque) (STL/CLR)](#op_lt)|Określa, czy obiekt `deque` jest mniejszy niż inny obiekt `deque`.|
|[operator<= (deque) (STL/CLR)](#op_lteq)|Określa, czy obiekt `deque` jest mniejszy niż lub równy innemu obiektowi `deque`.|
|[operator= (deque) (STL/CLR)](#op_as)|Zastępuje kontrolowaną sekwencję.|
|[operator== (deque) (STL/CLR)](#op_eq)|Określa, czy obiekt `deque` jest równy innemu obiektowi `deque`.|
|[operator> (deque) (STL/CLR)](#op_gt)|Określa, czy obiekt `deque` jest większy niż inny obiekt `deque`.|
|[operator>= (deque) (STL/CLR)](#op_gteq)|Określa, czy obiekt `deque` jest większy niż lub równy innemu obiektowi `deque`.|

## <a name="interfaces"></a>Interfejsy

|Interface|Opis|
|---------------|-----------------|
|<xref:System.ICloneable>|Duplikowanie obiektu.|
|<xref:System.Collections.IEnumerable>|Sekwencja przez elementy.|
|<xref:System.Collections.ICollection>|Obsługa grupy elementów.|
|<xref:System.Collections.Generic.IEnumerable%601>|Sekwencja przez wpisane elementy.|
|<xref:System.Collections.Generic.ICollection%601>|Obsługuj grupę wpisanych elementów.|
|<xref:System.Collections.Generic.IList%601>|Obsługuj uporządkowaną grupę wpisanych elementów.|
|IDeque < wartość\>|Obsługa kontenera ogólnego.|

## <a name="remarks"></a>Uwagi

Obiekt przydziela i zwalnia magazyn dla sekwencji, która kontroluje przez przechowywaną tablicę dojść, które wyznaczają bloki elementów `Value`. Macierz powiększa się na żądanie. Wzrost występuje w taki sposób, że koszt, który jest w trakcie oczekiwania lub dołączania nowego elementu, jest stałym czasem i żadne pozostałe elementy nie są zakłócone. Możesz również usunąć element z dowolnego końca w stałym czasie i bez zakłócania pozostałych elementów. W ten sposób deque jest dobrym kandydatem do bazowego kontenera dla kolejki klas szablonu [(STL/CLR)](../dotnet/queue-stl-clr.md) lub stosu klas szablonu [(STL/CLR)](../dotnet/stack-stl-clr.md).

Obiekt `deque` obsługuje Iteratory dostępu swobodnego, co oznacza, że można odwołać się do elementu bezpośrednio przy użyciu jego pozycji liczbowej, licząc od zera dla pierwszego (przedniego) elementu, do [deque:: size (STL/CLR)](#size)`() - 1` dla ostatniego elementu (z tyłu). Oznacza to również, że deque jest dobrym kandydatem dla bazowego kontenera dla klasy szablonu [priority_queue (STL/CLR)](../dotnet/priority-queue-stl-clr.md).

Iterator deque przechowuje dojście do skojarzonego obiektu deque, wraz z odchylenia elementu, który wyznaczy. Iteratorów można używać tylko ze skojarzonymi obiektami kontenera. Różnica elementu deque *nie* musi być taka sama jak jego położenie. Pierwszy wstawiony element ma zerową wartość zero, a następny dołączony element ma bias 1, ale następny element z elementem z prefiksem ma bias-1.

Wstawianie lub wymazywanie elementów z dowolnego końca nie *zmienia wartości* elementu przechowywanego w żadnym prawidłowym poleceniu. Jednakże Wstawianie lub wymazywanie elementu wewnętrznego *może* zmienić wartość elementu przechowywanego w danej oddzieleniu, dzięki czemu można także zmienić wartość wskazaną przez iterator. (Kontener może być konieczny do kopiowania elementów w górę lub w dół w celu utworzenia otworu przed wstawieniem lub wypełnienia otworu po wymazaniu). Niemniej jednak iterator deque pozostaje prawidłowy, tak długo, jak jego bias wyznacza prawidłowy element. Ponadto prawidłowy iterator pozostaje dereferencable — można go użyć w celu uzyskania dostępu do lub zmiany wartości elementu, która wyznaczona, tak długo, jak jej odchylenie nie jest równe odchylenia iteratora zwróconego przez `end()`.

Wymazywanie lub usuwanie elementu wywołuje destruktor dla jego przechowywanej wartości. Niszczenie kontenera powoduje wymazanie wszystkich elementów. W tym celu kontener, którego typem elementu jest Klasa ref, zapewnia, że żadne elementy nie wyprowadzą kontenera. Należy jednak zauważyć, że kontener dojść *nie* niszczy swoich elementów.

## <a name="members"></a>Members

## <a name="dequeassign-stlclr"></a><a name="assign"></a>deque:: Assign (STL/CLR)

Zamienia wszystkie elementy.

### <a name="syntax"></a>Składnia

```cpp
void assign(size_type count, value_type val);
template<typename InIt>
    void assign(InIt first, InIt last);
void assign(System::Collections::Generic::IEnumerable<Value>^ right);
```

#### <a name="parameters"></a>Parametry

*count*<br/>
Liczba elementów do wstawienia.

*pierwszego*<br/>
Początek zakresu do wstawienia.

*ostatniego*<br/>
Koniec zakresu do wstawienia.

*Kliknij*<br/>
Wyliczenie do wstawienia.

*użyte*<br/>
Wartość elementu do wstawienia.

### <a name="remarks"></a>Uwagi

Pierwsza funkcja członkowska zastępuje kontrolowana sekwencję z powtórzeniem elementów *Count* wartości *Val*. Służy do wypełniania kontenera wszystkimi elementami o tej samej wartości.

Jeśli `InIt` jest typu Integer, druga funkcja członkowska zachowuje się tak samo jak `assign((size_type)first, (value_type)last)`. W przeciwnym razie zastępuje kontrolowaną sekwencję sekwencją [`first`, `last`). Jest on używany do sterowania sekwencją, która kopiuje kolejną sekwencję.

Trzecia funkcja członkowska zastępuje kontrolowaną sekwencję sekwencją wyznaczonej przez moduł wyliczający w *prawo*. Jest on używany do naliczania kontrolowanej sekwencji kopii sekwencji opisanej przez moduł wyliczający.

### <a name="example"></a>Przykład

```cpp
// cliext_deque_assign.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // assign a repetition of values
    cliext::deque<wchar_t> c2;
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

## <a name="dequeat-stlclr"></a><a name="at"></a>deque:: at (STL/CLR)

Uzyskuje dostęp do elementu w określonej pozycji.

### <a name="syntax"></a>Składnia

```cpp
reference at(size_type pos);
```

#### <a name="parameters"></a>Parametry

*Terminal*<br/>
Pozycja elementu do uzyskania dostępu.

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca odwołanie do elementu kontrolowanej sekwencji w pozycji *punkt sprzedaży*. Jest on używany do odczytywania lub zapisywania elementu, którego położenie jest znane.

### <a name="example"></a>Przykład

```cpp
// cliext_deque_at.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
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

## <a name="dequeback-stlclr"></a><a name="back"></a>deque:: Back (STL/CLR)

Uzyskuje dostęp do ostatniego elementu.

### <a name="syntax"></a>Składnia

```cpp
reference back();
```

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca odwołanie do ostatniego elementu kontrolowanej sekwencji, które nie może być puste. Jest on używany do uzyskiwania dostępu do ostatniego elementu, gdy wiadomo, że już istnieje.

### <a name="example"></a>Przykład

```cpp
// cliext_deque_back.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
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

## <a name="dequeback_item-stlclr"></a><a name="back_item"></a>deque:: back_item (STL/CLR)

Uzyskuje dostęp do ostatniego elementu.

### <a name="syntax"></a>Składnia

```cpp
property value_type back_item;
```

### <a name="remarks"></a>Uwagi

Właściwość uzyskuje dostęp do ostatniego elementu kontrolowanej sekwencji, który nie może być pusty. Jest on używany do odczytywania lub zapisywania ostatniego elementu, gdy wiadomo, że już istnieje.

### <a name="example"></a>Przykład

```cpp
// cliext_deque_back_item.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
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

## <a name="dequebegin-stlclr"></a><a name="begin"></a>deque:: begin (STL/CLR)

Określa początek kontrolowanej sekwencji.

### <a name="syntax"></a>Składnia

```cpp
iterator begin();
```

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca iterator dostępu swobodnego, który wyznacza pierwszy element kontrolowanej sekwencji lub tuż poza końcem pustej sekwencji. Służy do uzyskania iteratora, który wyznacza `current` początku kontrolowanej sekwencji, ale jego stan może ulec zmianie w przypadku zmiany długości kontrolowanej sekwencji.

### <a name="example"></a>Przykład

```cpp
// cliext_deque_begin.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // inspect first two items
    cliext::deque<wchar_t>::iterator it = c1.begin();
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

## <a name="dequeclear-stlclr"></a><a name="clear"></a>deque:: Clear (STL/CLR)

Usuwa wszystkie elementy.

### <a name="syntax"></a>Składnia

```cpp
void clear();
```

### <a name="remarks"></a>Uwagi

Funkcja członkowska skutecznie wywołuje [deque:: Erase (STL/CLR)](#erase)`(` [deque:: begin (STL/CLR)](#begin)`(),` [DEQUE:: end (STL/CLR)](#end)`())`. Jest on używany do upewnienia się, że kontrolowana sekwencja jest pusta.

### <a name="example"></a>Przykład

```cpp
// cliext_deque_clear.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
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

## <a name="dequeconst_iterator-stlclr"></a><a name="const_iterator"></a>deque:: const_iterator (STL/CLR)

Typ iteratora stałego dla kontrolowanej sekwencji.

### <a name="syntax"></a>Składnia

```cpp
typedef T2 const_iterator;
```

### <a name="remarks"></a>Uwagi

Typ opisuje obiekt nieokreślonego typu `T2`, który może stanowić iterator stałego dostępu swobodnego dla kontrolowanej sekwencji.

### <a name="example"></a>Przykład

```cpp
// cliext_deque_const_iterator.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c"
    cliext::deque<wchar_t>::const_iterator cit = c1.begin();
    for (; cit != c1.end(); ++cit)
        System::Console::Write("{0} ", *cit);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="dequeconst_reference-stlclr"></a><a name="const_reference"></a>deque:: const_reference (STL/CLR)

Typ stałego odwołania do elementu.

### <a name="syntax"></a>Składnia

```cpp
typedef value_type% const_reference;
```

### <a name="remarks"></a>Uwagi

Typ opisuje stałe odwołanie do elementu.

### <a name="example"></a>Przykład

```cpp
// cliext_deque_const_reference.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a b c"
    cliext::deque<wchar_t>::const_iterator cit = c1.begin();
    for (; cit != c1.end(); ++cit)
        {   // get a const reference to an element
        cliext::deque<wchar_t>::const_reference cref = *cit;
        System::Console::Write("{0} ", cref);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="dequeconst_reverse_iterator-stlclr"></a><a name="const_reverse_iterator"></a>deque:: const_reverse_iterator (STL/CLR)

Typ iteratora stałego zwrotnego dla kontrolowanej sekwencji.

### <a name="syntax"></a>Składnia

```cpp
typedef T4 const_reverse_iterator;
```

### <a name="remarks"></a>Uwagi

Typ opisuje obiekt nieokreślonego typu `T4`, który może być używany jako ciągły iterator odwrotny dla kontrolowanej sekwencji.

### <a name="example"></a>Przykład

```cpp
// cliext_deque_const_reverse_iterator.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c" reversed
    cliext::deque<wchar_t>::const_reverse_iterator crit = c1.rbegin();
    cliext::deque<wchar_t>::const_reverse_iterator crend = c1.rend();
    for (; crit != crend; ++crit)
        System::Console::Write("{0} ", *crit);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
c b a
```

## <a name="dequedeque-stlclr"></a><a name="deque"></a>deque::d eque (STL/CLR)

Konstruuje obiekt kontenera.

### <a name="syntax"></a>Składnia

```cpp
deque();
deque(deque<Value>% right);
deque(deque<Value>^ right);
explicit deque(size_type count);
deque(size_type count, value_type val);
template<typename InIt>
    deque(InIt first, InIt last);
deque(System::Collections::Generic::IEnumerable<Value>^ right);
```

#### <a name="parameters"></a>Parametry

*count*<br/>
Liczba elementów do wstawienia.

*pierwszego*<br/>
Początek zakresu do wstawienia.

*ostatniego*<br/>
Koniec zakresu do wstawienia.

*Kliknij*<br/>
Obiekt lub zakres do wstawienia.

*użyte*<br/>
Wartość elementu do wstawienia.

### <a name="remarks"></a>Uwagi

Konstruktor:

`deque();`

Inicjuje kontrolowaną sekwencję bez elementów. Służy do określenia pustej kontrolowanej sekwencji.

Konstruktor:

`deque(deque<Value>% right);`

Inicjuje kontrolowaną sekwencję z sekwencją [`right.begin()`, `right.end()`). Służy do określenia początkowej kontrolowanej sekwencji, która jest kopią sekwencji kontrolowanej *przez obiekt deque*. Aby uzyskać więcej informacji na temat iteratorów, zobacz [deque:: begin (STL/CLR)](#begin) i [deque:: end (STL/CLR)](#end).

Konstruktor:

`deque(deque<Value>^ right);`

Inicjuje kontrolowaną sekwencję z sekwencją [`right->begin()`, `right->end()`). Służy do określenia początkowej kontrolowanej sekwencji, która jest kopią sekwencji kontrolowanej przez obiekt deque, którego uchwyt jest *prawidłowy*.

Konstruktor:

`explicit deque(size_type count);`

Inicjuje kontrolowaną sekwencję z elementami *Count* Each z wartością `value_type()`. Służy do wypełniania kontenera wszystkimi elementami o wartości domyślnej.

Konstruktor:

`deque(size_type count, value_type val);`

Inicjuje kontrolowaną sekwencję z elementami *Count* każda o wartości *Val*. Służy do wypełniania kontenera wszystkimi elementami o tej samej wartości.

Konstruktor:

`template<typename InIt>`

`deque(InIt first, InIt last);`

Inicjuje kontrolowaną sekwencję z sekwencją [`first`, `last`). Jest on używany do Przekształć sekwencję na kopię innej sekwencji.

Konstruktor:

`deque(System::Collections::Generic::IEnumerable<Value>^ right);`

Inicjuje kontrolowaną sekwencję z sekwencją wyznaczonej przez moduł wyliczający w *prawo*. Jest on używany do naliczania kontrolowanej sekwencji kopii kolejnej sekwencji opisanej przez moduł wyliczający.

### <a name="example"></a>Przykład

```cpp
// cliext_deque_construct.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
// construct an empty container
    cliext::deque<wchar_t> c1;
    System::Console::WriteLine("size() = {0}", c1.size());

    // construct with a repetition of default values
    cliext::deque<wchar_t> c2(3);
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", (int)elem);
    System::Console::WriteLine();

    // construct with a repetition of values
    cliext::deque<wchar_t> c3(6, L'x');
    for each (wchar_t elem in c3)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct with an iterator range
    cliext::deque<wchar_t>::iterator it = c3.end();
    cliext::deque<wchar_t> c4(c3.begin(), --it);
    for each (wchar_t elem in c4)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct with an enumeration
    cliext::deque<wchar_t> c5(   // NOTE: cast is not needed
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c3);
    for each (wchar_t elem in c5)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct by copying another container
    cliext::deque<wchar_t> c7(c3);
    for each (wchar_t elem in c7)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct by copying a container handle
    cliext::deque<wchar_t> c8(%c3);
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

## <a name="dequedifference_type-stlclr"></a><a name="difference_type"></a>deque::d ifference_type (STL/CLR)

Typy podpisanej odległości między dwoma elementami.

### <a name="syntax"></a>Składnia

```cpp
typedef int difference_type;
```

### <a name="remarks"></a>Uwagi

Typ opisuje liczbę elementów ze znakiem.

### <a name="example"></a>Przykład

```cpp
// cliext_deque_difference_type.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // compute positive difference
    cliext::deque<wchar_t>::difference_type diff = 0;
    for (cliext::deque<wchar_t>::iterator it = c1.begin();
        it != c1.end(); ++it) ++diff;
    System::Console::WriteLine("end()-begin() = {0}", diff);

    // compute negative difference
    diff = 0;
    for (cliext::deque<wchar_t>::iterator it = c1.end();
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

## <a name="dequeempty-stlclr"></a><a name="empty"></a>deque:: empty (STL/CLR)

Sprawdza, czy nie ma żadnych elementów.

### <a name="syntax"></a>Składnia

```cpp
bool empty();
```

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca wartość true dla pustej kontrolowanej sekwencji. Jest to odpowiednik [deque:: size (STL/CLR)](#size)`() == 0`. Służy do sprawdzania, czy deque jest pusty.

### <a name="example"></a>Przykład

```cpp
// cliext_deque_empty.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
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

## <a name="dequeend-stlclr"></a><a name="end"></a>deque:: end (STL/CLR)

Określa koniec kontrolowanej sekwencji.

### <a name="syntax"></a>Składnia

```cpp
iterator end();
```

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca iterator dostępu swobodnego, który wskazuje tuż poza końcem kontrolowanej sekwencji. Służy do uzyskania iteratora, który wyznacza `current` końca kontrolowanej sekwencji, ale jego stan może ulec zmianie w przypadku zmiany długości kontrolowanej sekwencji.

### <a name="example"></a>Przykład

```cpp
// cliext_deque_end.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // inspect last two items
    cliext::deque<wchar_t>::iterator it = c1.end();
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

## <a name="dequeerase-stlclr"></a><a name="erase"></a>deque:: Erase (STL/CLR)

Usuwa elementy z określonych pozycji.

### <a name="syntax"></a>Składnia

```cpp
iterator erase(iterator where);
iterator erase(iterator first, iterator last);
```

#### <a name="parameters"></a>Parametry

*pierwszego*<br/>
Początek zakresu do wymazania.

*ostatniego*<br/>
Koniec zakresu do wymazania.

*miejscu*<br/>
Element do wymazania.

### <a name="remarks"></a>Uwagi

Pierwsza funkcja członkowska usuwa element kontrolowanej sekwencji wskazywanej przez *WHERE*. Służy do usuwania pojedynczego elementu.

Druga funkcja członkowska usuwa elementy z kontrolowanej sekwencji z zakresu [`first`, `last`). Jest on używany do usuwania elementów sąsiadujących lub więcej.

Obie funkcje członkowskie zwracają iterator, który wyznacza pierwszy element, który nie został usunięty, lub [deque:: end (STL/CLR)](#end)`()`, jeśli taki element nie istnieje.

Podczas wymazywania elementów liczba kopii elementów jest liniowa w liczbie elementów między końcem wymazywania a bliskością końca sekwencji. (Podczas wymazywania jednego lub większej liczby elementów na końcu sekwencji nie są kopiowane żadne elementy).

### <a name="example"></a>Przykład

```cpp
// cliext_deque_erase.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
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
    cliext::deque<wchar_t>::iterator it = c1.end();
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

## <a name="dequefront-stlclr"></a><a name="front"></a>deque:: front (STL/CLR)

Uzyskuje dostęp do pierwszego elementu.

### <a name="syntax"></a>Składnia

```cpp
reference front();
```

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca odwołanie do pierwszego elementu kontrolowanej sekwencji, które nie może być puste. Jest on używany do odczytywania lub zapisywania pierwszego elementu, gdy wiadomo, że już istnieje.

### <a name="example"></a>Przykład

```cpp
// cliext_deque_front.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
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

## <a name="dequefront_item-stlclr"></a><a name="front_item"></a>deque:: front_item (STL/CLR)

Uzyskuje dostęp do pierwszego elementu.

### <a name="syntax"></a>Składnia

```cpp
property value_type front_item;
```

### <a name="remarks"></a>Uwagi

Właściwość uzyskuje dostęp do pierwszego elementu kontrolowanej sekwencji, która nie może być pusta. Jest on używany do odczytywania lub zapisywania pierwszego elementu, gdy wiadomo, że już istnieje.

### <a name="example"></a>Przykład

```cpp
// cliext_deque_front_item.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
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

## <a name="dequegeneric_container-stlclr"></a><a name="generic_container"></a>deque:: generic_container (STL/CLR)

Typ interfejsu generycznego dla kontenera.

### <a name="syntax"></a>Składnia

```cpp
typedef Microsoft::VisualC::StlClr::
    IDeque<generic_value>
    generic_container;
```

### <a name="remarks"></a>Uwagi

Typ opisuje ogólny interfejs dla tej klasy kontenera szablonu.

### <a name="example"></a>Przykład

```cpp
// cliext_deque_generic_container.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct a generic container
    cliext::deque<wchar_t>::generic_container^ gc1 = %c1;
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

## <a name="dequegeneric_iterator-stlclr"></a><a name="generic_iterator"></a>deque:: generic_iterator (STL/CLR)

Typ iteratora do użycia z interfejsem ogólnym dla kontenera.

### <a name="syntax"></a>Składnia

```cpp
typedef Microsoft::VisualC::StlClr::Generic::
    ContainerRandomAccessIterator<generic_value> generic_iterator;
```

### <a name="remarks"></a>Uwagi

Typ opisuje iterator ogólny, który może być używany z interfejsem ogólnym dla tej klasy kontenera szablonu.

### <a name="example"></a>Przykład

```cpp
// cliext_deque_generic_iterator.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct a generic container
    cliext::deque<wchar_t>::generic_container^ gc1 = %c1;
    for each (wchar_t elem in gc1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // modify generic and display original
    cliext::deque<wchar_t>::generic_iterator gcit = gc1->begin();
    cliext::deque<wchar_t>::generic_value gcval = *gcit;
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

## <a name="dequegeneric_reverse_iterator-stlclr"></a><a name="generic_reverse_iterator"></a>deque:: generic_reverse_iterator (STL/CLR)

Typ iteratora odwrotnego do użycia z interfejsem ogólnym dla kontenera.

### <a name="syntax"></a>Składnia

```cpp
typedef Microsoft::VisualC::StlClr::Generic::
    ReverseRandomAccessIterator<generic_value> generic_reverse_iterator;
```

### <a name="remarks"></a>Uwagi

Typ opisuje ogólny iterator odwrotny, który może być używany z ogólnym interfejsem klasy kontenera tego szablonu.

### <a name="example"></a>Przykład

```cpp
// cliext_deque_generic_reverse_iterator.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct a generic container
    cliext::deque<wchar_t>::generic_container^ gc1 = %c1;
    for each (wchar_t elem in gc1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // modify generic and display original
    cliext::deque<wchar_t>::generic_reverse_iterator gcit = gc1->rbegin();
    cliext::deque<wchar_t>::generic_value gcval = *gcit;
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

## <a name="dequegeneric_value-stlclr"></a><a name="generic_value"></a>deque:: generic_value (STL/CLR)

Typ elementu do użycia z interfejsem ogólnym dla kontenera.

### <a name="syntax"></a>Składnia

```cpp
typedef GValue generic_value;
```

### <a name="remarks"></a>Uwagi

Typ opisuje obiekt typu `GValue`, który opisuje wartość przechowywanego elementu do użycia z interfejsem ogólnym dla tej klasy kontenera szablonu.

### <a name="example"></a>Przykład

```cpp
// cliext_deque_generic_value.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct a generic container
    cliext::deque<wchar_t>::generic_container^ gc1 = %c1;
    for each (wchar_t elem in gc1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // modify generic and display original
    cliext::deque<wchar_t>::generic_iterator gcit = gc1->begin();
    cliext::deque<wchar_t>::generic_value gcval = *gcit;
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

## <a name="dequeinsert-stlclr"></a><a name="insert"></a>deque:: Insert (STL/CLR)

Dodaje elementy w określonej pozycji.

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

*count*<br/>
Liczba elementów do wstawienia.

*pierwszego*<br/>
Początek zakresu do wstawienia.

*ostatniego*<br/>
Koniec zakresu do wstawienia.

*Kliknij*<br/>
Wyliczenie do wstawienia.

*użyte*<br/>
Wartość elementu do wstawienia.

*miejscu*<br/>
Gdzie w kontenerze należy wstawić przed.

### <a name="remarks"></a>Uwagi

Każda funkcja członkowska wstawia przed elementem wskazywanym przez *WHERE* w kontrolowanej sekwencji sekwencję określoną przez pozostałe operandy.

Pierwsza funkcja członkowska wstawia element z wartością *Val* i zwraca iterator, który wyznacza nowo wstawiony element. Służy do wstawiania pojedynczego elementu przed miejscem wyznaczonym przez iterator.

Druga funkcja członkowska wstawia powtarzające się elementy *Count* wartości *Val*. Służy do wstawiania elementów ciągłych lub innych, które są kopiami tej samej wartości.

Jeśli `InIt` jest typu Integer, trzecia funkcja członkowska zachowuje się tak samo jak `insert(where, (size_type)first, (value_type)last)`. W przeciwnym razie wstawia sekwencję [`first`, `last`). Służy do wstawiania elementów sąsiadujących, które zostały skopiowane z innej sekwencji.

Czwarta funkcja członkowska wstawia sekwencję wydaną po *prawej stronie*. Służy do wstawiania sekwencji opisanej przez moduł wyliczający.

Podczas wstawiania pojedynczego elementu liczba kopii elementów jest liniowa w liczbie elementów między punktem wstawiania i bliską końcem sekwencji. (Podczas wstawiania co najmniej jednego elementu na końcu sekwencji nie ma żadnych kopii elementów). Jeśli `InIt` jest iteratorem wejściowym, trzecia funkcja członkowska skutecznie wykonuje pojedynczy wstawienie dla każdego elementu w sekwencji. W przeciwnym razie podczas wstawiania `N` elementów liczba kopii elementów jest liniowa w `N` plus liczba elementów między punktem wstawiania a bliskością końca sekwencji.

### <a name="example"></a>Przykład

```cpp
// cliext_deque_insert.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // insert a single value using iterator
    cliext::deque<wchar_t>::iterator it = c1.begin();
    System::Console::WriteLine("insert(begin()+1, L'x') = {0}",
        *c1.insert(++it, L'x'));
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // insert a repetition of values
    cliext::deque<wchar_t> c2;
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

## <a name="dequeiterator-stlclr"></a><a name="iterator"></a>deque:: iterator (STL/CLR)

Typ iteratora dla kontrolowanej sekwencji.

### <a name="syntax"></a>Składnia

```cpp
typedef T1 iterator;
```

### <a name="remarks"></a>Uwagi

Typ opisuje obiekt nieokreślonego typu `T1`, który może stanowić Iterator dostępu swobodnego dla kontrolowanej sekwencji.

### <a name="example"></a>Przykład

```cpp
// cliext_deque_iterator.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c"
    cliext::deque<wchar_t>::iterator it = c1.begin();
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

## <a name="dequeoperator-stlclr"></a><a name="op_neq"></a>deque:: operator! = (STL/CLR)

Deque nie równa się porównaniu.

### <a name="syntax"></a>Składnia

```cpp
template<typename Value>
    bool operator!=(deque<Value>% left,
        deque<Value>% right);
```

#### <a name="parameters"></a>Parametry

*lewym*<br/>
Lewy kontener do porównania.

*Kliknij*<br/>
Prawy kontener do porównania.

### <a name="remarks"></a>Uwagi

Funkcja operator zwraca `!(left == right)`. Służy do sprawdzania *, czy nie* jest on uporządkowany *tak samo jak w* przypadku, gdy dwa deques są porównywane elementu według elementu.

### <a name="example"></a>Przykład

```cpp
// cliext_deque_operator_ne.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // assign to a new container
    cliext::deque<wchar_t> c2;
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

## <a name="dequeoperatorstlclr"></a><a name="operator"></a>deque:: operator (STL/CLR)

Uzyskuje dostęp do elementu w określonej pozycji.

### <a name="syntax"></a>Składnia

```cpp
reference operator[](size_type pos);
```

#### <a name="parameters"></a>Parametry

*Terminal*<br/>
Pozycja elementu do uzyskania dostępu.

### <a name="remarks"></a>Uwagi

Operator członkowski zwraca referene do elementu w pozycji *pos*. Jest on używany do uzyskiwania dostępu do elementu, którego położenie jest znane.

### <a name="example"></a>Przykład

```cpp
// cliext_deque_operator_sub.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
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

## <a name="dequepop_back-stlclr"></a><a name="pop_back"></a>deque::p op_back (STL/CLR)

Usuwa ostatni element.

### <a name="syntax"></a>Składnia

```cpp
void pop_back();
```

### <a name="remarks"></a>Uwagi

Funkcja członkowska usuwa ostatni element kontrolowanej sekwencji, która nie może być pusta. Służy do skracania deque o jeden element na odwrocie.

### <a name="example"></a>Przykład

```cpp
// cliext_deque_pop_back.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
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

## <a name="dequepop_front-stlclr"></a><a name="pop_front"></a>deque::p op_front (STL/CLR)

Usuwa pierwszy element.

### <a name="syntax"></a>Składnia

```cpp
void pop_front();
```

### <a name="remarks"></a>Uwagi

Funkcja członkowska usuwa pierwszy element kontrolowanej sekwencji, która nie może być pusta. Służy do skracania deque o jeden element na początku.

### <a name="example"></a>Przykład

```cpp
// cliext_deque_pop_front.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
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

## <a name="dequepush_back-stlclr"></a><a name="push_back"></a>deque::p ush_back (STL/CLR)

Dodaje nowy ostatni element.

### <a name="syntax"></a>Składnia

```cpp
void push_back(value_type val);
```

### <a name="remarks"></a>Uwagi

Funkcja członkowska wstawia element z wartością `val` na końcu kontrolowanej sekwencji. Służy do dołączania kolejnego elementu do deque.

### <a name="example"></a>Przykład

```cpp
// cliext_deque_push_back.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
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

## <a name="dequepush_front-stlclr"></a><a name="push_front"></a>deque::p ush_front (STL/CLR)

Dodaje nowy pierwszy element.

### <a name="syntax"></a>Składnia

```cpp
void push_front(value_type val);
```

### <a name="remarks"></a>Uwagi

Funkcja członkowska wstawia element o wartości `val` na początku kontrolowanej sekwencji. Używa się go do dołączania kolejnego elementu do deque.

### <a name="example"></a>Przykład

```cpp
// cliext_deque_push_front.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
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

## <a name="dequerbegin-stlclr"></a><a name="rbegin"></a>deque:: rbegin (STL/CLR)

Określa początek odwróconej sekwencji kontrolowanej.

### <a name="syntax"></a>Składnia

```cpp
reverse_iterator rbegin();
```

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca iterator odwrotny, który wyznacza ostatni element kontrolowanej sekwencji lub tuż poza początkiem pustej sekwencji. W związku z tym wyznacza `beginning` sekwencji odwrotnej. Służy do uzyskania iteratora, który wyznacza `current` początku kontrolowanej sekwencji widocznej w odwrotnej kolejności, ale jego stan może ulec zmianie w przypadku zmiany długości kontrolowanej sekwencji.

### <a name="example"></a>Przykład

```cpp
// cliext_deque_rbegin.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // inspect first two items in reversed sequence
    cliext::deque<wchar_t>::reverse_iterator rit = c1.rbegin();
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

## <a name="dequereference-stlclr"></a><a name="reference"></a>deque:: Reference (STL/CLR)

Typ odwołania do elementu.

### <a name="syntax"></a>Składnia

```cpp
typedef value_type% reference;
```

### <a name="remarks"></a>Uwagi

Typ opisuje odwołanie do elementu.

### <a name="example"></a>Przykład

```cpp
// cliext_deque_reference.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a b c"
    cliext::deque<wchar_t>::iterator it = c1.begin();
    for (; it != c1.end(); ++it)
        {   // get a reference to an element
        cliext::deque<wchar_t>::reference ref = *it;
        System::Console::Write("{0} ", ref);
        }
    System::Console::WriteLine();

    // modify contents " a b c"
    for (it = c1.begin(); it != c1.end(); ++it)
        {   // get a reference to an element
        cliext::deque<wchar_t>::reference ref = *it;

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

## <a name="dequerend-stlclr"></a><a name="rend"></a>deque:: rend (STL/CLR)

Określa koniec odwróconej kontrolowanej sekwencji.

### <a name="syntax"></a>Składnia

```cpp
reverse_iterator rend();
```

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca iterator odwrotny, który wskazuje tuż poza początkiem kontrolowanej sekwencji. W związku z tym wyznacza `end` sekwencji odwrotnej. Służy do uzyskania iteratora, który wyznacza `current` końca kontrolowanej sekwencji widoczny w odwrotnej kolejności, ale jego stan może ulec zmianie w przypadku zmiany długości kontrolowanej sekwencji.

### <a name="example"></a>Przykład

```cpp
// cliext_deque_rend.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // inspect first two items
    cliext::deque<wchar_t>::reverse_iterator rit = c1.rend();
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

## <a name="dequeresize-stlclr"></a><a name="resize"></a>deque:: Resize (STL/CLR)

Zmienia liczbę elementów.

### <a name="syntax"></a>Składnia

```cpp
void resize(size_type new_size);
void resize(size_type new_size, value_type val);
```

#### <a name="parameters"></a>Parametry

*new_size*<br/>
Nowy rozmiar kontrolowanej sekwencji.

*użyte*<br/>
Wartość elementu dopełnienia.

### <a name="remarks"></a>Uwagi

Funkcje składowe gwarantują, że [deque:: size (STL/CLR)](#size)`()` odtąd zwraca *new_size*. Jeśli ta sekwencja musi być większa, funkcja pierwszej składowej dołącza elementy o wartości `value_type()`, podczas gdy druga funkcja członkowska dołącza elementy o wartości *Val*. Aby sekwencja była krótsza, obie funkcje członkowskie skutecznie kasują ostatni element [deque:: size (STL/CLR)](#size)`() -` `new_size` razy. Służy do upewnienia się, że kontrolowana sekwencja ma rozmiar *new_size*, przez przycinanie lub uzupełnienie bieżącej kontrolowanej sekwencji.

### <a name="example"></a>Przykład

```cpp
// cliext_deque_resize.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
// construct an empty container and pad with default values
    cliext::deque<wchar_t> c1;
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

## <a name="dequereverse_iterator-stlclr"></a><a name="reverse_iterator"></a>deque:: reverse_iterator (STL/CLR)

Typ iteratora odwrotnego dla kontrolowanej sekwencji.

### <a name="syntax"></a>Składnia

```cpp
typedef T3 reverse_iterator;
```

### <a name="remarks"></a>Uwagi

Typ opisuje obiekt nieokreślonego typu `T3`, który może działać jako iterator odwrotny dla kontrolowanej sekwencji.

### <a name="example"></a>Przykład

```cpp
// cliext_deque_reverse_iterator.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c" reversed
    cliext::deque<wchar_t>::reverse_iterator rit = c1.rbegin();
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

## <a name="dequesize-stlclr"></a><a name="size"></a>deque:: size (STL/CLR)

Liczy liczbę elementów.

### <a name="syntax"></a>Składnia

```cpp
size_type size();
```

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca długość kontrolowanej sekwencji. Służy do określania liczby elementów aktualnie w kontrolowanej sekwencji. Jeśli dowiesz się, czy sekwencja ma rozmiar różny od zera, zobacz [deque:: empty (STL/CLR)](#empty)`()`.

### <a name="example"></a>Przykład

```cpp
// cliext_deque_size.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
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

## <a name="dequesize_type-stlclr"></a><a name="size_type"></a>deque:: size_type (STL/CLR)

Typ podpisanej odległości między dwoma elementami.

### <a name="syntax"></a>Składnia

```cpp
typedef int size_type;
```

### <a name="remarks"></a>Uwagi

Typ opisuje nieujemną liczbę elementów.

### <a name="example"></a>Przykład

```cpp
// cliext_deque_size_type.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // compute positive difference
    cliext::deque<wchar_t>::size_type diff = c1.end() - c1.begin();
    System::Console::WriteLine("end()-begin() = {0}", diff);
    return (0);
    }
```

```Output
a b c
end()-begin() = 3
```

## <a name="dequeswap-stlclr"></a><a name="swap"></a>deque:: swap (STL/CLR)

Zamienia zawartości dwóch kontenerów.

### <a name="syntax"></a>Składnia

```cpp
void swap(deque<Value>% right);
```

#### <a name="parameters"></a>Parametry

*Kliknij*<br/>
Kontener, za pomocą którego ma zostać zamieniony zawartość.

### <a name="remarks"></a>Uwagi

Funkcja członkowska zamienia kontrolowane sekwencje między `*this` i *po prawej*. Robi to w stałym czasie i nie zgłasza wyjątków. Jest ona używana jako Szybka metoda wymiany zawartości dwóch kontenerów.

### <a name="example"></a>Przykład

```cpp
// cliext_deque_swap.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct another container with repetition of values
    cliext::deque<wchar_t> c2(5, L'x');
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

## <a name="dequeto_array-stlclr"></a><a name="to_array"></a>deque:: to_array (STL/CLR)

Kopiuje przekontrolowaną sekwencję do nowej tablicy.

### <a name="syntax"></a>Składnia

```cpp
cli::array<Value>^ to_array();
```

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca tablicę zawierającą kontrolowaną sekwencję. Służy do uzyskania kopii kontrolowanej sekwencji w formularzu tablicowym.

### <a name="example"></a>Przykład

```cpp
// cliext_deque_to_array.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
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

## <a name="dequevalue_type-stlclr"></a><a name="value_type"></a>deque:: value_type (STL/CLR)

Typ elementu.

### <a name="syntax"></a>Składnia

```cpp
typedef Value value_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla *wartości*parametru szablonu.

### <a name="example"></a>Przykład

```cpp
// cliext_deque_value_type.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c" using value_type
    for (cliext::deque<wchar_t>::iterator it = c1.begin();
        it != c1.end(); ++it)
        {   // store element in value_type object
        cliext::deque<wchar_t>::value_type val = *it;

        System::Console::Write("{0} ", val);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="operatorlt-deque-stlclr"></a><a name="op_lt"></a>&lt; operatora (deque) (STL/CLR)

Deque mniejsze niż porównanie.

### <a name="syntax"></a>Składnia

```cpp
template<typename Value>
    bool operator<(deque<Value>% left,
        deque<Value>% right);
```

#### <a name="parameters"></a>Parametry

*lewym*<br/>
Lewy kontener do porównania.

*Kliknij*<br/>
Prawy kontener do porównania.

### <a name="remarks"></a>Uwagi

Funkcja operator zwraca wartość true, jeśli dla najniższej pozycji `i`, dla której `!(right[i] < left[i])` jest również spełniony `left[i] < right[i]`. W przeciwnym razie zwraca `left->size() < right->size()` używany do sprawdzania, czy *lewa* jest uporządkowana przed *prawem* , gdy dwa deques są porównywane elementów według elementu.

### <a name="example"></a>Przykład

```cpp
// cliext_deque_operator_lt.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // assign to a new container
    cliext::deque<wchar_t> c2;
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

## <a name="operatorlt-deque-stlclr"></a><a name="op_lteq"></a>operator&lt;= (deque) (STL/CLR)

Deque mniejsze niż lub równe.

### <a name="syntax"></a>Składnia

```cpp
template<typename Value>
    bool operator<=(deque<Value>% left,
        deque<Value>% right);
```

#### <a name="parameters"></a>Parametry

*lewym*<br/>
Lewy kontener do porównania.

*Kliknij*<br/>
Prawy kontener do porównania.

### <a name="remarks"></a>Uwagi

Funkcja operator zwraca `!(right < left)`. Służy do sprawdzania *, czy nie* jest on uporządkowany po *prawej stronie* , gdy dwa deques są porównywane elementów według elementu.

### <a name="example"></a>Przykład

```cpp
// cliext_deque_operator_le.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // assign to a new container
    cliext::deque<wchar_t> c2;
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

## <a name="operator-deque-stlclr"></a><a name="op_as"></a>operator = (deque) (STL/CLR)

Zastępuje kontrolowaną sekwencję.

### <a name="syntax"></a>Składnia

```cpp
deque<Value>% operator=(deque<Value>% right);
```

#### <a name="parameters"></a>Parametry

*Kliknij*<br/>
Kontener do skopiowania.

### <a name="remarks"></a>Uwagi

Operator elementu członkowskiego kopiuje *prawo* do obiektu, a następnie zwraca `*this`. Służy do zastępowania kontrolowanej sekwencji kopią kontrolowanej sekwencji *po prawej stronie*.

### <a name="example"></a>Przykład

```cpp
// cliext_deque_operator_as.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // assign to a new container
    cliext::deque<wchar_t> c2;
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

## <a name="operator-deque-stlclr"></a><a name="op_eq"></a>operator = = (deque) (STL/CLR)

Deque równego porównania.

### <a name="syntax"></a>Składnia

```cpp
template<typename Value>
    bool operator==(deque<Value>% left,
        deque<Value>% right);
```

#### <a name="parameters"></a>Parametry

*lewym*<br/>
Lewy kontener do porównania.

*Kliknij*<br/>
Prawy kontener do porównania.

### <a name="remarks"></a>Uwagi

Funkcja operator zwraca wartość true tylko wtedy, gdy sekwencje sterowane przez *lewo* i *prawo* mają taką samą długość i, dla każdej pozycji `i`, `left[i] ==` `right[i]`. Służy do sprawdzania, czy *lewa* jest uporządkowana tak samo jak w przypadku *, gdy dwa* deques są porównywane elementów według elementu.

### <a name="example"></a>Przykład

```cpp
// cliext_deque_operator_eq.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // assign to a new container
    cliext::deque<wchar_t> c2;
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

## <a name="operatorgt-deque-stlclr"></a><a name="op_gt"></a>&gt; operatora (deque) (STL/CLR)

Deque większe niż porównanie.

### <a name="syntax"></a>Składnia

```cpp
template<typename Value>
    bool operator>(deque<Value>% left,
        deque<Value>% right);
```

#### <a name="parameters"></a>Parametry

*lewym*<br/>
Lewy kontener do porównania.

*Kliknij*<br/>
Prawy kontener do porównania.

### <a name="remarks"></a>Uwagi

Funkcja operator zwraca `right` `<` `left`. Służy do sprawdzania, czy *lewa* jest uporządkowana po *prawej* , gdy dwa deques są porównywane elementów według elementu.

### <a name="example"></a>Przykład

```cpp
// cliext_deque_operator_gt.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // assign to a new container
    cliext::deque<wchar_t> c2;
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

## <a name="operatorgt-deque-stlclr"></a><a name="op_gteq"></a>operator&gt;= (deque) (STL/CLR)

Deque większe niż lub równe.

### <a name="syntax"></a>Składnia

```cpp
template<typename Value>
    bool operator>=(deque<Value>% left,
        deque<Value>% right);
```

#### <a name="parameters"></a>Parametry

*lewym*<br/>
Lewy kontener do porównania.

*Kliknij*<br/>
Prawy kontener do porównania.

### <a name="remarks"></a>Uwagi

Funkcja operator zwraca `!(left` `<` `right)`. Służy do sprawdzania *, czy nie* jest on uporządkowany przed *prawem* , gdy dwa deques są porównywane elementów według elementu.

### <a name="example"></a>Przykład

```cpp
// cliext_deque_operator_ge.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // assign to a new container
    cliext::deque<wchar_t> c2;
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
