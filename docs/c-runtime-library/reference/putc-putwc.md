---
title: "putc —, putwc — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- putwc
- putc
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
- _puttc
- putwc
- putc
dev_langs:
- C++
helpviewer_keywords:
- streams, writing characters to
- characters, writing
- putwc function
- putc function
- _puttc function
- puttc function
ms.assetid: a37b2e82-9d88-4565-8190-ff8d04c0ddb9
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 4a3c07cab44f6b709affa22f470dfd7a8840b729
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2018
---
# <a name="putc-putwc"></a>putc, putwc
Zapisuje znak w strumieniu.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
      int putc(  
   int c,  
   FILE *stream   
);  
wint_t putwc(  
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
 Zwraca znak zapisywane. Błąd lub warunek plik końcowy `putc` i `putchar` zwracać `EOF`; `putwc` i `putwchar` zwracać **weof —**. Wszystkie cztery procedury, można użyć [ferror —](../../c-runtime-library/reference/ferror.md) lub [feof —](../../c-runtime-library/reference/feof.md) do sprawdzenia błąd lub koniec pliku. Jeśli przekazany wskaźnika o wartości null `stream`, program obsługi nieprawidłowych parametrów zostanie wywołany, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli jest dozwolone wykonywanie, aby kontynuować, te funkcje zwracają `EOF` lub **weof —** i ustaw `errno` do `EINVAL`.  
  
 Zobacz [_doserrno —, errno, _sys_errlist — i _sys_nerr —](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) Aby uzyskać więcej informacji na temat tych i innych kodów błędów.  
  
## <a name="remarks"></a>Uwagi  
 `putc` Procedury zapisuje pojedynczy znak `c` z danymi wyjściowymi `stream` w bieżącym położeniu. Dowolna liczba całkowita mogą zostać przekazane do `putc`, ale są zapisywane tylko pierwszych 8 bitów. `putchar` Procedura jest identyczna jak **putc — (** `c` **, stdout)**. Dla każdej procedury Jeśli wystąpi błąd, ustaw wskaźnik błędów dla tego strumienia. `putc` i `putchar` są podobne do `fputc` i `_fputchar`odpowiednio, ale są implementowane zarówno jako funkcje, jak i jako makra (zobacz [wybierania pomiędzy funkcjami i makrami](../../c-runtime-library/recommendations-for-choosing-between-functions-and-macros.md)). `putwc` i `putwchar` wersji znaków dwubajtowych `putc` i `putchar`odpowiednio. `putwc` i `putc` zachowują się tak samo, jakby strumień jest otwarty w trybie ANSI. `putc` obecnie nie obsługuje dane wyjściowe do strumienia UNICODE.  
  
 Wersje z **_nolock —** sufiks są identyczne z tą różnicą, że nie są chronione przez inne wątki od zakłóceń. Aby uzyskać więcej informacji, zobacz **_putc_nolock —, _putwc_nolock —**.  
  
### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu  
  
|Procedura TCHAR.H|_Unicode — & _MBCS nie zdefiniowany|_MBCS zdefiniowano|_UNICODE zdefiniowano|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_puttc`|`putc`|`putc`|**putwc**|  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`putc`|\<stdio.h>|  
|`putwc`|\<stdio.h > lub \<wchar.h >|  
  
Konsoli nie jest obsługiwane w aplikacjach systemu Windows platformy Uniwersalnej. Uchwyty Standardowy strumień, które są skojarzone z konsoli programu `stdin`, `stdout`, i `stderr`, muszą być przekierowywane przed funkcje wykonawcze języka C można używać ich w aplikacji platformy uniwersalnej systemu Windows. Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).
  
## <a name="libraries"></a>Biblioteki  
 Wszystkie wersje [biblioteki wykonawcze języka C](../../c-runtime-library/crt-library-features.md).  
  
## <a name="example"></a>Przykład  
  
```  
// crt_putc.c  
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
      ch = putc( *p, stream );  
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