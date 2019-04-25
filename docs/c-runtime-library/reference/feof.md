---
title: feof
ms.date: 11/04/2016
apiname:
- feof
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
- api-ms-win-crt-stdio-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- feof
helpviewer_keywords:
- end of file, testing for
- feof function
ms.assetid: 09081eee-7c4b-4189-861f-2fad95d3ec6d
ms.openlocfilehash: 9c023290df601bfc48f9708af86d32d91cd52dc4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62334401"
---
# <a name="feof"></a>feof

Testuje pod kątem koniec pliku dla strumienia.

## <a name="syntax"></a>Składnia

```C
int feof(
   FILE *stream
);
```

### <a name="parameters"></a>Parametry

*stream*<br/>
Wskaźnik do **pliku** struktury.

## <a name="return-value"></a>Wartość zwracana

**Feof** funkcja zwraca wartość różną od zera, jeśli operacja odczytu podjął próbę odczytu poza końcem pliku; w przeciwnym razie zwraca 0. Jeśli wskaźnik strumienia **NULL**, funkcja wywołuje procedurę obsługi nieprawidłowego parametru, zgodnie z opisem w [Parameter Validation](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, **errno** ustawiono **EINVAL** i **feof** zwraca wartość 0.

Zobacz [_doserrno, errno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) Aby uzyskać więcej informacji na temat tych i innych kodów błędu,.

## <a name="remarks"></a>Uwagi

**Feof** procedura (implementowana jako funkcja i jak makra) określa czy koniec *strumienia* został przekazany. Po upływie na końcu pliku odczytać operacje zwracają wskaźnik końca pliku, dopóki strumień jest zamknięty lub do momentu [rewind](rewind.md), **fsetpos**, [fseek](fseek-fseeki64.md), lub  **clearerr —** nazywa się przed nim.

Na przykład, jeśli plik zawiera 10 bajtów i odczytu 10 bajtów z pliku **feof** zwróci 0, ponieważ mimo że wskaźnik pliku znajduje się na końcu pliku, nie podjęto próbę odczytu poza końcem. Tylko po użytkownik próbuje odczytać 11 bajtów będą **feof** zwracają wartość różną od zera.

## <a name="requirements"></a>Wymagania

|Funkcja|Wymagany nagłówek|
|--------------|---------------------|
|**feof**|\<stdio.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

```C
// crt_feof.c
// This program uses feof to indicate when
// it reaches the end of the file CRT_FEOF.TXT. It also
// checks for errors with ferror.
//

#include <stdio.h>
#include <stdlib.h>

int main( void )
{
   int  count, total = 0;
   char buffer[100];
   FILE *stream;

   fopen_s( &stream, "crt_feof.txt", "r" );
   if( stream == NULL )
      exit( 1 );

   // Cycle until end of file reached:
   while( !feof( stream ) )
   {
      // Attempt to read in 100 bytes:
      count = fread( buffer, sizeof( char ), 100, stream );
      if( ferror( stream ) )      {
         perror( "Read error" );
         break;
      }

      // Total up actual bytes read
      total += count;
   }
   printf( "Number of bytes read = %d\n", total );
   fclose( stream );
}
```

## <a name="input-crtfeoftxt"></a>Dane wejściowe: crt_feof.txt

```Input
Line one.
Line two.
```

### <a name="output"></a>Dane wyjściowe

```Output
Number of bytes read = 19
```

## <a name="see-also"></a>Zobacz także

[Obsługa błędów](../../c-runtime-library/error-handling-crt.md)<br/>
[Stream operacji We/Wy](../../c-runtime-library/stream-i-o.md)<br/>
[clearerr](clearerr.md)<br/>
[_eof](eof.md)<br/>
[ferror](ferror.md)<br/>
[perror, _wperror](perror-wperror.md)<br/>
