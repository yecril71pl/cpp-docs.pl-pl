---
title: try-except, instrukcja
description: Odwołanie do microsoft C++ do __try i __except ustrukturyzowanych instrukcji obsługi wyjątków.
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
ms.openlocfilehash: 132edf7cc9819637fafa3947686972d311924b99
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366237"
---
# <a name="try-except-statement"></a>try-except, instrukcja

Instrukcja **try-except** jest rozszerzeniem firmy Microsoft, które obsługuje obsługę wyjątków strukturalnych w językach C i C++. To rozszerzenie jest **specyficzne dla firmy Microsoft**.

## <a name="syntax"></a>Składnia

> **\_\_try**<br/>
> {<br/>
> &nbsp;&nbsp;&nbsp;&nbsp;kod strzeżony<br/>
> }<br/>
> z wyjątkiem ( *wyrażenie* ) ** \_ \_**<br/>
> {<br/>
> &nbsp;&nbsp;&nbsp;&nbsp;kod obsługi wyjątków<br/>
> }

## <a name="remarks"></a>Uwagi

Instrukcja **try-except** jest rozszerzeniem firmy Microsoft do języków C i C++. Umożliwia aplikacjom docelowym przejęcie kontroli po wystąpieniu zdarzeń, które zwykle kończą wykonywanie programu. Takie zdarzenia są nazywane *wyjątkami strukturalnymi*lub *w skrócie wyjątkami.* Mechanizm, który zajmuje się tymi wyjątkami jest nazywany *ustrukturyzowania obsługi wyjątków* (SEH).

Aby uzyskać powiązane informacje, zobacz [instrukcję try-finally](../cpp/try-finally-statement.md).

Wyjątki mogą być oparte na sprzęcie lub oprogramowaniu. Obsługa wyjątków strukturalnych jest przydatna nawet wtedy, gdy aplikacje nie mogą całkowicie odzyskać z wyjątków sprzętu lub oprogramowania. SEH umożliwia wyświetlanie informacji o błędzie i pułapkę na stan wewnętrzny aplikacji, aby pomóc zdiagnozować problem. Jest to szczególnie przydatne w przypadku sporadycznych problemów, które nie są łatwe do odtworzenia.

> [!NOTE]
> Strukturalna obsługa wyjątków działa z Win32 dla plików źródłowych C i C++. Jednak nie jest specjalnie zaprojektowany dla języka C++. Można zapewnić, że kod będzie bardziej przenośny przy użyciu obsługi wyjątków C++. Ponadto, obsługa wyjątków C++ jest bardziej elastyczna, gdyż może obsługiwać wyjątki dowolnego typu. W przypadku programów W++ zaleca się używanie natywnej obsługi wyjątków języka C++: [try, catch i throw](../cpp/try-throw-and-catch-statements-cpp.md) instrukcji.

Instrukcja złożona po **klauzuli __try** jest sekcją *nadwozia* lub *osłoniętą.* Wyrażenie **__except** jest również znane jako wyrażenie *filtru.* Jego wartość określa sposób obsługi wyjątku. Instrukcja compound po **klauzuli __except** jest program obsługi wyjątków. Program obsługi określa akcje do podjęcia, jeśli wyjątek jest wywoływany podczas wykonywania sekcji treści. Wykonanie przebiega w następujący sposób:

1. Sekcja chroniona jest wykonywana.

1. Jeśli podczas wykonywania sekcji chronionej nie wystąpi żaden wyjątek, wykonanie jest kontynuowane w instrukcji po **klauzuli __except.**

1. Jeśli wystąpi wyjątek podczas wykonywania sekcji chronionej lub w dowolnej procedurze wywołania sekcji chronionej, __except **wyrażenie** jest oceniane. Możliwe są trzy wartości:

   - `EXCEPTION_CONTINUE_EXECUTION`(-1) Wyjątek jest odrzucany. Kontynuuj wykonywanie w punkcie, w którym wystąpił wyjątek.

   - `EXCEPTION_CONTINUE_SEARCH`(0) Wyjątek nie jest rozpoznawany. Kontynuuj wyszukiwanie stosu dla programu obsługi, najpierw dla zawierające **try-except** instrukcji, a następnie dla programów obsługi z następnego najwyższego pierwszeństwa.

   - `EXCEPTION_EXECUTE_HANDLER`(1) Wyjątek jest rozpoznawany. Przenieś kontrolę do obsługi wyjątków, wykonując **__except** złożoną instrukcję, a następnie kontynuuj wykonywanie po **bloku __except.**

Wyrażenie **__except** jest oceniane jako wyrażenie C. Jest ograniczona do pojedynczej wartości, operatora wyrażenia warunkowego lub operatora przecinka. Jeśli wymagane jest bardziej rozległe przetwarzanie, wyrażenie może wywołać procedurę, która zwraca jedną z trzech wartości wymienionych powyżej.

Każda aplikacja może mieć własną obsługę wyjątków.

Nie jest prawidłowe, aby przejść do **__try** instrukcji, ale ważne, aby wyskoczyć z jednego. Program obsługi wyjątków nie jest wywoływana, jeśli proces zostanie zakończony w trakcie wykonywania **instrukcji try-except.**

Aby uzyskać zgodność z poprzednimi wersjami, **_try** **, _except**i **_leave** są synonimami **dla __try,** **__except**i **__leave,** chyba że określono opcję kompilatora [/Za \(Wyłącz rozszerzenia języka).](../build/reference/za-ze-disable-language-extensions.md)

### <a name="the-__leave-keyword"></a>Słowo kluczowe __leave

__leave **__leave** słowo kluczowe jest ważne tylko w chronionej sekcji **instrukcji try-except,** a jego efektem jest przeskoczenie na koniec sekcji chronionej. Wykonywanie jest kontynuowane po pierwszej instrukcji następującej po programie obsługi wyjątków.

Instrukcja **goto** może również wyskoczyć z sekcji strzeżonej i nie obniża wydajności, jak to ma w **instrukcji try-finally.** To dlatego, że odwijanie stosu nie występuje. Zaleca się jednak użycie słowa kluczowego **__leave,** a nie **instrukcji goto.** Powodem jest to, że jesteś mniej prawdopodobne, aby popełnić błąd programowania, jeśli sekcja strzeżona jest duża lub złożona.

### <a name="structured-exception-handling-intrinsic-functions"></a>Wewnętrzne funkcje strukturalnej obsługi wyjątków

Obsługa wyjątków strukturalnych zapewnia dwie wewnętrzne funkcje, które są dostępne do użycia z **instrukcją try-except:** [GetExceptionCode](/windows/win32/Debug/getexceptioncode) i [GetExceptionInformation](/windows/win32/Debug/getexceptioninformation).

`GetExceptionCode`zwraca kod (32-bitową liczbę całkowitą) wyjątku.

Funkcja `GetExceptionInformation` wewnętrzna zwraca wskaźnik do [struktury EXCEPTION_POINTERS](/windows/win32/api/winnt/ns-winnt-exception_pointers) zawierającej dodatkowe informacje o wyjątku. Za pomocą tego wskaźnika można uzyskać dostęp do stanu maszyny w momencie wystąpienia wyjątku sprzętowego. Struktura jest następująca:

```cpp
typedef struct _EXCEPTION_POINTERS {
    PEXCEPTION_RECORD ExceptionRecord;
    PCONTEXT ContextRecord;
} EXCEPTION_POINTERS, *PEXCEPTION_POINTERS;
```

Typy `PEXCEPTION_RECORD` wskaźników `PCONTEXT` i \<są zdefiniowane w pliku dołączanym> `_EXCEPTION_RECORD` `_CONTEXT` i są zdefiniowane \<w pliku include excpt.h>

Można użyć `GetExceptionCode` w ramach obsługi wyjątków. Można jednak używać `GetExceptionInformation` tylko w ramach wyrażenia filtru wyjątków. Informacje, które wskazuje na jest ogólnie na stosie i nie jest już dostępna, gdy kontrola zostanie przeniesiona do obsługi wyjątków.

Funkcja wewnętrzna [AbnormalTermination](/windows/win32/Debug/abnormaltermination) jest dostępna w ramach programu obsługi zakończenia. Zwraca wartość 0, jeśli treść instrukcji **try-finally** kończy się sekwencyjnie. We wszystkich pozostałych przypadkach zwraca wartość 1.

\<excpt.h> definiuje niektóre alternatywne nazwy dla tych wewnętrzną:

`GetExceptionCode`jest równoznaczne z`_exception_code`

`GetExceptionInformation`jest równoznaczne z`_exception_info`

`AbnormalTermination`jest równoznaczne z`_abnormal_termination`

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

## <a name="see-also"></a>Zobacz też

[Pisanie obsługi wyjątków](../cpp/writing-an-exception-handler.md)<br/>
[Obsługa wyjątków strukturalnych (C/C++)](../cpp/structured-exception-handling-c-cpp.md)<br/>
[Słowa kluczowe](../cpp/keywords-cpp.md)
