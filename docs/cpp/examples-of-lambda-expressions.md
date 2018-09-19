---
title: Przykłady wyrażeń Lambda | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- lambda expressions [C++], examples
ms.assetid: 52506b15-0771-4190-a966-2f302049ca86
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b25d2914285e6ddab9e727f484823d40c9910d3b
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46061828"
---
# <a name="examples-of-lambda-expressions"></a>Przykłady wyrażeń lambda

W tym artykule przedstawiono sposób stosowania wyrażeń lambda w programach. Aby uzyskać przegląd wyrażeń lambda, zobacz [wyrażeń Lambda](../cpp/lambda-expressions-in-cpp.md). Aby uzyskać więcej informacji na temat struktury wyrażenia lambda, zobacz [Lambda Expression Syntax](../cpp/lambda-expression-syntax.md).

##  <a name="declaringLambdaExpressions"></a> Deklarowanie wyrażeń Lambda

### <a name="example-1"></a>Przykład 1

Ponieważ wyrażenie lambda jest wpisane, można je przypisać do **automatycznie** zmiennej lub [funkcja](../standard-library/function-class.md) obiektu, jak pokazano poniżej:

### <a name="code"></a>Kod

```cpp
// declaring_lambda_expressions1.cpp
// compile with: /EHsc /W4
#include <functional>
#include <iostream>

int main()
{

    using namespace std;

    // Assign the lambda expression that adds two numbers to an auto variable.
    auto f1 = [](int x, int y) { return x + y; };

    cout << f1(2, 3) << endl;

    // Assign the same lambda expression to a function object.
    function<int(int, int)> f2 = [](int x, int y) { return x + y; };

    cout << f2(3, 4) << endl;
}
```

### <a name="output"></a>Dane wyjściowe

```Output
5
7
```

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [automatycznie](../cpp/auto-cpp.md), [funkcji klasy](../standard-library/function-class.md), i [wywołania funkcji](../cpp/function-call-cpp.md).

Chociaż wyrażenia lambda najczęściej są deklarowane w treści funkcji, możesz je zadeklarować gdziekolwiek, można zainicjować zmienną.

### <a name="example-2"></a>Przykład 2

Kompilator języka Visual C++ wiąże wyrażenie lambda do swoich zmiennych przechwyconych, gdy wyrażenie jest zadeklarowane, a nie wtedy, gdy wyrażenie jest wywoływane. Poniższy przykład pokazuje Wyrażenie lambda, które przechwytuje zmienną lokalną `i` przez wartość i zmienną lokalną `j` przez odwołanie. Ponieważ wyrażenie lambda przechwytuje `i` według wartości, ponowne przypisanie `i` później w programie nie wpływa na wynik wyrażenia. Jednakże ponieważ wyrażenie lambda przechwytuje `j` według odwołania, ponowne przypisanie `j` wpływa na wynik wyrażenia.

### <a name="code"></a>Kod

```cpp
// declaring_lambda_expressions2.cpp
// compile with: /EHsc /W4
#include <functional>
#include <iostream>

int main()
{
   using namespace std;

   int i = 3;
   int j = 5;

   // The following lambda expression captures i by value and
   // j by reference.
   function<int (void)> f = [i, &j] { return i + j; };

   // Change the values of i and j.
   i = 22;
   j = 44;

   // Call f and print its result.
   cout << f() << endl;
}
```

### <a name="output"></a>Dane wyjściowe

```Output
47
```

[[w tym artykule](#top)]

##  <a name="callingLambdaExpressions"></a> Wywoływanie wyrażeń Lambda

Wyrażenie lambda można wywołać natychmiast, jak pokazano w następnym fragmencie kodu programu. Drugi fragment kodu pokazuje, jak przekazać lambda jako argument do algorytmów standardowej biblioteki języka C++ takich jak `find_if`.

### <a name="example-1"></a>Przykład 1

Ten przykład deklaruje Wyrażenie lambda, które zwraca sumę dwóch liczb całkowitych i wywołuje wyrażenie bezpośrednio z argumentami `5` i `4`:

### <a name="code"></a>Kod

```cpp
// calling_lambda_expressions1.cpp
// compile with: /EHsc
#include <iostream>

int main()
{
   using namespace std;
   int n = [] (int x, int y) { return x + y; }(5, 4);
   cout << n << endl;
}
```

### <a name="output"></a>Dane wyjściowe

```Output
9
```

### <a name="example-2"></a>Przykład 2

Ten przykład przekazuje Wyrażenie lambda jako argument do `find_if` funkcji. Wyrażenie lambda zwraca **true** jeśli jego parametr jest liczbą parzystą.

### <a name="code"></a>Kod

```cpp
// calling_lambda_expressions2.cpp
// compile with: /EHsc /W4
#include <list>
#include <algorithm>
#include <iostream>

int main()
{
    using namespace std;

    // Create a list of integers with a few initial elements.
    list<int> numbers;
    numbers.push_back(13);
    numbers.push_back(17);
    numbers.push_back(42);
    numbers.push_back(46);
    numbers.push_back(99);

    // Use the find_if function and a lambda expression to find the
    // first even number in the list.
    const list<int>::const_iterator result =
        find_if(numbers.begin(), numbers.end(),[](int n) { return (n % 2) == 0; });

    // Print the result.
    if (result != numbers.end()) {
        cout << "The first even number in the list is " << *result << "." << endl;
    } else {
        cout << "The list contains no even numbers." << endl;
    }
}
```

### <a name="output"></a>Dane wyjściowe

```Output
The first even number in the list is 42.
```

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji na temat `find_if` funkcji, zobacz [find_if](../standard-library/algorithm-functions.md#find_if). Aby uzyskać więcej informacji na temat funkcji standardowej biblioteki języka C++, wykonujących Typowe algorytmy, zobacz [ \<algorytm >](../standard-library/algorithm.md).

[[w tym artykule](#top)]

##  <a name="nestingLambdaExpressions"></a> Zagnieżdżanie wyrażeń Lambda

### <a name="example"></a>Przykład

Można zagnieżdżać wyrażenia lambda wewnątrz siebie, jak pokazano w poniższym przykładzie. Wewnętrzne wyrażenie lambda mnoży swój argument przez 2 i zwraca wynik. Wyrażenie zewnętrzne lambda wywołuje wyrażenie wewnętrzne lambda z jego argumentem i dodaje do wyniku 3.

### <a name="code"></a>Kod

```cpp
// nesting_lambda_expressions.cpp
// compile with: /EHsc /W4
#include <iostream>

int main()
{
    using namespace std;

    // The following lambda expression contains a nested lambda
    // expression.
    int timestwoplusthree = [](int x) { return [](int y) { return y * 2; }(x) + 3; }(5);

    // Print the result.
    cout << timestwoplusthree << endl;
}
```

### <a name="output"></a>Dane wyjściowe

```Output
13
```

### <a name="remarks"></a>Uwagi

W tym przykładzie `[](int y) { return y * 2; }` jest zagnieżdżonym wyrażeniem lambda.

[[w tym artykule](#top)]

##  <a name="higherOrderLambdaExpressions"></a> Funkcje Lambda wyższego rzędu

### <a name="example"></a>Przykład

Wiele języków programowania wspiera koncepcję *funkcja wyższego rzędu.* Funkcja wyższego rzędu jest wyrażeniem lambda, które pobiera inne wyrażenie lambda jako argument, lub które zwraca wyrażenie lambda. Możesz użyć [funkcja](../standard-library/function-class.md) klasy, aby umożliwić wyrażeniu lambda C++ zachowują się jak funkcja wyższego rzędu. Poniższy przykład pokazuje Wyrażenie lambda, które zwraca `function` obiekt i Wyrażenie lambda, która przyjmuje `function` obiekt jako argumentu.

### <a name="code"></a>Kod

```cpp
// higher_order_lambda_expression.cpp
// compile with: /EHsc /W4
#include <iostream>
#include <functional>

int main()
{
    using namespace std;

    // The following code declares a lambda expression that returns
    // another lambda expression that adds two numbers.
    // The returned lambda expression captures parameter x by value.
    auto addtwointegers = [](int x) -> function<int(int)> {
        return [=](int y) { return x + y; };
    };

    // The following code declares a lambda expression that takes another
    // lambda expression as its argument.
    // The lambda expression applies the argument z to the function f
    // and multiplies by 2.
    auto higherorder = [](const function<int(int)>& f, int z) {
        return f(z) * 2;
    };

    // Call the lambda expression that is bound to higherorder.
    auto answer = higherorder(addtwointegers(7), 8);

    // Print the result, which is (7+8)*2.
    cout << answer << endl;
}
```

### <a name="output"></a>Dane wyjściowe

```Output
30
```

[[w tym artykule](#top)]

##  <a name="methodLambdaExpressions"></a> Użycie wyrażenia Lambda w funkcji

### <a name="example"></a>Przykład

Można używać wyrażeń lambda w treści funkcji. Wyrażenie lambda może uzyskać dostęp do dowolny członek funkcję lub dane, które mogą uzyskiwać dostęp do funkcji otaczającej. Można jawnie lub niejawnie przechwycić **to** wskaźnik, aby zapewnić dostęp do funkcji i składowych danych otaczającej klasy.
**Visual Studio 2017 w wersji 15.3 lub nowszej** (udostępniono [/STD: c ++ 17](../build/reference/std-specify-language-standard-version.md)): Przechwytywanie **to** przez wartość (`[*this]`) po lambda będzie używana w operacji asynchronicznej lub równoległego w przypadku, gdy kod może być wykonywany po oryginalny obiekt wykracza poza zakres.

Możesz użyć **to** wskaźnika niejawnie w funkcji, jak pokazano poniżej:

```cpp
// capture "this" by reference
void ApplyScale(const vector<int>& v) const
{
   for_each(v.begin(), v.end(),
      [this](int n) { cout << n * _scale << endl; });
}

// capture "this" by value (Visual Studio 2017 version 15.3 and later)
void ApplyScale2(const vector<int>& v) const
{
   for_each(v.begin(), v.end(),
      [*this](int n) { cout << n * _scale << endl; });
}
```

Istnieje również możliwość przechwytywania **to** wskaźnika niejawnie:

```cpp
void ApplyScale(const vector<int>& v) const
{
   for_each(v.begin(), v.end(),
      [=](int n) { cout << n * _scale << endl; });
}
```

W poniższym przykładzie przedstawiono `Scale` klasy, która hermetyzuje wartość skali.

```cpp
// function_lambda_expression.cpp
// compile with: /EHsc /W4
#include <algorithm>
#include <iostream>
#include <vector>

using namespace std;

class Scale
{
public:
    // The constructor.
    explicit Scale(int scale) : _scale(scale) {}

    // Prints the product of each element in a vector object
    // and the scale value to the console.
    void ApplyScale(const vector<int>& v) const
    {
        for_each(v.begin(), v.end(), [=](int n) { cout << n * _scale << endl; });
    }

private:
    int _scale;
};

int main()
{
    vector<int> values;
    values.push_back(1);
    values.push_back(2);
    values.push_back(3);
    values.push_back(4);

    // Create a Scale object that scales elements by 3 and apply
    // it to the vector object. Does not modify the vector.
    Scale s(3);
    s.ApplyScale(values);
}
```

### <a name="output"></a>Dane wyjściowe

```Output
3
6
9
12
```

### <a name="remarks"></a>Uwagi

`ApplyScale` Funkcja używa wyrażenia lambda do drukowania produktu wartości skali i każdego elementu w `vector` obiektu. Wyrażenie lambda niejawnie przechwytuje **to** dzięki czemu mogą uzyskać dostęp `_scale` elementu członkowskiego.

[[w tym artykule](#top)]

##  <a name="templateLambdaExpressions"></a> Użycie wyrażeń Lambda z szablonami

### <a name="example"></a>Przykład

Ponieważ wyrażenia lambda mają typ, można ich użyć z szablonami języka C++. W poniższym przykładzie przedstawiono `negate_all` i `print_all` funkcji. `negate_all` Funkcja ma zastosowanie jednoargumentowe **operator -** do każdego elementu w `vector` obiektu. `print_all` Funkcja drukuje każdy element w `vector` obiekcie do konsoli.

### <a name="code"></a>Kod

```cpp
// template_lambda_expression.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <iostream>

using namespace std;

// Negates each element in the vector object. Assumes signed data type.
template <typename T>
void negate_all(vector<T>& v)
{
    for_each(v.begin(), v.end(), [](T& n) { n = -n; });
}

// Prints to the console each element in the vector object.
template <typename T>
void print_all(const vector<T>& v)
{
    for_each(v.begin(), v.end(), [](const T& n) { cout << n << endl; });
}

int main()
{
    // Create a vector of signed integers with a few elements.
    vector<int> v;
    v.push_back(34);
    v.push_back(-43);
    v.push_back(56);

    print_all(v);
    negate_all(v);
    cout << "After negate_all():" << endl;
    print_all(v);
}
```

### <a name="output"></a>Dane wyjściowe

```Output
34
-43
56
After negate_all():
-34
43
-56
```

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji na temat szablonów języka C++, zobacz [szablony](../cpp/templates-cpp.md).

[[w tym artykule](#top)]

##  <a name="ehLambdaExpressions"></a> Obsługa wyjątków

### <a name="example"></a>Przykład

Treść wyrażenia lambda kieruje się regułami dla obsługi wyjątków strukturalnych (SEH) i obsługi wyjątków C++. Można obsługiwać zgłoszony wyjątek w ciele wyrażenia lambda lub odroczyć obsługę wyjątków do zasięgu otaczającego. W poniższym przykładzie użyto **for_each** funkcji i wyrażenia lambda do wypełnienia `vector` obiekt o wartości innej. Używa ona **spróbuj**/**catch** bloku do obsługi nieprawidłowego dostępu do pierwszego wektora.

### <a name="code"></a>Kod

```cpp
// eh_lambda_expression.cpp
// compile with: /EHsc /W4
#include <vector>
#include <algorithm>
#include <iostream>
using namespace std;

int main()
{
    // Create a vector that contains 3 elements.
    vector<int> elements(3);

    // Create another vector that contains index values.
    vector<int> indices(3);
    indices[0] = 0;
    indices[1] = -1; // This is not a valid subscript. It will trigger an exception.
    indices[2] = 2;

    // Use the values from the vector of index values to
    // fill the elements vector. This example uses a
    // try/catch block to handle invalid access to the
    // elements vector.
    try
    {
        for_each(indices.begin(), indices.end(), [&](int index) {
            elements.at(index) = index;
        });
    }
    catch (const out_of_range& e)
    {
        cerr << "Caught '" << e.what() << "'." << endl;
    };
}
```

### <a name="output"></a>Dane wyjściowe

```Output
Caught 'invalid vector<T> subscript'.
```

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji na temat obsługi wyjątków, zobacz [wyjątków](../cpp/exception-handling-in-visual-cpp.md).

[[w tym artykule](#top)]

##  <a name="managedLambdaExpressions"></a> Użycie wyrażeń Lambda z typy zarządzane (C + +/ CLI)

### <a name="example"></a>Przykład

Klauzula przechwytywania wyrażenia lambda nie może zawierać zmiennej, która ma typ zarządzany. Jednak do listy parametrów wyrażenia lambda można przekazać argument, który ma typ zarządzany. Poniższy przykład zawiera wyrażenie lambda, które przechwytuje lokalną zmienną niezarządzaną `ch` przez wartość i przełącza <xref:System.String?displayProperty=fullName> obiekt jako parametr.

### <a name="code"></a>Kod

```cpp
// managed_lambda_expression.cpp
// compile with: /clr
using namespace System;

int main()
{
    char ch = '!'; // a local unmanaged variable

    // The following lambda expression captures local variables
    // by value and takes a managed String object as its parameter.
    [=](String ^s) {
        Console::WriteLine(s + Convert::ToChar(ch));
    }("Hello");
}
```

### <a name="output"></a>Dane wyjściowe

```Output
Hello!
```

### <a name="remarks"></a>Uwagi

Można również używać wyrażeń lambda z biblioteką STL/CLR. Aby uzyskać więcej informacji, zobacz [odwołanie do biblioteki STL/CLR](../dotnet/stl-clr-library-reference.md).

> [!IMPORTANT]
>  Wyrażenia lambda nie są obsługiwane w tych jednostkach zarządzanych środowiska uruchomieniowego (języka wspólnego CLR) języka wspólnego: **klasy referencyjnej**, **ref struct**, **klasę wartości**, i **struktury wartości**.

[[w tym artykule](#top)]

## <a name="see-also"></a>Zobacz także

[Wyrażenia lambda](../cpp/lambda-expressions-in-cpp.md)<br/>
[Składnia wyrażenia lambda](../cpp/lambda-expression-syntax.md)<br/>
[auto](../cpp/auto-cpp.md)<br/>
[function, klasa](../standard-library/function-class.md)<br/>
[find_if](../standard-library/algorithm-functions.md#find_if)<br/>
[\<Algorytm >](../standard-library/algorithm.md)<br/>
[Wywołanie funkcji](../cpp/function-call-cpp.md)<br/>
[Szablony](../cpp/templates-cpp.md)<br/>
[Obsługa wyjątków](../cpp/exception-handling-in-visual-cpp.md)<br/>
[Dokumentacja biblioteki STL/CLR](../dotnet/stl-clr-library-reference.md)