---
title: Instrukcje try, throw i catch (C++)
ms.date: 11/04/2016
f1_keywords:
- catch_cpp
- try_cpp
- throw_cpp
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
ms.openlocfilehash: 03f7f6f5a1a2842ad7fb0ba2715fada130277e70
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80187989"
---
# <a name="try-throw-and-catch-statements-c"></a>Instrukcje try, throw i catch (C++)

Aby zaimplementować obsługę wyjątków w C++programie, należy użyć wyrażeń **try**, **throw**i **catch** .

Najpierw użyj bloku **try** , aby ująć jedną lub więcej instrukcji, które mogą zgłosić wyjątek.

Wyrażenie **throw** sygnalizuje, że wyjątkowy warunek — często błąd — wystąpił w bloku **try** . Można użyć obiektu dowolnego typu jako operandu wyrażenia **throw** . Obiekt ten jest zazwyczaj używany do przekazywania informacji o błędzie. W większości przypadków zaleca się użycie klasy [std:: Exception](../standard-library/exception-class.md) lub jednej z klas pochodnych, które są zdefiniowane w standardowej bibliotece. Jeśli jeden z tych elementów nie jest odpowiedni, zalecamy uzyskanie własnej klasy wyjątku z `std::exception`.

Aby obsłużyć wyjątki, które mogą być zgłaszane, zaimplementuj jeden lub więcej bloków **catch** bezpośrednio po bloku **try** . Każdy blok **catch** określa typ wyjątku, który może obsłużyć.

Ten przykład pokazuje blok **try** i jego programy obsługi. Załóżmy, że `GetNetworkResource()` uzyskują dane przez połączenie sieciowe i że dwa typy wyjątków są klasami zdefiniowanymi przez użytkownika, które pochodzą z `std::exception`. Należy zauważyć, że wyjątki są przechwytywane przez odwołanie **const** w instrukcji **catch** . Firma Microsoft zaleca, aby generować wyjątki przez wartość i przechwytywać przez odniesienie const.

## <a name="example"></a>Przykład

```cpp
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

Kod po klauzuli **try** to chroniona sekcja kodu. Wyrażenie **throw** *zgłasza*— to znaczy, podnosi — wyjątek. Blok kodu po klauzuli **catch** jest programem obsługi wyjątków. Jest to procedura obsługi, która *przechwytuje* wyjątek zgłaszany, jeśli typy w wyrażeniach **throw** i **catch** są zgodne. Aby uzyskać listę reguł rządzących dopasowaniem typu w blokach **catch** , zobacz [jak są oceniane bloki catch](../cpp/how-catch-blocks-are-evaluated-cpp.md). Jeśli instrukcja **catch** określa wielokropek (...) zamiast typu, blok **catch** obsługuje każdy typ wyjątku. Podczas kompilowania z użyciem opcji [/EHa](../build/reference/eh-exception-handling-model.md) mogą to być wyjątki strukturalne C i generowane przez system lub generowane przez aplikacje wyjątki asynchroniczne, takie jak ochrona pamięci, dzielenie przez zero i naruszenia zmiennoprzecinkowe. Ponieważ bloki **catch** są przetwarzane w kolejności programu w celu znalezienia zgodnego typu, program obsługi wielokropka musi być ostatnim programem obsługi dla skojarzonego bloku **try** . Użyj `catch(...)` z zachowaniem ostrożności; nie Zezwalaj programowi na kontynuowanie, jeśli blok catch nie wie, jak obsłużyć konkretny wyjątek, który jest przechwytywany. Zazwyczaj blok `catch(...)` jest używany do rejestrowania błędów i wykonywania specjalnego oczyszczania przed zatrzymaniem wykonywania programu.

Wyrażenie **throw** , które nie ma operandu ponownie zgłasza aktualnie obsługiwany wyjątek. Zaleca się tę formę podczas ponownego zgłaszania wyjątku, ponieważ pozwala to zachować informacje o polimorficznym typie oryginalnego wyjątku. Takie wyrażenie powinno być używane tylko w obsłudze **catch** lub w funkcji, która jest wywoływana z procedury obsługi **catch** . Ponownie zgłoszony obiekt wyjątku to oryginalny obiekt wyjątku, a nie kopia.

```cpp
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

[Nowoczesne C++ najlepsze rozwiązania dotyczące wyjątków i obsługi błędów](../cpp/errors-and-exception-handling-modern-cpp.md)<br/>
[Słowa kluczowe](../cpp/keywords-cpp.md)<br/>
[Nieobsługiwane wyjątki języka C++](../cpp/unhandled-cpp-exceptions.md)<br/>
[__uncaught_exception](../c-runtime-library/reference/uncaught-exception.md)
