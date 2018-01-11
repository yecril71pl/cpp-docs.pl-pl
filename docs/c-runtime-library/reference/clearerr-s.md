---
title: "clearerr_s — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: clearerr_s
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
f1_keywords: clearerr_s
dev_langs: C++
helpviewer_keywords:
- error indicator for streams
- resetting stream error indicator
- clearerr_s function
ms.assetid: b74d014d-b7a8-494a-a330-e5ffd5614772
caps.latest.revision: "19"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 5c79a3d73806e82c5de6f7f241d011b3d8e19590
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="clearerrs"></a>clearerr_s
Resetuje wskaźnik błędów dla strumienia. To jest wersja [clearerr —](../../c-runtime-library/reference/clearerr.md) ulepszeń zabezpieczeń zgodnie z opisem w [funkcje zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).  
  
## <a name="syntax"></a>Składnia  
  
```  
errno_t clearerr_s(  
   FILE *stream   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `stream`  
 Wskaźnik do `FILE` — struktura  
  
## <a name="return-value"></a>Wartość zwracana  
 Zero w przypadku powodzenia; `EINVAL` Jeśli `stream` ma wartość NULL.  
  
## <a name="remarks"></a>Uwagi  
 `clearerr_s` Funkcja resetuje wskaźnik błędów i plik końcowy wskaźnik `stream`. Wskaźniki błędów nie są automatycznie usuwane; Po ustawieniu wskaźnik błędów dla określonego strumienia operacji na strumieniu w dalszym ciągu zwracają wartość błąd do `clearerr_s`, `clearerr`, `fseek`, `fsetpos`, lub `rewind` jest wywoływana.  
  
 Jeśli `stream` ma wartość NULL, program obsługi nieprawidłowych parametrów zostanie wywołany, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może kontynuować, ta funkcja ustawia `errno` do `EINVAL` i zwraca `EINVAL`.  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`clearerr_s`|\<stdio.h >|  
  
 Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md) we wprowadzeniu.  
  
## <a name="example"></a>Przykład  
  
```  
// crt_clearerr_s.c  
// This program creates an error  
// on the standard input stream, then clears  
// it so that future reads won't fail.  
  
#include <stdio.h>  
  
int main( void )  
{  
   int c;  
   errno_t err;  
  
   // Create an error by writing to standard input.  
   putc( 'c', stdin );  
   if( ferror( stdin ) )  
   {  
      perror( "Write error" );  
      err = clearerr_s( stdin );  
      if (err != 0)  
      {  
         abort();  
      }  
   }  
  
   // See if read causes an error.  
   printf( "Will input cause an error? " );  
   c = getc( stdin );  
   if( ferror( stdin ) )  
   {  
      perror( "Read error" );  
      err = clearerr_s( stdin );  
      if (err != 0)  
      {  
         abort();  
      }  
   }  
}  
```  
  
```Output  
  
n  
  
```  
  
```Output  
  
      nWrite error: Bad file descriptor  
Will input cause an error? n  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Obsługa błędów](../../c-runtime-library/error-handling-crt.md)   
 [We/Wy strumienia](../../c-runtime-library/stream-i-o.md)   
 [clearerr —](../../c-runtime-library/reference/clearerr.md)   
 [_eof —](../../c-runtime-library/reference/eof.md)   
 [feof —](../../c-runtime-library/reference/feof.md)   
 [ferror —](../../c-runtime-library/reference/ferror.md)   
 [perror, _wperror](../../c-runtime-library/reference/perror-wperror.md)