---
title: "printf, _printf_l —, wprintf, _wprintf_l — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- _printf_l
- wprintf
- _wprintf_l
- printf
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
apitype: DLLExport
f1_keywords:
- printf
- _tprintf
- wprintf
dev_langs:
- C++
helpviewer_keywords:
- printf function
- printf_l function
- tprintf_l function
- tprintf function
- _printf_l function
- wprintf function
- writing to console
- wprintf_l function
- _tprintf_l function
- _wprintf_l function
- _tprintf function
- printf function, format specification fields
- printf function, using
- formatted text [C++]
ms.assetid: 77a854ae-5b48-4865-89f4-f2dc5cf80f52
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f2ebdd4061b50646f9450bfdfaf2ea4db90b5774
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2018
---
# <a name="printf-printfl-wprintf-wprintfl"></a>printf, _printf_l, wprintf, _wprintf_l
Drukowanie sformatowanych dane wyjściowe do standardowego strumienia wyjściowego. Bezpieczniejsza wersje te funkcje są dostępne; zobacz [printf_s —, _printf_s_l —, wprintf_s —, _wprintf_s_l —](../../c-runtime-library/reference/printf-s-printf-s-l-wprintf-s-wprintf-s-l.md).  
  
## <a name="syntax"></a>Składnia  
  
```  
int printf(  
   const char *format [,  
   argument]...   
);  
int _printf_l(  
   const char *format,  
   locale_t locale [,  
   argument]...   
);  
int wprintf(  
   const wchar_t *format [,  
   argument]...   
);  
int _wprintf_l(  
   const wchar_t *format,  
   locale_t locale [,  
   argument]...   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `format`  
 Format formantu.  
  
 `argument`  
 Argumenty opcjonalne.  
  
 `locale`  
 Ustawienia regionalne do użycia.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca liczbę znakom lub wartość ujemną, jeśli wystąpi błąd. Jeśli `format` jest `NULL`, program obsługi nieprawidłowych parametrów zostanie wywołany, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli jest dozwolone wykonywanie, aby kontynuować, funkcja zwraca wartość -1 i zestawy `errno` do `EINVAL`. Jeśli **EOF** (0xFFFF) napotkano w `argument`, funkcja zwraca wartość -1.  
  
 Aby uzyskać informacje dotyczące `errno` i kody błędów, zobacz [_doserrno —, errno, _sys_errlist — i _sys_nerr —](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
## <a name="remarks"></a>Uwagi  
 `printf` Funkcji formatuje i wyświetla serii znaków i wartości do standardowego strumienia wyjściowego, `stdout`. Jeśli argumenty `format` ciągu `format` ciąg musi zawierać specyfikacji, które określają format wyjściowy dla argumentów. `printf` i [fprintf —](../../c-runtime-library/reference/fprintf-fprintf-l-fwprintf-fwprintf-l.md) zachowują się tak samo, z wyjątkiem `printf` zapisuje dane wyjściowe do `stdout` , a nie do miejsca docelowego typu `FILE`.  
  
 `wprintf` jest to wersja znaków dwubajtowych `printf`; `format` jest ciągiem znaków dwubajtowych. `wprintf` i `printf` zachowują się tak samo, jakby strumień jest otwarty w trybie ANSI. `printf` aktualnie nie obsługuje dane wyjściowe do strumienia UNICODE.  
  
 Wersje tych funkcji z `_l` sufiks są identyczne, z wyjątkiem tego, aby używały parametr ustawień regionalnych przekazano zamiast bieżącego ustawienia regionalne wątku.  
  
### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu  
  
|Procedura TCHAR.H|_Unicode — & _MBCS nie zdefiniowany|_MBCS zdefiniowano|_unicode — definicja|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_tprintf`|`printf`|`printf`|`wprintf`|  
  
 `format` Argument składa się ze znaków zwykłej, sekwencji unikowych i (Jeśli argumenty `format`) specyfikacji formatu. Zwykłe znaków oraz sekwencje specjalne są kopiowane do `stdout` w kolejności ich wyglądu. Na przykład wiersz:  
  
```  
printf("Line one\n\t\tLine two\n");   
```  
  
 generuje dane wyjściowe:  
  
```  
Line one  
        Line two  
```  
  
 [Specyfikacje formatu](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md) zawsze zaczynać się od znaku procentu (`%`) i są odczytywane lewej do prawej. Gdy `printf` napotka pierwszy specyfikacji formatu (jeśli istnieje), są konwertowane na wartość pierwszego argumentu po `format` i odpowiednio danych wyjściowych. Drugi specyfikacji formatu powoduje, że drugi argument przekonwertować i dane wyjściowe, i tak dalej. W przypadku więcej argumentów niż Brak specyfikacji formatu dodatkowe argumenty są ignorowane. Wyniki są niezdefiniowana, jeśli nie ma za mało argumentów dla wszystkich specyfikacji formatu.  
  
> [!IMPORTANT]
>  Upewnij się, że `format` nie jest ciągiem zdefiniowane przez użytkownika.  
  
### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu  
  
|Procedura tchar.h|_UNICODE i _MBCS niezdefiniowane|_MBCS zdefiniowano|_UNICODE zdefiniowano|  
|---------------------|--------------------------------------|--------------------|-----------------------|  
|`_tprintf`|`printf`|`printf`|`wprintf`|  
|`_tprintf_l`|`_printf_l`|`_printf_l`|`_wprintf_l`|  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`printf`, `_printf_l`|\<stdio.h>|  
|`wprintf`, `_wprintf_l`|\<stdio.h > lub \<wchar.h >|  
  
Konsoli nie jest obsługiwane w aplikacjach systemu Windows platformy Uniwersalnej. Uchwyty Standardowy strumień, które są skojarzone z konsoli programu `stdin`, `stdout`, i `stderr`, muszą być przekierowywane przed funkcje wykonawcze języka C można używać ich w aplikacji platformy uniwersalnej systemu Windows. Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).
  
## <a name="example"></a>Przykład  
  
```  
// crt_printf.c  
// This program uses the printf and wprintf functions  
// to produce formatted output.  
  
#include <stdio.h>  
  
int main( void )  
{  
   char     ch = 'h',   
            *string = "computer";  
   wchar_t  wch = L'w',   
            *wstring = L"Unicode";  
   int      count = -9234;  
   double   fp = 251.7366;  
  
   // Display integers  
   printf( "Integer formats:\n"  
           "   Decimal: %d  Justified: %.6d  "  
           "Unsigned: %u\n",  
           count, count, count, count );  
  
   // Display decimals  
   printf( "Decimal %d as:\n   Hex: %Xh  "  
           "C hex: 0x%x  Octal: %o\n",  
            count, count, count, count );  
  
   // Display in different radixes  
   printf( "Digits 10 equal:\n   Hex: %i  "  
           "Octal: %i  Decimal: %i\n",  
            0x10, 010, 10 );  
  
   // Display characters  
   printf("Characters in field (1):\n"  
          "%10c%5hc%5C%5lc\n",  
          ch, ch, wch, wch);  
   wprintf(L"Characters in field (2):\n"  
           L"%10C%5hc%5c%5lc\n",  
           ch, ch, wch, wch);  
  
   // Display strings  
   printf("Strings in field (1):\n%25s\n"  
          "%25.4hs\n   %S%25.3ls\n",  
          string, string, wstring, wstring);  
   wprintf(L"Strings in field (2):\n%25S\n"  
           L"%25.4hs\n   %s%25.3ls\n",  
           string, string, wstring, wstring);  
  
   // Display real numbers  
   printf("Real numbers:\n   %f %.2f %e %E\n",  
          fp, fp, fp, fp );  
  
   // Display pointer  
   printf( "\nAddress as:   %p\n", &count);  
}  
```  
  
## <a name="sample-output"></a>Przykładowe dane wyjściowe  
  
```  
Integer formats:  
   Decimal: -9234  Justified: -009234  Unsigned: 4294958062  
Decimal -9234 as:  
   Hex: FFFFDBEEh  C hex: 0xffffdbee  Octal: 37777755756  
Digits 10 equal:  
   Hex: 16  Octal: 8  Decimal: 10  
Characters in field (1):  
         h    h    w    w  
Characters in field (2):  
         h    h    w    w  
Strings in field (1):  
                 computer  
                     comp  
   Unicode                      Uni  
Strings in field (2):  
                 computer  
                     comp  
   Unicode                      Uni  
Real numbers:  
   251.736600 251.74 2.517366e+002 2.517366E+002  
  
Address as:   0012FF3C  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Obsługa liczb zmiennoprzecinkowych](../../c-runtime-library/floating-point-support.md)   
 [We/Wy strumienia](../../c-runtime-library/stream-i-o.md)   
 [Ustawienia regionalne](../../c-runtime-library/locale.md)   
 [fopen —, _wfopen —](../../c-runtime-library/reference/fopen-wfopen.md)   
 [_fprintf_p, _fprintf_p_l, _fwprintf_p, _fwprintf_p_l](../../c-runtime-library/reference/fprintf-p-fprintf-p-l-fwprintf-p-fwprintf-p-l.md)   
 [scanf, _scanf_l —, wscanf — _wscanf_l —](../../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md)   
 [sprintf, _sprintf_l, swprintf, _swprintf_l, \__swprintf_l](../../c-runtime-library/reference/sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)   
 [vprintf — funkcje](../../c-runtime-library/vprintf-functions.md)   
 [_set_output_format](../../c-runtime-library/set-output-format.md)