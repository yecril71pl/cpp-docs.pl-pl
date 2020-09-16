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
ms.openlocfilehash: 9e769bbef66bd1b55b9d445874f00d37a736025e
ms.sourcegitcommit: c1fd917a8c06c6504f66f66315ff352d0c046700
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/16/2020
ms.locfileid: "90683484"
---
# <a name="decltype--c"></a>decltype (C++)

**`decltype`** Specyfikator typu zwraca typ określonego wyrażenia. **`decltype`** Specyfikator typu, wraz ze [ `auto` słowem kluczowym](../cpp/auto-cpp.md), jest przydatny głównie dla deweloperów, którzy zapisują biblioteki szablonów. Użyj **`auto`** i, **`decltype`** Aby zadeklarować funkcję szablonu, której typ zwracany zależy od typów argumentów szablonu. Lub Użyj **`auto`** i, **`decltype`** Aby zadeklarować funkcję szablonu, która zawija wywołanie do innej funkcji, a następnie zwraca zwracany typ funkcji opakowanej.

## <a name="syntax"></a>Składnia

> **`decltype(`***wyrażenie***`)`**

### <a name="parameters"></a>Parametry

*wyrażenia*\
Wyrażenie. Aby uzyskać więcej informacji, zobacz [Expressions](../cpp/expressions-cpp.md).

## <a name="return-value"></a>Wartość zwracana

Typ parametru *wyrażenia* .

## <a name="remarks"></a>Uwagi

**`decltype`** Specyfikator typu jest obsługiwany w programie Visual Studio w wersji 2010 lub nowszej i może być używany z kodem natywnym lub zarządzanym. `decltype(auto)` (C++ 14) jest obsługiwany w programie Visual Studio 2015 i nowszych.

Kompilator używa następujących reguł, aby określić typ parametru *wyrażenia* .

- Jeśli parametr *Expression* jest identyfikatorem lub [dostępem do elementu członkowskiego klasy](../cpp/member-access-operators-dot-and.md), `decltype(expression)` jest typem jednostki o nazwie na *wyrażenie*. Jeśli nie istnieje taka jednostka lub parametr *wyrażenia* nazywa zestaw przeciążonych funkcji, kompilator generuje komunikat o błędzie.

- Jeśli parametr *Expression* jest wywołaniem funkcji lub funkcji przeciążonego operatora, `decltype(expression)` jest zwracanym typem funkcji. Nawiasy wokół przeciążonego operatora są ignorowane.

- Jeśli parametr *Expression* jest [rvalue](../cpp/lvalues-and-rvalues-visual-cpp.md), `decltype(expression)` jest typem *wyrażenia*. Jeśli parametr *Expression* jest [lvalue](../cpp/lvalues-and-rvalues-visual-cpp.md), `decltype(expression)` jest [odwołaniem lvalue](../cpp/lvalue-reference-declarator-amp.md) do typu *wyrażenia*.

Poniższy przykład kodu demonstruje niektóre zastosowania **`decltype`** specyfikatora typu. Najpierw założono, że zostały zakodowane następujące instrukcje.

```cpp
int var;
const int&& fx();
struct A { double x; }
const A* a = new A();
```

Następnie należy przeanalizować typy, które są zwracane przez cztery **`decltype`** instrukcje w poniższej tabeli.

|Instrukcja|Typ|Uwagi|
|---------------|----------|-----------|
|`decltype(fx());`|`const int&&`|[Odwołanie rvalue](../cpp/rvalue-reference-declarator-amp-amp.md) do **`const int`** .|
|`decltype(var);`|**`int`**|Typ zmiennej `var` .|
|`decltype(a->x);`|**`double`**|Typ dostępu do elementu członkowskiego.|
|`decltype((a->x));`|`const double&`|Nawiasy wewnętrzne powodują, że instrukcja jest szacowana jako wyrażenie, a nie dostęp do elementu członkowskiego. I ponieważ `a` jest zadeklarowany jako **`const`** wskaźnik, typ jest odwołaniem do **`const double`** .|

## <a name="decltype-and-auto"></a>Decltype i

W języku C++ 14 można użyć `decltype(auto)` bez końcowego typu zwracanego, aby zadeklarować funkcję szablonu, której typ zwracany zależy od typów argumentów szablonu.

W języku C++ 11 można użyć **`decltype`** specyfikatora typu na końcowym typie zwracanym ze **`auto`** słowem kluczowym, aby zadeklarować funkcję szablonu, której typ zwracany zależy od typów argumentów szablonu. Rozważmy na przykład poniższy przykład kodu, w którym zwracany typ funkcji szablonu zależy od typów argumentów szablonu. W przykładzie kodu *nieznany* symbol zastępczy wskazuje, że nie można określić zwracanego typu.

```cpp
template<typename T, typename U>
UNKNOWN func(T&& t, U&& u){ return t + u; };
```

Wprowadzenie **`decltype`** specyfikatora typu umożliwia deweloperowi uzyskanie typu wyrażenia zwracanego przez funkcję szablonu. Użyj *składni deklaracji funkcji alternatywnej* , która jest wyświetlana później, **`auto`** słowa kluczowego i **`decltype`** specyfikatora typu w celu zadeklarowania typu zwracanego z *późnym* typem. Typ zwracany określony jako późny jest określany podczas kompilowania deklaracji, a nie w chwili, gdy jest ona kodowana.

Następujący prototyp ilustruje składnię alternatywnej deklaracji funkcji. Należy zauważyć, **`const`** że **`volatile`** kwalifikatory i i **`throw`** [Specyfikacja wyjątku](../cpp/exception-specifications-throw-cpp.md) są opcjonalne. Symbol zastępczy *function_body* reprezentuje instrukcję złożoną, która określa działanie funkcji. Jako najlepsze rozwiązanie do pisania, symbol zastępczy *wyrażenia* w **`decltype`** instrukcji powinien pasować do wyrażenia określonego przez **`return`** instrukcję, jeśli istnieje, w *function_body*.

**`auto`***function_name* **`(`** wybór wyrażenia<sub>opt opt</sub> wyboru dla *parametrów* **`)`** **`const`** <sub>opt</sub> **`volatile`** <sub>opt</sub> **`->`** **`decltype(`** *expression* **`)`** **`noexcept`** <sub>opt</sub> **`{`** *function_body***`};`**

W poniższym przykładzie kodu, opóźniony typ zwracany `myFunc` funkcji szablonu jest określany przez typy `t` `u` argumentów i. Najlepszym rozwiązaniem w zakresie kodowania jest użycie przez przykład odwołań rvalue i `forward` szablonu funkcji, który obsługuje *doskonałe przekazywanie dalej*. Aby uzyskać więcej informacji, zobacz [rvalue Reference deklarator:  &&](../cpp/rvalue-reference-declarator-amp-amp.md).

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

## <a name="decltype-and-forwarding-functions-c11"></a>Funkcje decltype i przekazywania (C++ 11)

Funkcje przekazywania zawijają wywołania do innych funkcji. Rozważmy szablon funkcji, który przekazuje jego argumenty, lub wyniki wyrażenia, które obejmuje te argumenty, do innej funkcji. Ponadto funkcja przekazywania zwraca wynik wywołania innej funkcji. W tym scenariuszu zwracany typ funkcji przekazywania powinien być taki sam jak typ zwracany funkcji opakowanej.

W tym scenariuszu nie można zapisać odpowiedniego wyrażenia typu bez **`decltype`** specyfikatora typu. **`decltype`** Specyfikator typu włącza ogólne funkcje przekazywania, ponieważ nie utraci wymaganych informacji o tym, czy funkcja zwraca typ referencyjny. Aby zapoznać się z przykładem kodu funkcji przekazywania, zobacz `myFunc` przykład poprzedniej funkcji szablonu.

## <a name="examples"></a>Przykłady

Poniższy przykład kodu deklaruje opóźniony określony typ zwracany funkcji szablonu `Plus()` . `Plus`Funkcja przetwarza dwa operandy przy użyciu **`operator+`** przeciążenia. W związku z tym interpretacja operatora plus ( **`+`** ) i zwracanego typu `Plus` funkcji zależy od typów argumentów funkcji.

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

**Program Visual Studio 2017 lub nowszy:** Kompilator analizuje **`decltype`** argumenty, gdy zadeklarowane są szablony zamiast tworzenia wystąpienia. W związku z tym, jeśli w argumencie zostanie znaleziony niezależna specjalizacja **`decltype`** , nie zostanie ona odroczona do utworzenia wystąpienia — czas i zostanie przetworzona natychmiast, a wszystkie wynikające z niego błędy będą zdiagnozowane w tym czasie.

Poniższy przykład pokazuje błąd kompilatora, który jest wywoływany w punkcie deklaracji:

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

`decltype(auto)` wymaga programu Visual Studio 2015 lub nowszego.
