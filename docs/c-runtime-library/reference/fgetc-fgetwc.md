---
title: "fgetc —, fgetwc — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- fgetwc
- fgetc
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
- _fgettc
- fgetwc
- fgetc
dev_langs: C++
helpviewer_keywords:
- fgettc function
- characters, reading
- _fgettc function
- fgetc function
- streams, reading characters from
- reading characters from streams
- fgetwc function
ms.assetid: 13348b7b-dc86-421c-9d6c-611ca79c8338
caps.latest.revision: "18"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: de0b211c15077f62ecd3af0f774125e91f53017a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="fgetc-fgetwc"></a>fgetc, fgetwc
Znak odczytu ze strumienia.  
  
## <a name="syntax"></a>Składnia  
  
```  
int fgetc(   
   FILE *stream   
);  
wint_t fgetwc(   
   FILE *stream   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `stream`  
 Wskaźnik do `FILE` struktury.  
  
## <a name="return-value"></a>Wartość zwracana  
 `fgetc`Zwraca znak odczytany jako `int` lub zwraca `EOF` wskazująca błąd lub koniec pliku. `fgetwc`Zwraca, jako [wint_t —](../../c-runtime-library/standard-types.md), znaków dwubajtowych, który odpowiada znaków do odczytu lub zwraca `WEOF` wskazująca błąd lub koniec pliku. Dla obu tych funkcji, należy użyć `feof` lub `ferror` odróżnić błąd warunku końcowego pliku. Jeśli wystąpi błąd odczytu, ustawiono Wskaźnik błędów dla tego strumienia. Jeśli `stream` jest `NULL`, `fgetc` i `fgetwc` Wywołaj program obsługi nieprawidłowych parametrów, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli dozwolone jest wykonywanie aby kontynuować, ustawianie tych funkcji `errno` do `EINVAL` i zwracać `EOF`.  
  
## <a name="remarks"></a>Uwagi  
 Każda z tych funkcji odczytuje od bieżącego położenia pliku skojarzone z pojedynczym znakiem `stream`. Funkcja zwiększa następnie kursor skojarzony plik (jeśli jest zdefiniowana), aby wskazywały na następny znak. Jeśli strumień jest na końcu pliku, jest ustawiony dla tego strumienia wskaźnika końca pliku.  
  
 `fgetc`jest odpowiednikiem `getc`, ale jest zaimplementowana tylko jako funkcję, a nie jako funkcję i makr.  
  
 `fgetwc`jest to wersja znaków dwubajtowych `fgetc`; odczytuje `c` jako znaków wielobajtowych lub znaków dwubajtowych zgodnie z czy `stream` jest otwarty w trybie tekst lub binarny.  
  
 Wersje z `_nolock` sufiks są identyczne z tą różnicą, że nie są chronione przez inne wątki od zakłóceń.  
  
 Aby uzyskać więcej informacji na temat przetwarzania znaki dwubajtowe i znaków wielobajtowych w trybach tekstowym i binarnym, zobacz [we/wy strumienia w Unicode w trybach tekstowym i binarnym](../../c-runtime-library/unicode-stream-i-o-in-text-and-binary-modes.md).  
  
### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu  
  
|Procedura TCHAR.H|_Unicode — & _MBCS nie zdefiniowany|_MBCS zdefiniowano|_UNICODE zdefiniowano|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_fgettc`|`fgetc`|`fgetc`|`fgetwc`|  
  
## <a name="requirements"></a>Wymagania  
  
|Funkcja|Wymagany nagłówek|  
|--------------|---------------------|  
|`fgetc`|\<stdio.h >|  
|`fgetwc`|\<stdio.h > lub \<wchar.h >|  
  
 Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md) we wprowadzeniu.  
  
## <a name="example"></a>Przykład  
  
```  
// crt_fgetc.c  
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
   fopen_s( &stream, "crt_fgetc.txt", "r" );  
   if( stream == NULL )  
      exit( 0 );  
  
   // Read in first 80 characters and place them in "buffer":   
   ch = fgetc( stream );  
   for( i=0; (i < 80 ) && ( feof( stream ) == 0 ); i++ )  
   {  
      buffer[i] = (char)ch;  
      ch = fgetc( stream );  
   }  
  
   // Add null to end string   
   buffer[i] = '\0';  
   printf( "%s\n", buffer );  
   fclose( stream );  
}  
```  
  
## <a name="input-crtfgetctxt"></a>Dane wejściowe: crt_fgetc.txt  
  
```  
Line one.  
Line two.  
```  
  
### <a name="output"></a>Dane wyjściowe  
  
```  
Line one.  
Line two.  
```  
  
## <a name="see-also"></a>Zobacz też  
 [We/Wy strumienia](../../c-runtime-library/stream-i-o.md)   
 [fputc —, fputwc —](../../c-runtime-library/reference/fputc-fputwc.md)   
 [getc, getwc](../../c-runtime-library/reference/getc-getwc.md)