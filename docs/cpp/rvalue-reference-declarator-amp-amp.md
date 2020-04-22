---
title: Rvalue Reference Declarator:&amp;&amp;
ms.date: 11/04/2016
f1_keywords:
- '&&'
helpviewer_keywords:
- '&& rvalue reference declarator'
ms.assetid: eab0ce3a-c5a3-4992-aa70-6a8ab1f7491d
ms.openlocfilehash: 53729cca7c259bc2d3b792ddc3509d5fc3bd255a
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "81749828"
---
# <a name="rvalue-reference-declarator-ampamp"></a>Rvalue Reference Declarator:&amp;&amp;

Zawiera odwołanie do wyrażenia rvalue.

## <a name="syntax"></a>Składnia

```
type-id && cast-expression
```

## <a name="remarks"></a>Uwagi

Odwołania do wartości Rwalue umożliwiają odróżnienie wartości lvalue od wartości r. Odwołania lvalue i odwołania do wartości rvalue są syntaktycznie i semantycznie podobne, ale są zgodne z nieco innymi regułami. Aby uzyskać więcej informacji na temat wartości lvalues i rvalues, zobacz [Lvalues i Rvalues](../cpp/lvalues-and-rvalues-visual-cpp.md). Aby uzyskać więcej informacji na temat odwołań do lvalue, zobacz [Lvalue Reference Declarator: &](../cpp/lvalue-reference-declarator-amp.md).

W poniższych sekcjach opisano, w jaki sposób odwołania do wartości rwalue obsługują implementację *semantyki przenoszenia* i *doskonałego przekazywania*.

## <a name="move-semantics"></a>Przenoszenie semantyki

Odwołania do rvalue obsługują implementację *semantyki przenoszenia,* co może znacznie zwiększyć wydajność aplikacji. Przenieś semantyka umożliwia pisanie kodu, który przenosi zasoby (takie jak dynamicznie przydzielona pamięć) z jednego obiektu do drugiego. Przenieś semantyka działa, ponieważ umożliwia przenoszenie zasobów z obiektów tymczasowych, do których nie można odwoływać się w innym miejscu programu.

Aby zaimplementować przenieść semantyki, zazwyczaj należy podać *konstruktora przenoszenia* i opcjonalnie przenieść przypisania operatora **(operator=**), do klasy. Operacje kopiowania i przypisywania, których źródła są wartościami r, automatycznie korzystają z semantyki przenoszenia. W przeciwieństwie do domyślnego konstruktora kopii kompilator nie zapewnia domyślnego konstruktora przenoszenia. Aby uzyskać więcej informacji na temat sposobu pisania konstruktora przenoszenia i używania go w aplikacji, zobacz [Przenoszenie konstruktorów i przenoszenie operatorów przydziałów (C++)](../cpp/move-constructors-and-move-assignment-operators-cpp.md).

Można również przeciążyć zwykłe funkcje i operatory, aby skorzystać z semantyki przenoszenia. Visual Studio 2010 wprowadza semantyki przenoszenia do biblioteki standardowej języka C++. Na przykład `string` klasa implementuje operacje, które wykonują semantykę przenoszenia. Rozważmy następujący przykład, który łączy kilka ciągów i drukuje wynik:

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

Przed Visual Studio 2010, każde wywołanie **operator** + `string` przydziela i zwraca nowy obiekt tymczasowy (rvalue). **operator+** nie może dołączyć jednego ciągu do drugiego, ponieważ nie wie, czy ciągi źródłowe są wartościami lvalues lub rvalues. Jeśli ciągi źródłowe są zarówno lvalues, mogą być odwoływane w innym miejscu w programie i dlatego nie mogą być modyfikowane. Za pomocą rvalue odwołania, **operator +** mogą być modyfikowane do podjęcia rvalues, które nie mogą być odwoływane w innym miejscu w programie. W związku z tym **operator +** można teraz dołączyć jeden ciąg do innego. Może to znacznie zmniejszyć liczbę alokacji pamięci `string` dynamicznej, które klasa musi wykonać. Aby uzyskać więcej `string` informacji na temat klasy, zobacz [basic_string Class](../standard-library/basic-string-class.md).

Semantyka przenoszenia pomaga również, gdy kompilator nie może użyć optymalizacji wartości zwracanej (RVO) lub optymalizacji nazwanych wartości zwracanych (NRVO). W takich przypadkach kompilator wywołuje konstruktora przenoszenia, jeśli typ go definiuje.

Aby lepiej zrozumieć semantykę przenoszenia, należy wziąć `vector` pod uwagę przykład wstawiania elementu do obiektu. Jeśli pojemność `vector` obiektu zostanie przekroczona, `vector` obiekt musi ponownie przydzielić pamięć dla swoich elementów, a następnie skopiować każdy element do innej lokalizacji pamięci, aby zrobić miejsce dla wstawionego elementu. Gdy operacja wstawiania kopiuje element, tworzy nowy element, wywołuje konstruktora kopiowania, aby skopiować dane z poprzedniego elementu do nowego elementu, a następnie niszczy poprzedni element. Przenieś semantyka umożliwia bezpośrednie przenoszenie obiektów bez konieczności wykonywania kosztownych operacji alokacji pamięci i kopiowania.

Aby skorzystać z przenieść semantyki w `vector` przykładzie, można napisać konstruktora przenoszenia, aby przenieść dane z jednego obiektu do drugiego.

Aby uzyskać więcej informacji na temat wprowadzania semantyki przenoszenia do standardowej biblioteki języka C++ w programie Visual Studio 2010, zobacz [Standardowa biblioteka języka C++](../standard-library/cpp-standard-library-reference.md).

## <a name="perfect-forwarding"></a>Doskonałe przekazywanie

Doskonałe przekazywanie zmniejsza zapotrzebowanie na przeciążone funkcje i pomaga uniknąć problemu z przekazywaniem. *Problem z przekazywaniem może* wystąpić podczas pisania funkcji ogólnej, która przyjmuje odwołania jako swoje parametry i przekazuje (lub *przekazuje)* te parametry do innej funkcji. Na przykład jeśli funkcja ogólna przyjmuje `const T&`parametr typu , funkcja wywołana nie może zmodyfikować wartości tego parametru. Jeśli funkcja ogólna przyjmuje `T&`parametr typu , funkcja nie może być wywoływana przy użyciu wartości r (takiej jak obiekt tymczasowy lub literał całkowity).

Zwykle, aby rozwiązać ten problem, należy podać przeciążone wersje funkcji `T&` rodzajowej, które przyjmują zarówno dla `const T&` każdego z jego parametrów. W rezultacie liczba przeciążonych funkcji wzrasta wykładniczo wraz z liczbą parametrów. Odwołania do wartości Rwalue umożliwiają zapisanie jednej wersji funkcji, która akceptuje dowolne argumenty i przekazuje je do innej funkcji, tak jakby inna funkcja została wywołana bezpośrednio.

Rozważmy poniższy przykład, który `W` `X`deklaruje `Y`cztery `Z`typy, , , i . Konstruktor dla każdego typu przyjmuje inną kombinację **const** i**non-const** lvalue odwołania jako jego parametry.

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

Załóżmy, że chcesz napisać ogólną funkcję, która generuje obiekty. W poniższym przykładzie pokazano jeden sposób zapisu tej funkcji:

```cpp
template <typename T, typename A1, typename A2>
T* factory(A1& a1, A2& a2)
{
   return new T(a1, a2);
}
```

W poniższym przykładzie przedstawiono prawidłowe wywołanie `factory` funkcji:

```cpp
int a = 4, b = 5;
W* pw = factory<W>(a, b);
```

Jednak poniższy przykład nie zawiera prawidłowego `factory` wywołania funkcji, ponieważ `factory` przyjmuje odwołania lvalue, które można modyfikować jako jego parametry, ale jest wywoływana przy użyciu wartości rvalues:

```cpp
Z* pz = factory<Z>(2, 2);
```

Zwykle, aby rozwiązać ten problem, należy utworzyć przeciążoną `factory` wersję funkcji `A&` dla `const A&` każdej kombinacji i parametrów. Odwołania do wartości Rwalue umożliwiają zapisanie jednej wersji `factory` funkcji, jak pokazano w poniższym przykładzie:

```cpp
template <typename T, typename A1, typename A2>
T* factory(A1&& a1, A2&& a2)
{
   return new T(std::forward<A1>(a1), std::forward<A2>(a2));
}
```

W tym przykładzie użyto rvalue `factory` odwołania jako parametry funkcji. Celem funkcji [std::forward](../standard-library/utility-functions.md#forward) jest przekazanie parametrów funkcji fabrycznej do konstruktora klasy szablonu.

Poniższy przykład `main` przedstawia funkcję, która `factory` używa poprawionej funkcji `W` `X`do `Y`tworzenia `Z` wystąpień , , i klas. Zmieniona `factory` funkcja przekazuje swoje parametry (wartości lvalues lub rvalues) do odpowiedniego konstruktora klasy.

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

## <a name="additional-properties-of-rvalue-references"></a>Dodatkowe właściwości odwołań Rvalue

**Można przeciążyć funkcję, aby wziąć odwołanie lvalue i odwołanie rvalue.**

Przeciążając funkcję w celu podjęcia odwołania **const** lvalue lub odwołania do wartości rvalue, można napisać kod, który rozróżnia obiekty niemodyfikowalne (wartości lvalues) i modyfikowalne wartości tymczasowe (wartości rceny). Obiekt można przekazać do funkcji, która przyjmuje odwołanie do wartości r, chyba że obiekt jest oznaczony jako **const**. Poniższy przykład przedstawia `f`funkcję , która jest przeciążona do podjęcia odwołania lvalue i odwołania rvalue. Funkcja `main` wywołuje `f` zarówno wartości lvalues i rvalue.

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

W tym przykładzie pierwsze `f` wywołanie przekazuje zmienną lokalną (lvalue) jako jej argument. Drugie wywołanie `f` przekazuje obiekt tymczasowy jako jego argument. Ponieważ obiekt tymczasowy nie może odwoływać się w innym miejscu w programie, wywołanie wiąże się z `f` przeciążona wersja, która ma odwołanie rvalue, który jest wolny, aby zmodyfikować obiekt.

**Kompilator traktuje odwołanie o nazwie rvalue jako lvalue i nienazwane odwołanie rvalue jako wartość rvalue.**

Podczas pisania funkcji, która przyjmuje odwołanie rvalue jako parametr, ten parametr jest traktowany jako lvalue w treści funkcji. Kompilator traktuje odwołanie o nazwie rvalue jako wartość lvalue, ponieważ nazwany obiekt może odwoływać się do kilku części programu; byłoby niebezpieczne, aby umożliwić wiele części programu do modyfikowania lub usuwania zasobów z tego obiektu. Na przykład jeśli wiele części programu próbuje przenieść zasoby z tego samego obiektu, tylko pierwsza część pomyślnie przeniesie zasób.

Poniższy przykład przedstawia `g`funkcję , która jest przeciążona do podjęcia odwołania lvalue i odwołania rvalue. Funkcja `f` przyjmuje odwołanie rvalue jako parametr (odwołanie o nazwie rvalue) i zwraca odwołanie rvalue (nienazwane odwołanie do wartości r. ( W wywołaniu `g` `f`z , przeciążenie rozdzielczość `g` wybiera wersję, która przyjmuje odwołanie `f` lvalue, ponieważ treść traktuje jego parametr jako lvalue. W wywołaniu `g` `main`z , przeciążenie rozdzielczość `g` wybiera wersję, która przyjmuje `f` odwołanie rvalue, ponieważ zwraca odwołanie rvalue.

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

W tym przykładzie `main` funkcja przekazuje wartość `f`rvalue do . Treść `f` traktuje jego nazwany parametr jako lvalue. Wywołanie `f` z `g` wiąże parametr z odwołaniem lvalue (pierwsza przeciążona wersja `g`).

- **Wartość lvalue można rzutować na odwołanie wartości r.**

Funkcja C++ Standard Library [std::move](../standard-library/utility-functions.md#move) umożliwia konwertowanie obiektu na odwołanie do wartości r. do tego obiektu. Alternatywnie można użyć słowa kluczowego **static_cast,** aby rzutować wartość lvalue na odwołanie do wartości r, jak pokazano w poniższym przykładzie:

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

**Szablony funkcji wywniają ich typy argumentów szablonów, a następnie używają reguł zwijania odwołań.**

Często jest napisać szablon funkcji, który przekazuje (lub *przekazuje)* swoje parametry do innej funkcji. Ważne jest, aby zrozumieć, jak działanie dedukcji typu szablonu dla szablonów funkcji, które przyjmują odwołania do wartości.

Jeśli argument funkcji jest rvalue, kompilator wydeniuwuje argument jako odwołanie rvalue. Na przykład w przypadku przekazania odwołania rvalue `X` do obiektu typu do `T&&` funkcji szablonu, która przyjmuje typ `T` jako `X`parametr, wywnienie odliczenia argumentu szablonu ma być . W związku z tym `X&&`parametr ma typ . Jeśli argument funkcji jest lvalue lub **const** lvalue, kompilator wydeniuuje jego typ jako odwołanie lvalue lub **odwołanie do rescencji** tego typu.

Poniższy przykład deklaruje jeden szablon struktury, a następnie specjalizuje się w różnych typach odwołań. Funkcja `print_type_and_value` przyjmuje odwołanie rvalue jako parametr i przekazuje go do `S::print` odpowiedniej wersji wyspecjalizowanej metody. Funkcja `main` pokazuje różne sposoby wywołania `S::print` metody.

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

Aby rozwiązać każde `print_type_and_value` wywołanie funkcji, kompilator najpierw wykonuje dedukcję argumentu szablonu. Kompilator następnie stosuje reguły zwijania odwołania, gdy zastępuje wywnioskowane argumenty szablonu dla typów parametrów. Na przykład przekazanie zmiennej `s1` `print_type_and_value` lokalnej do funkcji powoduje, że kompilator tworzy następujący podpis funkcji:

```cpp
print_type_and_value<string&>(string& && t)
```

Kompilator używa reguł zwijania odwołań, aby zmniejszyć podpis do następujących:

```cpp
print_type_and_value<string&>(string& t)
```

Ta wersja `print_type_and_value` funkcji następnie przekazuje jego parametr do poprawnej wersji wyspecjalizowanej `S::print` metody.

W poniższej tabeli podsumowano reguły zwijania odwołania dla dedukcji typu argumentu szablonu:

|||
|-|-|
|Typ rozszerzony|Typ zwiniętego|
|`T& &`|`T&`|
|`T& &&`|`T&`|
|`T&& &`|`T&`|
|`T&& &&`|`T&&`|

Odliczenie argumentu szablonu jest ważnym elementem implementacji doskonałego przekazywania. Sekcja Perfect Forwarding, która jest przedstawiona wcześniej w tym temacie, opisuje doskonałe przekazywanie bardziej szczegółowo.

## <a name="summary"></a>Podsumowanie

Odwołania Rvalue odróżniają wartości lvalues od wartości r. Mogą one pomóc w zwiększeniu wydajności aplikacji, eliminując potrzebę niepotrzebnych alokacji pamięci i operacji kopiowania. Umożliwiają one również zapis jednej wersji funkcji, która akceptuje dowolne argumenty i przekazuje je do innej funkcji, tak jakby inna funkcja została wywołana bezpośrednio.

## <a name="see-also"></a>Zobacz też

[Wyrażenia z operatorami jednoargumentowymi](../cpp/expressions-with-unary-operators.md)<br/>
[Deklarator odwołania do wartości L: &](../cpp/lvalue-reference-declarator-amp.md)<br/>
[Wartości lvalues i wartości r](../cpp/lvalues-and-rvalues-visual-cpp.md)<br/>
[Konstruktory przenoszące i przenoszące operatory przypisania (C++)](../cpp/move-constructors-and-move-assignment-operators-cpp.md)<br/>
[Standardowa biblioteka języka C++](../standard-library/cpp-standard-library-reference.md)
