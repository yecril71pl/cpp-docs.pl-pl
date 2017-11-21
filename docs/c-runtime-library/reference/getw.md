---
title: "_getw — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _getw
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
f1_keywords: _getw
dev_langs: C++
helpviewer_keywords:
- _getw function
- integers, getting from streams
- getw function
ms.assetid: ef75facc-b84e-470f-9f5f-8746c90822a0
caps.latest.revision: "14"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 9d5cf5147f3225c9cd5c6f0c91d60bcaeb75b188
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="getw"></a>_getw
Pobiera liczbę całkowitą ze strumienia.  
  
## <a name="syntax"></a>Składnia  
  
```  
int _getw(   
   FILE *stream   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `stream`  
 Wskaźnik do `FILE` struktury.  
  
## <a name="return-value"></a>Wartość zwracana  
 `_getw`Zwraca wartość liczby całkowitej do odczytu. Zwracana wartość `EOF` wskazuje błąd lub koniec pliku. Jednak ponieważ `EOF` wartości jest również wartością całkowitą uzasadnione, użyj `feof` lub `ferror` można zweryfikować warunek plik końcowy lub błędu. Jeśli `stream` jest `NULL`, program obsługi nieprawidłowych parametrów zostanie wywołany, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli jest dozwolone wykonywanie, aby kontynuować, `errno` ustawiono `EINVAL` i funkcja zwraca `EOF`.  
  
## <a name="remarks"></a>Uwagi  
 `_getw` Funkcja odczytuje następny wartości binarnej typu `int` z pliku skojarzone z `stream` i zwiększa wskaźnik skojarzony plik (jeśli istnieje) aby wskazywały na następny znak nieprzeczytana. `_getw`nie przyjmuje żadnych specjalnych wyrównania elementów w strumieniu. Może wystąpić problemy z eksportowanie `_getw` ponieważ rozmiar `int` typu i kolejności bajtów w ramach `int` typu różnią się w różnych systemach.  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`_getw`|\<stdio.h >|  
  
 Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md) we wprowadzeniu.  
  
## <a name="example"></a>Przykład  
  
```  
// crt_getw.c  
// This program uses _getw to read a word  
// from a stream, then performs an error check.  
  
#include <stdio.h>  
#include <stdlib.h>  
  
int main( void )  
{  
   FILE *stream;  
   int i;  
  
   if( fopen_s( &stream, "crt_getw.txt", "rb" ) )  
      printf( "Couldn't open file\n" );  
   else  
   {  
      // Read a word from the stream:  
      i = _getw( stream );  
  
      // If there is an error...  
      if( ferror( stream ) )  
      {  
         printf( "_getw failed\n" );  
         clearerr_s( stream );  
      }  
      else  
         printf( "First data word in file: 0x%.4x\n", i );  
      fclose( stream );  
   }  
}  
```  
  
## <a name="input-crtgetwtxt"></a>Dane wejściowe: crt_getw.txt  
  
```  
Line one.  
Line two.  
```  
  
### <a name="output"></a>Dane wyjściowe  
  
```  
First data word in file: 0x656e694c  
```  
  
## <a name="see-also"></a>Zobacz też  
 [We/Wy strumienia](../../c-runtime-library/stream-i-o.md)   
 [_putw —](../../c-runtime-library/reference/putw.md)