---
title: _fgetc_nolock, _fgetwc_nolock
ms.date: 4/2/2020
api_name:
- _fgetc_nolock
- _fgetwc_nolock
- _o__fgetc_nolock
- _o__fgetwc_nolock
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
- api-ms-win-crt-stdio-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _fgetwc_nolock
- fgettc_nolock
- fgetwc_nolock
- _fgetc_nolock
- _fgettc_nolock
- fgetc_nolock
helpviewer_keywords:
- fgetc_nolock function
- fgetwc_nolock function
- _fgetwc_nolock function
- characters, reading
- _fgetc_nolock function
- streams, reading characters from
- fgettc_nolock function
- reading characters from streams
- _fgettc_nolock function
ms.assetid: fb8e7c5b-4503-493a-879e-6a1db75aa114
ms.openlocfilehash: 8d0fea4a663828eb0997bc5ccc43b800d0d1e513
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81346946"
---
# <a name="_fgetc_nolock-_fgetwc_nolock"></a>_fgetc_nolock, _fgetwc_nolock

Odczytuje znak ze strumienia bez blokowania wątku.

## <a name="syntax"></a>Składnia

```C
int _fgetc_nolock(
   FILE *stream
);
wint_t _fgetwc_nolock(
   FILE *stream
);
```

### <a name="parameters"></a>Parametry

*Strumienia*<br/>
Wskaźnik do struktury **PLIK.**

## <a name="return-value"></a>Wartość zwracana

Zobacz[fgetc, fgetwc](fgetc-fgetwc.md).

## <a name="remarks"></a>Uwagi

**_fgetc_nolock** i **_fgetwc_nolock** są identyczne odpowiednio z **fgetc** i **fgetwc,** z tą różnicą, że nie są chronione przed zakłóceniami przez inne wątki. Mogą one być szybsze, ponieważ nie ponoszą obciążenie blokowania innych wątków. Użyj tych funkcji tylko w kontekstach bezpiecznych dla wątków, takich jak aplikacje jednowątkowe lub gdzie zakres wywołujący obsługuje już izolację wątku.

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura tchar.h|_UNICODE i _MBCS niezdefiniowane|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_fgettc_nolock**|**_fgetc_nolock**|**_fgetc_nolock**|**_fgetwc_nolock**|

## <a name="requirements"></a>Wymagania

|Funkcja|Wymagany nagłówek|
|--------------|---------------------|
|**_fgetc_nolock**|\<stdio.h>|
|**_fgetwc_nolock**|\<stdio.h> lub \<wchar.h>|

Aby uzyskać więcej informacji o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

```C
// crt_fgetc_nolock.c
// This program uses getc to read the first
// 80 input characters (or until the end of input)
// and place them into a string named buffer.

#include <stdio.h>
#include <stdlib.h>

int main( void )
{
   FILE *stream;
   char buffer[81];
   int  i, ch;

   // Open file to read line from:
   if( fopen_s( &stream, "crt_fgetc_nolock.txt", "r" ) != 0 )
      exit( 0 );

   // Read in first 80 characters and place them in "buffer":
   ch = fgetc( stream );
   for( i=0; (i < 80 ) && ( feof( stream ) == 0 ); i++ )
   {
      buffer[i] = (char)ch;
      ch = _fgetc_nolock( stream );
   }

   // Add null to end string
   buffer[i] = '\0';
   printf( "%s\n", buffer );
   fclose( stream );
}
```

## <a name="input-crt_fgetc_nolocktxt"></a>Dane wejściowe: crt_fgetc_nolock.txt

```Input
Line one.
Line two.
```

### <a name="output"></a>Dane wyjściowe

```Output
Line one.
Line two.
```

## <a name="see-also"></a>Zobacz też

[We/Wy strumienia](../../c-runtime-library/stream-i-o.md)<br/>
[fputc, fputwc](fputc-fputwc.md)<br/>
[getc, getwc](getc-getwc.md)<br/>
