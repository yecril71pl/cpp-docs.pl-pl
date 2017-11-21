---
title: _alloca | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _alloca
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
- _alloca
- alloca
dev_langs: C++
helpviewer_keywords:
- memory allocation, stack
- alloca function
- _alloca function
ms.assetid: 74488eb1-b71f-4515-88e1-cdd03b6f8225
caps.latest.revision: "23"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 6068e1b3e6765b2a409fbc33d1a97b228c82abcd
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="alloca"></a>_alloca
Przydziela pamięć na stosie. Ta funkcja jest przestarzały, ponieważ bezpieczniejsza wersja jest dostępna; zobacz [_malloca —](../../c-runtime-library/reference/malloca.md).  
  
## <a name="syntax"></a>Składnia  
  
```  
void *_alloca(   
   size_t size   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 [in]`size`  
 Liczba bajtów do przydzielenia ze stosu.  
  
## <a name="return-value"></a>Wartość zwracana  
 `_alloca` Rutynowych zwraca `void` wskaźnik do przydzielone miejsce, który zostanie odpowiednio wyrównany do przechowywania obiekty dowolnego typu. Jeśli `size` ma wartość 0, `_alloca` przydziela elementu o zerowej długości i zwraca prawidłowego wskaźnika do elementu.  
  
 Wyjątek przepełnienia stosu jest generowany, gdy nie można przydzielić miejsce. Wyjątek przepełnienia stosu nie jest wyjątku C++; jest wyjątków strukturalnych. Zamiast używać C++, obsługa wyjątków, należy użyć [obsługi wyjątków strukturalnych](../../cpp/structured-exception-handling-c-cpp.md) (SEH).  
  
## <a name="remarks"></a>Uwagi  
 `_alloca`przydziela `size` bajtów ze stosu program. Ilość miejsca przydzielonego zwalnia się automatycznie, gdy funkcji wywołującej jest kończona (nie w przypadku Alokacja jedynie przekazuje poza zakresem). W związku z tym nie przekazuj zwrócony przez wartość wskaźnika `_alloca` jako argument [wolnego](../../c-runtime-library/reference/free.md).  
  
 Ma ograniczeń do wywoływania jawnie `_alloca` w obsłudze wyjątków (EH). Procedury EH, działające na procesorów klasy x86 działać w swojej ramce pamięci: wykonywanie zadań miejsca w pamięci nie jest oparty na bieżącej lokalizacji wskaźnik stosu funkcji otaczającej. Najczęściej występujące implementacje to obsługa (SEH) systemu Windows NT strukturę wyjątków i wyrażeń klauzuli catch C++. W związku z tym jawnie podczas wywoływania `_alloca` w żadnym następujące scenariusze powoduje błąd programu podczas powrotu do wywoływania procedury EH:  
  
-   Wyrażenie filtru wyjątków SEH systemu Windows NT: `__except` (`_alloca ()` )  
  
-   Program obsługi wyjątku końcowego SEH systemu Windows NT: `__finally` {`_alloca ()` }  
  
-   Wyrażenie klauzuli catch C++ EH  
  
 Jednak `_alloca` może być wywoływany bezpośrednio z procedury EH lub z dostarczonych aplikacji wywołanie zwrotne, które pobiera wywoływane przez jednego ze scenariuszy EH wymienionego powyżej.  
  
> [!IMPORTANT]
>  W systemie Windows XP Jeśli `_alloca` jest wywoływana w bloku try/catch, należy wywołać [_resetstkoflw](../../c-runtime-library/reference/resetstkoflw.md) w bloku catch.  
  
 Oprócz powyższych ograniczeń, korzystając z[/CLR (kompilacja języka wspólnego środowiska uruchomieniowego)](../../build/reference/clr-common-language-runtime-compilation.md) opcji `_alloca` nie można używać w `__except` bloków. Aby uzyskać więcej informacji, zobacz [/CLR ograniczenia](../../build/reference/clr-restrictions.md).  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`_alloca`|\<malloc.h >|  
  
## <a name="example"></a>Przykład  
  
```  
// crt_alloca.c  
// This program demonstrates the use of  
// _alloca and trapping any exceptions  
// that may occur.  
  
#include <windows.h>  
#include <stdio.h>  
#include <malloc.h>  
  
int main()  
{  
    int     size = 1000;  
    int     errcode = 0;  
    void    *pData = NULL;  
  
    // Note: Do not use try/catch for _alloca,  
    // use __try/__except, since _alloca throws  
    // Structured Exceptions, not C++ exceptions.  
  
    __try {  
        // An unbounded _alloca can easily result in a   
        // stack overflow.  
        // Checking for a size < 1024 bytes is recommended.  
        if (size > 0 && size < 1024)  
        {  
            pData = _alloca( size );  
            printf_s( "Allocated %d bytes of stack at 0x%p",  
                      size, pData);  
        }  
        else  
        {  
            printf_s("Tried to allocate too many bytes.\n");  
        }  
    }  
  
    // If an exception occured with the _alloca function  
    __except( GetExceptionCode() == STATUS_STACK_OVERFLOW )  
    {  
        printf_s("_alloca failed!\n");  
  
        // If the stack overflows, use this function to restore.  
        errcode = _resetstkoflw();  
        if (errcode)  
        {  
            printf_s("Could not reset the stack!\n");  
            _exit(1);  
        }  
    };  
}  
```  
  
```Output  
Allocated 1000 bytes of stack at 0x0012FB50  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Alokacja pamięci](../../c-runtime-library/memory-allocation.md)   
 [calloc —](../../c-runtime-library/reference/calloc.md)   
 [— funkcja malloc](../../c-runtime-library/reference/malloc.md)   
 [realloc](../../c-runtime-library/reference/realloc.md)   
 [_resetstkoflw](../../c-runtime-library/reference/resetstkoflw.md)   
 [_malloca —](../../c-runtime-library/reference/malloca.md)