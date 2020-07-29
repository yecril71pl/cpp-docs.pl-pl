---
title: try-finally — instrukcja
ms.date: 11/19/2018
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
ms.openlocfilehash: 6234e8a2d2c18177a1e66475fff850c76f7ef73e
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87227078"
---
# <a name="try-finally-statement"></a>try-finally — instrukcja

**Specyficzne dla firmy Microsoft**

Następująca składnia opisuje instrukcję **try-finally** :

> **\_\_try**<br/>
> {\
> &nbsp;&nbsp;&nbsp;&nbsp;chroniony kod \
> }\
> **\_\_Ostateczny**\
> {\
> &nbsp;&nbsp;&nbsp;&nbsp;kod zakończenia \
> }

## <a name="grammar"></a>Gramatyka

*try-finally-Statement*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*instrukcja* ** \_ \_ try** złożonej *instrukcji* " ** \_ \_ finally** "

Instrukcja **try-finally** to rozszerzenie firmy Microsoft do języków C i C++, które umożliwiają aplikacjom docelowym wykonywanie kodu czyszczącego w przypadku przerwania wykonywania bloku kodu. Oczyszczanie składa się z takich zadań, jak cofanie alokacji pamięci, zamykanie plików i zwalnianie dojść do plików. Instrukcja **try-finally** jest szczególnie przydatna w przypadku procedur, które mają kilka miejsc, w których wystąpiło sprawdzenie błędu, który może spowodować przedwcześnie powrót z procedury.

Aby uzyskać informacje pokrewne i przykład kodu, zobacz [Instrukcja try-except](../cpp/try-except-statement.md). Aby uzyskać więcej informacji o ogólnym obsłudze wyjątków, zobacz [strukturalna obsługa wyjątków](../cpp/structured-exception-handling-c-cpp.md). Aby uzyskać więcej informacji na temat obsługi wyjątków w aplikacjach zarządzanych przy użyciu języka C++/CLI, zobacz [Obsługa wyjątków w obszarze/CLR](../extensions/exception-handling-cpp-component-extensions.md).

> [!NOTE]
> Strukturalna obsługa wyjątków działa z Win32 dla plików źródłowych C i C++. Jednakże nie jest specjalnie zaprojektowana dla języka C++. Można zapewnić, że kod będzie bardziej przenośny przy użyciu obsługi wyjątków C++. Ponadto, obsługa wyjątków C++ jest bardziej elastyczna, gdyż może obsługiwać wyjątki dowolnego typu. W przypadku programów C++ zaleca się używanie mechanizmu obsługi wyjątków C++ (instrukcje[try, catch i throw](../cpp/try-throw-and-catch-statements-cpp.md) ).

Instrukcja złożona po klauzuli **__try** jest sekcją chronioną. Złożona instrukcja po **`__finally`** klauzuli to procedura obsługi zakończenia. Procedura obsługi określa zestaw akcji, które są wykonywane, gdy Sekcja chroniona zostanie zakończona, bez względu na to, czy sekcja chroniona została zakończona przez wyjątek (nietypowe zakończenie), czy przez Standard (normalne zakończenie).

Formant dociera do instrukcji **__try** przez proste wykonywanie sekwencyjne (przechodzenie). Gdy kontrolka przejdzie do **__try**, jego skojarzona procedura obsługi zostanie uaktywniona. Jeśli przepływ sterowania osiągnie koniec bloku try, wykonanie przebiega w następujący sposób:

1. Procedura obsługi zakończenia jest wywoływana.

1. Po zakończeniu procedury obsługi zakończenia wykonywanie jest kontynuowane po **`__finally`** instrukcji. Bez względu na to, jak sekcja chroniona kończy się (na przykład za pośrednictwem **`goto`** niechronionej treści lub **`return`** instrukcji), program obsługi zakończenia jest wykonywany *przed* przejściem z sekcji chronionej przez przepływ sterowania.

   **`__finally`** Instrukcja nie blokuje wyszukiwania odpowiedniego programu obsługi wyjątków.

Jeśli wystąpi wyjątek w bloku **__try** , system operacyjny musi znaleźć procedurę obsługi dla wyjątku lub program zakończy się niepowodzeniem. Jeśli zostanie znaleziona procedura obsługi, wszystkie **`__finally`** bloki są wykonywane i wznawiają wykonywanie w programie obsługi.

Załóżmy na przykład, że seria wywołań funkcji łączy funkcję A z funkcją D, jak pokazano na poniższej ilustracji. Każda funkcja ma jedną procedurę obsługi zakończenia. Jeśli wyjątek jest wywoływany w funkcji D i obsługiwany w, programy obsługi zakończenia są wywoływane w tej kolejności, w której system rozwinięcia stosu: D, C, B.

![Kolejność zakończenia wykonywania programu obsługi&#45;](../cpp/media/vc38cx1.gif "Kolejność zakończenia wykonywania programu obsługi&#45;") <br/>
Kolejność zakończenia — wykonywanie programu obsługi

> [!NOTE]
> Zachowanie try-finally różni się od innych języków, które obsługują korzystanie z **finally**, takich jak C#.  Pojedynczy **__try** może mieć jeden, ale nie oba, z **`__finally`** i **`__except`** .  Jeśli oba te elementy mają być używane razem, zewnętrzna Instrukcja try-except musi zawierać wewnętrzną instrukcję try-finally.  Reguły określające, kiedy każdy blok wykonuje się również inaczej.

W celu zapewnienia zgodności z poprzednimi wersjami, **_try**, **_finally**i **_leave** są synonimami dla **__try**, **`__finally`** i, **`__leave`** chyba że opcja kompilatora [/za \( wyłączenie rozszerzeń języka)](../build/reference/za-ze-disable-language-extensions.md) jest określona.

## <a name="the-__leave-keyword"></a>Słowo kluczowe __leave

**`__leave`** Słowo kluczowe jest prawidłowe tylko w sekcji chronionej instrukcji **try-finally** i ma przechodzenie do końca sekcji chronionej. Wykonywanie jest kontynuowane na pierwszej instrukcji w programie obsługi zakończenia.

**`goto`** Instrukcja może również wyskoczyć z chronionej sekcji, ale obniża wydajność, ponieważ wywołuje odwracanie stosu. **`__leave`** Instrukcja jest bardziej wydajna, ponieważ nie powoduje odwinięcia stosu.

## <a name="abnormal-termination"></a>Nietypowe zakończenie

Kończenie instrukcji **try-finally** przy użyciu funkcji [longjmp](../c-runtime-library/reference/longjmp.md) Run-Time jest uznawane za nietypowe zakończenie. Przechodzenie do instrukcji **__try** nie jest dozwolone, ale w celu wychodzenia z jednej z nich. Wszystkie **`__finally`** instrukcje, które są aktywne między punktem wyjścia (normalne zakończenie bloku **__try** ) i miejsce docelowe ( **`__except`** blok obsługujący wyjątek), muszą być uruchomione. Jest to nazywane lokalnym odwinięciem.

Jeśli **`try`** blok jest przedwcześnie zakończony z dowolnego powodu, włącznie z skokiem z bloku, system wykonuje skojarzony blok **finally** jako część procesu odwinięcia stosu. W takich przypadkach funkcja [AbnormalTermination](/windows/win32/Debug/abnormaltermination) zwraca wartość, **`true`** Jeśli wywoływana z wewnątrz bloku **finally** ; w przeciwnym razie zwraca wartość **`false`** .

Procedura obsługi zakończenia nie jest wywoływana, jeśli proces zostanie zamknięty w trakcie wykonywania instrukcji **try-finally** .

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz także

[Pisanie programu obsługi zakończenia](../cpp/writing-a-termination-handler.md)<br/>
[Obsługa wyjątków strukturalnych (C/C++)](../cpp/structured-exception-handling-c-cpp.md)<br/>
[Słowa kluczowe](../cpp/keywords-cpp.md)<br/>
[Zakończenie — składnia programu obsługi](/windows/win32/Debug/termination-handler-syntax)
