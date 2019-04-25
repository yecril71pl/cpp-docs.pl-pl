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
ms.openlocfilehash: a55c1f2d5c2e73028b337d17b74fe1280f670707
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62266788"
---
# <a name="try-throw-and-catch-statements-c"></a>Instrukcje try, throw i catch (C++)

Aby zaimplementować obsługę wyjątków w języku C++, należy użyć **spróbuj**, **throw**, i **catch** wyrażenia.

Najpierw za pomocą **spróbuj** blok należy ująć jedną lub więcej instrukcji, które mogą zgłosić wyjątek.

A **throw** wyrażenie informuje, że wyjątkowy warunek — zazwyczaj błąd — wystąpił w **spróbuj** bloku. Można użyć dowolnego typu obiektu jako operandu **throw** wyrażenia. Obiekt ten jest zazwyczaj używany do przekazywania informacji o błędzie. W większości przypadków zaleca się, że używasz [std::exception](../standard-library/exception-class.md) klasy lub jednej z klas pochodnych, które są zdefiniowane w bibliotece standardowej. Jeśli jeden z nich nie jest właściwa, firma Microsoft zaleca wyprowadzenie własne klasy wyjątku z `std::exception`.

Aby obsłużyć wyjątki, które mogą być generowane, zaimplementuj jeden lub więcej **catch** bloki natychmiast po **spróbuj** bloku. Każdy **catch** bloku określa typ wyjątku może obsługiwać.

W tym przykładzie **spróbuj** bloku i jego obsługę. Przyjęto założenie, że `GetNetworkResource()` uzyskuje dane poprzez połączenie sieciowe i że dwa typy wyjątków to klasy zdefiniowane przez użytkownika, które wynikają z `std::exception`. Należy zauważyć, że wyjątki są przechwytywane przez **const** odwoływać w **catch** instrukcji. Firma Microsoft zaleca, aby generować wyjątki przez wartość i przechwytywać przez odniesienie const.

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

Kod po **spróbuj** klauzula jest zabezpieczona sekcja kodu. **Throw** wyrażenie *zgłasza*— czyli generuje — wyjątek. Blok kodu po **catch** klauzula jest program obsługi wyjątków. To jest program obsługi, *przechwytuje* wyjątek, który jest generowany, jeśli typy w **throw** i **catch** wyrażenia są zgodne. Aby uzyskać listę reguł, które określają dopasowanie typu w **catch** bloków, zobacz [jak Catch Blocks are Evaluated](../cpp/how-catch-blocks-are-evaluated-cpp.md). Jeśli **catch** Instrukcja określa wielokropek (...), a nie typ, **catch** blok obsługuje każdy typ wyjątku. Podczas kompilacji z [/eha](../build/reference/eh-exception-handling-model.md) opcji należą wyjątki strukturalne C oraz wyjątki asynchroniczne generowanych przez system lub wygenerowane w aplikacji takich jak pamięci ochrony, dzielenie przez zero i zmiennoprzecinkowych naruszeń . Ponieważ **catch** bloki są przetwarzane w kolejności programu w celu znalezienia pasującego typu, kod obsługi wielokropka musi być ostatnim kodem obsługi skojarzonego **spróbuj** bloku. Użyj `catch(...)` z ostrożnością; nie Zezwalaj programowi na kontynuację, chyba że blok catch wie, jak obsłużyć określony wyjątek, który zostanie przechwycony. Zazwyczaj `catch(...)` blok jest używany do rejestrowania błędów i wykonywania specjalnej operacji czyszczenia, zanim wykonywanie programu zostanie zatrzymane.

A **throw** wyrażenie, które ma nie operandu, ponownie zgłasza aktualnie obsługiwany wyjątek. Zaleca się tę formę podczas ponownego zgłaszania wyjątku, ponieważ pozwala to zachować informacje o polimorficznym typie oryginalnego wyjątku. Takie wyrażenie można używać tylko w **catch** obsługi lub w funkcji, która jest wywoływana z **catch** programu obsługi. Ponownie zgłoszony obiekt wyjątku to oryginalny obiekt wyjątku, a nie kopia.

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

[Obsługa wyjątków języka C++](../cpp/cpp-exception-handling.md)<br/>
[Słowa kluczowe](../cpp/keywords-cpp.md)<br/>
[Nieobsługiwane wyjątki języka C++](../cpp/unhandled-cpp-exceptions.md)<br/>
[__uncaught_exception](../c-runtime-library/reference/uncaught-exception.md)