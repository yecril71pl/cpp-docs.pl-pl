---
title: Obsługa wyjątków strukturalnych (C/C++)
description: Przegląd strukturalnej obsługi wyjątków w Microsoft C/C++.
ms.date: 08/24/2020
helpviewer_keywords:
- termination handlers [C++], handling exceptions in C++
- structured exception handling [C++]
- try-catch keyword [C++], exception handlers
- C++ exception handling, termination handlers
- try-catch keyword [C++], termination handlers
- C++ exception handling, exception handlers
ms.assetid: dd3b647d-c269-43a8-aab9-ad1458712976
ms.openlocfilehash: 142e89bc82adbe7938e8825029908e814df6055c
ms.sourcegitcommit: efc8c32205c9d610f40597556273a64306dec15d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/26/2020
ms.locfileid: "88898628"
---
# <a name="structured-exception-handling-cc"></a>Obsługa wyjątków strukturalnych (C/C++)

Obsługa wyjątków strukturalnych (SEH) to rozszerzenie firmy Microsoft do języka C, które obsługuje pewne wyjątkowe sytuacje związane z kodem, takie jak błędy sprzętu. Chociaż systemy Windows i Microsoft C++ obsługują SEH, zalecamy użycie obsługi wyjątków ISO-standard C++. Sprawia, że kod jest bardziej przenośny i elastyczny. Jednak aby zachować istniejący kod lub dla określonych rodzajów programów, nadal może być konieczne użycie SEH.

**Specyficzne dla firmy Microsoft:**

## <a name="grammar"></a>Gramatyka

> *`try-except-statement`* :<br/>
> &emsp;**`__try`** *`compound-statement`* **`__except`** **`(`** *`expression`* **`)`** *`compound-statement`*
>
> *`try-finally-statement`* :<br/>
> &emsp;**`__try`** *`compound-statement`* **`__finally`** *`compound-statement`*

## <a name="remarks"></a>Uwagi

Za pomocą SEH można upewnić się, że zasoby, takie jak bloki pamięci i pliki, zostaną wydane prawidłowo, jeśli wykonanie nieoczekiwanie zakończy się. Można także obsłużyć konkretne problemy — na przykład niewystarczająca ilość pamięci — przy użyciu zwięzłego kodu strukturalnego, który nie polega na **`goto`** instrukcjach lub opracowywaniu testów kodów powrotu.

`try-except`Instrukcje i, `try-finally` do których odwołuje się w tym artykule, są rozszerzeniami firmy Microsoft do języka C. Obsługują one SEH, umożliwiając aplikacjom uzyskanie kontroli nad programem po zdarzeniach, które w przeciwnym razie spowodują zakończenie wykonywania. Chociaż SEH współpracuje z plikami źródłowymi języka C++, nie jest to zaprojektowane specjalnie dla języka C++. Jeśli używasz SEH w programie C++ kompilowanym przy użyciu opcji [ `/EHa` lub `/EHsc` ](../build/reference/eh-exception-handling-model.md) , destruktory dla obiektów lokalnych są wywoływane, ale inne zachowanie wykonywania może nie być oczekiwane. Aby zapoznać się z ilustracją, zobacz przykład w dalszej części tego artykułu. W większości przypadków zamiast SEH zaleca się użycie [obsługi wyjątków](../cpp/try-throw-and-catch-statements-cpp.md)ISO-standard c++, która obsługuje również kompilator języka Microsoft c++. Korzystając z obsługi wyjątków C++, można upewnić się, że kod jest bardziej przenośny i można obsługiwać wyjątki dowolnego typu.

Jeśli masz kod C, który używa SEH, możesz go mieszać z kodem C++, który korzysta z obsługi wyjątków C++. Aby uzyskać więcej informacji, zobacz [Obsługa wyjątków strukturalnych w języku C++](../cpp/exception-handling-differences.md).

Istnieją dwa mechanizmy SEH:

- [Programy obsługi wyjątków](../cpp/writing-an-exception-handler.md)lub **`__except`** bloki, które mogą reagować na lub odrzucić wyjątek.

- [Programy obsługi zakończenia](../cpp/writing-a-termination-handler.md)lub **`__finally`** bloki, które są zawsze wywoływane, niezależnie od tego, czy wyjątek powoduje zakończenie, czy nie.

Te dwa rodzaje obsługi są różne, ale są ściśle powiązane z procesem znanym jako odwracanie *stosu*. Gdy wystąpi wyjątek strukturalny, system Windows szuka ostatnio zainstalowanego programu obsługi wyjątków, który jest obecnie aktywny. Program obsługi może wykonać jedną z trzech czynności:

- Nie można rozpoznać wyjątku i przekazać kontroli do innych programów obsługi.

- Rozpoznaj wyjątek, ale Odrzuć go.

- Rozpoznać wyjątek i obsłużyć go.

Program obsługi wyjątków, który rozpoznaje wyjątek, może nie znajdować się w funkcji, która była uruchomiona, gdy wystąpił wyjątek. Może ona znajdować się w funkcji znacznie większej na stosie. Aktualnie uruchomiona funkcja i wszystkie inne funkcje w ramce stosu są kończone. W trakcie tego procesu *stos jest*rozłożony. Oznacza to, że lokalne zmienne niestatyczne dla zakończonych funkcji są wyczyszczone ze stosu.

Po odłączeniu stosu system operacyjny wywołuje wszystkie programy obsługi zakończenia, które zostały zapisaną dla każdej funkcji. Za pomocą procedury obsługi zakończenia, można wyczyścić zasoby, które w przeciwnym razie pozostaną otwarte z powodu nietypowego zakończenia. Jeśli wprowadzono sekcję krytyczną, możesz ją zamknąć w programie obsługi zakończenia. Gdy program zostanie zamknięty, można wykonywać inne zadania dla gospodarstw domowych, takie jak zamykanie i usuwanie plików tymczasowych.

## <a name="next-steps"></a>Następne kroki

- [Pisanie programu do obsługi wyjątku](../cpp/writing-an-exception-handler.md)

- [Pisanie programu obsługi zakończenia](../cpp/writing-a-termination-handler.md)

- [Obsługa wyjątków strukturalnych w języku C++](../cpp/exception-handling-differences.md)

## <a name="example"></a>Przykład

Jak wspomniano wcześniej, destruktory dla obiektów lokalnych są wywoływane, jeśli używasz SEH w programie C++ i kompilujesz go przy użyciu **`/EHa`** **`/EHsc`** opcji lub. Zachowanie podczas wykonywania może jednak nie być oczekiwane w przypadku korzystania z wyjątków C++. Ten przykład ilustruje te różnice w zachowaniu.

```cpp
#include <stdio.h>
#include <Windows.h>
#include <exception>

class TestClass
{
public:
    ~TestClass()
    {
        printf("Destroying TestClass!\r\n");
    }
};

__declspec(noinline) void TestCPPEX()
{
#ifdef CPPEX
    printf("Throwing C++ exception\r\n");
    throw std::exception("");
#else
    printf("Triggering SEH exception\r\n");
    volatile int *pInt = 0x00000000;
    *pInt = 20;
#endif
}

__declspec(noinline) void TestExceptions()
{
    TestClass d;
    TestCPPEX();
}

int main()
{
    __try
    {
        TestExceptions();
    }
    __except(EXCEPTION_EXECUTE_HANDLER)
    {
        printf("Executing SEH __except block\r\n");
    }

    return 0;
}
```

Jeśli używasz **`/EHsc`** do kompilowania tego kodu, ale makro kontroli testu lokalnego `CPPEX` jest niezdefiniowane, `TestClass` destruktor nie zostanie uruchomiony. Dane wyjściowe wyglądają następująco:

```Output
Triggering SEH exception
Executing SEH __except block
```

Jeśli używasz **`/EHsc`** do kompilowania kodu i `CPPEX` jest on definiowany przy użyciu `/DCPPEX` (w celu wygenerowania wyjątku C++), destruktor zostanie `TestClass` uruchomiony, a dane wyjściowe wyglądają następująco:

```Output
Throwing C++ exception
Destroying TestClass!
Executing SEH __except block
```

Jeśli używasz **`/EHa`** do kompilowania kodu, `TestClass` destruktor wykonuje, czy wyjątek został zgłoszony przez użycie `std::throw` lub przy użyciu SEH, aby wyzwolić wyjątek. Oznacza to, czy `CPPEX` jest zdefiniowany, czy nie. Dane wyjściowe wyglądają następująco:

```Output
Throwing C++ exception
Destroying TestClass!
Executing SEH __except block
```

Aby uzyskać więcej informacji, zobacz [ `/EH` (model obsługi wyjątków)](../build/reference/eh-exception-handling-model.md).

**ZAKOŃCZENIE specyficzne dla firmy Microsoft**

## <a name="see-also"></a>Zobacz też

[Obsługa wyjątków](../cpp/exception-handling-in-visual-cpp.md)<br/>
[Słowa kluczowe](../cpp/keywords-cpp.md)<br/>
[`<exception>`](../standard-library/exception.md)<br/>
[Błędy i obsługa wyjątków](../cpp/errors-and-exception-handling-modern-cpp.md)<br/>
[Strukturalna obsługa wyjątków (system Windows)](/windows/win32/debug/structured-exception-handling)
