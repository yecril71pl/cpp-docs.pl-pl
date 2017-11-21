---
title: "Specyfikacje wyjątków (throw) (C++) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
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
- throw keyword [C++], throw() vs. throw(...)
- throw keyword [C++], exception specifications
ms.assetid: 4d3276df-6f31-4c7f-8cab-b9d2d003a629
caps.latest.revision: "20"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: e308d95f25b25a99fecde976d8ba6433316f460f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="exception-specifications-throw-noexcept-c"></a>Specyfikacje wyjątków (throw, noexcept) (C++)
Specyfikacje wyjątków są funkcją języka C++, która wskazuje zamiar programisty o typów wyjątków, które mogą być przekazywane przez funkcję. Można określić, czy funkcja może lub nie może zamknąć przez wyjątek przy użyciu *specyfikacji wyjątku*. Kompilator można wykorzystać te informacje do optymalizacji wywołania funkcji, a zakończenie program, jeśli wystąpił nieoczekiwany wyjątek specjalne funkcji. Istnieją dwa rodzaje specyfikacji wyjątku. *Specyfikacji noexcept* nowego w języku C ++ 11. Określa, czy zestaw potencjalnych wyjątki, które można wprowadzić funkcji jest pusta. *Specyfikacji wyjątków dynamicznych*, lub `throw(optional_type_list)` specyfikacji, jest przestarzała w języku C ++ 11 i jest tylko częściowo obsługiwane przez program Visual Studio. Specyfikacja tego wyjątku została zaprojektowana w celu zapewnienia podsumowanie informacji o jakie wyjątki może zostać wygenerowany poza funkcją, ale w praktyce znaleziono problemów. Jedną specyfikację wyjątków dynamicznych, które okazać się przydatne w pewnym stopniu został bezwarunkowe `throw()` specyfikacji. Na przykład deklaracji funkcji:  
  
```cpp  
void MyFunction(int i) throw();  
```  
  
 informuje kompilator, funkcja generują żadnych wyjątków. Jest to równoważne z przy użyciu [__declspec(nothrow)](../cpp/nothrow-cpp.md). Wykorzystanie przez niego są traktowane jako opcjonalne.  
  
W języku C ++ 11 normy ISO [noexcept](../cpp/noexcept-cpp.md) operator została wprowadzona jako zamiennika. Jest obsługiwane w programie Visual Studio 2015 i nowszych. Jeśli to możliwe, użyj `noexcept` wyrażenia, aby określić, czy funkcja może zgłaszać wyjątków. Na przykład użyć tej deklaracji funkcji zamiast powyżej:  
  
```cpp  
void MyFunction(int i) noexcept;  
```  
  
Gdy Visual C++ w pełni obsługuje `noexcept` wyrażenia, różni się ona od ISO C++ standardowy jego wykonywania specyfikacje wyjątków dynamicznych.  Poniższa tabela zawiera podsumowanie wdrożenia Visual C++ specyfikacje wyjątków:  
  
|Specyfikacja wyjątku|Znaczenie|  
|-----------------------------|-------------|  
|`noexcept`<br/>`noexcept(true)`<br/>`throw()`|Funkcja nie zgłasza wyjątek. Jednak jeśli wyjątek jest poza funkcją oznaczone `throw()`, wywołania kompilatora Visual C++ `std::terminate`, a nie `std::unexpected`. Zobacz [std::unexpected](../c-runtime-library/reference/unexpected-crt.md) Aby uzyskać więcej informacji. Jeśli funkcja jest oznaczony jako `noexcept`, `noexcept(true)`, lub `throw()`, kompilator języka Visual C++ przyjęto założenie, że funkcja nie zgłaszają wyjątki C++ i odpowiednio generuje kod. Ponieważ optymalizacje kodu może zostać wykonana przez kompilator języka C++, oparte na założeniu, że funkcja nie zgłoszenia wyjątki C++, jeśli funkcja zgłosić wyjątek, program może zostać wykonane nieprawidłowo.|  
|`noexcept(false)`<br/>`throw(...)`<br/>Brak specyfikacji|Funkcja może zgłosić wyjątek dowolnego typu.|  
|`throw(type)`|Funkcja może zgłosić wyjątek typu `type`. W programie Visual C++ tej składni jest akceptowany, ale jest interpretowany jako `noexcept(false)`.|  
  
 Jeśli obsługa wyjątków jest używany w aplikacji, musi istnieć funkcji w stosie wywołań, który oznaczony uchwytów zgłaszane wyjątki przed ich zakończyć zewnętrznym zakresie funkcji `noexcept`, `noexcept(true)`, lub `throw()`. Jeśli wszystkie funkcje wywoływane między jedną, która zgłasza wyjątek i jedną, która obsługuje wyjątek są określone jako `noexcept`, `noexcept(true)`, lub `throw()`, program zostanie zakończony, gdy funkcja noexcept propaguje wyjątek.  
  
 Zachowanie wyjątek funkcji jest zależna od następujących czynników:  
  
-   Określa, czy kompilacja funkcji w obszarze C lub C++.  
  
-   Które [/EH](../build/reference/eh-exception-handling-model.md) używasz — opcja kompilatora.  
  
-   Określa, czy jawnie określić specyfikacji wyjątku.  
  
 Specyfikacje wyjątków jawne są niedozwolone w funkcji języka C. Funkcja C założono, że nie zgłaszają wyjątki w obszarze **/ehsc**i może zgłaszać wyjątki strukturalne w obszarze **/EHS**, **/eha**, lub **/EHac**.  
  
 Poniższa tabela zawiera podsumowanie, czy funkcja C++ potencjalnie może zgłaszać w różnych wyjątek kompilatora opcje obsługi:  
  
|Funkcja|/ EHsc|/ EHs|/ EHa|/ EHac|  
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
 [Spróbuj, throw i catch instrukcji (C++)](../cpp/try-throw-and-catch-statements-cpp.md)   
 [C++, obsługa wyjątków](../cpp/cpp-exception-handling.md)