---
title: "Spróbuj-except — instrukcja | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- _abnormal_termination_cpp
- _exception_code_cpp
- EXCEPTION_CONTINUE_SEARCH
- _exception_info
- __except
- EXCEPTION_CONTINUE_EXECUTION
- _exception_code
- __except_cpp
- _exception_info_cpp
- EXCEPTION_EXECUTE_HANDLER
- _abnormal_termination
dev_langs: C++
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
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 12aeb14d63f20592c94292b1548a8d3d700fef0b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="try-except-statement"></a>try-except — instrukcja

**Dotyczące firmy Microsoft**  
**Spróbuj — z wyjątkiem** instrukcji to rozszerzenie firmy Microsoft do C i obsługa wyjątków strukturalnych języków C++, które obsługuje.  

## <a name="syntax"></a>Składnia  
  
> **__try**   
> {  
>    Kod ochroną  
> }  
> **__except** ( *wyrażenie* )  
> {  
>    Kod obsługi wyjątków  
> }  

## <a name="remarks"></a>Uwagi

**Spróbuj — z wyjątkiem** instrukcji to rozszerzenie firmy Microsoft do C i języków C++, które umożliwia aplikacji docelowych w celu uzyskania kontroli, gdy występują zdarzenia, które zwykle na zakończenie wykonywania programu. Takie zdarzenia są nazywane *wyjątki*, i nosi nazwę mechanizm, który zajmuje się wyjątki *Obsługa wyjątków strukturalnych* (SEH).

Aby uzyskać odpowiednie informacje, zobacz [try-finally — instrukcja](../cpp/try-finally-statement.md).

Wyjątki mogą być sprzętowe lub programowe. Nawet wtedy, gdy aplikacje nie mogą całkowicie odzyskać sprawności po wystąpieniu wyjątku sprzętowego lub programowego, strukturalna obsługa wyjątków umożliwia wyświetlenie informacji o błędzie i pozwala na przechwycenie wewnętrznego stanu aplikacji, aby pomóc w zdiagnozowaniu problemu. Jest to szczególnie użyteczne w przypadku sporadycznych problemów, których nie można łatwo odtworzyć.

> [!NOTE]
> Strukturalna obsługa wyjątków działa z Win32 dla plików źródłowych C i C++. Jednakże nie jest specjalnie zaprojektowana dla języka C++. Można zapewnić, że kod będzie bardziej przenośny przy użyciu obsługi wyjątków C++. Ponadto, obsługa wyjątków C++ jest bardziej elastyczna, gdyż może obsługiwać wyjątki dowolnego typu. Dla programów C++, zaleca się użycie mechanizmu obsługi wyjątków języka C++ ([spróbuj, catch i zgłosić](../cpp/try-throw-and-catch-statements-cpp.md) instrukcje).

Instrukcja złożona po klauzuli `__try` jest ciałem sekcji chronionej. Złożone wyrażenie po klauzuli `__except` to program obsługi wyjątków. Kod obsługi wyjątku określa zestaw akcji, które zostaną wykonane, jeśli wystąpi wyjątek w ciele chronionej sekcji. Wykonanie przebiega w następujący sposób:

1. Sekcja chroniona jest wykonywana.

2. Jeśli podczas wykonywania sekcji chronionej nie wystąpi wyjątek, program kontynuuje wykonywanie instrukcji po klauzuli `__except`.  

3. Jeśli wystąpi wyjątek podczas wykonywania sekcji ochroną lub w dowolnej procedury wywołuje sekcji ochroną, `__except` *wyrażenie* (o nazwie *filtru* wyrażenie) jest obliczane i wartości Określa sposób obsługi wyjątków. Istnieją trzy wartości:

   **Exception_continue_execution — (-1)** wyjątku jest odrzucane. Kontynuuj wykonywanie w punkcie, w którym wystąpił wyjątek.

   **Exception_continue_search — (0)** wyjątek nie został rozpoznany. Kontynuować wyszukiwanie górę stosu w przypadku obsługi najpierw zawierający **spróbuj — z wyjątkiem** instrukcje, a następnie dla programów obsługi o najwyższym priorytecie dalej.

   **Exception_execute_handler — (1)** wyjątek został rozpoznany. Przenieś kontrolę do obsługi wyjątków przez wykonanie złożonego wyrażenia `__except`, a następnie kontynuuj wykonywanie po bloku `__except`.

Ponieważ `__except` wyrażenie jest obliczane jako wyrażenie C, jest ograniczona do jednej wartości, operator wyrażenia warunkowego lub przecinka. Jeśli wymagane jest bardziej rozległe przetwarzanie, wyrażenie może wywołać procedurę, która zwraca jedną z trzech wartości wymienionych powyżej.

Każda aplikacja może mieć własną obsługę wyjątków.

Niedozwolone jest przejście do instrukcji `__try`, ale dozwolone jest wyjście z niej. Program obsługi wyjątku nie jest wywoływana, gdy proces zostanie zakończony w trakcie wykonywania **spróbuj — z wyjątkiem** instrukcji.  
  
Aby uzyskać więcej informacji, zobacz artykuł z bazy wiedzy Q315937: HOW TO: Trap Stack Overflow in a Visual C++ Application.  
  
## <a name="the-leave-keyword"></a>Słowo kluczowe __leave

`__leave` — Słowo kluczowe jest prawidłowy tylko wewnątrz sekcji ochroną **spróbuj — z wyjątkiem** instrukcji, a jego wpływ jest przejście do końca sekcji ochroną. Wykonywanie jest kontynuowane po pierwszej instrukcji następującej po programie obsługi wyjątków.

A `goto` instrukcja również może wykonać skok poza sekcji ochroną i go nie zmniejsza wydajność, co w **try-finally** instrukcji ponieważ odwijanie stosu nie występuje. Jednakże, Microsoft zaleca użycie słowa kluczowego `__leave` zamiast instrukcji `goto` ponieważ zmniejsza to prawdopodobieństwo wystąpienia błędu w dużej lub złożonej sekcji chronionej.

### <a name="structured-exception-handling-intrinsic-functions"></a>Wewnętrzne funkcje strukturalnej obsługi wyjątków

Obsługa wyjątków strukturalnych oferuje dwie funkcje wewnętrzne, które są dostępne do użycia z **spróbuj — z wyjątkiem** instrukcji: `GetExceptionCode` i `GetExceptionInformation`.

`GetExceptionCode`Zwraca numer kierunkowy wyjątku (32-bitowa liczba całkowita).

Wewnętrzna funkcja `GetExceptionInformation` zwraca wskaźnik do struktury, zawierający dodatkowe informacje o wyjątku. Za pomocą tego wskaźnika można uzyskać dostęp do stanu maszyny w momencie wystąpienia wyjątku sprzętowego. Struktura jest następująca:

```cpp  
typedef struct _EXCEPTION_POINTERS {
    PEXCEPTION_RECORD ExceptionRecord;
    PCONTEXT ContextRecord;
} EXCEPTION_POINTERS, *PEXCEPTION_POINTERS; 
```  

Typy wskaźników `PEXCEPTION_RECORD` i `PCONTEXT` są zdefiniowane w pliku dołączanego Windows NT. H, i `_EXCEPTION_RECORD` i `_CONTEXT` są zdefiniowane w pliku dyrektywy include z wyjątkiem. H

Można użyć `GetExceptionCode` wewnątrz obsługi wyjątków. Można jednak użyć `GetExceptionInformation` tylko w wyrażeniu filtru wyjątków. Informacje na które wskazuje są na ogół na stosie i nie są dostępne po przekazaniu kontroli do programu obsługi wyjątków.

Wewnętrzna funkcja `AbnormalTermination` jest dostępna w ramach programu obsługi zakończenia. Zwraca 0, jeśli treść **try-finally** instrukcji kończy się po kolei. We wszystkich pozostałych przypadkach zwraca wartość 1.

EXCPT.H definiuje kilka nazw alternatywnych dla funkcji wewnętrznych:

`GetExceptionCode`jest odpowiednikiem`_exception_code`

 `GetExceptionInformation`jest odpowiednikiem`_exception_info`

 `AbnormalTermination`jest odpowiednikiem`_abnormal_termination`
  
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
  
## <a name="output"></a>Dane wyjściowe  
  
```  
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

**KOŃCOWY określonych firmy Microsoft**  

## <a name="see-also"></a>Zobacz też

[Pisanie programu do obsługi wyjątków](../cpp/writing-an-exception-handler.md)   
[(C/C++) obsługi wyjątków strukturalnych](../cpp/structured-exception-handling-c-cpp.md)   
[Słowa kluczowe](../cpp/keywords-cpp.md)
