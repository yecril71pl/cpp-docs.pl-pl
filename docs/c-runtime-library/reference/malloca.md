---
title: _malloca — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- _malloca
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
- malloca
- _malloca
dev_langs:
- C++
helpviewer_keywords:
- memory allocation, stack
- malloca function
- _malloca function
ms.assetid: 293992df-cfca-4bc9-b313-0a733a6bb936
caps.latest.revision: 27
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 7ef8f17af191d9af288e9d59f43f3e48cd869ed1
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2018
---
# <a name="malloca"></a>_malloca

Przydziela pamięć na stosie. To jest wersja [_alloca](alloca.md) ulepszeń zabezpieczeń zgodnie z opisem w [funkcje zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Składnia

```C
void *_malloca(
   size_t size
);
```

### <a name="parameters"></a>Parametry

*Rozmiar*<br/>
Liczba bajtów do przydzielenia ze stosu.

## <a name="return-value"></a>Wartość zwracana

**_Malloca —** rutynowych zwraca **void** wskaźnik do przydzielone miejsce, który zostanie odpowiednio wyrównany do przechowywania obiekty dowolnego typu. Jeśli *rozmiar* ma wartość 0, **_malloca —** przydziela elementu o zerowej długości i zwraca prawidłowego wskaźnika do elementu.

Wyjątek przepełnienia stosu jest generowany, gdy nie można przydzielić miejsce. Wyjątek przepełnienia stosu nie jest wyjątku C++; jest wyjątków strukturalnych. Zamiast używać C++, obsługa wyjątków, należy użyć [obsługi wyjątków strukturalnych](../../cpp/structured-exception-handling-c-cpp.md) (SEH).

## <a name="remarks"></a>Uwagi

**_malloca —** przydziela *rozmiar* bajtów ze stosu program lub sterty, jeśli żądanie przekracza określony rozmiar w bajtach przez **_ALLOCA_S_THRESHOLD**. Różnica między **_malloca —** i **_alloca** jest to, że **_alloca** zawsze przydziela na stosie, niezależnie od rozmiaru. W odróżnieniu od **_alloca**, które nie wymagają ani nie zezwala na wywołania **wolnego** aby zwolnić pamięć, więc przydzielone, **_malloca —** wymaga użycia [_freea —](freea.md)zwolnienia pamięci. W trybie debugowania **_malloca —** zawsze przydziela pamięć sterty.

Ma ograniczeń do wywoływania jawnie **_malloca —** w obsłudze wyjątków (EH). Procedury EH, działające na procesorów klasy x86 działać w swojej ramce pamięci: wykonywanie zadań miejsca w pamięci nie jest oparty na bieżącej lokalizacji wskaźnik stosu funkcji otaczającej. Najczęściej występujące implementacje to obsługa (SEH) systemu Windows NT strukturę wyjątków i wyrażeń klauzuli catch C++. W związku z tym jawnie podczas wywoływania **_malloca —** w żadnym następujące scenariusze powoduje błąd programu podczas powrotu do wywoływania procedury EH:

- Wyrażenie filtru wyjątków SEH systemu Windows NT: **__except** (`_malloca ()` )

- Program obsługi wyjątku końcowego SEH systemu Windows NT: **__finally** {`_malloca ()` }

- Wyrażenie klauzuli catch C++ EH

Jednak **_malloca —** może być wywoływany bezpośrednio z procedury EH lub z dostarczonych aplikacji wywołanie zwrotne, które pobiera wywoływane przez jednego ze scenariuszy EH wymienionego powyżej.

> [!IMPORTANT]
> W systemie Windows XP Jeśli **_malloca —** jest wywoływana w bloku try/catch, należy wywołać [_resetstkoflw](resetstkoflw.md) w bloku catch.

Oprócz powyższych ograniczeń, korzystając z [/CLR (kompilacja języka wspólnego środowiska uruchomieniowego)](../../build/reference/clr-common-language-runtime-compilation.md) opcji **_malloca —** nie można używać w **__except** bloków. Aby uzyskać więcej informacji, zobacz [/CLR ograniczenia](../../build/reference/clr-restrictions.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_malloca**|\<malloc.h>|

## <a name="example"></a>Przykład

```C
// crt_malloca_simple.c
#include <stdio.h>
#include <malloc.h>

void Fn()
{
   char * buf = (char *)_malloca( 100 );
   // do something with buf
   _freea( buf );
}

int main()
{
   Fn();
}
```

## <a name="example"></a>Przykład

```C
// crt_malloca_exception.c
// This program demonstrates the use of
// _malloca and trapping any exceptions
// that may occur.

#include <windows.h>
#include <stdio.h>
#include <malloc.h>

int main()
{
    int     size;
    int     numberRead = 0;
    int     errcode = 0;
    void    *p = NULL;
    void    *pMarker = NULL;

    while (numberRead == 0)
    {
        printf_s("Enter the number of bytes to allocate "
                 "using _malloca: ");
        numberRead = scanf_s("%d", &size);
    }

    // Do not use try/catch for _malloca,
    // use __try/__except, since _malloca throws
    // Structured Exceptions, not C++ exceptions.

    __try
    {
        if (size > 0)
        {
            p =  _malloca( size );
        }
        else
        {
            printf_s("Size must be a positive number.");
        }
        _freea( p );
    }

    // Catch any exceptions that may occur.
    __except( GetExceptionCode() == STATUS_STACK_OVERFLOW )
    {
        printf_s("_malloca failed!\n");

        // If the stack overflows, use this function to restore.
        errcode = _resetstkoflw();
        if (errcode)
        {
            printf("Could not reset the stack!");
            _exit(1);
        }
    };
}
```

### <a name="input"></a>Dane wejściowe

```Input
1000
```

### <a name="sample-output"></a>Przykładowe dane wyjściowe

```Output
Enter the number of bytes to allocate using _malloca: 1000
```

## <a name="see-also"></a>Zobacz także

[Alokacja pamięci](../../c-runtime-library/memory-allocation.md)<br/>
[calloc](calloc.md)<br/>
[malloc](malloc.md)<br/>
[realloc](realloc.md)<br/>
[_resetstkoflw](resetstkoflw.md)<br/>
