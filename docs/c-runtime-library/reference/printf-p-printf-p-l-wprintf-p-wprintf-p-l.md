---
title: "_printf_p —, _printf_p_l —, _wprintf_p —, _wprintf_p_l — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _printf_p
- _wprintf_p
- _printf_p_l
- _wprintf_p_l
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
- wprintf_p
- _wprintf_p
- printf_p_l
- _printf_p
- printf_p
- _wprintf_p_l
- _printf_p_l
- wprintf_p_l
dev_langs: C++
helpviewer_keywords:
- printf_p function
- printf_p_l function
- wprintf_p function
- wprintf_p_l function
- _tprintf_p_l function
- _wprintf_p function
- _wprintf_p_l function
- _printf_p function
- tprintf_p_l function
- _printf_p_l function
ms.assetid: 1b7e9ef9-a069-45db-af9d-c2730168322e
caps.latest.revision: "22"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 19bbe19ed2cf753d07cfe9c7e42fe533bc90a834
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="printfp-printfpl-wprintfp-wprintfpl"></a>_printf_p, _printf_p_l, _wprintf_p, _wprintf_p_l
Drukuje sformatowane dane wyjściowe do standardowego strumienia wyjściowego i umożliwia określenie kolejności, w której parametry są używane w ciągu formatu.  
  
## <a name="syntax"></a>Składnia  
  
```  
int _printf_p(  
   const char *format [,  
   argument]...   
);  
int _printf_p_l(  
   const char *format,  
   locale_t locale [,  
   argument]...   
);  
int _wprintf_p(  
   const wchar_t *format [,  
   argument]...   
);  
int _wprintf_p_l(  
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
 Zwraca liczbę znakom lub wartość ujemną, jeśli wystąpi błąd.  
  
## <a name="remarks"></a>Uwagi  
 `_printf_p` Funkcji formatuje i wyświetla serii znaków i wartości do standardowego strumienia wyjściowego, `stdout`. Jeśli argumenty `format` ciągu `format` ciąg musi zawierać specyfikacji, które określają format wyjściowy dla argumentów (zobacz [printf_p parametry pozycyjne](../../c-runtime-library/printf-p-positional-parameters.md)).  
  
 Różnica między `_printf_p` i `printf_s` jest to, że `_printf_p` parametrów pozycyjnych obsługuje, które umożliwiają określenie kolejności, w którym argumenty są używane w ciągu formatu. Aby uzyskać więcej informacji, zobacz [printf_p parametry pozycyjne](../../c-runtime-library/printf-p-positional-parameters.md).  
  
 `_wprintf_p`jest to wersja znaków dwubajtowych `_printf_p`; działają tak samo, jeśli strumień jest otwarty w trybie ANSI. `_printf_p`obecnie nie obsługuje dane wyjściowe do strumienia UNICODE.  
  
 Wersje tych funkcji z `_l` sufiks są identyczne, z wyjątkiem tego, aby używały parametr ustawień regionalnych przekazano zamiast bieżącego ustawienia regionalne wątku.  
  
> [!IMPORTANT]
>  Upewnij się, że `format` nie jest ciągiem zdefiniowane przez użytkownika.  
  
 Jeśli `format` lub `argument` są `NULL`, lub w formacie ciągu zawiera nieprawidłowe znaki formatowania, `_printf_p` i `_wprintf_p` funkcji Wywołaj program obsługi nieprawidłowych parametrów, zgodnie z opisem w [parametru Sprawdzanie poprawności](../../c-runtime-library/parameter-validation.md). Jeśli jest dozwolone wykonywanie, aby kontynuować, funkcja zwraca wartość -1 i zestawy `errno` do `EINVAL`.  
  
### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu  
  
|Procedura tchar.h|_UNICODE i _MBCS niezdefiniowane|_MBCS zdefiniowano|_UNICODE zdefiniowano|  
|---------------------|--------------------------------------|--------------------|-----------------------|  
|`_tprintf_p`|`_printf_p`|`_printf_p`|`_wprintf_p`|  
|`_tprintf_p_l`|`_printf_p_l`|`_printf_p_l`|`_wprintf_p_l`|  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`_printf_p`, `_printf_p_l`|\<stdio.h >|  
|`_wprintf_p`, `_wprintf_p_l`|\<stdio.h > lub \<wchar.h >|  
  
 Konsola nie jest obsługiwana w [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] aplikacji. Uchwyty Standardowy strumień, które są skojarzone z konsoli programu —`stdin`, `stdout`, i `stderr`— muszą być przekierowywane przed funkcje wykonawcze języka C można używać ich w [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] aplikacji. Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).  
  
## <a name="example"></a>Przykład  
  
```  
// crt_printf_p.c  
// This program uses the _printf_p and _wprintf_p  
// functions to choose the order in which parameters  
// are used.  
  
#include <stdio.h>  
  
int main( void )  
{  
   // Positional arguments   
   _printf_p( "Specifying the order: %2$s %3$s %1$s %4$s %5$s.\n",  
              "little", "I'm", "a", "tea", "pot");  
  
   // Resume arguments  
   _wprintf_p( L"Reusing arguments: %1$d %1$d %1$d %1$d\n", 10);  
  
   // Width argument  
   _printf_p("Width specifiers: %1$*2$s", "Hello\n", 10);  
}  
```  
  
```Output  
Specifying the order: I'm a little tea pot.  
Reusing arguments: 10 10 10 10  
Width specifiers:     Hello  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Obsługa liczb zmiennoprzecinkowych](../../c-runtime-library/floating-point-support.md)   
 [We/Wy strumienia](../../c-runtime-library/stream-i-o.md)   
 [Ustawienia regionalne](../../c-runtime-library/locale.md)   
 [fopen —, _wfopen —](../../c-runtime-library/reference/fopen-wfopen.md)   
 [_fprintf_p —, _fprintf_p_l —, _fwprintf_p — _fwprintf_p_l —](../../c-runtime-library/reference/fprintf-p-fprintf-p-l-fwprintf-p-fwprintf-p-l.md)   
 [fprintf —, _fprintf_l —, fwprintf — _fwprintf_l —](../../c-runtime-library/reference/fprintf-fprintf-l-fwprintf-fwprintf-l.md)   
 [fprintf_s —, _fprintf_s_l —, fwprintf_s — _fwprintf_s_l —](../../c-runtime-library/reference/fprintf-s-fprintf-s-l-fwprintf-s-fwprintf-s-l.md)   
 [scanf, _scanf_l —, wscanf — _wscanf_l —](../../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md)   
 [scanf_s —, _scanf_s_l —, wscanf_s — _wscanf_s_l —](../../c-runtime-library/reference/scanf-s-scanf-s-l-wscanf-s-wscanf-s-l.md)   
 [_sprintf_p —, _sprintf_p_l —, _swprintf_p — _swprintf_p_l —](../../c-runtime-library/reference/sprintf-p-sprintf-p-l-swprintf-p-swprintf-p-l.md)   
 [sprintf, _sprintf_l —, swprintf —, _swprintf_l —, \__swprintf_l —](../../c-runtime-library/reference/sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)   
 [sprintf_s —, _sprintf_s_l —, swprintf_s — _swprintf_s_l —](../../c-runtime-library/reference/sprintf-s-sprintf-s-l-swprintf-s-swprintf-s-l.md)   
 [vprintf, funkcje](../../c-runtime-library/vprintf-functions.md)