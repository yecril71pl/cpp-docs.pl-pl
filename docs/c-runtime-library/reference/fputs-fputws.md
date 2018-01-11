---
title: "fputs —, fputws — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- fputs
- fputws
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
- fputs
- fputws
- _fputts
dev_langs: C++
helpviewer_keywords:
- streams, writing strings to
- fputws function
- _fputts function
- fputs function
- fputts function
ms.assetid: d48c82b8-aa17-4830-8c7d-30442ddbb326
caps.latest.revision: "18"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: e4fcfe29abceb102534cd376c563917f3804d6df
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="fputs-fputws"></a>fputs, fputws
Zapisuje ciąg w strumieniu.  
  
## <a name="syntax"></a>Składnia  
  
```  
int fputs(   
   const char *str,  
   FILE *stream   
);  
int fputws(   
   const wchar_t *str,  
   FILE *stream   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `str`  
 Ciąg w danych wyjściowych.  
  
 `stream`  
 Wskaźnik do `FILE` struktury.  
  
## <a name="return-value"></a>Wartość zwracana  
 Każda z tych funkcji zwraca wartość nieujemną, jeśli powiedzie się. W przypadku wystąpienia błędu `fputs` i `fputws` zwracać `EOF`. Jeśli `str` lub `stream` jest wskaźnika o wartości null, te funkcje Wywołaj program obsługi nieprawidłowych parametrów, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli dozwolone jest wykonywanie aby kontynuować, ustawianie tych funkcji `errno` do `EINVAL` , a następnie `fputs` zwraca `EOF`, i `fputws` zwraca `WEOF`.  
  
 Zobacz [_doserrno —, errno, _sys_errlist — i _sys_nerr —](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) Aby uzyskać więcej informacji na temat tych i innych kodów błędów.  
  
## <a name="remarks"></a>Uwagi  
 Każdy z tych funkcji kopie `str` z danymi wyjściowymi `stream` w bieżącym położeniu. `fputws`kopiuje argument znaków dwubajtowych `str` do `stream` jako ciąg znaków wielobajtowych lub ciągiem znaków dwubajtowych zgodnie z czy `stream` odpowiednio jest otwarty w trybie tekstu lub w trybie binarnym. Żadna funkcja kopiuje znak końcowy null.  
  
 Dwie funkcje zachowują się tak samo, jakby strumień jest otwarty w trybie ANSI. `fputs`aktualnie nie obsługuje dane wyjściowe do strumienia UNICODE.  
  
### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu  
  
|Procedura TCHAR.H|_Unicode — & _MBCS nie zdefiniowany|_MBCS zdefiniowano|_UNICODE zdefiniowano|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_fputts`|`fputs`|`fputs`|`fputws`|  
  
## <a name="requirements"></a>Wymagania  
  
|Funkcja|Wymagany nagłówek|  
|--------------|---------------------|  
|`fputs`|\<stdio.h >|  
|`fputws`|\<stdio.h > lub \<wchar.h >|  
  
 Konsola nie jest obsługiwana w [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] aplikacji. Uchwyty Standardowy strumień, które są skojarzone z konsoli programu —`stdin`, `stdout`, i `stderr`— muszą być przekierowywane przed funkcje wykonawcze języka C można używać ich w [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] aplikacji. Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).  
  
## <a name="example"></a>Przykład  
  
```  
// crt_fputs.c  
// This program uses fputs to write  
// a single line to the stdout stream.  
  
#include <stdio.h>  
  
int main( void )  
{  
   fputs( "Hello world from fputs.\n", stdout );  
}  
```  
  
```Output  
Hello world from fputs.  
```  
  
## <a name="see-also"></a>Zobacz też  
 [We/Wy strumienia](../../c-runtime-library/stream-i-o.md)   
 [fgets —, fgetws —](../../c-runtime-library/reference/fgets-fgetws.md)   
 [pobiera _getws —](../../c-runtime-library/gets-getws.md)   
 [puts, _putws](../../c-runtime-library/reference/puts-putws.md)