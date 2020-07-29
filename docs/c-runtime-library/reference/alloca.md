---
title: _alloca
ms.date: 11/04/2016
api_name:
- _alloca
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _alloca
- alloca
helpviewer_keywords:
- memory allocation, stack
- alloca function
- _alloca function
ms.assetid: 74488eb1-b71f-4515-88e1-cdd03b6f8225
ms.openlocfilehash: 159f474927b4aaf364ad6972450edbe513a3c0b0
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87218744"
---
# <a name="_alloca"></a>_alloca

Przydziela pamięć na stosie. Ta funkcja jest przestarzała, ponieważ jest dostępna bezpieczniejsza wersja; Zobacz [_malloca](malloca.md).

## <a name="syntax"></a>Składnia

```C
void *_alloca(
   size_t size
);
```

### <a name="parameters"></a>Parametry

*zmienia*<br/>
Bajty do przydzielenia ze stosu.

## <a name="return-value"></a>Wartość zwracana

Procedura **_alloca** zwraca **`void`** wskaźnik do przydzieloną miejsce, który jest gwarantowany odpowiednio wyrównany do przechowywania dowolnego typu obiektu. Jeśli *size* ma wartość 0, **_alloca** przydziela element o zerowej długości i zwraca prawidłowy wskaźnik do tego elementu.

Wyjątek przepełnienia stosu jest generowany, jeśli nie można przydzielyć miejsca. Wyjątek przepełnienia stosu nie jest wyjątkiem C++; jest to wyjątek strukturalny. Zamiast korzystać z obsługi wyjątków C++, należy użyć [obsługi wyjątków strukturalnych](../../cpp/structured-exception-handling-c-cpp.md) (SEH).

## <a name="remarks"></a>Uwagi

**_alloca** przydziela bajtów *rozmiaru* ze stosu programu. Przydzielone miejsce jest automatycznie zwalniane, gdy wywoływana funkcja zostanie zakończona (nie gdy przydział jedynie przejdzie poza zakres). W związku z tym nie przekazuj wartości wskaźnika zwracanej przez **_alloca** jako argument do [zwolnienia](free.md).

Istnieją ograniczenia dotyczące jawnego wywoływania **_alloca** w programie obsługi wyjątków (EH). Procedury EH uruchamiane na procesorach klasy x86 działają w ich własnej ramce pamięci: wykonują swoje zadania w przestrzeni pamięci, które nie są oparte na bieżącej lokalizacji wskaźnika stosu otaczającej funkcji. Najpopularniejsze implementacje obejmują wyrażenia z obsługą wyjątków strukturalnych systemu Windows NT (SEH) i wyrażenie klauzuli catch języka C++. W związku z tym jawne wywołanie **_alloca** w jednym z następujących scenariuszy powoduje błąd programu podczas powrotu do procedury wywołującej EH:

- Wyrażenie filtru wyjątków SEH systemu Windows NT:`__except ( _alloca() )`

- Końcowy program obsługi wyjątków SEH systemu Windows NT:`__finally { _alloca() }`

- Wyrażenie klauzuli catch języka C++ EH

Jednakże **_alloca** można wywołać bezpośrednio z poziomu procedury EH lub z wywołania zwrotnego dostarczonego przez aplikację, które jest wywoływane przez jedno z wcześniej wymienionych scenariuszy EH.

> [!IMPORTANT]
> W systemie Windows XP, jeśli **_alloca** jest wywoływana wewnątrz bloku try/catch, należy wywołać [_resetstkoflw](resetstkoflw.md) w bloku catch.

Oprócz powyższych ograniczeń, przy użyciu opcji[/CLR (Kompilacja środowiska uruchomieniowego języka wspólnego)](../../build/reference/clr-common-language-runtime-compilation.md) **_alloca** nie można używać w **`__except`** blokach. Aby uzyskać więcej informacji, zobacz temat [ograniczenia/CLR](../../build/reference/clr-restrictions.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_alloca**|\<malloc.h>|

## <a name="example"></a>Przykład

```C
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

    // If an exception occurred with the _alloca function
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

## <a name="see-also"></a>Zobacz także

[Alokacja pamięci](../../c-runtime-library/memory-allocation.md)<br/>
[calloc](calloc.md)<br/>
[malloc](malloc.md)<br/>
[realloc](realloc.md)<br/>
[_resetstkoflw](resetstkoflw.md)<br/>
[_malloca](malloca.md)<br/>
