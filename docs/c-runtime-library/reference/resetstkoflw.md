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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: dfe0de4f48173a0e79bcdcfb24bfdf7a21f47a04
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81332818"
---
# <a name="_resetstkoflw"></a>_resetstkoflw

Odzyskuje z przepełnienia stosu.

> [!IMPORTANT]
> Tego interfejsu API nie można używać w aplikacjach wykonywanych w czasie wykonywania systemu Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT nieobjęte w aplikacjach platformy uniwersalnej systemu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Składnia

```C
int _resetstkoflw( void );
```

## <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli funkcja powiedzie się, zero, jeśli nie powiedzie się.

## <a name="remarks"></a>Uwagi

Funkcja **_resetstkoflw** odzyskuje z warunków przepełnienia stosu, umożliwiając programowi kontynuowanie, a nie niepowodzenie z błędem wyjątku krytycznego. Jeśli funkcja **_resetstkoflw** nie jest wywoływana, nie ma żadnych stron straży po poprzednim wyjątku. Następnym razem, gdy istnieje przepełnienie stosu, nie ma żadnych wyjątków i proces kończy się bez ostrzeżenia.

Jeśli wątek w aplikacji powoduje **wyjątek EXCEPTION_STACK_OVERFLOW,** wątek opuścił swój stos w stanie uszkodzonym. Jest to w przeciwieństwie do innych wyjątków, takich jak **EXCEPTION_ACCESS_VIOLATION** lub **EXCEPTION_INT_DIVIDE_BY_ZERO**, gdzie stos nie jest uszkodzony. Stos jest ustawiony na dowolnie małą wartość, gdy program jest po raz pierwszy załadowany. Stos następnie rośnie na żądanie, aby zaspokoić potrzeby wątku. Jest to realizowane przez umieszczenie strony z dostępem PAGE_GUARD na końcu bieżącego stosu. Aby uzyskać więcej informacji, zobacz [Tworzenie stron straży](/windows/win32/Memory/creating-guard-pages).

Gdy kod powoduje, że wskaźnik stosu, aby wskazać adres na tej stronie, występuje wyjątek i system wykonuje następujące trzy rzeczy:

- Usuwa ochronę PAGE_GUARD na stronie ochrony, dzięki czemu wątek może odczytywać i zapisywać dane w pamięci.

- Przydziela nową stronę straży, która znajduje się jedna strona poniżej ostatniej.

- Ponownie rozpoczyna instrukcję, która zgłosiła wyjątek.

W ten sposób system może automatycznie zwiększyć rozmiar stosu dla wątku. Każdy wątek w procesie ma maksymalny rozmiar stosu. Rozmiar stosu jest ustawiany w czasie kompilacji przez [/STACK (Stack Allocations)](../../build/reference/stack-stack-allocations.md)lub przez [stacksize](../../build/reference/stacksize.md) instrukcji w pliku .def dla projektu.

Po przekroczeniu tego maksymalnego rozmiaru stosu system wykonuje następujące trzy czynności:

- Usuwa ochronę PAGE_GUARD na stronie osłony, jak opisano wcześniej.

- Próbuje przydzielić nową stronę straży poniżej ostatniej. Jednak to nie powiedzie się, ponieważ maksymalny rozmiar stosu został przekroczony.

- Zgłasza wyjątek, tak aby wątek może obsługiwać go w bloku wyjątku.

Należy zauważyć, że w tym momencie stos nie ma już strony ochrony. Następnym razem, gdy program powiększa stos aż do końca, gdzie powinna istnieć strona straży, program zapisuje poza koniec stosu i powoduje naruszenie zasad dostępu.

Wywołaj **_resetstkoflw,** aby przywrócić stronę straży, gdy odzyskiwanie odbywa się po wyjątku przepełnienia stosu. Tę funkcję można wywołać od wewnątrz głównego obiektu bloku **__except** lub poza blokiem **__except.** Istnieją jednak pewne ograniczenia dotyczące tego, kiedy należy go używać. **_resetstkoflw** nigdy nie należy wywoływać z:

- Wyrażenie filtru.

- Funkcja filtrowania.

- Funkcja wywoływana z funkcji filtru.

- Blok **połowu.**

- Blok **__finally.**

W tych punktach stos nie jest jeszcze wystarczająco rozwiń.

Wyjątki przepełnienia stosu są generowane jako wyjątki strukturalne, a nie wyjątki C++, więc **_resetstkoflw** nie jest przydatne w zwykłym bloku **catch,** ponieważ nie będzie przechwytywać wyjątek przepełnienia stosu. Jednak jeśli [_set_se_translator](set-se-translator.md) jest używany do implementacji ustrukturyzowanych translator wyjątków, który zgłasza wyjątki C++ (jak w drugim przykładzie), wyjątek przepełnienia stosu powoduje wyjątek C++, który może być obsługiwany przez blok catch języka C++.

Nie jest bezpieczne do wywołania **_resetstkoflw** w bloku catch C++, który jest osiągany z wyjątku zgłaszanego przez funkcję translatora wyjątków strukturalnych. W takim przypadku miejsce na stosie nie jest zwalniany i wskaźnik stosu nie jest resetowany, dopóki poza catch bloku, mimo że destruktory zostały wywołane dla wszelkich zniszczalnych obiektów przed catch bloku. Ta funkcja nie powinna być wywoływana, dopóki miejsce na stosie nie zostanie zwolniona, a wskaźnik stosu zostanie zresetowany. W związku z tym należy wywołać tylko po wyjściu z bloku catch. Jak najmniej miejsca na stosie, jak to możliwe powinny być używane w bloku catch, ponieważ przepełnienie stosu, który występuje w bloku catch, który sam próbuje odzyskać z poprzedniego przepełnienia stosu nie jest możliwe do odzyskania i może spowodować, że program przestanie odpowiadać jako przepełnienie w bloku catch wyzwala wyjątek, który sam jest obsługiwany przez ten sam blok catch.

Istnieją sytuacje, w których **_resetstkoflw** może zakończyć się niepowodzeniem, nawet jeśli jest używany w odpowiedniej lokalizacji, na przykład w bloku **__except.** Jeśli nawet po odwijaniu stosu, nadal nie ma wystarczającej ilości miejsca na stosie, aby wykonać **_resetstkoflw** bez zapisu na ostatniej stronie stosu, **_resetstkoflw** nie można zresetować ostatniej strony stosu jako strony straży i zwraca 0, wskazując na błąd. W związku z tym bezpieczne użycie tej funkcji powinny obejmować sprawdzanie wartości zwracanej zamiast przy założeniu, że stos jest bezpieczny w użyciu.

Obsługa wyjątków strukturalnych nie spowoduje wyładunku wyjątku **STATUS_STACK_OVERFLOW,** gdy aplikacja jest kompilowana z **/clr** (zobacz [/clr (Kompilacja środowiska wykonawczego języka wspólnego).](../../build/reference/clr-common-language-runtime-compilation.md)

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_resetstkoflw**|\<> malloc.h|

Aby uzyskać więcej informacji o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

**Biblioteki:** Wszystkie wersje [funkcji biblioteki CRT](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Przykład

Poniższy przykład przedstawia zalecane użycie funkcji **_resetstkoflw.**

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

W poniższym przykładzie przedstawiono zalecane użycie **_resetstkoflw** w programie, w którym wyjątki strukturalne są konwertowane na wyjątki języka C++.

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
