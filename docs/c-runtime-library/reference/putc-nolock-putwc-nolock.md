---
title: "_putc_nolock —, _putwc_nolock — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _putc_nolock
- _putwc_nolock
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
- _puttc_nolock
- puttc_nolock
- putwc_nolock
- _putwc_nolock
- _putc_nolock
- putc_nolock
dev_langs: C++
helpviewer_keywords:
- puttc_nolock function
- putc_nolock function
- _putc_nolock function
- streams, writing characters to
- characters, writing
- putwc_nolock function
- _puttc_nolock function
- _putwc_nolock function
ms.assetid: 3cfc7f21-c9e8-4b7f-b0fb-af0d4d85e7e1
caps.latest.revision: "15"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: ad994b11cecb304bd91d357516aa7c81a7351917
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="putcnolock-putwcnolock"></a>_putc_nolock, _putwc_nolock
Zapisuje znak w strumieniu bez blokowania wątku.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
      int _putc_nolock(  
   int c,  
   FILE *stream   
);  
wint_t _putwc_nolock(  
   wchar_t c,  
   FILE *stream   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `c`  
 Znak do zapisania.  
  
 `stream`  
 Wskaźnik do **pliku** struktury.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zobacz **putc —, putwc —**.  
  
## <a name="remarks"></a>Uwagi  
 `_putc_nolock`i `_putwc_nolock` są takie same jak wersje bez **_nolock —** sufiks z tą różnicą, że nie są chronione przez inne wątki od zakłóceń. Może być szybsze, ponieważ nie wiążą się z obciążenie zablokowania inne wątki. Ich używać tylko w kontekstach wątkowo, np. aplikacje jednowątkowe lub gdzie wywoływania zakres już obsługuje izolacji wątku.  
  
 `_putwc_nolock`jest to wersja znaków dwubajtowych `_putc_nolock`; dwie funkcje zachowują się tak samo, jakby strumień jest otwarty w trybie ANSI. `_putc_nolock`obecnie nie obsługuje dane wyjściowe do strumienia UNICODE.  
  
### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu  
  
|Procedura tchar.h|_UNICODE i _MBCS niezdefiniowane|_MBCS zdefiniowano|_UNICODE zdefiniowano|  
|---------------------|--------------------------------------|--------------------|-----------------------|  
|`_puttc_nolock`|`_putc_nolock`|`_putc_nolock`|**_putwc_nolock —**|  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`_putc_nolock`|\<stdio.h >|  
|`_putwc_nolock`|\<stdio.h > lub \<wchar.h >|  
  
 Konsola nie jest obsługiwana w [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] aplikacji. Uchwyty Standardowy strumień, które są skojarzone z konsoli programu —`stdin`, `stdout`, i `stderr`— muszą być przekierowywane przed funkcje wykonawcze języka C można używać ich w [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] aplikacji. Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).  
  
## <a name="libraries"></a>Biblioteki  
 Wszystkie wersje [biblioteki wykonawcze języka C](../../c-runtime-library/crt-library-features.md).  
  
## <a name="example"></a>Przykład  
  
```  
// crt_putc_nolock.c  
/* This program uses putc to write buffer  
 * to a stream. If an error occurs, the program  
 * stops before writing the entire buffer.  
 */  
  
#include <stdio.h>  
  
int main( void )  
{  
   FILE *stream;  
   char *p, buffer[] = "This is the line of output\n";  
   int  ch;  
  
   ch = 0;  
   /* Make standard out the stream and write to it. */  
   stream = stdout;  
   for( p = buffer; (ch != EOF) && (*p != '\0'); p++ )  
      ch = _putc_nolock( *p, stream );  
}  
```  
  
## <a name="output"></a>Dane wyjściowe  
  
```  
This is the line of output  
```  
  
## <a name="see-also"></a>Zobacz też  
 [We/Wy strumienia](../../c-runtime-library/stream-i-o.md)   
 [fputc —, fputwc —](../../c-runtime-library/reference/fputc-fputwc.md)   
 [getc, getwc](../../c-runtime-library/reference/getc-getwc.md)