---
title: _fgetchar, _fgetwchar
ms.date: 4/2/2020
api_name:
- _fgetchar
- _fgetwchar
- _o__fgetchar
- _o__fgetwchar
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
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- fgetwchar
- _fgettchar
- _fgetchar
- _fgetwchar
- fgettchar
helpviewer_keywords:
- fgetwchar function
- _fgetchar function
- fgettchar function
- _fgetwchar function
- _fgettchar function
- standard input, reading from
- fgetchar function
ms.assetid: 8bce874c-701a-41a3-b1b2-feff266fb5b9
ms.openlocfilehash: 79b932268f379309d7765d8fa03797a5b8360ccf
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2020
ms.locfileid: "82912765"
---
# <a name="_fgetchar-_fgetwchar"></a>_fgetchar, _fgetwchar

Odczytuje znak z **stdin**.

## <a name="syntax"></a>Składnia

```C
int _fgetchar( void );
wint_t _fgetwchar( void );
```

## <a name="return-value"></a>Wartość zwracana

fgetchar zwraca znak odczytywany jako **int** lub Return `EOF` , aby wskazać błąd lub koniec pliku. ** \_** fgetwchar zwraca, jako [wint_t](../../c-runtime-library/standard-types.md), znak dwubajtowy, który odpowiada znakowi odczytywania lub powracania `WEOF` , aby wskazać błąd lub koniec pliku. ** \_** Dla obu funkcji Użyj **feof** lub obiektu **odwołującego** do rozróżnienia między błędem a warunkiem końca pliku.

## <a name="remarks"></a>Uwagi

Te funkcje odczytują pojedynczy znak z **stdin**. Funkcja następnie zwiększa skojarzony wskaźnik pliku (jeśli jest zdefiniowany), aby wskazywał na następny znak. Jeśli strumień znajduje się na końcu pliku, wskaźnik końca pliku dla strumienia jest ustawiony.

**_fgetchar** jest równoważne `fgetc( stdin )`. Jest ona również równoważna z **GetChar**, ale implementowana tylko jako funkcja, a nie jako funkcja i makro. **_fgetwchar** to wersja znaku dwubajtowego **_fgetchar**.

Te funkcje nie są zgodne ze standardem ANSI.

Domyślnie globalny stan tej funkcji jest objęty zakresem aplikacji. Aby to zmienić, zobacz [stan globalny w CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura tchar.h|_UNICODE i _MBCS niezdefiniowane|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_fgettchar**|**_fgetchar**|**_fgetchar**|**_fgetwchar**|

## <a name="requirements"></a>Wymagania

|Funkcja|Wymagany nagłówek|
|--------------|---------------------|
|**_fgetchar**|\<stdio. h>|
|**_fgetwchar**|\<stdio. h> lub \<WCHAR. h>|

Konsola nie jest obsługiwana w aplikacjach platforma uniwersalna systemu Windows (platformy UWP). Standardowe uchwyty strumienia, które są skojarzone z konsolą —**stdin**, **stdout**i **stderr**— muszą zostać przekierowane przed użyciem funkcji języka C w aplikacjach platformy UWP. Aby uzyskać więcej informacji o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

```C
// crt_fgetchar.c
// This program uses _fgetchar to read the first
// 80 input characters (or until the end of input)
// and place them into a string named buffer.
//

#include <stdio.h>
#include <stdlib.h>

int main( void )
{
   char buffer[81];
   int  i, ch;

   // Read in first 80 characters and place them in "buffer":
   ch = _fgetchar();
   for( i=0; (i < 80 ) && ( feof( stdin ) == 0 ); i++ )
   {
      buffer[i] = (char)ch;
      ch = _fgetchar();
   }

   // Add null to end string
   buffer[i] = '\0';
   printf( "%s\n", buffer );
}
```

```Output

      Line one.
Line two.Line one.
Line two.
```

## <a name="see-also"></a>Zobacz też

[We/Wy strumienia](../../c-runtime-library/stream-i-o.md)<br/>
[fputc, fputwc](fputc-fputwc.md)<br/>
[getc, getwc](getc-getwc.md)<br/>
