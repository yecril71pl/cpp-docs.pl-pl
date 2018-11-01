---
title: _resetstkoflw
ms.date: 11/04/2016
apiname:
- _resetstkoflw
apilocation:
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
apitype: DLLExport
f1_keywords:
- resetstkoflw
- _resetstkoflw
helpviewer_keywords:
- resetstkoflw function
- stack overflow
- stack, recovering
- _resetstkoflw function
ms.assetid: 319529cd-4306-4d22-810b-2063f3ad9e14
ms.openlocfilehash: ad8c9b470c33a4c84f46ac7758d368917e7938e0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50480551"
---
# <a name="resetstkoflw"></a>_resetstkoflw

Odzyskuje z przepełnienia stosu.

> [!IMPORTANT]
> Tego API nie można używać w aplikacjach korzystających ze środowiska wykonawczego Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT nieobsługiwane w aplikacjach platformy uniwersalnej Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Składnia

```C
int _resetstkoflw( void );
```

## <a name="return-value"></a>Wartość zwracana

Różna od zera, jeśli funkcja się powiedzie, zero, jeśli zakończy się niepowodzeniem.

## <a name="remarks"></a>Uwagi

**_Resetstkoflw** funkcji odzyskiwania sprawności stanu przepełnienia stosu, pozwalając programowi na kontynuowanie zamiast zwracając błąd wyjątku krytycznego. Jeśli **_resetstkoflw** funkcja nie jest wywoływana, istnieją żadnych stron zabezpieczenia po poprzednim wyjątku. Przepełnienie podczas następnego to stosu, w ogóle nie ma żadnych wyjątków, a proces zakończy się bez ostrzeżenia.

Jeśli wątek w aplikacji powoduje, że **EXCEPTION_STACK_OVERFLOW** wyjątku, wątek opuścił stos w stanie uszkodzonym. Jest to w przeciwieństwie do innych wyjątków takich jak **EXCEPTION_ACCESS_VIOLATION** lub **EXCEPTION_INT_DIVIDE_BY_ZERO**, gdy stos nie jest uszkodzony. Stos jest ustawiony na arbitralnie małej wartości, gdy program jest ładowany. Stos następnie rośnie na żądanie do potrzeb wątku. To jest zaimplementowane przez umieszczenie strony z dostępem do PAGE_GUARD na końcu bieżącego stosu. Aby uzyskać więcej informacji, zobacz [tworzenie stron ochrony](/windows/desktop/Memory/creating-guard-pages).

Gdy kod powoduje, że wskaźnik stosu wskazuje adres na tej stronie, wystąpi wyjątek, a system wykonuje następujące czynności:

- Usuwa ochronę PAGE_GUARD na stronie ochrony, tak aby wątek mógł czytać i zapisywać dane do pamięci.

- Przydziela nowego strażnika stronie oznacza to znajduje się jedną stronę poniżej ostatniej z nich.

- Umożliwia ponowne wykonanie instrukcji, która wywołała wyjątek.

W ten sposób system może automatycznie zwiększyć rozmiar stosu dla wątku. Każdy wątek w procesie ma rozmiar maksymalny stosu. Rozmiar stosu jest ustawiony w czasie kompilacji przez [/STACK (twórz stos z alokacji)](../../build/reference/stack-stack-allocations.md), lub [STACKSIZE](../../build/reference/stacksize.md) instrukcja w pliku o rozszerzeniu def dla projektu.

Po przekroczeniu tej wielkości maksymalnej stosu, system wykonuje następujące czynności:

- Usuwa ochronę PAGE_GUARD na stronie, jak opisano wcześniej.

- Próbuje przydzielić nowe strony strażnika poniżej ostatniej z nich. Jednak to nie działa, ponieważ przekroczono maksymalny rozmiar stosu.

- Zgłasza wyjątek, tak aby wątek mógł go obsłużyć w bloku wyjątków.

Należy pamiętać, że w tym momencie stos nie ma już strony ochronnej. Następnym razem, gdy program rozwija stos aż do końca, gdzie powinna być strona ochrona, program zapisuje poza końcem stosu i powoduje naruszenie zasad dostępu.

Wywołaj **_resetstkoflw** Aby przywrócić stronę ochronną przy każdym odzyskiwaniu po wyjątku przepełnienia stosu. Ta funkcja może zostać wywołana z wnętrza głównego tekstu z **__except** bloku lub poza **__except** bloku. Istnieją jednak pewne ograniczenia dotyczące kiedy należy użyć. **_resetstkoflw** nigdy nie powinna być wywoływana z:

- Wyrażenie filtru.

- Funkcja filtrowania.

- Funkcja wywoływana z funkcji filtru.

- A **catch** bloku.

- A **__finally** bloku.

W tych punktach stos nie jest jeszcze wystarczająco rozwinięty.

Wyjątki przepełnienia stosu są generowane jako wyjątki strukturalne, nie wyjątki C++, więc **_resetstkoflw** nie jest użyteczny w zwykłej **catch** bloku, ponieważ nie będzie przechwytywać wyjątków przepełnienia stosu. Jednak jeśli [_set_se_translator](set-se-translator.md) jest używany do implementowania translatora złożonego wyjątku, który wyrzuca wyjątki C++ (jak w drugim przykładzie), catch powoduje wyjątek przepełnienia stosu wyjątku C++, który może zostać obsłużony przez C++ blok.

Nie jest bezpieczne wywołanie **_resetstkoflw** w bloku catch języka C++, który zostanie osiągnięty z wyjątku wyrzuconego przez strukturalną funkcję tłumacza wyjątków. W tym przypadku przestrzeń stosu nie jest zwalniana, a wskaźnik stosu nie jest resetowana do momentu poza blok catch, choć destruktory zostały wywołane do wszelkich obiektów zniszczalnych przed blokiem catch. Ta funkcja nie powinna być wywoływana, dopóki nie zostanie zwolnione miejsca na stosie i wskaźnik stosu zostało zresetowane. W związku z tym powinien zostać wywołany tylko po wyjściu bloku catch. Małego obszar stosu, jak to możliwe należy użyć w bloku catch, ponieważ przepełnienie stosu, który występuje w bloku catch, który jest elementem próby odzyskania z poprzednim przepełnieniu stosu nie jest możliwe do odzyskania i może spowodować, że program przestanie odpowiadać jako przeciążenia blok catch wyjątku, który sam jest obsługiwany przez ten sam w wyzwalaczach bloku catch.

Istnieją sytuacje, gdzie **_resetstkoflw** może zakończyć się niepowodzeniem, nawet jeśli używane w poprawnej lokalizacji, na przykład w ramach **__except** bloku. Jeśli nawet po odwinięciu stosu, wciąż Brak wystarczającej ilości miejsca stosu do wykonania **_resetstkoflw** bez pisania na ostatniej stronie stosu, **_resetstkoflw** nie będzie mogła zresetować ostatniej strony stosu jako strony ochronnej i zwraca wartość 0, wskazując niepowodzenie. W związku z tym bezpieczne korzystanie z tej funkcji powinno obejmować sprawdzenie wartości zwracanej, a, przy założeniu, że stos jest bezpieczny w użyciu.

Obsługa wyjątków strukturalnych nie będzie przechwytywać **STATUS_STACK_OVERFLOW** wyjątek podczas kompilowania aplikacji za pomocą **/CLR** (zobacz [kompilacji/CLR (Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md)).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_resetstkoflw**|\<malloc.h>|

Aby uzyskać więcej informacji na temat zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

**Biblioteki:** wszystkie wersje [funkcje biblioteki CRT](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Przykład

Poniższy przykład pokazuje rekomendowane użycie funkcji **_resetstkoflw** funkcji.

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

Program przestaje odpowiadać bez dalszego wykonywania iteracji.

Bez argumentów programu:

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

Poniższy kod przedstawia zalecane użycie **_resetstkoflw** w programie, gdzie strukturalne wyjątki są konwertowane na wyjątki C++.

### <a name="code"></a>Kod

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

## <a name="see-also"></a>Zobacz także

[_alloca](alloca.md)<br/>
