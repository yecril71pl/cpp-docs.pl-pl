---
title: priority_queue (STL/CLR)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- cliext::priority_queue
- cliext::priority_queue::assign
- cliext::priority_queue::const_reference
- cliext::priority_queue::container_type
- cliext::priority_queue::difference_type
- cliext::priority_queue::empty
- cliext::priority_queue::generic_container
- cliext::priority_queue::generic_value
- cliext::priority_queue::get_container
- cliext::priority_queue::operator=
- cliext::priority_queue::pop
- cliext::priority_queue::priority_queue
- cliext::priority_queue::push
- cliext::priority_queue::reference
- cliext::priority_queue::size
- cliext::priority_queue::size_type
- cliext::priority_queue::to_array
- cliext::priority_queue::top
- cliext::priority_queue::top_item
- cliext::priority_queue::value_comp
- cliext::priority_queue::value_compare
- cliext::priority_queue::value_type
helpviewer_keywords:
- priority_queue class [STL/CLR]
- <queue> header [STL/CLR]
- <cliext/queue> header [STL/CLR]
- assign member [STL/CLR]
- const_reference member [STL/CLR]
- container_type member [STL/CLR]
- difference_type member [STL/CLR]
- empty member [STL/CLR]
- generic_container member [STL/CLR]
- generic_value member [STL/CLR]
- get_container member [STL/CLR]
- operator= member [STL/CLR]
- pop member [STL/CLR]
- priority_queue member [STL/CLR]
- push member [STL/CLR]
- reference member [STL/CLR]
- size member [STL/CLR]
- size_type member [STL/CLR]
- to_array member [STL/CLR]
- top member [STL/CLR]
- top_item member [STL/CLR]
- value_comp member [STL/CLR]
- value_compare member [STL/CLR]
- value_type member [STL/CLR]
ms.assetid: 4d0000d3-68ff-4c4b-8157-7060540136f5
ms.openlocfilehash: e21e7ba4dc3a4ed270548506ac1a9e37a2c1a23a
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80208471"
---
# <a name="priority_queue-stlclr"></a>priority_queue (STL/CLR)

Klasa szablonu opisuje obiekt, który kontroluje różnej długości uporządkowaną sekwencję elementów, które mają ograniczony dostęp. Karta kontenera jest używana `priority_queue` do zarządzania kontenerem bazowym jako kolejką priorytetową.

W poniższym opisie `GValue` jest taka sama jak *wartość* , chyba że ostatni jest typem ref, w takim przypadku jest `Value^`. Podobnie `GContainer` jest taka sama jak *kontener* , chyba że ostatni jest typem ref, w takim przypadku jest `Container^`.

## <a name="syntax"></a>Składnia

```cpp
template<typename Value,
    typename Container>
    ref class priority_queue
        System::ICloneable,
        Microsoft::VisualC::StlClr::IPriorityQueue<GValue, GContainer>
    { ..... };
```

### <a name="parameters"></a>Parametry

*Wartość*<br/>
Typ elementu w kontrolowanej sekwencji.

*Wbudowane*<br/>
Typ bazowego kontenera.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<cliext/Queue >

**Przestrzeń nazw:** cliext

## <a name="declarations"></a>Deklaracje

|Definicja typu|Opis|
|---------------------|-----------------|
|[priority_queue::const_reference (STL/CLR)](#const_reference)|Typ stałego odwołania do elementu.|
|[priority_queue::container_type (STL/CLR)](#container_type)|Typ bazowego kontenera.|
|[priority_queue::difference_type (STL/CLR)](#difference_type)|Typ odległości ze znakiem między dwoma elementami.|
|[priority_queue::generic_container (STL/CLR)](#generic_container)|Typ interfejsu ogólnego karty kontenera.|
|[priority_queue::generic_value (STL/CLR)](#generic_value)|Typ elementu dla interfejsu ogólnego karty kontenera.|
|[priority_queue::reference (STL/CLR)](#reference)|Typ odwołania do elementu.|
|[priority_queue::size_type (STL/CLR)](#size_type)|Typ odległości ze znakiem między dwoma elementami.|
|[priority_queue::value_compare (STL/CLR)](#value_compare)|Delegat porządkowania dla dwóch elementów.|
|[priority_queue::value_type (STL/CLR)](#value_type)|Typ elementu.|

|Funkcja elementów członkowskich|Opis|
|---------------------|-----------------|
|[priority_queue::assign (STL/CLR)](#assign)|Zamienia wszystkie elementy.|
|[priority_queue::empty (STL/CLR)](#empty)|Sprawdza, czy nie ma żadnych elementów.|
|[priority_queue::get_container (STL/CLR)](#get_container)|Uzyskuje dostęp do bazowego kontenera.|
|[priority_queue::pop (STL/CLR)](#pop)|Usuwa element hghest-Priority.|
|[priority_queue::priority_queue (STL/CLR)](#priority_queue)|Konstruuje obiekt kontenera.|
|[priority_queue::push (STL/CLR)](#push)|Dodaje nowy element.|
|[priority_queue::size (STL/CLR)](#size)|Liczy liczbę elementów.|
|[priority_queue::top (STL/CLR)](#top)|Uzyskuje dostęp do najwyższego priorytetu elementu.|
|[priority_queue::to_array (STL/CLR)](#to_array)|Kopiuje przekontrolowaną sekwencję do nowej tablicy.|
|[priority_queue::value_comp (STL/CLR)](#value_comp)|Kopiuje delegata porządkowania dla dwóch elementów.|

|Właściwość|Opis|
|--------------|-----------------|
|[priority_queue::top_item (STL/CLR)](#top_item)|Uzyskuje dostęp do najwyższego priorytetu elementu.|

|Operator|Opis|
|--------------|-----------------|
|[priority_queue::operator= (STL/CLR)](#op_as)|Zastępuje kontrolowaną sekwencję.|

## <a name="interfaces"></a>Interfejsy

|Interface|Opis|
|---------------|-----------------|
|<xref:System.ICloneable>|Duplikowanie obiektu.|
|IPriorityQueue\<wartość, kontener >|Obsługa karty kontenera ogólnego.|

## <a name="remarks"></a>Uwagi

Obiekt przydziela i zwalnia magazyn dla sekwencji, która kontroluje za pomocą bazowego kontenera, typu `Container`, który przechowuje `Value` elementów i rośnie na żądanie. Zachowuje sekwencję uporządkowaną jako stertę, a element o najwyższym priorytecie (najwyższego elementu) jest łatwo dostępny i wymienny. Obiekt ogranicza dostęp do wypychania nowych elementów i usuwanie tylko najwyższy priorytet elementu, implementując kolejkę priorytetową.

Obiekt porządkuje sekwencję, która kontroluje, wywołując zapisany obiekt delegata typu [priority_queue:: value_compare (STL/CLR)](../dotnet/priority-queue-value-compare-stl-clr.md). Podczas konstruowania priority_queue można określić przechowywany obiekt delegata; Jeśli określisz brak obiektu delegowanego, wartością domyślną jest porównanie `operator<(value_type, value_type)`. Dostęp do tego przechowywanego obiektu można uzyskać, wywołując funkcję członkowską [priority_queue:: value_comp (STL/CLR)](../dotnet/priority-queue-value-comp-stl-clr.md)`()`.

Taki obiekt delegata musi nałożyć ścisłe słabe porządkowanie dla wartości typu [priority_queue:: value_type (STL/CLR)](../dotnet/priority-queue-value-type-stl-clr.md). Oznacza to, że dla dowolnych dwóch kluczy `X` i `Y`:

`value_comp()(X, Y)` zwraca ten sam wynik Boolean dla każdego wywołania.

Jeśli `value_comp()(X, Y)` ma wartość true, `value_comp()(Y, X)` musi mieć wartość false.

Jeśli `value_comp()(X, Y)` ma wartość true, wówczas `X` jest określana jako uporządkowana przed `Y`.

Jeśli `!value_comp()(X, Y) && !value_comp()(Y, X)` ma wartość true, wówczas `X` i `Y` są określane jako równoważne.

Dla każdego elementu `X`, który poprzedza `Y` w kontrolowanej sekwencji, `key_comp()(Y, X)` ma wartość false. (Dla domyślnego obiektu delegowanego klucze nigdy nie zmniejszają wartości).

Element o najwyższym priorytecie jest w tym samym jednym z elementów, które nie są uporządkowane przed jakimkolwiek innym elementem.

Ponieważ źródłowy kontener zachowuje elementy uporządkowane jako sterta:

Kontener musi obsługiwać Iteratory dostępu swobodnego.

Elementy o równoważnej kolejności mogą być zdjęte w innej kolejności niż ich wypychanie. (Kolejność nie jest stabilna).

W tym celu kandydaci dla kontenera bazowego obejmują [deque (STL/CLR)](../dotnet/deque-stl-clr.md) i [Vector (STL/CLR)](../dotnet/vector-stl-clr.md).

## <a name="members"></a>Members

## <a name="priority_queueassign-stlclr"></a><a name="assign"></a>priority_queue:: Assign (STL/CLR)

Zamienia wszystkie elementy.

### <a name="syntax"></a>Składnia

```cpp
void assign(priority_queue<Value, Container>% right);
```

#### <a name="parameters"></a>Parametry

*Kliknij*<br/>
Karta kontenera do wstawienia.

### <a name="remarks"></a>Uwagi

Funkcja członkowska przypisuje `right.get_container()` do bazowego kontenera. Służy do zmiany całej zawartości kolejki.

### <a name="example"></a>Przykład

```cpp
// cliext_priority_queue_assign.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::priority_queue<wchar_t> Mypriority_queue;
int main()
    {
    Mypriority_queue c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // assign a repetition of values
    Mypriority_queue c2;
    c2.assign(c1);
    for each (wchar_t elem in c2.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
c a b
c a b
```

## <a name="priority_queueconst_reference-stlclr"></a><a name="const_reference"></a>priority_queue:: const_reference (STL/CLR)

Typ stałego odwołania do elementu.

### <a name="syntax"></a>Składnia

```cpp
typedef value_type% const_reference;
```

### <a name="remarks"></a>Uwagi

Typ opisuje stałe odwołanie do elementu.

### <a name="example"></a>Przykład

```cpp
// cliext_priority_queue_const_reference.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::priority_queue<wchar_t> Mypriority_queue;
int main()
    {
    Mypriority_queue c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

    // display reversed contents " c b a"
    for (; !c1.empty(); c1.pop())
        {   // get a const reference to an element
        Mypriority_queue::const_reference cref = c1.top();
        System::Console::Write("{0} ", cref);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
c b a
```

## <a name="priority_queuecontainer_type-stlclr"></a><a name="container_type"></a>priority_queue:: container_type (STL/CLR)

Typ bazowego kontenera.

### <a name="syntax"></a>Składnia

```cpp
typedef Container value_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla parametru szablonu `Container`.

### <a name="example"></a>Przykład

```cpp
// cliext_priority_queue_container_type.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::priority_queue<wchar_t> Mypriority_queue;
int main()
    {
    Mypriority_queue c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

    // display contents " a b c" using container_type
    Mypriority_queue::container_type wc1 = c1.get_container();
    for each (wchar_t elem in wc1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
c a b
```

## <a name="priority_queuedifference_type-stlclr"></a><a name="difference_type"></a>priority_queue::d ifference_type (STL/CLR)

Typy podpisanej odległości między dwoma elementami.

### <a name="syntax"></a>Składnia

```cpp
typedef int difference_type;
```

### <a name="remarks"></a>Uwagi

Typ opisuje prawdopodobnie ujemną liczbę elementów.

### <a name="example"></a>Przykład

```cpp
// cliext_priority_queue_difference_type.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::priority_queue<wchar_t> Mypriority_queue;
int main()
    {
    Mypriority_queue c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // compute negative difference
    Mypriority_queue::difference_type diff = c1.size();
    c1.push(L'd');
    c1.push(L'e');
    diff -= c1.size();
    System::Console::WriteLine("pushing 2 = {0}", diff);

    // compute positive difference
    diff = c1.size();
    c1.pop();
    c1.pop();
    c1.pop();
    diff -= c1.size();
    System::Console::WriteLine("popping 3 = {0}", diff);
    return (0);
    }
```

```Output
c a b
pushing 2 = -2
popping 3 = 3
```

## <a name="priority_queueempty-stlclr"></a><a name="empty"></a>priority_queue:: empty (STL/CLR)

Sprawdza, czy nie ma żadnych elementów.

### <a name="syntax"></a>Składnia

```cpp
bool empty();
```

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca wartość true dla pustej kontrolowanej sekwencji. Jest to odpowiednik`() == 0`[priority_queue:: size (STL/CLR)](../dotnet/priority-queue-size-stl-clr.md) . Służy do sprawdzania, czy priority_queue jest puste.

### <a name="example"></a>Przykład

```cpp
// cliext_priority_queue_empty.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::priority_queue<wchar_t> Mypriority_queue;
int main()
    {
    Mypriority_queue c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    System::Console::WriteLine("size() = {0}", c1.size());
    System::Console::WriteLine("empty() = {0}", c1.empty());

    // clear the container and reinspect
    c1.pop();
    c1.pop();
    c1.pop();
    System::Console::WriteLine("size() = {0}", c1.size());
    System::Console::WriteLine("empty() = {0}", c1.empty());
    return (0);
    }
```

```Output
c a b
size() = 3
empty() = False
size() = 0
empty() = True
```

## <a name="priority_queuegeneric_container-stlclr"></a><a name="generic_container"></a>priority_queue:: generic_container (STL/CLR)

Typ interfejsu generycznego dla kontenera.

### <a name="syntax"></a>Składnia

```cpp
typedef Microsoft::VisualC::StlClr::IPriorityQueue<Value>
    generic_container;
```

### <a name="remarks"></a>Uwagi

Typ opisuje ogólny interfejs dla tej klasy adaptera kontenerów szablonów.

### <a name="example"></a>Przykład

```cpp
// cliext_priority_queue_generic_container.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::priority_queue<wchar_t> Mypriority_queue;
int main()
    {
    Mypriority_queue c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct a generic container
    Mypriority_queue::generic_container^ gc1 = %c1;
    for each (wchar_t elem in gc1->get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // modify generic and display original
    gc1->push(L'd');
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // modify original and display generic
    c1.push(L'e');
    for each (wchar_t elem in gc1->get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
c a b
c a b
d c b a
e d b a c
```

## <a name="priority_queuegeneric_value-stlclr"></a><a name="generic_value"></a>priority_queue:: generic_value (STL/CLR)

Typ elementu do użycia z interfejsem ogólnym dla kontenera.

### <a name="syntax"></a>Składnia

```cpp
typedef GValue generic_value;
```

### <a name="remarks"></a>Uwagi

Typ opisuje obiekt typu `GValue`, który opisuje wartość przechowywanego elementu do użycia z interfejsem ogólnym dla tej klasy kontenera szablonu. (`GValue` jest `value_type` lub `value_type^`, jeśli `value_type` jest typem ref).

### <a name="example"></a>Przykład

```cpp
// cliext_priority_queue_generic_value.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::priority_queue<wchar_t> Mypriority_queue;
int main()
    {
    Mypriority_queue c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // get interface to container
    Mypriority_queue::generic_container^ gc1 = %c1;
    for each (wchar_t elem in gc1->get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // display in priority order using generic_value
    for (; !gc1->empty(); gc1->pop())
        {
        Mypriority_queue::generic_value elem = gc1->top();

        System::Console::Write("{0} ", elem);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
c a b
c a b
c b a
```

## <a name="priority_queueget_container-stlclr"></a><a name="get_container"></a>priority_queue:: get_container (STL/CLR)

Uzyskuje dostęp do bazowego kontenera.

### <a name="syntax"></a>Składnia

```cpp
container_type get_container();
```

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca bazowego kontenera. Służy do pomijania ograniczeń narzuconych przez otokę kontenera.

### <a name="example"></a>Przykład

```cpp
// cliext_priority_queue_get_container.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::priority_queue<wchar_t> Mypriority_queue;
int main()
    {
    Mypriority_queue c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
c a b
```

## <a name="priority_queueoperator-stlclr"></a><a name="op_as"></a>priority_queue:: operator = (STL/CLR)

Zastępuje kontrolowaną sekwencję.

### <a name="syntax"></a>Składnia

```cpp
priority_queue <Value, Container>% operator=(priority_queue <Value, Container>% right);
```

#### <a name="parameters"></a>Parametry

*Kliknij*<br/>
Adapter kontenera do skopiowania.

### <a name="remarks"></a>Uwagi

Operator elementu członkowskiego kopiuje *prawo* do obiektu, a następnie zwraca `*this`. Służy do zastępowania kontrolowanej sekwencji kopią kontrolowanej sekwencji *po prawej stronie*.

### <a name="example"></a>Przykład

```cpp
// cliext_priority_queue_operator_as.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::priority_queue<wchar_t> Mypriority_queue;
int main()
    {
    Mypriority_queue c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // assign to a new container
    Mypriority_queue c2;
    c2 = c1;
    for each (wchar_t elem in c2.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
c a b
c a b
```

## <a name="priority_queuepop-stlclr"></a><a name="pop"></a>priority_queue::p op (STL/CLR)

Usuwa element najwyższego proirity.

### <a name="syntax"></a>Składnia

```cpp
void pop();
```

### <a name="remarks"></a>Uwagi

Funkcja członkowska usuwa element o najwyższym priorytecie kontrolowanej sekwencji, który nie może być pusty. Służy do skracania kolejki według jednego elementu na odwrocie.

### <a name="example"></a>Przykład

```cpp
// cliext_priority_queue_pop.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::priority_queue<wchar_t> Mypriority_queue;
int main()
    {
    Mypriority_queue c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // pop an element and redisplay
    c1.pop();
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
c a b
b a
```

## <a name="priority_queuepriority_queue-stlclr"></a><a name="priority_queue"></a>priority_queue::p riority_queue (STL/CLR)

Konstruuje obiekt karty kontenera.

### <a name="syntax"></a>Składnia

```cpp
priority_queue();
priority_queue(priority_queue<Value, Container> right);
priority_queue(priority_queue<Value, Container> right);
explicit priority_queue(value_compare^ pred);
priority_queue(value_compare^ pred, container_type% cont);
template<typename InIt>
    priority_queue(InIt first, InIt last);
template<typename InIt>
    priority_queue(InIt first, InIt last,
        value_compare^ pred);
template<typename InIt>
    priority_queue(InIt first, InIt last,
        value_compare^ pred, container_type% cont);
```

#### <a name="parameters"></a>Parametry

*dawanie*<br/>
Kontener do skopiowania.

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

`priority_queue();`

tworzy pusty kontener opakowany przy użyciu domyślnego predykatu porządkowania. Służy do określania pustej początkowej kontrolowanej sekwencji przy użyciu domyślnego predykatu porządkowania.

Konstruktor:

`priority_queue(priority_queue<Value, Container>% right);`

tworzy opakowany kontener, który jest kopią `right.get_container()`, z predykatem porządkowania `right.value_comp()`. Służy do określenia początkowej kontrolowanej sekwencji, która jest kopią sekwencji kontrolowanej *przez obiekt kolejki*z tym samym predykatem kolejności.

Konstruktor:

`priority_queue(priority_queue<Value, Container>^ right);`

tworzy opakowany kontener, który jest kopią `right->get_container()`, z predykatem porządkowania `right->value_comp()`. Służy do określenia początkowej kontrolowanej sekwencji, która jest kopią sekwencji kontrolowanej przez obiekt kolejki `*right`, z tym samym predykatem kolejności.

Konstruktor:

`explicit priority_queue(value_compare^ pred);`

tworzy pusty kontener opakowany z predykatem porządkowania *pred*. Służy do określania pustej początkowej kontrolowanej sekwencji z określonym predykatem kolejności.

Konstruktor:

`priority_queue(value_compare^ pred, container_type cont);`

tworzy pusty kontener opakowany z predykatem porządkowania *pred*, a następnie wypycha wszystkie elementy *pozostałego* do użycia w celu określenia początkowej kontrolowanej sekwencji z istniejącego kontenera z określonym predykatem kolejności.

Konstruktor:

`template<typename InIt> priority_queue(InIt first, InIt last);`

tworzy pusty kontener opakowany przy użyciu domyślnego predykatu kolejności, a następnie wypchnięcie sekwencji [`first`, `last`). Służy do określenia początkowej kontrolowanej sekwencji z określonego eqeuence, z określonym predykatem porządkowania.

Konstruktor:

`template<typename InIt> priority_queue(InIt first, InIt last, value_compare^ pred);`

tworzy pusty kontener opakowany z predykatem porządkowania *pred*, a następnie wypchnięcie sekwencji [`first`, `last`). Służy do określenia początkowej kontrolowanej sekwencji z określonego seqeuence, z określonym predykatem porządkowania.

Konstruktor:

`template<typename InIt> priority_queue(InIt first, InIt last, value_compare^ pred, container_type% cont);`

tworzy pusty kontener opakowany z predykatem porządkowania *pred*, a następnie wypycha wszystkie elementy instrukcji Then *i* sekwencję [`first`, `last`). Służy do określenia początkowej kontrolowanej sekwencji z istniejącego kontenera i określonego seqeuence z określonym predykatem kolejności.

### <a name="example"></a>Przykład

```cpp
// cliext_priority_queue_construct.cpp
// compile with: /clr
#include <cliext/queue>
#include <cliext/deque>

typedef cliext::priority_queue<wchar_t> Mypriority_queue;
typedef cliext::deque<wchar_t> Mydeque;
int main()
    {
// construct an empty container
    Mypriority_queue c1;
    Mypriority_queue::container_type^ wc1 = c1.get_container();
    System::Console::WriteLine("size() = {0}", c1.size());

    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');
    for each (wchar_t elem in wc1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct with an ordering rule
    Mypriority_queue c2 = cliext::greater<wchar_t>();
    System::Console::WriteLine("size() = {0}", c2.size());

    for each (wchar_t elem in wc1)
        c2.push(elem);
    for each (wchar_t elem in c2.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct with an ordering rule by copying an underlying container
    Mypriority_queue c2x =
        gcnew Mypriority_queue(cliext::greater<wchar_t>(), *wc1);
   for each (wchar_t elem in c2x.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct with an iterator range
    Mypriority_queue c3(wc1->begin(), wc1->end());
    for each (wchar_t elem in c3.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct with an iterator range and an ordering rule
    Mypriority_queue c4(wc1->begin(), wc1->end(),
        cliext::greater<wchar_t>());
    for each (wchar_t elem in c4.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct with an iterator range, another container, and an ordering rule
    Mypriority_queue c5(wc1->begin(), wc1->end(),
        cliext::greater<wchar_t>(), *wc1);
    for each (wchar_t elem in c5.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct from a generic container
    Mypriority_queue c6(c3);
    for each (wchar_t elem in c6.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct by copying another container
    Mypriority_queue c7(%c3);
    for each (wchar_t elem in c7.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct with an ordering rule, by copying an underlying container
    Mypriority_queue c8 =
        gcnew Mypriority_queue(cliext::greater<wchar_t>(), *wc1);
    for each (wchar_t elem in c8.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    return (0);
    }
```

```Output
size() = 0
c a b
size() = 0
a c b
a c b
c a b
a c b
a a b c c b
c a b
c a b
a c b
```

## <a name="priority_queuepush-stlclr"></a><a name="push"></a>priority_queue::p USH (STL/CLR)

Dodaje nowy element.

### <a name="syntax"></a>Składnia

```cpp
void push(value_type val);
```

### <a name="remarks"></a>Uwagi

Funkcja członkowska wstawia element z wartością `val` do kontrolowanej sekwencji i zmienia kolejność kontrolowanej sekwencji w celu utrzymania dyscypliny sterty. Służy do dodawania kolejnego elementu do kolejki.

### <a name="example"></a>Przykład

```cpp
// cliext_priority_queue_push.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::priority_queue<wchar_t> Mypriority_queue;
int main()
    {
    Mypriority_queue c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
c a b
```

## <a name="priority_queuereference-stlclr"></a><a name="reference"></a>priority_queue:: Reference (STL/CLR)

Typ odwołania do elementu.

### <a name="syntax"></a>Składnia

```cpp
typedef value_type% reference;
```

### <a name="remarks"></a>Uwagi

Typ opisuje odwołanie do elementu.

### <a name="example"></a>Przykład

```cpp
// cliext_priority_queue_reference.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::priority_queue<wchar_t> Mypriority_queue;
int main()
    {
    Mypriority_queue c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // modify top of priority_queue and redisplay
    Mypriority_queue::reference ref = c1.top();
    ref = L'x';
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
c a b
x a b
```

## <a name="priority_queuesize-stlclr"></a><a name="size"></a>priority_queue:: size (STL/CLR)

Liczy liczbę elementów.

### <a name="syntax"></a>Składnia

```cpp
size_type size();
```

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca długość kontrolowanej sekwencji. Służy do określania liczby elementów aktualnie w kontrolowanej sekwencji. Jeśli dowiesz się, czy sekwencja ma rozmiar różny od zera, zobacz [priority_queue:: empty (STL/CLR)](../dotnet/priority-queue-empty-stl-clr.md)`()`.

### <a name="example"></a>Przykład

```cpp
// cliext_priority_queue_size.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::priority_queue<wchar_t> Mypriority_queue;
int main()
    {
    Mypriority_queue c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    System::Console::WriteLine("size() = {0} starting with 3", c1.size());

    // pop an item and reinspect
    c1.pop();
    System::Console::WriteLine("size() = {0} after popping", c1.size());

    // add two elements and reinspect
    c1.push(L'a');
    c1.push(L'b');
    System::Console::WriteLine("size() = {0} after adding 2", c1.size());
    return (0);
    }
```

```Output
c a b
size() = 3 starting with 3
size() = 2 after popping
size() = 4 after adding 2
```

## <a name="priority_queuesize_type-stlclr"></a><a name="size_type"></a>priority_queue:: size_type (STL/CLR)

Typ podpisanej odległości między dwoma elementami.

### <a name="syntax"></a>Składnia

```cpp
typedef int size_type;
```

### <a name="remarks"></a>Uwagi

Typ opisuje nieujemną liczbę elementów.

### <a name="example"></a>Przykład

```cpp
// cliext_priority_queue_size_type.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::priority_queue<wchar_t> Mypriority_queue;
int main()
    {
    Mypriority_queue c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // compute positive difference
    Mypriority_queue::size_type diff = c1.size();
    c1.pop();
    c1.pop();
    diff -= c1.size();
    System::Console::WriteLine("size difference = {0}", diff);
    return (0);
    }
```

```Output
c a b
size difference = 2
```

## <a name="priority_queueto_array-stlclr"></a><a name="to_array"></a>priority_queue:: to_array (STL/CLR)

Kopiuje przekontrolowaną sekwencję do nowej tablicy.

### <a name="syntax"></a>Składnia

```cpp
cli::array<Value>^ to_array();
```

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca tablicę zawierającą kontrolowaną sekwencję. Służy do uzyskania kopii kontrolowanej sekwencji w formularzu tablicowym.

### <a name="example"></a>Przykład

```cpp
// cliext_priority_queue_to_array.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::priority_queue<wchar_t> Mypriority_queue;
int main()
    {
    Mypriority_queue c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

    // copy the container and modify it
    cli::array<wchar_t>^ a1 = c1.to_array();

    c1.push(L'd');
    for each (wchar_t elem in c1.get_container())
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
d c b a
c a b
```

## <a name="priority_queuetop-stlclr"></a><a name="top"></a>priority_queue:: Top (STL/CLR)

Uzyskuje dostęp do najwyższego priorytetu elementu.

### <a name="syntax"></a>Składnia

```cpp
reference top();
```

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca odwołanie do elementu Top (najwyższy priorytet) kontrolowanej sekwencji, która nie może być pusta. Ten element jest używany do uzyskiwania dostępu do najwyższego priorytetu, gdy wiadomo, że już istnieje.

### <a name="example"></a>Przykład

```cpp
// cliext_priority_queue_top.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::priority_queue<wchar_t> Mypriority_queue;
int main()
    {
    Mypriority_queue c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // inspect last item
    System::Console::WriteLine("top() = {0}", c1.top());

    // alter last item and reinspect
    c1.top() = L'x';
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

## <a name="priority_queuetop_item-stlclr"></a><a name="top_item"></a>priority_queue:: top_item (STL/CLR)

Uzyskuje dostęp do najwyższego priorytetu elementu.

### <a name="syntax"></a>Składnia

```cpp
property value_type back_item;
```

### <a name="remarks"></a>Uwagi

Właściwość uzyskuje dostęp do górnego elementu (najwyższego priorytetu) kontrolowanej sekwencji, która nie może być pusta. Jest on używany do odczytywania lub zapisywania elementu o najwyższym priorytecie, gdy wiadomo, że już istnieje.

### <a name="example"></a>Przykład

```cpp
// cliext_priority_queue_top_item.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::priority_queue<wchar_t> Mypriority_queue;
int main()
    {
    Mypriority_queue c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // inspect last item
    System::Console::WriteLine("top_item = {0}", c1.top_item);

    // alter last item and reinspect
    c1.top_item = L'x';
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
c a b
top_item = c
x a b
```

## <a name="priority_queuevalue_comp-stlclr"></a><a name="value_comp"></a>priority_queue:: value_comp (STL/CLR)

Kopiuje delegata porządkowania dla dwóch elementów.

### <a name="syntax"></a>Składnia

```cpp
value_compare^ value_comp();
```

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca delegat porządkowania używany do uporządkowania kontrolowanej sekwencji. Służy do porównywania dwóch wartości.

### <a name="example"></a>Przykład

```cpp
// cliext_priority_queue_value_comp.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::priority_queue<wchar_t> Mypriority_queue;
int main()
    {
    Mypriority_queue c1;
    Mypriority_queue::value_compare^ vcomp = c1.value_comp();

    System::Console::WriteLine("compare(L'a', L'a') = {0}",
        vcomp(L'a', L'a'));
    System::Console::WriteLine("compare(L'a', L'b') = {0}",
        vcomp(L'a', L'b'));
    System::Console::WriteLine("compare(L'b', L'a') = {0}",
        vcomp(L'b', L'a'));
    System::Console::WriteLine();

    // test a different ordering rule
    Mypriority_queue c2 = cliext::greater<wchar_t>();
    vcomp = c2.value_comp();

    System::Console::WriteLine("compare(L'a', L'a') = {0}",
        vcomp(L'a', L'a'));
    System::Console::WriteLine("compare(L'a', L'b') = {0}",
        vcomp(L'a', L'b'));
    System::Console::WriteLine("compare(L'b', L'a') = {0}",
        vcomp(L'b', L'a'));
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

## <a name="priority_queuevalue_compare-stlclr"></a><a name="value_compare"></a>priority_queue:: value_compare (STL/CLR)

Delegat porządkowania dla dwóch wartości.

### <a name="syntax"></a>Składnia

```cpp
binary_delegate<value_type, value_type, int> value_compare;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla delegata, który określa, czy pierwszy argument jest uporządkowany przed drugim.

### <a name="example"></a>Przykład

```cpp
// cliext_priority_queue_value_compare.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::priority_queue<wchar_t> Mypriority_queue;
int main()
    {
    Mypriority_queue c1;
    Mypriority_queue::value_compare^ vcomp = c1.value_comp();

    System::Console::WriteLine("compare(L'a', L'a') = {0}",
        vcomp(L'a', L'a'));
    System::Console::WriteLine("compare(L'a', L'b') = {0}",
        vcomp(L'a', L'b'));
    System::Console::WriteLine("compare(L'b', L'a') = {0}",
        vcomp(L'b', L'a'));
    System::Console::WriteLine();

    // test a different ordering rule
    Mypriority_queue c2 = cliext::greater<wchar_t>();
    vcomp = c2.value_comp();

    System::Console::WriteLine("compare(L'a', L'a') = {0}",
        vcomp(L'a', L'a'));
    System::Console::WriteLine("compare(L'a', L'b') = {0}",
        vcomp(L'a', L'b'));
    System::Console::WriteLine("compare(L'b', L'a') = {0}",
        vcomp(L'b', L'a'));
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

## <a name="priority_queuevalue_type-stlclr"></a><a name="value_type"></a>priority_queue:: value_type (STL/CLR)

Typ elementu.

### <a name="syntax"></a>Składnia

```cpp
typedef Value value_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla *wartości*parametru szablonu.

### <a name="example"></a>Przykład

```cpp
// cliext_priority_queue_value_type.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::priority_queue<wchar_t> Mypriority_queue;
int main()
    {
    Mypriority_queue c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

    // display reversed contents " a b c" using value_type
    for (; !c1.empty(); c1.pop())
        {   // store element in value_type object
        Mypriority_queue::value_type val = c1.top();

        System::Console::Write("{0} ", val);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
c b a
```
