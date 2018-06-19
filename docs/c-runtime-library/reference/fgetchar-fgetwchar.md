---
title: _fgetchar —, _fgetwchar — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- fgetwchar function
- _fgetchar function
- fgettchar function
- _fgetwchar function
- _fgettchar function
- standard input, reading from
- fgetchar function
ms.assetid: 8bce874c-701a-41a3-b1b2-feff266fb5b9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 87b5b42c72f4ea2756358208f85d9c01f7863dba
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32400567"
---
# <a name="fgetchar-fgetwchar"></a>_fgetchar, _fgetwchar

Odczytuje znak z **stdin**.

## <a name="syntax"></a>Składnia

```C
int _fgetchar( void );
wint_t _fgetwchar( void );
```

## <a name="return-value"></a>Wartość zwracana

**_fgetchar —** zwraca znak odczytany jako **int** lub zwróć **EOF** wskazująca błąd lub koniec pliku. **_ *** fgetwchar —** zwraca, jako [wint_t —](../../c-runtime-library/standard-types.md), znaków dwubajtowych, który odpowiada znaków do odczytu lub zwraca **weof —** wskazująca błąd lub koniec pliku. Dla obu tych funkcji, należy użyć **feof —** lub **ferror —** odróżnić błąd warunku końcowego pliku.

## <a name="remarks"></a>Uwagi

Te funkcje odczytu pojedynczy znak z **stdin**. Funkcja zwiększa następnie kursor skojarzony plik (jeśli jest zdefiniowana), aby wskazywały na następny znak. Jeśli strumień jest na końcu pliku, jest ustawiony dla tego strumienia wskaźnika końca pliku.

**_fgetchar —** jest odpowiednikiem `fgetc( stdin )`. Również jest odpowiednikiem **getchar**, ale zaimplementowany tylko jako funkcję, a nie jako funkcję i makra. **_fgetwchar —** jest wersja znaków dwubajtowych **_fgetchar —**.

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

Konsoli nie jest obsługiwane w aplikacjach systemu Windows platformy Uniwersalnej. Uchwyty Standardowy strumień, które są skojarzone z konsoli programu —**stdin**, **stdout**, i **stderr**— muszą być przekierowywane przed funkcje wykonawcze języka C można używać ich w aplikacji platformy uniwersalnej systemu Windows . Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

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

[We/Wy strumienia](../../c-runtime-library/stream-i-o.md)<br/>
[fputc, fputwc](fputc-fputwc.md)<br/>
[getc, getwc](getc-getwc.md)<br/>
