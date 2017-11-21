---
title: "_vprintf_p —, _vprintf_p_l —, _vwprintf_p —, _vwprintf_p_l — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _vwprintf_p
- _vprintf_p
- _vprintf_p_l
- _vwprintf_p_l
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
- _vwprintf_p_l
- vprintf_p
- _vprintf_p_l
- _vwprintf_p
- vprintf_p_l
- vwprintf_p_l
- vwprintf_p
- vtprintf_p
- _vtprintf_p
- _vprintf_p
dev_langs: C++
helpviewer_keywords:
- _vtprintf_p_l function
- _vtprintf_p function
- vtprintf_p function
- _vwprintf_p function
- _vwprintf_p_l function
- _vprintf_p function
- _vprintf_p_l function
- vprintf_p_l function
- vwprintf_p function
- vprintf_p function
- vtprintf_p_l function
- vwprintf_p_l function
- formatted text [C++]
ms.assetid: 3f99bde3-c891-493d-908f-30559c421058
caps.latest.revision: "17"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: e9695992fca625bc9b39f8d25074764af031da73
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="vprintfp-vprintfpl-vwprintfp-vwprintfpl"></a>_vprintf_p, _vprintf_p_l, _vwprintf_p, _vwprintf_p_l
Zapisuje dane wyjściowe sformatowany za pomocą wskaźnika do listy argumentów i umożliwia określenie kolejności, w którym są używane argumenty.  
  
## <a name="syntax"></a>Składnia  
  
```  
int _vprintf_p(  
   const char *format,  
   va_list argptr   
);  
int _vprintf_p_l(  
   const char *format,  
   locale_t locale,  
   va_list argptr   
);  
int _vwprintf_p(  
   const wchar_t *format,  
   va_list argptr   
);  
int _vwprintf_p_l(  
   const wchar_t *format,  
   locale_t locale,  
   va_list argptr   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `format`  
 Definicja formatu.  
  
 `argptr`  
 Wskaźnik do listy argumentów.  
  
 `locale`  
 Ustawienia regionalne do użycia.  
  
 Aby uzyskać więcej informacji, zobacz [specyfikacje formatu](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md).  
  
## <a name="return-value"></a>Wartość zwracana  
 `_vprintf_p`i `_vwprintf_p` zwraca liczbę znaków zapisane, nie włączając znak końcowy null lub wartość ujemną, jeśli wystąpi błąd wyjścia.  
  
## <a name="remarks"></a>Uwagi  
 Każda z tych funkcji przyjmuje wskaźnik do listy argumentów, a następnie formatuje i zapisuje określone dane do `stdout`. Funkcje te różnią się od `vprintf_s` i `vwprintf_s` tylko w tym obsługują umożliwia określenie kolejności, w którym są używane argumentów. Aby uzyskać więcej informacji, zobacz [printf_p parametry pozycyjne](../../c-runtime-library/printf-p-positional-parameters.md).  
  
 `_vwprintf_p`jest to wersja znaków dwubajtowych `_vprintf_p`; dwie funkcje zachowują się tak samo, jakby strumień jest otwarty w trybie ANSI. `_vprintf_p`obecnie nie obsługuje dane wyjściowe do strumienia UNICODE.  
  
 Wersje tych funkcji z `_l` sufiks są identyczne, z wyjątkiem tego, aby używały parametr ustawień regionalnych przekazano zamiast bieżącego ustawienia regionalne wątku.  
  
> [!IMPORTANT]
>  Upewnij się, że `format` nie jest ciągiem zdefiniowane przez użytkownika. Aby uzyskać więcej informacji, zobacz [unikanie Overruns buforu](http://msdn.microsoft.com/library/windows/desktop/ms717795).  
  
 Jeśli `format` jest wskaźnika o wartości null, lub jeśli ciąg formatu zawiera nieprawidłowe znaki formatowania, program obsługi nieprawidłowych parametrów zostanie wywołany, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Zwróć -1, jeśli może kontynuować wykonywania, funkcje i ustaw `errno` do `EINVAL`.  
  
### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu  
  
|Procedura TCHAR.H|_Unicode — & _MBCS nie zdefiniowany|_MBCS zdefiniowano|_UNICODE zdefiniowano|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_vtprintf_p`|`_vprintf_p`|`_vprintf_p`|`_vwprintf_p`|  
|`_vtprintf_p_l`|`_vprintf_p_l`|`_vprintf_p_l`|`_vwprintf_p_l`|  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|Opcjonalne nagłówki|  
|-------------|---------------------|----------------------|  
|`_vprintf_p`, `_vprintf_p_l`|\<stdio.h > i \<stdarg.h >|\<VarArgs.h > *|  
|`_vwprintf_p`, `_vwprintf_p_l`|\<stdio.h > lub \<wchar.h >, a \<stdarg.h >|\<VarArgs.h > *|  
  
 \*Wymagany w przypadku zgodności UNIX V.  
  
 Konsola nie jest obsługiwana w [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] aplikacji. Uchwyty Standardowy strumień, które są skojarzone z konsoli programu —`stdin`, `stdout`, i `stderr`— muszą być przekierowywane przed funkcje wykonawcze języka C można używać ich w [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] aplikacji. Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).  
  
## <a name="see-also"></a>Zobacz też  
 [We/Wy strumienia](../../c-runtime-library/stream-i-o.md)   
 [vprintf — funkcje](../../c-runtime-library/vprintf-functions.md)   
 [_fprintf_p —, _fprintf_p_l —, _fwprintf_p — _fwprintf_p_l —](../../c-runtime-library/reference/fprintf-p-fprintf-p-l-fwprintf-p-fwprintf-p-l.md)   
 [_printf_p —, _printf_p_l —, _wprintf_p — _wprintf_p_l —](../../c-runtime-library/reference/printf-p-printf-p-l-wprintf-p-wprintf-p-l.md)   
 [_sprintf_p —, _sprintf_p_l —, _swprintf_p — _swprintf_p_l —](../../c-runtime-library/reference/sprintf-p-sprintf-p-l-swprintf-p-swprintf-p-l.md)   
 [vsprintf_s —, _vsprintf_s_l —, vswprintf_s — _vswprintf_s_l —](../../c-runtime-library/reference/vsprintf-s-vsprintf-s-l-vswprintf-s-vswprintf-s-l.md)   
 [va_arg, va_copy, va_end, makra va_start](../../c-runtime-library/reference/va-arg-va-copy-va-end-va-start.md)   
 [_vfprintf_p —, _vfprintf_p_l —, _vfwprintf_p — _vfwprintf_p_l —](../../c-runtime-library/reference/vfprintf-p-vfprintf-p-l-vfwprintf-p-vfwprintf-p-l.md)   
 [_printf_p —, _printf_p_l —, _wprintf_p — _wprintf_p_l —](../../c-runtime-library/reference/printf-p-printf-p-l-wprintf-p-wprintf-p-l.md)   
 [printf_p parametry pozycyjne](../../c-runtime-library/printf-p-positional-parameters.md)