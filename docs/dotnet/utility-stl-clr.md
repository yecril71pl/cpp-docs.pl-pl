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
ms.openlocfilehash: 6d025230abcff42e367a231e616a13f0f8c684f0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81320287"
---
# <a name="utility-stlclr"></a>utility (STL/CLR)

Dołącz nagłówek `<cliext/utility>` STL/CLR, aby `pair` zdefiniować klasę szablonu i kilka funkcji szablonu pomocniczego.

## <a name="syntax"></a>Składnia

```cpp
#include <utility>
```

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<cliext /> użytkowej

**Obszar nazw:** cliext

## <a name="declarations"></a>Deklaracje

|Klasa|Opis|
|-----------|-----------------|
|[pair (STL/CLR)](#pair)|Zawiń parę elementów.|

|Operator|Opis|
|--------------|-----------------|
|[operator== (pair) (STL/CLR)](#op_eq)|Sparuj równe porównanie.|
|[operator!= (para) (STL/CLR)](#op_neq)|Para nie równa porównanie.|
|[operator< (para) (STL/CLR)](#op_lt)|Para mniej niż porównanie.|
|[operator\<= (para) (STL/CLR)](#op_lteq)|Sparuj mniej niż lub równe porównanie.|
|[operator> (para) (STL/CLR)](#op_gt)|Para większa niż porównanie.|
|[operator>= (para) (STL/CLR)](#op_gteq)|Paruj porównanie większe lub równe.|

|Funkcja|Opis|
|--------------|-----------------|
|[make_pair (STL/CLR)](#make_pair)|Zrób parę z pary wartości.|

## <a name="members"></a>Elementy członkowskie

## <a name="pair-stlclr"></a><a name="pair"></a>par (STL/CLR)

Klasa szablonu opisuje obiekt, który zawija parę wartości.

### <a name="syntax"></a>Składnia

```cpp
template<typename Value1,
    typename Value2>
    ref class pair;
```

#### <a name="parameters"></a>Parametry

*Wartość1*<br/>
Typ pierwszej wartości zawiniętej.

*Wartość2*<br/>
Typ drugiej wartości zawiniętej.

## <a name="members"></a>Elementy członkowskie

|Definicja typu|Opis|
|---------------------|-----------------|
|[pair::first_type (STL/CLR)](#first_type)|Typ pierwszej wartości zawiniętej.|
|[pair::second_type (STL/CLR)](#second_type)|Typ drugiej wartości zawiniętej.|

|Obiekt elementu członkowskiego|Opis|
|-------------------|-----------------|
|[pair::first (STL/CLR)](#first)|Pierwsza przechowywana wartość.|
|[pair::second (STL/CLR)](#second)|Druga przechowywana wartość.|

|Funkcja elementów członkowskich|Opis|
|---------------------|-----------------|
|[pair::pair (STL/CLR)](#pair_pair)|Konstruuje obiekt pary.|
|[pair::swap (STL/CLR)](#swap)|Zamienia zawartość dwóch par.|

|Operator|Opis|
|--------------|-----------------|
|[pair::operator= (STL/CLR)](#op_as)|Zastępuje przechowywaną parę wartości.|

## <a name="remarks"></a>Uwagi

Obiekt przechowuje parę wartości. Ta klasa szablonu służy do łączenia dwóch wartości w jeden obiekt. Ponadto obiekt `cliext::pair` (opisane w tym miejscu) przechowuje tylko typy zarządzane; , aby zapisać parę typów `std::pair`niezarządzanych , zadeklarowanych w `<utility>`.

## <a name="pairfirst-stlclr"></a><a name="first"></a>para::pierwszy (STL/CLR)

Pierwsza opakowana wartość.

### <a name="syntax"></a>Składnia

```cpp
Value1 first;
```

### <a name="remarks"></a>Uwagi

Obiekt przechowuje pierwszą wartość opakowane.

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

## <a name="pairfirst_type-stlclr"></a><a name="first_type"></a>para::first_type (STL/CLR)

Typ pierwszej wartości zawiniętej.

### <a name="syntax"></a>Składnia

```cpp
typedef Value1 first_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem parametru szablonu *Value1*.

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

## <a name="pairoperator-stlclr"></a><a name="op_as"></a>para::operator= (STL/CLR)

Zastępuje przechowywaną parę wartości.

### <a name="syntax"></a>Składnia

```cpp
pair<Value1, Value2>% operator=(pair<Value1, Value2>% right);
```

#### <a name="parameters"></a>Parametry

*Prawo*<br/>
Para do skopiowania.

### <a name="remarks"></a>Uwagi

Operator elementu członkowskiego kopiuje *prawo* `*this`do obiektu, a następnie zwraca . Służy do zastąpienia zapisanej pary wartości kopią zapisanej pary wartości w *prawej*.

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

## <a name="pairpair-stlclr"></a><a name="pair_pair"></a>para::pair (STL/CLR)

Konstruuje obiekt pary.

### <a name="syntax"></a>Składnia

```cpp
pair();
pair(pair<Coll>% right);
pair(pair<Coll>^ right);
pair(Value1 val1, Value2 val2);
```

#### <a name="parameters"></a>Parametry

*Prawo*<br/>
Sparuj do przechowywania.

*val1*<br/>
Pierwsza wartość do przechowywania.

*val2 (val2)*<br/>
Druga wartość do zapisania.

### <a name="remarks"></a>Uwagi

Konstruktor:

`pair();`

inicjuje zapisaną parę z domyślnymi wartościami konstruowanymi.

Konstruktor:

`pair(pair<Value1, Value2>% right);`

inicjuje przechowywaną `right.`parę z [parą::first (STL/CLR)](../dotnet/pair-first-stl-clr.md) i `right.` [parą::second (STL/CLR)](../dotnet/pair-second-stl-clr.md).

`pair(pair<Value1, Value2>^ right);`

inicjuje przechowywaną `right->`parę z [parą::first (STL/CLR)](../dotnet/pair-first-stl-clr.md) i `right>` [parą::second (STL/CLR)](../dotnet/pair-second-stl-clr.md).

Konstruktor:

`pair(Value1 val1, Value2 val2);`

inicjuje przechowywaną parę z *val1* i *val2*.

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

## <a name="pairsecond-stlclr"></a><a name="second"></a>para::second (STL/CLR)

Druga opakowana wartość.

### <a name="syntax"></a>Składnia

```cpp
Value2 second;
```

### <a name="remarks"></a>Uwagi

Obiekt przechowuje drugą wartość opakowane.

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

## <a name="pairsecond_type-stlclr"></a><a name="second_type"></a>para::second_type (STL/CLR)

Typ drugiej wartości zawiniętej.

### <a name="syntax"></a>Składnia

```cpp
typedef Value2 second_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem parametru szablonu *Value2*.

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

## <a name="pairswap-stlclr"></a><a name="swap"></a>para::swap (STL/CLR)

Zamienia zawartość dwóch par.

### <a name="syntax"></a>Składnia

```cpp
void swap(pair<Value1, Value2>% right);
```

#### <a name="parameters"></a>Parametry

*Prawo*<br/>
Sparuj, aby zamienić zawartość.

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zamienia zapisaną `*this` parę wartości między i *w prawo*.

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

Zrób `pair` z pary wartości.

### <a name="syntax"></a>Składnia

```cpp
template<typename Value1,
    typename Value2>
    pair<Value1, Value2> make_pair(Value1 first, Value2 second);
```

#### <a name="parameters"></a>Parametry

*Wartość1*<br/>
Typ pierwszej wartości zawiniętej.

*Wartość2*<br/>
Typ drugiej wartości zawiniętej.

*Pierwszym*<br/>
Pierwsza wartość do zawijania.

*Drugi*<br/>
Druga wartość do zawijania.

### <a name="remarks"></a>Uwagi

Funkcja szablonu `pair<Value1, Value2>(first, second)`zwraca . Służy do konstruowania `pair<Value1, Value2>` obiektu z pary wartości.

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

## <a name="operator-pair-stlclr"></a><a name="op_neq"></a>operator!= (para) (STL/CLR)

Para nie równa porównanie.

### <a name="syntax"></a>Składnia

```cpp
template<typename Value1,
    typename Value2>
    bool operator!=(pair<Value1, Value2>% left,
        pair<Value1, Value2>% right);
```

#### <a name="parameters"></a>Parametry

*Lewej*<br/>
Lewa para do porównania.

*Prawo*<br/>
Prawa para do porównania.

### <a name="remarks"></a>Uwagi

Funkcja operatora `!(left == right)`zwraca . Służy do testowania, czy *left* nie jest uporządkowany tak samo jak *prawo,* gdy dwie pary są porównywane element po elemencie.

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

## <a name="operatorlt-pair-stlclr"></a><a name="op_lt"></a>operator&lt; (para) (STL/CLR)

Para mniej niż porównanie.

### <a name="syntax"></a>Składnia

```cpp
template<typename Value1,
    typename Value2>
    bool operator<(pair<Value1, Value2>% left,
        pair<Value1, Value2>% right);
```

#### <a name="parameters"></a>Parametry

*Lewej*<br/>
Lewa para do porównania.

*Prawo*<br/>
Prawa para do porównania.

### <a name="remarks"></a>Uwagi

Funkcja operatora `left.first <` `right.first || !(right.first <` `left.first &&` `left.second <` `right.second`zwraca . Służy do testowania, czy *left* jest uporządkowany przed *prawym,* gdy dwie pary są porównywane element po elemencie.

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

## <a name="operatorlt-pair-stlclr"></a><a name="op_lteq"></a>operator&lt;= (para) (STL/CLR)

Sparuj mniej niż lub równe porównanie.

### <a name="syntax"></a>Składnia

```cpp
template<typename Value1,
    typename Value2>
    bool operator<=(pair<Value1, Value2>% left,
        pair<Value1, Value2>% right);
```

#### <a name="parameters"></a>Parametry

*Lewej*<br/>
Lewa para do porównania.

*Prawo*<br/>
Prawa para do porównania.

### <a name="remarks"></a>Uwagi

Funkcja operatora `!(right < left)`zwraca . Służy do testowania, czy *left* nie jest uporządkowany po *prawej,* gdy dwie pary są porównywane element po elemencie.

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

## <a name="operator-pair-stlclr"></a><a name="op_eq"></a>operator== (para) (STL/CLR)

Sparuj równe porównanie.

### <a name="syntax"></a>Składnia

```cpp
template<typename Value1,
    typename Value2>
    bool operator==(pair<Value1, Value2>% left,
        pair<Value1, Value2>% right);
```

#### <a name="parameters"></a>Parametry

*Lewej*<br/>
Lewa para do porównania.

*Prawo*<br/>
Prawa para do porównania.

### <a name="remarks"></a>Uwagi

Funkcja operatora `left.first ==` `right.first &&` `left.second ==` `right.second`zwraca . Służy do testowania, czy *left* jest uporządkowany tak samo jak *prawo,* gdy dwie pary są porównywane element po elemencie.

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

## <a name="operatorgt-pair-stlclr"></a><a name="op_gt"></a>operator&gt; (para) (STL/CLR)

Para większa niż porównanie.

### <a name="syntax"></a>Składnia

```cpp
template<typename Value1,
    typename Value2>
    bool operator>(pair<Value1, Value2>% left,
        pair<Value1, Value2>% right);
```

#### <a name="parameters"></a>Parametry

*Lewej*<br/>
Lewa para do porównania.

*Prawo*<br/>
Prawa para do porównania.

### <a name="remarks"></a>Uwagi

Funkcja operatora `right` `<` `left`zwraca . Służy do testowania, czy *left* jest uporządkowany po *prawej stronie,* gdy dwie pary są porównywane element po elemencie.

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

## <a name="operatorgt-pair-stlclr"></a><a name="op_gteq"></a>operator&gt;= (para) (STL/CLR)

Paruj porównanie większe lub równe.

### <a name="syntax"></a>Składnia

```cpp
template<typename Value1,
    typename Value2>
    bool operator>=(pair<Value1, Value2>% left,
        pair<Value1, Value2>% right);
```

#### <a name="parameters"></a>Parametry

*Lewej*<br/>
Lewa para do porównania.

*Prawo*<br/>
Prawa para do porównania.

### <a name="remarks"></a>Uwagi

Funkcja operatora `!(left < right)`zwraca . Służy do testowania, czy *left* nie jest uporządkowany przed *prawym,* gdy dwie pary są porównywane element po elemencie.

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
