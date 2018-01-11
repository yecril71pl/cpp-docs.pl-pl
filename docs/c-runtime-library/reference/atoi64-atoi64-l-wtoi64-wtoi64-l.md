---
title: "_atoi64 —, _atoi64_l —, _wtoi64 —, _wtoi64_l — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _atoi64_l
- _wtoi64
- _atoi64
- _wtoi64_l
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
- api-ms-win-crt-convert-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _atoi64
- _tstoi64
- _ttoi64
- wtoi64
- _tstoi64_l
- atoi64
- _wtoi64_l
- _wtoi64
- wtoi64_l
- _atoi64_l
- atoi64_l
dev_langs: C++
helpviewer_keywords:
- tstoi64 function
- wtoi64 function
- atoi64_l function
- _ttoi64 function
- string conversion, to integers
- wtoi64_l function
- atoi64 function
- _tstoi64 function
- _atoi64_l function
- _wtoi64_l function
- ttoi64 function
- _wtoi64 function
- _atoi64 function
ms.assetid: 2c3e30fd-545d-4222-8364-0c5905df9526
caps.latest.revision: "24"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 33337f0db51e81da06c193cc42cac1e5df085218
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="atoi64-atoi64l-wtoi64-wtoi64l"></a>_atoi64, _atoi64_l, _wtoi64, _wtoi64_l
Konwertuje ciąg na 64-bitową liczbę całkowitą.  
  
## <a name="syntax"></a>Składnia  
  
```  
__int64 _atoi64(  
   const char *str   
);  
__int64 _wtoi64(  
   const wchar_t *str   
);  
__int64 _atoi64_l(  
   const char *str,  
   _locale_t locale  
);  
__int64 _wtoi64_l(  
   const wchar_t *str,  
   _locale_t locale  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `str`  
 Ciąg do przekonwertowania.  
  
 `locale`  
 Ustawienia regionalne do użycia.  
  
## <a name="return-value"></a>Wartość zwracana  
 Każda funkcja zwraca `__int64` wartość utworzonego przez interpretowanie znaków wejściowy jako liczby. Wartość zwracana jest 0 dla `_atoi64` Jeśli dane wejściowe nie można przekonwertować wartości tego typu.  
  
 W przypadku przepełnienia o dużych dodatnie wartości całkowite `_atoi64` zwraca `I64_MAX` i `I64_MIN` w przypadku przepełnienia o dużych wartościach całkowitych ujemnych.  
  
 We wszystkich przypadkach out-of-range `errno` ma ustawioną wartość `ERANGE`. Jeśli parametr przekazano `NULL`, program obsługi nieprawidłowych parametrów zostanie wywołany, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli dozwolone jest wykonywanie aby kontynuować, ustawianie tych funkcji `errno` do `EINVAL` i zwraca 0.  
  
## <a name="remarks"></a>Uwagi  
 Te funkcje przekonwertować ciągu znaków na wartość 64-bitową liczbę całkowitą.  
  
 Ciąg wejściowy jest sekwencji znaków, które mogą być interpretowane jako wartość liczbowa określonego typu. Funkcja zatrzymuje odczytywania ciąg wejściowy pierwszego znaku, który nie jest rozpoznawana jako część liczby. Ten znak może być znak null ('\0' lub L '\0') zakończenie ciągu.  
  
 `str` Argument `_atoi64` ma następujący format:  
  
```  
[whitespace] [sign] [digits]]  
```  
  
 A `whitespace` zawiera spację lub tabulator znaki, które są ignorowane. `sign` jest plus (+) lub minus (-); i `digits` są co najmniej jedną cyfrę.  
  
 `_wtoi64`jest taka sama jak `_atoi64` z tą różnicą, że trwa ciąg znaków typu wide jako parametr.  
  
 Wersje tych funkcji z `_l` sufiks są identyczne, z wyjątkiem tego, aby używały parametr ustawień regionalnych przekazano zamiast bieżących ustawień regionalnych. Aby uzyskać więcej informacji, zobacz [ustawień regionalnych](../../c-runtime-library/locale.md).  
  
### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu  
  
|Procedura tchar.h|_UNICODE i _MBCS niezdefiniowane|_MBCS zdefiniowano|_UNICODE zdefiniowano|  
|---------------------|--------------------------------------|--------------------|-----------------------|  
|`_tstoi64`|`_atoi64`|`_atoi64`|`_wtoi64`|  
|`_ttoi64`|`_atoi64`|`_atoi64`|`_wtoi64`|  
  
## <a name="requirements"></a>Wymagania  
  
|Procedury|Wymagany nagłówek|  
|--------------|---------------------|  
|`_atoi64`, `_atoi64_l`|\<stdlib.h >|  
|`_wtoi64`, `_wtoi64_l`|\<stdlib.h > lub \<wchar.h >|  
  
## <a name="example"></a>Przykład  
 Ten program pokazuje, jak liczby przechowywane jako ciąg można przekonwertować wartości liczbowych za pomocą `_atoi64` funkcji.  
  
```  
// crt_atoi64.c  
// This program shows how numbers stored as  
// strings can be converted to numeric values  
// using the _atoi64 functions.  
#include <stdlib.h>  
#include <stdio.h>  
#include <errno.h>  
  
int main( void )  
{  
    char    *str = NULL;  
    __int64 value = 0;  
  
    // An example of the _atoi64 function  
    // with leading and trailing white spaces.  
    str = "  -2309 ";  
    value = _atoi64( str );  
    printf( "Function: _atoi64( \"%s\" ) = %d\n", str, value );  
  
    // Another example of the _atoi64 function   
    // with an arbitrary decimal point.  
    str = "314127.64";  
    value = _atoi64( str );  
    printf( "Function: _atoi64( \"%s\" ) = %d\n", str, value );  
  
    // Another example of the _atoi64 function  
    // with an overflow condition occurring.  
    str = "3336402735171707160320";  
    value = _atoi64( str );  
    printf( "Function: _atoi64( \"%s\" ) = %d\n", str, value );  
    if (errno == ERANGE)  
    {  
       printf("Overflow condition occurred.\n");  
    }  
}  
```  
  
```Output  
Function: _atoi64( "  -2309 " ) = -2309  
Function: _atoi64( "314127.64" ) = 314127  
Function: _atoi64( "3336402735171707160320" ) = -1  
Overflow condition occurred.  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Konwersja danych](../../c-runtime-library/data-conversion.md)   
 [Obsługa liczb zmiennoprzecinkowych](../../c-runtime-library/floating-point-support.md)   
 [Ustawienia regionalne](../../c-runtime-library/locale.md)   
 [_ecvt —](../../c-runtime-library/reference/ecvt.md)   
 [_fcvt —](../../c-runtime-library/reference/fcvt.md)   
 [_gcvt —](../../c-runtime-library/reference/gcvt.md)   
 [setLocale, _wsetlocale —](../../c-runtime-library/reference/setlocale-wsetlocale.md)   
 [_atodbl, _atodbl_l, _atoldbl, _atoldbl_l, _atoflt, _atoflt_l](../../c-runtime-library/reference/atodbl-atodbl-l-atoldbl-atoldbl-l-atoflt-atoflt-l.md)