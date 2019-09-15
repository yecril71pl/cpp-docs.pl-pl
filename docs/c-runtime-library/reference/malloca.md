---
title: _malloca
ms.date: 11/04/2016
api_name:
- _malloca
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
- malloca
- _malloca
helpviewer_keywords:
- memory allocation, stack
- malloca function
- _malloca function
ms.assetid: 293992df-cfca-4bc9-b313-0a733a6bb936
ms.openlocfilehash: 0b12b4adde710f2fc46b3a3790519006fabbb1fc
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70952772"
---
# <a name="_malloca"></a>_malloca

Przydziela pamięć na stosie. Jest to wersja [_alloca](alloca.md) z ulepszeniami zabezpieczeń, zgodnie z opisem w temacie [funkcje zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Składnia

```C
void *_malloca(
   size_t size
);
```

### <a name="parameters"></a>Parametry

*zmienia*<br/>
Bajty do przydzielenia ze stosu.

## <a name="return-value"></a>Wartość zwracana

Procedura **_malloca** zwraca wskaźnik **void** do przydzieloną miejsce, co gwarantuje, że jest odpowiednio wyrównany do przechowywania dowolnego typu obiektu. Jeśli *size* ma wartość 0, **_malloca** przydziela element o zerowej długości i zwraca prawidłowy wskaźnik do tego elementu.

Jeśli *rozmiar* jest większy niż **_ALLOCA_S_THRESHOLD**, następnie **_malloca** próbuje przydzielić na stercie i zwraca wskaźnik o wartości null, jeśli nie można przydzielić miejsca. Jeśli wartość *size* jest mniejsza lub równa **_ALLOCA_S_THRESHOLD**, wówczas **_malloca** próbuje przydzielić na stosie, a wyjątek przepełnienia stosu jest generowany, jeśli nie można przydzielić miejsca. Wyjątek przepełnienia stosu nie C++ jest wyjątkiem; jest to wyjątek strukturalny. Zamiast korzystać C++ z obsługi wyjątków, należy użyć [obsługi wyjątków strukturalnych](../../cpp/structured-exception-handling-c-cpp.md) (SEH) w celu przechwycenia tego wyjątku.

## <a name="remarks"></a>Uwagi

**_malloca** przydziela bajty *rozmiaru* ze stosu programu lub sterty, jeśli żądanie przekroczy określony rozmiar w bajtach przyznanych przez **_ALLOCA_S_THRESHOLD**. Różnica między **_malloca** i **_alloca** polega na tym, że **_alloca** zawsze przydziela na stosie, bez względu na rozmiar. W przeciwieństwie do **_alloca**, która nie wymaga ani nie zezwala na wywołanie **bezpłatne do zwolnienia** pamięci do przydzielenia, **_malloca** wymaga użycia [_freea](freea.md) do zwolnienia pamięci. W trybie debugowania **_malloca** zawsze przydziela pamięć ze sterty.

Istnieją ograniczenia dotyczące jawnego wywoływania **_malloca** w obsłudze wyjątków (EH). Procedury EH uruchamiane na procesorach klasy x86 działają w ich własnych ramkach pamięci: Wykonują swoje zadania w przestrzeni pamięci, które nie są oparte na bieżącej lokalizacji wskaźnika stosu otaczającej funkcji. Najpopularniejsze implementacje obejmują obsługę wyjątków strukturalnych systemu Windows NT (SEH) C++ i wyrażenia klauzuli catch. W związku z tym jawne wywołanie **_malloca** w jednym z następujących scenariuszy powoduje niepowodzenie programu podczas powrotu do procedury wywołującej EH:

- Wyrażenie filtru wyjątków SEH systemu Windows NT : __except`_malloca ()` ()

- Końcowy program obsługi wyjątków SEH systemu Windows NT:`_malloca ()` __finally {}

- C++Wyrażenie klauzuli catch w instrukcji EH

Jednakże **_malloca** można wywołać bezpośrednio z poziomu procedury EH lub z wywołania zwrotnego dostarczonego przez aplikację, które jest wywoływane przez jedno z wcześniej wymienionych scenariuszy EH.

> [!IMPORTANT]
> W systemie Windows XP, jeśli **_malloca** jest wywoływana wewnątrz bloku try/catch, należy wywołać [_resetstkoflw](resetstkoflw.md) w bloku catch.

Oprócz powyższych ograniczeń, przy użyciu opcji [/CLR (Kompilacja środowiska uruchomieniowego języka wspólnego)](../../build/reference/clr-common-language-runtime-compilation.md) **_malloca** nie można używać w blokach **__except** . Aby uzyskać więcej informacji, zobacz temat [ograniczenia/CLR](../../build/reference/clr-restrictions.md).

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
