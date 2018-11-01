---
title: _vcprintf, _vcprintf_l, _vcwprintf, _vcwprintf_l
ms.date: 11/04/2016
apiname:
- _vcwprintf
- _vcprintf_l
- _vcwprintf_l
- _vcprintf
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
- _vcwprintf_l
- _vtcprintf
- vcwprintf
- _vcwprintf
- vcprintf_l
- _vcprintf_l
- _vcprintf
- vcprintf
- vcwprintf_l
helpviewer_keywords:
- vcwprintf function
- _vcwprintf_l function
- _vcprintf function
- _vcprintf_l function
- vtcprintf_l function
- vcprintf function
- vcprintf_l function
- _vtcprintf function
- _vcwprintf function
- _vtcprintf_l function
- vcwprintf_l function
- vtcprintf function
- formatted text [C++]
ms.assetid: 4ef8d237-6200-4b66-8731-8c57e5624bb1
ms.openlocfilehash: e78d2f0b873042bda4fc79df100374b52751aebc
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50624760"
---
# <a name="vcprintf-vcprintfl-vcwprintf-vcwprintfl"></a>_vcprintf, _vcprintf_l, _vcwprintf, _vcwprintf_l

Pisze sformatowane dane wyjściowe do konsoli, za pomocą wskaźnika do listy argumentów. Dostępne są bardziej bezpieczne wersje tych funkcji, zobacz [_vcprintf_s —, _vcprintf_s_l —, _vcwprintf_s —, _vcwprintf_s_l —](vcprintf-s-vcprintf-s-l-vcwprintf-s-vcwprintf-s-l.md).

> [!IMPORTANT]
> Tego API nie można używać w aplikacjach korzystających ze środowiska wykonawczego Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT nieobsługiwane w aplikacjach platformy uniwersalnej Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Składnia

```C
int _vcprintf(
   const char* format,
   va_list argptr
);
int _vcprintf_l(
   const char* format,
   locale_t locale,
   va_list argptr
);
int _vcwprintf(
   const wchar_t* format,
   va_list argptr
);
int _vcwprintf_l(
   const wchar_t* format,
   locale_t locale,
   va_list argptr
);
```

### <a name="parameters"></a>Parametry

*Format*<br/>
Specyfikacja formatu.

*argptr*<br/>
Wskaźnik do listy argumentów.

*Ustawienia regionalne*<br/>
Ustawienia regionalne do użycia.

Aby uzyskać więcej informacji, zobacz [specyfikacji formatu](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md).

## <a name="return-value"></a>Wartość zwracana

Liczba znaków zapisanych, lub wartość ujemną, jeśli wystąpi błąd danych wyjściowych. Jeśli *format* jest pustym wskaźnikiem, wywoływany nieprawidłowy parametr uchwytu, zgodnie z opisem w [Parameter Validation](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, **errno** ustawiono **EINVAL** i zwracana jest wartość -1.

## <a name="remarks"></a>Uwagi

Każda z tych funkcji pobiera wskaźnik do listy argumentów, a następnie formatuje i zapisuje dostarczone dane do konsoli. **_vcwprintf —** jest wersją znaków dwubajtowych **_vcprintf —**. Pobiera ciąg znaków dwubajtowych jako argument.

Wersje tych funkcji **_l** sufiksem są identyczne, z tą różnicą, że używają parametru ustawień regionalnych przekazanych zamiast bieżących ustawień regionalnych.

> [!IMPORTANT]
> Upewnij się, że *format* nie jest ciągiem zdefiniowanym przez użytkownika. Aby uzyskać więcej informacji, zobacz [unikanie przepełnień bufora](/windows/desktop/SecBP/avoiding-buffer-overruns).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|_UNICODE & _MBCS nie zdefiniowano|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_vtcprintf —**|**_vcprintf**|**_vcprintf**|**_vcwprintf**|
|**_vtcprintf_l —**|**_vcprintf_l**|**_vcprintf_l**|**_vcwprintf_l**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|Opcjonalne nagłówki|
|-------------|---------------------|----------------------|
|**_vcprintf —**, **_vcprintf_l —**|\<conio.h > i \<stdarg.h >|\<varargs.h>*|
|**_vcwprintf —**, **_vcwprintf_l —**|\<conio.h > lub \<wchar.h >, a \<stdarg.h >|\<varargs.h>*|

\* Wymagane dla zgodności systemu UNIX V.

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

```cpp
// crt_vcprintf.cpp
// compile with: /c
#include <conio.h>
#include <stdarg.h>

// An error formatting function used to print to the console.
int eprintf(const char* format, ...)
{
    va_list args;
    va_start(args, format);
    int result = _vcprintf(format, args);
    va_end(args);
    return result;
}

int main()
{
    eprintf("(%d:%d): Error %s%d : %s\n", 10, 23, "C", 2111,
           "<some error text>");
    eprintf("    (Related to symbol '%s' defined on line %d).\n",
            "<symbol>", 5 );
}
```

```Output
(10,23): Error C2111 : <some error text>
    (Related to symbol '<symbol>' defined on line 5).
```

## <a name="see-also"></a>Zobacz także

[Stream operacji We/Wy](../../c-runtime-library/stream-i-o.md)<br/>
[vprintf, funkcje](../../c-runtime-library/vprintf-functions.md)<br/>
[_cprintf, _cprintf_l, _cwprintf, _cwprintf_l](cprintf-cprintf-l-cwprintf-cwprintf-l.md)<br/>
[fprintf, _fprintf_l, fwprintf, _fwprintf_l](fprintf-fprintf-l-fwprintf-fwprintf-l.md)<br/>
[printf, _printf_l, wprintf, _wprintf_l](printf-printf-l-wprintf-wprintf-l.md)<br/>
[sprintf, _sprintf_l, swprintf, _swprintf_l, \__swprintf_l](sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)<br/>
[va_arg, va_copy, va_end, va_start](va-arg-va-copy-va-end-va-start.md)<br/>
