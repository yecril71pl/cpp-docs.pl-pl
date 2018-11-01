---
title: _fgetchar, _fgetwchar
ms.date: 11/04/2016
apiname:
- _fgetchar
- _fgetwchar
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
ms.openlocfilehash: c74618fa0be5392062d13618ff73e2ef45bf7c2a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50453788"
---
# <a name="fgetchar-fgetwchar"></a>_fgetchar, _fgetwchar

Odczytuje znak z **stdin**.

## <a name="syntax"></a>Składnia

```C
int _fgetchar( void );
wint_t _fgetwchar( void );
```

## <a name="return-value"></a>Wartość zwracana

**\_fgetchar —** zwraca znak odczytywany jako **int** lub zwraca `EOF` aby wskazać błąd lub koniec pliku. **\_fgetwchar —** zwraca, jako [wint_t](../../c-runtime-library/standard-types.md), znak dwubajtowy, który odpowiada znakowi odczytu lub zwraca `WEOF` aby wskazać błąd lub koniec pliku. W przypadku obu tych funkcji, użyj **feof** lub **ferror** Aby rozróżnić między błędem a warunkiem końca pliku.

## <a name="remarks"></a>Uwagi

Te funkcje odczytują pojedynczy znak z **stdin**. Funkcja następnie zwiększa skojarzony wskaźnik pliku (Jeżeli zdefiniowane) aby wskazywała na następny znak. Jeśli strumień jest na końcu pliku, wskaźnik końca pliku dla strumienia jest ustawiony.

**_fgetchar —** jest odpowiednikiem `fgetc( stdin )`. Jest również równoważne **getchar**, ale realizowane tylko jako funkcja, a nie jako funkcja i makra. **_fgetwchar —** jest wersją znaków dwubajtowych **_fgetchar —**.

Te funkcje nie są zgodne ze standardem ANSI.

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura tchar.h|_UNICODE i _MBCS niezdefiniowane|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_fgettchar —**|**_fgetchar**|**_fgetchar**|**_fgetwchar**|

## <a name="requirements"></a>Wymagania

|Funkcja|Wymagany nagłówek|
|--------------|---------------------|
|**_fgetchar**|\<stdio.h>|
|**_fgetwchar**|\<stdio.h > lub \<wchar.h >|

Konsola nie jest obsługiwana w aplikacjach platformy uniwersalnej Windows (UWP). Standardowe uchwyty strumienia, które są powiązane z konsolą —**stdin**, **stdout**, i **stderr**— muszą zostać przekierowane zanim funkcje środowiska wykonawczego języka C można ich używać w aplikacjach platformy UWP . Aby uzyskać więcej informacji na temat zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Zobacz także

[Stream operacji We/Wy](../../c-runtime-library/stream-i-o.md)<br/>
[fputc, fputwc](fputc-fputwc.md)<br/>
[getc, getwc](getc-getwc.md)<br/>
