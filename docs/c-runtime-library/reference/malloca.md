---
title: _malloca
ms.date: 11/04/2016
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
helpviewer_keywords:
- memory allocation, stack
- malloca function
- _malloca function
ms.assetid: 293992df-cfca-4bc9-b313-0a733a6bb936
ms.openlocfilehash: 22a63002c900d69e8a7706a54acedf0b4b4f6376
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62156879"
---
# <a name="malloca"></a>_malloca

Przydziela pamięć na stosie. To jest wersja [_alloca](alloca.md) ze wzmocnieniem zabezpieczeń, zgodnie z opisem w [funkcje zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Składnia

```C
void *_malloca(
   size_t size
);
```

### <a name="parameters"></a>Parametry

*Rozmiar*<br/>
Bajty do przydzielenia ze stosu.

## <a name="return-value"></a>Wartość zwracana

**_Malloca** rutynowe zwroty **void** wskaźnik do przydzielonego miejsca jest gwarantowane do bycia odpowiednio wyrównaną do przechowywania dowolnego typu obiektu. Jeśli *rozmiar* ma wartość 0, **_malloca** przydziela element o zerowej długości i zwraca prawidłowy wskaźnik do tego elementu.

Jeśli *rozmiar* jest większa niż **_ALLOCA_S_THRESHOLD**, następnie **_malloca** próbuje przydzielić na stosie i zwraca wskaźnikiem typu null, jeśli nie można przydzielić miejsce. Jeśli *rozmiar* jest mniejsza niż lub równa **_ALLOCA_S_THRESHOLD**, następnie **_malloca** próbuje przydzielić na stosie, a wyjątek przepełnienia stosu jest generowany, gdy nie miejsce przydzielone. Wyjątek przepełnienia stosu nie jest wyjątek języka C++; jest wyjątków strukturalnych. Zamiast korzystać z obsługi wyjątków C++, należy użyć [obsługi wyjątków strukturalnych](../../cpp/structured-exception-handling-c-cpp.md) (SEH), aby wykryć tego wyjątku.

## <a name="remarks"></a>Uwagi

**_malloca** przydziela *rozmiar* bajtów stosu program lub sterty, jeśli żądanie przekracza określony rozmiar w bajtach, określone przez **_ALLOCA_S_THRESHOLD**. Różnica między **_malloca** i **_alloca** jest fakt, że **_alloca** zawsze przydziela na stosie, bez względu na rozmiar. W odróżnieniu od **_alloca**, które nie wymagają ani nie zezwala na wywołania **bezpłatne** aby zwolnić pamięć, więc przydzielone, **_malloca** wymaga użycia [_freea —](freea.md)aby zwolnić pamięć. W trybie debugowania **_malloca** zawsze przydziela pamięć ze stosu.

Ma ograniczeń do jawnego wywołania **_malloca** w obsłudze wyjątków (EH). Procedury EH, działających na procesorach x86 klasy działają w ich własnych ramki pamięci: Wykonują swoje zadania w obszarze pamięci, która nie jest oparty na bieżącej lokalizacji wskaźnika stosu funkcji otaczającej. Najbardziej najczęściej występujące implementacje to obsługi (SEH) wyjątków systemu Windows NT, ze strukturą i wyrażeń klauzuli catch języka C++. W związku z tym, jawne wywołanie **_malloca** we wszystkich następujących scenariuszy powoduje awarię programu podczas powrotu do wywoływania procedury EH:

- Wyrażenie filtru wyjątków SEH Windows NT: **__except** (`_malloca ()` )

- Program obsługi wyjątków końcowego strukturalnej obsługi wyjątków systemu Windows NT: **__finally** {`_malloca ()` }

- Wyrażenie klauzuli catch EH w języku C++

Jednak **_malloca** mogą być wywoływane bezpośrednio z w ramach procedury EH lub z dostarczonych aplikacji wywołanie zwrotne, które pobiera wywoływane przez jednego ze scenariuszy EH wymienionych powyżej.

> [!IMPORTANT]
> Windows XP Jeśli **_malloca** nazywa się wewnątrz bloku try/catch, należy wywołać [_resetstkoflw](resetstkoflw.md) w bloku catch.

Oprócz powyższych ograniczeń, korzystając z [/CLR (kompilacja języka wspólnego środowiska uruchomieniowego)](../../build/reference/clr-common-language-runtime-compilation.md) opcji **_malloca** nie można używać w **__except** bloków. Aby uzyskać więcej informacji, zobacz [/CLR ograniczenia](../../build/reference/clr-restrictions.md).

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
