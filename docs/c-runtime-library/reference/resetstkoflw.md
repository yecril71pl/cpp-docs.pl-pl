---
title: _resetstkoflw | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _resetstkoflw
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
dev_langs: C++
helpviewer_keywords:
- resetstkoflw function
- stack overflow
- stack, recovering
- _resetstkoflw function
ms.assetid: 319529cd-4306-4d22-810b-2063f3ad9e14
caps.latest.revision: "20"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 5bebef156656ba3618c216ad8266e1baf5dd7f9b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="resetstkoflw"></a>_resetstkoflw
Odzyskuje z przepełnienia stosu.  
  
> [!IMPORTANT]
>  Nie można używać tego interfejsu API w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT, nie są obsługiwane z parametrem /ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## <a name="syntax"></a>Składnia  
  
```  
  
int _resetstkoflw ( void );  
  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli funkcja zakończy się powodzeniem, zero, jeśli działanie nie powiodło się.  
  
## <a name="remarks"></a>Uwagi  
 `_resetstkoflw` Funkcji odzyskiwania z przepełnienie stosu, dzięki czemu program kontynuowanie zamiast się niepowodzeniem z powodu błędu wyjątek krytyczny. Jeśli `_resetstkoflw` funkcja nie jest wywoływana, Brak stron guard po poprzedniego wyjątku. Przepełnienie przy następnym Brak stosu, w ogóle nie ma żadnych wyjątków i kończy proces bez ostrzeżenia.  
  
 Jeśli powoduje, że wątek w aplikacji **EXCEPTION_STACK_OVERFLOW** wyjątek, wątek opuścił jego stosu w stanie uszkodzenia. Dzięki temu nie trzeba pozostałe wyjątki takich jak **EXCEPTION_ACCESS_VIOLATION** lub **EXCEPTION_INT_DIVIDE_BY_ZERO**, gdy stos nie jest uszkodzony. Stos ustawiono arbitralnie mała wartość po raz pierwszy załadowano program. Stos następnie rozwoju na żądanie w celu spełnienia potrzeb wątku. Ten sposób jest implementowany przez umieszczenie strony z dostępem PAGE_GUARD na koniec bieżącego stosu. Aby uzyskać więcej informacji, zobacz [tworzenie stron Guard](http://msdn.microsoft.com/library/windows/desktop/aa366549).  
  
 Gdy kod powoduje wskaźnik stosu wskazywał adres na tej stronie, wystąpi wyjątek i system wykonuje następujących czynności:  
  
-   Usuwa ochronę PAGE_GUARD na stronie zabezpieczenia, dzięki czemu wątek może odczytywania i zapisywania danych do pamięci.  
  
-   Przydziela guard nowej strony czyli znajduje się jeden poniżej ostatnią.  
  
-   Umożliwia ponowne wykonanie instrukcji, która wywołała wyjątek.  
  
 W ten sposób system może automatycznie zwiększyć rozmiar stosu wątku. Każdy wątek w procesie ma rozmiar maksymalny stosu. Rozmiar stosu jest ustawiony w czasie kompilacji [/STACK (twórz stos z alokacji)](../../build/reference/stack-stack-allocations.md), lub [STACKSIZE](../../build/reference/stacksize.md) instrukcji w pliku .def dla projektu.  
  
 Po przekroczeniu tej rozmiar maksymalny stosu systemu wykonuje następujących czynności:  
  
-   Usuwa ochronę PAGE_GUARD na stronie zabezpieczenia, jak opisano wcześniej.  
  
-   Próbuje przydzielić nowej strony guard poniżej ostatnią. Jednak to nie działa, ponieważ przekroczono rozmiar maksymalny stosu.  
  
-   Zgłasza wyjątek, dzięki czemu wątek może je obsłużyć w bloku wyjątków.  
  
 Należy pamiętać, że w tym momencie stosu nie ma już strony zabezpieczenia. Przy następnym, że program rozwoju stosu aż do końca, gdzie powinien być strony ochronnej, program zapisuje poza koniec stosu i powoduje naruszenie zasad dostępu.  
  
 Wywołanie `_resetstkoflw` przywrócić stronę guard zawsze, gdy odzyskiwania jest wykonywane po wyjątku przepełnienia stosu. Ta funkcja może zostać wywołana z wewnątrz treści głównego `__except` bloku lub poza **__except** bloku. Istnieją pewne ograniczenia dotyczące kiedy należy użyć. `_resetstkoflw`nigdy nie powinna być wywoływana ze:  
  
-   Wyrażenie filtru.  
  
-   Funkcja filtru.  
  
-   Funkcja wywoływana z funkcji filtru.  
  
-   A **catch** bloku.  
  
-   A `__finally` bloku.  
  
 W tych punktach stosu nie jest jeszcze wystarczająco oddzielić.  
  
 Wyjątki przepełnienie stosu są generowane jako wyjątki strukturalne nie wyjątków języka C++, więc `_resetstkoflw` nie jest przydatne w zwykłych **catch** zablokować, ponieważ nie będzie przechwytywać wyjątku przepełnienia stosu. Jednak jeśli [_set_se_translator —](../../c-runtime-library/reference/set-se-translator.md) jest używane do implementowania translator wyjątków strukturalnych, która zgłasza wyjątków języka C++ (tak jak w drugim przykładzie), catch powoduje wyjątek przepełnienia stosu wyjątków C++, które są obsługiwane przez C++ blok.  
  
 Nie jest bezpieczne wywołania **_resetstkoflw** w bloku catch C++ osiągnięcia z wyjątek zgłoszony przez funkcję translatora wyjątków strukturalnych. W takim przypadku nie jest zwolnienie miejsca na stosie i wskaźnik stosu nie zostanie zresetowana, dopóki poza blokiem catch, mimo że destruktory mają zostanie wywołana dla obiektów które można zniszczyć przed bloku catch. Nie należy wywoływać tej funkcji do momentu miejsca stosu i wskaźnik stosu został zresetowany. W związku z tym powinna być wywoływana tylko po zakończeniu bloku catch. Małego miejsca na stosie możliwie należy użyć w bloku catch, ponieważ przepełnienie stosu występujący w bloku catch, który jest elementem próby odzyskania z poprzednich przepełnienie stosu nie jest możliwe do odzyskania i może spowodować, że program przestanie odpowiadać jako przeciążenia w bloku catch wyzwalacze blok catch wyjątku sam jest obsługiwany przez ten sam.  
  
 Istnieją sytuacje, gdy **_resetstkoflw** może zakończyć się niepowodzeniem, nawet w przypadku używania w odpowiednim miejscu, takich jak w ramach **__except** bloku. Jeśli, nawet po odwijanie stosu, nadal nie ma wystarczającej ilości miejsca na stosie pozostało do wykonania **_resetstkoflw** bez pisania na ostatniej stronie stosu, **_resetstkoflw** nie będzie mogła zresetować ostatniej strony stos strony guard i zwraca wartość 0, informujący o niepowodzeniu. W związku z tym bezpieczne użycie tej funkcji powinna zawierać sprawdzanie wartość zwracana zamiast przy założeniu, że stos jest bezpiecznie korzystać.  
  
 Obsługa wyjątków strukturalnych nie będzie przechwytywać `STATUS_STACK_OVERFLOW` wyjątku, gdy aplikacja jest skompilowana przy użyciu `/clr` (zobacz [/CLR (kompilacja języka wspólnego środowiska uruchomieniowego)](../../build/reference/clr-common-language-runtime-compilation.md)).  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`_resetstkoflw`|\<malloc.h >|  
  
 Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).  
  
 **Biblioteki:** wszystkie wersje [Biblioteka CRT — funkcje](../../c-runtime-library/crt-library-features.md).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono zalecane użycie `_resetstkoflw` funkcji.  
  
```  
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
  
## <a name="sample-output"></a>Przykładowe dane wyjściowe  
 Bez argumentów program:  
  
```  
loop #1  
```  
  
 Program nie odpowiada bez dalszego wykonywania iteracji.  
  
 Program argumentów:  
  
```  
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
 W poniższym przykładzie przedstawiono zalecane użycie `_resetstkoflw` w programie, w którym wyjątki strukturalne są konwertowane na wyjątków języka C++.  
  
### <a name="code"></a>Kod  
  
```  
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
  
## <a name="sample-output"></a>Przykładowe dane wyjściowe  
  
```  
0 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 20 21 22 23 24  
Stack overflow!  
Recovered from stack overflow and allocated 100,000 bytes using _alloca.  
```  
  
## <a name="see-also"></a>Zobacz też  
 [_alloca](../../c-runtime-library/reference/alloca.md)