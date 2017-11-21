---
title: "Spróbuj, throw i catch instrukcji (C++) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- catch_cpp
- try_cpp
- throw_cpp
dev_langs: C++
helpviewer_keywords:
- catch keyword [C++]
- keywords [C++], exception handling
- C++ exception handling, statement syntax
- try-catch keyword [C++], about try-catch exception handling
- throw keyword [C++]
- try-catch keyword [C++]
- try-catch keyword [C++], exception handling
- throwing exceptions [C++], throw keyword
- try-catch keyword [C++], throw keyword [C++]s
- throwing exceptions [C++], implementing C++ exception handling
- throwing exceptions [C++]
- throw keyword [C++], throw() vs. throw(...)
ms.assetid: 15e6a87b-b8a5-4032-a7ef-946c644ba12a
caps.latest.revision: "24"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 747ee64a701250c83b3b0401a5fbb3d82496a99e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="try-throw-and-catch-statements-c"></a>Instrukcje try, throw i catch (C++)
Aby zaimplementować obsługi wyjątków w języku C++, należy użyć `try`, `throw`, i `catch` wyrażenia.  
  
 Najpierw użyj `try` bloku, aby załączyć przynajmniej jednej instrukcji, które może zgłosić wyjątek.  
  
 A `throw` wyrażenie sygnalizuje, że warunek wyjątkowych — często, błąd — wystąpił w `try` bloku. Obiekt dowolnego typu może być używany jako argument operacji `throw` wyrażenia. Obiekt ten jest zazwyczaj używany do przekazywania informacji o błędzie. W większości przypadków zaleca się użycie [std::exception](../standard-library/exception-class.md) klasy lub jednej z klas pochodnych, które są zdefiniowane w standardowej bibliotece. Jeśli nie jest jednym z tych właściwe, firma Microsoft zaleca klasy wyprowadzonej własne klasy wyjątków z `std::exception`.  
  
 Do obsługi wyjątków, które może zostać zgłoszony, zaimplementować jedną lub więcej `catch` bloki bezpośrednio po `try` bloku. Każdy `catch` bloku określa typ wyjątku może obsługiwać.  
  
 W tym przykładzie pokazano `try` bloku i jego obsługi. Przyjęto założenie, że `GetNetworkResource()` uzyskuje danych za pośrednictwem połączenia sieciowego i czy typów wyjątków dwie klasy zdefiniowane przez użytkownika, które pochodzą z `std::exception`. Należy zauważyć, że wyjątki są przechwytywane przez `const` odwołania w `catch` instrukcji. Firma Microsoft zaleca, aby generować wyjątki przez wartość i przechwytywać przez odniesienie const.  
  
## <a name="example"></a>Przykład  
  
```  
  
MyData md;  
try {  
   // Code that could throw an exception  
   md = GetNetworkResource();  
}  
catch (const networkIOException& e) {  
   // Code that executes when an exception of type  
   // networkIOException is thrown in the try block  
   // ...  
   // Log error message in the exception object  
   cerr << e.what();  
}  
catch (const myDataFormatException& e) {  
   // Code that handles another exception type  
   // ...  
   cerr << e.what();  
}  
  
// The following syntax shows a throw expression  
MyData GetNetworkResource()  
{  
   // ...  
   if (IOSuccess == false)  
      throw networkIOException("Unable to connect");  
   // ...  
   if (readError)  
      throw myDataFormatException("Format error");   
   // ...  
}  
```  
  
## <a name="remarks"></a>Uwagi  
 Kod po `try` klauzula jest zabezpieczona sekcji kodu. `throw` Wyrażenie *zgłasza*— to znaczy zgłasza — Wystąpił wyjątek. Blok kodu po `catch` klauzula jest program obsługi wyjątku. To jest program obsługi który *przechwytuje* wyjątek, który jest generowany, jeśli typy w `throw` i `catch` wyrażenia są zgodne. Lista reguł, które będą zarządzały sposobem dopasowania w `catch` bloków, zobacz [są obliczane bloki przechwytywania w sposób](../cpp/how-catch-blocks-are-evaluated-cpp.md). Jeśli `catch` instrukcji określa wielokropek (...) zamiast typu `catch` bloku obsługi każdego typu wyjątku. Podczas kompilacji z [/eha](../build/reference/eh-exception-handling-model.md) opcji mogą do nich wyjątki C strukturalnych i generowanych przez system lub wygenerowane w aplikacji wyjątków asynchronicznych np. naruszenia dzielenie przez zero i typem zmiennoprzecinkowym ochrony pamięci . Ponieważ `catch` bloki są przetwarzane w kolejności programu można znaleźć zgodnego typu, program obsługi wielokropka musi być ostatnim obsługi skojarzonych z nim `try` bloku. Użyj `catch(...)` ostrożnie; nie zezwalaj na program kontynuować, chyba że blok catch potrafi obsłużyć określony wyjątek, który zostanie przechwycony. Zazwyczaj `catch(...)` blok służy do dziennika błędów i wykonać specjalne oczyszczania przed wykonania programu została zatrzymana.  
  
 A `throw` wyrażenie, które nie operand ponownie zgłasza wyjątek, w obecnie obsługiwane. Zaleca się tę formę podczas ponownego zgłaszania wyjątku, ponieważ pozwala to zachować informacje o polimorficznym typie oryginalnego wyjątku. Takie wyrażenie należy używać tylko w `catch` obsługi lub funkcję, która jest wywoływana z `catch` obsługi. Ponownie zgłoszony obiekt wyjątku to oryginalny obiekt wyjątku, a nie kopia.  
  
```  
try {  
   throw CSomeOtherException();  
}  
catch(...) {  
   // Catch all exceptions - dangerous!!!  
   // Respond (perhaps only partially) to the exception, then  
   // re-throw to pass the exception to some other handler  
   // ...  
   throw;  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [C++, obsługa wyjątków](../cpp/cpp-exception-handling.md)   
 [Słowa kluczowe](../cpp/keywords-cpp.md)   
 [Nieobsługiwane wyjątki języka C++](../cpp/unhandled-cpp-exceptions.md)   
 [__uncaught_exception](../c-runtime-library/reference/uncaught-exception.md)