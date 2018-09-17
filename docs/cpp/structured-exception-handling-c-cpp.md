---
title: (C/C++) obsługi wyjątków strukturalnych | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 08/14/2018
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- termination handlers [C++], handling exceptions in C++
- structured exception handling [C++]
- try-catch keyword [C++], exception handlers
- C++ exception handling, termination handlers
- try-catch keyword [C++], termination handlers
- C++ exception handling, exception handlers
ms.assetid: dd3b647d-c269-43a8-aab9-ad1458712976
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 861cb216dba1e8b3d451d6120dba897e06ba910a
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45713196"
---
# <a name="structured-exception-handling-cc"></a>Obsługa wyjątków strukturalnych (C/C++)

Obsługa wyjątków strukturalnych (SEH) jest rozszerzeniem firmy Microsoft do C, aby bezpiecznie obsłużyć niektórych sytuacjach wyjątkowych kodu, takich jak awarie sprzętu. Mimo że Windows i Visual C++ obsługuje SEH, zalecane jest użycie ISO standard C++ obsługi wyjątków ponieważ sprawia, że Twój kod bardziej przenośny i elastyczny. Niemniej jednak aby zachować istniejący kod lub dla szczególnych typów programów, nadal może być konieczne używanie SEH.

**Specyficzne dla firmy Microsoft:**

## <a name="grammar"></a>Gramatyka

*instrukcji z wyjątkiem try* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**__try** *compound-statement* **__except** **(** *wyrażenie* **)** *compound-statement*

*Spróbuj na koniec instrukcji* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**__try** *compound-statement* **__finally** *compound-statement*

## <a name="remarks"></a>Uwagi

Z SEH można zagwarantować, że zasoby, takie jak bloki pamięci i pliki są poprawnie zwalniane, jeśli wykonanie następuje nieoczekiwane zakończenie. Może również obsługiwać konkretnych problemów — na przykład brak wystarczającej ilości pamięci — przy użyciu zwięzłe ze strukturą kodu, które nie zależą od **goto** instrukcji lub rozbudowane testowania kody powrotne.

Try-except i try-finally, określone w tym artykule są rozszerzenia Microsoft do języka C. Obsługiwane są też SEH, dzięki czemu aplikacje mogą przejąć kontrolę nad programem po zdarzenia, które w przeciwnym razie zakończy się wykonywanie. Mimo że SEH działa przy użyciu plików źródłowych języka C++, go nie opracowano specjalnie dla języka C++. Jeśli używasz strukturalnej obsługi wyjątków w programie C++, który kompilujesz przy użyciu [/eha lub/ehsc](../build/reference/eh-exception-handling-model.md) opcję destruktory dla obiektów lokalnych są wywoływane, ale inne zachowanie wykonywania może nie być, czego oczekiwać. Ilustracja znajduje się w przykładzie w dalszej części tego artykułu. W większości przypadków zamiast SEH firma Microsoft zaleca użycie ISO standard [obsługi wyjątków C++](../cpp/try-throw-and-catch-statements-cpp.md), który obsługuje również Visual C++. Korzystając z obsługi wyjątków C++, można upewnić się, że Twój kod będzie bardziej przenośny i może obsługiwać wyjątki dowolnego typu.

Jeśli masz kod C, który używa SEH, można łączyć je z kodem C++, używającej obsługi wyjątków C++. Aby uzyskać informacje, zobacz [obsługi wyjątków strukturalnych w języku C++](../cpp/exception-handling-differences.md).

Istnieją dwa mechanizmy strukturalnej obsługi wyjątków:

- [Programy obsługi wyjątków](../cpp/writing-an-exception-handler.md), lub **__except** bloki, które mogą odpowiadać na lub odrzucić wyjątku.

- [Programy obsługi zakończenia](../cpp/writing-a-termination-handler.md), lub **__finally** bloki, które są zawsze wywołuje się, czy wyjątek powoduje zakończenia, czy nie.

Te dwa rodzaje obsługi różniące się od siebie, ale są ściśle powiązane przez proces ten jest znany jako "odwijania stosu." W przypadku wyjątków strukturalnych Windows wyszukuje ostatnio zainstalowane obsługi wyjątków, który jest obecnie aktywny. Program obsługi, można wykonać jedną z trzech zdarzeń:

- Nie można rozpoznać wyjątek i przekazać sterowanie do innych programów obsługi.

- Rozpoznaje wyjątek, ale je zamknąć.

- Rozpoznaje wyjątek, a następnie go obsłużyć.

Program obsługi wyjątku, który rozpoznaje wyjątek, może nie być w funkcji, która była uruchomiona w chwili wystąpienia wyjątku. W niektórych przypadkach może być w funkcji znacznie wyższa na stosie. Aktualnie uruchomionej funkcji i innych funkcji na ramce stosu są kończone. W trakcie tego procesu stos jest "rozwinięty"; oznacza to, że zmienne lokalne niestatycznej funkcji zakończone są usuwane ze stosu.

Zgodnie z jego rozwija stos, system operacyjny wywołuje programy obsługi zakończenia, które zostały napisane dla każdej funkcji. Za pomocą programu obsługi zakończenia, możesz wyczyścić zasoby, które w przeciwnym razie mogłyby pozostają otwarte, jeśli ze względu na Nienormalne zakończenie. Jeśli zostały wprowadzone sekcję krytyczną, możesz ją zakończyć programu obsługi zakończenia. Jeśli program będzie zamknięty, można wykonywać inne zadania celów, takich jak zamknięcie i usuwanie plików tymczasowych.

## <a name="next-steps"></a>Następne kroki

- [Pisanie programu do obsługi wyjątku](../cpp/writing-an-exception-handler.md)

- [Pisanie programu obsługi zakończenia](../cpp/writing-a-termination-handler.md)

- [Obsługa wyjątków strukturalnych w języku C++](../cpp/exception-handling-differences.md)

## <a name="example"></a>Przykład

Jak wspomniano wcześniej, destruktory dla obiektów lokalnych są wywoływane, jeśli SEH należy używać w programie C++ i skompiluj go za pomocą **/eha** lub **/ehsc** opcji. Jednakże zachowanie podczas wykonywania może nie być, oczekują Jeśli używane są również wyjątki C++. W tym przykładzie pokazano te różnice w zachowaniu.

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

Jeśli używasz **/ehsc** skompilować ten kod, ale makro kontroli lokalnego testu `CPPEX` jest niezdefiniowana, istnieje nie wykonywania `TestClass` destruktor i dane wyjściowe wyglądają podobnie do następującego:

```Output
Triggering SEH exception
Executing SEH __except block
```

Jeśli używasz **/ehsc** skompilować kod i `CPPEX` jest definiowana za pomocą `/DCPPEX` (dzięki czemu jest zgłaszany wyjątek języka C++), `TestClass` wykonuje destruktor i dane wyjściowe wyglądają następująco:

```Output
Throwing C++ exception
Destroying TestClass!
Executing SEH __except block
```

Jeśli używasz **/eha** do kompilowania kodu, `TestClass` destruktor jest wykonywany niezależnie od tego, czy wyjątek został zgłoszony za pomocą `std::throw` lub za pomocą SEH, aby wyzwolić wyjątek, oznacza to, czy `CPPEX` zdefiniowane lub nie. Dane wyjściowe wyglądają następująco:

```Output
Throwing C++ exception
Destroying TestClass!
Executing SEH __except block
```

Aby uzyskać więcej informacji, zobacz [/EH (Model obsługi wyjątku)](../build/reference/eh-exception-handling-model.md).

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz także

[Obsługa wyjątków](../cpp/exception-handling-in-visual-cpp.md)  
[Słowa kluczowe](../cpp/keywords-cpp.md)  
[\<wyjątku >](../standard-library/exception.md)  
[Błędy w obsłudze wyjątków](../cpp/errors-and-exception-handling-modern-cpp.md)  
[(Windows) do obsługi wyjątków strukturalnych](https://msdn.microsoft.com/library/windows/desktop/ms680657.aspx)  
