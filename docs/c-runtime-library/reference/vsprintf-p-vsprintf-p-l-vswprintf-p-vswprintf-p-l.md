---
title: "_vsprintf_p —, _vsprintf_p_l —, _vswprintf_p —, _vswprintf_p_l — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _vsprintf_p
- _vswprintf_p
- _vsprintf_p_l
- _vswprintf_p_l
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
- vsprintf_p
- _vswprintf_p
- _vstprintf_p
- vswprintf_p
- _vsprintf_p
- vstprintf_p
dev_langs: C++
helpviewer_keywords:
- vstprintf_p_l function
- _vsprintf_p_l function
- _vstprintf_p function
- vsprintf_p_l function
- _vswprintf_p function
- vswprintf_p function
- vsprintf_p function
- vswprintf_p_l function
- _vswprintf_p_l function
- vstprintf_p function
- formatted text [C++]
- _vsprintf_p function
- _vstprintf_p_l function
ms.assetid: 00821c0d-9fee-4d8a-836c-0669cfb11317
caps.latest.revision: "20"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 1d64200b38fb206426b037c0c12d008739e0509b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="vsprintfp-vsprintfpl-vswprintfp-vswprintfpl"></a>_vsprintf_p, _vsprintf_p_l, _vswprintf_p, _vswprintf_p_l
Zapis sformatowane wyniki za pomocą wskaźnika do listy argumentów, z możliwością określić kolejność, w którym są używane argumentów.  
  
## <a name="syntax"></a>Składnia  
  
```  
int _vsprintf_p(  
   char *buffer,  
   size_t sizeInBytes,  
   const char *format,  
   va_list argptr   
);   
int _vsprintf_p_l(  
   char *buffer,  
   size_t sizeInBytes,  
   const char *format,  
   locale_t locale,  
   va_list argptr   
);   
int _vswprintf_p(  
   wchar_t *buffer,  
   size_t count,  
   const wchar_t *format,  
   va_list argptr   
);  
int _vswprintf_p_l(  
   wchar_t *buffer,  
   size_t count,  
   const wchar_t *format,  
   locale_t locale,  
   va_list argptr   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `buffer`  
 Lokalizacja magazynu dla danych wyjściowych.  
  
 `sizeInBytes`  
 Rozmiar `buffer` w znakach.  
  
 `count`  
 Maksymalna liczba znaków do przechowywania w wersji UNICODE tej funkcji.  
  
 `format`  
 Definicja formatu.  
  
 `argptr`  
 Wskaźnik do listy argumentów.  
  
 `locale`  
 Ustawienia regionalne do użycia.  
  
## <a name="return-value"></a>Wartość zwracana  
 `_vsprintf_p`i `_vswprintf_p` zwraca liczbę znaków zapisane, nie włączając znak końcowy null lub wartość ujemną, jeśli wystąpi błąd wyjścia.  
  
## <a name="remarks"></a>Uwagi  
 Każda z tych funkcji przyjmuje wskaźnik do listy argumentów i sformatowanie i zapisuje podane dane pamięci wskazywanej przez `buffer`.  
  
 Funkcje te różnią się od `vsprintf_s` i `vswprintf_s` tylko w tym obsługują parametrów pozycyjnych. Aby uzyskać więcej informacji, zobacz [printf_p parametry pozycyjne](../../c-runtime-library/printf-p-positional-parameters.md).  
  
 Wersje tych funkcji z `_l` sufiks są identyczne, z wyjątkiem tego, aby używały parametr ustawień regionalnych przekazano zamiast bieżącego ustawienia regionalne wątku.  
  
 Jeśli `buffer` lub `format` parametry są wskaźników NULL, jeśli liczba jest równa zero, lub jeśli ciąg formatu zawiera nieprawidłowe znaki formatowania, zostanie wywołany program obsługi nieprawidłowych parametrów, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Zwróć -1, jeśli może kontynuować wykonywania, funkcje i ustaw `errno` do `EINVAL`.  
  
### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu  
  
|Procedura TCHAR.H|_Unicode — & _MBCS nie zdefiniowany|_MBCS zdefiniowano|_UNICODE zdefiniowano|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_vstprintf_p`|`_vsprintf_p`|`_vsprintf_p`|`_vswprintf_p`|  
|`_vstprintf_p_l`|`_vsprintf_p_l`|`_vsprintf_p_l`|`_vswprintf_p_l`|  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|Opcjonalne nagłówki|  
|-------------|---------------------|----------------------|  
|`_vsprintf_p`, `_vsprintf_p_l`|\<stdio.h > i \<stdarg.h >|\<VarArgs.h > *|  
|`_vswprintf_p`, `_vswprintf_p_l`|\<stdio.h > lub \<wchar.h >, a \<stdarg.h >|\<VarArgs.h > *|  
  
 \*Wymagany w przypadku zgodności UNIX V.  
  
 Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md) we wprowadzeniu.  
  
## <a name="example"></a>Przykład  
  
```  
// crt__vsprintf_p.c  
// This program uses vsprintf_p to write to a buffer.  
// The size of the buffer is determined by _vscprintf_p.  
  
#include <stdlib.h>  
#include <stdio.h>  
#include <stdarg.h>  
  
void example( char * format, ... )  
{  
    va_list  args;  
    int      len;  
    char     *buffer = NULL;  
  
    va_start( args, format );  
  
    // _vscprintf doesn't count the   
    // null terminating string so we add 1.  
    len = _vscprintf_p( format, args ) + 1;  
  
    // Allocate memory for our buffer  
    buffer = (char*)malloc( len * sizeof(char) );  
    if (buffer)  
    {  
        _vsprintf_p( buffer, len, format, args );  
        puts( buffer );  
        free( buffer );  
    }  
    va_end( args );
}  
  
int main( void )  
{  
    // First example  
    example( "%2$d %1$c %3$d", '<', 123, 456 );  
  
    // Second example  
    example( "%s", "This is a string" );  
}  
```  
  
```Output  
123 < 456  
This is a string  
```  
  
## <a name="see-also"></a>Zobacz też  
 [We/Wy strumienia](../../c-runtime-library/stream-i-o.md)   
 [vprintf — funkcje](../../c-runtime-library/vprintf-functions.md)   
 [Składnia specyfikacji formatu: funkcje printf i wprintf](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)   
 [fprintf —, _fprintf_l —, fwprintf — _fwprintf_l —](../../c-runtime-library/reference/fprintf-fprintf-l-fwprintf-fwprintf-l.md)   
 [printf, _printf_l —, wprintf, _wprintf_l —](../../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)   
 [sprintf, _sprintf_l —, swprintf —, _swprintf_l —, \__swprintf_l —](../../c-runtime-library/reference/sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)   
 [va_arg, va_copy, va_end, va_start](../../c-runtime-library/reference/va-arg-va-copy-va-end-va-start.md)