---
title: fprintf_s, _fprintf_s_l, fwprintf_s, _fwprintf_s_l
ms.date: 11/04/2016
apiname:
- _fprintf_s_l
- fwprintf_s
- fprintf_s
- _fwprintf_s_l
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
- _ftprintf_s
- fprintf_s
- fwprintf_s
helpviewer_keywords:
- ftprintf_s_l function
- ftprintf_s function
- _fprintf_s_l function
- _ftprintf_s function
- _ftprintf_s_l function
- fwprintf_s_l function
- fwprintf_s function
- fprintf_s_l function
- fprintf_s function
- _fwprintf_s_l function
- print formatted data to streams
ms.assetid: 16067c3c-69ce-472a-8272-9aadf1f5beed
ms.openlocfilehash: 05886dc4ce7de771749f157913a222b6b01a5c5a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50639429"
---
# <a name="fprintfs-fprintfsl-fwprintfs-fwprintfsl"></a>fprintf_s, _fprintf_s_l, fwprintf_s, _fwprintf_s_l

Drukowanie sformatowanych danych do strumienia. Są to wersje [fprintf, _fprintf_l —, fwprintf —, _fwprintf_l —](fprintf-fprintf-l-fwprintf-fwprintf-l.md) ze wzmocnieniem zabezpieczeń, zgodnie z opisem w [funkcje zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Składnia

```C
int fprintf_s(
   FILE *stream,
   const char *format [,
   argument_list ]
);
int _fprintf_s_l(
   FILE *stream,
   const char *format,
   locale_t locale [,
   argument_list ]
);
int fwprintf_s(
   FILE *stream,
   const wchar_t *format [,
   argument_list ]
);
int _fwprintf_s_l(
   FILE *stream,
   const wchar_t *format,
   locale_t locale [,
   argument_list ]
);
```

### <a name="parameters"></a>Parametry

*Stream*<br/>
Wskaźnik do **pliku** struktury.

*Format*<br/>
Ciąg kontroli formatu.

*argument_list*<br/>
Opcjonalne argumenty ciągu formatu.

*Ustawienia regionalne*<br/>
Ustawienia regionalne do użycia.

## <a name="return-value"></a>Wartość zwracana

**fprintf_s —** zwraca liczba zapisanych bajtów. **fwprintf_s —** zwraca liczbę znaków dwubajtowych, zapisane. Każda z tych funkcji zwraca wartość ujemną zamiast tego po wystąpieniu błędu danych wyjściowych.

## <a name="remarks"></a>Uwagi

**fprintf_s —** formatuje i drukuje serie znaków i wartości w danych wyjściowych *strumienia*. Każdy argument *argument_list* (jeśli istnieje) jest konwertowaya i wychodzi według specyfikacji formatu w *format*. *Format* używa argumentu [formatowanie składni Specyfikacja funkcji printf i wprintf](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md).

**fwprintf_s —** to wersja znaku dwubajtowego **fprintf_s —**; w **fwprintf_s —**, *format* jest ciągiem znaku dwubajtowego. Funkcje te zachowują się identycznie, jeżeli strumień jest otwarty w trybie ANSI. **fprintf_s —** aktualnie nie obsługuje danych wyjściowych w strumieniu UNICODE.

Wersje tych funkcji **_l** sufiksem są identyczne, z tą różnicą, że używają parametru ustawień regionalnych przekazanych zamiast bieżących ustawień regionalnych.

> [!IMPORTANT]
> Upewnij się, że *format* nie jest ciągiem zdefiniowanym przez użytkownika.

Podobnie jak niezabezpieczone wersje (patrz [fprintf, _fprintf_l —, fwprintf —, _fwprintf_l —](fprintf-fprintf-l-fwprintf-fwprintf-l.md)), te funkcje sprawdzają poprawność swoich parametrów i wywołują nieprawidłowy parametr uchwytu, zgodnie z opisem w [Parameter Validation](../../c-runtime-library/parameter-validation.md), jeśli *strumienia* lub *format* jest wskaźnikiem wartości null. Tym samym ciąg formatu jest również sprawdzany. W przypadku wszelkich nieznanych lub źle sformułowanych specyfikatorów formatowania, te funkcje tworzą wyjątek nieprawidłowego parametru. We wszystkich przypadkach, jeśli wykonanie może być kontynuowane, te funkcje zwracają wartość -1 i ustaw **errno** do **EINVAL**. Zobacz [_doserrno, errno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) Aby uzyskać więcej informacji na temat tych i innych kodów błędu,.

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|_UNICODE & _MBCS nie zdefiniowano|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_ftprintf_s —**|**fprintf_s**|**fprintf_s**|**fwprintf_s**|
|**_ftprintf_s_l —**|**_fprintf_s_l**|**_fprintf_s_l**|**_fwprintf_s_l**|

Aby uzyskać więcej informacji, zobacz [specyfikacji formatu](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md).

## <a name="requirements"></a>Wymagania

|Funkcja|Wymagany nagłówek|
|--------------|---------------------|
|**fprintf_s —**, **_fprintf_s_l —**|\<stdio.h>|
|**fwprintf_s —**, **_fwprintf_s_l —**|\<stdio.h > lub \<wchar.h >|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

```C
// crt_fprintf_s.c
// This program uses fprintf_s to format various
// data and print it to the file named FPRINTF_S.OUT. It
// then displays FPRINTF_S.OUT on the screen using the system
// function to invoke the operating-system TYPE command.

#include <stdio.h>
#include <process.h>

FILE *stream;

int main( void )
{
   int    i = 10;
   double fp = 1.5;
   char   s[] = "this is a string";
   char   c = '\n';

   fopen_s( &stream, "fprintf_s.out", "w" );
   fprintf_s( stream, "%s%c", s, c );
   fprintf_s( stream, "%d\n", i );
   fprintf_s( stream, "%f\n", fp );
   fclose( stream );
   system( "type fprintf_s.out" );
}
```

```Output
this is a string
10
1.500000
```

## <a name="see-also"></a>Zobacz także

[Stream operacji We/Wy](../../c-runtime-library/stream-i-o.md)<br/>
[_cprintf, _cprintf_l, _cwprintf, _cwprintf_l](cprintf-cprintf-l-cwprintf-cwprintf-l.md)<br/>
[fscanf, _fscanf_l, fwscanf, _fwscanf_l](fscanf-fscanf-l-fwscanf-fwscanf-l.md)<br/>
[sprintf, _sprintf_l, swprintf, _swprintf_l, \__swprintf_l](sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)<br/>
