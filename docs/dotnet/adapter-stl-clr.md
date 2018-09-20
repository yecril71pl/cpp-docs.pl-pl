---
title: Karta (STL/CLR) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 06/15/2018
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- <cliext/adapter>
- cliext::collection_adapter
- cliext::collection_adapter::base
- cliext::collection_adapter::begin
- cliext::collection_adapter
- cliext::collection_adapter::collection_adapter
- cliext::collection_adapter::difference_type
- cliext::collection_adapter::end
- cliext::collection_adapter::iterator
- cliext::collection_adapter::key_type
- cliext::collection_adapter::mapped_type
- cliext::collection_adapter::operator=
- cliext::collection_adapter::reference
- cliext::collection_adapter::size
- cliext::collection_adapter::size_type
- cliext::collection_adapter::swap
- cliext::collection_adapter::value_type
- cliext::make_collection
- cliext::range_adapter
- cliext::operator=
- cliext::range_adapter::operator=
- cliext::range_adapter::range_adapter
dev_langs:
- C++
helpviewer_keywords:
- <adapter> header [STL/CLR]
- adapter [STL/CLR]
- <cliext/adapter> header [STL/CLR]
- collection_adapter class [STL/CLR]
- base member [STL/CLR]
- begin member [STL/CLR]
- collection_adapter member [STL/CLR]
- difference_type member [STL/CLR]
- end member [STL/CLR]
- iterator member [STL/CLR]
- key_type member [STL/CLR]
- mapped_type member [STL/CLR]
- operator= member [STL/CLR]
- reference member [STL/CLR]
- size member [STL/CLR]
- size_type member [STL/CLR]
- swap member [STL/CLR]
- value_type member [STL/CLR]
- make_collection function [STL/CLR]
- range_adapter class [STL/CLR]
- operator= member [STL/CLR]
- range_adapter member [STL/CLR]
ms.assetid: 71ce7e51-42b6-4f70-9595-303791a97677
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: b3ccf32175fc39bb607d381b6eb84c1ddc4e3693
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46423926"
---
# <a name="adapter-stlclr"></a>adapter (STL/CLR)

Nagłówek STL/CLR `<cliext/adapter>` określa dwie klasy szablonu (`collection_adapter` i `range_adapter`), a funkcja szablonu `make_collection`.

## <a name="syntax"></a>Składnia

```cpp
#include <cliext/adapter>
```

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<cliext — / karty >

**Namespace:** cliext —

## <a name="declarations"></a>Deklaracje

|Class|Opis|
|-----------|-----------------|
|[collection_adapter (STL/CLR)](#collection_adapter)|Opakowuje kolekcji Biblioteka klasy podstawowej (BCL), jako zakres.|
|[range_adapter (STL/CLR)](#range_adapter)|Opakowuje zakresu jako kolekcja BCL.|

|Funkcja|Opis|
|--------------|-----------------|
|[make_collection (STL/CLR)](#make_collection)|Tworzy karty zakresu, używając pary iteratora.|

## <a name="members"></a>Elementy członkowskie

## <a name="collection_adapter"></a> collection_adapter — (STL/CLR)

Opakowuje kolekcji .NET do użycia jako kontenera STL/CLR. Element `collection_adapter` jest klasa szablonu opisuje prosty obiekt kontenera STL/CLR. Opakowuje interfejs Biblioteka klasy podstawowej (BCL) i zwraca pary iteratora, które są używane do manipulowania kontrolowanej sekwencji.

### <a name="syntax"></a>Składnia

```cpp
template<typename Coll>
    ref class collection_adapter;

template<>
    ref class collection_adapter<
        System::Collections::ICollection>;
template<>
    ref class collection_adapter<
        System::Collections::IEnumerable>;
template<>
    ref class collection_adapter<
        System::Collections::IList>;
template<>
    ref class collection_adapter<
        System::Collections::IDictionary>;
template<typename Value>
    ref class collection_adapter<
        System::Collections::Generic::ICollection<Value>>;
template<typename Value>
    ref class collection_adapter<
        System::Collections::Generic::IEnumerable<Value>>;
template<typename Value>
    ref class collection_adapter<
        System::Collections::Generic::IList<Value>>;
template<typename Key,
    typename Value>
    ref class collection_adapter<
        System::Collections::Generic::IDictionary<Key, Value>>;
```

#### <a name="parameters"></a>Parametry

*Coll*<br/>
Typ opakowany kolekcji.

### <a name="specializations"></a>Specjalizacje

|Specjalizacja|Opis|
|--------------------|-----------------|
|Interfejs IEnumerable|Sekwencje przez elementy.|
|Interfejs ICollection|Przechowuje grupy elementów.|
|IList|Obsługuje uporządkowane grupy elementów.|
|Element IDictionary|Obsługa zestawu {klucz, wartość} pary.|
|Interfejs IEnumerable\<wartość >|Sekwencje za pośrednictwem typizowanych elementów.|
|Interfejs ICollection\<wartość >|Przechowuje grupy typizowanych elementów.|
|IList\<wartość >|Obsługuje uporządkowane grupy typizowanych elementów.|
|Element IDictionary\<wartość >|Obsługuje zestaw wpisane {klucz, wartość} pary.|

### <a name="members"></a>Elementy członkowskie

|Definicja typu|Opis|
|---------------------|-----------------|
|[collection_adapter::difference_type (STL/CLR)](#difference_type)|Typ odległości ze znakiem między dwoma elementami.|
|[collection_adapter::iterator (STL/CLR)](#iterator)|Typ iteratora dla kontrolowanej sekwencji.|
|[collection_adapter::key_type (STL/CLR)](#key_type)|Typ klucza słownika.|
|[collection_adapter::mapped_type (STL/CLR)](#mapped_type)|Typ wartości słownika.|
|[collection_adapter::reference (STL/CLR)](#reference)|Typ odwołania do elementu.|
|[collection_adapter::size_type (STL/CLR)](#size_type)|Typ odległości ze znakiem między dwoma elementami.|
|[collection_adapter::value_type (STL/CLR)](#value_type)|Typ elementu.|

|Funkcja elementów członkowskich|Opis|
|---------------------|-----------------|
|[collection_adapter::base (STL/CLR)](#base)|Wyznacza opakowana interfejsu BCL.|
|[collection_adapter::begin (STL/CLR)](#begin)|Określa początek kontrolowanej sekwencji.|
|[collection_adapter::collection_adapter (STL/CLR)](#collection_adapter_collection_adapter)|Konstruuje obiekt karty.|
|[collection_adapter::end (STL/CLR)](#end)|Określa koniec kontrolowanej sekwencji.|
|[collection_adapter::size (STL/CLR)](#size)|Liczy liczbę elementów.|
|[collection_adapter::swap (STL/CLR)](#swap)|Zamienia zawartości dwóch kontenerów.|

|Operator|Opis|
|--------------|-----------------|
|[collection_adapter::operator= (STL/CLR)](#op_eq)|Zastępuje przechowywane uchwyt BCL.|

### <a name="remarks"></a>Uwagi

Użyjesz tej klasy szablonu do manipulowania kontener BCL jako kontenera STL/CLR. `collection_adapter` Przechowuje dojście do interfejsu BCL, który z kolei kontroluje sekwencję elementów. A `collection_adapter` obiektu `X` zwraca parę iteratorów wejściowych `X.begin()` i `X.end()` umożliwia można znaleźć elementy, w kolejności. Niektóre specjalizacji również mieć możliwość napisania `X.size()` do określania długości kontrolowanej sekwencji.

## <a name="base"></a> collection_adapter::Base (STL/CLR)

Wyznacza opakowana interfejsu BCL.

### <a name="syntax"></a>Składnia

```cpp
Coll^ base();
```

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca przechowywanych uchwyt interfejsu BCL.

### <a name="example"></a>Przykład

```cpp
// cliext_collection_adapter_base.cpp
// compile with: /clr
#include <cliext/adapter>
#include <cliext/deque>

typedef cliext::collection_adapter<
    System::Collections::ICollection> Mycoll;
int main()
    {
    cliext::deque<wchar_t> d6x(6, L'x');
    Mycoll c1(%d6x);

    // display initial contents "x x x x x x "
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    System::Console::WriteLine("base() same = {0}", c1.base() == %c1);
    return (0);
    }
```

```Output
x x x x x x
base() same = True
```

## <a name="begin"></a> collection_adapter::BEGIN (STL/CLR)

Określa początek kontrolowanej sekwencji.

### <a name="syntax"></a>Składnia

```cpp
iterator begin();
```

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca iterator danych wejściowych, który wyznacza pierwszego elementu w kontrolowanej sekwencji lub tuż za koniec pustą sekwencją.

### <a name="example"></a>Przykład

```cpp
// cliext_collection_adapter_begin.cpp
// compile with: /clr
#include <cliext/adapter>
#include <cliext/deque>

typedef cliext::collection_adapter<
    System::Collections::ICollection> Mycoll;
int main()
{
    cliext::deque<wchar_t> d1;
    d1.push_back(L'a');
    d1.push_back(L'b');
    d1.push_back(L'c');
    Mycoll c1(%d1);

    // display initial contents "a b c "
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // inspect first two items
    Mycoll::iterator it = c1.begin();
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

## <a name="collection_adapter_collection_adapter"></a> collection_adapter::collection_adapter (STL/CLR)

Konstruuje obiekt karty.

### <a name="syntax"></a>Składnia

```cpp
collection_adapter();
collection_adapter(collection_adapter<Coll>% right);
collection_adapter(collection_adapter<Coll>^ right);
collection_adapter(Coll^ collection);
```

#### <a name="parameters"></a>Parametry

*Kolekcja*<br/>
BCL dojście do opakowania.

*right*<br/>
Obiekt do skopiowania.

### <a name="remarks"></a>Uwagi

Konstruktor:

`collection_adapter();`

Inicjuje przechowywanych uchwytu z `nullptr`.

Konstruktor:

`collection_adapter(collection_adapter<Coll>% right);`

Inicjuje przechowywanych uchwytu z `right.` [collection_adapter::base (STL/CLR)](../dotnet/collection-adapter-base-stl-clr.md)`()`.

Konstruktor:

`collection_adapter(collection_adapter<Coll>^ right);`

Inicjuje przechowywanych uchwytu z `right->` [collection_adapter::base (STL/CLR)](../dotnet/collection-adapter-base-stl-clr.md)`()`.

Konstruktor:

`collection_adapter(Coll^ collection);`

Inicjuje przechowywanych uchwytu z `collection`.

### <a name="example"></a>Przykład

```cpp
// cliext_collection_adapter_construct.cpp
// compile with: /clr
#include <cliext/adapter>
#include <cliext/deque>

typedef cliext::collection_adapter<
    System::Collections::ICollection> Mycoll;
int main()
{
    cliext::deque<wchar_t> d6x(6, L'x');

    // construct an empty container
    Mycoll c1;
    System::Console::WriteLine("base() null = {0}", c1.base() == nullptr);

    // construct with a handle
    Mycoll c2(%d6x);
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct by copying another container
    Mycoll c3(c2);
    for each (wchar_t elem in c3)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct by copying a container handle
    Mycoll c4(%c3);
    for each (wchar_t elem in c4)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    return (0);
}
```

```Output
base() null = True
x x x x x x
x x x x x x
x x x x x x
```

## <a name="difference_type"></a> collection_adapter::difference_type (STL/CLR)

Typy odległości ze znakiem między dwoma elementami.

### <a name="syntax"></a>Składnia

```cpp
typedef int difference_type;
```

### <a name="remarks"></a>Uwagi

Typ opisuje liczba element podpisem.

### <a name="example"></a>Przykład

```cpp
// cliext_collection_adapter_difference_type.cpp
// compile with: /clr
#include <cliext/adapter>
#include <cliext/deque>

typedef cliext::collection_adapter<
    System::Collections::ICollection> Mycoll;
int main()
{
    cliext::deque<wchar_t> d1;
    d1.push_back(L'a');
    d1.push_back(L'b');
    d1.push_back(L'c');
    Mycoll c1(%d1);

    // display initial contents "a b c "
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // compute positive difference
    Mycoll::difference_type diff = 0;
    Mycoll::iterator it = c1.begin();
    for (; it != c1.end(); ++it)
        ++diff;
    System::Console::WriteLine("end()-begin() = {0}", diff);
    return (0);
}
```

```Output
a b c
end()-begin() = 3
```

## <a name="end"></a> collection_adapter::end (STL/CLR)

Określa koniec kontrolowanej sekwencji.

### <a name="syntax"></a>Składnia

```cpp
iterator end();
```

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca iterator danych wejściowych, który wskazuje tuż za koniec kontrolowanej sekwencji.

### <a name="example"></a>Przykład

```cpp
// cliext_collection_adapter_end.cpp
// compile with: /clr
#include <cliext/adapter>
#include <cliext/deque>

typedef cliext::collection_adapter<
    System::Collections::ICollection> Mycoll;
int main()
{
    cliext::deque<wchar_t> d1;
    d1.push_back(L'a');
    d1.push_back(L'b');
    d1.push_back(L'c');
    Mycoll c1(%d1);

    // display initial contents "a b c "
    Mycoll::iterator it = c1.begin();
    for (; it != c1.end(); ++it)
        System::Console::Write("{0} ", *it);
    System::Console::WriteLine();
    return (0);
}
```

```Output
a b c
```

## <a name="iterator"></a> collection_adapter::iterator (STL/CLR)

Typ iteratora dla kontrolowanej sekwencji.

### <a name="syntax"></a>Składnia

```cpp
typedef T1 iterator;
```

### <a name="remarks"></a>Uwagi

Typ opisuje obiekt nieokreślonego typu `T1` który może służyć jako iterator danych wejściowych dla kontrolowanej sekwencji.

### <a name="example"></a>Przykład

```cpp
// cliext_collection_adapter_iterator.cpp
// compile with: /clr
#include <cliext/adapter>
#include <cliext/deque>

typedef cliext::collection_adapter<
    System::Collections::ICollection> Mycoll;
int main()
{
    cliext::deque<wchar_t> d1;
    d1.push_back(L'a');
    d1.push_back(L'b');
    d1.push_back(L'c');
    Mycoll c1(%d1);

    // display initial contents "a b c "
    Mycoll::iterator it = c1.begin();
    for (; it != c1.end(); ++it)
        System::Console::Write("{0} ", *it);
    System::Console::WriteLine();
    return (0);
}
```

```Output
a b c
```

## <a name="key_type"></a> collection_adapter::key_type (STL/CLR)

Typ klucza słownika.

### <a name="syntax"></a>Składnia

```cpp
typedef Key key_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla parametru szablonu `Key`, w specjalizacji dla `IDictionary` lub `IDictionary<Value>`; w przeciwnym razie nie jest zdefiniowany.

### <a name="example"></a>Przykład

```cpp
// cliext_collection_adapter_key_type.cpp
// compile with: /clr
#include <cliext/adapter>
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
typedef cliext::collection_adapter<
    System::Collections::Generic::IDictionary<wchar_t, int>> Mycoll;
typedef System::Collections::Generic::KeyValuePair<wchar_t,int> Mypair;
int main()
{
    Mymap d1;
    d1.insert(Mymap::make_value(L'a', 1));
    d1.insert(Mymap::make_value(L'b', 2));
    d1.insert(Mymap::make_value(L'c', 3));
    Mycoll c1(%d1);

    // display contents "[a 1] [b 2] [c 3] "
    for each (Mypair elem in c1)
    {
        Mycoll::key_type key = elem.Key;
        Mycoll::mapped_type value = elem.Value;
        System::Console::Write("[{0} {1}] ", key, value);
    }
    System::Console::WriteLine();
    return (0);
}
```

```Output
[a 1] [b 2] [c 3]
```

## <a name="mapped_type"></a> collection_adapter::mapped_type (STL/CLR)

Typ wartości słownika.

### <a name="syntax"></a>Składnia

```cpp
typedef Value mapped_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla parametru szablonu `Value`, w specjalizacji dla `IDictionary` lub `IDictionary<Value>`; w przeciwnym razie nie jest zdefiniowany.

### <a name="example"></a>Przykład

```cpp
// cliext_collection_adapter_mapped_type.cpp
// compile with: /clr
#include <cliext/adapter>
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
typedef cliext::collection_adapter<
    System::Collections::Generic::IDictionary<wchar_t, int>> Mycoll;
typedef System::Collections::Generic::KeyValuePair<wchar_t,int> Mypair;
int main()
{
    Mymap d1;
    d1.insert(Mymap::make_value(L'a', 1));
    d1.insert(Mymap::make_value(L'b', 2));
    d1.insert(Mymap::make_value(L'c', 3));
    Mycoll c1(%d1);

    // display contents "[a 1] [b 2] [c 3] "
    for each (Mypair elem in c1)
    {
        Mycoll::key_type key = elem.Key;
        Mycoll::mapped_type value = elem.Value;
        System::Console::Write("[{0} {1}] ", key, value);
    }
    System::Console::WriteLine();
    return (0);
}
```

```Output
[a 1] [b 2] [c 3]
```

## <a name="op_eq"></a> collection_adapter::operator = (STL/CLR)

Zastępuje przechowywane uchwyt BCL.

### <a name="syntax"></a>Składnia

```cpp
collection_adapter<Coll>% operator=(collection_adapter<Coll>% right);
```

#### <a name="parameters"></a>Parametry

*right*<br/>
Karty do skopiowania.

### <a name="remarks"></a>Uwagi

Kopiuje operator składowej *prawo* do obiektu, następnie zwraca `*this`. Umożliwia ona Zamień przechowywanych uchwyt BCL kopii przechowywanej uchwytu BCL *prawo*.

### <a name="example"></a>Przykład

```cpp
// cliext_collection_adapter_operator_as.cpp
// compile with: /clr
#include <cliext/adapter>
#include <cliext/deque>

typedef cliext::collection_adapter<
    System::Collections::ICollection> Mycoll;
int main()
{
    cliext::deque<wchar_t> d1;
    d1.push_back(L'a');
    d1.push_back(L'b');
    d1.push_back(L'c');
    Mycoll c1(%d1);

    // display initial contents "a b c "
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // assign to a new container
    Mycoll c2;
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

## <a name="reference"></a> collection_adapter::Reference (STL/CLR)

Typ odwołania do elementu.

### <a name="syntax"></a>Składnia

```cpp
typedef value_type% reference;
```

### <a name="remarks"></a>Uwagi

Typ opisuje odwołanie do elementu.

### <a name="example"></a>Przykład

```cpp
// cliext_collection_adapter_reference.cpp
// compile with: /clr
#include <cliext/adapter>
#include <cliext/deque>

typedef cliext::collection_adapter<
    System::Collections::ICollection> Mycoll;
int main()
    {
    cliext::deque<wchar_t> d1;
    d1.push_back(L'a');
    d1.push_back(L'b');
    d1.push_back(L'c');
    Mycoll c1(%d1);

    // display initial contents "a b c "
    Mycoll::iterator it = c1.begin();
    for (; it != c1.end(); ++it)
    {   // get a reference to an element
        Mycoll::reference ref = *it;
        System::Console::Write("{0} ", ref);
    }
    System::Console::WriteLine();
    return (0);
}
```

```Output
a b c
```

## <a name="size"></a> collection_adapter::size (STL/CLR)

Liczy liczbę elementów.

### <a name="syntax"></a>Składnia

```cpp
size_type size();
```

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca długość kontrolowanej sekwencji. Nie jest zdefiniowany w specjalizacji dla `IEnumerable` lub `IEnumerable<Value>`.

### <a name="example"></a>Przykład

```cpp
// cliext_collection_adapter_size.cpp
// compile with: /clr
#include <cliext/adapter>
#include <cliext/deque>

typedef cliext::collection_adapter<
    System::Collections::ICollection> Mycoll;
int main()
{
    cliext::deque<wchar_t> d6x(6, L'x');
    Mycoll c1(%d6x);

    // display initial contents "x x x x x x "
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    System::Console::WriteLine("size() = {0}", c1.size());
    return (0);
}
```

```Output
x x x x x x
size() = 6
```

## <a name="size_type"></a> collection_adapter::size_type (STL/CLR)

Typ odległości ze znakiem między dwoma elementu.

### <a name="syntax"></a>Składnia

```cpp
typedef int size_type;
```

### <a name="remarks"></a>Uwagi

Typ opisuje liczby nieujemnej wartości elementu.

### <a name="example"></a>Przykład

```cpp
// cliext_collection_adapter_size_type.cpp
// compile with: /clr
#include <cliext/adapter>
#include <cliext/deque>

typedef cliext::collection_adapter<
    System::Collections::ICollection> Mycoll;
int main()
{
    cliext::deque<wchar_t> d6x(6, L'x');
    Mycoll c1(%d6x);

    // display initial contents "x x x x x x"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    Mycoll::size_type size = c1.size();
    System::Console::WriteLine("size() = {0}", size);
    return (0);
}
```

```Output
x x x x x x
size() = 6
```

## <a name="swap"></a> collection_adapter::swap (STL/CLR)

Zamienia zawartości dwóch kontenerów.

### <a name="syntax"></a>Składnia

```cpp
void swap(collection_adapter<Coll>% right);
```

#### <a name="parameters"></a>Parametry

*right*<br/>
Kontener do wymiany zawartości z.

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zamienia przechowywanych uchwyty BCL między `*this` i *prawo*.

### <a name="example"></a>Przykład

```cpp
// cliext_collection_adapter_swap.cpp
// compile with: /clr
#include <cliext/adapter>
#include <cliext/deque>

typedef cliext::collection_adapter<
    System::Collections::ICollection> Mycoll;
int main()
{
    cliext::deque<wchar_t> d1;
    d1.push_back(L'a');
    d1.push_back(L'b');
    d1.push_back(L'c');
    Mycoll c1(%d1);

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct another container with repetition of values
    cliext::deque<wchar_t> d2(5, L'x');
    Mycoll c2(%d2);
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

## <a name="value_type"></a> collection_adapter::value_type (STL/CLR)

Typ elementu.

### <a name="syntax"></a>Składnia

```cpp
typedef Value value_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla parametru szablonu *wartość*, jeśli jest obecny w specjalizacji; w przeciwnym razie jest synonimem `System::Object^`.

### <a name="example"></a>Przykład

```cpp
// cliext_collection_adapter_value_type.cpp
// compile with: /clr
#include <cliext/adapter>
#include <cliext/deque>

typedef cliext::collection_adapter<
    System::Collections::ICollection> Mycoll;
int main()
{
    cliext::deque<wchar_t> d1;
    d1.push_back(L'a');
    d1.push_back(L'b');
    d1.push_back(L'c');
    Mycoll c1(%d1);

    // display contents "a b c" using value_type
    for (Mycoll::iterator it = c1.begin();
        it != c1.end(); ++it)
    {   // store element in value_type object
        Mycoll::value_type val = *it;

        System::Console::Write("{0} ", val);
    }
    System::Console::WriteLine();
    return (0);
}
```

```Output
a b c
```

## <a name="make_collection"></a> make_collection — (STL/CLR)

Wprowadź `range_adapter` z pary iteratora.

### <a name="syntax"></a>Składnia

```cpp
template<typename Iter>
    range_adapter<Iter> make_collection(Iter first, Iter last);
```

#### <a name="parameters"></a>Parametry

*ITER*<br/>
Typ opakowany Iteratory.

*pierwszy*<br/>
Pierwszy iterator do opakowania.

*ostatni*<br/>
Drugi iterator do opakowania.

### <a name="remarks"></a>Uwagi

Funkcja szablonu zwraca `gcnew range_adapter<Iter>(first, last)`. Służy do konstruowania `range_adapter<Iter>` obiekt z parę iteratorów.

### <a name="example"></a>Przykład

```cpp
// cliext_make_collection.cpp
// compile with: /clr
#include <cliext/adapter>
#include <cliext/deque>

typedef cliext::deque<wchar_t> Mycont;
typedef cliext::range_adapter<Mycont::iterator> Myrange;
int main()
{
    cliext::deque<wchar_t> d1;
    d1.push_back(L'a');
    d1.push_back(L'b');
    d1.push_back(L'c');

    // display contents " a b c"
    for each (wchar_t elem in d1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    System::Collections::ICollection^ p1 =
        cliext::make_collection(d1.begin(), d1.end());
    System::Console::WriteLine("Count = {0}", p1->Count);
    System::Console::WriteLine("IsSynchronized = {0}",
        p1->IsSynchronized);
    System::Console::WriteLine("SyncRoot not nullptr = {0}",
        p1->SyncRoot != nullptr);

    // copy the sequence
    cli::array<System::Object^>^ a1 = gcnew cli::array<System::Object^>(5);

    a1[0] = L'|';
    p1->CopyTo(a1, 1);
    a1[4] = L'|';
    for each (wchar_t elem in a1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    return (0);
}
```

```Output
a b c
Count = 3
IsSynchronized = False
SyncRoot not nullptr = True
| a b c |
```

## <a name="range_adapter"></a> range_adapter — (STL/CLR)

Klasa szablonu, który otacza parę iteratorów, które są używane do implementowania kilka interfejsów Biblioteka klasy podstawowej (BCL). Range_adapter — służy do manipulowania zakresu STL/CLR, tak jakby kolekcji BCL.

### <a name="syntax"></a>Składnia

```cpp
template<typename Iter>
    ref class range_adapter
        :   public
        System::Collections::IEnumerable,
        System::Collections::ICollection,
        System::Collections::Generic::IEnumerable<Value>,
        System::Collections::Generic::ICollection<Value>
    { ..... };
```

#### <a name="parameters"></a>Parametry

*ITER*<br/>
Typ skojarzony z iteratorami opakowana.

### <a name="members"></a>Elementy członkowskie

|Funkcja elementów członkowskich|Opis|
|---------------------|-----------------|
|[range_adapter::range_adapter (STL/CLR)](#range_adapter_range_adapter)|Konstruuje obiekt karty.|

|Operator|Opis|
|--------------|-----------------|
|[range_adapter::operator= (STL/CLR)](#range_adapter_op_eq)|Zastępuje pary przechowywany iterator.|

### <a name="interfaces"></a>Interfejsy

|Interface|Opis|
|---------------|-----------------|
|<xref:System.Collections.IEnumerable>|Wykonuje iterację przez elementy w kolekcji.|
|<xref:System.Collections.ICollection>|Przechowuje grupy elementów.|
|<xref:System.Collections.Generic.IEnumerable%601>|Wykonuje iterację typizowanych elementów w kolekcji...|
|<xref:System.Collections.Generic.ICollection%601>|Przechowuje grupy typizowanych elementów.|

### <a name="remarks"></a>Uwagi

Range_adapter — przechowuje parę iteratorów, które z kolei określają sekwencję elementów. Obiekt implementuje cztery interfejsów BCL, które pozwalają iterowania po elementach, w kolejności. Użyjesz tej klasy szablonu do manipulowania zakresów STL/CLR, podobnie jak kontenery BCL.

## <a name="range_adapter_op_eq"></a> range_adapter::operator = (STL/CLR)

Zastępuje pary przechowywany iterator.

### <a name="syntax"></a>Składnia

```cpp
range_adapter<Iter>% operator=(range_adapter<Iter>% right);
```

#### <a name="parameters"></a>Parametry

*right*<br/>
Karty do skopiowania.

### <a name="remarks"></a>Uwagi

Kopiuje operator składowej *prawo* do obiektu, następnie zwraca `*this`. Umożliwia ona Zamień pary przechowywanego iteratora kopię pary przechowywanego iteratora w *prawo*.

### <a name="example"></a>Przykład

```cpp
// cliext_range_adapter_operator_as.cpp
// compile with: /clr
#include <cliext/adapter>
#include <cliext/deque>

typedef cliext::deque<wchar_t> Mycont;
typedef cliext::range_adapter<Mycont::iterator> Myrange;
int main()
{
    cliext::deque<wchar_t> d1;
    d1.push_back(L'a');
    d1.push_back(L'b');
    d1.push_back(L'c');
    Myrange c1(d1.begin(), d1.end());

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // assign to a new container
    Myrange c2;
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

## <a name="range_adapter_range_adapter"></a> range_adapter::range_adapter (STL/CLR)

Konstruuje obiekt karty.

### <a name="syntax"></a>Składnia

```cpp
range_adapter();
range_adapter(range_adapter<Iter>% right);
range_adapter(range_adapter<Iter>^ right);
range_adapter(Iter first, Iter last);
```

#### <a name="parameters"></a>Parametry

*pierwszy*<br/>
Pierwszy iterator do opakowania.

*ostatni*<br/>
Drugi iterator do opakowania.

*right*<br/>
Obiekt do skopiowania.

### <a name="remarks"></a>Uwagi

Konstruktor:

`range_adapter();`

Inicjuje pary przechowywanego iteratora, z iteratorami domyślne.

Konstruktor:

`range_adapter(range_adapter<Iter>% right);`

Inicjuje pary przechowywanego iteratora, kopiując pary przechowywane w *prawo*.

Konstruktor:

`range_adapter(range_adapter<Iter>^ right);`

Inicjuje pary przechowywanego iteratora, kopiując pary przechowywane w `*right`.

Konstruktor:

`range_adapter(Iter^ first, last);`

Inicjuje pary przechowywanego iteratora, z *pierwszy* i *ostatniego*.

### <a name="example"></a>Przykład

```cpp
// cliext_range_adapter_construct.cpp
// compile with: /clr
#include <cliext/adapter>
#include <cliext/deque>

typedef cliext::deque<wchar_t> Mycont;
typedef cliext::range_adapter<Mycont::iterator> Myrange;
int main()
{
    cliext::deque<wchar_t> d1;
    d1.push_back(L'a');
    d1.push_back(L'b');
    d1.push_back(L'c');

    // construct an empty adapter
    Myrange c1;

    // construct with an iterator pair
    Myrange c2(d1.begin(), d1.end());
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct by copying another adapter
    Myrange c3(c2);
    for each (wchar_t elem in c3)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct by copying an adapter handle
    Myrange c4(%c3);
    for each (wchar_t elem in c4)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    return (0);
}
```

```Output
a b c
a b c
a b c
```
