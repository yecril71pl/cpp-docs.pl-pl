---
title: "gets_s —, _getws_s — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _getws_s
- gets_s
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
- _getws_s
- gets_s
dev_langs: C++
helpviewer_keywords:
- getws_s function
- _getws_s function
- lines, getting
- streams, getting lines
- buffers, avoiding overruns
- buffer overruns
- buffers, buffer overruns
- gets_s function
- standard input, reading from
ms.assetid: 5880c36f-122c-4061-a1a5-aeeced6fe58c
caps.latest.revision: "29"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: ea0c9053ef052359a0dc827299ade1ef2bbcb20f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="getss-getwss"></a>gets_s, _getws_s
Pobiera wiersza ze `stdin` strumienia. Te wersje programu [pobiera _getws —](../../c-runtime-library/gets-getws.md) zostały ulepszone zabezpieczenia, zgodnie z opisem w [funkcje zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).  
  
## <a name="syntax"></a>Składnia  
  
```  
char *gets_s(   
   char *buffer,  
   size_t sizeInCharacters  
);  
wchar_t *_getws_s(   
   wchar_t *buffer,  
   size_t sizeInCharacters  
);  
template <size_t size>  
char *gets_s(   
   char (&buffer)[size]  
); // C++ only  
template <size_t size>  
wchar_t *_getws_s(   
   wchar_t (&buffer)[size]  
); // C++ only  
```  
  
#### <a name="parameters"></a>Parametry  
 [out]`buffer`  
 Lokalizacja magazynu dla ciągu wejściowego.  
  
 [in]`sizeInCharacters`  
 Rozmiar buforu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca `buffer` w przypadku powodzenia. A `NULL` wskaźnik wskazuje błąd lub końca pliku. Użyj [ferror —](../../c-runtime-library/reference/ferror.md) lub [feof —](../../c-runtime-library/reference/feof.md) ustalenie, który wystąpił.  
  
## <a name="remarks"></a>Uwagi  
 `gets_s` Funkcja odczytuje wiersz z Standardowy strumień wejściowy `stdin` i przechowuje ją w `buffer`. Wiersz składa się z wszystkich znaków, w tym pierwszym znakiem nowego wiersza ("\n"). `gets_s`następnie zastępuje znaku nowego wiersza znak null ('\0') przed powrotem z wiersza. Z kolei `fgets_s` funkcja zachowuje znaku nowego wiersza.  
  
 Jeśli pierwszym znakiem odczytać znaki końca pliku, znak null znajduje się na początku `buffer` i `NULL` jest zwracany.  
  
 `_getws`jest to wersja znaków dwubajtowych `gets_s`; jego argumentów i wartości zwracanej są ciągami znaków dwubajtowych.  
  
 Jeśli `buffer` jest `NULL` lub `sizeInCharacters` jest mniejsza niż lub równa zero, lub jeśli bufor jest zbyt mały, aby pomieścił wierszu danych wejściowych i terminatorem null, te funkcje wywołanie program obsługi nieprawidłowych parametrów, zgodnie z opisem w [parametru Sprawdzanie poprawności](../../c-runtime-library/parameter-validation.md). Jeśli jest dozwolone wykonywanie, aby kontynuować, te funkcje zwracają `NULL` ustawiono errno `ERANGE`.  
  
 W języku C++ za pomocą tych funkcji zostało uproszczone dzięki przeciążenia szablonu; przeciążeń można automatycznie rozpoznać długość buforu (wyeliminowanie konieczności określania argumentem rozmiaru) i automatycznie można zastąpić starszą, które nie są bezpieczne funkcje z ich odpowiedniki nowsza, bezpieczne. Aby uzyskać więcej informacji, zobacz [Secure szablonu Overloads](../../c-runtime-library/secure-template-overloads.md).  
  
### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu  
  
|Procedura TCHAR.H|_Unicode — & _MBCS nie zdefiniowany|_MBCS zdefiniowano|_UNICODE zdefiniowano|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_getts`|`gets_s`|`gets_s`|`_getws`|  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`gets_s`|\<stdio.h >|  
|`_getws`|\<stdio.h > lub \<wchar.h >|  
  
 Konsola nie jest obsługiwana w [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] aplikacji. Uchwyty Standardowy strumień, które są skojarzone z konsoli programu —`stdin`, `stdout`, i `stderr`— muszą być przekierowywane przed funkcje wykonawcze języka C można używać ich w [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] aplikacji. Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).  
  
## <a name="example"></a>Przykład  
  
```  
// crt_gets_s.c  
// This program retrieves a string from the stdin and   
// prints the same string to the console.  
  
#include <stdio.h>  
  
int main( void )  
{  
   char line[21]; // room for 20 chars + '\0'  
   gets_s( line, 20 );  
   printf( "The line entered was: %s\n", line );  
}  
```  
  
```Output  
  
Hello there!The line entered was: Hello there!  
```  
  
## <a name="see-also"></a>Zobacz też  
 [We/Wy strumienia](../../c-runtime-library/stream-i-o.md)   
 [pobiera _getws —](../../c-runtime-library/gets-getws.md)   
 [fgets —, fgetws —](../../c-runtime-library/reference/fgets-fgetws.md)   
 [fputs —, fputws —](../../c-runtime-library/reference/fputs-fputws.md)   
 [umieszcza _putws —](../../c-runtime-library/reference/puts-putws.md)