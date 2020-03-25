---
title: functional (STL/CLR)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- <cliext/functional>
- cliext::binary_delegate
- cliext::binary_delegate_noreturn
- cliext::binary_negate
- cliext::bind1st
- cliext::bind2nd
- cliext::binder1st
- cliext::binder2nd
- cliext::divides
- cliext::equal_to
- cliext::greater
- cliext::greater_equal
- cliext::less
- cliext::less_equal
- cliext::logical_and
- cliext::logical_not
- cliext::logical_or
- cliext::minus
- cliext::modulus
- cliext::multiplies
- cliext::negate
- cliext::not_equal_to
- cliext::not1
- cliext::not2
- cliext::plus
- cliext::unary_delegate
- cliext::unary_delegate_noreturn
- cliext::unary_negate
helpviewer_keywords:
- <functional> header [STL/CLR]
- <cliext/functional> header [STL/CLR]
- functional functions [STL/CLR]
- binary_delegate function [STL/CLR]
- binary_delegate_noreturn function [STL/CLR]
- binary_negate function [STL/CLR]
- bind1st function [STL/CLR]
- bind2nd function [STL/CLR]
- binder1st function [STL/CLR]
- binder2nd function [STL/CLR]
- divides function [STL/CLR]
- equal_to function [STL/CLR]
- greater function [STL/CLR]
- greater_equal function [STL/CLR]
- less function [STL/CLR]
- less_equal function [STL/CLR]
- logical_and function [STL/CLR]
- logical_not function [STL/CLR]
- logical_or function [STL/CLR]
- minus function [STL/CLR]
- modulus function [STL/CLR]
- multiplies function [STL/CLR]
- negate function [STL/CLR]
- not_equal_to function [STL/CLR]
- not1 function [STL/CLR]
- not2 function [STL/CLR]
- plus function [STL/CLR]
- unary_delegate function [STL/CLR]
- unary_delegate_noreturn function [STL/CLR]
- unary_negate function [STL/CLR]
ms.assetid: 88738b8c-5d37-4375-970e-a4442bf5efde
ms.openlocfilehash: 2d06a92fea9a702633216e3244879687b66f97d6
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80208731"
---
# <a name="functional-stlclr"></a>functional (STL/CLR)

Dołącz nagłówek STL/CLR `<cliext/functional>`, aby zdefiniować liczbę klas szablonu i powiązane z nią delegatów szablonu i funkcje.

## <a name="syntax"></a>Składnia

```
#include <functional>
```

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<cliext/> funkcjonalne

**Przestrzeń nazw:** cliext

## <a name="declarations"></a>Deklaracje

|Delegate|Opis|
|--------------|-----------------|
|[binary_delegate (STL/CLR)](#binary_delegate)|Delegat dwóch argumentów.|
|[binary_delegate_noreturn (STL/CLR)](#binary_delegate_noreturn)|Delegat dwóch argumentów zwraca **typ void**.|
|[unary_delegate (STL/CLR)](#unary_delegate)|Delegat z jednym argumentem.|
|[unary_delegate_noreturn (STL/CLR)](#unary_delegate_noreturn)|Delegat z jednym argumentem zwraca **typ void**.|

|Klasa|Opis|
|-----------|-----------------|
|[binary_negate (STL/CLR)](#binary_negate)|Funktor Negate dwa argumentu Funktor.|
|[binder1st (STL/CLR)](#binder1st)|Funktor, aby powiązać pierwszy argument z dwoma argumentami Funktor.|
|[binder2nd (STL/CLR)](#binder2nd)|Funktor do powiązania drugiego argumentu z dwoma argumentami Funktor.|
|[divides (STL/CLR)](#divides)|Podziel Funktor.|
|[equal_to (STL/CLR)](#equal_to)|Równe porównanie Funktor.|
|[greater (STL/CLR)](#greater)|Większe porównanie Funktor.|
|[greater_equal (STL/CLR)](#greater_equal)|Większe lub równe porównanie Funktor.|
|[less (STL/CLR)](#less)|Mniej porównania Funktor.|
|[less_equal (STL/CLR)](#less_equal)|Mniejsze lub równe porównanie Funktor.|
|[logical_and (STL/CLR)](#logical_and)|Koniunkcja logiczna i Funktor.|
|[logical_not (STL/CLR)](#logical_not)|Logiczna nie Funktor.|
|[logical_or (STL/CLR)](#logical_or)|Logiczne lub Funktor.|
|[minus (STL/CLR)](#minus)|Odejmij Funktor.|
|[modulus (STL/CLR)](#modulus)|Moduł Funktor.|
|[multiplies (STL/CLR)](#multiplies)|Pomnóż Funktor.|
|[negate (STL/CLR)](#negate)|Funktor, aby zwrócić argument z negacją.|
|[not_equal_to (STL/CLR)](#not_equal_to)|Nie równa się Funktor porównania.|
|[plus (STL/CLR)](#plus)|Dodaj Funktor.|
|[unary_negate (STL/CLR)](#unary_negate)|Funktor Negate z jednym argumentem Funktor.|

|Funkcja|Opis|
|--------------|-----------------|
|[bind1st (STL/CLR)](#bind1st)|Generuje binder1st — dla argumentu i Funktor.|
|[bind2nd (STL/CLR)](#bind2nd)|Generuje binder2nd — dla argumentu i Funktor.|
|[not1 (STL/CLR)](#not1)|Generuje unary_negate dla elementu Funktor.|
|[not2 (STL/CLR)](#not2)|Generuje binary_negate dla elementu Funktor.|

## <a name="members"></a>Members

## <a name="binary_delegate-stlclr"></a><a name="binary_delegate"></a>binary_delegate (STL/CLR)

Klasa genereic opisuje delegata dwóch argumentów. Służy do tego określenie delegata w odniesieniu do jego argumentu i typów zwracanych.

### <a name="syntax"></a>Składnia

```cpp
generic<typename Arg1,
    typename Arg2,
    typename Result>
    delegate Result binary_delegate(Arg1, Arg2);
```

#### <a name="parameters"></a>Parametry

*Arg1*<br/>
Typ pierwszego argumentu.

*Arg2*<br/>
Typ drugiego argumentu.

*Wynika*<br/>
Typ zwracany.

### <a name="remarks"></a>Uwagi

Delegat genereic opisuje funkcję dwuargumentową.

Należy pamiętać, że w przypadku:

`binary_delegate<int, int, int> Fun1;`

`binary_delegate<int, int, int> Fun2;`

typy `Fun1` i `Fun2` są synonimami, a w przypadku:

`delegate int Fun1(int, int);`

`delegate int Fun2(int, int);`

nie są tego samego typu.

### <a name="example"></a>Przykład

```cpp
// cliext_binary_delegate.cpp
// compile with: /clr
#include <cliext/functional>

bool key_compare(wchar_t left, wchar_t right)
    {
    return (left < right);
    }

typedef cliext::binary_delegate<wchar_t, wchar_t, bool> Mydelegate;
int main()
    {
    Mydelegate^ kcomp = gcnew Mydelegate(&key_compare);

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

## <a name="binary_delegate_noreturn-stlclr"></a><a name="binary_delegate_noreturn"></a>binary_delegate_noreturn (STL/CLR)

Klasa genereic opisuje delegata dwóch argumentów, która zwraca wartość **void**. Używasz tego elementu jako delegata w odniesieniu do jego argumentu.

### <a name="syntax"></a>Składnia

```cpp
generic<typename Arg1,
    typename Arg2>
    delegate void binary_delegate(Arg1, Arg2);
```

#### <a name="parameters"></a>Parametry

*Arg1*<br/>
Typ pierwszego argumentu.

*Arg2*<br/>
Typ drugiego argumentu.

### <a name="remarks"></a>Uwagi

Delegat genereic opisuje funkcję dwuargumentową zwracającą **typ void**.

Należy pamiętać, że w przypadku:

`binary_delegate_noreturn<int, int> Fun1;`

`binary_delegate_noreturn<int, int> Fun2;`

typy `Fun1` i `Fun2` są synonimami, a w przypadku:

`delegate void Fun1(int, int);`

`delegate void Fun2(int, int);`

nie są tego samego typu.

### <a name="example"></a>Przykład

```cpp
// cliext_binary_delegate_noreturn.cpp
// compile with: /clr
#include <cliext/functional>

void key_compare(wchar_t left, wchar_t right)
    {
    System::Console::WriteLine("compare({0}, {1}) = {2}",
        left, right, left < right);
    }

typedef cliext::binary_delegate_noreturn<wchar_t, wchar_t> Mydelegate;
int main()
    {
    Mydelegate^ kcomp = gcnew Mydelegate(&key_compare);

    kcomp(L'a', L'a');
    kcomp(L'a', L'b');
    kcomp(L'b', L'a');
    System::Console::WriteLine();
    return (0);
    }
```

```Output
compare(a, a) = False
compare(a, b) = True
compare(b, a) = False
```

## <a name="binary_negate-stlclr"></a><a name="binary_negate"></a>binary_negate (STL/CLR)

Klasa szablonu opisuje Funktor, który, gdy wywoływana, zwraca wartość logiczną, a nie przechowywane dwa argumenty Funktor. Służy do określania obiektu funkcji w postaci Funktor przechowywanych elementów.

### <a name="syntax"></a>Składnia

```cpp
template<typename Fun>
    ref class binary_negate
    { // wrap operator()
public:
    typedef Fun stored_function_type;
    typedef typename Fun::first_argument_type first_argument_type;
    typedef typename Fun::second_argument_type second_argument_type;
    typedef bool result_type;
    typedef Microsoft::VisualC::StlClr::BinaryDelegate<
        first_argument_type, second_argument_type, result_type>
        delegate_type;

    explicit binary_negate(Fun% functor);
    binary_negate(binary_negate<Arg>% right);

    result_type operator()(first_argument_type left,
        second_argument_type right);
    operator delegate_type^();
    };
```

#### <a name="parameters"></a>Parametry

*Zabawny*<br/>
Typ przechowywanego Funktor.

## <a name="member-functions"></a>Funkcje elementów członkowskich

|Definicja typu|Opis|
|---------------------|-----------------|
|delegate_type|Typ delegata ogólnego.|
|first_argument_type|Typ pierwszego argumentu Funktor.|
|result_type|Typ wyniku Funktor.|
|second_argument_type|Typ drugiego argumentu Funktor.|
|stored_function_type|Typ Funktor.|

|Członek|Opis|
|------------|-----------------|
|binary_negate|Konstruuje Funktor.|

|Operator|Opis|
|--------------|-----------------|
|operator ()|Oblicza odpowiednią funkcję.|
|delegate_type operatora ^ ()|Rzutuje Funktor na delegata.|

### <a name="remarks"></a>Uwagi

Klasa szablonu opisuje dwa argumenty Funktor, które przechowują kolejne dwa argumenty Funktor. Definiuje operator elementu członkowskiego `operator()` tak, aby, gdy obiekt jest wywoływany jako funkcja, zwraca wartość logiczną, a nie przechowywane Funktor wywołana z dwoma argumentami.

Można również przekazać obiekt jako argument funkcji, którego typ jest `delegate_type^` i zostanie odpowiednio przekonwertowane.

### <a name="example"></a>Przykład

```cpp
// cliext_binary_negate.cpp
// compile with: /clr
#include <cliext/algorithm>
#include <cliext/functional>
#include <cliext/vector>

typedef cliext::vector<int> Myvector;
int main()
    {
    Myvector c1;
    c1.push_back(4);
    c1.push_back(3);
    Myvector c2;
    c2.push_back(4);
    c2.push_back(4);
    Myvector c3(2, 0);

// display initial contents " 4 3" and " 4 4"
    for each (int elem in c1)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

    for each (int elem in c2)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display
    cliext::less<int> less_op;

    cliext::transform(c1.begin(), c1.begin() + 2,
        c2.begin(), c3.begin(),
        cliext::binary_negate<cliext::less<int> >(less_op));
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display with function
    cliext::transform(c1.begin(), c1.begin() + 2,
        c2.begin(), c3.begin(), cliext::not2(less_op));
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
4 3
4 4
1 0
1 0
```

## <a name="bind1st-stlclr"></a><a name="bind1st"></a>bind1st — (STL/CLR)

Generuje `binder1st` dla argumentu i Funktor.

### <a name="syntax"></a>Składnia

```cpp
template<typename Fun,
    typename Arg>
    binder1st<Fun> bind1st(Fun% functor,
        Arg left);
```

#### <a name="template-parameters"></a>Parametry szablonu

*ARG*<br/>
Typ argumentu.

*Zabawny*<br/>
Typ Funktor.

#### <a name="function-parameters"></a>Parametry funkcji

*Funktor*<br/>
Funktor do zawijania.

*lewym*<br/>
Pierwszy argument, który ma być zawijany.

### <a name="remarks"></a>Uwagi

Funkcja Template zwraca [binder1st — (STL/CLR)](../dotnet/binder1st-stl-clr.md)`<Fun>(functor, left)`. Jest on używany jako wygodny sposób zawijania Funktor dwuargumentowego i jego pierwszego argumentu w Funktor jednoargumentowym, który wywołuje ją z drugim argumentem.

### <a name="example"></a>Przykład

```cpp
// cliext_bind1st.cpp
// compile with: /clr
#include <cliext/algorithm>
#include <cliext/functional>
#include <cliext/vector>

typedef cliext::vector<int> Myvector;
int main()
    {
    Myvector c1;
    c1.push_back(4);
    c1.push_back(3);
    Myvector c3(2, 0);

// display initial contents " 4 3"
    for each (int elem in c1)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display
    cliext::minus<int> sub_op;
    cliext::binder1st<cliext::minus<int> > subfrom3(sub_op, 3);

    cliext::transform(c1.begin(), c1.begin() + 2, c3.begin(),
        subfrom3);
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display with function
    cliext::transform(c1.begin(), c1.begin() + 2, c3.begin(),
        bind1st(sub_op, 3));
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
4 3
-1 0
-1 0
```

## <a name="bind2nd-stlclr"></a><a name="bind2nd"></a>bind2nd — (STL/CLR)

Generuje `binder2nd` dla argumentu i Funktor.

### <a name="syntax"></a>Składnia

```cpp
template<typename Fun,
    typename Arg>
    binder2nd<Fun> bind2nd(Fun% functor,
        Arg right);
```

#### <a name="template-parameters"></a>Parametry szablonu

*ARG*<br/>
Typ argumentu.

*Zabawny*<br/>
Typ Funktor.

#### <a name="function-parameters"></a>Parametry funkcji

*Funktor*<br/>
Funktor do zawijania.

*Kliknij*<br/>
Drugi argument, który ma być zawijany.

### <a name="remarks"></a>Uwagi

Funkcja Template zwraca [binder2nd — (STL/CLR)](../dotnet/binder2nd-stl-clr.md)`<Fun>(functor, right)`. Jest on używany jako wygodny sposób zawijania Funktor dwuargumentowego i jego drugiego argumentu w Funktor jednym argumencie, który wywołuje go przy użyciu pierwszego argumentu.

### <a name="example"></a>Przykład

```cpp
// cliext_bind2nd.cpp
// compile with: /clr
#include <cliext/algorithm>
#include <cliext/functional>
#include <cliext/vector>

typedef cliext::vector<int> Myvector;
int main()
    {
    Myvector c1;
    c1.push_back(4);
    c1.push_back(3);
    Myvector c3(2, 0);

// display initial contents " 4 3"
    for each (int elem in c1)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display
    cliext::minus<int> sub_op;
    cliext::binder2nd<cliext::minus<int> > sub4(sub_op, 4);

    cliext::transform(c1.begin(), c1.begin() + 2, c3.begin(),
        sub4);
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display with function
    cliext::transform(c1.begin(), c1.begin() + 2, c3.begin(),
        bind2nd(sub_op, 4));
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
4 3
0 -1
0 -1
```

## <a name="binder1st-stlclr"></a><a name="binder1st"></a>binder1st — (STL/CLR)

Klasa szablonu opisuje jednoargumentowe Funktor, które, po wywołaniu, zwraca przechowywane dwa argumenty Funktor, które są wywoływane z przechowywanym pierwszym argumentem i podanym drugim argumentem. Służy do określania obiektu funkcji w postaci Funktor przechowywanych elementów.

### <a name="syntax"></a>Składnia

```cpp
template<typename Fun>
    ref class binder1st
    { // wrap operator()
public:
    typedef Fun stored_function_type;
    typedef typename Fun::first_argument_type first_argument_type;
    typedef typename Fun::second_argument_type second_argument_type;
    typedef typename Fun:result_type result_type;
    typedef Microsoft::VisualC::StlClr::UnaryDelegate<
        second_argument_type, result_type>
        delegate_type;

    binder1st(Fun% functor, first_argument_type left);
    binder1st(binder1st<Arg>% right);

    result_type operator()(second_argument_type right);
    operator delegate_type^();
    };
```

#### <a name="parameters"></a>Parametry

*Zabawny*<br/>
Typ przechowywanego Funktor.

### <a name="member-functions"></a>Funkcje elementów członkowskich

|Definicja typu|Opis|
|---------------------|-----------------|
|delegate_type|Typ delegata ogólnego.|
|first_argument_type|Typ pierwszego argumentu Funktor.|
|result_type|Typ wyniku Funktor.|
|second_argument_type|Typ drugiego argumentu Funktor.|
|stored_function_type|Typ Funktor.|

|Członek|Opis|
|------------|-----------------|
|binder1st|Konstruuje Funktor.|

|Operator|Opis|
|--------------|-----------------|
|operator ()|Oblicza odpowiednią funkcję.|
|delegate_type operatora ^ ()|Rzutuje Funktor na delegata.|

### <a name="remarks"></a>Uwagi

Klasa szablonu opisuje Funktor z jednym argumentem, który przechowuje dwa argumenty Funktor i pierwszy argument. Definiuje operator elementu członkowskiego `operator()` tak, aby, gdy obiekt jest wywoływany jako funkcja, zwraca wynik wywołania przechowywanej Funktor z przechowywanym pierwszym argumentem i podanym drugim argumentem.

Można również przekazać obiekt jako argument funkcji, którego typ jest `delegate_type^` i zostanie odpowiednio przekonwertowane.

### <a name="example"></a>Przykład

```cpp
// cliext_binder1st.cpp
// compile with: /clr
#include <cliext/algorithm>
#include <cliext/functional>
#include <cliext/vector>

typedef cliext::vector<int> Myvector;
int main()
    {
    Myvector c1;
    c1.push_back(4);
    c1.push_back(3);
    Myvector c3(2, 0);

// display initial contents " 4 3"
    for each (int elem in c1)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display
    cliext::minus<int> sub_op;
    cliext::binder1st<cliext::minus<int> > subfrom3(sub_op, 3);

    cliext::transform(c1.begin(), c1.begin() + 2, c3.begin(),
        subfrom3);
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display with function
    cliext::transform(c1.begin(), c1.begin() + 2, c3.begin(),
        bind1st(sub_op, 3));
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
4 3
-1 0
-1 0
```

## <a name="binder2nd-stlclr"></a><a name="binder2nd"></a>binder2nd — (STL/CLR)

Klasa szablonu opisuje jednoargumentowe Funktor, które, po wywołaniu, zwraca przechowywane dwa argumenty Funktor, które są wywoływane przy użyciu podanego pierwszego argumentu i przechowywanego drugiego argumentu. Służy do określania obiektu funkcji w postaci Funktor przechowywanych elementów.

### <a name="syntax"></a>Składnia

```cpp
template<typename Fun>
    ref class binder2nd
    { // wrap operator()
public:
    typedef Fun stored_function_type;
    typedef typename Fun::first_argument_type first_argument_type;
    typedef typename Fun::second_argument_type second_argument_type;
    typedef typename Fun:result_type result_type;
    typedef Microsoft::VisualC::StlClr::UnaryDelegate<
        first_argument_type, result_type>
        delegate_type;

    binder2nd(Fun% functor, second_argument_type left);
    binder2nd(binder2nd<Arg>% right);

    result_type operator()(first_argument_type right);
    operator delegate_type^();
    };
```

#### <a name="parameters"></a>Parametry

*Zabawny*<br/>
Typ przechowywanego Funktor.

## <a name="member-functions"></a>Funkcje elementów członkowskich

|Definicja typu|Opis|
|---------------------|-----------------|
|delegate_type|Typ delegata ogólnego.|
|first_argument_type|Typ pierwszego argumentu Funktor.|
|result_type|Typ wyniku Funktor.|
|second_argument_type|Typ drugiego argumentu Funktor.|
|stored_function_type|Typ Funktor.|

|Członek|Opis|
|------------|-----------------|
|binder2nd|Konstruuje Funktor.|

|Operator|Opis|
|--------------|-----------------|
|operator ()|Oblicza odpowiednią funkcję.|
|delegate_type operatora ^ ()|Rzutuje Funktor na delegata.|

### <a name="remarks"></a>Uwagi

Klasa szablonu opisuje Funktor z jednym argumentem, który przechowuje dwa argumenty Funktor i drugi argument. Definiuje operator elementu członkowskiego `operator()` tak, aby, gdy obiekt jest wywoływany jako funkcja, zwraca wynik wywołania przechowywanego Funktor z podanym pierwszym argumentem i przechowywaną drugim argumentem.

Można również przekazać obiekt jako argument funkcji, którego typ jest `delegate_type^` i zostanie odpowiednio przekonwertowane.

### <a name="example"></a>Przykład

```cpp
// cliext_binder2nd.cpp
// compile with: /clr
#include <cliext/algorithm>
#include <cliext/functional>
#include <cliext/vector>

typedef cliext::vector<int> Myvector;
int main()
    {
    Myvector c1;
    c1.push_back(4);
    c1.push_back(3);
    Myvector c3(2, 0);

// display initial contents " 4 3"
    for each (int elem in c1)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display
    cliext::minus<int> sub_op;
    cliext::binder2nd<cliext::minus<int> > sub4(sub_op, 4);

    cliext::transform(c1.begin(), c1.begin() + 2, c3.begin(),
        sub4);
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display with function
    cliext::transform(c1.begin(), c1.begin() + 2, c3.begin(),
        bind2nd(sub_op, 4));
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
4 3
0 -1
0 -1
```

## <a name="divides-stlclr"></a><a name="divides"></a>podziały (STL/CLR)

Klasa szablonu opisuje element Funktor, który po wywołaniu zwraca pierwszy argument podzielony przez drugi. Służy do określania obiektu funkcji w postaci typu argumentu.

### <a name="syntax"></a>Składnia

```cpp
template<typename Arg>
    ref class divides
    { // wrap operator()
public:
    typedef Arg first_argument_type;
    typedef Arg second_argument_type;
    typedef Arg result_type;
    typedef Microsoft::VisualC::StlClr::BinaryDelegate<
        first_argument_type, second_argument_type, result_type>
        delegate_type;

    divides();
    divides(divides<Arg>% right);

    result_type operator()(first_argument_type left,
        second_argument_type right);
    operator delegate_type^();
    };
```

#### <a name="parameters"></a>Parametry

*ARG*<br/>
Typ argumentów i wartość zwracana.

### <a name="member-functions"></a>Funkcje elementów członkowskich

|Definicja typu|Opis|
|---------------------|-----------------|
|delegate_type|Typ delegata ogólnego.|
|first_argument_type|Typ pierwszego argumentu Funktor.|
|result_type|Typ wyniku Funktor.|
|second_argument_type|Typ drugiego argumentu Funktor.|

|Członek|Opis|
|------------|-----------------|
|divides|Konstruuje Funktor.|

|Operator|Opis|
|--------------|-----------------|
|operator ()|Oblicza odpowiednią funkcję.|
|delegate_type operatora ^ ()|Rzutuje Funktor na delegata.|

### <a name="remarks"></a>Uwagi

Klasa szablonu opisuje dwa argumenty Funktor. Definiuje operator elementu członkowskiego `operator()` tak, aby, gdy obiekt jest wywoływany jako funkcja, zwraca pierwszy argument podzielony przez drugi.

Można również przekazać obiekt jako argument funkcji, którego typ jest `delegate_type^` i zostanie odpowiednio przekonwertowane.

### <a name="example"></a>Przykład

```cpp
// cliext_divides.cpp
// compile with: /clr
#include <cliext/algorithm>
#include <cliext/functional>
#include <cliext/vector>

typedef cliext::vector<int> Myvector;
int main()
    {
    Myvector c1;
    c1.push_back(4);
    c1.push_back(3);
    Myvector c2;
    c2.push_back(2);
    c2.push_back(1);
    Myvector c3(2, 0);

// display initial contents " 4 3" and " 2 1"
    for each (int elem in c1)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

    for each (int elem in c2)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display
    cliext::transform(c1.begin(), c1.begin() + 2,
        c2.begin(), c3.begin(), cliext::divides<int>());
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
4 3
2 1
2 3
```

## <a name="equal_to-stlclr"></a><a name="equal_to"></a>equal_to (STL/CLR)

Klasa szablonu opisuje Funktor, który po wywołaniu zwraca wartość true tylko wtedy, gdy pierwszy argument jest równy drugiemu. Służy do określania obiektu funkcji w postaci typu argumentu.

### <a name="syntax"></a>Składnia

```cpp
template<typename Arg>
    ref class equal_to
    { // wrap operator()
public:
    typedef Arg first_argument_type;
    typedef Arg second_argument_type;
    typedef bool result_type;
    typedef Microsoft::VisualC::StlClr::BinaryDelegate<
        first_argument_type, second_argument_type, result_type>
        delegate_type;

    equal_to();
    equal_to(equal_to<Arg>% right);

    result_type operator()(first_argument_type left,
        second_argument_type right);
    operator delegate_type^();
    };
```

#### <a name="parameters"></a>Parametry

*ARG*<br/>
Typ argumentów.

### <a name="member-functions"></a>Funkcje elementów członkowskich

|Definicja typu|Opis|
|---------------------|-----------------|
|delegate_type|Typ delegata ogólnego.|
|first_argument_type|Typ pierwszego argumentu Funktor.|
|result_type|Typ wyniku Funktor.|
|second_argument_type|Typ drugiego argumentu Funktor.|

|Członek|Opis|
|------------|-----------------|
|equal_to|Konstruuje Funktor.|

|Operator|Opis|
|--------------|-----------------|
|operator ()|Oblicza odpowiednią funkcję.|
|delegate_type operatora ^ ()|Rzutuje Funktor na delegata.|

### <a name="remarks"></a>Uwagi

Klasa szablonu opisuje dwa argumenty Funktor. Definiuje operator elementu członkowskiego `operator()` tak, aby, gdy obiekt jest wywoływany jako funkcja, zwraca wartość true tylko wtedy, gdy pierwszy argument jest równy drugiemu.

Można również przekazać obiekt jako argument funkcji, którego typ jest `delegate_type^` i zostanie odpowiednio przekonwertowane.

### <a name="example"></a>Przykład

```cpp
// cliext_equal_to.cpp
// compile with: /clr
#include <cliext/algorithm>
#include <cliext/functional>
#include <cliext/vector>

typedef cliext::vector<int> Myvector;
int main()
    {
    Myvector c1;
    c1.push_back(4);
    c1.push_back(3);
    Myvector c2;
    c2.push_back(4);
    c2.push_back(4);
    Myvector c3(2, 0);

// display initial contents " 4 3" and " 4 4"
    for each (int elem in c1)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

    for each (int elem in c2)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display
    cliext::transform(c1.begin(), c1.begin() + 2,
        c2.begin(), c3.begin(), cliext::equal_to<int>());
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
4 3
4 4
1 0
```

## <a name="greater-stlclr"></a><a name="greater"></a>większe (STL/CLR)

Klasa szablonu opisuje Funktor, który po wywołaniu zwraca wartość true tylko wtedy, gdy pierwszy argument jest większy od drugiego. Służy do określania obiektu funkcji w postaci typu argumentu.

### <a name="syntax"></a>Składnia

```cpp
template<typename Arg>
    ref class greater
    { // wrap operator()
public:
    typedef Arg first_argument_type;
    typedef Arg second_argument_type;
    typedef bool result_type;
    typedef Microsoft::VisualC::StlClr::BinaryDelegate<
        first_argument_type, second_argument_type, result_type>
        delegate_type;

    greater();
    greater(greater<Arg>% right);

    result_type operator()(first_argument_type left,
        second_argument_type right);
    operator delegate_type^();
    };
```

#### <a name="parameters"></a>Parametry

*ARG*<br/>
Typ argumentów.

### <a name="member-functions"></a>Funkcje elementów członkowskich

|Definicja typu|Opis|
|---------------------|-----------------|
|delegate_type|Typ delegata ogólnego.|
|first_argument_type|Typ pierwszego argumentu Funktor.|
|result_type|Typ wyniku Funktor.|
|second_argument_type|Typ drugiego argumentu Funktor.|

|Członek|Opis|
|------------|-----------------|
|greater|Konstruuje Funktor.|

|Operator|Opis|
|--------------|-----------------|
|operator ()|Oblicza odpowiednią funkcję.|
|delegate_type operatora ^|Rzutuje Funktor na delegata.|

### <a name="remarks"></a>Uwagi

Klasa szablonu opisuje dwa argumenty Funktor. Definiuje operator elementu członkowskiego `operator()` tak, aby, gdy obiekt jest wywoływany jako funkcja, zwraca wartość true tylko wtedy, gdy pierwszy argument jest większy od drugiego.

Można również przekazać obiekt jako argument funkcji, którego typ jest `delegate_type^` i zostanie odpowiednio przekonwertowane.

### <a name="example"></a>Przykład

```cpp
// cliext_greater.cpp
// compile with: /clr
#include <cliext/algorithm>
#include <cliext/functional>
#include <cliext/vector>

typedef cliext::vector<int> Myvector;
int main()
    {
    Myvector c1;
    c1.push_back(4);
    c1.push_back(3);
    Myvector c2;
    c2.push_back(3);
    c2.push_back(3);
    Myvector c3(2, 0);

// display initial contents " 4 3" and " 3 3"
    for each (int elem in c1)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

    for each (int elem in c2)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display
    cliext::transform(c1.begin(), c1.begin() + 2,
        c2.begin(), c3.begin(), cliext::greater<int>());
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
4 3
3 3
1 0
```

## <a name="greater_equal-stlclr"></a><a name="greater_equal"></a>greater_equal (STL/CLR)

Klasa szablonu opisuje Funktor, który po wywołaniu zwraca wartość true tylko wtedy, gdy pierwszy argument jest większy lub równy drugiemu. Służy do określania obiektu funkcji w postaci typu argumentu.

### <a name="syntax"></a>Składnia

```cpp
template<typename Arg>
    ref class greater_equal
    { // wrap operator()
public:
    typedef Arg first_argument_type;
    typedef Arg second_argument_type;
    typedef bool result_type;
    typedef Microsoft::VisualC::StlClr::BinaryDelegate<
        first_argument_type, second_argument_type, result_type>
        delegate_type;

    greater_equal();
    greater_equal(greater_equal<Arg>% right);

    result_type operator()(first_argument_type left,
        second_argument_type right);
    operator delegate_type^();
    };
```

#### <a name="parameters"></a>Parametry

*ARG*<br/>
Typ argumentów.

### <a name="member-functions"></a>Funkcje elementów członkowskich

|Definicja typu|Opis|
|---------------------|-----------------|
|delegate_type|Typ delegata ogólnego.|
|first_argument_type|Typ pierwszego argumentu Funktor.|
|result_type|Typ wyniku Funktor.|
|second_argument_type|Typ drugiego argumentu Funktor.|

|Członek|Opis|
|------------|-----------------|
|greater_equal|Konstruuje Funktor.|

|Operator|Opis|
|--------------|-----------------|
|operator ()|Oblicza odpowiednią funkcję.|
|delegate_type operatora ^|Rzutuje Funktor na delegata.|

### <a name="remarks"></a>Uwagi

Klasa szablonu opisuje dwa argumenty Funktor. Definiuje operator elementu członkowskiego `operator()` tak, aby, gdy obiekt jest wywoływany jako funkcja, zwraca wartość true tylko wtedy, gdy pierwszy argument jest większy lub równy drugiemu.

Można również przekazać obiekt jako argument funkcji, którego typ jest `delegate_type^` i zostanie odpowiednio przekonwertowane.

### <a name="example"></a>Przykład

```cpp
// cliext_greater_equal.cpp
// compile with: /clr
#include <cliext/algorithm>
#include <cliext/functional>
#include <cliext/vector>

typedef cliext::vector<int> Myvector;
int main()
    {
    Myvector c1;
    c1.push_back(4);
    c1.push_back(3);
    Myvector c2;
    c2.push_back(4);
    c2.push_back(4);
    Myvector c3(2, 0);

// display initial contents " 4 3" and " 4 4"
    for each (int elem in c1)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

    for each (int elem in c2)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display
    cliext::transform(c1.begin(), c1.begin() + 2,
        c2.begin(), c3.begin(), cliext::greater_equal<int>());
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
4 3
4 4
1 0
```

## <a name="less-stlclr"></a><a name="less"></a>less (STL/CLR)

Klasa szablonu opisuje Funktor, który po wywołaniu zwraca wartość true tylko wtedy, gdy pierwszy argument jest mniejszy od drugiego. Służy do określania obiektu funkcji w postaci typu argumentu.

### <a name="syntax"></a>Składnia

```cpp
template<typename Arg>
    ref class less
    { // wrap operator()
public:
    typedef Arg first_argument_type;
    typedef Arg second_argument_type;
    typedef bool result_type;
    typedef Microsoft::VisualC::StlClr::BinaryDelegate<
        first_argument_type, second_argument_type, result_type>
        delegate_type;

    less();
    less(less<Arg>% right);

    result_type operator()(first_argument_type left,
        second_argument_type right);
    operator delegate_type^();
    };
```

#### <a name="parameters"></a>Parametry

*ARG*<br/>
Typ argumentów.

### <a name="member-functions"></a>Funkcje elementów członkowskich

|Definicja typu|Opis|
|---------------------|-----------------|
|delegate_type|Typ delegata ogólnego.|
|first_argument_type|Typ pierwszego argumentu Funktor.|
|result_type|Typ wyniku Funktor.|
|second_argument_type|Typ drugiego argumentu Funktor.|

|Członek|Opis|
|------------|-----------------|
|less|Konstruuje Funktor.|

|Operator|Opis|
|--------------|-----------------|
|operator ()|Oblicza odpowiednią funkcję.|
|delegate_type operatora ^|Rzutuje Funktor na delegata.|

### <a name="remarks"></a>Uwagi

Klasa szablonu opisuje dwa argumenty Funktor. Definiuje operator elementu członkowskiego `operator()` tak, aby, gdy obiekt jest wywoływany jako funkcja, zwraca wartość true tylko wtedy, gdy pierwszy argument jest mniejszy od drugiego.

Można również przekazać obiekt jako argument funkcji, którego typ jest `delegate_type^` i zostanie odpowiednio przekonwertowane.

### <a name="example"></a>Przykład

```cpp
// cliext_less.cpp
// compile with: /clr
#include <cliext/algorithm>
#include <cliext/functional>
#include <cliext/vector>

typedef cliext::vector<int> Myvector;
int main()
    {
    Myvector c1;
    c1.push_back(4);
    c1.push_back(3);
    Myvector c2;
    c2.push_back(4);
    c2.push_back(4);
    Myvector c3(2, 0);

// display initial contents " 4 3" and " 4 4"
    for each (int elem in c1)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

    for each (int elem in c2)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display
    cliext::transform(c1.begin(), c1.begin() + 2,
        c2.begin(), c3.begin(), cliext::less<int>());
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
4 3
4 4
0 1
```

## <a name="less_equal-stlclr"></a><a name="less_equal"></a>less_equal (STL/CLR)

Klasa szablonu opisuje Funktor, który po wywołaniu zwraca wartość true tylko wtedy, gdy pierwszy argument jest mniejszy lub równy drugiemu. Służy do określania obiektu funkcji w postaci typu argumentu.

### <a name="syntax"></a>Składnia

```cpp
template<typename Arg>
    ref class less_equal
    { // wrap operator()
public:
    typedef Arg first_argument_type;
    typedef Arg second_argument_type;
    typedef bool result_type;
    typedef Microsoft::VisualC::StlClr::BinaryDelegate<
        first_argument_type, second_argument_type, result_type>
        delegate_type;

    less_equal();
    less_equal(less_equal<Arg>% right);

    result_type operator()(first_argument_type left,
        second_argument_type right);
    operator delegate_type^();
    };
```

#### <a name="parameters"></a>Parametry

*ARG*<br/>
Typ argumentów.

### <a name="member-functions"></a>Funkcje elementów członkowskich

|Definicja typu|Opis|
|---------------------|-----------------|
|delegate_type|Typ delegata ogólnego.|
|first_argument_type|Typ pierwszego argumentu Funktor.|
|result_type|Typ wyniku Funktor.|
|second_argument_type|Typ drugiego argumentu Funktor.|

|Członek|Opis|
|------------|-----------------|
|less_equal|Konstruuje Funktor.|

|Operator|Opis|
|--------------|-----------------|
|operator ()|Oblicza odpowiednią funkcję.|
|delegate_type operatora ^|Rzutuje Funktor na delegata.|

### <a name="remarks"></a>Uwagi

Klasa szablonu opisuje dwa argumenty Funktor. Definiuje operator elementu członkowskiego `operator()` tak, aby, gdy obiekt jest wywoływany jako funkcja, zwraca wartość true tylko wtedy, gdy pierwszy argument jest mniejszy lub równy drugiemu.

Można również przekazać obiekt jako argument funkcji, którego typ jest `delegate_type^` i zostanie odpowiednio przekonwertowane.

### <a name="example"></a>Przykład

```cpp
// cliext_less_equal.cpp
// compile with: /clr
#include <cliext/algorithm>
#include <cliext/functional>
#include <cliext/vector>

typedef cliext::vector<int> Myvector;
int main()
    {
    Myvector c1;
    c1.push_back(4);
    c1.push_back(3);
    Myvector c2;
    c2.push_back(3);
    c2.push_back(3);
    Myvector c3(2, 0);

// display initial contents " 4 3" and " 3 3"
    for each (int elem in c1)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

    for each (int elem in c2)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display
    cliext::transform(c1.begin(), c1.begin() + 2,
        c2.begin(), c3.begin(), cliext::less_equal<int>());
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
4 3
3 3
0 1
```

## <a name="logical_and-stlclr"></a><a name="logical_and"></a>logical_and (STL/CLR)

Klasa szablonu opisuje Funktor, który po wywołaniu zwraca wartość true tylko wtedy, gdy oba argumenty i drugi test mają wartość true. Służy do określania obiektu funkcji w postaci typu argumentu.

### <a name="syntax"></a>Składnia

```cpp
template<typename Arg>
    ref class logical_and
    { // wrap operator()
public:
    typedef Arg first_argument_type;
    typedef Arg second_argument_type;
    typedef bool result_type;
    typedef Microsoft::VisualC::StlClr::BinaryDelegate<
        first_argument_type, second_argument_type, result_type>
        delegate_type;

    logical_and();
    logical_and(logical_and<Arg>% right);

    result_type operator()(first_argument_type left,
        second_argument_type right);
    operator delegate_type^();
    };
```

#### <a name="parameters"></a>Parametry

*ARG*<br/>
Typ argumentów.

### <a name="member-functions"></a>Funkcje elementów członkowskich

|Definicja typu|Opis|
|---------------------|-----------------|
|delegate_type|Typ delegata ogólnego.|
|first_argument_type|Typ pierwszego argumentu Funktor.|
|result_type|Typ wyniku Funktor.|
|second_argument_type|Typ drugiego argumentu Funktor.|

|Członek|Opis|
|------------|-----------------|
|logical_and|Konstruuje Funktor.|

|Operator|Opis|
|--------------|-----------------|
|operator ()|Oblicza odpowiednią funkcję.|
|delegate_type operatora ^|Rzutuje Funktor na delegata.|

### <a name="remarks"></a>Uwagi

Klasa szablonu opisuje dwa argumenty Funktor. Definiuje operator elementu członkowskiego `operator()` tak, aby, gdy obiekt jest wywoływany jako funkcja, zwraca wartość true tylko wtedy, gdy oba argumenty i drugi test mają wartość true.

Można również przekazać obiekt jako argument funkcji, którego typ jest `delegate_type^` i zostanie odpowiednio przekonwertowane.

### <a name="example"></a>Przykład

```cpp
// cliext_logical_and.cpp
// compile with: /clr
#include <cliext/algorithm>
#include <cliext/functional>
#include <cliext/vector>

typedef cliext::vector<int> Myvector;
int main()
    {
    Myvector c1;
    c1.push_back(2);
    c1.push_back(0);
    Myvector c2;
    c2.push_back(3);
    c2.push_back(0);
    Myvector c3(2, 0);

// display initial contents " 1 0" and " 1 0"
    for each (int elem in c1)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

    for each (int elem in c2)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display
    cliext::transform(c1.begin(), c1.begin() + 2,
        c2.begin(), c3.begin(), cliext::logical_and<int>());
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
2 0
3 0
1 0
```

## <a name="logical_not-stlclr"></a><a name="logical_not"></a>logical_not (STL/CLR)

Klasa szablonu opisuje element Funktor, który po wywołaniu zwraca wartość true tylko wtedy, gdy jego argument ma wartość false. Służy do określania obiektu funkcji w postaci typu argumentu.

### <a name="syntax"></a>Składnia

```cpp
template<typename Arg>
    ref class logical_not
    { // wrap operator()
public:
    typedef Arg argument_type;
    typedef bool result_type;
    typedef Microsoft::VisualC::StlClr::UnaryDelegate<
        argument_type, result_type>
        delegate_type;

    logical_not();
    logical_not(logical_not<Arg> %right);

    result_type operator()(argument_type left);
    operator delegate_type^();
    };
```

#### <a name="parameters"></a>Parametry

*ARG*<br/>
Typ argumentów.

### <a name="member-functions"></a>Funkcje elementów członkowskich

|Definicja typu|Opis|
|---------------------|-----------------|
|argument_type|Typ argumentu Funktor.|
|delegate_type|Typ delegata ogólnego.|
|result_type|Typ wyniku Funktor.|

|Członek|Opis|
|------------|-----------------|
|logical_not|Konstruuje Funktor.|

|Operator|Opis|
|--------------|-----------------|
|operator ()|Oblicza odpowiednią funkcję.|
|delegate_type operatora ^|Rzutuje Funktor na delegata.|

### <a name="remarks"></a>Uwagi

Klasa szablonu opisuje Funktor z jednym argumentem. Definiuje operator elementu członkowskiego `operator()` tak, aby, gdy obiekt jest wywoływany jako funkcja, zwraca wartość true tylko wtedy, gdy jego argument ma wartość false.

Można również przekazać obiekt jako argument funkcji, którego typ jest `delegate_type^` i zostanie odpowiednio przekonwertowane.

### <a name="example"></a>Przykład

```cpp
// cliext_logical_not.cpp
// compile with: /clr
#include <cliext/algorithm>
#include <cliext/functional>
#include <cliext/vector>

typedef cliext::vector<int> Myvector;
int main()
    {
    Myvector c1;
    c1.push_back(4);
    c1.push_back(0);
    Myvector c3(2, 0);

// display initial contents " 4 0"
    for each (int elem in c1)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display
    cliext::transform(c1.begin(), c1.begin() + 2,
        c3.begin(), cliext::logical_not<int>());
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
4 0
0 1
```

## <a name="logical_or-stlclr"></a><a name="logical_or"></a>logical_or (STL/CLR)

Klasa szablonu opisuje Funktor, który po wywołaniu zwraca wartość true tylko wtedy, gdy pierwszy argument lub drugi test ma wartość true. Służy do określania obiektu funkcji w postaci typu argumentu.

### <a name="syntax"></a>Składnia

```cpp
template<typename Arg>
    ref class logical_or
    { // wrap operator()
public:
    typedef Arg first_argument_type;
    typedef Arg second_argument_type;
    typedef bool result_type;
    typedef Microsoft::VisualC::StlClr::BinaryDelegate<
        first_argument_type, second_argument_type, result_type>
        delegate_type;

    logical_or();
    logical_or(logical_or<Arg>% right);

    result_type operator()(first_argument_type left,
        second_argument_type right);
    operator delegate_type^();
    };
```

#### <a name="parameters"></a>Parametry

*ARG*<br/>
Typ argumentów.

### <a name="member-functions"></a>Funkcje elementów członkowskich

|Definicja typu|Opis|
|---------------------|-----------------|
|delegate_type|Typ delegata ogólnego.|
|first_argument_type|Typ pierwszego argumentu Funktor.|
|result_type|Typ wyniku Funktor.|
|second_argument_type|Typ drugiego argumentu Funktor.|

|Członek|Opis|
|------------|-----------------|
|logical_or|Konstruuje Funktor.|

|Operator|Opis|
|--------------|-----------------|
|operator ()|Oblicza odpowiednią funkcję.|
|delegate_type operatora ^|Rzutuje Funktor na delegata.|

### <a name="remarks"></a>Uwagi

Klasa szablonu opisuje dwa argumenty Funktor. Definiuje operator elementu członkowskiego `operator()` tak, aby, gdy obiekt jest wywoływany jako funkcja, zwraca wartość true tylko wtedy, gdy pierwszy argument lub drugi test ma wartość true.

Można również przekazać obiekt jako argument funkcji, którego typ jest `delegate_type^` i zostanie odpowiednio przekonwertowane.

### <a name="example"></a>Przykład

```cpp
// cliext_logical_or.cpp
// compile with: /clr
#include <cliext/algorithm>
#include <cliext/functional>
#include <cliext/vector>

typedef cliext::vector<int> Myvector;
int main()
    {
    Myvector c1;
    c1.push_back(2);
    c1.push_back(0);
    Myvector c2;
    c2.push_back(0);
    c2.push_back(0);
    Myvector c3(2, 0);

// display initial contents " 2 0" and " 0 0"
    for each (int elem in c1)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

    for each (int elem in c2)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display
    cliext::transform(c1.begin(), c1.begin() + 2,
        c2.begin(), c3.begin(), cliext::logical_or<int>());
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
2 0
0 0
1 0
```

## <a name="minus-stlclr"></a><a name="minus"></a>minus (STL/CLR)

Klasa szablonu opisuje Funktor, który po wywołaniu zwraca pierwszy argument minus sekunda. Służy do określania obiektu funkcji w postaci typu argumentu.

### <a name="syntax"></a>Składnia

```cpp
template<typename Arg>
    ref class minus
    { // wrap operator()
public:
    typedef Arg first_argument_type;
    typedef Arg second_argument_type;
    typedef Arg result_type;
    typedef Microsoft::VisualC::StlClr::BinaryDelegate<
        first_argument_type, second_argument_type, result_type>
        delegate_type;

    minus();
    minus(minus<Arg>% right);

    result_type operator()(first_argument_type left,
        second_argument_type right);
    operator delegate_type^();
    };
```

#### <a name="parameters"></a>Parametry

*ARG*<br/>
Typ argumentów i wartość zwracana.

### <a name="member-functions"></a>Funkcje elementów członkowskich

|Definicja typu|Opis|
|---------------------|-----------------|
|delegate_type|Typ delegata ogólnego.|
|first_argument_type|Typ pierwszego argumentu Funktor.|
|result_type|Typ wyniku Funktor.|
|second_argument_type|Typ drugiego argumentu Funktor.|

|Członek|Opis|
|------------|-----------------|
|minus|Konstruuje Funktor.|

|Operator|Opis|
|--------------|-----------------|
|operator ()|Oblicza odpowiednią funkcję.|
|delegate_type operatora ^|Rzutuje Funktor na delegata.|

### <a name="remarks"></a>Uwagi

Klasa szablonu opisuje dwa argumenty Funktor. Definiuje operator składowej `operator()` tak, aby, gdy obiekt jest wywoływany jako funkcja, zwraca pierwszy argument minus sekunda.

Można również przekazać obiekt jako argument funkcji, którego typ jest `delegate_type^` i zostanie odpowiednio przekonwertowane.

### <a name="example"></a>Przykład

```cpp
// cliext_minus.cpp
// compile with: /clr
#include <cliext/algorithm>
#include <cliext/functional>
#include <cliext/vector>

typedef cliext::vector<int> Myvector;
int main()
    {
    Myvector c1;
    c1.push_back(4);
    c1.push_back(3);
    Myvector c2;
    c2.push_back(2);
    c2.push_back(1);
    Myvector c3(2, 0);

// display initial contents " 4 3" and " 2 1"
    for each (int elem in c1)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

    for each (int elem in c2)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display
    cliext::transform(c1.begin(), c1.begin() + 2,
        c2.begin(), c3.begin(), cliext::minus<int>());
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
4 3
2 1
2 2
```

## <a name="modulus-stlclr"></a><a name="modulus"></a>Moduł (STL/CLR)

Klasa szablonu opisuje element Funktor, który po wywołaniu zwraca pierwszy argument modulo drugi. Służy do określania obiektu funkcji w postaci typu argumentu.

### <a name="syntax"></a>Składnia

```cpp
template<typename Arg>
    ref class modulus
    { // wrap operator()
public:
    typedef Arg first_argument_type;
    typedef Arg second_argument_type;
    typedef Arg result_type;
    typedef Microsoft::VisualC::StlClr::BinaryDelegate<
        first_argument_type, second_argument_type, result_type>
        delegate_type;

    modulus();
    modulus(modulus<Arg>% right);

    result_type operator()(first_argument_type left,
        second_argument_type right);
    operator delegate_type^();
    };
```

#### <a name="parameters"></a>Parametry

*ARG*<br/>
Typ argumentów i wartość zwracana.

### <a name="member-functions"></a>Funkcje elementów członkowskich

|Definicja typu|Opis|
|---------------------|-----------------|
|delegate_type|Typ delegata ogólnego.|
|first_argument_type|Typ pierwszego argumentu Funktor.|
|result_type|Typ wyniku Funktor.|
|second_argument_type|Typ drugiego argumentu Funktor.|

|Członek|Opis|
|------------|-----------------|
|modulus|Konstruuje Funktor.|

|Operator|Opis|
|--------------|-----------------|
|operator ()|Oblicza odpowiednią funkcję.|
|delegate_type operatora ^|Rzutuje Funktor na delegata.|

### <a name="remarks"></a>Uwagi

Klasa szablonu opisuje dwa argumenty Funktor. Definiuje operator elementu członkowskiego `operator()` tak, aby, gdy obiekt jest wywoływany jako funkcja, zwraca pierwszy argument modulo w drugim.

Można również przekazać obiekt jako argument funkcji, którego typ jest `delegate_type^` i zostanie odpowiednio przekonwertowane.

### <a name="example"></a>Przykład

```cpp
// cliext_modulus.cpp
// compile with: /clr
#include <cliext/algorithm>
#include <cliext/functional>
#include <cliext/vector>

typedef cliext::vector<int> Myvector;
int main()
    {
    Myvector c1;
    c1.push_back(4);
    c1.push_back(2);
    Myvector c2;
    c2.push_back(3);
    c2.push_back(1);
    Myvector c3(2, 0);

// display initial contents " 4 2" and " 3 1"
    for each (int elem in c1)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

    for each (int elem in c2)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display
    cliext::transform(c1.begin(), c1.begin() + 2,
        c2.begin(), c3.begin(), cliext::modulus<int>());
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
4 2
3 1
1 0
```

## <a name="multiplies-stlclr"></a><a name="multiplies"></a>Mnoży (STL/CLR)

Klasa szablonu opisuje element Funktor, który po wywołaniu zwraca pierwszy argument, który przetimes sekundy. Służy do określania obiektu funkcji w postaci typu argumentu.

### <a name="syntax"></a>Składnia

```cpp
template<typename Arg>
    ref class multiplies
    { // wrap operator()
public:
    typedef Arg first_argument_type;
    typedef Arg second_argument_type;
    typedef Arg result_type;
    typedef Microsoft::VisualC::StlClr::BinaryDelegate<
        first_argument_type, second_argument_type, result_type>
        delegate_type;

    multiplies();
    multiplies(multiplies<Arg>% right);

    result_type operator()(first_argument_type left,
        second_argument_type right);
    operator delegate_type^();
    };
```

#### <a name="parameters"></a>Parametry

*ARG*<br/>
Typ argumentów i wartość zwracana.

### <a name="member-functions"></a>Funkcje elementów członkowskich

|Definicja typu|Opis|
|---------------------|-----------------|
|delegate_type|Typ delegata ogólnego.|
|first_argument_type|Typ pierwszego argumentu Funktor.|
|result_type|Typ wyniku Funktor.|
|second_argument_type|Typ drugiego argumentu Funktor.|

|Członek|Opis|
|------------|-----------------|
|multiplies|Konstruuje Funktor.|

|Operator|Opis|
|--------------|-----------------|
|operator ()|Oblicza odpowiednią funkcję.|
|delegate_type operatora ^|Rzutuje Funktor na delegata.|

### <a name="remarks"></a>Uwagi

Klasa szablonu opisuje dwa argumenty Funktor. Definiuje operator elementu członkowskiego `operator()` tak, aby, gdy obiekt jest wywoływany jako funkcja, zwraca pierwszy argument razy w drugim.

Można również przekazać obiekt jako argument funkcji, którego typ jest `delegate_type^` i zostanie odpowiednio przekonwertowane.

### <a name="example"></a>Przykład

```cpp
// cliext_multiplies.cpp
// compile with: /clr
#include <cliext/algorithm>
#include <cliext/functional>
#include <cliext/vector>

typedef cliext::vector<int> Myvector;
int main()
    {
    Myvector c1;
    c1.push_back(4);
    c1.push_back(3);
    Myvector c2;
    c2.push_back(2);
    c2.push_back(1);
    Myvector c3(2, 0);

// display initial contents " 4 3" and " 2 1"
    for each (int elem in c1)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

    for each (int elem in c2)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display
    cliext::transform(c1.begin(), c1.begin() + 2,
        c2.begin(), c3.begin(), cliext::multiplies<int>());
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
4 3
2 1
8 3
```

## <a name="negate-stlclr"></a><a name="negate"></a>Negate (STL/CLR)

Klasa szablonu opisuje Funktor, który, gdy wywoływana, zwraca swój argument negacji. Służy do określania obiektu funkcji w postaci typu argumentu.

### <a name="syntax"></a>Składnia

```cpp
template<typename Arg>
    ref class negate
    { // wrap operator()
public:
    typedef Arg argument_type;
    typedef bool result_type;
    typedef Microsoft::VisualC::StlClr::UnaryDelegate<
        argument_type, result_type>
        delegate_type;

    negate();
    negate(negate<Arg>% right);

    result_type operator()(argument_type left);
    operator delegate_type^();
    };
```

#### <a name="parameters"></a>Parametry

*ARG*<br/>
Typ argumentów.

### <a name="member-functions"></a>Funkcje elementów członkowskich

|Definicja typu|Opis|
|---------------------|-----------------|
|argument_type|Typ argumentu Funktor.|
|delegate_type|Typ delegata ogólnego.|
|result_type|Typ wyniku Funktor.|

|Członek|Opis|
|------------|-----------------|
|negate|Konstruuje Funktor.|

|Operator|Opis|
|--------------|-----------------|
|operator ()|Oblicza odpowiednią funkcję.|
|delegate_type operatora ^|Rzutuje Funktor na delegata.|

### <a name="remarks"></a>Uwagi

Klasa szablonu opisuje Funktor z jednym argumentem. Definiuje operator elementu członkowskiego `operator()` tak, aby, gdy obiekt jest wywoływany jako funkcja, zwraca swój argument Negacja.

Można również przekazać obiekt jako argument funkcji, którego typ jest `delegate_type^` i zostanie odpowiednio przekonwertowane.

### <a name="example"></a>Przykład

```cpp
// cliext_negate.cpp
// compile with: /clr
#include <cliext/algorithm>
#include <cliext/functional>
#include <cliext/vector>

typedef cliext::vector<int> Myvector;
int main()
    {
    Myvector c1;
    c1.push_back(4);
    c1.push_back(-3);
    Myvector c3(2, 0);

// display initial contents " 4 -3"
    for each (int elem in c1)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display
    cliext::transform(c1.begin(), c1.begin() + 2,
        c3.begin(), cliext::negate<int>());
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
4 -3
-4 3
```

## <a name="not_equal_to-stlclr"></a><a name="not_equal_to"></a>not_equal_to (STL/CLR)

Klasa szablonu opisuje Funktor, który po wywołaniu zwraca wartość true tylko wtedy, gdy pierwszy argument nie jest równy drugiemu. Służy do określania obiektu funkcji w postaci typu argumentu.

### <a name="syntax"></a>Składnia

```cpp
template<typename Arg>
    ref class not_equal_to
    { // wrap operator()
public:
    typedef Arg first_argument_type;
    typedef Arg second_argument_type;
    typedef bool result_type;
    typedef Microsoft::VisualC::StlClr::BinaryDelegate<
        first_argument_type, second_argument_type, result_type>
        delegate_type;

    not_equal_to();
    not_equal_to(not_equal_to<Arg>% right);

    result_type operator()(first_argument_type left,
        second_argument_type right);
    operator delegate_type^();
    };
```

#### <a name="parameters"></a>Parametry

*ARG*<br/>
Typ argumentów.

### <a name="member-functions"></a>Funkcje elementów członkowskich

|Definicja typu|Opis|
|---------------------|-----------------|
|delegate_type|Typ delegata ogólnego.|
|first_argument_type|Typ pierwszego argumentu Funktor.|
|result_type|Typ wyniku Funktor.|
|second_argument_type|Typ drugiego argumentu Funktor.|

|Członek|Opis|
|------------|-----------------|
|not_equal_to|Konstruuje Funktor.|

|Operator|Opis|
|--------------|-----------------|
|operator ()|Oblicza odpowiednią funkcję.|
|delegate_type operatora ^|Rzutuje Funktor na delegata.|

### <a name="remarks"></a>Uwagi

Klasa szablonu opisuje dwa argumenty Funktor. Definiuje operator elementu członkowskiego `operator()` tak, aby, gdy obiekt jest wywoływany jako funkcja, zwraca wartość true tylko wtedy, gdy pierwszy argument nie jest równy drugiemu.

Można również przekazać obiekt jako argument funkcji, którego typ jest `delegate_type^` i zostanie odpowiednio przekonwertowane.

### <a name="example"></a>Przykład

```cpp
// cliext_not_equal_to.cpp
// compile with: /clr
#include <cliext/algorithm>
#include <cliext/functional>
#include <cliext/vector>

typedef cliext::vector<int> Myvector;
int main()
    {
    Myvector c1;
    c1.push_back(4);
    c1.push_back(3);
    Myvector c2;
    c2.push_back(4);
    c2.push_back(4);
    Myvector c3(2, 0);

// display initial contents " 4 3" and " 4 4"
    for each (int elem in c1)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

    for each (int elem in c2)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display
    cliext::transform(c1.begin(), c1.begin() + 2,
        c2.begin(), c3.begin(), cliext::not_equal_to<int>());
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
4 3
4 4
0 1
```

## <a name="not1-stlclr"></a><a name="not1"></a>not1 — (STL/CLR)

Generuje `unary_negate` dla elementu Funktor.

### <a name="syntax"></a>Składnia

```cpp
template<typename Fun>
    unary_negate<Fun> not1(Fun% functor);
```

#### <a name="template-parameters"></a>Parametry szablonu

*Zabawny*<br/>
Typ Funktor.

#### <a name="function-parameters"></a>Parametry funkcji

*Funktor*<br/>
Funktor do zawijania.

### <a name="remarks"></a>Uwagi

Funkcja szablonu zwraca [unary_negate (STL/CLR)](../dotnet/unary-negate-stl-clr.md)`<Fun>(functor)`. Jest on używany jako wygodny sposób zawijania Funktor z jednym argumentem w Funktor, który dostarcza jej wartość logiczną.

### <a name="example"></a>Przykład

```cpp
// cliext_not1.cpp
// compile with: /clr
#include <cliext/algorithm>
#include <cliext/functional>
#include <cliext/vector>

typedef cliext::vector<int> Myvector;
int main()
    {
    Myvector c1;
    c1.push_back(4);
    c1.push_back(0);
    Myvector c3(2, 0);

// display initial contents " 4 0"
    for each (int elem in c1)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display
    cliext::logical_not<int> not_op;

    cliext::transform(c1.begin(), c1.begin() + 2, c3.begin(),
        cliext::unary_negate<cliext::logical_not<int> >(not_op));
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display with function
    cliext::transform(c1.begin(), c1.begin() + 2, c3.begin(),
        cliext::not1(not_op));
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
4 0
1 0
1 0
```

## <a name="not2-stlclr"></a><a name="not2"></a>not2 — (STL/CLR)

Generuje `binary_negate` dla elementu Funktor.

### <a name="syntax"></a>Składnia

```cpp
template<typename Fun>
    binary_negate<Fun> not2(Fun% functor);
```

#### <a name="template-parameters"></a>Parametry szablonu

*Zabawny*<br/>
Typ Funktor.

#### <a name="function-parameters"></a>Parametry funkcji

*Funktor*<br/>
Funktor do zawijania.

### <a name="remarks"></a>Uwagi

Funkcja szablonu zwraca [binary_negate (STL/CLR)](../dotnet/binary-negate-stl-clr.md)`<Fun>(functor)`. Jest on używany jako wygodny sposób zawijania Funktor dwuargumentowego w Funktor, który zapewnia jego wartość logiczną.

### <a name="example"></a>Przykład

```cpp
// cliext_not2.cpp
// compile with: /clr
#include <cliext/algorithm>
#include <cliext/functional>
#include <cliext/vector>

typedef cliext::vector<int> Myvector;
int main()
    {
    Myvector c1;
    c1.push_back(4);
    c1.push_back(3);
    Myvector c2;
    c2.push_back(4);
    c2.push_back(4);
    Myvector c3(2, 0);

// display initial contents " 4 3" and " 4 4"
    for each (int elem in c1)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

    for each (int elem in c2)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display
    cliext::less<int> less_op;

    cliext::transform(c1.begin(), c1.begin() + 2,
        c2.begin(), c3.begin(),
        cliext::binary_negate<cliext::less<int> >(less_op));
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display with function
    cliext::transform(c1.begin(), c1.begin() + 2,
        c2.begin(), c3.begin(), cliext::not2(less_op));
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
4 3
4 4
1 0
1 0
```

## <a name="plus-stlclr"></a><a name="plus"></a>Plus (STL/CLR)

Klasa szablonu opisuje Funktor, który po wywołaniu zwraca pierwszy argument Plus sekunda. Służy do określania obiektu funkcji w postaci typu argumentu.

### <a name="syntax"></a>Składnia

```cpp
template<typename Arg>
    ref class plus
    { // wrap operator()
public:
    typedef Arg first_argument_type;
    typedef Arg second_argument_type;
    typedef Arg result_type;
    typedef Microsoft::VisualC::StlClr::BinaryDelegate<
        first_argument_type, second_argument_type, result_type>
        delegate_type;

    plus();
    plus(plus<Arg>% right);

    result_type operator()(first_argument_type left,
        second_argument_type right);
    operator delegate_type^();
    };
```

#### <a name="parameters"></a>Parametry

*ARG*<br/>
Typ argumentów i wartość zwracana.

### <a name="member-functions"></a>Funkcje elementów członkowskich

|Definicja typu|Opis|
|---------------------|-----------------|
|delegate_type|Typ delegata ogólnego.|
|first_argument_type|Typ pierwszego argumentu Funktor.|
|result_type|Typ wyniku Funktor.|
|second_argument_type|Typ drugiego argumentu Funktor.|

|Członek|Opis|
|------------|-----------------|
|plus|Konstruuje Funktor.|

|Operator|Opis|
|--------------|-----------------|
|operator ()|Oblicza odpowiednią funkcję.|
|delegate_type operatora ^|Rzutuje Funktor na delegata.|

### <a name="remarks"></a>Uwagi

Klasa szablonu opisuje dwa argumenty Funktor. Definiuje operator składowej `operator()` tak, aby, gdy obiekt jest wywoływany jako funkcja, zwraca pierwszy argument Plus sekunda.

Można również przekazać obiekt jako argument funkcji, którego typ jest `delegate_type^` i zostanie odpowiednio przekonwertowane.

### <a name="example"></a>Przykład

```cpp
// cliext_plus.cpp
// compile with: /clr
#include <cliext/algorithm>
#include <cliext/functional>
#include <cliext/vector>

typedef cliext::vector<int> Myvector;
int main()
    {
    Myvector c1;
    c1.push_back(4);
    c1.push_back(3);
    Myvector c2;
    c2.push_back(2);
    c2.push_back(1);
    Myvector c3(2, 0);

// display initial contents " 4 3" and " 2 1"
    for each (int elem in c1)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

    for each (int elem in c2)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display
    cliext::transform(c1.begin(), c1.begin() + 2,
        c2.begin(), c3.begin(), cliext::plus<int>());
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
4 3
2 1
6 4
```

## <a name="unary_delegate-stlclr"></a><a name="unary_delegate"></a>unary_delegate (STL/CLR)

Klasa genereic opisuje delegata z jednym argumentem. Służy do tego określenie delegata w odniesieniu do jego argumentu i typów zwracanych.

### <a name="syntax"></a>Składnia

```cpp
generic<typename Arg,
    typename Result>
    delegate Result unary_delegate(Arg);
```

#### <a name="parameters"></a>Parametry

*ARG*<br/>
Typ argumentu.

*Wynika*<br/>
Typ zwracany.

### <a name="remarks"></a>Uwagi

Delegat genereic opisuje funkcję z jednym argumentem.

Należy pamiętać, że w przypadku:

`unary_delegare<int, int> Fun1;`

`unary_delegare<int, int> Fun2;`

typy `Fun1` i `Fun2` są synonimami, a w przypadku:

`delegate int Fun1(int);`

`delegate int Fun2(int);`

nie są tego samego typu.

### <a name="example"></a>Przykład

```cpp
// cliext_unary_delegate.cpp
// compile with: /clr
#include <cliext/functional>

int hash_val(wchar_t val)
    {
    return ((val * 17 + 31) % 67);
    }

typedef cliext::unary_delegate<wchar_t, int> Mydelegate;
int main()
    {
    Mydelegate^ myhash = gcnew Mydelegate(&hash_val);

    System::Console::WriteLine("hash(L'a') = {0}", myhash(L'a'));
    System::Console::WriteLine("hash(L'b') = {0}", myhash(L'b'));
    return (0);
    }
```

```Output
hash(L'a') = 5
hash(L'b') = 22
```

## <a name="unary_delegate_noreturn-stlclr"></a><a name="unary_delegate_noreturn"></a>unary_delegate_noreturn (STL/CLR)

Klasa genereic opisuje delegata z jednym argumentem, który zwraca wartość **void**. Służy do tego określenie delegata pod względem jego typu argumentu.

### <a name="syntax"></a>Składnia

```cpp
generic<typename Arg>
    delegate void unary_delegate_noreturn(Arg);
```

#### <a name="parameters"></a>Parametry

*ARG*<br/>
Typ argumentu.

### <a name="remarks"></a>Uwagi

Delegat genereic opisuje funkcję jednoargumentową zwracającą **typ void**.

Należy pamiętać, że w przypadku:

`unary_delegare_noreturn<int> Fun1;`

`unary_delegare_noreturn<int> Fun2;`

typy `Fun1` i `Fun2` są synonimami, a w przypadku:

`delegate void Fun1(int);`

`delegate void Fun2(int);`

nie są tego samego typu.

### <a name="example"></a>Przykład

```cpp
// cliext_unary_delegate_noreturn.cpp
// compile with: /clr
#include <cliext/functional>

void hash_val(wchar_t val)
    {
    System::Console::WriteLine("hash({0}) = {1}",
       val, (val * 17 + 31) % 67);
    }

typedef cliext::unary_delegate_noreturn<wchar_t> Mydelegate;
int main()
    {
    Mydelegate^ myhash = gcnew Mydelegate(&hash_val);

    myhash(L'a');
    myhash(L'b');
    return (0);
    }
```

```Output
hash(a) = 5
hash(b) = 22
```

## <a name="unary_negate-stlclr"></a><a name="unary_negate"></a>unary_negate (STL/CLR)

Klasa szablonu opisuje Funktor, który, gdy wywoływana, zwraca wartość logiczną, a nie przechowywany Funktor jednego argumentu. Służy do określania obiektu funkcji w postaci Funktor przechowywanych elementów.

### <a name="syntax"></a>Składnia

```cpp
template<typename Fun>
    ref class unary_negate
    { // wrap operator()
public:
    typedef Fun stored_function_type;
    typedef typename Fun::argument_type argument_type;
    typedef bool result_type;
    typedef Microsoft::VisualC::StlClr::UnaryDelegate<
        argument_type, result_type>
        delegate_type;

    unary_negate(Fun% functor);
    unary_negate(unary_negate<Fun>% right);

    result_type operator()(argument_type left);
    operator delegate_type^();
    };
```

#### <a name="parameters"></a>Parametry

*Zabawny*<br/>
Typ przechowywanego Funktor.

### <a name="member-functions"></a>Funkcje elementów członkowskich

|Definicja typu|Opis|
|---------------------|-----------------|
|argument_type|Typ argumentu Funktor.|
|delegate_type|Typ delegata ogólnego.|
|result_type|Typ wyniku Funktor.|

|Członek|Opis|
|------------|-----------------|
|unary_negate|Konstruuje Funktor.|

|Operator|Opis|
|--------------|-----------------|
|operator ()|Oblicza odpowiednią funkcję.|
|delegate_type ^|Rzutuje Funktor na delegata.|

### <a name="remarks"></a>Uwagi

Klasa szablonu opisuje Funktor z jednym argumentem, który przechowuje kolejną Funktor z jednym argumentem. Definiuje operator elementu członkowskiego `operator()` tak, aby, gdy obiekt jest wywoływany jako funkcja, zwraca wartość logiczną, a nie przechowywane Funktor wywołana z argumentem.

Można również przekazać obiekt jako argument funkcji, którego typ jest `delegate_type^` i zostanie odpowiednio przekonwertowane.

### <a name="example"></a>Przykład

```cpp
// cliext_unary_negate.cpp
// compile with: /clr
#include <cliext/algorithm>
#include <cliext/functional>
#include <cliext/vector>

typedef cliext::vector<int> Myvector;
int main()
    {
    Myvector c1;
    c1.push_back(4);
    c1.push_back(0);
    Myvector c3(2, 0);

// display initial contents " 4 0"
    for each (int elem in c1)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display
    cliext::logical_not<int> not_op;

    cliext::transform(c1.begin(), c1.begin() + 2, c3.begin(),
        cliext::unary_negate<cliext::logical_not<int> >(not_op));
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display with function
    cliext::transform(c1.begin(), c1.begin() + 2, c3.begin(),
        cliext::not1(not_op));
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
4 0
1 0
1 0
```
