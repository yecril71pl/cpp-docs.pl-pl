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
ms.openlocfilehash: 1ed07b8987df7b621ea2809409069cc1121fa24f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80180215"
---
# <a name="decltype--c"></a>decltype (C++)

Specyfikator typu **decltype** zwraca typ określonego wyrażenia. Specyfikator typu **decltype** wraz ze [słowem kluczowym autosłowo kluczowe](../cpp/auto-cpp.md)jest przydatny głównie dla deweloperów, którzy piszą biblioteki szablonów. Użyj **opcji** autoi **decltype** , aby zadeklarować funkcję szablonu, której typ zwracany zależy od typów argumentów szablonu. Lub **Użyj funkcji** autoi **decltype** , aby zadeklarować funkcję szablonu, która zawija wywołanie do innej funkcji, a następnie zwraca zwracany typ funkcji opakowanej.

## <a name="syntax"></a>Składnia

```
decltype( expression )
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*wyrażenia*|Wyrażenie. Aby uzyskać więcej informacji, zobacz [Expressions](../cpp/expressions-cpp.md).|

## <a name="return-value"></a>Wartość zwracana

Typ parametru *wyrażenia* .

## <a name="remarks"></a>Uwagi

Specyfikator typu **decltype** jest obsługiwany w programie Visual Studio 2010 lub jego nowszych wersjach i może być używany z kodem natywnym lub zarządzanym. `decltype(auto)` (C++ 14) jest obsługiwany w programie Visual Studio 2015 i nowszych.

Kompilator używa następujących reguł, aby określić typ parametru *wyrażenia* .

- Jeśli parametr *Expression* jest identyfikatorem lub [dostępem do elementu członkowskiego klasy](../cpp/member-access-operators-dot-and.md), `decltype(expression)` jest typem *jednostki o nazwie.* Jeśli nie istnieje taka jednostka lub parametr *wyrażenia* nazywa zestaw przeciążonych funkcji, kompilator generuje komunikat o błędzie.

- Jeśli parametr *Expression* jest wywołaniem funkcji lub funkcji przeciążonego operatora, `decltype(expression)` jest typem zwracanym funkcji. Nawiasy wokół przeciążonego operatora są ignorowane.

- Jeśli parametr *Expression* jest [rvalue](../cpp/lvalues-and-rvalues-visual-cpp.md), `decltype(expression)` jest typem *wyrażenia*. Jeśli parametr *Expression* jest [lvalue](../cpp/lvalues-and-rvalues-visual-cpp.md), `decltype(expression)` jest [odwołaniem lvalue](../cpp/lvalue-reference-declarator-amp.md) do typu *wyrażenia*.

Poniższy przykład kodu demonstruje niektóre zastosowania specyfikatora typu **decltype** . Najpierw założono, że zostały zakodowane następujące instrukcje.

```cpp
int var;
const int&& fx();
struct A { double x; }
const A* a = new A();
```

Następnie zapoznaj się z typami zwracanymi przez cztery instrukcje **decltype** w poniższej tabeli.

|Wyciąg|Typ|Uwagi|
|---------------|----------|-----------|
|`decltype(fx());`|`const int&&`|[Odwołanie rvalue](../cpp/rvalue-reference-declarator-amp-amp.md) do **stałej int**.|
|`decltype(var);`|**int**|Typ zmiennej `var`.|
|`decltype(a->x);`|**double**|Typ dostępu do elementu członkowskiego.|
|`decltype((a->x));`|`const double&`|Nawiasy wewnętrzne powodują, że instrukcja jest szacowana jako wyrażenie, a nie dostęp do elementu członkowskiego. I ponieważ `a` jest zadeklarowany jako wskaźnik `const`, typ jest odwołaniem do **podwójnej precyzji**.|

## <a name="decltype-and-auto"></a>Decltype i

W języku C++ 14 można użyć `decltype(auto)` bez końcowego typu zwracanego, aby zadeklarować funkcję szablonu, której typ zwracany zależy od typów argumentów szablonu.

W języku C++ 11 można użyć specyfikatora typu **decltype** na końcowym typie zwracanym **ze słowem** kluczowym autosłowo, aby zadeklarować funkcję szablonu, której typ zwracany zależy od typów argumentów szablonu. Rozważmy na przykład poniższy przykład kodu, w którym zwracany typ funkcji szablonu zależy od typów argumentów szablonu. W przykładzie kodu *nieznany* symbol zastępczy wskazuje, że nie można określić zwracanego typu.

```cpp
template<typename T, typename U>
UNKNOWN func(T&& t, U&& u){ return t + u; };
```

Wprowadzenie specyfikatora typu **decltype** umożliwia deweloperowi uzyskanie typu wyrażenia zwracanego przez funkcję szablonu. Użyj *składni deklaracji funkcji alternatywnej* , która jest wyświetlana później, **słowa** kluczowego "autosłowo kluczowe" i specyfikatora typu **decltype** do deklarowania typu zwracanego z *późnym* typem. Typ zwracany określony jako późny jest określany podczas kompilowania deklaracji, a nie w chwili, gdy jest ona kodowana.

Następujący prototyp ilustruje składnię alternatywnej deklaracji funkcji. Należy zauważyć, że kwalifikatory **const** i **volatile** oraz [Specyfikacja wyjątku](../cpp/exception-specifications-throw-cpp.md) **throw** są opcjonalne. Symbol zastępczy *function_body* reprezentuje instrukcję złożoną, która określa działanie funkcji. Najlepszym rozwiązaniem w zakresie kodowania jest symbol zastępczy *wyrażenia* w instrukcji **decltype** , który powinien być zgodny z wyrażeniem określonym przez instrukcję **Return** , jeśli istnieje, w *function_body*.

**auto** *autofunction_name* **(** *parameters*<sub>opt Parameters</sub> **)** **const**<sub>opt</sub> **unvolatile**<sub>opt</sub> **->** **decltype (** *wyrażenie* **)** **throw**<sub>opt</sub> **{** *function_body* **};**

W poniższym przykładzie kodu, opóźniony typ zwracany funkcji szablonu `myFunc` jest określany przez typy argumentów szablonu `t` i `u`. Jako najlepsze rozwiązanie do pisania kodu używa również odwołań rvalue i szablonu funkcji `forward`, który obsługuje *doskonałe przekazywanie dalej*. Aby uzyskać więcej informacji, zobacz [rvalue Reference deklarator: & &](../cpp/rvalue-reference-declarator-amp-amp.md).

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

W tym scenariuszu nie można zapisać odpowiedniego wyrażenia typu bez specyfikatora typu **decltype** . Specyfikator typu **decltype** umożliwia ogólne funkcje przekazywania, ponieważ nie tracą wymaganych informacji o tym, czy funkcja zwraca typ referencyjny. Aby zapoznać się z przykładem kodu funkcji przekazywania, zobacz poprzedni przykład funkcji szablonu `myFunc`.

## <a name="example"></a>Przykład

Poniższy przykład kodu deklaruje opóźniony, zwracany typ funkcji szablonu `Plus()`. Funkcja `Plus` przetwarza dwa operandy za pomocą **operatora +** Przeciążenie. W związku z tym interpretacja operatora plus (+) i zwracanego typu funkcji `Plus` zależy od typów argumentów funkcji.

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

**Program Visual Studio 2017 lub nowszy:** Kompilator analizuje argumenty decltype podczas deklarowania szablonów zamiast tworzenia wystąpienia. W związku z tym, jeśli w argumencie decltype zostanie znaleziony niezależna specjalizacja, nie zostanie ona odroczona do utworzenia wystąpienia — czas i zostanie przetworzona natychmiast, a wszystkie wynikające z niego błędy będą zdiagnozowane w tym czasie.

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
