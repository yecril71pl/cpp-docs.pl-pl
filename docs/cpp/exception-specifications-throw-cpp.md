---
title: Specyfikacje wyjątków (throw, noexcept) (C++) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2018
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- exceptions [C++], exception specifications
- throwing exceptions [C++], throw keyword
- C++ exception handling [C++], throwing exceptions
- throw keyword [C++]
- noexcept keyword [C++]
ms.assetid: 4d3276df-6f31-4c7f-8cab-b9d2d003a629
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1dfc9c50503fcd277f34e8f5dfc4a630d888eebf
ms.sourcegitcommit: f0c90000125a9497bf61e41624de189a043703c0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2018
ms.locfileid: "44318281"
---
# <a name="exception-specifications-throw-noexcept-c"></a>Specyfikacje wyjątków (throw, noexcept) (C++)

Specyfikacje wyjątków są funkcją języka C++, wskazujące intencji programisty dotyczące typów wyjątków, które mogą być przekazywane przez funkcję. Można określić, że funkcja może lub nie może zakończyć przez wyjątek przy użyciu *Specyfikacja wyjątku*. Kompilator może dzięki tym informacjom można zoptymalizować wywołań funkcji, a następnie zakończyć program, jeśli wystąpił nieoczekiwany wyjątek specjalne funkcji. 

Przed C ++ 17 wystąpiły dwa rodzaje Specyfikacja wyjątku. *Specyfikacji noexcept* nowych funkcji w języku C ++ 11. Określa, czy zestaw potencjalne wyjątki, które można udosłownić funkcji jest pusta. *Specyfikacji wyjątków dynamicznych*, lub `throw(optional_type_list)` specyfikacji zostało uznane za przestarzałe w C ++ 11 i usunięte w języku C ++ 17, z wyjątkiem `throw()`, która jest aliasem `noexcept(true)`. Ta specyfikacja wyjątku zaprojektowano tak, aby podawać sumaryczne informacje o tym, jakie wyjątki mogą zostać wygenerowane z funkcji, ale w praktyce okazało się być problematyczne. Jeden specyfikacji wyjątków dynamicznych, która miała być nieco użyteczne został bezwarunkowe `throw()` specyfikacji. Na przykład deklaracji funkcji:

```cpp
void MyFunction(int i) throw();
```
informuje kompilator, że funkcja nie generuje żadnych wyjątków. Jednak w **/STD: c ++ 14** trybu, może to spowodować niezdefiniowane zachowanie, jeśli funkcja zgłosi wyjątek. W związku z tym zaleca się używanie [noexcept](../cpp/noexcept-cpp.md) operator zamiast powyżej:

```cpp
void MyFunction(int i) noexcept;
```
Poniższa tabela zawiera podsumowanie implementacji specyfikacji wyjątków Microsoft Visual C++:

|Specyfikacja wyjątku|Znaczenie|
|-----------------------------|-------------|
|`noexcept`<br/>`noexcept(true)`<br/>`throw()`|Funkcja nie zgłasza wyjątku. W [/STD: c ++ 14](../build/reference/std-specify-language-standard-version.md) tryb (jest to ustawienie domyślne), `noexcept` i `noexcept(true)` są równoważne. Gdy wyjątek jest generowany przez funkcję, która jest zadeklarowana `noexcept` lub `noexcept(true)`, [std::terminate](../standard-library/exception-functions.md#terminate) zostanie wywołana. Gdy wyjątek jest generowany przez funkcję zadeklarowane jako `throw()` w **/STD: c ++ 14** tryb, wynik jest niezdefiniowane zachowanie. Brak określonej funkcji jest wywoływana. Jest to rozbieżności z C ++ 14 w warstwie standardowa, który wymagany kompilator, aby wywołać [std::unexpected](../standard-library/exception-functions.md#unexpected).  <br/> **Visual Studio 2017 w wersji 15.5 lub nowszej**: W **/STD: c ++ 17** trybie `noexcept`, `noexcept(true)`, i `throw()` są wszystkie równoważne. W **/STD: c ++ 17** trybie `throw()` jest aliasem `noexcept(true)`. W **/STD: c ++ 17** tryb, gdy wyjątek jest generowany przez funkcję zadeklarowane za pomocą dowolnego z tych specyfikacji [std::terminate](../standard-library/exception-functions.md#terminate) wywoływaną zgodnie z wymaganiami C ++ 17 standardowych.|
|`noexcept(false)`<br/>`throw(...)`<br/>Brak specyfikacji|Funkcja może zgłosić wyjątek dowolnego typu.|
|`throw(type)`| (**C ++ 14 i starszych**) funkcja może zgłosić wyjątek typu `type`. Kompilator akceptuje składni, ale zinterpretuje ją jako `noexcept(false)`. W **/STD: c ++ 17** tryb kompilator generuje ostrzeżenie C5040.|

Jeśli w aplikacji zastosowano obsługę wyjątków, musi istnieć funkcji w stosie wywołań, który obsługuje zgłaszane wyjątki, zanim zamykania zewnętrznym zakresem funkcji oznaczony `noexcept`, `noexcept(true)`, lub `throw()`. Jeśli wszystkie funkcje wywołane między tą, która zgłosiła wyjątek oraz jedną, która obsługuje wyjątek, są określane jako `noexcept`, `noexcept(true)` (lub `throw()` w **/STD: c ++ 17** tryb), program zostanie zakończony, kiedy Funkcja noexcept propaguje wyjątek.

Zachowanie wyjątku przez funkcję zależy od następujących czynników:

- Które [Tryb standardowy kompilacji języka](../build/reference/std-specify-language-standard-version.md) jest ustawiona.
- Czy kompilujesz funkcję w C lub C++.

- Które [/EH](../build/reference/eh-exception-handling-model.md) — opcja kompilatora używasz.

- Czy jawnie określasz wyjątek specyfikacji.

Jawne specyfikacje wyjątku nie są dozwolone w funkcjach c. Funkcja języka C założono, że nie zgłaszają wyjątki, w obszarze **/ehsc**i może zgłaszać wyjątki strukturalne, w obszarze **/EHS**, **/eha**, lub **/EHac**.

W poniższej tabeli podsumowano, czy funkcja C++ potencjalnie może zgłaszać w ramach różnych wyjątków kompilatora, opcje obsługi:

|Funkcja|/EHsc|/ EHs|/EHa|/EHac|
|--------------|------------|-----------|-----------|------------|
|Funkcja języka C++ bez określenia wyjątków|Tak|Tak|Tak|Tak|
|Funkcja języka C++ z `noexcept`, `noexcept(true)`, lub `throw()` Specyfikacja wyjątku|Nie|Nie|Tak|Tak|
|Funkcja języka C++ z `noexcept(false)`, `throw(...)`, lub `throw(type)` Specyfikacja wyjątku|Tak|Tak|Tak|Tak|

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

## <a name="see-also"></a>Zobacz także
 [Instrukcje try, throw i catch (C++)](../cpp/try-throw-and-catch-statements-cpp.md)  
 [Obsługa wyjątków języka C++](../cpp/cpp-exception-handling.md)