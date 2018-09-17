---
title: Spróbuj-except, instrukcja | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c2780697c1a50e15e170f2096a2841e2c50d844a
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45724688"
---
# <a name="try-except-statement"></a>try-except — instrukcja

**Microsoft Specific**

**Spróbuj — z wyjątkiem** instrukcja jest rozszerzeniem firmy Microsoft do C i języków C++, które obsługuje obsługę wyjątków strukturalnych.  

## <a name="syntax"></a>Składnia  
  
> **__try**   
> {  
>    Kod chronionych  
> }  
> **__except** ( *wyrażenie* )  
> {  
>    Kod obsługi wyjątków  
> }  

## <a name="remarks"></a>Uwagi

**Spróbuj — z wyjątkiem** instrukcja jest rozszerzeniem firmy Microsoft do C i języków C++, które umożliwiają aplikacji docelowej uzyskanie kontroli, kiedy występują zdarzenia, które normalnie zakończyć wykonywania programu. Takie zdarzenia nazywane są *wyjątki*, a mechanizm, który zajmuje się wyjątkami nazywa się *obsługę wyjątków strukturalnych* (SEH).

Aby uzyskać powiązane informacje, zobacz [try-finally — instrukcja](../cpp/try-finally-statement.md).

Wyjątki mogą być sprzętowe lub programowe. Nawet wtedy, gdy aplikacje nie mogą całkowicie odzyskać sprawności po wystąpieniu wyjątku sprzętowego lub programowego, strukturalna obsługa wyjątków umożliwia wyświetlenie informacji o błędzie i pozwala na przechwycenie wewnętrznego stanu aplikacji, aby pomóc w zdiagnozowaniu problemu. Jest to szczególnie użyteczne w przypadku sporadycznych problemów, których nie można łatwo odtworzyć.

> [!NOTE]
> Strukturalna obsługa wyjątków działa z Win32 dla plików źródłowych C i C++. Jednakże nie jest specjalnie zaprojektowana dla języka C++. Można zapewnić, że kod będzie bardziej przenośny przy użyciu obsługi wyjątków C++. Ponadto, obsługa wyjątków C++ jest bardziej elastyczna, gdyż może obsługiwać wyjątki dowolnego typu. Programy w języku C++, zalecane jest używanie mechanizmu obsługi wyjątków C++ ([try, catch i throw](../cpp/try-throw-and-catch-statements-cpp.md) instrukcji).

Instrukcja złożona po **__try** klauzula jest ciałem sekcji chronionej. Instrukcja złożona po **__except** klauzula jest program obsługi wyjątków. Kod obsługi wyjątku określa zestaw akcji, które zostaną wykonane, jeśli wystąpi wyjątek w ciele chronionej sekcji. Wykonanie działa w następujący sposób:

1. Sekcja chroniona jest wykonywana.

2. Jeśli nie wystąpi wyjątek podczas wykonywania sekcji chronionej, wykonywanie jest kontynuowane na instrukcji znajdującej się po **__except** klauzuli.  

3. Jeśli wystąpi wyjątek podczas wykonywania sekcji chronionej lub w dowolnej procedurze, wywołuje sekcję chronioną, **__except** *wyrażenie* (o nazwie *filtru* wyrażenia) jest obliczane i wartość określa sposób obsługi wyjątku. Istnieją trzy wartości:

   EXCEPTION_CONTINUE_EXECUTION (-1) wyjątek zostaje odrzucony. Kontynuuj wykonywanie w punkcie, w którym wystąpił wyjątek.

   Wyjątek EXCEPTION_CONTINUE_SEARCH (0) nie została rozpoznana. Kontynuuj przeszukiwanie stosu obsługi, najpierw zawierającego wyrażenia **spróbuj — z wyjątkiem** instrukcji, następnie obsługi z następnym największym priorytetem.

   EXCEPTION_EXECUTE_HANDLER (1) wyjątek został rozpoznany. Kontrola jest przekazywana do programu obsługi wyjątków przez wykonanie **__except** instrukcja złożona (c), a następnie kontynuuj wykonywanie po **__except** bloku.

Ponieważ **__except** wyrażenie jest obliczane jak wyrażenie C, zatem zostaje ograniczone do pojedynczej wartości, operator wyrażenia warunkowego lub operatora przecinka. Jeśli wymagane jest bardziej rozległe przetwarzanie, wyrażenie może wywołać procedurę, która zwraca jedną z trzech wartości wymienionych powyżej.

Każda aplikacja może mieć własną obsługę wyjątków.

Nie jest prawidłową realizowanie **__try** instrukcji, ale dozwolone jest wyjście z niej. Obsługa wyjątków nie jest wywoływana, gdy proces zostanie zakończony w środku wykonywania wyrażenia **spróbuj — z wyjątkiem** instrukcji.  
  
Aby uzyskać więcej informacji, zobacz artykuł z bazy wiedzy Q315937: HOW TO: Trap Stack Overflow in a Visual C++ Application.  
  
## <a name="the-leave-keyword"></a>Słowo kluczowe __leave

**__Leave** — słowo kluczowe jest prawidłowy tylko wewnątrz sekcji chronionej **spróbuj — z wyjątkiem** instrukcji, a jego efektem jest przeskoczenie do końca sekcji chronionej. Wykonywanie jest kontynuowane po pierwszej instrukcji następującej po programie obsługi wyjątków.

A **goto** instrukcji może również przeskoczyć poza sekcję chronioną i nie zmniejsza wydajność co w **try-finally** instrukcji, ponieważ nie występuje odwrócenie stosu. Jednak firma Microsoft zaleca użycie **__leave** — słowo kluczowe zamiast **goto** instrukcji, ponieważ jest mniej prawdopodobne się zdarzyć, jeśli dużej lub złożonej sekcji chronionej.

### <a name="structured-exception-handling-intrinsic-functions"></a>Wewnętrzne funkcje strukturalnej obsługi wyjątków

Strukturalna obsługa wyjątków zapewnia dwie funkcje wewnętrzne, które są dostępne do użycia z **spróbuj — z wyjątkiem** instrukcji: `GetExceptionCode` i `GetExceptionInformation`.

`GetExceptionCode` Zwraca kod wyjątku (liczba całkowita 32-bitowe).

Wewnętrzna funkcja `GetExceptionInformation` zwraca wskaźnik do struktury zawierającej dodatkowe informacje o wyjątku. Za pomocą tego wskaźnika można uzyskać dostęp do stanu maszyny w momencie wystąpienia wyjątku sprzętowego. Struktura jest następująca:

```cpp  
typedef struct _EXCEPTION_POINTERS {
    PEXCEPTION_RECORD ExceptionRecord;
    PCONTEXT ContextRecord;
} EXCEPTION_POINTERS, *PEXCEPTION_POINTERS; 
```  

Typy wskaźników `PEXCEPTION_RECORD` i `PCONTEXT` są zdefiniowane w dołączanym pliku \<opis pliku winnt.h >, a `_EXCEPTION_RECORD` i `_CONTEXT` są zdefiniowane w dołączanym pliku \<excpt.h >

Możesz użyć `GetExceptionCode` w ramach programu obsługi wyjątków. Można jednak użyć `GetExceptionInformation` tylko w wyrażeniu filtru wyjątków. Informacje na które wskazuje są na ogół na stosie i nie są dostępne po przekazaniu kontroli do programu obsługi wyjątków.

Wewnętrzna funkcja `AbnormalTermination` jest dostępna w ramach programu obsługi zakończenia. Zwraca 0, jeśli treść **try-finally** kończy się sekwencyjnie. We wszystkich pozostałych przypadkach zwraca wartość 1.

excpt.h definiuje kilka nazw alternatywnych dla funkcji wewnętrznych:

`GetExceptionCode` jest odpowiednikiem `_exception_code`

 `GetExceptionInformation` jest odpowiednikiem `_exception_info`

 `AbnormalTermination` jest odpowiednikiem `_abnormal_termination`
  
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

**END specyficzny dla Microsoft**  

## <a name="see-also"></a>Zobacz także
 [Pisanie programu do obsługi wyjątków](../cpp/writing-an-exception-handler.md)   
 [Obsługa wyjątków strukturalnych (C/C++)](../cpp/structured-exception-handling-c-cpp.md)   
 [Słowa kluczowe](../cpp/keywords-cpp.md)