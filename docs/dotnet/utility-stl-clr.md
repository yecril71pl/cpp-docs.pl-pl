---
title: utility (STL/CLR)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- <cliext/utility>
- cliext::pair
- cliext::pair::pair
- cliext::pair::first
- cliext::pair::first_type
- cliext::pair::second
- cliext::pair::second_type
- cliext::pair::swap
- cliext::make_pair
- cliext::pair::operator=
- cliext::pair::operator==
- cliext::pair::operator>=
- cliext::pair::operator>
- cliext::pair::operator!=
- cliext::pair::operator<=
- cliext::pair::operator<
helpviewer_keywords:
- <utility> header [STL/CLR]
- utility header [STL/CLR]
- <cliext/utility> header [STL/CLR]
- first member [STL/CLR]
- first_type member [STL/CLR]
- second member [STL/CLR]
- second_type member [STL/CLR]
- swap member [STL/CLR]
- make_pair function [STL/CLR]
- pair class [STL/CLR]
- pair member [STL/CLR]
- operator== member [STL/CLR]
- operator= member [STL/CLR]
- operator>= member [STL/CLR]
- operator> member [STL/CLR]
- operator!= member [STL/CLR]
- operator<= member [STL/CLR]
- operator< member [STL/CLR]
ms.assetid: fb48cb75-d5ef-47ce-b526-bf60dc86c552
ms.openlocfilehash: b21f9ec2ace54281f30f8f32134c7fb3466a1faa
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87214857"
---
# <a name="utility-stlclr"></a>utility (STL/CLR)

Dołącz nagłówek STL/CLR `<cliext/utility>` w celu zdefiniowania klasy szablonu `pair` i kilku funkcji szablonu pomocniczego.

## <a name="syntax"></a>Składnia

```cpp
#include <utility>
```

## <a name="requirements"></a>Wymagania

**Nagłówek:**\<cliext/utility>

**Przestrzeń nazw:** cliext

## <a name="declarations"></a>Deklaracje

|Klasa|Opis|
|-----------|-----------------|
|[pair (STL/CLR)](#pair)|Zawiń parę elementów.|

|Operator|Opis|
|--------------|-----------------|
|[operator== (pair) (STL/CLR)](#op_eq)|Porównanie równości pary.|
|[operator! = (para) (STL/CLR)](#op_neq)|Para nie jest równa porównaniu.|
|[< operatora (para) (STL/CLR)](#op_lt)|Para jest mniejsza niż porównanie.|
|[operator \< = (para) (STL/CLR)](#op_lteq)|Para jest mniejsza niż lub równa.|
|[> operatora (para) (STL/CLR)](#op_gt)|Para większa niż porównanie.|
|[operator>= (para) (STL/CLR)](#op_gteq)|Para większa niż lub równa porównywania.|

|Funkcja|Opis|
|--------------|-----------------|
|[make_pair (STL/CLR)](#make_pair)|Utwórz parę z pary wartości.|

## <a name="members"></a>Elementy członkowskie

## <a name="pair-stlclr"></a><a name="pair"></a>para (STL/CLR)

Klasa szablonu opisuje obiekt, który zawija parę wartości.

### <a name="syntax"></a>Składnia

```cpp
template<typename Value1,
    typename Value2>
    ref class pair;
```

#### <a name="parameters"></a>Parametry

*Sekwencj*<br/>
Typ pierwszej opakowanej wartości.

*Wartość2*<br/>
Typ drugiej opakowanej wartości.

## <a name="members"></a>Elementy członkowskie

|Definicja typu|Opis|
|---------------------|-----------------|
|[pair::first_type (STL/CLR)](#first_type)|Typ pierwszej opakowanej wartości.|
|[pair::second_type (STL/CLR)](#second_type)|Typ drugiej opakowanej wartości.|

|Obiekt członkowski|Opis|
|-------------------|-----------------|
|[pair::first (STL/CLR)](#first)|Pierwsza przechowywana wartość.|
|[pair::second (STL/CLR)](#second)|Druga przechowywana wartość.|

|Funkcja elementów członkowskich|Opis|
|---------------------|-----------------|
|[pair::pair (STL/CLR)](#pair_pair)|Konstruuje obiekt pary.|
|[pair::swap (STL/CLR)](#swap)|Zamienia zawartość dwóch par.|

|Operator|Opis|
|--------------|-----------------|
|[pair::operator= (STL/CLR)](#op_as)|Zastępuje składowaną parę wartości.|

## <a name="remarks"></a>Uwagi

Obiekt przechowuje parę wartości. Ta klasa szablonu służy do łączenia dwóch wartości w jeden obiekt. Ponadto obiekt `cliext::pair` (opisany tutaj) przechowuje tylko typy zarządzane; aby można było przechowywać parę typów niezarządzanych `std::pair` , zadeklarowanych w `<utility>` .

## <a name="pairfirst-stlclr"></a><a name="first"></a>para:: First (STL/CLR)

Pierwsza opakowana wartość.

### <a name="syntax"></a>Składnia

```cpp
Value1 first;
```

### <a name="remarks"></a>Uwagi

Obiekt przechowuje pierwszą opakowaną wartość.

### <a name="example"></a>Przykład

```cpp
// cliext_pair_first.cpp
// compile with: /clr
#include <cliext/utility>

int main()
    {
    cliext::pair<wchar_t, int> c1(L'x', 3);
    System::Console::WriteLine("[{0}, {1}]", c1.first, c1.second);

    cliext::pair<wchar_t, int>::first_type first_val = c1.first;
    cliext::pair<wchar_t, int>::second_type second_val = c1.second;
    System::Console::WriteLine("[{0}, {1}]", first_val, second_val);
    return (0);
    }
```

```Output
[x, 3]
```

## <a name="pairfirst_type-stlclr"></a><a name="first_type"></a>para:: first_type (STL/CLR)

Typ pierwszej opakowanej wartości.

### <a name="syntax"></a>Składnia

```cpp
typedef Value1 first_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla parametru szablonu *wartość1*.

### <a name="example"></a>Przykład

```cpp
// cliext_pair_first_type.cpp
// compile with: /clr
#include <cliext/utility>

int main()
    {
    cliext::pair<wchar_t, int> c1(L'x', 3);
    System::Console::WriteLine("[{0}, {1}]", c1.first, c1.second);

    cliext::pair<wchar_t, int>::first_type first_val = c1.first;
    cliext::pair<wchar_t, int>::second_type second_val = c1.second;
    System::Console::WriteLine("[{0}, {1}]", first_val, second_val);
    return (0);
    }
```

```Output
[x, 3]
```

## <a name="pairoperator-stlclr"></a><a name="op_as"></a>para:: operator = (STL/CLR)

Zastępuje składowaną parę wartości.

### <a name="syntax"></a>Składnia

```cpp
pair<Value1, Value2>% operator=(pair<Value1, Value2>% right);
```

#### <a name="parameters"></a>Parametry

*Kliknij*<br/>
Para do skopiowania.

### <a name="remarks"></a>Uwagi

Operator elementu członkowskiego kopiuje *prawo* do obiektu, a następnie zwraca **`*this`** . Służy do zamienienia przechowywanej pary wartości z kopią przechowywanej pary wartości w *prawo*.

### <a name="example"></a>Przykład

```cpp
// cliext_pair_operator_as.cpp
// compile with: /clr
#include <cliext/utility>

int main()
    {
    cliext::pair<wchar_t, int> c1(L'x', 3);
    System::Console::WriteLine("[{0}, {1}]", c1.first, c1.second);

// assign to a new pair
    cliext::pair<wchar_t, int> c2;
    c2 = c1;
    System::Console::WriteLine("[{0}, {1}]", c2.first, c2.second);
    return (0);
    }
```

```Output
[x, 3]
[x, 3]
```

## <a name="pairpair-stlclr"></a><a name="pair_pair"></a>para::p powietrze (STL/CLR)

Konstruuje obiekt pary.

### <a name="syntax"></a>Składnia

```cpp
pair();
pair(pair<Coll>% right);
pair(pair<Coll>^ right);
pair(Value1 val1, Value2 val2);
```

#### <a name="parameters"></a>Parametry

*Kliknij*<br/>
Para do zapisania.

*Val1*<br/>
Pierwsza wartość do zapisania.

*val2*<br/>
Druga wartość do zapisania.

### <a name="remarks"></a>Uwagi

Konstruktor:

`pair();`

Inicjuje składowaną parę z domyślnymi skonstruowanymi wartościami.

Konstruktor:

`pair(pair<Value1, Value2>% right);`

Inicjuje składowaną parę z `right.` [parą:: First (STL/CLR)](../dotnet/pair-first-stl-clr.md) i `right.` [parę:: Second (STL/CLR)](../dotnet/pair-second-stl-clr.md).

`pair(pair<Value1, Value2>^ right);`

Inicjuje składowaną parę z `right->` [parą:: First (STL/CLR)](../dotnet/pair-first-stl-clr.md) i `right>` [parę:: Second (STL/CLR)](../dotnet/pair-second-stl-clr.md).

Konstruktor:

`pair(Value1 val1, Value2 val2);`

Inicjuje składowaną parę z *Val1* i *val2*.

### <a name="example"></a>Przykład

```cpp
// cliext_pair_construct.cpp
// compile with: /clr
#include <cliext/utility>

int main()
    {
// construct an empty container
    cliext::pair<wchar_t, int> c1;
    System::Console::WriteLine("[{0}, {1}]",
        c1.first == L'\0' ? "\\0" : "??", c1.second);

// construct with a pair of values
    cliext::pair<wchar_t, int> c2(L'x', 3);
    System::Console::WriteLine("[{0}, {1}]", c2.first, c2.second);

// construct by copying another pair
    cliext::pair<wchar_t, int> c3(c2);
    System::Console::WriteLine("[{0}, {1}]", c3.first, c3.second);

// construct by copying a pair handle
    cliext::pair<wchar_t, int> c4(%c3);
    System::Console::WriteLine("[{0}, {1}]", c4.first, c4.second);

    return (0);
    }
```

```Output
[\0, 0]
[x, 3]
[x, 3]
[x, 3]
```

## <a name="pairsecond-stlclr"></a><a name="second"></a>para:: Second (STL/CLR)

Druga opakowana wartość.

### <a name="syntax"></a>Składnia

```cpp
Value2 second;
```

### <a name="remarks"></a>Uwagi

Obiekt przechowuje drugą opakowaną wartość.

### <a name="example"></a>Przykład

```cpp
// cliext_pair_second.cpp
// compile with: /clr
#include <cliext/utility>

int main()
    {
    cliext::pair<wchar_t, int> c1(L'x', 3);
    System::Console::WriteLine("[{0}, {1}]", c1.first, c1.second);

    cliext::pair<wchar_t, int>::first_type first_val = c1.first;
    cliext::pair<wchar_t, int>::second_type second_val = c1.second;
    System::Console::WriteLine("[{0}, {1}]", first_val, second_val);
    return (0);
    }
```

```Output
[x, 3]
```

## <a name="pairsecond_type-stlclr"></a><a name="second_type"></a>para:: second_type (STL/CLR)

Typ drugiej opakowanej wartości.

### <a name="syntax"></a>Składnia

```cpp
typedef Value2 second_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla parametru szablonu *wartość2*.

### <a name="example"></a>Przykład

```cpp
// cliext_pair_second_type.cpp
// compile with: /clr
#include <cliext/utility>

int main()
    {
    cliext::pair<wchar_t, int> c1(L'x', 3);
    System::Console::WriteLine("[{0}, {1}]", c1.first, c1.second);

    cliext::pair<wchar_t, int>::first_type first_val = c1.first;
    cliext::pair<wchar_t, int>::second_type second_val = c1.second;
    System::Console::WriteLine("[{0}, {1}]", first_val, second_val);
    return (0);
    }
```

```Output
[x, 3]
```

## <a name="pairswap-stlclr"></a><a name="swap"></a>para:: swap (STL/CLR)

Zamienia zawartość dwóch par.

### <a name="syntax"></a>Składnia

```cpp
void swap(pair<Value1, Value2>% right);
```

#### <a name="parameters"></a>Parametry

*Kliknij*<br/>
Para do zamiany zawartości na.

### <a name="remarks"></a>Uwagi

Funkcja członkowska zamienia składowaną parę wartości między **`*this`** i *po prawej*.

### <a name="example"></a>Przykład

```cpp
// cliext_pair_swap.cpp
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

## <a name="make_pair-stlclr"></a><a name="make_pair"></a>make_pair (STL/CLR)

Utwórz `pair` z pary wartości.

### <a name="syntax"></a>Składnia

```cpp
template<typename Value1,
    typename Value2>
    pair<Value1, Value2> make_pair(Value1 first, Value2 second);
```

#### <a name="parameters"></a>Parametry

*Sekwencj*<br/>
Typ pierwszej opakowanej wartości.

*Wartość2*<br/>
Typ drugiej opakowanej wartości.

*pierwszego*<br/>
Pierwsza wartość do zawinięcia.

*drugi*<br/>
Druga wartość do zawinięcia.

### <a name="remarks"></a>Uwagi

Funkcja szablonu zwraca wartość `pair<Value1, Value2>(first, second)` . Służy do konstruowania obiektu na `pair<Value1, Value2>` podstawie pary wartości.

### <a name="example"></a>Przykład

```cpp
// cliext_make_pair.cpp
// compile with: /clr
#include <cliext/utility>

int main()
    {
    cliext::pair<wchar_t, int> c1(L'x', 3);
    System::Console::WriteLine("[{0}, {1}]", c1.first, c1.second);

    c1 = cliext::make_pair(L'y', 4);
    System::Console::WriteLine("[{0}, {1}]", c1.first, c1.second);
    return (0);
    }
```

```Output
[x, 3]
[y, 4]
```

## <a name="operator-pair-stlclr"></a><a name="op_neq"></a>operator! = (para) (STL/CLR)

Para nie jest równa porównaniu.

### <a name="syntax"></a>Składnia

```cpp
template<typename Value1,
    typename Value2>
    bool operator!=(pair<Value1, Value2>% left,
        pair<Value1, Value2>% right);
```

#### <a name="parameters"></a>Parametry

*lewym*<br/>
Lewa para do porównania.

*Kliknij*<br/>
Prawa para do porównania.

### <a name="remarks"></a>Uwagi

Funkcja operatora zwraca wartość `!(left == right)` . Służy do sprawdzania, czy *lewo* nie jest uporządkowane *tak samo, jak w* przypadku porównywania dwóch par elementów według elementu.

### <a name="example"></a>Przykład

```cpp
// cliext_pair_operator_ne.cpp
// compile with: /clr
#include <cliext/utility>

int main()
    {
    cliext::pair<wchar_t, int> c1(L'x', 3);
    System::Console::WriteLine("[{0}, {1}]", c1.first, c1.second);
    cliext::pair<wchar_t, int> c2(L'x', 4);
    System::Console::WriteLine("[{0}, {1}]", c2.first, c2.second);

    System::Console::WriteLine("[x 3] != [x 3] is {0}",
        c1 != c1);
    System::Console::WriteLine("[x 3] != [x 4] is {0}",
        c1 != c2);
    return (0);
    }
```

```Output
[x, 3]
[x, 4]
[x 3] != [x 3] is False
[x 3] != [x 4] is True
```

## <a name="operatorlt-pair-stlclr"></a><a name="op_lt"></a>operator &lt; (para) (STL/CLR)

Para jest mniejsza niż porównanie.

### <a name="syntax"></a>Składnia

```cpp
template<typename Value1,
    typename Value2>
    bool operator<(pair<Value1, Value2>% left,
        pair<Value1, Value2>% right);
```

#### <a name="parameters"></a>Parametry

*lewym*<br/>
Lewa para do porównania.

*Kliknij*<br/>
Prawa para do porównania.

### <a name="remarks"></a>Uwagi

Funkcja operatora zwraca wartość `left.first <` `right.first || !(right.first <` `left.first &&` `left.second <` `right.second` . Służy do sprawdzania, czy *lewa* jest uporządkowana przed *prawem* , gdy dwie pary są porównywane elementy według elementu.

### <a name="example"></a>Przykład

```cpp
// cliext_pair_operator_lt.cpp
// compile with: /clr
#include <cliext/utility>

int main()
    {
    cliext::pair<wchar_t, int> c1(L'x', 3);
    System::Console::WriteLine("[{0}, {1}]", c1.first, c1.second);
    cliext::pair<wchar_t, int> c2(L'x', 4);
    System::Console::WriteLine("[{0}, {1}]", c2.first, c2.second);

    System::Console::WriteLine("[x 3] < [x 3] is {0}",
        c1 < c1);
    System::Console::WriteLine("[x 3] < [x 4] is {0}",
        c1 < c2);
    return (0);
    }
```

```Output
[x, 3]
[x, 4]
[x 3] < [x 3] is False
[x 3] < [x 4] is True
```

## <a name="operatorlt-pair-stlclr"></a><a name="op_lteq"></a>operator &lt; = (para) (STL/CLR)

Para jest mniejsza niż lub równa.

### <a name="syntax"></a>Składnia

```cpp
template<typename Value1,
    typename Value2>
    bool operator<=(pair<Value1, Value2>% left,
        pair<Value1, Value2>% right);
```

#### <a name="parameters"></a>Parametry

*lewym*<br/>
Lewa para do porównania.

*Kliknij*<br/>
Prawa para do porównania.

### <a name="remarks"></a>Uwagi

Funkcja operatora zwraca wartość `!(right < left)` . Służy do sprawdzania *, czy nie* jest on uporządkowany po *prawej stronie* , gdy dwie pary są porównywane elementów według elementu.

### <a name="example"></a>Przykład

```cpp
// cliext_pair_operator_le.cpp
// compile with: /clr
#include <cliext/utility>

int main()
    {
    cliext::pair<wchar_t, int> c1(L'x', 3);
    System::Console::WriteLine("[{0}, {1}]", c1.first, c1.second);
    cliext::pair<wchar_t, int> c2(L'x', 4);
    System::Console::WriteLine("[{0}, {1}]", c2.first, c2.second);

    System::Console::WriteLine("[x 3] <= [x 3] is {0}",
        c1 <= c1);
    System::Console::WriteLine("[x 4] <= [x 3] is {0}",
        c2 <= c1);
    return (0);
    }
```

```Output
[x, 3]
[x, 4]
[x 3] <= [x 3] is True
[x 4] <= [x 3] is False
```

## <a name="operator-pair-stlclr"></a><a name="op_eq"></a>operator = = (para) (STL/CLR)

Porównanie równości pary.

### <a name="syntax"></a>Składnia

```cpp
template<typename Value1,
    typename Value2>
    bool operator==(pair<Value1, Value2>% left,
        pair<Value1, Value2>% right);
```

#### <a name="parameters"></a>Parametry

*lewym*<br/>
Lewa para do porównania.

*Kliknij*<br/>
Prawa para do porównania.

### <a name="remarks"></a>Uwagi

Funkcja operatora zwraca wartość `left.first ==` `right.first &&` `left.second ==` `right.second` . Służy do sprawdzania, czy *lewa* jest uporządkowana *tak samo jak w* przypadku porównywania dwóch par elementów według elementu.

### <a name="example"></a>Przykład

```cpp
// cliext_pair_operator_eq.cpp
// compile with: /clr
#include <cliext/utility>

int main()
    {
    cliext::pair<wchar_t, int> c1(L'x', 3);
    System::Console::WriteLine("[{0}, {1}]", c1.first, c1.second);
    cliext::pair<wchar_t, int> c2(L'x', 4);
    System::Console::WriteLine("[{0}, {1}]", c2.first, c2.second);

    System::Console::WriteLine("[x 3] == [x 3] is {0}",
        c1 == c1);
    System::Console::WriteLine("[x 3] == [x 4] is {0}",
        c1 == c2);
    return (0);
    }
```

```Output
[x, 3]
[x, 4]
[x 3] == [x 3] is True
[x 3] == [x 4] is False
```

## <a name="operatorgt-pair-stlclr"></a><a name="op_gt"></a>operator &gt; (para) (STL/CLR)

Para większa niż porównanie.

### <a name="syntax"></a>Składnia

```cpp
template<typename Value1,
    typename Value2>
    bool operator>(pair<Value1, Value2>% left,
        pair<Value1, Value2>% right);
```

#### <a name="parameters"></a>Parametry

*lewym*<br/>
Lewa para do porównania.

*Kliknij*<br/>
Prawa para do porównania.

### <a name="remarks"></a>Uwagi

Funkcja operatora zwraca wartość `right` `<` `left` . Służy do sprawdzania, czy *lewa* jest uporządkowana po *prawej* , gdy dwie pary są porównywane elementów według elementu.

### <a name="example"></a>Przykład

```cpp
// cliext_pair_operator_gt.cpp
// compile with: /clr
#include <cliext/utility>

int main()
    {
    cliext::pair<wchar_t, int> c1(L'x', 3);
    System::Console::WriteLine("[{0}, {1}]", c1.first, c1.second);
    cliext::pair<wchar_t, int> c2(L'x', 4);
    System::Console::WriteLine("[{0}, {1}]", c2.first, c2.second);

    System::Console::WriteLine("[x 3] > [x 3] is {0}",
        c1 > c1);
    System::Console::WriteLine("[x 4] > [x 3] is {0}",
        c2 > c1);
    return (0);
    }
```

```Output
[x, 3]
[x, 4]
[x 3] > [x 3] is False
[x 4] > [x 3] is True
```

## <a name="operatorgt-pair-stlclr"></a><a name="op_gteq"></a>operator &gt; = (para) (STL/CLR)

Para większa niż lub równa porównywania.

### <a name="syntax"></a>Składnia

```cpp
template<typename Value1,
    typename Value2>
    bool operator>=(pair<Value1, Value2>% left,
        pair<Value1, Value2>% right);
```

#### <a name="parameters"></a>Parametry

*lewym*<br/>
Lewa para do porównania.

*Kliknij*<br/>
Prawa para do porównania.

### <a name="remarks"></a>Uwagi

Funkcja operatora zwraca wartość `!(left < right)` . Służy do sprawdzania, czy nie *jest on* uporządkowany przed *prawem* , gdy dwie pary są porównywane elementów według elementu.

### <a name="example"></a>Przykład

```cpp
// cliext_pair_operator_ge.cpp
// compile with: /clr
#include <cliext/utility>

int main()
    {
    cliext::pair<wchar_t, int> c1(L'x', 3);
    System::Console::WriteLine("[{0}, {1}]", c1.first, c1.second);
    cliext::pair<wchar_t, int> c2(L'x', 4);
    System::Console::WriteLine("[{0}, {1}]", c2.first, c2.second);

    System::Console::WriteLine("[x 3] >= [x 3] is {0}",
        c1 >= c1);
    System::Console::WriteLine("[x 3] >= [x 4] is {0}",
        c1 >= c2);
    return (0);
    }
```

```Output
[x, 3]
[x, 4]
[x 3] >= [x 3] is True
[x 3] >= [x 4] is False
```
