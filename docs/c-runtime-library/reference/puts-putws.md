---
title: "umieszcza _putws — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _putws
- puts
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
- _putts
- _putws
- puts
dev_langs: C++
helpviewer_keywords:
- strings [C++], writing
- _putts function
- standard output, writing to
- putws function
- puts function
- putts function
- _putws function
ms.assetid: 32dada12-ed45-40ac-be06-3feeced9ecd6
caps.latest.revision: "15"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: e05b0560032d79e5e69a1cafe8669c79160b8e1a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="puts-putws"></a>puts, _putws
Zapisuje ciąg **stdout**.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
      int puts(  
   const char *str   
);  
int _putws(  
   const wchar_t *str   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `str`  
 Ciąg w danych wyjściowych.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość nieujemną w przypadku powodzenia. Jeśli `puts` nie powiedzie się, zwraca `EOF`; Jeśli `_putws` nie powiedzie się, zwraca **weof —**. Jeśli `str` wskaźnika o wartości null, jest program obsługi nieprawidłowych parametrów zostanie wywołany, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może kontynuować, Ustaw funkcje `errno` do `EINVAL` i zwracać `EOF` lub **weof —**.  
  
 Aby uzyskać informacje na temat tych i innych kodów błędów, zobacz [_doserrno —, errno, _sys_errlist — i _sys_nerr —](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
## <a name="remarks"></a>Uwagi  
 `puts` Funkcji zapisy `str` do standardowego strumienia wyjściowego **stdout**, zastępując ciąg do zakończenia znak null ('\0') ze znakiem nowego wiersza (\n) do strumienia wyjściowego.  
  
 `_putws`jest to wersja znaków dwubajtowych `puts`; dwie funkcje zachowują się tak samo, jakby strumień jest otwarty w trybie ANSI. `puts`obecnie nie obsługuje dane wyjściowe do strumienia UNICODE.  
  
 W systemie Windows 2000 lub nowszego oraz **_putwch —** zapisuje znaków Unicode przy użyciu bieżących ustawień regionalnych konsoli.  
  
### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu  
  
|Procedura TCHAR.H|_Unicode — & _MBCS nie zdefiniowany|_MBCS zdefiniowano|_UNICODE zdefiniowano|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_putts`|`puts`|`puts`|`_putws`|  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`puts`|\<stdio.h >|  
|`_putws`|\<stdio.h >|  
  
 Konsola nie jest obsługiwana w [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] aplikacji. Uchwyty Standardowy strumień, które są skojarzone z konsoli programu —`stdin`, `stdout`, i `stderr`— muszą być przekierowywane przed funkcje wykonawcze języka C można używać ich w [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] aplikacji. Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).  
  
## <a name="libraries"></a>Biblioteki  
 Wszystkie wersje [biblioteki wykonawcze języka C](../../c-runtime-library/crt-library-features.md).  
  
## <a name="example"></a>Przykład  
  
```  
// crt_puts.c  
/* This program uses puts to write a string to stdout.  
 */  
  
#include <stdio.h>  
  
int main( void )  
{  
   puts( "Hello world from puts!" );  
}  
```  
  
## <a name="output"></a>Dane wyjściowe  
  
```  
Hello world from puts!  
```  
  
## <a name="see-also"></a>Zobacz też  
 [We/Wy strumienia](../../c-runtime-library/stream-i-o.md)   
 [fputs —, fputws —](../../c-runtime-library/reference/fputs-fputws.md)   
 [fgets, fgetws](../../c-runtime-library/reference/fgets-fgetws.md)