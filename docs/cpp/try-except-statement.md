---
title: try-except — instrukcja
ms.date: 10/09/2018
f1_keywords:
- _abnormal_termination_cpp
- _exception_code_cpp
- EXCEPTION_CONTINUE_SEARCH
- _exception_info
- __except
- _except
- EXCEPTION_CONTINUE_EXECUTION
- _exception_code
- __except_cpp
- _exception_info_cpp
- EXCEPTION_EXECUTE_HANDLER
- _abnormal_termination
helpviewer_keywords:
- __try keyword [C++]
- EXCEPTION_CONTINUE_EXECUTION macro
- EXCEPTION_CONTINUE_SEARCH macro
- EXCEPTION_EXECUTE_HANDLER macro
- GetExceptionCode function
- try-catch keyword [C++], try-except keyword [C++]
- _exception_code keyword [C++]
- try-except keyword [C++]
- _exception_info keyword [C++]
- _abnormal_termination keyword [C++]
ms.assetid: 30d60071-ea49-4bfb-a8e6-7a420de66381
ms.openlocfilehash: af378f510f11e1fe7d08619b5f33efe92a13d7be
ms.sourcegitcommit: 654aecaeb5d3e3fe6bc926bafd6d5ace0d20a80e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/20/2019
ms.locfileid: "74245163"
---
# <a name="try-except-statement"></a>try-except — instrukcja

**Specyficzne dla firmy Microsoft**

Instrukcja **try-except** to rozszerzenie firmy Microsoft do języków C i C++ , które obsługują obsługę wyjątków strukturalnych.

## <a name="syntax"></a>Składnia

> **\_\_spróbuj**<br/>
> {<br/>
> &nbsp;&nbsp;&nbsp;kod &nbsp;//chroniony<br/>
> }<br/>
> **\_\_z wyjątkiem** ( *wyrażenie* )<br/>
> {<br/>
> &nbsp;&nbsp;&nbsp;kod procedury obsługi wyjątków &nbsp;//<br/>
> }

## <a name="remarks"></a>Uwagi

Instrukcja **try-except** to rozszerzenie firmy Microsoft do języków C i C++ , które umożliwiają aplikacjom docelowym uzyskanie kontroli w przypadku wystąpienia zdarzeń, które normalnie kończą wykonywanie programu. Takie zdarzenia są nazywane *wyjątkami*, a mechanizm, który zajmuje się wyjątkami, jest nazywany *obsługą wyjątków strukturalnych* (SEH).

Aby uzyskać powiązane informacje, zobacz [instrukcję try-finally](../cpp/try-finally-statement.md).

Wyjątki mogą być sprzętowe lub programowe. Nawet wtedy, gdy aplikacje nie mogą całkowicie odzyskać sprawności po wystąpieniu wyjątku sprzętowego lub programowego, strukturalna obsługa wyjątków umożliwia wyświetlenie informacji o błędzie i pozwala na przechwycenie wewnętrznego stanu aplikacji, aby pomóc w zdiagnozowaniu problemu. Jest to szczególnie użyteczne w przypadku sporadycznych problemów, których nie można łatwo odtworzyć.

> [!NOTE]
> Strukturalna obsługa wyjątków działa z Win32 dla plików źródłowych C i C++. Jednakże nie jest specjalnie zaprojektowana dla języka C++. Można zapewnić, że kod będzie bardziej przenośny przy użyciu obsługi wyjątków C++. Ponadto, obsługa wyjątków C++ jest bardziej elastyczna, gdyż może obsługiwać wyjątki dowolnego typu. W C++ przypadku programów zaleca się użycie mechanizmu obsługi C++ wyjątków (instrukcje[try, catch i throw](../cpp/try-throw-and-catch-statements-cpp.md) ).

Instrukcja złożona po klauzuli **__try** to treść lub chroniona sekcja. Instrukcja złożona po klauzuli **__except** to procedura obsługi wyjątków. Kod obsługi wyjątku określa zestaw akcji, które zostaną wykonane, jeśli wystąpi wyjątek w ciele chronionej sekcji. Wykonanie przebiega w następujący sposób:

1. Sekcja chroniona jest wykonywana.

1. Jeśli podczas wykonywania sekcji chronionej nie wystąpi wyjątek, wykonywanie jest kontynuowane przy użyciu instrukcji po klauzuli **__except** .

1. Jeśli wystąpi wyjątek podczas wykonywania sekcji chronionej lub w jakiejkolwiek rutynowej wywołaniu sekcji chronionej, *wyrażenie* **__except** (o nazwie wyrażenie *filtru* ) jest oceniane i wartość określa sposób obsługi wyjątku. Istnieją trzy możliwe wartości:

   - EXCEPTION_CONTINUE_EXECUTION (-1) wyjątek zostanie odrzucony. Kontynuuj wykonywanie w punkcie, w którym wystąpił wyjątek.

   - Wyjątek EXCEPTION_CONTINUE_SEARCH (0) nie został rozpoznany. Kontynuuj wyszukiwanie stosu dla programu obsługi, najpierw dla zawiera instrukcje **try-except** , a następnie dla programów obsługi przy użyciu następnego najwyższego pierwszeństwa.

   - EXCEPTION_EXECUTE_HANDLER (1) wyjątek jest rozpoznawany. Przenieś kontrolę do programu obsługi wyjątków, wykonując instrukcję **__except** złożonej, a następnie kontynuuj wykonywanie po bloku **__except** .

Ponieważ wyrażenie **__except** jest oceniane jako wyrażenie C, jest ograniczone do pojedynczej wartości, operatora warunkowego wyrażenia lub operatora przecinki. Jeśli wymagane jest bardziej rozległe przetwarzanie, wyrażenie może wywołać procedurę, która zwraca jedną z trzech wartości wymienionych powyżej.

Każda aplikacja może mieć własną obsługę wyjątków.

Nie można przeskoczyć do instrukcji **__try** , ale prawidłowym wyjściem jest przejście z jednego. Procedura obsługi wyjątków nie jest wywoływana, jeśli proces zostanie zakończony w trakcie wykonywania instrukcji **try-except** .

Aby zapewnić zgodność z poprzednimi wersjami, **_try**, **_Except**i **_leave** są synonimami dla **__try**, **__except**i **__leave** , chyba że opcja kompilatora [/za \(Disable Extensions)](../build/reference/za-ze-disable-language-extensions.md) jest określona.

### <a name="the-__leave-keyword"></a>Słowo kluczowe __leave

Słowo kluczowe **__leave** jest prawidłowe tylko w sekcji chronionej instrukcji **try-except** , a jej efektem jest przechodzenie do końca sekcji chronionej. Wykonywanie jest kontynuowane po pierwszej instrukcji następującej po programie obsługi wyjątków.

Instrukcja **goto** może również wyskoczyć z sekcji chronionej i nie obniża wydajności, ponieważ wykonuje ją w instrukcji **try-finally** , ponieważ nie nastąpiło odchodzenie stosu. Zaleca się jednak użycie słowa kluczowego **__leave** , a nie instrukcji **goto** , ponieważ nie można wprowadzać błędu programistycznego, jeśli chroniona sekcja jest duża lub skomplikowana.

### <a name="structured-exception-handling-intrinsic-functions"></a>Wewnętrzne funkcje strukturalnej obsługi wyjątków

Strukturalna obsługa wyjątków udostępnia dwie funkcje wewnętrzne, które są dostępne do użycia z instrukcją **try-except** : `GetExceptionCode` i `GetExceptionInformation`.

`GetExceptionCode` zwraca kod (32-bitową liczbę całkowitą) wyjątku.

Funkcja wewnętrzna `GetExceptionInformation` zwraca wskaźnik do struktury zawierającej dodatkowe informacje o wyjątku. Za pomocą tego wskaźnika można uzyskać dostęp do stanu maszyny w momencie wystąpienia wyjątku sprzętowego. Struktura jest następująca:

```cpp
typedef struct _EXCEPTION_POINTERS {
    PEXCEPTION_RECORD ExceptionRecord;
    PCONTEXT ContextRecord;
} EXCEPTION_POINTERS, *PEXCEPTION_POINTERS;
```

Typy wskaźnika `PEXCEPTION_RECORD` i `PCONTEXT` są zdefiniowane w pliku dołączanym \<Winnt. h >, a `_EXCEPTION_RECORD` i `_CONTEXT` są zdefiniowane w pliku dołączanym \<EXCPT. h >

`GetExceptionCode` można użyć w ramach procedury obsługi wyjątków. Można jednak używać `GetExceptionInformation` tylko w wyrażeniu filtru wyjątków. Informacje na które wskazuje są na ogół na stosie i nie są dostępne po przekazaniu kontroli do programu obsługi wyjątków.

Funkcja wewnętrzna `AbnormalTermination` jest dostępna w ramach procedury obsługi zakończenia. Zwraca wartość 0, jeśli treść instrukcji **try-finally** kończy się sekwencyjnie. We wszystkich pozostałych przypadkach zwraca wartość 1.

EXCPT. h definiuje alternatywne nazwy dla następujących elementów wewnętrznych:

`GetExceptionCode` jest równoznaczna z `_exception_code`

`GetExceptionInformation` jest równoznaczna z `_exception_info`

`AbnormalTermination` jest równoznaczna z `_abnormal_termination`

## <a name="example"></a>Przykład

```cpp
// exceptions_try_except_Statement.cpp
// Example of try-except and try-finally statements
#include <stdio.h>
#include <windows.h> // for EXCEPTION_ACCESS_VIOLATION
#include <excpt.h>

int filter(unsigned int code, struct _EXCEPTION_POINTERS *ep)
{
    puts("in filter.");
    if (code == EXCEPTION_ACCESS_VIOLATION)
    {
        puts("caught AV as expected.");
        return EXCEPTION_EXECUTE_HANDLER;
    }
    else
    {
        puts("didn't catch AV, unexpected.");
        return EXCEPTION_CONTINUE_SEARCH;
    };
}

int main()
{
    int* p = 0x00000000;   // pointer to NULL
    puts("hello");
    __try
    {
        puts("in try");
        __try
        {
            puts("in try");
            *p = 13;    // causes an access violation exception;
        }
        __finally
        {
            puts("in finally. termination: ");
            puts(AbnormalTermination() ? "\tabnormal" : "\tnormal");
        }
    }
    __except(filter(GetExceptionCode(), GetExceptionInformation()))
    {
        puts("in except");
    }
    puts("world");
}
```

### <a name="output"></a>Dane wyjściowe

```Output
hello
in try
in try
in filter.
caught AV as expected.
in finally. termination:
        abnormal
in except
world
```

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz także

[Pisanie procedury obsługi wyjątków](../cpp/writing-an-exception-handler.md)<br/>
[Obsługa wyjątków strukturalnych (C/C++)](../cpp/structured-exception-handling-c-cpp.md)<br/>
[Słowa kluczowe](../cpp/keywords-cpp.md)
