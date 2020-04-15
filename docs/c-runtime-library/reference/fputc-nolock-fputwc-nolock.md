---
title: _fputc_nolock, _fputwc_nolock
ms.date: 4/2/2020
api_name:
- _fputwc_nolock
- _fputc_nolock
- _o__fputc_nolock
- _o__fputwc_nolock
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
- _fputc_nolock
- fputwc_nolock
- fputc_nolock
- fputtc_nolock
- _fputwc_nolock
- _fputtc_nolock
helpviewer_keywords:
- streams, writing characters to
- fputwc_nolock function
- fputtc_nolock function
- _fputc_nolock function
- fputc_nolock function
- _fputtc_nolock function
- _fputwc_nolock function
ms.assetid: c63eb3ad-58fa-46d0-9249-9c25f815eab9
ms.openlocfilehash: f1ad79a1517783a48de887ccf2294d7a8018f70e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81346254"
---
# <a name="_fputc_nolock-_fputwc_nolock"></a>_fputc_nolock, _fputwc_nolock

Zapisuje znak do strumienia bez blokowania wątku.

## <a name="syntax"></a>Składnia

```C
int _fputc_nolock(
   int c,
   FILE *stream
);
wint_t _fputwc_nolock(
   wchar_t c,
   FILE *stream
);
```

### <a name="parameters"></a>Parametry

*C*<br/>
Znak do zapisania.

*Strumienia*<br/>
Wskaźnik do struktury **PLIK.**

## <a name="return-value"></a>Wartość zwracana

Każda z tych funkcji zwraca zapisany znak. Aby uzyskać informacje o błędzie, zobacz [fputc, fputwc](fputc-fputwc.md).

## <a name="remarks"></a>Uwagi

**_fputc_nolock** i **_fputwc_nolock** są identyczne odpowiednio z **fputc** i **fputwc,** z tą różnicą, że nie są chronione przed zakłóceniami przez inne wątki. Mogą one być szybsze, ponieważ nie ponoszą obciążenie blokowania innych wątków. Użyj tych funkcji tylko w kontekstach bezpiecznych dla wątków, takich jak aplikacje jednowątkowe lub gdzie zakres wywołujący obsługuje już izolację wątku.

Te dwie funkcje zachowują się identycznie, jeśli strumień jest otwarty w trybie ANSI. **_fputc_nolock** obecnie nie obsługuje danych wyjściowych do strumienia UNICODE.

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura tchar.h|_UNICODE i _MBCS niezdefiniowane|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_fputtc_nolock**|**_fputc_nolock**|**_fputc_nolock**|**_fputwc_nolock**|

## <a name="requirements"></a>Wymagania

|Funkcja|Wymagany nagłówek|
|--------------|---------------------|
|**_fputc_nolock**|\<stdio.h>|
|**_fputwc_nolock**|\<stdio.h> lub \<wchar.h>|

Konsola nie jest obsługiwana w aplikacjach platformy uniwersalnej systemu Windows (UWP). Standardowe uchwyty strumienia, które są skojarzone z konsolą—**stdin,** **stdout**i **stderr**— muszą zostać przekierowane, zanim funkcje c w czasie wykonywania będą mogły z nich korzystać w aplikacjach platformy uniwersalnej systemu Windows. Aby uzyskać więcej informacji o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

```C
// crt_fputc_nolock.c
// This program uses _fputc_nolock
// to send a character array to stdout.

#include <stdio.h>

int main( void )
{
   char strptr1[] = "This is a test of _fputc_nolock!!\n";
   char *p;

   // Print line to stream using fputc.
   p = strptr1;
   while( (*p != '\0') && _fputc_nolock( *(p++), stdout ) != EOF ) ;

}
```

```Output
This is a test of _fputc_nolock!!
```

## <a name="see-also"></a>Zobacz też

[We/Wy strumienia](../../c-runtime-library/stream-i-o.md)<br/>
[fgetc, fgetwc](fgetc-fgetwc.md)<br/>
[putc, putwc](putc-putwc.md)<br/>
