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

**Microsoft Specific**

The **try-except** statement is a Microsoft extension to the C and C++ languages that supports structured exception handling.

## <a name="syntax"></a>Składnia

> **\_\_try**<br/>
> {<br/>
> &nbsp;&nbsp;&nbsp;&nbsp;// guarded code<br/>
> }<br/>
> **\_\_except** ( *expression* )<br/>
> {<br/>
> &nbsp;&nbsp;&nbsp;&nbsp;// exception handler code<br/>
> }

## <a name="remarks"></a>Uwagi

The **try-except** statement is a Microsoft extension to the C and C++ languages that enables target applications to gain control when events that normally terminate program execution occur. Such events are called *exceptions*, and the mechanism that deals with exceptions is called *structured exception handling* (SEH).

For related information, see the [try-finally statement](../cpp/try-finally-statement.md).

Wyjątki mogą być sprzętowe lub programowe. Nawet wtedy, gdy aplikacje nie mogą całkowicie odzyskać sprawności po wystąpieniu wyjątku sprzętowego lub programowego, strukturalna obsługa wyjątków umożliwia wyświetlenie informacji o błędzie i pozwala na przechwycenie wewnętrznego stanu aplikacji, aby pomóc w zdiagnozowaniu problemu. Jest to szczególnie użyteczne w przypadku sporadycznych problemów, których nie można łatwo odtworzyć.

> [!NOTE]
> Strukturalna obsługa wyjątków działa z Win32 dla plików źródłowych C i C++. Jednakże nie jest specjalnie zaprojektowana dla języka C++. Można zapewnić, że kod będzie bardziej przenośny przy użyciu obsługi wyjątków C++. Ponadto, obsługa wyjątków C++ jest bardziej elastyczna, gdyż może obsługiwać wyjątki dowolnego typu. For C++ programs, it is recommended that you use the C++ exception-handling mechanism ([try, catch, and throw](../cpp/try-throw-and-catch-statements-cpp.md) statements).

The compound statement after the **__try** clause is the body or guarded section. The compound statement after the **__except** clause is the exception handler. Kod obsługi wyjątku określa zestaw akcji, które zostaną wykonane, jeśli wystąpi wyjątek w ciele chronionej sekcji. Execution proceeds as follows:

1. Sekcja chroniona jest wykonywana.

1. If no exception occurs during execution of the guarded section, execution continues at the statement after the **__except** clause.

1. If an exception occurs during execution of the guarded section or in any routine the guarded section calls, the **__except** *expression* (called the *filter* expression) is evaluated and the value determines how the exception is handled. There are three possible values:

   - EXCEPTION_CONTINUE_EXECUTION (-1) Exception is dismissed. Kontynuuj wykonywanie w punkcie, w którym wystąpił wyjątek.

   - EXCEPTION_CONTINUE_SEARCH (0) Exception is not recognized. Continue to search up the stack for a handler, first for containing **try-except** statements, then for handlers with the next highest precedence.

   - EXCEPTION_EXECUTE_HANDLER (1) Exception is recognized. Transfer control to the exception handler by executing the **__except** compound statement, then continue execution after the **__except** block.

Because the **__except** expression is evaluated as a C expression, it is limited to a single value, the conditional-expression operator, or the comma operator. Jeśli wymagane jest bardziej rozległe przetwarzanie, wyrażenie może wywołać procedurę, która zwraca jedną z trzech wartości wymienionych powyżej.

Każda aplikacja może mieć własną obsługę wyjątków.

It is not valid to jump into a **__try** statement, but valid to jump out of one. The exception handler is not called if a process is terminated in the middle of executing a **try-except** statement.

For compatibility with previous versions, **_try**, **_except**, and **_leave** are synonyms for **__try**, **__except**, and **__leave** unless compiler option [/Za \(Disable language extensions)](../build/reference/za-ze-disable-language-extensions.md) is specified.

### <a name="the-__leave-keyword"></a>Słowo kluczowe __leave

The **__leave** keyword is valid only within the guarded section of a **try-except** statement, and its effect is to jump to the end of the guarded section. Wykonywanie jest kontynuowane po pierwszej instrukcji następującej po programie obsługi wyjątków.

A **goto** statement can also jump out of the guarded section, and it does not degrade performance as it does in a **try-finally** statement because stack unwinding does not occur. However, we recommend that you use the **__leave** keyword rather than a **goto** statement because you are less likely to make a programming mistake if the guarded section is large or complex.

### <a name="structured-exception-handling-intrinsic-functions"></a>Wewnętrzne funkcje strukturalnej obsługi wyjątków

Structured exception handling provides two intrinsic functions that are available to use with the **try-except** statement: `GetExceptionCode` and `GetExceptionInformation`.

`GetExceptionCode` returns the code (a 32-bit integer) of the exception.

The intrinsic function `GetExceptionInformation` returns a pointer to a structure containing additional information about the exception. Za pomocą tego wskaźnika można uzyskać dostęp do stanu maszyny w momencie wystąpienia wyjątku sprzętowego. Struktura jest następująca:

```cpp
typedef struct _EXCEPTION_POINTERS {
    PEXCEPTION_RECORD ExceptionRecord;
    PCONTEXT ContextRecord;
} EXCEPTION_POINTERS, *PEXCEPTION_POINTERS;
```

The pointer types `PEXCEPTION_RECORD` and `PCONTEXT` are defined in the include file \<winnt.h>, and `_EXCEPTION_RECORD` and `_CONTEXT` are defined in the include file \<excpt.h>

You can use `GetExceptionCode` within the exception handler. However, you can use `GetExceptionInformation` only within the exception filter expression. Informacje na które wskazuje są na ogół na stosie i nie są dostępne po przekazaniu kontroli do programu obsługi wyjątków.

The intrinsic function `AbnormalTermination` is available within a termination handler. It returns 0 if the body of the **try-finally** statement terminates sequentially. We wszystkich pozostałych przypadkach zwraca wartość 1.

excpt.h defines some alternate names for these intrinsics:

`GetExceptionCode` is equivalent to `_exception_code`

`GetExceptionInformation` is equivalent to `_exception_info`

`AbnormalTermination` is equivalent to `_abnormal_termination`

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

**END Microsoft Specific**

## <a name="see-also"></a>Zobacz także

[Writing an exception handler](../cpp/writing-an-exception-handler.md)<br/>
[Obsługa wyjątków strukturalnych (C/C++)](../cpp/structured-exception-handling-c-cpp.md)<br/>
[Słowa kluczowe](../cpp/keywords-cpp.md)
