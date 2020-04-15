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

Instrukcja `try-finally` jest rozszerzenie firmy Microsoft do języka C, który umożliwia aplikacjom, aby zagwarantować wykonanie kodu oczyszczania, gdy wykonanie bloku kodu jest przerwana. Oczyszczanie składa się z takich zadań, jak przydzielanie pamięci, zamykanie plików i zwalnianie uchwytów plików. Instrukcja `try-finally` jest szczególnie przydatna w przypadku procedur, które mają kilka miejsc, w których jest sprawdzane pod kątem błędu, który może spowodować przedwczesny powrót z procedury.

*try-finally-statement*: **__try**  *złożone oświadczenie*

**__finally**  *zestawienie złożone*

Instrukcja złożona `__try` po klauzuli jest sekcją chroniona. Instrukcja złożona `__finally` po klauzuli jest program obsługi zakończenia. Program obsługi określa zestaw akcji, które są wykonywane po zamknięciu sekcji strzeżonej, niezależnie od tego, czy sekcja strzeżona jest zamykana przez wyjątek (nieprawidłowe zakończenie), czy przez standardowe przechodzenie (normalne zakończenie).

Formant osiąga `__try` instrukcję przez proste wykonanie sekwencyjne (spadek przez). Gdy formant `__try` wprowadza instrukcję, jego skojarzony program obsługi staje się aktywny. Wykonanie przebiega w następujący sposób:

1. Sekcja chroniona jest wykonywana.

1. Wywoływany jest program obsługi zakończenia.

1. Po zakończeniu obsługi zakończenia wykonywanie jest `__finally` kontynuowane po instrukcji. Niezależnie od tego, jak kończy się sekcja `goto` strzeżona (na przykład za `return` pomocą instrukcji z chronionego obiektu lub za pomocą instrukcji), program obsługi zakończenia jest wykonywany przed przeniesieniem przepływu sterowania z sekcji strzeżonej.

Słowo `__leave` kluczowe jest `try-finally` prawidłowe w bloku instrukcji. Efektem `__leave` jest przeskoczyć do `try-finally` końca bloku. Program obsługi zakończenia jest natychmiast wykonywany. Chociaż `goto` instrukcja może służyć do osiągnięcia `goto` tego samego wyniku, instrukcja powoduje odwijania stosu. Instrukcja `__leave` jest bardziej wydajne, ponieważ nie obejmuje odwijania stosu.

Zamykanie `try-finally` instrukcji przy `return` użyciu `longjmp` instrukcji lub funkcji czasu wykonywania jest uważane za nieprawidłowe zakończenie. To jest nielegalne, `__try` aby przejść do oświadczenia, ale legalne wyskoczyć z jednego. Wszystkie `__finally` instrukcje, które są aktywne między punktem wyjścia a miejscem docelowym, muszą być uruchamiane. To się nazywa "lokalne unwind".

Program obsługi zakończenia nie jest wywoływana, jeśli `try-finally` proces zostanie zabity podczas wykonywania instrukcji.

> [!NOTE]
> Obsługa wyjątków strukturalnych działa z plikami źródłowymi języka C i C++. Jednakże nie jest specjalnie zaprojektowana dla języka C++. Można zapewnić, że kod będzie bardziej przenośny przy użyciu obsługi wyjątków C++. Ponadto mechanizm obsługi wyjątków C++ jest znacznie bardziej elastyczny, ponieważ może obsługiwać wyjątki dowolnego typu.

> [!NOTE]
> W przypadku programów C++ należy używać obsługi wyjątków języka C++ zamiast obsługi wyjątków strukturalnych. Aby uzyskać więcej informacji, zobacz [Obsługa wyjątków](../cpp/exception-handling-in-visual-cpp.md) w *odwołaniu do języka języka języka C++*.

Zobacz przykład [instrukcji try-except,](../c-language/try-except-statement-c.md) aby `try-finally` zobaczyć, jak działa instrukcja.

**ZAKOŃCZ Specyficzne dla firmy Microsoft**

## <a name="see-also"></a>Zobacz też

[try-finally, instrukcja](../cpp/try-finally-statement.md)
