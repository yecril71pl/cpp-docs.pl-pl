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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: b9d805483395d3050a1eb0bc78afef8cd99ca984
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81346932"
---
# <a name="_fgetchar-_fgetwchar"></a>_fgetchar, _fgetwchar

Odczytuje znak z **stdin**.

## <a name="syntax"></a>Składnia

```C
int _fgetchar( void );
wint_t _fgetwchar( void );
```

## <a name="return-value"></a>Wartość zwracana

fgetchar zwraca znak odczytany jako `EOF` **int** lub zwraca, aby wskazać błąd lub koniec pliku. ** \_** fgetwchar zwraca, jako [wint_t,](../../c-runtime-library/standard-types.md)szeroki znak, który odpowiada znakowi `WEOF` odczytanego lub zwraca, aby wskazać błąd lub koniec pliku. ** \_** W przypadku obu funkcji należy użyć **feof** lub **ferror,** aby odróżnić błąd od stanu końca pliku.

## <a name="remarks"></a>Uwagi

Te funkcje odczytywać pojedynczy znak z **stdin**. Następnie funkcja zwiększa wskaźnik skojarzonego pliku (jeśli jest zdefiniowany), aby wskazywał następny znak. Jeśli strumień znajduje się na końcu pliku, ustawiony jest wskaźnik końca pliku dla strumienia.

**_fgetchar** jest odpowiednikiem `fgetc( stdin )`. Jest to również równoważne **getchar**, ale realizowane tylko jako funkcja, a nie jako funkcja i makro. **_fgetwchar** jest szerokoznakową wersją **_fgetchar**.

Funkcje te nie są zgodne ze standardem ANSI.

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura tchar.h|_UNICODE i _MBCS niezdefiniowane|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_fgettchar**|**_fgetchar**|**_fgetchar**|**_fgetwchar**|

## <a name="requirements"></a>Wymagania

|Funkcja|Wymagany nagłówek|
|--------------|---------------------|
|**_fgetchar**|\<stdio.h>|
|**_fgetwchar**|\<stdio.h> lub \<wchar.h>|

Konsola nie jest obsługiwana w aplikacjach platformy uniwersalnej systemu Windows (UWP). Standardowe uchwyty strumienia, które są skojarzone z konsolą—**stdin,** **stdout**i **stderr**— muszą zostać przekierowane, zanim funkcje c w czasie wykonywania będą mogły z nich korzystać w aplikacjach platformy uniwersalnej systemu Windows. Aby uzyskać więcej informacji o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

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
