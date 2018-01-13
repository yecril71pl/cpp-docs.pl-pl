---
title: "_vfprintf_p —, _vfprintf_p_l —, _vfwprintf_p —, _vfwprintf_p_l — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _vfprintf_p
- _vfwprintf_p
- _vfprintf_p_l
- _vfwprintf_p_l
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
- _vfwprintf_p_l
- _vfprintf_p
- vfwprintf_p_l
- vfwprintf_p
- vfprintf_p_l
- _vfwprintf_p
- _vftprintf_p
- _vfprintf_p_l
- vfprintf_p
dev_langs: C++
helpviewer_keywords:
- vfprintf_p_l function
- _vftprintf_p_l function
- _vfprintf_p function
- vfprintf_p function
- vftprintf_p_l function
- _vfprintf_p_l function
- _vftprintf_p function
- _vfwprintf_p_l function
- vfwprintf_p_l function
- _vfwprintf_p function
- vftprintf_p function
- formatted text [C++]
- vfwprintf_p function
ms.assetid: 4d4a0914-4175-4b65-9ca1-037c4ef29147
caps.latest.revision: "15"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 49684bcb7f1022bad7a0f3dad3a0ec5692373996
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="vfprintfp-vfprintfpl-vfwprintfp-vfwprintfpl"></a>_vfprintf_p, _vfprintf_p_l, _vfwprintf_p, _vfwprintf_p_l
Zapis sformatowane wyniki za pomocą wskaźnika do listy argumentów, z możliwością określić kolejność, że argumenty są używane w ciągu formatu.  
  
## <a name="syntax"></a>Składnia  
  
```  
int _vfprintf_p(  
   FILE *stream,  
   const char *format,  
   va_list argptr   
);  
int _vfprintf_p_l(  
   FILE *stream,  
   const char *format,  
   locale_t locale,  
   va_list argptr   
);  
int _vfwprintf_p(  
   FILE *stream,  
   const wchar_t *format,  
   va_list argptr   
);  
int _vfwprintf_p_l(  
   FILE *stream,  
   const wchar_t *format,  
   locale_t locale,  
   va_list argptr   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `stream`  
 Wskaźnik do `FILE` struktury.  
  
 `format`  
 Definicja formatu.  
  
 `argptr`  
 Wskaźnik do listy argumentów.  
  
 `locale`  
 Ustawienia regionalne do użycia.  
  
 Aby uzyskać więcej informacji, zobacz [specyfikacje formatu](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md).  
  
## <a name="return-value"></a>Wartość zwracana  
 `_vfprintf_p`i `_vfwprintf_p` zwraca liczbę znaków zapisane, nie włączając znak końcowy null lub wartość ujemną, jeśli wystąpi błąd wyjścia.  
  
## <a name="remarks"></a>Uwagi  
 Każda z tych funkcji przyjmuje wskaźnik do listy argumentów, a następnie formatuje i zapisuje określone dane do `stream`. Funkcje te różnią się od `_vfprint_s` i `_vfwprint_s` wersji tylko w tym obsługują parametrów pozycyjnych. Aby uzyskać więcej informacji, zobacz [printf_p parametry pozycyjne](../../c-runtime-library/printf-p-positional-parameters.md).  
  
 `_vfwprintf_p`jest to wersja znaków dwubajtowych `_vprintf_p`; dwie funkcje zachowują się tak samo, jakby strumień jest otwarty w trybie ANSI. `_vprintf_p`obecnie nie obsługuje dane wyjściowe do strumienia UNICODE.  
  
 Wersje tych funkcji z `_l` sufiks są identyczne, z wyjątkiem tego, aby używały parametr ustawień regionalnych przekazano zamiast bieżącego ustawienia regionalne wątku.  
  
> [!IMPORTANT]
>  Upewnij się, że `format` nie jest ciągiem zdefiniowane przez użytkownika. Aby uzyskać więcej informacji, zobacz [unikanie Overruns buforu](http://msdn.microsoft.com/library/windows/desktop/ms717795).  
  
 Jeśli dowolny `stream` lub `format` jest wskaźnika o wartości null, lub jeśli ciąg formatu zawiera nieprawidłowe znaki formatowania, program obsługi nieprawidłowych parametrów zostanie wywołany, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Zwróć -1, jeśli może kontynuować wykonywania, funkcje i ustaw `errno` do `EINVAL`.  
  
### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu  
  
|Procedura TCHAR.H|_Unicode — & _MBCS nie zdefiniowany|_MBCS zdefiniowano|_UNICODE zdefiniowano|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_vftprintf_p`|`_vfprintf_p`|`_vfprintf_p`|`_vfwprintf_p`|  
|`_vftprintf_p_l`|`_vfprintf_p_l`|`_vfprintf_p_l`|`_vfwprintf_p_l`|  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|Opcjonalne nagłówki|  
|-------------|---------------------|----------------------|  
|`_vfprintf_p`, `_vfprintf_p_l`|\<stdio.h > i \<stdarg.h >|\<VarArgs.h > *|  
|`_vfwprintf_p`, `_vfwprintf_p_l`|\<stdio.h > lub \<wchar.h >, a \<stdarg.h >|\<VarArgs.h > *|  
  
 \*Wymagany w przypadku zgodności UNIX V.  
  
 Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md) we wprowadzeniu.  
  
## <a name="see-also"></a>Zobacz też  
 [We/Wy strumienia](../../c-runtime-library/stream-i-o.md)   
 [vprintf — funkcje](../../c-runtime-library/vprintf-functions.md)   
 [fprintf —, _fprintf_l —, fwprintf — _fwprintf_l —](../../c-runtime-library/reference/fprintf-fprintf-l-fwprintf-fwprintf-l.md)   
 [printf, _printf_l —, wprintf, _wprintf_l —](../../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)   
 [sprintf, _sprintf_l —, swprintf —, _swprintf_l —, \__swprintf_l —](../../c-runtime-library/reference/sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)   
 [va_arg, va_copy, va_end, makra va_start](../../c-runtime-library/reference/va-arg-va-copy-va-end-va-start.md)   
 [printf_p parametry pozycyjne](../../c-runtime-library/printf-p-positional-parameters.md)   
 [_fprintf_p —, _fprintf_p_l —, _fwprintf_p — _fwprintf_p_l —](../../c-runtime-library/reference/fprintf-p-fprintf-p-l-fwprintf-p-fwprintf-p-l.md)   
 [_vsprintf_p —, _vsprintf_p_l —, _vswprintf_p — _vswprintf_p_l —](../../c-runtime-library/reference/vsprintf-p-vsprintf-p-l-vswprintf-p-vswprintf-p-l.md)   
 [_sprintf_p, _sprintf_p_l, _swprintf_p, _swprintf_p_l](../../c-runtime-library/reference/sprintf-p-sprintf-p-l-swprintf-p-swprintf-p-l.md)