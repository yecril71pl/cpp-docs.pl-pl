---
title: try-finally — instrukcja (C)
ms.date: 11/04/2016
helpviewer_keywords:
- try-finally keyword [C]
- __finally keyword [C], try-finally statement syntax
- __finally keyword [C]
- structured exception handling, try-finally
ms.assetid: 514400c1-c322-4bf3-9e48-3047240b8a82
ms.openlocfilehash: 82cc5ffa3f50196fc5f518b8bb5b2080ff14fd8d
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/12/2019
ms.locfileid: "56151835"
---
# <a name="try-finally-statement-c"></a>try-finally — instrukcja (C)

**Microsoft Specific**

`try-finally` Instrukcja jest rozszerzeniem firmy Microsoft dla języka C, umożliwiającą aplikacjom gwarantuje wykonywanie czyszczenia kodu, gdy działanie zostanie zakłócone wykonanie bloku kodu. Oczyszczanie składa się z zadania, takie jak cofanie przydziału pamięci, zamykanie plików i zwalniania dojścia do plików. `try-finally` Instrukcji jest szczególnie przydatne dla procedur, które mają w kilku miejscach, w którym dokonuje błędu, który może spowodować przedwczesne zwracają rutynowych.

*Spróbuj na koniec instrukcji*: **__try** *compound-statement* 

**__finally** *compound-statement* 

Instrukcja złożona po `__try` klauzula jest sekcja chroniona. Instrukcja złożona po `__finally` klauzula jest programu obsługi zakończenia. Kod obsługi wyjątku określa zestaw akcji, które są wykonywane podczas Sekcja chroniona jest został zakończony, czy sekcja chroniona jest został zakończony przez wyjątek (Nienormalne zakończenie) lub standardowy poniżej (normalne zakończenie).

Kontrola osiąga `__try` oświadczenie proste wykonywania sekwencyjnego (poniżej). Kiedy sterowania przechodzi `__try` instrukcji, jego skojarzony program obsługi stanie się aktywny. Wykonanie działa w następujący sposób:

1. Sekcja chroniona jest wykonywana.

1. Program obsługi przerwania jest wywoływana.

1. Po zakończeniu działania programu obsługi zakończenia, wykonywanie jest kontynuowane po `__finally` instrukcji. Niezależnie od tego, jak chronionych końce sekcji (na przykład za pośrednictwem `goto` instrukcji z treści chronionych lub za pośrednictwem `return` instrukcji), program obsługi przerwania jest wykonywany przed przepływ sterowania przenosi poza sekcję chronioną.

`__leave` — Słowo kluczowe jest prawidłowy w ramach `try-finally` blok instrukcji. Efekt `__leave` jest przeskoczenie do końca `try-finally` bloku. Program obsługi przerwania jest wykonywany, natychmiast. Mimo że `goto` instrukcja może być używana, aby osiągnąć ten sam wynik `goto` instrukcja powoduje odwrócenie stosu. `__leave` Instrukcja jest bardziej wydajne, ponieważ nie wymaga wykonywania operacji odwijania stosu.

Kończenie `try-finally` przy użyciu instrukcji `return` instrukcji lub `longjmp` funkcji środowiska uruchomieniowego jest uznawany za Nienormalne zakończenie. Nie jest dozwolone realizowanie `__try` instrukcji, ale informacje prawne wyjście z niej. Wszystkie `__finally` instrukcji, które są aktywni w okresie między punktem wyjścia i miejsce docelowe musi być uruchamiane. Jest to nazywane "rozwinięcie lokalne".

Program obsługi przerwania nie jest wywoływana, gdy proces jest zabite podczas wykonywania `try-finally` instrukcji.

> [!NOTE]
>  Strukturalna obsługa wyjątków działa z plikami źródłowymi C i C++. Jednakże nie jest specjalnie zaprojektowana dla języka C++. Można zapewnić, że kod będzie bardziej przenośny przy użyciu obsługi wyjątków C++. Ponadto mechanizm obsługi wyjątków C++ jest bardziej elastyczne, gdyż może obsługiwać wyjątki dowolnego typu.

> [!NOTE]
>  Dla programów C++ Obsługa wyjątków języka C++ powinny być używane zamiast strukturalna Obsługa wyjątków. Aby uzyskać więcej informacji, zobacz [wyjątków](../cpp/exception-handling-in-visual-cpp.md) w *C++ Language Reference*.

Zobacz przykład dla [spróbuj-except, instrukcja](../c-language/try-except-statement-c.md) aby zobaczyć, jak `try-finally` instrukcji działa.

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz także

[try-finally, instrukcja](../cpp/try-finally-statement.md)
