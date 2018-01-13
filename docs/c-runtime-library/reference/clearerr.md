---
title: "clearerr — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: clearerr
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
f1_keywords: clearerr
dev_langs: C++
helpviewer_keywords:
- error indicator for streams
- resetting stream error indicator
- clearerr function
ms.assetid: a9711cd4-3335-43d4-a018-87bbac5b3bac
caps.latest.revision: "21"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 35fafbe762780ace0fbd255f905307f7793d4c04
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="clearerr"></a>clearerr
Resetuje wskaźnik błędów dla strumienia. Bezpieczniejsza wersja ta funkcja jest dostępna; zobacz [clearerr_s —](../../c-runtime-library/reference/clearerr-s.md).  
  
## <a name="syntax"></a>Składnia  
  
```  
void clearerr(  
   FILE *stream   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `stream`  
 Wskaźnik do `FILE` struktury.  
  
## <a name="remarks"></a>Uwagi  
 `clearerr` Funkcja resetuje wskaźnik błędów i plik końcowy wskaźnik `stream`. Wskaźniki błędów nie są automatycznie usuwane; Po ustawieniu wskaźnik błędów dla określonego strumienia operacji na strumieniu w dalszym ciągu zwracają wartość błąd do `clearerr`, `fseek`, `fsetpos`, lub `rewind` jest wywoływana.  
  
 Jeśli `stream` jest `NULL`, program obsługi nieprawidłowych parametrów zostanie wywołany, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może kontynuować, ta funkcja ustawia `errno` do `EINVAL` i zwraca. Aby uzyskać więcej informacji na temat `errno` i kody błędów, zobacz [errno — stałe](../../c-runtime-library/errno-constants.md).  
  
 Bezpieczniejsza wersja ta funkcja jest dostępna; zobacz [clearerr_s —](../../c-runtime-library/reference/clearerr-s.md).  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`clearerr`|\<stdio.h >|  
  
 Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md) we wprowadzeniu.  
  
## <a name="example"></a>Przykład  
  
```  
// crt_clearerr.c  
// This program creates an error  
// on the standard input stream, then clears  
// it so that future reads won't fail.  
  
#include <stdio.h>  
  
int main( void )  
{  
   int c;  
   // Create an error by writing to standard input.  
   putc( 'c', stdin );  
   if( ferror( stdin ) )  
   {  
      perror( "Write error" );  
      clearerr( stdin );  
   }  
  
   // See if read causes an error.  
   printf( "Will input cause an error? " );  
   c = getc( stdin );  
   if( ferror( stdin ) )  
   {  
      perror( "Read error" );  
      clearerr( stdin );  
   }  
   else  
      printf( "No read error\n" );  
}  
```  
  
```Output  
  
n  
  
```  
  
```Output  
  
      nWrite error: No error  
Will input cause an error? n  
No read error  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Obsługa błędów](../../c-runtime-library/error-handling-crt.md)   
 [We/Wy strumienia](../../c-runtime-library/stream-i-o.md)   
 [_eof —](../../c-runtime-library/reference/eof.md)   
 [feof —](../../c-runtime-library/reference/feof.md)   
 [ferror —](../../c-runtime-library/reference/ferror.md)   
 [perror, _wperror](../../c-runtime-library/reference/perror-wperror.md)