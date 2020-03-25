---
title: Specyfikacje wyjątków (throw, noexcept) (C++)
ms.date: 01/18/2018
helpviewer_keywords:
- exceptions [C++], exception specifications
- throwing exceptions [C++], throw keyword
- C++ exception handling [C++], throwing exceptions
- throw keyword [C++]
- noexcept keyword [C++]
ms.assetid: 4d3276df-6f31-4c7f-8cab-b9d2d003a629
ms.openlocfilehash: 6f8f9466b867603738919c6210055d02d3c579ae
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80180046"
---
# <a name="exception-specifications-throw-noexcept-c"></a>Specyfikacje wyjątków (throw, noexcept) (C++)

Specyfikacje wyjątków są funkcją C++ języka, która wskazuje zamiar programisty o typach wyjątków, które mogą być propagowane przez funkcję. Można określić, że funkcja może lub nie może wyjść przez wyjątek przy użyciu *specyfikacji wyjątku*. Kompilator może używać tych informacji do optymalizowania wywołań funkcji i kończenia działania programu, jeśli wystąpił nieoczekiwany wyjątek.

Wcześniej niż C++ 17 wystąpiły dwa rodzaje specyfikacji wyjątków. *Specyfikacja noexcept* była nowością w języku c++ 11. Określa, czy zestaw potencjalnych wyjątków, które mogą ucieczki funkcja jest pusty. *Specyfikacja wyjątku dynamicznego*lub Specyfikacja `throw(optional_type_list)` była przestarzała w języku c++ 11 i została usunięta w języku c++ 17, z wyjątkiem `throw()`, który jest aliasem dla `noexcept(true)`. Ta specyfikacja wyjątku została zaprojektowana w celu udostępnienia informacji podsumowujących o wyjątkach, które mogą być zgłaszane z funkcji, ale w rzeczywistości okazało się to problematyczne. Jedna Specyfikacja dynamicznego wyjątku, która okazała się nieco przydatna, była niewarunkową specyfikacją `throw()`. Na przykład deklaracja funkcji:

```cpp
void MyFunction(int i) throw();
```

informuje kompilator, że funkcja nie generuje żadnych wyjątków. Jednak w **/std: tryb c++ 14** może to spowodować niezdefiniowane zachowanie, jeśli funkcja zgłosi wyjątek. W związku z tym zalecamy użycie operatora [noexcept](../cpp/noexcept-cpp.md) zamiast jednego z powyższych:

```cpp
void MyFunction(int i) noexcept;
```

W poniższej tabeli zestawiono implementację C++ firmy Microsoft dotyczącej specyfikacji wyjątków:

|Specyfikacja wyjątku|Znaczenie|
|-----------------------------|-------------|
|`noexcept`<br/>`noexcept(true)`<br/>`throw()`|Funkcja nie zgłasza wyjątku. W [/std: tryb c++ 14](../build/reference/std-specify-language-standard-version.md) (co jest ustawieniem domyślnym) `noexcept` i `noexcept(true)` są równoważne. Gdy wyjątek jest zgłaszany przez funkcję zadeklarowaną `noexcept` lub `noexcept(true)`, zostanie wywołana wartość [std:: terminate](../standard-library/exception-functions.md#terminate) . Gdy wyjątek jest zgłaszany przez funkcję zadeklarowaną jako `throw()` w trybie **/std: c++ 14** , wynik jest niezdefiniowanym zachowaniem. Nie została wywołana żadna konkretna funkcja. Jest to rozbieżność ze standardu C++ 14, która wymagała kompilatora do wywołania [std:: unniespodziewane](../standard-library/exception-functions.md#unexpected).  <br/> **Program Visual Studio 2017 w wersji 15,5 i nowszej**: w **/std: tryb c++ 17** , `noexcept`, `noexcept(true)`i `throw()` są równoważne. W **/std: tryb c++ 17** , `throw()` jest aliasem dla `noexcept(true)`. W trybie **/std: c++ 17** , gdy wyjątek jest zgłaszany z funkcji zadeklarowanej za pomocą którejkolwiek z tych specyfikacji, [std:: terminate](../standard-library/exception-functions.md#terminate) jest wywoływana zgodnie z wymaganiami standardu c++ 17.|
|`noexcept(false)`<br/>`throw(...)`<br/>Brak specyfikacji|Funkcja może zgłosić wyjątek dowolnego typu.|
|`throw(type)`| (**C++ 14 i starsze**) Funkcja może zgłosić wyjątek typu `type`. Kompilator akceptuje składnię, ale interpretuje ją jako `noexcept(false)`. W **/std: w trybie c++ 17** kompilator wystawia ostrzeżenie C5040.|

Jeśli obsługa wyjątków jest używana w aplikacji, musi istnieć funkcja w stosie wywołań, która obsługuje zgłoszone wyjątki przed wyjściem zewnętrznego zakresu funkcji oznaczonej `noexcept`, `noexcept(true)`lub `throw()`. Jeśli jakakolwiek funkcja wywołana między tą, która zgłasza wyjątek, a taka, która obsługuje wyjątek, jest określona jako `noexcept`, `noexcept(true)` (lub `throw()` w trybie **/std: c++ 17** ), program zostanie przerwany, gdy funkcja noexcept propaguje wyjątek.

Zachowanie wyjątków funkcji zależy od następujących czynników:

- [Tryb kompilacji standardowej języka](../build/reference/std-specify-language-standard-version.md) jest ustawiony.
- Bez względu na to, czy kompilujesz C++funkcję w języku C, czy.

- Która opcja kompilatora [/EH](../build/reference/eh-exception-handling-model.md) jest używana.

- Określa, czy określono jawnie specyfikację wyjątku.

Jawne specyfikacje wyjątków nie są dozwolone w funkcjach języka C. Przyjęto, że funkcja C nie zgłasza wyjątków w ramach **/EHsc**i może zgłosić wyjątki strukturalne w obszarze **/EHS**, **/EHa**lub **/EHac**.

Poniższa tabela zawiera podsumowanie informacji o C++ tym, czy funkcja może potencjalnie zgłosić się w ramach różnych opcji obsługi wyjątków kompilatora:

|Funkcja|/EHsc|/EHs|/EHa|/EHac|
|--------------|------------|-----------|-----------|------------|
|C++Funkcja bez specyfikacji wyjątku|Yes|Yes|Yes|Yes|
|C++Funkcja z `noexcept`, `noexcept(true)`lub `throw()` Specyfikacja wyjątku|Nie|Nie|Yes|Yes|
|C++Funkcja z `noexcept(false)`, `throw(...)`lub `throw(type)` Specyfikacja wyjątku|Yes|Yes|Yes|Yes|

## <a name="example"></a>Przykład

```cpp
// exception_specification.cpp
// compile with: /EHs
#include <stdio.h>

void handler() {
   printf_s("in handler\n");
}

void f1(void) throw(int) {
   printf_s("About to throw 1\n");
   if (1)
      throw 1;
}

void f5(void) throw() {
   try {
      f1();
   }
   catch(...) {
      handler();
    }
}

// invalid, doesn't handle the int exception thrown from f1()
// void f3(void) throw() {
//   f1();
// }

void __declspec(nothrow) f2(void) {
   try {
      f1();
   }
   catch(int) {
      handler();
    }
}

// only valid if compiled without /EHc
// /EHc means assume extern "C" functions don't throw exceptions
extern "C" void f4(void);
void f4(void) {
   f1();
}

int main() {
   f2();

   try {
      f4();
   }
   catch(...) {
      printf_s("Caught exception from f4\n");
   }
   f5();
}
```

```Output
About to throw 1
in handler
About to throw 1
Caught exception from f4
About to throw 1
in handler
```

## <a name="see-also"></a>Zobacz też

[Instrukcje try, throw i catch (C++)](../cpp/try-throw-and-catch-statements-cpp.md)<br/>
[Nowoczesne C++ najlepsze rozwiązania dotyczące wyjątków i obsługi błędów](errors-and-exception-handling-modern-cpp.md)
