---
title: Obsługa wyjątków strukturalnych (C/C++)
ms.date: 08/14/2018
helpviewer_keywords:
- termination handlers [C++], handling exceptions in C++
- structured exception handling [C++]
- try-catch keyword [C++], exception handlers
- C++ exception handling, termination handlers
- try-catch keyword [C++], termination handlers
- C++ exception handling, exception handlers
ms.assetid: dd3b647d-c269-43a8-aab9-ad1458712976
ms.openlocfilehash: 4555690476bc149687c680fc2baae53b96658a4e
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69498492"
---
# <a name="structured-exception-handling-cc"></a>Obsługa wyjątków strukturalnych (C/C++)

Obsługa wyjątków strukturalnych (SEH) to rozszerzenie firmy Microsoft do języka C, które obsługuje pewne wyjątkowe sytuacje związane z kodem, takie jak błędy sprzętu. Mimo że systemy Windows C++ i Microsoft obsługują SEH, zalecamy korzystanie z obsługi wyjątków standardu C++ ISO, ponieważ sprawia, że kod jest bardziej przenośny i elastyczny. Niemniej jednak, aby zachować istniejący kod lub dla określonych rodzajów programów, nadal może być konieczne użycie SEH.

**Specyficzne dla firmy Microsoft:**

## <a name="grammar"></a>Gramatyka

*try-except-Statement* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **__try** *instrukcja złożona* **__except** **(** *wyrażenie* **)** *instrukcja złożona*

*try-finally-Statement* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **__try** *instrukcja złożona* **__finally** *instrukcja złożona*

## <a name="remarks"></a>Uwagi

Za pomocą SEH można upewnić się, że zasoby, takie jak bloki pamięci i pliki, zostaną wydane prawidłowo, jeśli wykonanie nieoczekiwanie zakończy się. Można także obsłużyć konkretne problemy — na przykład niewystarczająca ilość pamięci — przy użyciu zwięzłego kodu strukturalnego, który nie polega na instrukcjach **goto** ani opracowaniu testów kodów powrotu.

Instrukcje try-except i try-finally, o których mowa w tym artykule, są rozszerzeniami firmy Microsoft do języka C. Obsługują one SEH, umożliwiając aplikacjom uzyskanie kontroli nad programem po zdarzeniach, które w przeciwnym razie spowodują zakończenie wykonywania. Chociaż SEH współpracuje z C++ plikami źródłowymi, nie jest to specjalnie zaprojektowane C++dla programu. Jeśli używasz SEH w C++ programie kompilowanym przy użyciu opcji [/EHa lub/EHsc](../build/reference/eh-exception-handling-model.md) , destruktory dla obiektów lokalnych są wywoływane, ale inne zachowanie wykonywania może nie być oczekiwane. Aby zapoznać się z ilustracją, zobacz przykład w dalszej części tego artykułu. W większości przypadków zamiast SEH zalecamy użycie standardowej [ C++ obsługi wyjątków](../cpp/try-throw-and-catch-statements-cpp.md)ISO, która obsługuje również kompilator firmy Microsoft C++ . Korzystając C++ z obsługi wyjątków, można upewnić się, że kod jest bardziej przenośny i można obsługiwać wyjątki dowolnego typu.

Jeśli masz kod w języku C, który używa SEH, możesz go mieszać C++ z kodem, C++ który używa obsługi wyjątków. Aby uzyskać więcej informacji, zobacz [Obsługa wyjątków C++strukturalnych w programie ](../cpp/exception-handling-differences.md).

Istnieją dwa mechanizmy SEH:

- [Obsługa wyjątków](../cpp/writing-an-exception-handler.md)lub bloki **__except** , które mogą reagować na lub odrzucić wyjątek.

- [Programy obsługi zakończenia](../cpp/writing-a-termination-handler.md)lub **__finally** bloki, które są zawsze wywoływane, niezależnie od tego, czy wyjątek powoduje zakończenie, czy nie.

Te dwa rodzaje obsługi są różne, ale są ściśle powiązane przez proces znany jako "odchodzenie stosu". Gdy wystąpi wyjątek strukturalny, system Windows szuka ostatnio zainstalowanego programu obsługi wyjątków, który jest obecnie aktywny. Program obsługi może wykonać jedną z trzech czynności:

- Nie można rozpoznać wyjątku i przekazać kontroli do innych programów obsługi.

- Rozpoznaj wyjątek, ale Odrzuć go.

- Rozpoznać wyjątek i obsłużyć go.

Program obsługi wyjątków, który rozpoznaje wyjątek, może nie znajdować się w funkcji, która była uruchomiona, gdy wystąpił wyjątek. W niektórych przypadkach może on znajdować się w funkcji znacznie większej na stosie. Aktualnie uruchomiona funkcja i wszystkie inne funkcje w ramce stosu są kończone. W trakcie tego procesu stos ma wartość "unrany;", a lokalne zmienne niestatyczne funkcji zakończonych są usuwane ze stosu.

Po odłączeniu stosu system operacyjny wywołuje wszystkie programy obsługi zakończenia, które zostały zapisaną dla każdej funkcji. Za pomocą procedury obsługi zakończenia można wyczyścić zasoby, które w przeciwnym razie pozostaną otwarte ze względu na nietypowe zakończenie. Jeśli wprowadzono sekcję krytyczną, możesz ją zamknąć w programie obsługi zakończenia. Jeśli program zostanie zamknięty, można wykonywać inne zadania dla gospodarstw domowych, takie jak zamykanie i usuwanie plików tymczasowych.

## <a name="next-steps"></a>Następne kroki

- [Pisanie programu do obsługi wyjątku](../cpp/writing-an-exception-handler.md)

- [Pisanie programu obsługi zakończenia](../cpp/writing-a-termination-handler.md)

- [Obsługa wyjątków strukturalnych w języku C++](../cpp/exception-handling-differences.md)

## <a name="example"></a>Przykład

Jak wspomniano wcześniej, destruktory dla obiektów lokalnych są wywoływane, jeśli używasz SEH w C++ programie i kompilujesz go przy użyciu opcji **/EHa** lub **/EHsc** . Zachowanie podczas wykonywania może jednak nie być oczekiwane w przypadku korzystania z C++ wyjątków. Ten przykład ilustruje te różnice w zachowaniu.

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

Jeśli używasz **/EHsc** do kompilowania tego kodu, ale makro `CPPEX` kontroli testu lokalnego jest niezdefiniowane, `TestClass` nie ma żadnego wykonywania destruktora, a dane wyjściowe wyglądają następująco:

```Output
Triggering SEH exception
Executing SEH __except block
```

Jeśli używasz **/EHsc** do kompilowania `CPPEX` kodu i jest on definiowany przy użyciu `/DCPPEX` (w taki sposób, aby C++ wyjątek został zgłoszony) `TestClass` , destruktor wykonuje, a dane wyjściowe wyglądają następująco:

```Output
Throwing C++ exception
Destroying TestClass!
Executing SEH __except block
```

Jeśli używasz **/EHa** do kompilowania kodu, `TestClass` destruktor jest wykonywany bez względu na to, czy wyjątek został zgłoszony przez użycie `std::throw` lub za pomocą SEH, aby wyzwolić wyjątek, czyli czy `CPPEX` nie został zdefiniowany. Dane wyjściowe wyglądają następująco:

```Output
Throwing C++ exception
Destroying TestClass!
Executing SEH __except block
```

Aby uzyskać więcej informacji, zobacz [/EH (model obsługi wyjątków)](../build/reference/eh-exception-handling-model.md).

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz także

[Obsługa wyjątków](../cpp/exception-handling-in-visual-cpp.md)<br/>
[Słowa kluczowe](../cpp/keywords-cpp.md)<br/>
[\<> wyjątku](../standard-library/exception.md)<br/>
[Błędy i obsługa wyjątków](../cpp/errors-and-exception-handling-modern-cpp.md)<br/>
[Strukturalna obsługa wyjątków (system Windows)](/windows/win32/debug/structured-exception-handling)
