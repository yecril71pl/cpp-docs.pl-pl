---
title: _alloca
ms.date: 11/04/2016
apiname:
- _alloca
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
helpviewer_keywords:
- memory allocation, stack
- alloca function
- _alloca function
ms.assetid: 74488eb1-b71f-4515-88e1-cdd03b6f8225
ms.openlocfilehash: 7c083e791301d3224709a5fc6c711ceaa6397d38
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62341603"
---
# <a name="alloca"></a>_alloca

Przydziela pamięć na stosie. Ta funkcja jest przestarzały, ponieważ bardziej bezpieczna wersja jest dostępna; zobacz [_malloca](malloca.md).

## <a name="syntax"></a>Składnia

```C
void *_alloca(
   size_t size
);
```

### <a name="parameters"></a>Parametry

*Rozmiar*<br/>
Bajty do przydzielenia ze stosu.

## <a name="return-value"></a>Wartość zwracana

**_Alloca** rutynowe zwroty **void** wskaźnik do przydzielonego miejsca jest gwarantowane do bycia odpowiednio wyrównaną do przechowywania dowolnego typu obiektu. Jeśli *rozmiar* ma wartość 0, **_alloca** przydziela element o zerowej długości i zwraca prawidłowy wskaźnik do tego elementu.

Wyjątek przepełnienia stosu jest generowany, gdy nie można przydzielić miejsce. Wyjątek przepełnienia stosu nie jest wyjątek języka C++; jest wyjątków strukturalnych. Zamiast korzystać z obsługi wyjątków C++, należy użyć [obsługi wyjątków strukturalnych](../../cpp/structured-exception-handling-c-cpp.md) (SEH).

## <a name="remarks"></a>Uwagi

**_alloca** przydziela *rozmiar* bajtów ze stosu program. Ilość miejsca przydzielonego automatycznie jest zwalniana, gdy funkcja wywołująca istnieje (nie w momencie alokacji jedynie przekazuje poza zakresem). W związku z tym, nie przekazuj wartości wskaźnika zwróconej przez **_alloca** jako argument do [bezpłatne](free.md).

Ma ograniczeń do jawnego wywołania **_alloca** w obsłudze wyjątków (EH). Procedury EH, działających na procesorach x86 klasy działają w ich własnych ramki pamięci: Wykonują swoje zadania w obszarze pamięci, która nie jest oparty na bieżącej lokalizacji wskaźnika stosu funkcji otaczającej. Najbardziej najczęściej występujące implementacje to obsługi (SEH) wyjątków systemu Windows NT, ze strukturą i wyrażeń klauzuli catch języka C++. W związku z tym, jawne wywołanie **_alloca** we wszystkich następujących scenariuszy powoduje awarię programu podczas powrotu do wywoływania procedury EH:

- Wyrażenie filtru wyjątków SEH Windows NT: `__except ( _alloca() )`

- Program obsługi wyjątków końcowego Windows NT strukturalnej obsługi wyjątków: `__finally { _alloca() }`

- Wyrażenie klauzuli catch EH w języku C++

Jednak **_alloca** mogą być wywoływane bezpośrednio z w ramach procedury EH lub z dostarczonych aplikacji wywołanie zwrotne, które pobiera wywoływane przez jednego ze scenariuszy EH wymienionych powyżej.

> [!IMPORTANT]
> Windows XP Jeśli **_alloca** nazywa się wewnątrz bloku try/catch, należy wywołać [_resetstkoflw](resetstkoflw.md) w bloku catch.

Oprócz powyższych ograniczeń, korzystając z[/CLR (kompilacja języka wspólnego środowiska uruchomieniowego)](../../build/reference/clr-common-language-runtime-compilation.md) opcji **_alloca** nie można używać w **__except** bloków. Aby uzyskać więcej informacji, zobacz [/CLR ograniczenia](../../build/reference/clr-restrictions.md).

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

## <a name="see-also"></a>Zobacz także

[Alokacja pamięci](../../c-runtime-library/memory-allocation.md)<br/>
[calloc](calloc.md)<br/>
[malloc](malloc.md)<br/>
[realloc](realloc.md)<br/>
[_resetstkoflw](resetstkoflw.md)<br/>
[_malloca](malloca.md)<br/>
