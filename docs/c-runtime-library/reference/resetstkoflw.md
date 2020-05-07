---
title: _resetstkoflw
ms.date: 4/2/2020
api_name:
- _resetstkoflw
- _o__resetstkoflw
api_location:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- resetstkoflw
- _resetstkoflw
helpviewer_keywords:
- resetstkoflw function
- stack overflow
- stack, recovering
- _resetstkoflw function
ms.assetid: 319529cd-4306-4d22-810b-2063f3ad9e14
ms.openlocfilehash: b19b66279427aa4623cff037e67067096eb6bd42
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2020
ms.locfileid: "82917781"
---
# <a name="_resetstkoflw"></a>_resetstkoflw

Odzyskiwanie z przepełnienia stosu.

> [!IMPORTANT]
> Tego interfejsu API nie można używać w aplikacjach, które są wykonywane w środowisko wykonawcze systemu Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT nieobsługiwane w aplikacjach platforma uniwersalna systemu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Składnia

```C
int _resetstkoflw( void );
```

## <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli funkcja się powiedzie, zero, jeśli zakończy się niepowodzeniem.

## <a name="remarks"></a>Uwagi

Funkcja **_resetstkoflw** przywraca ze stanu przepełnienia stosu, umożliwiając programowi kontynuowanie zamiast niepowodzenia z powodu błędu krytycznego wyjątku. Jeśli funkcja **_resetstkoflw** nie jest wywoływana, nie ma żadnych stron ochrony po poprzednim wyjątku. Przy następnym przepełnieniu stosu nie ma żadnych wyjątków w ogóle i proces kończy się bez ostrzeżenia.

Jeśli wątek w aplikacji powoduje wyjątek **EXCEPTION_STACK_OVERFLOW** , wątek opuścił stos w stanie uszkodzenia. Jest to w przeciwieństwie do innych wyjątków, takich jak **EXCEPTION_ACCESS_VIOLATION** lub **EXCEPTION_INT_DIVIDE_BY_ZERO**, w których stos nie jest uszkodzony. Podczas pierwszego ładowania programu stos jest ustawiany na niewielką wartość. Stos zostanie następnie powiększony na żądanie, aby spełniał wymagania wątku. Jest to implementowane przez umieszczenie strony z dostępem PAGE_GUARD na końcu bieżącego stosu. Aby uzyskać więcej informacji, zobacz [Tworzenie stron ochrony](/windows/win32/Memory/creating-guard-pages).

Gdy kod powoduje, że wskaźnik stosu wskazuje na adres na tej stronie, wystąpi wyjątek, a system wykonuje następujące trzy rzeczy:

- Usuwa ochronę PAGE_GUARD na stronie Ochrona, aby wątek mógł odczytywać i zapisywać dane w pamięci.

- Przypisuje nową stronę ochrony, która znajduje się na jednej stronie poniżej ostatniej.

- Ponownie uruchamia instrukcję, która wywołała wyjątek.

W ten sposób system może automatycznie zwiększyć rozmiar stosu dla wątku. Każdy wątek w procesie ma maksymalny rozmiar stosu. Rozmiar stosu jest ustawiany w czasie kompilacji przez [/Stack (alokacje stosu)](../../build/reference/stack-stack-allocations.md)lub instrukcję [STACKSIZE](../../build/reference/stacksize.md) w pliku. def dla projektu.

Po przekroczeniu maksymalnego rozmiaru stosu system wykonuje następujące trzy czynności:

- Usuwa ochronę PAGE_GUARD na stronie Ochrona, jak opisano wcześniej.

- Próbuje przydzielić nową stronę ochrony poniżej ostatniej. Jednak to nie powiedzie się z powodu przekroczenia maksymalnego rozmiaru stosu.

- Wywołuje wyjątek, aby wątek mógł obsłużyć go w bloku wyjątków.

Należy pamiętać, że w tym momencie stos nie ma już strony ochrony. Przy następnym powiększeniu stosu przez program do końca, gdzie powinna być stroną ochrony, program zapisuje się poza końcem stosu i powoduje naruszenie zasad dostępu.

Wywołaj **_resetstkoflw** , aby przywrócić stronę ochrony po każdym zakończeniu odzyskiwania po wystąpieniu wyjątku przepełnienia stosu. Tę funkcję można wywołać z wewnątrz głównej treści bloku **__except** lub poza blokiem **__except** . Istnieją jednak pewne ograniczenia dotyczące sytuacji, w których należy korzystać z programu. nie należy wywoływać **_resetstkoflw** z:

- Wyrażenie filtru.

- Funkcja filtru.

- Funkcja wywołana z funkcji filtrowania.

- Blok **catch** .

- Blok **__finally** .

W tych punktach stos nie jest jeszcze wystarczająco rozrany.

Wyjątki przepełnienia stosu są generowane jako wyjątki strukturalne, nie wyjątki C++, więc **_resetstkoflw** nie są przydatne w przypadku zwykłego bloku **catch** , ponieważ nie przechwytuje wyjątku przepełnienia stosu. Jeśli jednak [_set_se_translator](set-se-translator.md) jest używany do implementowania translatora wyjątków strukturalnych, który zgłasza wyjątki C++ (jak w drugim przykładzie), wyjątek przepełnienia stosu spowoduje wyjątek języka c++, który może być obsługiwany przez blok catch języka c++.

Nie jest bezpieczne wywoływanie **_resetstkoflw** w bloku catch języka C++, który został osiągnięty od wyjątku zgłoszonego przez funkcję translatora wyjątków strukturalnych. W takim przypadku przestrzeń stosu nie jest zwalniana, a wskaźnik stosu nie jest resetowany do zewnątrz bloku catch, chociaż destruktory zostały wywołane dla wszystkich obiektów zniszczalnych przed blokiem catch. Ta funkcja nie powinna być wywoływana do momentu zwolnienia przestrzeni stosu i zresetowania wskaźnika stosu. W związku z tym należy ją wywołać tylko po opuszczeniu bloku catch. W bloku catch należy używać możliwie najmniejszej ilości miejsca w stosie, ponieważ przepełnienie stosu, który występuje w bloku catch, który jest samo próba odzyskania z poprzedniego przepełnienia stosu, nie jest możliwe do odzyskania i może spowodować, że program przestanie odpowiadać, ponieważ przepełnienie w bloku catch wyzwala wyjątek, który jest obsługiwany przez ten sam blok catch.

Istnieją sytuacje, w których **_resetstkoflw** mogą kończyć się niepowodzeniem nawet wtedy, gdy są używane w poprawnej lokalizacji, na przykład w bloku **__except** . Jeśli nawet po rozmieszczeniu stosu nadal nie ma wystarczającej ilości miejsca na stosie, aby wykonać **_resetstkoflw** bez zapisywania na ostatniej stronie stosu, **_resetstkoflw** nie może zresetować ostatniej strony stosu jako strony ochrony i zwróci wartość 0, wskazując awarię. W związku z tym bezpieczne użycie tej funkcji powinno obejmować sprawdzenie wartości zwracanej zamiast zagwarantowania, że stos jest bezpieczny do użycia.

Strukturalna obsługa wyjątków nie przechwytuje wyjątku **STATUS_STACK_OVERFLOW** , gdy aplikacja zostanie skompilowana z **/CLR** (zobacz [/CLR (Kompilacja środowiska uruchomieniowego języka wspólnego)](../../build/reference/clr-common-language-runtime-compilation.md)).

Domyślnie globalny stan tej funkcji jest objęty zakresem aplikacji. Aby to zmienić, zobacz [stan globalny w CRT](../global-state.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_resetstkoflw**|\<malloc. h>|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

**Biblioteki:** Wszystkie wersje [funkcji biblioteki CRT](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Przykład

W poniższym przykładzie pokazano zalecane użycie funkcji **_resetstkoflw** .

```C
// crt_resetstkoflw.c
// Launch program with and without arguments to observe
// the difference made by calling _resetstkoflw.

#include <malloc.h>
#include <stdio.h>
#include <windows.h>

void recursive(int recurse)
{
   _alloca(2000);
   if (recurse)
      recursive(recurse);
}

// Filter for the stack overflow exception.
// This function traps the stack overflow exception, but passes
// all other exceptions through.
int stack_overflow_exception_filter(int exception_code)
{
   if (exception_code == EXCEPTION_STACK_OVERFLOW)
   {
       // Do not call _resetstkoflw here, because
       // at this point, the stack is not yet unwound.
       // Instead, signal that the handler (the __except block)
       // is to be executed.
       return EXCEPTION_EXECUTE_HANDLER;
   }
   else
       return EXCEPTION_CONTINUE_SEARCH;
}

int main(int ac)
{
   int i = 0;
   int recurse = 1, result = 0;

   for (i = 0 ; i < 10 ; i++)
   {
      printf("loop #%d\n", i + 1);
      __try
      {
         recursive(recurse);

      }

      __except(stack_overflow_exception_filter(GetExceptionCode()))
      {
         // Here, it is safe to reset the stack.

         if (ac >= 2)
         {
            puts("resetting stack overflow");
            result = _resetstkoflw();
         }
      }

      // Terminate if _resetstkoflw failed (returned 0)
      if (!result)
         return 3;
   }

   return 0;
}
```

Przykładowe dane wyjściowe bez argumentów programu:

```Output
loop #1
```

Program przestaje odpowiadać bez wykonywania dalszych iteracji.

Z argumentami programu:

```Output
loop #1
resetting stack overflow
loop #2
resetting stack overflow
loop #3
resetting stack overflow
loop #4
resetting stack overflow
loop #5
resetting stack overflow
loop #6
resetting stack overflow
loop #7
resetting stack overflow
loop #8
resetting stack overflow
loop #9
resetting stack overflow
loop #10
resetting stack overflow
```

### <a name="description"></a>Opis

W poniższym przykładzie przedstawiono zalecane użycie **_resetstkoflw** w programie, w którym strukturalne wyjątki są konwertowane na wyjątki C++.

### <a name="code"></a>Code

```cpp
// crt_resetstkoflw2.cpp
// compile with: /EHa
// _set_se_translator requires the use of /EHa
#include <malloc.h>
#include <stdio.h>
#include <windows.h>
#include <eh.h>

class Exception { };

class StackOverflowException : Exception { };

// Because the overflow is deliberate, disable the warning that
// this function will cause a stack overflow.
#pragma warning (disable: 4717)
void CauseStackOverflow (int i)
{
    // Overflow the stack by allocating a large stack-based array
    // in a recursive function.
    int a[10000];
    printf("%d ", i);
    CauseStackOverflow (i + 1);
}

void __cdecl SEHTranslator (unsigned int code, _EXCEPTION_POINTERS*)
{
    // For stack overflow exceptions, throw our own C++
    // exception object.
    // For all other exceptions, throw a generic exception object.
    // Use minimal stack space in this function.
    // Do not call _resetstkoflw in this function.

    if (code == EXCEPTION_STACK_OVERFLOW)
        throw StackOverflowException ( );
    else
        throw Exception( );
}

int main ( )
{
    bool stack_reset = false;
    bool result = false;

    // Set up a function to handle all structured exceptions,
    // including stack overflow exceptions.
    _set_se_translator (SEHTranslator);

    try
    {
        CauseStackOverflow (0);
    }
    catch (StackOverflowException except)
    {
        // Use minimal stack space here.
        // Do not call _resetstkoflw here.
        printf("\nStack overflow!\n");
        stack_reset = true;
    }
    catch (Exception except)
    {
        // Do not call _resetstkoflw here.
        printf("\nUnknown Exception!\n");
    }
    if (stack_reset)
    {
        result = _resetstkoflw();
        // If stack reset failed, terminate the application.
        if (result == 0)
            exit(1);
    }

    void* pv = _alloca(100000);
    printf("Recovered from stack overflow and allocated 100,000 bytes"
           " using _alloca.");

    return 0;
}
```

```Output
0 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 20 21 22 23 24
Stack overflow!
Recovered from stack overflow and allocated 100,000 bytes using _alloca.
```

## <a name="see-also"></a>Zobacz też

[_alloca](alloca.md)<br/>
