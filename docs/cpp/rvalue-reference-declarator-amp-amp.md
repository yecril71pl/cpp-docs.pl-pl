---
title: 'Deklarator odwołania do wartości: &amp; &amp; | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- '&&'
dev_langs:
- C++
helpviewer_keywords:
- '&& rvalue reference declarator'
ms.assetid: eab0ce3a-c5a3-4992-aa70-6a8ab1f7491d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 64a42a65e112930767aa27f94612d06b7fb2d34a
ms.sourcegitcommit: a738519aa491a493a8f213971354356c0e6a5f3a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/05/2018
ms.locfileid: "48821637"
---
# <a name="rvalue-reference-declarator-ampamp"></a>Deklarator odwołania do wartości: &amp;&amp;

Zawiera odwołanie do wyrażenia rvalue.

## <a name="syntax"></a>Składnia

```
type-id && cast-expression
```

## <a name="remarks"></a>Uwagi

Odwołania Rvalue umożliwiają odróżnienie wartości lvalue od rvalue. Odwołania Lvalue i odwołania rvalue są składniowo i semantycznie podobne, ale mają nieco inne reguły. Aby uzyskać więcej informacji na temat lvalues i rvalues, zobacz [Lvalues i Rvalues](../cpp/lvalues-and-rvalues-visual-cpp.md). Aby uzyskać więcej informacji na temat odwołań do l-wartości, zobacz [l-wartości Reference Declarator: &](../cpp/lvalue-reference-declarator-amp.md).

W poniższych sekcjach opisano, jak odwołania rvalue wspierają implementację *semantyki przenoszenia* i *doskonała przekazywania*.

## <a name="move-semantics"></a>Semantyka przenoszenia

Odwołania Rvalue wspierają implementację *semantyki przenoszenia*, co może znacząco zwiększyć wydajność aplikacji. Semantykę przenoszenia umożliwia napisanie kodu, który przenosi zasoby (takie jak pamięć przydzielana dynamicznie) z jednego obiektu do innego. Przenieś semantyki działa, ponieważ umożliwia zasobów z tymczasowych obiektów, których nie można odwoływać się gdzie indziej w programie.

Aby zaimplementować semantykę przenoszenia, zazwyczaj podajesz *Konstruktor przenoszący,* i opcjonalnie operator przypisania przenoszenia (**operator =**), do swojej klasy. Kopiuj i przypisz operacje, których źródłami są r-wartości, a następnie automatycznie skorzystaj z semantyki przeniesienia. W przeciwieństwie do domyślnego konstruktora kopii kompilator nie udostępnia domyślnego konstruktora przenoszącego. Aby uzyskać więcej informacji na temat sposobu pisania konstruktora przenoszącego i jak z niej korzystać w aplikacji, zobacz [konstruktory przenoszenia i operatory przenoszenia przypisania (C++)](../cpp/move-constructors-and-move-assignment-operators-cpp.md).

Możesz także przeciążać zwykłe funkcje i operatory, aby skorzystać z semantyki przenoszenia. Visual C++ 2010 wprowadza semantykę ruchu do standardowej biblioteki języka C++. Na przykład `string` klasa implementuje operacje wykonujące semantykę przenoszenia. Rozważmy następujący przykład, który łączy kilka ciągów i wypisuje wynik:

```cpp
// string_concatenation.cpp
// compile with: /EHsc
#include <iostream>
#include <string>
using namespace std;

int main()
{
   string s = string("h") + "e" + "ll" + "o";
   cout << s << endl;
}
```

Przed Visual C++ 2010, każdy wywołanie **operator +** przydzielało i zwracało nowy tymczasowy `string` obiektu (r-wartości). **operator +** nie może dołączyć jednego ciągu do drugiego, ponieważ nie wie, czy ciągi źródłowe są wartościami lvalue czy rvalue. Jeżeli ciągi źródłowe są oba l-wartością, może się odwoływać się gdzie indziej w programie i dlatego nie mogą zostać zmodyfikowane. Za pomocą odwołania rvalue **operator +** może zostać zmodyfikowany do r-wartości, której nie można odwoływać się gdzie indziej w programie. W związku z tym **operator +** mogą teraz łączyć jeden ciąg do innego. Może to znacznie zmniejszyć liczbę alokacji pamięci dynamicznej, `string` musi wykonać klasa. Aby uzyskać więcej informacji na temat `string` klasy, zobacz [basic_string — klasa](../standard-library/basic-string-class.md).

Semantyka przenoszenia pomaga również w przypadku, gdy kompilator nie można używać optymalizacji zwracają wartość (RVO) ani o nazwie zwracają wartość optymalizacji (NRVO). W takich przypadkach kompilator wywołuje konstruktora przenoszącego, jeśli typ Określa go. Aby uzyskać więcej informacji o optymalizacji nazwanej zwracanej wartości, zobacz [optymalizacji nazwanej zwracanej wartości w programie Visual C++ 2005](https://msdn.microsoft.com/library/ms364057.aspx).

Aby lepiej zrozumieć semantykę przenoszenia, rozważ przykład wstawiania elementu do `vector` obiektu. Jeśli pojemność `vector` zostanie przekroczona `vector` obiektu musi ponownie przydzielić pamięci dla swoich elementów, a następnie skopiować każdy element do innej lokalizacji pamięci, aby zwolnić miejsce dla wstawionego elementu. Gdy operacja wstawiania kopiuje element, tworzy nowy element, wywołuje konstruktor Kopiuj, aby skopiować dane z poprzedniego elementu do nowego elementu i następnie niszczy poprzedni element. Semantyka przenoszenia umożliwia przenoszenie obiektów bezpośrednio, bez konieczności wykonywania alokacji pamięci kosztowne i operacji kopiowania.

Aby skorzystać z semantyki przenoszenia w `vector` przykład można napisać Konstruktor przenoszący, aby przenieść dane z jednego obiektu do drugiego.

Aby uzyskać więcej informacji na temat wprowadzenia semantyki przenoszenia do biblioteki standardowej języka C++ w programie Visual C++ 2010, zobacz [standardowej biblioteki języka C++](../standard-library/cpp-standard-library-reference.md).

## <a name="perfect-forwarding"></a>Doskonałe przekazywanie do przodu

Perfekcyjne przekazywanie ogranicza potrzebę przeciążania funkcji i pomaga uniknąć problemów z przesyłaniem dalej. *Problem z przesyłaniem* może wystąpić, gdy możesz napisać funkcję ogólną, która przyjmuje odniesienia parametrów i przekazuje (lub *przekazuje*) te parametry do innej funkcji. Na przykład, jeśli funkcja ogólna przyjmuje parametr typu `const T&`, a następnie wywoływana funkcja nie może modyfikować wartości tego parametru. Jeśli funkcja ogólna przyjmuje parametr typu `T&`, a następnie funkcja nie może być wywoływana przy użyciu rvalue (takie jak tymczasowy obiekt lub literał liczby całkowitej).

Zwykle Aby rozwiązać ten problem, należy podać przeciążone wersje funkcji ogólnej, które przyjmują typy `T&` i `const T&` dla każdego z jego parametrów. Co w efekcie wiele funkcji zastąpionej wykładniczo zwiększa się liczba parametrów. Odwołania Rvalue umożliwiają pisanie jednej wersji funkcji, która przyjmuje argumenty dowolne i przekazuje je do innej funkcji, tak jakby innych funkcji jakby została ona bezpośrednio wywołana.

Rozważmy następujący przykład, w którym zadeklarowano cztery typy `W`, `X`, `Y`, i `Z`. Konstruktor dla każdego typu ma inną kombinację **const** i innych niż-**const** odwołania lvalue jako jego parametry.

```cpp
struct W
{
   W(int&, int&) {}
};

struct X
{
   X(const int&, int&) {}
};

struct Y
{
   Y(int&, const int&) {}
};

struct Z
{
   Z(const int&, const int&) {}
};
```

Załóżmy, że chcesz napisać funkcję ogólną, która generuje obiekty. Jednym ze sposobów, aby zapisać tę funkcję można znaleźć w poniższym przykładzie:

```cpp
template <typename T, typename A1, typename A2>
T* factory(A1& a1, A2& a2)
{
   return new T(a1, a2);
}
```

Poniższy przykład ilustruje poprawne wywoływanie do `factory` funkcji:

```cpp
int a = 4, b = 5;
W* pw = factory<W>(a, b);
```

Natomiast poniższy przykład nie zawiera prawidłowego wywołania `factory` działać, ponieważ `factory` ma odwołania lvalue, które można modyfikować jako jej parametry, ale jest wywoływana za pomocą wartości rvalue:

```cpp
Z* pz = factory<Z>(2, 2);
```

Zwykle Aby rozwiązać ten problem, należy utworzyć przeciążoną wersję `factory` funkcji dla każdej kombinacji `A&` i `const A&` parametrów. Odwołania Rvalue umożliwiają pisanie jednej wersji `factory` funkcji, jak pokazano w poniższym przykładzie:

```cpp
template <typename T, typename A1, typename A2>
T* factory(A1&& a1, A2&& a2)
{
   return new T(std::forward<A1>(a1), std::forward<A2>(a2));
}
```

Ten przykład używa odwołań rvalue jako parametrów dla `factory` funkcji. Celem [std::forward](../standard-library/utility-functions.md#forward) funkcja jest przekazywanie parametrów funkcji fabryki do konstruktora klasy szablonu.

W poniższym przykładzie przedstawiono `main` funkcja, która używa zweryfikowanej `factory` funkcji, aby utworzyć wystąpienia elementu `W`, `X`, `Y`, i `Z` klasy. Zweryfikowana `factory` funkcja przekazuje parametry (lvalues lub rvalues) do konstruktora właściwej klasy.

```cpp
int main()
{
   int a = 4, b = 5;
   W* pw = factory<W>(a, b);
   X* px = factory<X>(2, b);
   Y* py = factory<Y>(a, 2);
   Z* pz = factory<Z>(2, 2);

   delete pw;
   delete px;
   delete py;
   delete pz;
}
```

## <a name="additional-properties-of-rvalue-references"></a>Dodatkowe właściwości odwołań r-wartości

**Możesz doprowadzić do przeciążenia funkcji aby odwołanie lvalue i odwołanie rvalue.**

Przy przeciążeniu funkcji w celu **const** odwołanie lvalue lub odwołaniem rvalue, można napisać kod, który rozróżnia obiekty uniemożliwiającym (l-wartością) i wartości modyfikowalne tymczasowo (r-wartości). Obiekt można przekazać do funkcji, która przyjmuje odwołanie rvalue, chyba że obiekt jest oznaczony jako **const**. Poniższy przykład ukazuje funkcję `f`, która jest przeciążona, aby pobrać odwołanie lvalue i odwołanie rvalue. `main` Wywołaniach funkcji `f` z lvalues i rvalue.

```cpp
// reference-overload.cpp
// Compile with: /EHsc
#include <iostream>
using namespace std;

// A class that contains a memory resource.
class MemoryBlock
{
   // TODO: Add resources for the class here.
};

void f(const MemoryBlock&)
{
   cout << "In f(const MemoryBlock&). This version cannot modify the parameter." << endl;
}

void f(MemoryBlock&&)
{
   cout << "In f(MemoryBlock&&). This version can modify the parameter." << endl;
}

int main()
{
   MemoryBlock block;
   f(block);
   f(MemoryBlock());
}
```

Ten przykład generuje następujące wyniki:

```Output
In f(const MemoryBlock&). This version cannot modify the parameter.
In f(MemoryBlock&&). This version can modify the parameter.
```

W tym przykładzie pierwsze wywołanie do `f` przekazuje zmienną lokalną (lvalue) jako argument. Drugie wywołanie `f` przekazuje tymczasowy obiekt jako argument. Ponieważ tymczasowego obiektu nie można odwoływać się gdzie indziej w programie, wywołanie jest powiązana z przeciążoną wersją `f` która przyjmuje odwołanie rvalue, która jest bezpłatna może modyfikować dany obiekt.

**Kompilator traktuje odwołanie nazwane rvalue jako lvalue i odwołanie nienazwane rvalue jako rvalue.**

Podczas pisania funkcji, która przyjmuje odwołanie rvalue za parametr, ten parametr jest traktowany jako lvalue w treści funkcji. Kompilator traktuje odwołanie nazwane rvalue jako lvalue, ponieważ nazwany obiekt mogą być przywoływane przez kilka części programu; byłoby niebezpieczne zezwolić wielu częściom programu na modyfikowanie lub usuwanie zasobów z tego obiektu. Na przykład jeśli wiele części programu próbuje przenieść zasoby z tego samego obiektu, tylko pierwsza część pomyślnie spowoduje przeniesienie zasobu.

Poniższy przykład ukazuje funkcję `g`, która jest przeciążona, aby pobrać odwołanie lvalue i odwołanie rvalue. Funkcja `f` przyjmuje odwołanie rvalue za parametr (nazwane odwołanie rvalue) i zwraca odwołanie rvalue (nienazwane odwołanie rvalue). W wywołaniu `g` z `f`, funkcja rozpoznawania przeciążeń wybiera wersję `g` pobiera odwołanie lvalue, ponieważ treść `f` traktuje jego parametr jako lvalue. W wywołaniu `g` z `main`, funkcja rozpoznawania przeciążeń wybiera wersję `g` przyjmuje odwołanie rvalue, ponieważ `f` zwraca odwołanie rvalue.

```cpp
// named-reference.cpp
// Compile with: /EHsc
#include <iostream>
using namespace std;

// A class that contains a memory resource.
class MemoryBlock
{
   // TODO: Add resources for the class here.
};

void g(const MemoryBlock&)
{
   cout << "In g(const MemoryBlock&)." << endl;
}

void g(MemoryBlock&&)
{
   cout << "In g(MemoryBlock&&)." << endl;
}

MemoryBlock&& f(MemoryBlock&& block)
{
   g(block);
   return block;
}

int main()
{
   g(f(MemoryBlock()));
}
```

Ten przykład generuje następujące wyniki:

```cpp
In g(const MemoryBlock&).
In g(MemoryBlock&&).
```

W tym przykładzie `main` funkcja przekazuje wartości rvalue do `f`. Treść `f` traktuje jego nazwany parametr jako lvalue. Wywołanie funkcji z `f` do `g` powiązuje parametr z odwołaniem lvalue (pierwsza przeciążona wersja `g`).

- **Można rzutować lvalue na odwołanie rvalue.**

Standardowa biblioteka C++ [std::move](../standard-library/utility-functions.md#move) funkcja umożliwia konwertowanie obiektu do odwołania rvalue do tego obiektu. Alternatywnie, można użyć **static_cast** — słowo kluczowe, można rzutować lvalue na odwołanie rvalue, jak pokazano w poniższym przykładzie:

```cpp
// cast-reference.cpp
// Compile with: /EHsc
#include <iostream>
using namespace std;

// A class that contains a memory resource.
class MemoryBlock
{
   // TODO: Add resources for the class here.
};

void g(const MemoryBlock&)
{
   cout << "In g(const MemoryBlock&)." << endl;
}

void g(MemoryBlock&&)
{
   cout << "In g(MemoryBlock&&)." << endl;
}

int main()
{
   MemoryBlock block;
   g(block);
   g(static_cast<MemoryBlock&&>(block));
}
```

Ten przykład generuje następujące wyniki:

```cpp
In g(const MemoryBlock&).
In g(MemoryBlock&&).
```

**Szablony funkcji wywnioskować swoje typy argumentów szablonu, a następnie używają reguł zwijanie odwołań.**

To powszechne zapisać szablon funkcji, który przekazuje (lub *przekazuje*) jej parametry do innej funkcji. Należy zrozumieć, jak działa dedukcja typu szablonu dla szablonów funkcji, które przyjmują odwołania rvalue.

Jeśli argument funkcji jest wartość rvalue, kompilator wywnioskowuje, że argument jest odwołaniem rvalue. Na przykład w przypadku przekazania odwołania rvalue do obiektu typu `X` do funkcji szablonu, która przyjmuje typ `T&&` jako parametr, określi odliczanie argumentu szablon `T` jako `X`. W związku z tym, parametr ma typ `X&&`. Jeśli argument funkcji jest wartością lvalue lub **const** l-wartości, kompilator wywnioskowuje, że jej typ jest odwołaniem lvalue lub **const** odwołanie l-wartością tego typu.

Poniższy przykład deklaruje jeden szablon struktury, a następnie specjalizuje go dla różnych typów odwołań. `print_type_and_value` Funkcja przyjmuje odwołanie rvalue za parametr i przekazuje go do odpowiedniej wersji specjalistycznej metody `S::print` metody. `main` Funkcji pokazuje różne sposoby wywoływania `S::print` metody.

```cpp
// template-type-deduction.cpp
// Compile with: /EHsc
#include <iostream>
#include <string>
using namespace std;

template<typename T> struct S;

// The following structures specialize S by
// lvalue reference (T&), const lvalue reference (const T&),
// rvalue reference (T&&), and const rvalue reference (const T&&).
// Each structure provides a print method that prints the type of
// the structure and its parameter.

template<typename T> struct S<T&> {
   static void print(T& t)
   {
      cout << "print<T&>: " << t << endl;
   }
};

template<typename T> struct S<const T&> {
   static void print(const T& t)
   {
      cout << "print<const T&>: " << t << endl;
   }
};

template<typename T> struct S<T&&> {
   static void print(T&& t)
   {
      cout << "print<T&&>: " << t << endl;
   }
};

template<typename T> struct S<const T&&> {
   static void print(const T&& t)
   {
      cout << "print<const T&&>: " << t << endl;
   }
};

// This function forwards its parameter to a specialized
// version of the S type.
template <typename T> void print_type_and_value(T&& t)
{
   S<T&&>::print(std::forward<T>(t));
}

// This function returns the constant string "fourth".
const string fourth() { return string("fourth"); }

int main()
{
   // The following call resolves to:
   // print_type_and_value<string&>(string& && t)
   // Which collapses to:
   // print_type_and_value<string&>(string& t)
   string s1("first");
   print_type_and_value(s1);

   // The following call resolves to:
   // print_type_and_value<const string&>(const string& && t)
   // Which collapses to:
   // print_type_and_value<const string&>(const string& t)
   const string s2("second");
   print_type_and_value(s2);

   // The following call resolves to:
   // print_type_and_value<string&&>(string&& t)
   print_type_and_value(string("third"));

   // The following call resolves to:
   // print_type_and_value<const string&&>(const string&& t)
   print_type_and_value(fourth());
}
```

Ten przykład generuje następujące wyniki:

```cpp
print<T&>: first
print<const T&>: second
print<T&&>: third
print<const T&&>: fourth
```

Aby rozwiązać każde wywołanie `print_type_and_value` funkcji, kompilator wykonuje najpierw odliczanie argumentu szablon. Następnie kompilator stosuje odniesienie zwijania reguł, gdy zastępuje wywnioskowane argumenty szablonu dla typów parametrów. Na przykład przekazanie zmiennej lokalnej `s1` do `print_type_and_value` funkcji powoduje, że kompilator generuje następujący podpis funkcji:

```cpp
print_type_and_value<string&>(string& && t)
```

Kompilator używa odniesienie zwijania reguł do zmniejszania podpisu do następujących:

```cpp
print_type_and_value<string&>(string& t)
```

Ta wersja `print_type_and_value` funkcja następnie przesyła parametr do poprawnej wersji specjalistycznej wersji programu `S::print` metody.

Poniższa tabela podsumowuje zwijane zasady odwołania dla wyznaczenia typu argumentu szablonu:

|||
|-|-|
|Typ rozszerzony|Typ zwinięty|
|`T& &`|`T&`|
|`T& &&`|`T&`|
|`T&& &`|`T&`|
|`T&& &&`|`T&&`|

Odliczanie argumentu szablon jest istotnym elementem wdrażania przekazywania. Sekcja doskonałe przekazywanie dalej, przedstawiona wcześniej w tym temacie opisuje Perfekcyjne przekazywanie bardziej szczegółowo.

## <a name="summary"></a>Podsumowanie

Odwołania Rvalue odróżniają wartości lvalues od rvalues. Mogą one pomóc Ci zwiększyć wydajność aplikacji poprzez wyeliminowanie potrzeby przydzielania niepotrzebnych alokacji pamięci i operacji kopiowania. Umożliwiają one również pisanie jednej wersji funkcji, która przyjmuje argumenty dowolne i przekazuje je do innej funkcji, tak jakby innych funkcji jakby została ona bezpośrednio wywołana.

## <a name="see-also"></a>Zobacz także

[Wyrażenia z operatorami jednoargumentowymi](../cpp/expressions-with-unary-operators.md)<br/>
[Deklarator odwołania do wartości L: &](../cpp/lvalue-reference-declarator-amp.md)<br/>
[Lvalues i Rvalues](../cpp/lvalues-and-rvalues-visual-cpp.md)<br/>
[Konstruktory przenoszące i przenoszące operatory przypisania (C++)](../cpp/move-constructors-and-move-assignment-operators-cpp.md)<br/>
[Standardowa biblioteka C++](../standard-library/cpp-standard-library-reference.md)
