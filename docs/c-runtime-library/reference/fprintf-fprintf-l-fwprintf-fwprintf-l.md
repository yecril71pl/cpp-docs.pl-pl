---
title: fprintf —, _fprintf_l —, fwprintf —, _fwprintf_l — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- fwprintf
- fprintf
- _fprintf_l
- _fwprintf_l
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
- fprintf
- fwprintf
- _ftprintf
dev_langs:
- C++
helpviewer_keywords:
- _fwprintf_l function
- fprintf function
- fprintf_l function
- _fprintf_l function
- _ftprintf function
- fwprintf function
- ftprintf_l function
- ftprintf function
- _ftprintf_l function
- print formatted data to streams
- fwprintf_l function
ms.assetid: 34a87e1c-6e4d-4d48-a611-58314dd4dc4b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c7578a8a8c2bef7fe68e9a08ae987ac7c1609cb5
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32403885"
---
# <a name="fprintf-fprintfl-fwprintf-fwprintfl"></a>fprintf, _fprintf_l, fwprintf, _fwprintf_l

Drukowanie sformatowanych danych do strumienia. Bezpieczniejsza wersje te funkcje są dostępne; zobacz [fprintf_s —, _fprintf_s_l —, fwprintf_s —, _fwprintf_s_l —](fprintf-s-fprintf-s-l-fwprintf-s-fwprintf-s-l.md).

## <a name="syntax"></a>Składnia

```C
int fprintf(
   FILE *stream,
   const char *format [,
   argument ]...
);
int _fprintf_l(
   FILE *stream,
   const char *format,
   locale_t locale [,
   argument ]...
);
int fwprintf(
   FILE *stream,
   const wchar_t *format [,
   argument ]...
);
int _fwprintf_l(
   FILE *stream,
   const wchar_t *format,
   locale_t locale [,
   argument ]...
);
```

### <a name="parameters"></a>Parametry

*Strumień*<br/>
Wskaźnik do **pliku** struktury.

*Format*<br/>
Ciąg kontroli formatu.

*Argument*<br/>
Argumenty opcjonalne.

*Ustawienia regionalne*<br/>
Ustawienia regionalne do użycia.

## <a name="return-value"></a>Wartość zwracana

**fprintf —** zwraca liczba zapisanych bajtów. **fwprintf —** zwraca liczbę znaki dwubajtowe są zapisywane. Każda z tych funkcji zwraca wartość ujemną zamiast tego po wystąpieniu błędu w danych wyjściowych. Jeśli *strumienia* lub *format* jest **NULL**, te funkcje Wywołaj program obsługi nieprawidłowych parametrów, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Zwróć -1, jeśli może kontynuować wykonywania, funkcje i ustaw **errno** do **einval —**. Ciąg formatu nie jest zaznaczone występowanie prawidłowych znaków formatowania, ponieważ jest on przy użyciu **fprintf_s —** lub **fwprintf_s —**.

Zobacz [_doserrno —, errno, _sys_errlist — i _sys_nerr —](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) Aby uzyskać więcej informacji na temat tych i innych kodów błędów.

## <a name="remarks"></a>Uwagi

**fprintf —** formatuje i wyświetla serii znaków i wartościami danych wyjściowych *strumienia*. Każda funkcja *argument* (jeśli istnieje) jest konwertowana i dane wyjściowe według specyfikacji formatu w *format*. Aby uzyskać **fprintf —**, *format* argument ma tej samej składni i użycia, które ma w **printf**.

**fwprintf —** jest wersja znaków dwubajtowych **fprintf —**; na liście **fwprintf —**, *format* jest ciągiem znaków dwubajtowych. Te funkcje zachowują się tak samo, jakby strumień jest otwarty w trybie ANSI. **fprintf —** nie obsługuje obecnie dane wyjściowe do strumienia UNICODE.

Wersje tych funkcji z **_l** sufiks są identyczne, z wyjątkiem tego, aby używały parametr ustawień regionalnych przekazano zamiast bieżącego ustawienia regionalne wątku.

> [!IMPORTANT]
> Upewnij się, że *format* nie jest ciągiem zdefiniowane przez użytkownika.

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|_Unicode — & _MBCS nie zdefiniowany|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_ftprintf —**|**fprintf —**|**fprintf —**|**fwprintf**|
|**_ftprintf_l —**|**_fprintf_l**|**_fprintf_l**|**_fwprintf_l**|

Aby uzyskać więcej informacji, zobacz [specyfikacje formatu](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md).

## <a name="requirements"></a>Wymagania

|Funkcja|Wymagany nagłówek|
|--------------|---------------------|
|**fprintf —**, **_fprintf_l —**|\<stdio.h>|
|**fwprintf —**, **_fwprintf_l —**|\<stdio.h > lub \<wchar.h >|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

```C
// crt_fprintf.c
/* This program uses fprintf to format various
* data and print it to the file named FPRINTF.OUT. It
* then displays FPRINTF.OUT on the screen using the system
* function to invoke the operating-system TYPE command.
*/

#include <stdio.h>
#include <process.h>

FILE *stream;

int main( void )
{
   int    i = 10;
   double fp = 1.5;
   char   s[] = "this is a string";
   char   c = '\n';

   fopen_s( &stream, "fprintf.out", "w" );
   fprintf( stream, "%s%c", s, c );
   fprintf( stream, "%d\n", i );
   fprintf( stream, "%f\n", fp );
   fclose( stream );
   system( "type fprintf.out" );
}
```

```Output
this is a string
10
1.500000
```

## <a name="see-also"></a>Zobacz także

[We/Wy strumienia](../../c-runtime-library/stream-i-o.md)<br/>
[_cprintf, _cprintf_l, _cwprintf, _cwprintf_l](cprintf-cprintf-l-cwprintf-cwprintf-l.md)<br/>
[fscanf, _fscanf_l, fwscanf, _fwscanf_l](fscanf-fscanf-l-fwscanf-fwscanf-l.md)<br/>
[sprintf, _sprintf_l, swprintf, _swprintf_l, \__swprintf_l](sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)<br/>
[Składnia specyfikacji formatu: funkcje printf i wprintf](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)<br/>
