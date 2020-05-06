---
title: try-except, instrukcja
description: Dokumentacja języka Microsoft C++ do instrukcji obsługi wyjątków strukturalnych __try i __except.
ms.date: 04/03/2020
f1_keywords:
- _abnormal_termination_cpp
- _exception_code_cpp
- _exception_info
- __except
- _except
- _exception_code
- __except_cpp
- _exception_info_cpp
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
ms.openlocfilehash: d0471bbd50e07fccbf160e9e866de4c545cdeb7e
ms.sourcegitcommit: 6b749db14b4cf3a2b8d581fda6fdd8cb98bc3207
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/05/2020
ms.locfileid: "82825773"
---
# <a name="try-except-statement"></a>try-except, instrukcja

Instrukcja **try-except** to rozszerzenie firmy Microsoft, które obsługuje strukturalną obsługę wyjątków w językach C i C++. To rozszerzenie jest **specyficzne dla firmy Microsoft**.

## <a name="syntax"></a>Składnia

> **\_\_spróbował**\
> {\
> &nbsp;&nbsp;&nbsp;&nbsp;chroniony kod \
> }\
> except ( *wyrażenie* ) \ ** \_ \_**
> {\
> &nbsp;&nbsp;&nbsp;&nbsp;kod procedury obsługi wyjątków \
> }

## <a name="remarks"></a>Uwagi

Instrukcja **try-except** to rozszerzenie firmy Microsoft do języków C i C++. Umożliwia aplikacjom docelowym uzyskanie kontroli w przypadku wystąpienia zdarzeń, które zwykle kończą wykonywanie programu. Takie zdarzenia są nazywane *wyjątkami strukturalnymi*lub *wyjątkami* . Mechanizm, który zajmuje się tymi wyjątkami, nazywa się *obsługą wyjątków strukturalnych* (SEH).

Aby uzyskać powiązane informacje, zobacz [instrukcję try-finally](../cpp/try-finally-statement.md).

Wyjątki mogą być zależne od sprzętu lub oprogramowania. Obsługa wyjątków strukturalnych jest przydatna, nawet gdy aplikacje nie mogą całkowicie odzyskać sprawności od wyjątków sprzętowych i programowych. SEH umożliwia wyświetlanie informacji o błędach i zalewkowanie wewnętrznego stanu aplikacji w celu ułatwienia zdiagnozowania problemu. Jest to szczególnie przydatne w przypadku sporadycznych problemów, które nie są łatwe do odtworzenia.

> [!NOTE]
> Strukturalna obsługa wyjątków działa z Win32 dla plików źródłowych C i C++. Nie jest to jednak przeznaczone specjalnie dla języka C++. Można zapewnić, że kod będzie bardziej przenośny przy użyciu obsługi wyjątków C++. Ponadto, obsługa wyjątków C++ jest bardziej elastyczna, gdyż może obsługiwać wyjątki dowolnego typu. W przypadku programów C++ zalecamy użycie natywnej obsługi wyjątków języka C++: instrukcje [try, catch i throw](../cpp/try-throw-and-catch-statements-cpp.md) .

Instrukcja złożona po klauzuli **__try** to *treść* lub *chroniona* sekcja. Wyrażenie **__except** jest również znane jako wyrażenie *filtru* . Jego wartość określa sposób obsługi wyjątku. Instrukcja złożona po klauzuli **__except** to procedura obsługi wyjątków. Procedura obsługi Określa akcje do wykonania, jeśli wyjątek jest wywoływany podczas wykonywania sekcji treść. Wykonanie przebiega w następujący sposób:

1. Sekcja chroniona jest wykonywana.

1. Jeśli podczas wykonywania sekcji chronionej nie wystąpi wyjątek, wykonywanie jest kontynuowane przy użyciu instrukcji po klauzuli **__except** .

1. Jeśli podczas wykonywania sekcji chronionej wystąpi wyjątek lub w każdej rutynowej sekcji jest wywoływana funkcja chroniona, wyrażenie **__except** jest oceniane. Możliwe są trzy wartości:

   - `EXCEPTION_CONTINUE_EXECUTION`(-1) Wyjątek jest odrzucany. Kontynuuj wykonywanie w punkcie, w którym wystąpił wyjątek.

   - `EXCEPTION_CONTINUE_SEARCH`(0) wyjątek nie został rozpoznany. Kontynuuj wyszukiwanie stosu dla programu obsługi, najpierw dla zawiera instrukcje **try-except** , a następnie dla programów obsługi przy użyciu następnego najwyższego pierwszeństwa.

   - `EXCEPTION_EXECUTE_HANDLER`(1) wyjątek jest rozpoznawany. Przenieś kontrolę do programu obsługi wyjątków, wykonując instrukcję **__except** złożonej, a następnie kontynuuj wykonywanie po bloku **__except** .

Wyrażenie **__except** jest oceniane jako wyrażenie języka C. Jest ograniczona do pojedynczej wartości, operatora warunkowego wyrażenia lub operatora przecinki. Jeśli wymagane jest bardziej rozległe przetwarzanie, wyrażenie może wywołać procedurę, która zwraca jedną z trzech wartości wymienionych powyżej.

Każda aplikacja może mieć własną obsługę wyjątków.

Nie można przeskoczyć do instrukcji **__try** , ale prawidłowym wyjściem jest przejście z jednego. Procedura obsługi wyjątków nie jest wywoływana, jeśli proces zostanie zakończony w trakcie wykonywania instrukcji **try-except** .

Aby zapewnić zgodność z poprzednimi wersjami, **_try**, **_Except**i **_leave** są synonimami dla **__try**, **__except**i **__leave** , chyba że jest określona opcja kompilatora [/za \(wyłączanie rozszerzeń języka)](../build/reference/za-ze-disable-language-extensions.md) .

### <a name="the-__leave-keyword"></a>Słowo kluczowe __leave

Słowo kluczowe **__leave** jest prawidłowe tylko w sekcji chronionej instrukcji **try-except** , a jej efektem jest przechodzenie do końca sekcji chronionej. Wykonywanie jest kontynuowane po pierwszej instrukcji następującej po programie obsługi wyjątków.

Instrukcja **goto** może również wyskoczyć z sekcji chronionej i nie obniża wydajności, ponieważ wykonuje ją w instrukcji **try-finally** . Dzieje się tak, ponieważ nie występuje oduzwojenie stosu. Zaleca się jednak użycie słowa kluczowego **__leave** , a nie instrukcji **goto** . Przyczyną jest to, że zmniejsza się błąd programistyczny, jeśli chroniona sekcja jest duża lub skomplikowana.

### <a name="structured-exception-handling-intrinsic-functions"></a>Wewnętrzne funkcje strukturalnej obsługi wyjątków

Strukturalna obsługa wyjątków udostępnia dwie funkcje wewnętrzne, które są dostępne do użycia z instrukcją **try-except** : [GetExceptionCode](/windows/win32/Debug/getexceptioncode) i [GetExceptionInformation](/windows/win32/Debug/getexceptioninformation).

`GetExceptionCode`zwraca kod (32-bitową liczbę całkowitą) wyjątku.

Funkcja `GetExceptionInformation` wewnętrzna zwraca wskaźnik do struktury [EXCEPTION_POINTERS](/windows/win32/api/winnt/ns-winnt-exception_pointers) zawierającej dodatkowe informacje o wyjątku. Za pomocą tego wskaźnika można uzyskać dostęp do stanu maszyny w momencie wystąpienia wyjątku sprzętowego. Struktura jest następująca:

```cpp
typedef struct _EXCEPTION_POINTERS {
    PEXCEPTION_RECORD ExceptionRecord;
    PCONTEXT ContextRecord;
} EXCEPTION_POINTERS, *PEXCEPTION_POINTERS;
```

Typy `PEXCEPTION_RECORD` wskaźnika `PCONTEXT` i są zdefiniowane w pliku \<dołączanym> Winnt. h, a `_EXCEPTION_RECORD` i `_CONTEXT` są zdefiniowane w pliku Dołącz plik \<EXCPT. h>

Można użyć `GetExceptionCode` wewnątrz procedury obsługi wyjątków. Jednak można użyć `GetExceptionInformation` tylko w wyrażeniu filtru wyjątków. Informacje, na które wskazuje, są zwykle na stosie i nie są już dostępne, gdy sterowanie jest przekazywane do programu obsługi wyjątków.

Funkcja wewnętrzna [AbnormalTermination](/windows/win32/Debug/abnormaltermination) jest dostępna w ramach procedury obsługi zakończenia. Zwraca wartość 0, jeśli treść instrukcji **try-finally** kończy się sekwencyjnie. We wszystkich pozostałych przypadkach zwraca wartość 1.

\<EXCPT. h> definiuje kilka alternatywnych nazw dla tych elementów wewnętrznych:

`GetExceptionCode`jest równoważne`_exception_code`

`GetExceptionInformation`jest równoważne`_exception_info`

`AbnormalTermination`jest równoważne`_abnormal_termination`

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

## <a name="see-also"></a>Zobacz także

[Pisanie procedury obsługi wyjątków](../cpp/writing-an-exception-handler.md)<br/>
[Obsługa wyjątków strukturalnych (C/C++)](../cpp/structured-exception-handling-c-cpp.md)<br/>
[Słowa kluczowe](../cpp/keywords-cpp.md)
