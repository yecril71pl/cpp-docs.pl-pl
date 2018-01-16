---
title: "Specyfikacje wyjątków (throw) (C++) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 01/12/2018
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords:
- exceptions [C++], exception specifications
- throwing exceptions [C++], throw keyword
- C++ exception handling [C++], throwing exceptions
- throw keyword [C++]
- noexcept keyword [C++]
ms.assetid: 4d3276df-6f31-4c7f-8cab-b9d2d003a629
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: c93fdaa75155e6f0117ef1c30d4e093d5ca0e576
ms.sourcegitcommit: c2e990450ccd528d85b2783fbc63042612987cfd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/16/2018
---
# <a name="exception-specifications-throw-noexcept-c"></a>Specyfikacje wyjątków (throw, noexcept) (C++)

Specyfikacje wyjątków są funkcją języka C++, która wskazuje zamiar programisty o typów wyjątków, które mogą być przekazywane przez funkcję. Można określić, czy funkcja może lub nie może zamknąć przez wyjątek przy użyciu *specyfikacji wyjątku*. Kompilator można wykorzystać te informacje do optymalizacji wywołania funkcji, a zakończenie program, jeśli wystąpił nieoczekiwany wyjątek specjalne funkcji. 

Przed C ++ 17 wystąpiły dwa rodzaje specyfikacji wyjątku. *Specyfikacji noexcept* nowych funkcji w języku C ++ 11. Określa, czy zestaw potencjalnych wyjątki, które można wprowadzić funkcji jest pusta. *Specyfikacji wyjątków dynamicznych*, lub `throw(optional_type_list)` specyfikacja, została uznana za przestarzałą w języku C ++ 11 i usunięte w języku C ++ 17, z wyjątkiem `throw()`, który jest aliasem noexcept(true). Specyfikacja tego wyjątku została zaprojektowana w celu zapewnienia podsumowanie informacji o jakie wyjątki może zostać wygenerowany poza funkcją, ale w praktyce znaleziono problemów. Jedną specyfikację wyjątków dynamicznych, które okazać się przydatne w pewnym stopniu został bezwarunkowe `throw()` specyfikacji. Na przykład deklaracji funkcji:

```cpp
void MyFunction(int i) throw();
```

 informuje kompilator, funkcja generują żadnych wyjątków. Jednak w **/std:c ++ 14** może prowadzić do trybu niezdefiniowane zachowanie, jeśli funkcja Zgłoś wyjątek. Dlatego zaleca się używanie [noexcept](../cpp/noexcept-cpp.md) operator zamiast powyżej:

```cpp
void MyFunction(int i) noexcept;
```

Poniższa tabela zawiera podsumowanie wdrożenia Visual C++ specyfikacje wyjątków:

|Specyfikacja wyjątku|Znaczenie|
|-----------------------------|-------------|
|`noexcept`<br>`noexcept(true)`<br>`throw()`|Funkcja nie zgłasza wyjątek. W [/std:c ++ 14](../build/reference/std-specify-language-standard-version.md) trybu (która jest wartością domyślną), `noexcept` i `noexcept(true)` są równoważne. Jeśli wyjątek jest funkcja, która jest zadeklarowana jako `noexcept` lub `noexcept(true)`, [std::terminate](../standard-library/exception-functions.md#terminate) jest wywoływana. Jeśli wyjątek jest funkcji zadeklarowany jako `throw()` w **/std:c ++ 14** tryb, wynik jest niezdefiniowane zachowanie. Nie określonego funkcja jest wywoływana. Jest to rozbieżność z języka C ++ 14 standardowe, wymagająca kompilatora do wywołania [std::unexpected](../standard-library/exception-functions.md#unexpected).  <br> **Visual Studio 2017 wersji 15.5 i nowszych**: W **/std:c ++ 17** trybie `noexcept`, `noexcept(true)`, i `throw()` wszystkie równoważne. W **/std:c ++ 17** trybie `throw()` jest aliasem `noexcept(true)`. W **/std:c ++ 17** tryb, gdy wyjątek funkcja zadeklarowana ze wszystkimi tymi specyfikacjami [std::terminate](../standard-library/exception-functions.md#terminate) wywoływany jest zgodnie z żądaniem standardzie C ++ 17.|
|`noexcept(false)`<br/>`throw(...)`<br/>Brak specyfikacji|Funkcja może zgłosić wyjątek dowolnego typu.|
|`throw(type)`| (**C ++ 14 i wcześniejszych**) funkcja może zgłosić wyjątek typu `type`. Kompilator Microsoft C++ akceptuje składnię, ale zinterpretuje ją jako `noexcept(false)`. W **/std:c ++ 17** tryb kompilator generuje ostrzeżenie C5040.|

 Jeśli obsługa wyjątków jest używany w aplikacji, musi istnieć funkcji w stosie wywołań, który oznaczony uchwytów zgłaszane wyjątki przed ich zakończyć zewnętrznym zakresie funkcji `noexcept`, `noexcept(true)`, lub `throw()`. Jeśli wszystkie funkcje wywoływane między jedną, która zgłasza wyjątek i jedną, która obsługuje wyjątek są określone jako `noexcept`, `noexcept(true)` (lub `throw()` w **/std:c ++ 17** tryb), program zostanie zakończony, kiedy Funkcja noexcept propaguje wyjątek.

 Zachowanie wyjątek funkcji jest zależna od następujących czynników:

- Które [Tryb standardowy kompilacji języka](../build/reference/std-specify-language-standard-version.md) jest ustawiona.
- Określa, czy kompilacja funkcji w obszarze C lub C++.

- Które [/EH](../build/reference/eh-exception-handling-model.md) używasz — opcja kompilatora.

- Określa, czy jawnie określić specyfikacji wyjątku.

 Specyfikacje wyjątków jawne są niedozwolone w funkcji języka C. Funkcja C założono, że nie zgłaszają wyjątki w obszarze **/ehsc**i może zgłaszać wyjątki strukturalne w obszarze **/EHS**, **/eha**, lub **/EHac**.

 Poniższa tabela zawiera podsumowanie, czy funkcja C++ potencjalnie może zgłaszać w różnych wyjątek kompilatora opcje obsługi:

|Funkcja|/EHsc|/ EHs|/EHa|/EHac|
|--------------|------------|-----------|-----------|------------|
|Funkcja języka C++ z Brak specyfikacji wyjątku|Tak|Tak|Tak|Tak|
|Funkcja języka C++ z `noexcept`, `noexcept(true)`, lub `throw()` specyfikacji wyjątku|Nie|Nie|Tak|Tak|
|Funkcja języka C++ z `noexcept(false)`, `throw(...)`, lub `throw(type)` specyfikacji wyjątku|Tak|Tak|Tak|Tak|

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

 [Spróbuj, throw i catch instrukcji (C++)](../cpp/try-throw-and-catch-statements-cpp.md) [Obsługa wyjątków języka C++](../cpp/cpp-exception-handling.md)