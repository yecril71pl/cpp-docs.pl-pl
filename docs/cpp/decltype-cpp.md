---
title: decltype (C++)
ms.date: 11/04/2016
f1_keywords:
- decltype_cpp
helpviewer_keywords:
- operators [C++], decltype
- decltype operator
- operators [C++], type of an expression
- operators [C++], deduce expression type
ms.assetid: 6dcf8888-8196-4f13-af50-51e3797255d4
ms.openlocfilehash: 0a4e9eb015df056dfe2a35da18cfa50875ced432
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2019
ms.locfileid: "65222460"
---
# <a name="decltype--c"></a>decltype (C++)

**Decltype** Specyfikator typu daje typu określonego wyrażenia. **Decltype** specyfikator, typu, łącznie z [auto — słowo kluczowe](../cpp/auto-cpp.md), jest przydatne głównie dla deweloperów, którzy zapisu biblioteki szablonów. Użyj **automatycznie** i **decltype** do deklarowania funkcji szablonu, którego zwracany typ jest zależny od typów argumentów szablonu. Możesz też korzystać z **automatycznie** i **decltype** do deklarowania funkcji szablonu, który zawija wywołanie do innej funkcji, a następnie zwraca typ zwracany opakowana funkcja.

## <a name="syntax"></a>Składnia

```
decltype( expression )
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*expression*|Wyrażenie. Aby uzyskać więcej informacji, zobacz [wyrażenia](../cpp/expressions-cpp.md).|

## <a name="return-value"></a>Wartość zwracana

Typ *wyrażenie* parametru.

## <a name="remarks"></a>Uwagi

**Decltype** Specyfikator typu jest obsługiwana w programie Visual Studio 2010 lub nowszy i może być używany z kodu natywnego lub zarządzanych. `decltype(auto)` (C ++ 14) jest obsługiwana w programie Visual Studio 2015 i nowszych wersjach.

Kompilator używa następujących reguł, aby określić typ *wyrażenie* parametru.

- Jeśli *wyrażenie* parametru jest identyfikatorem lub [dostęp do składowej klasy](../cpp/member-access-operators-dot-and.md), `decltype(expression)` jest typem jednostki o nazwie określonej przez *wyrażenie*. Jeśli nie ma takich jednostki lub *wyrażenie* zestaw przeciążonych funkcji nazwy parametrów, kompilator daje komunikat o błędzie.

- Jeśli *wyrażenie* parametru jest wywołaniem funkcji lub funkcję przeciążonego operatora `decltype(expression)` jest zwracany typ funkcji. Nawiasy wokół przeciążonego operatora są ignorowane.

- Jeśli *wyrażenie* parametr jest [rvalue](../cpp/lvalues-and-rvalues-visual-cpp.md), `decltype(expression)` jest typem *wyrażenie*. Jeśli *wyrażenie* parametr jest [l-wartości](../cpp/lvalues-and-rvalues-visual-cpp.md), `decltype(expression)` jest [odwołanie lvalue](../cpp/lvalue-reference-declarator-amp.md) do typu *wyrażenie*.

Poniższy przykład kodu demonstruje niektórych zastosowań **decltype** Specyfikator typu. Najpierw Przyjmij, które mają kodowane następujące instrukcje.

```cpp
int var;
const int&& fx();
struct A { double x; }
const A* a = new A();
```

Następnie sprawdź typy, które są zwracane przez cztery **decltype** instrukcji w poniższej tabeli.

|Instrukcja|Typ|Uwagi|
|---------------|----------|-----------|
|`decltype(fx());`|`const int&&`|[Odwołanie rvalue](../cpp/rvalue-reference-declarator-amp-amp.md) do **const int**.|
|`decltype(var);`|**int**|Typ zmiennej `var`.|
|`decltype(a->x);`|**double**|Typ dostępu do elementu członkowskiego.|
|`decltype((a->x));`|`const double&`|Wewnętrzny nawiasy, że instrukcja ma zostać obliczone jako wyrażenia zamiast dostęp do elementu członkowskiego. A ponieważ `a` jest zadeklarowany jako `const` wskaźnika, typ jest odwołaniem do **const double**.|

## <a name="decltype-and-auto"></a>Decltype i automatycznie

W języku C ++ 14, można użyć `decltype(auto)` z końcowym typem zwracanym do deklarowania funkcji szablonu, którego typem zwracanym zależy od typów argumentów szablonu.

W języku C ++ 11, możesz użyć **decltype** wpisz specyfikatora na końcowym typem zwracanym, wraz z **automatycznie** — słowo kluczowe do deklarowania funkcji szablonu, którego typem zwracanym jest zależna od typów szablonu argumenty. Rozważmy na przykład poniższy kod, w której zwracany typ funkcji szablonu zależy od typów argumentów szablonu. W przykładzie kodu *nieznany* symbolu zastępczego wskazuje, że nie można określić typ zwracany.

```cpp
template<typename T, typename U>
UNKNOWN func(T&& t, U&& u){ return t + u; };
```

Wprowadzenie **decltype** Specyfikator typu umożliwia zatem programistą, aby uzyskać typ wyrażenia, które zwraca funkcja szablonu. Użyj *Składnia deklaracji funkcji alternatywne* , jest wyświetlany później **automatycznie** — słowo kluczowe i **decltype** specyfikator do deklarowania typu  *opóźnione określony* typ zwracany. Opóźnione określony typ zwracany jest określana podczas deklaracji jest kompilowany, zamiast po kanonicznej zakodowanej.

Poniższy prototyp ilustruje Składnia deklaracji funkcji alternatywne. Należy pamiętać, że **const** i **volatile** kwalifikatorów i **throw** [Specyfikacja wyjątku](../cpp/exception-specifications-throw-cpp.md) są opcjonalne. *Function_body* symbol zastępczy reprezentuje instrukcję złożonego, która określa, jak działa funkcja. Jako kodowania rozwiązaniem jest najlepszym *wyrażenie* symbol zastępczy w **decltype** instrukcji powinien być zgodny z wyrażeniem określonym przez **zwracają** instrukcji, jeśli występują w *function_body*.

**automatyczne** *nazwa_funkcji* **(** *parametry*<sub>zoptymalizowany pod kątem</sub> **)**  **Const**<sub>zoptymalizowany pod kątem</sub> **volatile**<sub>zoptymalizowany pod kątem</sub> **->** **decltype (** *wyrażenie* **)** **throw**<sub>zoptymalizowany pod kątem</sub> **{** *function_body* **};**

W poniższym przykładzie kodu późno określony zwracany typ `myFunc` funkcji szablonu jest określana przez typy `t` i `u` argumentów szablonu. Jako najlepsze praktyki programowania, przykładowy kod używa również odwołania rvalue i `forward` funkcji szablonu, który obsługuje *doskonała przekazywania*. Aby uzyskać więcej informacji, zobacz [Rvalue Reference Declarator: & &](../cpp/rvalue-reference-declarator-amp-amp.md).

```cpp
//C++11
template<typename T, typename U>
auto myFunc(T&& t, U&& u) -> decltype (forward<T>(t) + forward<U>(u))
        { return forward<T>(t) + forward<U>(u); };

//C++14
template<typename T, typename U>
decltype(auto) myFunc(T&& t, U&& u)
        { return forward<T>(t) + forward<U>(u); };
```

## <a name="decltype-and-forwarding-functions-c11"></a>Decltype i funkcji przekazywania (C ++ 11)

Funkcje przekazywania owijają odwołania do innych funkcji. Należy wziąć pod uwagę szablonu funkcji, która przekazuje argumenty lub wyniki wyrażenia, które obejmuje tych argumentów, do innej funkcji. Ponadto funkcja przesyłania dalej zwraca wynik wywołania innych funkcji. W tym scenariuszu zwracany typ funkcji przekazywania powinna być taka sama, jako typ zwracany funkcji opakowana.

W tym scenariuszu nie można zapisać odpowiedni typ wyrażenia bez **decltype** Specyfikator typu. **Decltype** Specyfikator typu umożliwia przekazywanie ogólnych funkcji, ponieważ nie traci wymaganych informacji na temat tego, czy funkcja zwraca typ odwołania. Dla przykładu kodu funkcji przekazywania, zobacz poprzedni `myFunc` przykład funkcji szablonu.

## <a name="example"></a>Przykład

Poniższy przykład kodu deklaruje późno określony zwracany typ funkcji szablonu `Plus()`. `Plus` Funkcja przetwarza dwóch argumentów operacji za pomocą **operator +** przeciążenia. W związku z tym, interpretacja operatora znaku plus (+) i zwracanym typem `Plus` funkcji zależy od typów argumentów funkcji.

```cpp
// decltype_1.cpp
// compile with: cl /EHsc decltype_1.cpp

#include <iostream>
#include <string>
#include <utility>
#include <iomanip>

using namespace std;

template<typename T1, typename T2>
auto Plus(T1&& t1, T2&& t2) ->
   decltype(forward<T1>(t1) + forward<T2>(t2))
{
   return forward<T1>(t1) + forward<T2>(t2);
}

class X
{
   friend X operator+(const X& x1, const X& x2)
   {
      return X(x1.m_data + x2.m_data);
   }

public:
   X(int data) : m_data(data) {}
   int Dump() const { return m_data;}
private:
   int m_data;
};

int main()
{
   // Integer
   int i = 4;
   cout <<
      "Plus(i, 9) = " <<
      Plus(i, 9) << endl;

   // Floating point
   float dx = 4.0;
   float dy = 9.5;
   cout <<
      setprecision(3) <<
      "Plus(dx, dy) = " <<
      Plus(dx, dy) << endl;

   // String
   string hello = "Hello, ";
   string world = "world!";
   cout << Plus(hello, world) << endl;

   // Custom type
   X x1(20);
   X x2(22);
   X x3 = Plus(x1, x2);
   cout <<
      "x3.Dump() = " <<
      x3.Dump() << endl;
}
```

```Output
Plus(i, 9) = 13
Plus(dx, dy) = 13.5
Hello, world!
x3.Dump() = 42
```

## <a name="example"></a>Przykład

**Visual Studio 2017 i nowszym:** Jeśli szablony są deklarowane, a nie wystąpienia, w którym kompilator analizuje decltype argumentów. W związku z tym jeśli specjalizacji zależne od innych znajduje się w argumencie decltype, nie zostaną przeniesione czasu wystąpienia i zostaną niezwłocznie przetworzone i wszystkie wynikowe błędy będą zdiagnozować, w tym czasie.

Poniższy przykład przedstawia takich błąd kompilatora, który jest wywoływany w punkcie deklaracji:

```cpp
#include <utility>
template <class T, class ReturnT, class... ArgsT> class IsCallable
{
public:
   struct BadType {};
   template <class U>
   static decltype(std::declval<T>()(std::declval<ArgsT>()...)) Test(int); //C2064. Should be declval<U>
   template <class U>
   static BadType Test(...);
   static constexpr bool value = std::is_convertible<decltype(Test<T>(0)), ReturnT>::value;
};

constexpr bool test1 = IsCallable<int(), int>::value;
static_assert(test1, "PASS1");
constexpr bool test2 = !IsCallable<int*, int>::value;
static_assert(test2, "PASS2");
```

## <a name="requirements"></a>Wymagania

Program Visual Studio 2010 lub nowszy.

`decltype(auto)` wymaga programu Visual Studio 2015 lub nowszej.