---
title: "getchar, getwchar — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- getchar
- getwchar
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
- getwchar
- GetChar
dev_langs: C++
helpviewer_keywords:
- gettchar function
- characters, reading
- getwchar function
- _gettchar function
- standard input, reading from
ms.assetid: 19fda588-3e33-415c-bb60-dd73c028086a
caps.latest.revision: "15"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: bc45c7d367008745b7cfa7e933ec65909c37fde8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="getchar-getwchar"></a>getchar, getwchar
Odczytuje znak z standardowe dane wejściowe.  
  
## <a name="syntax"></a>Składnia  
  
```  
int getchar();  
wint_t getwchar();  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca znak do odczytu. Błąd odczytu lub warunek plik końcowy `getchar` zwraca `EOF`, i `getwchar` zwraca `WEOF`. Dla `getchar`, użyj `ferror` lub `feof` do sprawdzania błędów lub na końcu pliku.  
  
## <a name="remarks"></a>Uwagi  
 Każda procedura odczytuje pojedynczy znak z `stdin` i zwiększa kursor skojarzony plik na następny znak. `getchar`jest taka sama jak [_fgetchar —](../../c-runtime-library/reference/fgetc-fgetwc.md), ale jest zaimplementowana, jako funkcję, a makra.  
  
 Te funkcje Zablokuj wątek wywołujący i w związku z tym są wątkowo. Wersja — blokowanie dla [_getchar_nolock —, _getwchar_nolock —](../../c-runtime-library/reference/getchar-nolock-getwchar-nolock.md).  
  
### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu  
  
|Procedura TCHAR.H|_Unicode — & _MBCS nie zdefiniowany|_MBCS zdefiniowano|_UNICODE zdefiniowano|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_gettchar`|`getchar`|`getchar`|`getwchar`|  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`getchar`|\<stdio.h >|  
|`getwchar`|\<stdio.h > lub \<wchar.h >|  
  
 Konsola nie jest obsługiwana w [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] aplikacji. Uchwyty Standardowy strumień, które są skojarzone z konsoli programu —`stdin`, `stdout`, i `stderr`— muszą być przekierowywane przed funkcje wykonawcze języka C można używać ich w [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] aplikacji. Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).  
  
## <a name="example"></a>Przykład  
  
```  
// crt_getchar.c  
// Use getchar to read a line from stdin.  
  
#include <stdio.h>  
  
int main()  
{  
    char buffer[81];  
    int i, ch;  
  
    for (i = 0; (i < 80) && ((ch = getchar()) != EOF)  
                         && (ch != '\n'); i++)  
    {  
        buffer[i] = (char) ch;  
    }  
  
    // Terminate string with a null character   
    buffer[i] = '\0';  
    printf( "Input was: %s\n", buffer);  
}  
```  
  
```Output  
  
This textInput was: This text  
```  
  
## <a name="see-also"></a>Zobacz też  
 [We/Wy strumienia](../../c-runtime-library/stream-i-o.md)   
 [getc —, getwc —](../../c-runtime-library/reference/getc-getwc.md)   
 [fgetc —, fgetwc —](../../c-runtime-library/reference/fgetc-fgetwc.md)   
 [_getch —, _getwch —](../../c-runtime-library/reference/getch-getwch.md)   
 [putc —, putwc —](../../c-runtime-library/reference/putc-putwc.md)   
 [ungetc, ungetwc](../../c-runtime-library/reference/ungetc-ungetwc.md)