---
title: try-finally — instrukcja (C)
ms.date: 11/04/2016
helpviewer_keywords:
- try-finally keyword [C]
- __finally keyword [C], try-finally statement syntax
- __finally keyword [C]
- structured exception handling, try-finally
ms.assetid: 514400c1-c322-4bf3-9e48-3047240b8a82
ms.openlocfilehash: 61a6a9edd9faaf8afb06bb7bfdc619cddde3e6fc
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81349613"
---
# <a name="try-finally-statement-c"></a>try-finally — instrukcja (C)

**Specyficzne dla firmy Microsoft**

`try-finally` Instrukcja to rozszerzenie firmy Microsoft do języka C, który umożliwia aplikacjom zagwarantowanie wykonania kodu czyszczącego w przypadku przerwania wykonywania bloku kodu. Oczyszczanie składa się z takich zadań, jak cofanie alokacji pamięci, zamykanie plików i zwalnianie dojść do plików. `try-finally` Instrukcja jest szczególnie przydatna w przypadku procedur, które mają kilka miejsc, w których wykonywane jest sprawdzenie dla błędu, który może spowodować przedwcześnie powrót z procedury.

*try-finally-Statement*: **__try**  *złożonej instrukcji*

**__finally**  *instrukcji złożonej*

Instrukcja złożona po `__try` klauzuli jest sekcją chronioną. Złożona instrukcja po `__finally` klauzuli to procedura obsługi zakończenia. Program obsługi określa zestaw akcji, które są wykonywane, gdy Sekcja chroniona zostanie zakończona, niezależnie od tego, czy chroniona sekcja została zakończona przez wyjątek (nietypowe zakończenie) lub według standardu (normalne zakończenie).

Formant dociera do `__try` instrukcji przez proste wykonywanie sekwencyjne (przechodzenie). Gdy kontrolka przechodzi `__try` do instrukcji, jej skojarzony program obsługi zostanie uaktywniony. Wykonanie przebiega w następujący sposób:

1. Sekcja chroniona jest wykonywana.

1. Procedura obsługi zakończenia jest wywoływana.

1. Po zakończeniu procedury obsługi zakończenia wykonywanie jest kontynuowane po `__finally` instrukcji. Bez względu na to, jak sekcja chroniona kończy się (na przykład `goto` za pomocą instrukcji z chronionej treścią lub za `return` pośrednictwem instrukcji), program obsługi zakończenia jest wykonywany przed przeniesieniem przepływu sterowania z sekcji chronionej.

`__leave` Słowo kluczowe jest prawidłowe w bloku `try-finally` instrukcji. Efekt `__leave` ma przeskoczyć do końca `try-finally` bloku. Program obsługi zakończenia jest natychmiast wykonywany. Mimo że `goto` instrukcja może służyć do osiągnięcia tego samego wyniku, `goto` instrukcja powoduje odwinięcie stosu. Instrukcja `__leave` jest wydajniejsza, ponieważ nie obejmuje odwinięcia stosu.

Kończenie `try-finally` instrukcji przy użyciu `return` instrukcji lub funkcji `longjmp` Run-Time jest uznawane za nietypowe zakończenie. Przechodzenie do `__try` instrukcji nie jest dozwolone, ale istnieje możliwość wychodzenia z jednego. Należy `__finally` uruchomić wszystkie instrukcje, które są aktywne między punktem wyjścia a miejscem docelowym. Jest to tzw. "lokalne rozwinięcie".

Procedura obsługi zakończenia nie jest wywoływana, jeśli proces zostanie zamknięty podczas wykonywania `try-finally` instrukcji.

> [!NOTE]
> Strukturalna obsługa wyjątków współpracuje z plikami źródłowymi C i C++. Jednakże nie jest specjalnie zaprojektowana dla języka C++. Można zapewnić, że kod będzie bardziej przenośny przy użyciu obsługi wyjątków C++. Ponadto mechanizm obsługi wyjątków C++ jest znacznie bardziej elastyczny, dzięki czemu może obsługiwać wyjątki dowolnego typu.

> [!NOTE]
> W przypadku programów C++, obsługa wyjątków C++ powinna być używana zamiast strukturalnej obsługi wyjątków. Aby uzyskać więcej informacji, zobacz [Obsługa wyjątków](../cpp/exception-handling-in-visual-cpp.md) w *dokumentacji języka C++*.

Zobacz przykład dla [instrukcji try-except](../c-language/try-except-statement-c.md) , aby zobaczyć, jak działa `try-finally` instrukcja.

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz też

[try-finally, instrukcja](../cpp/try-finally-statement.md)
