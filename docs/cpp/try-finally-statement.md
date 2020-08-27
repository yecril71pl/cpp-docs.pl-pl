---
title: try-finally, instrukcja
description: Dokumentacja języka Microsoft C++ do instrukcji obsługi wyjątków strukturalnych __try i __finally.
ms.date: 08/25/2020
f1_keywords:
- __try
- _try
- __leave_cpp
- __leave
- __finally_cpp
- __try_cpp
- __finally
- _finally
helpviewer_keywords:
- __try keyword [C++]
- __finally keyword [C++]
- __leave keyword [C++]
- try-catch keyword [C++], try-finally keyword
- try-finally keyword [C++]
- __finally keyword [C++], try-finally statement syntax
- __leave keyword [C++], try-finally statement
- structured exception handling [C++], try-finally
ms.assetid: 826e0347-ddfe-4f6e-a7bc-0398e0edc7c2
ms.openlocfilehash: edabbbe35c86f0305e31f36584c4dfe01f2f88cd
ms.sourcegitcommit: efc8c32205c9d610f40597556273a64306dec15d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/26/2020
ms.locfileid: "88898647"
---
# <a name="try-finally-statement"></a>`try-finally` Merge

`try-finally`Instrukcja jest rozszerzeniem **specyficznym dla firmy Microsoft** , które obsługuje strukturalną obsługę wyjątków w językach C i C++.

## <a name="syntax"></a>Składnia

Poniższa składnia zawiera opis `try-finally` instrukcji:

```cpp
    // . . .
    __try {
        // guarded code
    }
    __finally {
        // termination code
    }
    // . . .
```

## <a name="grammar"></a>Gramatyka

> *`try-finally-statement`*:\
> &emsp;**`__try`** *`compound-statement`* **`__finally`** *`compound-statement`*

`try-finally`Instrukcja to rozszerzenie firmy Microsoft do języków C i C++, które umożliwiają aplikacjom docelowym wykonywanie kodu czyszczącego w przypadku przerwania wykonywania bloku kodu. Oczyszczanie składa się z takich zadań, jak cofanie alokacji pamięci, zamykanie plików i zwalnianie dojść do plików. `try-finally`Instrukcja jest szczególnie przydatna w przypadku procedur, które mają kilka miejsc, w których wykonywane jest sprawdzenie dla błędu, który może spowodować przedwcześnie powrót z procedury.

Aby uzyskać informacje pokrewne i przykład kodu, zobacz [ `try-except` instrukcja](../cpp/try-except-statement.md). Aby uzyskać więcej informacji o ogólnym obsłudze wyjątków, zobacz [strukturalna obsługa wyjątków](../cpp/structured-exception-handling-c-cpp.md). Aby uzyskać więcej informacji na temat obsługi wyjątków w aplikacjach zarządzanych przy użyciu języka C++/CLI, zobacz [Obsługa wyjątków w `/clr` ](../extensions/exception-handling-cpp-component-extensions.md)temacie.

> [!NOTE]
> Strukturalna obsługa wyjątków działa z Win32 dla plików źródłowych C i C++. Jednakże nie jest specjalnie zaprojektowana dla języka C++. Można zapewnić, że kod będzie bardziej przenośny przy użyciu obsługi wyjątków C++. Ponadto, obsługa wyjątków C++ jest bardziej elastyczna, gdyż może obsługiwać wyjątki dowolnego typu. W przypadku programów C++ zaleca się użycie mechanizmu obsługi wyjątków C++ ([ `try` , `catch` i `throw` ](../cpp/try-throw-and-catch-statements-cpp.md) instrukcji).

Instrukcja złożona po **`__try`** klauzuli jest sekcją chronioną. Złożona instrukcja po **`__finally`** klauzuli to procedura obsługi zakończenia. Program obsługi określa zestaw akcji, które są wykonywane, gdy Sekcja chroniona zostanie zakończona, bez względu na to, czy opuszcza sekcję chronioną przez wyjątek (nietypowe zakończenie) lub według standardu (normalne zakończenie).

Formant dociera do **`__try`** instrukcji przez proste wykonywanie sekwencyjne (przechodzenie). Gdy kontrolka przejdzie do **`__try`** , jego skojarzona procedura obsługi zostanie uaktywniona. Jeśli przepływ sterowania osiągnie koniec bloku try, wykonanie przebiega w następujący sposób:

1. Procedura obsługi zakończenia jest wywoływana.

1. Po zakończeniu procedury obsługi zakończenia wykonywanie jest kontynuowane po **`__finally`** instrukcji. Jednak Sekcja chroniona kończy się (na przykład za pośrednictwem **`goto`** niechronionej treści lub **`return`** instrukcji), program obsługi zakończenia jest wykonywany *przed* przejściem z sekcji chronionej przez przepływ sterowania.

   **`__finally`** Instrukcja nie blokuje wyszukiwania odpowiedniego programu obsługi wyjątków.

Jeśli w bloku wystąpi wyjątek **`__try`** , system operacyjny musi znaleźć procedurę obsługi dla wyjątku lub program zakończy się niepowodzeniem. Jeśli zostanie znaleziona procedura obsługi, wszystkie **`__finally`** bloki są wykonywane i wznawiają wykonywanie w programie obsługi.

Załóżmy na przykład, że seria wywołań funkcji łączy funkcję A z funkcją D, jak pokazano na poniższej ilustracji. Każda funkcja ma jedną procedurę obsługi zakończenia. Jeśli wyjątek jest wywoływany w funkcji D i obsługiwany w, programy obsługi zakończenia są wywoływane w tej kolejności, w której system rozwinięcia stosu: D, C, B.

![Kolejność zakończenia wykonywania programu obsługi&#45;](../cpp/media/vc38cx1.gif "Kolejność zakończenia wykonywania programu obsługi&#45;") <br/>
Kolejność zakończenia — wykonywanie programu obsługi

> [!NOTE]
> Zachowanie funkcji try-finally różni się od innych języków, które obsługują korzystanie z programu **`finally`** , takich jak C#.  Pojedynczy **`__try`** może mieć jedną z nich, ale nie obie, z **`__finally`** i **`__except`** .  Jeśli oba te elementy mają być używane razem, zewnętrzna Instrukcja try-except musi zawierać wewnętrzną instrukcję try-finally.  Reguły określające, kiedy każdy blok wykonuje się również inaczej.

W celu zapewnienia zgodności z poprzednimi wersjami,, **`_try`** **`_finally`** i **`_leave`** są synonimami dla **`__try`** , **`__finally`** i, **`__leave`** Jeśli opcja kompilatora [ `/Za` (Wyłącz rozszerzenia języka)](../build/reference/za-ze-disable-language-extensions.md) jest określona.

## <a name="the-__leave-keyword"></a>Słowo kluczowe __leave

**`__leave`** Słowo kluczowe jest prawidłowe tylko w sekcji chronionej `try-finally` instrukcji i jego efektem jest przejście do końca sekcji chronionej. Wykonywanie jest kontynuowane na pierwszej instrukcji w programie obsługi zakończenia.

**`goto`** Instrukcja może również wyskoczyć z chronionej sekcji, ale obniża wydajność, ponieważ wywołuje odwracanie stosu. **`__leave`** Instrukcja jest bardziej wydajna, ponieważ nie powoduje odwinięcia stosu.

## <a name="abnormal-termination"></a>Nietypowe zakończenie

Kończenie `try-finally` instrukcji przy użyciu funkcji [longjmp](../c-runtime-library/reference/longjmp.md) Run-Time jest uznawane za nietypowe zakończenie. Nie jest to dozwolone, aby przechodzić do **`__try`** instrukcji, ale jest to dozwolone w przypadku przechodzenia z jednego. Wszystkie **`__finally`** instrukcje, które są aktywne między punktem wyjścia (normalne zakończenie **`__try`** bloku) i miejsce docelowe ( **`__except`** blok obsługujący wyjątek), muszą być uruchomione. Jest on nazywany *lokalnym odwinięciem*.

Jeśli **`__try`** blok jest przedwcześnie zakończony z dowolnego powodu, włącznie z skokiem z bloku, system wykonuje skojarzony **`__finally`** blok jako część procesu odwinięcia stosu. W takich przypadkach [`AbnormalTermination`](/windows/win32/Debug/abnormaltermination) Funkcja zwraca w **`true`** przypadku wywołania z **`__finally`** bloku; w przeciwnym razie zwraca **`false`** .

Procedura obsługi zakończenia nie jest wywoływana, jeśli proces zostanie zamknięty w trakcie wykonywania `try-finally` instrukcji.

**ZAKOŃCZENIE specyficzne dla firmy Microsoft**

## <a name="see-also"></a>Zobacz też

[Pisanie programu obsługi zakończenia](../cpp/writing-a-termination-handler.md)<br/>
[Obsługa wyjątków strukturalnych (C/C++)](../cpp/structured-exception-handling-c-cpp.md)<br/>
[Słowa kluczowe](../cpp/keywords-cpp.md)<br/>
[Zakończenie — składnia programu obsługi](/windows/win32/Debug/termination-handler-syntax)
