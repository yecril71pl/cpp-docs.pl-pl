---
title: try-finally, instrukcja (C)
description: Microsoft C/C++ implementuje obsługę wyjątków strukturalnych (SEH) przy użyciu rozszerzenia języka instrukcji try-finally.
ms.date: 08/24/2020
helpviewer_keywords:
- try-finally keyword [C]
- __finally keyword [C], try-finally statement syntax
- __finally keyword [C]
- structured exception handling, try-finally
ms.assetid: 514400c1-c322-4bf3-9e48-3047240b8a82
ms.openlocfilehash: 6f9cf901ed0a82b355880225c902ec4fc3e1082b
ms.sourcegitcommit: efc8c32205c9d610f40597556273a64306dec15d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/26/2020
ms.locfileid: "88898706"
---
# <a name="try-finally-statement-c"></a>try-finally, instrukcja (C)

**specyficzne dla firmy Microsoft**

`try-finally`Instrukcja to rozszerzenie firmy Microsoft do języka C, który umożliwia aplikacjom zagwarantowanie wykonania kodu czyszczącego w przypadku przerwania wykonywania bloku kodu. Oczyszczanie składa się z takich zadań, jak cofanie alokacji pamięci, zamykanie plików i zwalnianie dojść do plików. `try-finally`Instrukcja jest szczególnie przydatna w przypadku procedur, które mają kilka miejsc, w których wykonywane jest sprawdzenie dla błędu, który może spowodować przedwcześnie powrót z procedury.

> *`try-finally-statement`*:\
> &emsp;**`__try`** *`compound-statement`* **`__finally`** *`compound-statement`*

Instrukcja złożona po **`__try`** klauzuli jest sekcją chronioną. Złożona instrukcja po **`__finally`** klauzuli to procedura obsługi zakończenia. Program obsługi określa zestaw akcji, które są wykonywane, gdy Sekcja chroniona zostanie zakończona. Nie ma znaczenia, czy sekcja chroniona została zakończona przez wyjątek (nietypowe zakończenie) lub przez standardową wartość (normalne zakończenie).

Formant dociera do **`__try`** instrukcji przez proste wykonywanie sekwencyjne (przechodzenie). Gdy kontrolka przechodzi do **`__try`** instrukcji, jej skojarzony program obsługi zostanie uaktywniony. Wykonanie przebiega w następujący sposób:

1. Sekcja chroniona jest wykonywana.

1. Procedura obsługi zakończenia jest wywoływana.

1. Po zakończeniu procedury obsługi zakończenia wykonywanie jest kontynuowane po **`__finally`** instrukcji. Niezależnie od tego, jak sekcja chroniona kończy się (na przykład za pomocą **`goto`** instrukcji z chronionej treścią lub za pośrednictwem **`return`** instrukcji), program obsługi zakończenia jest wykonywany przed przeniesieniem przepływu sterowania z sekcji chronionej.

**`__leave`** Słowo kluczowe jest prawidłowe w `try-finally` bloku instrukcji. Efekt **`__leave`** ma przeskoczyć do końca `try-finally` bloku. Program obsługi zakończenia jest natychmiast wykonywany. Mimo że **`goto`** instrukcja może służyć do osiągnięcia tego samego wyniku, **`goto`** instrukcja powoduje odwinięcie stosu. **`__leave`** Instrukcja jest bardziej wydajna, ponieważ nie obejmuje odwinięcia stosu.

Kończenie `try-finally` instrukcji przy użyciu **`return`** instrukcji lub `longjmp` funkcji run-time jest uznawane za nietypowe zakończenie. Przechodzenie do instrukcji nie jest dozwolone **`__try`** , ale z tego względu można przejść z jednego. **`__finally`** Należy uruchomić wszystkie instrukcje, które są aktywne między punktem wyjścia a miejscem docelowym. Jest on nazywany *lokalnym odwinięciem*.

Procedura obsługi zakończenia nie jest wywoływana, jeśli proces zostanie zamknięty podczas wykonywania `try-finally` instrukcji.

> [!NOTE]
> Strukturalna obsługa wyjątków współpracuje z plikami źródłowymi C i C++. Nie jest to jednak przeznaczone specjalnie dla języka C++. W przypadku przenośnych programów C++ obsługa wyjątków C++ powinna być używana zamiast strukturalnej obsługi wyjątków. Ponadto mechanizm obsługi wyjątków C++ jest znacznie bardziej elastyczny, dzięki czemu może obsługiwać wyjątki dowolnego typu. Aby uzyskać więcej informacji, zobacz [Obsługa wyjątków](../cpp/exception-handling-in-visual-cpp.md) w *dokumentacji języka C++*.

Zobacz przykład [ `try-except` instrukcji](../c-language/try-except-statement-c.md) , aby zobaczyć, jak `try-finally` działa instrukcja.

**ZAKOŃCZENIE specyficzne dla firmy Microsoft**

## <a name="see-also"></a>Zobacz też

[`try-finally` Instrukcja (C++)](../cpp/try-finally-statement.md)
