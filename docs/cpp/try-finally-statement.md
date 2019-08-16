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
ms.openlocfilehash: c26b72f7c675a4130f38c515cf71ecc290328ccc
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69498606"
---
# <a name="try-finally-statement"></a>try-finally — instrukcja

**Microsoft Specific**

Następująca składnia opisuje instrukcję **try-finally** :

> **\_\_spróbował**<br/>
> {<br/>
> &nbsp;&nbsp;&nbsp;&nbsp;chroniony kod<br/>
> }<br/>
> **\_\_Ostateczny**<br/>
> {<br/>
> &nbsp;&nbsp;&nbsp;&nbsp;kod zakończenia<br/>
> }

## <a name="grammar"></a>Gramatyka

*try-finally-Statement*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;Instrukcja try złożonej *instrukcji*  **\_ \_"finally** "  **\_ \_**

Instrukcja **try-finally** to rozszerzenie firmy Microsoft do języków C i C++ , które umożliwiają aplikacjom docelowym wykonywanie kodu czyszczącego w przypadku przerwania wykonywania bloku kodu. Oczyszczanie składa się z takich zadań, jak cofanie alokacji pamięci, zamykanie plików i zwalnianie dojść do plików. Instrukcja **try-finally** jest szczególnie przydatna w przypadku procedur, które mają kilka miejsc, w których wystąpiło sprawdzenie błędu, który może spowodować przedwcześnie powrót z procedury.

Aby uzyskać informacje pokrewne i przykład kodu, zobacz [Instrukcja try-except](../cpp/try-except-statement.md). Aby uzyskać więcej informacji o ogólnym obsłudze wyjątków, zobacz [strukturalna obsługa wyjątków](../cpp/structured-exception-handling-c-cpp.md). Aby uzyskać więcej informacji na temat obsługi wyjątków w zarządzanych C++aplikacjach za pomocą/CLI, zobacz [Obsługa wyjątków w obszarze/CLR](../extensions/exception-handling-cpp-component-extensions.md).

> [!NOTE]
> Strukturalna obsługa wyjątków działa z Win32 dla plików źródłowych C i C++. Jednakże nie jest specjalnie zaprojektowana dla języka C++. Można zapewnić, że kod będzie bardziej przenośny przy użyciu obsługi wyjątków C++. Ponadto, obsługa wyjątków C++ jest bardziej elastyczna, gdyż może obsługiwać wyjątki dowolnego typu. W C++ przypadku programów zaleca się użycie mechanizmu obsługi C++ wyjątków (instrukcje[try, catch i throw](../cpp/try-throw-and-catch-statements-cpp.md) ).

Instrukcja złożona po klauzuli **__try** jest sekcją chronioną. Instrukcja złożona po klauzuli **__finally** jest programem obsługi zakończenia. Procedura obsługi określa zestaw akcji, które są wykonywane, gdy Sekcja chroniona zostanie zakończona, bez względu na to, czy sekcja chroniona została zakończona przez wyjątek (nietypowe zakończenie), czy przez Standard (normalne zakończenie).

Kontrolka osiągnie instrukcję **__try** przez proste wykonywanie sekwencyjne (przechodzenie przez). Gdy kontrolka przejdzie do **__try**, jego skojarzona procedura obsługi zostanie uaktywniona. Jeśli przepływ sterowania osiągnie koniec bloku try, wykonanie przebiega w następujący sposób:

1. Procedura obsługi zakończenia jest wywoływana.

1. Po zakończeniu procedury obsługi zakończenia wykonywanie jest kontynuowane po instrukcji **__finally** . Bez względu na to, jak zakończył się sekcja chroniona (na przykład za pomocą instrukcji **goto** z chronionej treści lub instrukcja **Return** ), program obsługi zakończenia jest wykonywany *przed* przeniesieniem przepływu sterowania z sekcji chronionej.

   Instrukcja **__finally** nie blokuje wyszukiwania odpowiedniego programu obsługi wyjątków.

Jeśli wystąpi wyjątek w bloku **__try** , system operacyjny musi znaleźć procedurę obsługi dla wyjątku lub program zakończy się niepowodzeniem. Jeśli zostanie znaleziona procedura obsługi, wszystkie bloki **__finally** są wykonywane i wznawiają wykonywanie w programie obsługi.

Załóżmy na przykład, że seria wywołań funkcji łączy funkcję A z funkcją D, jak pokazano na poniższej ilustracji. Każda funkcja ma jedną procedurę obsługi zakończenia. Jeśli wyjątek jest wywoływany w funkcji D i obsługiwany w, programy obsługi zakończenia są wywoływane w tej kolejności, w jakiej system wychodzi ze stosu: D, C, B.

![Kolejność&#45;]wykonywania procedury obsługi zakończenia(../cpp/media/vc38cx1.gif "wykonania&#45;") procedury obsługi zakończenia <br/>
Kolejność zakończenia — wykonywanie programu obsługi

> [!NOTE]
> Zachowanie try-finally różni się od innych języków, które obsługują korzystanie z **finally**, takich jak C#.  Pojedynczy **__try** może mieć jedną, ale nie obie wartości **__finally** i **__except**.  Jeśli oba te elementy mają być używane razem, zewnętrzna Instrukcja try-except musi zawierać wewnętrzną instrukcję try-finally.  Reguły określające, kiedy każdy blok wykonuje się również inaczej.

Aby zapewnić zgodność z poprzednimi wersjami, **_try**, **_finally**i **_leave** są synonimami dla **__try**, **__finally**i **__leave** , chyba że opcja kompilatora [/za \(wyłączanie rozszerzeń języka) ](../build/reference/za-ze-disable-language-extensions.md)jest określony.

## <a name="the-__leave-keyword"></a>Słowo kluczowe __leave

Słowo kluczowe **__leave** jest prawidłowe tylko w sekcji chronionej instrukcji **try-finally** , a jej efektem jest przechodzenie do końca sekcji chronionej. Wykonywanie jest kontynuowane na pierwszej instrukcji w programie obsługi zakończenia.

Instrukcja **goto** może również wyskoczyć z chronionej sekcji, ale obniża wydajność, ponieważ wywołuje odwracanie stosu. Instrukcja **__leave** jest wydajniejsza, ponieważ nie powoduje odwinięcia stosu.

## <a name="abnormal-termination"></a>Nietypowe zakończenie

Kończenie instrukcji **try-finally** przy użyciu funkcji [longjmp](../c-runtime-library/reference/longjmp.md) Run-Time jest uznawane za nietypowe zakończenie. Przechodzenie do instrukcji **__try** jest niedozwolone, ale z tego względu można przejść z jednego. Wszystkie instrukcje **__finally** , które są aktywne między punktem wyjścia (normalne zakończenie bloku **__try** ) i miejscem docelowym (blok **__except** , który obsługuje wyjątek) musi być uruchomiony. Jest to nazywane lokalnym odwinięciem.

Jeśli blok **try** jest przedwcześnie zakończony z dowolnego powodu, włącznie z skokiem z bloku, system wykonuje skojarzony blok **finally** jako część procesu odwinięcia stosu. W takich przypadkach funkcja [AbnormalTermination](/windows/win32/Debug/abnormaltermination) zwraca **wartość true** , jeśli wywoływana z wewnątrz bloku **finally** ; w przeciwnym razie zwraca **wartość false**.

Procedura obsługi zakończenia nie jest wywoływana, jeśli proces zostanie zamknięty w trakcie wykonywania instrukcji **try-finally** .

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz także

[Pisanie programu obsługi zakończenia](../cpp/writing-a-termination-handler.md)<br/>
[Obsługa wyjątków strukturalnych (C/C++)](../cpp/structured-exception-handling-c-cpp.md)<br/>
[Słowa kluczowe](../cpp/keywords-cpp.md)<br/>
[Zakończenie — składnia programu obsługi](/windows/win32/Debug/termination-handler-syntax)