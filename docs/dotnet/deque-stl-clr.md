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
ms.openlocfilehash: ff5ddcfa101baf4c85145d1c6d64a6a3b9e7df58
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50445061"
---
# <a name="deque-stlclr"></a>deque (STL/CLR)

Klasa szablonu opisuje obiekt, który kontroluje różnej długości sekwencje elementów mającego dostępu swobodnego. Korzystasz z kontenera `deque` Zarządzanie sekwencję elementów, który wygląda jak ciągłego bloku magazynu, ale który może rosnąć lub maleć na obu końcach bez potrzeby kopiowania wszystkie pozostałe elementy. Dlatego można skutecznie zaimplementować `double-ended queue`. (Stąd nazwa.)

W poniższym opisie `GValue` jest taka sama jak `Value` o ile nie jest typem odwołania, w którym to przypadku jest `Value^`.

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
Ogólny typ elementu w kontrolowanej sekwencji.

*Wartość*<br/>
Typ elementu w kontrolowanej sekwencji.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<cliext — / deque >

**Namespace:** cliext —

## <a name="declarations"></a>Deklaracje

|Definicja typu|Opis|
|---------------------|-----------------|
|[deque::const_iterator (STL/CLR)](#const_iterator)|Typ iteratora stałego dla kontrolowanej sekwencji.|
|[deque::const_reference (STL/CLR)](#const_reference)|Typ stałego odwołania do elementu.|
|[deque::const_reverse_iterator (STL/CLR)](#const_reverse_iterator)|Typ iteratora odwrotnego stałego dla kontrolowanej sekwencji.|
|[deque::difference_type (STL/CLR)](#difference_type)|Typ odległości ze znakiem między dwoma elementami.|
|[deque::generic_container (STL/CLR)](#generic_container)|Typ ogólny interfejs dla kontenera.|
|[deque::generic_iterator (STL/CLR)](#generic_iterator)|Typ iteratora dla ogólny interfejs dla kontenera.|
|[deque::generic_reverse_iterator (STL/CLR)](#generic_reverse_iterator)|Typ iteratora odwrotnego dla ogólny interfejs dla kontenera.|
|[deque::generic_value (STL/CLR)](#generic_value)|Typ elementu dla ogólny interfejs dla kontenera.|
|[deque::iterator (STL/CLR)](#iterator)|Typ iteratora dla kontrolowanej sekwencji.|
|[deque::reference (STL/CLR)](#reference)|Typ odwołania do elementu.|
|[deque::reverse_iterator (STL/CLR)](#reverse_iterator)|Typ iteratora odwrotnego dla kontrolowanej sekwencji.|
|[deque::size_type (STL/CLR)](#size_type)|Typ odległości ze znakiem między dwoma elementami.|
|[deque::value_type (STL/CLR)](#value_type)|Typ elementu.|

|Funkcja elementów członkowskich|Opis|
|---------------------|-----------------|
|[deque::assign (STL/CLR)](#assign)|Zamienia wszystkie elementy.|
|[deque::at (STL/CLR)](#at)|Uzyskuje dostęp do elementu na określonej pozycji.|
|[deque::back (STL/CLR)](#back)|Uzyskuje dostęp do ostatniego elementu.|
|[deque::begin (STL/CLR)](#begin)|Określa początek kontrolowanej sekwencji.|
|[deque::clear (STL/CLR)](#clear)|Usuwa wszystkie elementy.|
|[deque::deque (STL/CLR)](#deque)|Konstruuje obiekt kontenera.|
|[deque::empty (STL/CLR)](#empty)|Sprawdza, czy nie ma żadnych elementów.|
|[deque::end (STL/CLR)](#end)|Określa koniec kontrolowanej sekwencji.|
|[deque::erase (STL/CLR)](#erase)|Usuwa elementy z określonych pozycji.|
|[deque::front (STL/CLR)](#front)|Uzyskuje dostęp do pierwszego elementu.|
|[deque::insert (STL/CLR)](#insert)|Dodaje elementy na określonej pozycji.|
|[deque::pop_back (STL/CLR)](#pop_back)|Usuwa ostatni element.|
|[deque::pop_front (STL/CLR)](#pop_front)|Usuwa pierwszy element.|
|[deque::push_back (STL/CLR)](#push_back)|Dodaje nowy element ostatni.|
|[deque::push_front (STL/CLR)](#push_front)|Dodaje nowy element pierwszego.|
|[deque::rbegin (STL/CLR)](#rbegin)|Określa początek kontrolowanej sekwencji odwróconej.|
|[deque::rend (STL/CLR)](#rend)|Określa koniec kontrolowanej sekwencji odwróconej.|
|[deque::resize (STL/CLR)](#resize)|Zmiany liczby elementów.|
|[deque::size (STL/CLR)](#size)|Liczy liczbę elementów.|
|[deque::swap (STL/CLR)](#swap)|Zamienia zawartości dwóch kontenerów.|
|[deque::to_array (STL/CLR)](#to_array)|Kopiuje kontrolowanej sekwencji do nowej tablicy.|

|Właściwość|Opis|
|--------------|-----------------|
|[deque::back_item (STL/CLR)](#back_item)|Uzyskuje dostęp do ostatniego elementu.|
|[deque::front_item (STL/CLR)](#front_item)|Uzyskuje dostęp do pierwszego elementu.|

|Operator|Opis|
|--------------|-----------------|
|[deque::operator!= (STL/CLR)](#op_neq)|Określa, czy dwa `deque` obiekty nie są równe.|
|[deque::operator(STL/CLR)](#operator)|Uzyskuje dostęp do elementu na określonej pozycji.|
|[operator< (deque) (STL/CLR)](#op_lt)|Określa, czy `deque` obiekt jest mniejszy niż inny `deque` obiektu.|
|[operator<= (deque) (STL/CLR)](#op_lteq)|Określa, czy `deque` obiekt jest mniejszy niż lub równy innemu `deque` obiektu.|
|[operator= (deque) (STL/CLR)](#op_as)|Zastępuje kontrolowanej sekwencji.|
|[operator== (deque) (STL/CLR)](#op_eq)|Określa, czy `deque` obiekt jest równy innemu `deque` obiektu.|
|[operator> (deque) (STL/CLR)](#op_gt)|Określa, czy `deque` obiekt jest większy niż inny `deque` obiektu.|
|[operator>= (deque) (STL/CLR)](#op_gteq)|Określa, czy `deque` obiekt jest większy niż lub równy innemu `deque` obiektu.|

## <a name="interfaces"></a>Interfejsy

|Interface|Opis|
|---------------|-----------------|
|<xref:System.ICloneable>|Duplikowanie obiektów.|
|<xref:System.Collections.IEnumerable>|Przeprowadzaj sekwencjonowanie przez elementy.|
|<xref:System.Collections.ICollection>|Obsługa grupy elementów.|
|<xref:System.Collections.Generic.IEnumerable%601>|Przeprowadzaj Sekwencjonowanie za pośrednictwem typizowanych elementów.|
|<xref:System.Collections.Generic.ICollection%601>|Obsługa grupy typizowanych elementów.|
|<xref:System.Collections.Generic.IList%601>|Obsługa uporządkowane grupy typizowanych elementów.|
|IDeque < wartość\>|Obsługa kontenerów ogólnego.|

## <a name="remarks"></a>Uwagi

Obiekt przydziela i zwalnia pamięć dla sekwencji za pośrednictwem przechowywanych tablica dojść, które wyznaczają bloki konstrukcyjne `Value` elementów. Tablica rośnie na żądanie. Wzrost odbywa się w taki sposób, że koszt AS lub dodanie nowego elementu jest stałym czasie, a nie pozostałe elementy są zakłóceń. Można również usunąć element na obu końcach w stałym czasie i bez zakłóceń pozostałe elementy. W związku z tym, deque jest dobrym kandydatem do bazowego kontener dla klasy szablonu [kolejki (STL/CLR)](../dotnet/queue-stl-clr.md) lub klasą szablonu [stosu (STL/CLR)](../dotnet/stack-stl-clr.md).

A `deque` obiekt obsługuje iteratorami dostępu swobodnego, co oznacza, że można odwołać się do elementu bezpośrednio podanej pozycji liczbowych licząc od zera dla pierwszego elementu (frontonu), aby [deque::size (STL/CLR)](#size) `() - 1` dla ostatniego elementu (wstecz). Oznacza to również, że deque jest dobrym kandydatem do bazowego kontener dla klasy szablonu [priority_queue — (STL/CLR)](../dotnet/priority-queue-stl-clr.md).

Deque iterator przechowuje dojście do jego obiektu skojarzone deque, wraz z odchylenia element, który ją określa. Iteratory można użyć tylko w nich obiekty skojarzony kontener. Jest obliczana do elementu deque *nie* musi być taka sama, jak jego położenie. Pierwszy element wstawiony ma odchylenie zero i dalej dołączony element ma odchylenie 1, ale następny prepended element ma odchylenie -1.

Wstawianie lub wymazując elementy na obu końcach zależnie od nie *nie* zmienić wartości elementu przechowywaną w dowolnym Nieprawidłowa różnica. Wstawianie lub wymazywanie posługiwanie się nimi elementu, jednak *można* Zmień wartość elementu przechowywaną w danym odchylenie, więc również zmienić wartość wyznaczonym przez iterator. (Kontener może mieć skopiuj elementy w górę lub w dół do tworzenia dziury przed wstawieniem lub do wypełnienia dziury po wymazywania). Niemniej jednak iteratora deque pozostaje ważny tak długo, jak jego odchylenie wyznacza prawidłowego elementu. Ponadto prawidłowe iteratora pozostaje wyłuskiwania — służy do dostępu lub zmień wartość elementu ustanowi —, tak długo, jak jego odchylenie nie jest równy różnicy dla iteratorów zwróconych przez `end()`.

Wymazywanie lub usunięcie elementu wywołuje destruktor do jego przechowywanej wartości. Niszczenie kontenera usuwa wszystkie elementy. W związku z tym kontener, którego typ elementu jest klasą ref gwarantuje, że żadne elementy on nakreślał kontenera. Należy jednak pamiętać, że kontener dojścia nie *nie* zniszczyć jego elementów.

## <a name="members"></a>Elementy członkowskie

## <a name="assign"></a> deque::ASSIGN (STL/CLR)

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

## <a name="at"></a> deque::AT (STL/CLR)

Uzyskuje dostęp do elementu na określonej pozycji.

### <a name="syntax"></a>Składnia

```cpp
reference at(size_type pos);
```

#### <a name="parameters"></a>Parametry

*punktu sprzedaży*<br/>
Pozycja elementu, aby uzyskać dostęp.

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca odwołanie do elementu w kontrolowanej sekwencji w położeniu *pos*. Możesz użyć do odczytu lub zapisu elementu, którego pozycja znasz.

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

## <a name="back"></a> deque::back (STL/CLR)

Uzyskuje dostęp do ostatniego elementu.

### <a name="syntax"></a>Składnia

```cpp
reference back();
```

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca odwołanie do ostatniego elementu w kontrolowanej sekwencji, która musi być niepusta. Umożliwia ona dostęp do ostatniego elementu, gdy wiadomo, że istnieje.

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

## <a name="back_item"></a> deque::back_item (STL/CLR)

Uzyskuje dostęp do ostatniego elementu.

### <a name="syntax"></a>Składnia

```cpp
property value_type back_item;
```

### <a name="remarks"></a>Uwagi

Właściwość uzyskuje dostęp do ostatniego elementu w kontrolowanej sekwencji, która musi być niepusta. Możesz użyć do odczytu lub zapisu ostatniego elementu, gdy wiadomo, że istnieje.

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

## <a name="begin"></a> deque::BEGIN (STL/CLR)

Określa początek kontrolowanej sekwencji.

### <a name="syntax"></a>Składnia

```cpp
iterator begin();
```

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca iterator dostępu swobodnego, który wyznacza pierwszego elementu w kontrolowanej sekwencji lub tuż za koniec pustą sekwencją. Służy do uzyskiwania iterator, który wyznacza `current` początek kontrolowanej sekwencji, ale jej stan można zmienić, jeśli zmieni się długość kontrolowanej sekwencji.

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

## <a name="clear"></a> deque::Clear (STL/CLR)

Usuwa wszystkie elementy.

### <a name="syntax"></a>Składnia

```cpp
void clear();
```

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego skutecznie wywołuje [deque::erase (STL/CLR)](#erase) `(` [deque::begin (STL/CLR)](#begin) `(),` [deque::end (STL/CLR)](#end) `())`. Umożliwia ona upewnij się, że kontrolowanej sekwencji jest pusty.

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

## <a name="const_iterator"></a> deque::const_iterator (STL/CLR)

Typ iteratora stałego dla kontrolowanej sekwencji.

### <a name="syntax"></a>Składnia

```cpp
typedef T2 const_iterator;
```

### <a name="remarks"></a>Uwagi

Typ opisuje obiekt nieokreślonego typu `T2` który może służyć jako stały iterator dostępu swobodnego dla kontrolowanej sekwencji.

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

## <a name="const_reference"></a> deque::const_reference (STL/CLR)

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

## <a name="const_reverse_iterator"></a> deque::const_reverse_iterator (STL/CLR)

Typ iteratora odwrotnego stałego dla kontrolowanej sekwencji...

### <a name="syntax"></a>Składnia

```cpp
typedef T4 const_reverse_iterator;
```

### <a name="remarks"></a>Uwagi

Typ opisuje obiekt nieokreślonego typu `T4` który może służyć jako stałe odwrotnego iteratora dla kontrolowanej sekwencji.

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

## <a name="deque"></a> deque::deque (STL/CLR)

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

`deque();`

Inicjuje kontrolowanej sekwencji bez elementów. Umożliwia ona określenie pustą kontrolowaną sekwencję początkowej.

Konstruktor:

`deque(deque<Value>% right);`

Inicjuje kontrolowanej sekwencji za pomocą sekwencji [`right.begin()`, `right.end()`). Umożliwia ona określenie początkowej kontrolowanej sekwencji, który jest kopią na sekwencję kontrolowaną przez obiekt deque *prawo*. Aby uzyskać więcej informacji dotyczących iteratorów, zobacz [deque::begin (STL/CLR)](#begin) i [deque::end (STL/CLR)](#end).

Konstruktor:

`deque(deque<Value>^ right);`

Inicjuje kontrolowanej sekwencji za pomocą sekwencji [`right->begin()`, `right->end()`). Umożliwia ona określenie początkowej kontrolowanej sekwencji, który jest kopią na sekwencję kontrolowaną przez obiekt deque, którego dojście jest *prawo*.

Konstruktor:

`explicit deque(size_type count);`

Inicjuje kontrolowanej sekwencji za pomocą *liczba* elementów z wartością `value_type()`. Umożliwia ona wypełnić kontener z elementami wszystkich mających wartość domyślną.

Konstruktor:

`deque(size_type count, value_type val);`

Inicjuje kontrolowanej sekwencji za pomocą *liczba* elementów z wartością *val*. Umożliwia ona wypełnić kontener z elementami wszystkich mających taką samą wartość.

Konstruktor:

`template<typename InIt>`

`deque(InIt first, InIt last);`

Inicjuje kontrolowanej sekwencji za pomocą sekwencji [`first`, `last`). Umożliwia ona Utwórz kopię innej sekwencji kontrolowanej sekwencji.

Konstruktor:

`deque(System::Collections::Generic::IEnumerable<Value>^ right);`

Inicjuje kontrolowanej sekwencji za pomocą sekwencji wyznaczonym przez moduł wyliczający *prawo*. Umożliwia ona utworzyć kopię sekwencji innego opisanego przez moduł wyliczający kontrolowanej sekwencji.

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

## <a name="difference_type"></a> deque::difference_type (STL/CLR)

Typy odległości ze znakiem między dwoma elementami.

### <a name="syntax"></a>Składnia

```cpp
typedef int difference_type;
```

### <a name="remarks"></a>Uwagi

Typ opisuje liczba element podpisem.

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

## <a name="empty"></a> deque::EMPTY (STL/CLR)

Sprawdza, czy nie ma żadnych elementów.

### <a name="syntax"></a>Składnia

```cpp
bool empty();
```

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca wartość true dla pustą kontrolowaną sekwencję. Jest to równoważne [deque::size (STL/CLR)](#size)`() == 0`. Możesz użyć do sprawdzenia, czy deque jest pusty.

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

## <a name="end"></a> deque::end (STL/CLR)

Określa koniec kontrolowanej sekwencji.

### <a name="syntax"></a>Składnia

```cpp
iterator end();
```

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca iterator dostępu swobodnego, który wskazuje tuż za koniec kontrolowanej sekwencji. Służy do uzyskiwania iterator, który wyznacza `current` koniec kontrolowanej sekwencji, ale jej stan można zmienić, jeśli zmieni się długość kontrolowanej sekwencji.

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

## <a name="erase"></a> deque::ERASE (STL/CLR)

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

Obie funkcje Członkowskie zwracają iterator opisujący pierwszy element pozostający poza wszelkimi elementami usuniętymi lub [deque::end (STL/CLR)](#end) `()` jeśli taki element nie istnieje.

Gdy wymazując elementy zależnie od, liczbę kopii elementu jest liniowa w liczbie elementów między końcem wymazywanie a im bliżej siebie końca sekwencji. (Podczas wymazywania jeden lub więcej elementów na końcu sekwencji, nie kopiuje element wykonywane.)

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

## <a name="front"></a> deque::Front (STL/CLR)

Uzyskuje dostęp do pierwszego elementu.

### <a name="syntax"></a>Składnia

```cpp
reference front();
```

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca odwołanie do pierwszego elementu w kontrolowanej sekwencji, która musi być niepusta. Możesz użyć do odczytu lub zapisu pierwszego elementu, gdy wiadomo, że istnieje.

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

## <a name="front_item"></a> deque::front_item (STL/CLR)

Uzyskuje dostęp do pierwszego elementu.

### <a name="syntax"></a>Składnia

```cpp
property value_type front_item;
```

### <a name="remarks"></a>Uwagi

Właściwość uzyskuje dostęp do pierwszego elementu w kontrolowanej sekwencji, która musi być niepusta. Możesz użyć do odczytu lub zapisu pierwszego elementu, gdy wiadomo, że istnieje.

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

## <a name="generic_container"></a> deque::generic_container (STL/CLR)

Typ ogólny interfejs dla kontenera.

### <a name="syntax"></a>Składnia

```cpp
typedef Microsoft::VisualC::StlClr::
    IDeque<generic_value>
    generic_container;
```

### <a name="remarks"></a>Uwagi

Typ opisuje ogólny interfejs dla tej klasy szablonu w kontenerze.

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

## <a name="generic_iterator"></a> deque::generic_iterator (STL/CLR)

Typ iteratora do użytku z ogólny interfejs dla kontenera.

### <a name="syntax"></a>Składnia

```cpp
typedef Microsoft::VisualC::StlClr::Generic::
    ContainerRandomAccessIterator<generic_value> generic_iterator;
```

### <a name="remarks"></a>Uwagi

Typ opisuje iterator ogólny, który mogą być używane z ogólny interfejs dla tej klasy szablonu w kontenerze.

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

## <a name="generic_reverse_iterator"></a> deque::generic_reverse_iterator (STL/CLR)

Typ iteratora odwrotnego do użytku z ogólny interfejs dla kontenera.

### <a name="syntax"></a>Składnia

```cpp
typedef Microsoft::VisualC::StlClr::Generic::
    ReverseRandomAccessIterator<generic_value> generic_reverse_iterator;
```

### <a name="remarks"></a>Uwagi

Typ opisuje iterator odwrotny ogólnego, które mogą być używane z ogólny interfejs dla tej klasy kontenera szablonu.

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

## <a name="generic_value"></a> deque::generic_value (STL/CLR)

Typ elementu do użycia przy użyciu interfejsu ogólnego dla kontenera.

### <a name="syntax"></a>Składnia

```cpp
typedef GValue generic_value;
```

### <a name="remarks"></a>Uwagi

Typ opisuje obiekt typu `GValue` wartość elementu przechowywane do użytku z ogólny interfejs dla tej klasy kontenera szablonu, który opisuje.

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

## <a name="insert"></a> deque::INSERT (STL/CLR)

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

## <a name="iterator"></a> deque::iterator (STL/CLR)

Typ iteratora dla kontrolowanej sekwencji.

### <a name="syntax"></a>Składnia

```cpp
typedef T1 iterator;
```

### <a name="remarks"></a>Uwagi

Typ opisuje obiekt nieokreślonego typu `T1` który może służyć jako iterator dostępu swobodnego dla kontrolowanej sekwencji.

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

## <a name="op_neq"></a> deque::operator! = (STL/CLR)

Deque — są nierówne porównania.

### <a name="syntax"></a>Składnia

```cpp
template<typename Value>
    bool operator!=(deque<Value>% left,
        deque<Value>% right);
```

#### <a name="parameters"></a>Parametry

*left*<br/>
Po lewej stronie kontenera do porównania.

*right*<br/>
Kontener prawo do porównania.

### <a name="remarks"></a>Uwagi

Funkcja operator zwraca `!(left == right)`. Używanej do testowania czy *po lewej stronie* nie jest taka sama jak określona *prawo* po dwóch deques są w porównaniu element po elemencie.

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

## <a name="operator"></a> deque::operator(STL/CLR)

Uzyskuje dostęp do elementu na określonej pozycji.

### <a name="syntax"></a>Składnia

```cpp
reference operator[](size_type pos);
```

#### <a name="parameters"></a>Parametry

*punktu sprzedaży*<br/>
Pozycja elementu, aby uzyskać dostęp.

### <a name="remarks"></a>Uwagi

Operator elementu członkowskiego zwraca referene do elementu w położeniu *pos*. Umożliwia ona uzyskiwanie dostępu do elementu, której pozycja znasz.

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

## <a name="pop_back"></a> deque::pop_back (STL/CLR)

Usuwa ostatni element.

### <a name="syntax"></a>Składnia

```cpp
void pop_back();
```

### <a name="remarks"></a>Uwagi

Funkcja członkowska usuwa ostatniego elementu w kontrolowanej sekwencji, która musi być niepusta. Umożliwia ona skrócić czas deque przez jeden element w tle.

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

## <a name="pop_front"></a> deque::pop_front (STL/CLR)

Usuwa pierwszy element.

### <a name="syntax"></a>Składnia

```cpp
void pop_front();
```

### <a name="remarks"></a>Uwagi

Funkcja członkowska usuwa pierwszego elementu w kontrolowanej sekwencji, która musi być niepusta. Umożliwia ona skrócić czas deque przez jeden element z przodu.

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

## <a name="push_back"></a> deque::push_back (STL/CLR)

Dodaje nowy element ostatni.

### <a name="syntax"></a>Składnia

```cpp
void push_back(value_type val);
```

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego wstawia element z wartością `val` na koniec kontrolowanej sekwencji. Umożliwia ona dołączyć inny element do deque.

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

## <a name="push_front"></a> deque::push_front (STL/CLR)

Dodaje nowy element pierwszego.

### <a name="syntax"></a>Składnia

```cpp
void push_front(value_type val);
```

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego wstawia element z wartością `val` na początku kontrolowanej sekwencji. Umożliwia ona dołączana do innego elementu deque.

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

## <a name="rbegin"></a> deque::rbegin (STL/CLR)

Określa początek kontrolowanej sekwencji odwróconej.

### <a name="syntax"></a>Składnia

```cpp
reverse_iterator rbegin();
```

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca odwrotnego iteratora, który wyznacza wartość ostatniego elementu w kontrolowanej sekwencji lub tuż za koniec pustą sekwencją. Dzięki temu wyznacza `beginning` odwrotnej kolejności. Służy do uzyskiwania iterator, który wyznacza `current` początek kontrolowanej sekwencji występuje w odwrotnej kolejności, ale jej stan można zmienić, jeśli zmieni się długość kontrolowanej sekwencji.

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

## <a name="reference"></a> deque::Reference (STL/CLR)

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

## <a name="rend"></a> deque::rend (STL/CLR)

Określa koniec kontrolowanej sekwencji odwróconej.

### <a name="syntax"></a>Składnia

```cpp
reverse_iterator rend();
```

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca odwrotnego iteratora, który wskazuje tuż za początek kontrolowanej sekwencji. Dzięki temu wyznacza `end` odwrotnej kolejności. Służy do uzyskiwania iterator, który wyznacza `current` koniec kontrolowanej sekwencji występuje w odwrotnej kolejności, ale jej stan można zmienić, jeśli zmieni się długość kontrolowanej sekwencji.

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

## <a name="resize"></a> deque::Resize (STL/CLR)

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

Funkcje elementów członkowskich obu, upewnij się, że [deque::size (STL/CLR)](#size) `()` odtąd zwraca *new_size*. Jeśli musi stworzyć kontrolowanej sekwencji dłużej, pierwsza funkcja elementu członkowskiego dołącza elementy z wartością `value_type()`, natomiast funkcja drugiego członka dołącza elementy z wartością *val*. Aby kontrolowanej sekwencji krótszy, oba funkcje Członkowskie skutecznie wymazać po ostatnim elemencie [deque::size (STL/CLR)](#size) `() -` `new_size` razy. Służy do Sprawdź, czy kontrolowanej sekwencji ma rozmiar *new_size*, przycinanie lub wypełnienie bieżącej kontrolowanej sekwencji.

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

## <a name="reverse_iterator"></a> deque::reverse_iterator (STL/CLR)

Typ iteratora odwrotnego dla kontrolowanej sekwencji.

### <a name="syntax"></a>Składnia

```cpp
typedef T3 reverse_iterator;
```

### <a name="remarks"></a>Uwagi

Typ opisuje obiekt nieokreślonego typu `T3` który może służyć jako odwrotnego iteratora dla kontrolowanej sekwencji.

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

## <a name="size"></a> deque::size (STL/CLR)

Liczy liczbę elementów.

### <a name="syntax"></a>Składnia

```cpp
size_type size();
```

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca długość kontrolowanej sekwencji. Umożliwia ona określenie liczby elementów aktualnie w kontrolowanej sekwencji. Jeśli jest wszystkich interesujących Cię, czy sekwencja ma wartość różną od zera rozmiaru, zobacz [deque::empty (STL/CLR)](#empty)`()`.

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

## <a name="size_type"></a> deque::size_type (STL/CLR)

Typ odległości ze znakiem między dwoma elementu.

### <a name="syntax"></a>Składnia

```cpp
typedef int size_type;
```

### <a name="remarks"></a>Uwagi

Typ opisuje liczby nieujemnej wartości elementu.

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

## <a name="swap"></a> deque::swap (STL/CLR)

Zamienia zawartości dwóch kontenerów.

### <a name="syntax"></a>Składnia

```cpp
void swap(deque<Value>% right);
```

#### <a name="parameters"></a>Parametry

*right*<br/>
Kontener do wymiany zawartości z.

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zamienia kontrolowanej sekwencji między `*this` i *prawo*. Robi to w stałym czasie i w wyniku weryfikacji zgłasza wyjątek bez wyjątków. Możesz użyć go w prosty sposób do wymiany zawartości dwóch kontenerów.

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

## <a name="to_array"></a> deque::to_array (STL/CLR)

Kopiuje kontrolowanej sekwencji do nowej tablicy.

### <a name="syntax"></a>Składnia

```cpp
cli::array<Value>^ to_array();
```

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca tablicę zawierającą kontrolowanej sekwencji. Umożliwia ona otrzymać kopię kontrolowanej sekwencji w postaci tablicy.

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

## <a name="value_type"></a> deque::value_type (STL/CLR)

Typ elementu.

### <a name="syntax"></a>Składnia

```cpp
typedef Value value_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla parametru szablonu *wartość*.

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

## <a name="op_lt"></a> operator&lt; (deque) (STL/CLR)

Deque — mniej niż porównania.

### <a name="syntax"></a>Składnia

```cpp
template<typename Value>
    bool operator<(deque<Value>% left,
        deque<Value>% right);
```

#### <a name="parameters"></a>Parametry

*left*<br/>
Po lewej stronie kontenera do porównania.

*right*<br/>
Kontener prawo do porównania.

### <a name="remarks"></a>Uwagi

Operator funkcja zwraca wartość true, jeśli, na najniższą pozycję `i` dla którego `!(right[i] < left[i])` jest również wartość true, który `left[i] < right[i]`. W przeciwnym razie zwraca `left->size() < right->size()` używanej do testowania czy *po lewej stronie* był zamówiony przed *prawo* po dwóch deques są w porównaniu element po elemencie.

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

## <a name="op_lteq"></a> operator&lt;= (deque) (STL/CLR)

Deque — mniejsze niż lub równe porównania.

### <a name="syntax"></a>Składnia

```cpp
template<typename Value>
    bool operator<=(deque<Value>% left,
        deque<Value>% right);
```

#### <a name="parameters"></a>Parametry

*left*<br/>
Po lewej stronie kontenera do porównania.

*right*<br/>
Kontener prawo do porównania.

### <a name="remarks"></a>Uwagi

Funkcja operator zwraca `!(right < left)`. Używanej do testowania czy *po lewej stronie* nie są porządkowane po *prawo* po dwóch deques są w porównaniu element po elemencie.

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

## <a name="op_as"></a> Operator = (deque) (STL/CLR)

Zastępuje kontrolowanej sekwencji.

### <a name="syntax"></a>Składnia

```cpp
deque<Value>% operator=(deque<Value>% right);
```

#### <a name="parameters"></a>Parametry

*right*<br/>
Kontener do skopiowania.

### <a name="remarks"></a>Uwagi

Kopiuje operator składowej *prawo* do obiektu, następnie zwraca `*this`. Umożliwia ona Zastąp kopię kontrolowanej sekwencji w kontrolowanej sekwencji *prawo*.

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

## <a name="op_eq"></a> Operator == (deque) (STL/CLR)

Porównanie równego Deque.

### <a name="syntax"></a>Składnia

```cpp
template<typename Value>
    bool operator==(deque<Value>% left,
        deque<Value>% right);
```

#### <a name="parameters"></a>Parametry

*left*<br/>
Po lewej stronie kontenera do porównania.

*right*<br/>
Kontener prawo do porównania.

### <a name="remarks"></a>Uwagi

Funkcja operator zwraca wartość true, tylko wtedy, gdy sekwencje kontrolowane przez *po lewej stronie* i *prawo* tę samą długość, a dla każdej pozycji `i`, `left[i] ==` `right[i]`. Używanej do testowania czy *po lewej stronie* jest taka sama jak określona *prawo* po dwóch deques są w porównaniu element po elemencie.

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

## <a name="op_gt"></a> operator&gt; (deque) (STL/CLR)

Deque — większa niż porównania.

### <a name="syntax"></a>Składnia

```cpp
template<typename Value>
    bool operator>(deque<Value>% left,
        deque<Value>% right);
```

#### <a name="parameters"></a>Parametry

*left*<br/>
Po lewej stronie kontenera do porównania.

*right*<br/>
Kontener prawo do porównania.

### <a name="remarks"></a>Uwagi

Funkcja operator zwraca `right` `<` `left`. Używanej do testowania czy *po lewej stronie* są porządkowane po *prawo* po dwóch deques są w porównaniu element po elemencie.

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

## <a name="op_gteq"></a> operator&gt;= (deque) (STL/CLR)

Deque — porównanie większe lub równe.

### <a name="syntax"></a>Składnia

```cpp
template<typename Value>
    bool operator>=(deque<Value>% left,
        deque<Value>% right);
```

#### <a name="parameters"></a>Parametry

*left*<br/>
Po lewej stronie kontenera do porównania.

*right*<br/>
Kontener prawo do porównania.

### <a name="remarks"></a>Uwagi

Funkcja operator zwraca `!(left` `<` `right)`. Można go używać do testowania czy *po lewej stronie* nie był zamówiony przed *prawo* po dwóch deques są w porównaniu element po elemencie.

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