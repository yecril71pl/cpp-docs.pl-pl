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
ms.openlocfilehash: 4108d24b2c285b9d55d514dffae7b2efda1b3f86
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87227065"
---
# <a name="try-throw-and-catch-statements-c"></a>Instrukcje try, throw i catch (C++)

Aby zaimplementować obsługę wyjątków w języku C++, należy **`try`** użyć **`throw`** wyrażeń, i **`catch`** .

Najpierw należy użyć **`try`** bloku, aby ująć jedną lub więcej instrukcji, które mogą zgłosić wyjątek.

**`throw`** Wyrażenie sygnalizuje, że wyjątkowe warunki — często, błąd — wystąpił w **`try`** bloku. Można użyć obiektu dowolnego typu jako operandu **`throw`** wyrażenia. Obiekt ten jest zazwyczaj używany do przekazywania informacji o błędzie. W większości przypadków zaleca się użycie klasy [std:: Exception](../standard-library/exception-class.md) lub jednej z klas pochodnych, które są zdefiniowane w standardowej bibliotece. Jeśli jeden z tych elementów nie jest odpowiedni, zalecamy uzyskanie własnej klasy wyjątków z `std::exception` .

Aby obsłużyć wyjątki, które mogą być zgłaszane, zaimplementuj jeden lub więcej **`catch`** bloków bezpośrednio po **`try`** bloku. Każdy **`catch`** blok określa typ wyjątku, który może obsłużyć.

Ten przykład pokazuje **`try`** blok i jego programy obsługi. Załóżmy, że `GetNetworkResource()` uzyskuje dane za pośrednictwem połączenia sieciowego i że dwa typy wyjątków są klasami zdefiniowanymi przez użytkownika, które pochodzą od `std::exception` . Należy zauważyć, że wyjątki są przechwytywane przez **`const`** odwołanie w **`catch`** instrukcji. Firma Microsoft zaleca, aby generować wyjątki przez wartość i przechwytywać przez odniesienie const.

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

Kod po **`try`** klauzuli jest chronioną sekcją kodu. **`throw`** Wyrażenie *zgłasza*— to znaczy, podnosi — wyjątek. Blok kodu po **`catch`** klauzuli jest programem obsługi wyjątków. Jest to procedura obsługi, która *przechwytuje* wyjątek zgłaszany, jeśli typy w **`throw`** **`catch`** wyrażeniach i są zgodne. Aby uzyskać listę reguł rządzących dopasowaniem typu w **`catch`** blokach, zobacz [jak są oceniane bloki catch](../cpp/how-catch-blocks-are-evaluated-cpp.md). Jeśli **`catch`** instrukcja określa wielokropek (...) zamiast typu, **`catch`** blok obsługuje każdy typ wyjątku. Podczas kompilowania z użyciem opcji [/EHa](../build/reference/eh-exception-handling-model.md) mogą to być wyjątki strukturalne C i generowane przez system lub generowane przez aplikacje wyjątki asynchroniczne, takie jak ochrona pamięci, dzielenie przez zero i naruszenia zmiennoprzecinkowe. Ponieważ **`catch`** bloki są przetwarzane w kolejności programu w celu znalezienia zgodnego typu, program obsługi wielokropka musi być ostatnim programem obsługi dla skojarzonego **`try`** bloku. Należy używać `catch(...)` z zachowaniem ostrożności; nie Zezwalaj programowi na kontynuowanie, chyba że blok catch wie, jak obsłużyć konkretny wyjątek, który jest przechwytywany. Zazwyczaj `catch(...)` blok jest używany do rejestrowania błędów i wykonywania specjalnego oczyszczania przed zatrzymaniem wykonywania programu.

**`throw`** Wyrażenie, które nie ma operandu, powoduje ponowne zgłoszenie aktualnie obsługiwanego wyjątku. Zaleca się tę formę podczas ponownego zgłaszania wyjątku, ponieważ pozwala to zachować informacje o polimorficznym typie oryginalnego wyjątku. Takie wyrażenie powinno być używane tylko w programie **`catch`** obsługi lub w funkcji, która jest wywoływana z **`catch`** procedury obsługi. Ponownie zgłoszony obiekt wyjątku to oryginalny obiekt wyjątku, a nie kopia.

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

## <a name="see-also"></a>Zobacz także

[Nowoczesne najlepsze rozwiązania w języku C++ dotyczące wyjątków i obsługi błędów](../cpp/errors-and-exception-handling-modern-cpp.md)<br/>
[Słowa kluczowe](../cpp/keywords-cpp.md)<br/>
[Nieobsłużone wyjątki C++](../cpp/unhandled-cpp-exceptions.md)<br/>
[__uncaught_exception](../c-runtime-library/reference/uncaught-exception.md)
