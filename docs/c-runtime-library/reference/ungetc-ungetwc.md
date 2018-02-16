---
title: "ungetc —, ungetwc — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- ungetwc
- ungetc
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
- _ungettc
- ungetwc
- ungetc
dev_langs:
- C++
helpviewer_keywords:
- ungetwc function
- ungettc function
- characters, pushing back onto stream
- _ungettc function
- ungetc function
ms.assetid: e0754f3a-b4c6-408f-90c7-e6387b830d84
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: d65453f1254e4c42658ef6f27d7c90d2ad0022b9
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2018
---
# <a name="ungetc-ungetwc"></a>ungetc, ungetwc
Wypycha znak wstecz do strumienia.  
  
## <a name="syntax"></a>Składnia  
  
```  
int ungetc(  
   int c,  
   FILE *stream   
);  
wint_t ungetwc(  
   wint_t c,  
   FILE *stream   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `c`  
 Znak do zostać przeniesiony.  
  
 `stream`  
 Wskaźnik do `FILE` struktury.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli się powiedzie, każda z tych funkcji zwraca znak argument `c`. Jeśli `c` nie może zostać przeniesiony wstecz lub jeśli żadne znaki nie do odczytu strumień wejściowy jest bez zmian i `ungetc` zwraca `EOF`; `ungetwc` zwraca `WEOF`. Jeśli `stream` jest `NULL`, program obsługi nieprawidłowych parametrów zostanie wywołany, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli jest dozwolone wykonywanie, aby kontynuować, `EOF` lub `WEOF` jest zwracany i `errno` ma ustawioną wartość `EINVAL`.  
  
 Aby uzyskać informacje na temat tych i innych kodów błędów, zobacz [_doserrno —, errno, _sys_errlist — i _sys_nerr —](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
## <a name="remarks"></a>Uwagi  
 `ungetc` Funkcja wypchnięcia znak `c` ponownie do `stream` i czyści wskaźnik końca pliku. Strumień musi być otwarty do odczytu. Kolejnej operacji odczytu na `stream` rozpoczyna się od `c`. Próba push `EOF` na stream przy użyciu `ungetc` jest ignorowana.  
  
 Znaki umieszczony w strumieniu przez `ungetc` mogą zostać utracone, jeśli `fflush`, `fseek`, `fsetpos`, lub `rewind` jest wywoływana przed znak jest do odczytu ze strumienia. Wskaźnik położenia pliku będzie miał wartość sprzed znaki zostały przekazane ponownie. Niezmieniona magazynu zewnętrznego odpowiadający strumienia. Pomyślnie `ungetc` wywołanie przed strumienia tekstu, wskaźnika położenia pliku jest nieokreślony aż wszystkie znaki przesunięta zwroty są odczytywane lub odrzucone. Na każdym pomyślnym `ungetc` wywołania przed binarne strumienia wskaźnika położenia pliku zostanie zmniejszona; Jeśli wartość 0, przed wywołaniem metody, wartość jest niezdefiniowana po wywołaniu.  
  
 Wyniki są nieprzewidywalne Jeśli `ungetc` jest wywoływana dwukrotnie bez położenia pliku operacji między dwoma wywołania odczytu lub. Po wywołaniu `fscanf`, wywołanie `ungetc` może zakończyć się niepowodzeniem, chyba że innej operacji odczytu (takie jak `getc`) ma zostać wykonane. Jest to spowodowane `fscanf` sam wywołuje `ungetc`.  
  
 `ungetwc` jest to wersja znaków dwubajtowych `ungetc`. Jednak na każdym pomyślnym `ungetwc` wywołanie przed tekstowe lub binarne strumienia wartości wskaźnika położenia pliku jest nieokreślony dopóki wszystkie znaki przesunięta zwroty są odczytywane lub odrzucone.  
  
 Te funkcje są wątkowo i Zablokuj poufne dane podczas wykonywania. Wersja — blokowanie dla [_ungetc_nolock —, _ungetwc_nolock —](../../c-runtime-library/reference/ungetc-nolock-ungetwc-nolock.md).  
  
### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu  
  
|Procedura TCHAR.H|_Unicode — & _MBCS nie zdefiniowany|_MBCS zdefiniowano|_UNICODE zdefiniowano|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_ungettc`|`ungetc`|`ungetc`|`ungetwc`|  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`ungetc`|\<stdio.h>|  
|`ungetwc`|\<stdio.h > lub \<wchar.h >|  
  
Konsoli nie jest obsługiwane w aplikacjach systemu Windows platformy Uniwersalnej. Uchwyty Standardowy strumień, które są skojarzone z konsoli programu `stdin`, `stdout`, i `stderr`, muszą być przekierowywane przed funkcje wykonawcze języka C można używać ich w aplikacji platformy uniwersalnej systemu Windows. Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).
  
## <a name="example"></a>Przykład  
  
```  
// crt_ungetc.c  
// This program first converts a character  
// representation of an unsigned integer to an integer. If  
// the program encounters a character that is not a digit,  
// the program uses ungetc to replace it in the  stream.  
//  
  
#include <stdio.h>  
#include <ctype.h>  
  
int main( void )  
{  
   int ch;  
   int result = 0;  
  
   // Read in and convert number:  
   while( ((ch = getchar()) != EOF) && isdigit( ch ) )  
      result = result * 10 + ch - '0';    // Use digit.  
   if( ch != EOF )  
      ungetc( ch, stdin );                // Put nondigit back.  
   printf( "Number = %d\nNext character in stream = '%c'",   
            result, getchar() );  
}  
```  
  
```Output  
  
      521aNumber = 521  
Next character in stream = 'a'  
```  
  
## <a name="see-also"></a>Zobacz też  
 [We/Wy strumienia](../../c-runtime-library/stream-i-o.md)   
 [getc —, getwc —](../../c-runtime-library/reference/getc-getwc.md)   
 [putc, putwc](../../c-runtime-library/reference/putc-putwc.md)