---
title: Deklarator odwołania rvalue:&amp;&amp;
ms.date: 11/04/2016
f1_keywords:
- '&&'
helpviewer_keywords:
- '&& rvalue reference declarator'
ms.assetid: eab0ce3a-c5a3-4992-aa70-6a8ab1f7491d
ms.openlocfilehash: 65eec84447043b89ff94b77b7aed22b1b06f58e3
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87227104"
---
# <a name="rvalue-reference-declarator-ampamp"></a>Deklarator odwołania rvalue:&amp;&amp;

Przechowuje odwołanie do wyrażenia rvalue.

## <a name="syntax"></a>Składnia

```
type-id && cast-expression
```

## <a name="remarks"></a>Uwagi

Odwołania rvalue umożliwiają odróżnienie lvalue od rvalue. Odwołania lvalue i odwołania rvalue są składniowo i semantycznie podobne, ale są one zgodne z pewnymi różnymi regułami. Aby uzyskać więcej informacji na temat lvalues i rvalues, zobacz [lvalues i rvalues](../cpp/lvalues-and-rvalues-visual-cpp.md). Aby uzyskać więcej informacji o odwołaniach lvalue, zobacz [lvalue Reference deklarator: &](../cpp/lvalue-reference-declarator-amp.md).

W poniższych sekcjach opisano sposób, w jaki odwołania rvalue obsługują implementację *semantyki przenoszenia* i *doskonałe przekazywanie dalej*.

## <a name="move-semantics"></a>Przenoszenie semantyki

Odwołania rvalue obsługują implementację *semantyki przenoszenia*, co może znacząco zwiększyć wydajność aplikacji. Semantyka przenoszenia umożliwia pisanie kodu, który przesyła zasoby (na przykład dynamicznie przydzieloną pamięć) z jednego obiektu do drugiego. Semantyka przenoszenia działa, ponieważ umożliwia przesyłanie zasobów z obiektów tymczasowych, do których nie można się odwoływać w innym miejscu programu.

Aby zaimplementować semantykę przenoszenia, zazwyczaj udostępniamy *Konstruktor przenoszący* i opcjonalnie operator przypisania przenoszenia (**operator =**) do klasy. Operacje kopiowania i przypisywania, których źródła są rvalues, automatycznie wykorzystują semantykę przenoszenia. W przeciwieństwie do domyślnego konstruktora kopiującego, kompilator nie udostępnia domyślnego konstruktora przenoszenia. Aby uzyskać więcej informacji na temat pisania konstruktora przenoszącego i sposobu korzystania z niego w aplikacji, zobacz [przenoszenie konstruktorów i operatory przypisania przenoszenia (C++)](../cpp/move-constructors-and-move-assignment-operators-cpp.md).

Można również przeciążać zwykłe funkcje i operatory, aby skorzystać z semantyki przenoszenia. W programie Visual Studio 2010 wprowadzono semantykę przenoszenia do standardowej biblioteki języka C++. Na przykład `string` Klasa implementuje operacje, które wykonują semantykę przenoszenia. Rozważmy następujący przykład, który łączy kilka ciągów i drukuje wynik:

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

Przed wystąpieniem programu Visual Studio 2010 każde wywołanie **operatora +** przydzieli i zwróci nowy `string` obiekt tymczasowy (rvalue). **operator +** nie może dołączyć jednego ciągu do drugiego, ponieważ nie wie, czy ciągi źródłowe są lvalues lub rvalues. Jeśli ciągi źródłowe są zarówno lvalues, mogą być przywoływane w innym miejscu w programie i dlatego nie mogą być modyfikowane. Za pomocą odwołań rvalue, **operator +** można modyfikować, aby przyjmować rvalues, do których nie można się odwoływać w innym miejscu programu. W związku z tym **operator +** może teraz dołączyć jeden ciąg do innego. Może to znacznie zmniejszyć liczbę alokacji pamięci dynamicznej, które `string` musi wykonać Klasa. Aby uzyskać więcej informacji na temat `string` klasy, zobacz [basic_string Class](../standard-library/basic-string-class.md).

Semantyka przenoszenia również pomaga, gdy kompilator nie może używać optymalizacji wartości zwracanej (RVO) ani optymalizacji wartości zwracanej (NRVO). W takich przypadkach kompilator wywołuje konstruktor przenoszący, jeśli typ go definiuje.

Aby lepiej zrozumieć semantykę przenoszenia, rozważmy przykład wstawiania elementu do `vector` obiektu. W przypadku `vector` przekroczenia pojemności obiektu, `vector` obiekt musi ponownie przydzielić pamięć dla elementów, a następnie skopiować każdy element do innej lokalizacji pamięci, aby zwolnić miejsce dla wstawionego elementu. Gdy operacja wstawiania kopiuje element, tworzy nowy element, wywołuje konstruktora kopiującego, aby skopiować dane z poprzedniego elementu do nowego elementu, a następnie niszczy poprzedni element. Semantyka przenoszenia umożliwia przenoszenie obiektów bezpośrednio bez konieczności wykonywania kosztownych alokacji pamięci i operacji kopiowania.

Aby skorzystać z semantyki przenoszenia w `vector` przykładzie, można napisać Konstruktor przenoszący, aby przenieść dane z jednego obiektu do drugiego.

Aby uzyskać więcej informacji o wprowadzaniu semantyki przenoszenia do standardowej biblioteki C++ w programie Visual Studio 2010, zobacz [standardowa biblioteka języka c++](../standard-library/cpp-standard-library-reference.md).

## <a name="perfect-forwarding"></a>Doskonałe przekazywanie

Doskonałe przekazywanie ogranicza potrzebę przeciążonych funkcji i pomaga uniknąć problemów z przekazywaniem. *Problem z przekazywaniem* może wystąpić podczas pisania funkcji ogólnej, która pobiera odwołania jako parametry i przekazuje (lub *przesyła dalej*) te parametry do innej funkcji. Jeśli na przykład funkcja generyczna przyjmuje parametr typu `const T&` , wywoływana funkcja nie może modyfikować wartości tego parametru. Jeśli funkcja generyczna przyjmuje parametr typu `T&` , funkcja nie może być wywoływana za pomocą rvalue (na przykład obiektu tymczasowego lub literału liczb całkowitych).

Zwykle aby rozwiązać ten problem, należy zapewnić przeciążone wersje funkcji ogólnej, która przyjmuje oba `T&` `const T&` Parametry i dla każdego z nich. W efekcie liczba przeciążonych funkcji rośnie wykładniczo z liczbą parametrów. Odwołania rvalue umożliwiają pisanie jednej wersji funkcji, która akceptuje dowolne argumenty i przekazuje je do innej funkcji, tak jakby inna funkcja została wywołana bezpośrednio.

Rozważmy następujący przykład, który deklaruje cztery typy,,,, `W` `X` `Y` i `Z` . Konstruktor dla każdego typu przyjmuje inną kombinację **`const`** i **`const`** lvalue odwołania jako parametry.

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

Załóżmy, że chcesz napisać ogólną funkcję, która generuje obiekty. W poniższym przykładzie pokazano jeden ze sposobów zapisania tej funkcji:

```cpp
template <typename T, typename A1, typename A2>
T* factory(A1& a1, A2& a2)
{
   return new T(a1, a2);
}
```

W poniższym przykładzie pokazano prawidłowe wywołanie `factory` funkcji:

```cpp
int a = 4, b = 5;
W* pw = factory<W>(a, b);
```

Jednak Poniższy przykład nie zawiera prawidłowego wywołania `factory` funkcji, ponieważ `factory` Pobiera odwołania lvalue, które są modyfikowalne jako parametry, ale są wywoływane za pomocą rvalues:

```cpp
Z* pz = factory<Z>(2, 2);
```

Zwykle aby rozwiązać ten problem, należy utworzyć przeciążoną wersję `factory` funkcji dla każdej kombinacji `A&` `const A&` parametrów i. Odwołania rvalue umożliwiają pisanie jednej wersji `factory` funkcji, jak pokazano w następującym przykładzie:

```cpp
template <typename T, typename A1, typename A2>
T* factory(A1&& a1, A2&& a2)
{
   return new T(std::forward<A1>(a1), std::forward<A2>(a2));
}
```

W tym przykładzie używa się odwołań rvalue jako parametrów `factory` funkcji. Celem funkcji [std:: Forward](../standard-library/utility-functions.md#forward) jest przekazanie parametrów funkcji fabryki do konstruktora klasy szablonu.

Poniższy przykład pokazuje funkcję, `main` która używa poprawionej `factory` funkcji do tworzenia wystąpień `W` `X` klas,, `Y` , i `Z` . Poprawiona `factory` Funkcja przekazuje swoje parametry (lvalues lub rvalues) do odpowiedniego konstruktora klasy.

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

## <a name="additional-properties-of-rvalue-references"></a>Dodatkowe właściwości odwołań rvalue

**Można przeciążać funkcję, aby przyjmować odwołanie lvalue i odwołanie rvalue.**

Przeciążanie funkcji, aby pobrać **`const`** odwołanie lvalue lub odwołanie do rvalue, można napisać kod odróżniający między niemodyfikowalnymi obiektami (lvalues) i modyfikowalnymi wartościami tymczasowymi (rvalues). Można przekazać obiekt do funkcji, która przyjmuje odwołanie rvalue, chyba że obiekt jest oznaczony jako **`const`** . Poniższy przykład pokazuje funkcję `f` , która jest przeciążona, aby pobrać odwołanie lvalue i odwołanie rvalue. `main`Funkcja wywołuje `f` zarówno lvalues, jak i rvalue.

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

W tym przykładzie pierwsze wywołanie do `f` przekazuje zmienną lokalną (lvalue) jako argument. Drugie wywołanie `f` przekazuje tymczasowy obiekt jako argument. Ponieważ obiekt tymczasowy nie może być przywoływany w innym miejscu w programie, wywołanie jest powiązane z przeciążoną wersją, `f` która przyjmuje odwołanie rvalue, które jest bezpłatne do modyfikacji obiektu.

**Kompilator traktuje nazwane odwołanie rvalue jako lvalue i nienazwane odwołanie rvalue jako rvalue.**

Gdy piszesz funkcję, która przyjmuje jako parametr odwołanie rvalue, ten parametr jest traktowany jako lvalue w treści funkcji. Kompilator traktuje nazwane odwołanie rvalue jako lvalue, ponieważ obiekt nazwany może być przywoływany przez kilka części programu; może być niebezpieczne dla wielu części programu, aby modyfikować lub usuwać zasoby z tego obiektu. Na przykład jeśli wiele części programu próbuje przenieść zasoby z tego samego obiektu, tylko pierwsza część pomyślnie przeniesie zasób.

Poniższy przykład pokazuje funkcję `g` , która jest przeciążona, aby pobrać odwołanie lvalue i odwołanie rvalue. Funkcja `f` przyjmuje odwołanie rvalue jako parametr (nazwane odwołanie rvalue) i zwraca odwołanie rvalue (nienazwane odwołanie rvalue). W wywołaniu `g` z, Metoda `f` rozpoznawania przeciążenia wybiera wersję `g` , która pobiera odwołanie lvalue, ponieważ treść `f` traktuje swój parametr jako lvalue. W wywołaniu `g` od `main` , rozpoznawanie przeciążenia wybiera wersję `g` , która pobiera odwołanie rvalue, ponieważ `f` zwraca odwołanie rvalue.

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
   return move(block);
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

W tym przykładzie `main` Funkcja przekazuje rvalue do `f` . Treść `f` traktuje nazwany parametr jako lvalue. Wywołanie z `f` do `g` powiązania parametru z odwołaniem lvalue (pierwszą przeciążoną wersją `g` ).

- **Można rzutować lvalue na odwołanie rvalue.**

Standardowa biblioteka języka C++ [std:: Move](../standard-library/utility-functions.md#move) funkcja umożliwia konwertowanie obiektu na odwołanie rvalue do tego obiektu. Alternatywnie można użyć **`static_cast`** słowa kluczowego do rzutowania lvalue na odwołanie rvalue, jak pokazano w następującym przykładzie:

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

**Szablony funkcji ustalają ich typy argumentów szablonu, a następnie używają reguł zwijania odwołań.**

Często należy napisać szablon funkcji, który przekazuje (lub *przesyła dalej*) jego parametry do innej funkcji. Ważne jest, aby zrozumieć, w jaki sposób Metoda odejmowania typu szablonu działa dla szablonów funkcji, które pobierają odwołania rvalue.

Jeśli argument funkcji jest rvalue, kompilator wywnioskuje argument jako odwołanie rvalue. Na przykład, Jeśli przekażesz odwołanie rvalue do obiektu typu `X` do funkcji szablonu, która przyjmuje typ `T&&` jako parametr, odliczanie argumentu szablonu zostanie określone jako `T` `X` . W związku z tym parametr ma typ `X&&` . Jeśli argument funkcji jest lvalue lub **`const`** lvalue, kompilator określa jego typ jako odwołanie lvalue lub **`const`** lvalue do tego typu.

W poniższym przykładzie zadeklarowano jeden szablon struktury, a następnie jest on wyspecjalizowany dla różnych typów referencyjnych. `print_type_and_value`Funkcja przyjmuje jako parametr odwołanie rvalue i przekazuje go do odpowiedniej wyspecjalizowanej wersji `S::print` metody. `main`Funkcja pokazuje różne sposoby wywoływania `S::print` metody.

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

Aby rozwiązać każde wywołanie `print_type_and_value` funkcji, kompilator najpierw wykonuje potrącenie argumentu szablonu. Następnie kompilator stosuje reguły zwijające odwołania, gdy zastępuje argumenty szablonu wywnioskowanych dla typów parametrów. Na przykład przekazanie zmiennej lokalnej `s1` do `print_type_and_value` funkcji powoduje, że kompilator wygenerował następującą sygnaturę funkcji:

```cpp
print_type_and_value<string&>(string& && t)
```

Kompilator używa reguł zwijania odwołania, aby zmniejszyć sygnaturę do następujących:

```cpp
print_type_and_value<string&>(string& t)
```

Ta wersja `print_type_and_value` funkcji następnie przekazuje jej parametr do odpowiedniej wersji wyspecjalizowanej `S::print` metody.

Poniższa tabela podsumowuje reguły zwijania odwołań dla typu argumentu szablonu:

|||
|-|-|
|Typ rozwinięty|Typ zwinięty|
|`T& &`|`T&`|
|`T& &&`|`T&`|
|`T&& &`|`T&`|
|`T&& &&`|`T&&`|

Potrącenie argumentu szablonu jest ważnym elementem implementującym doskonałe przekazywanie. Sekcja doskonałe przekazywanie, która jest przedstawiona wcześniej w tym temacie, opisuje doskonałe przekazywanie bardziej szczegółowo.

## <a name="summary"></a>Podsumowanie

Rvalue odwołuje się do odróżnia lvalues od rvalues. Mogą one pomóc zwiększyć wydajność aplikacji, eliminując konieczność niepotrzebnych alokacji pamięci i operacji kopiowania. Umożliwiają one także pisanie jednej wersji funkcji, która akceptuje dowolne argumenty i przekazuje je do innej funkcji, tak jakby inna funkcja została wywołana bezpośrednio.

## <a name="see-also"></a>Zobacz także

[Wyrażenia z operatorami jednoargumentowymi](../cpp/expressions-with-unary-operators.md)<br/>
[Deklarator odwołania do wartości L: &](../cpp/lvalue-reference-declarator-amp.md)<br/>
[Lvalues i rvalues](../cpp/lvalues-and-rvalues-visual-cpp.md)<br/>
[Konstruktory przenoszące i przenoszące operatory przypisania (C++)](../cpp/move-constructors-and-move-assignment-operators-cpp.md)<br/>
[Standardowa biblioteka języka C++](../standard-library/cpp-standard-library-reference.md)
