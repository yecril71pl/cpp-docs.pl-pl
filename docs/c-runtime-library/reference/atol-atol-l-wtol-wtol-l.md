---
title: "Atol —, _atol_l —, _wtol —, _wtol_l — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- atol
- _wtol_l
- _wtol
- _atol_l
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
- _atol_l
- _ttol_l
- _tstol_l
- _tstol
- _wtol
- _ttol
- _wtol_l
dev_langs: C++
helpviewer_keywords:
- tstol function
- atol function
- ttol function
- _atol_l function
- _tstol_l function
- string conversion, to integers
- _tstol function
- _ttol function
- _ttol_l function
- atol_l function
- wtol_l function
- _wtol_l function
- wtol function
- _wtol function
ms.assetid: cedfc21c-2d64-4e9c-bd04-bdf60b12db46
caps.latest.revision: "22"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 4ef61564dcecabf25c0945f9774de8bc48de1447
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="atol-atoll-wtol-wtoll"></a>atol, _atol_l, _wtol, _wtol_l
Konwertowanie ciągu na liczbę całkowitą typu long.  
  
## <a name="syntax"></a>Składnia  
  
```  
long atol(  
   const char *str   
);  
long _atol_l(  
   const char *str,  
   _locale_t locale  
);  
long _wtol(  
   const wchar_t *str   
);  
long _wtol_l(  
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
 Każda funkcja zwraca `long` wartość utworzonego przez interpretowanie znaków wejściowy jako liczby. Wartość zwracana jest 0L- `atol` Jeśli dane wejściowe nie można przekonwertować wartości tego typu.  
  
 W przypadku przepełnienia o dużych dodatnie wartości całkowite `atol` zwraca `LONG_MAX`; w przypadku przepełnienia o dużych wartościach całkowitych ujemnych, `LONG_MIN` jest zwracany. We wszystkich przypadkach out-of-range `errno` ma ustawioną wartość `ERANGE`. Jeśli parametr przekazano `NULL`, program obsługi nieprawidłowych parametrów zostanie wywołany, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli dozwolone jest wykonywanie aby kontynuować, ustawianie tych funkcji `errno` do `EINVAL` i zwraca 0.  
  
## <a name="remarks"></a>Uwagi  
 Te funkcje przekonwertować ciągu znaków na wartość długich liczb całkowitych (`atol`).  
  
 Ciąg wejściowy jest sekwencji znaków, które mogą być interpretowane jako wartość liczbowa określonego typu. Funkcja zatrzymuje odczytywania ciąg wejściowy pierwszego znaku, który nie jest rozpoznawana jako część liczby. Ten znak może być `NULL` znak ('\0' lub L '\0') zakończenie ciągu.  
  
 `str` Argument `atol` ma następujący format:  
  
 [`whitespace`] [`sign`] [`digits`]]  
  
 A `whitespace` zawiera spację lub tabulator znaki, które są ignorowane. `sign` jest plus (+) lub minus (-); i `digits` są co najmniej jedną cyfrę.  
  
 `_wtol`jest taka sama jak `atol` z tą różnicą, że trwa ciąg znaków typu wide.  
  
 Wersje tych funkcji z `_l` sufiks są identyczne, z wyjątkiem tego, aby używały parametr ustawień regionalnych przekazano zamiast bieżących ustawień regionalnych. Aby uzyskać więcej informacji, zobacz [ustawień regionalnych](../../c-runtime-library/locale.md).  
  
### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu  
  
|Procedura TCHAR.H|_Unicode — & _MBCS nie zdefiniowany|_MBCS zdefiniowano|_UNICODE zdefiniowano|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_tstol`|`atol`|`atol`|`_wtol`|  
|`_ttol`|`atol`|`atol`|`_wtol`|  
  
## <a name="requirements"></a>Wymagania  
  
|Procedury|Wymagany nagłówek|  
|--------------|---------------------|  
|`atol`|\<stdlib.h >|  
|`_atol_l`, `_wtol`, `_wtol_l`|\<stdlib.h > i \<wchar.h >|  
  
## <a name="example"></a>Przykład  
 Ten program pokazuje, jak liczby przechowywane jako ciąg można przekonwertować wartości liczbowych za pomocą `atol` funkcji.  
  
```  
// crt_atol.c  
// This program shows how numbers stored as  
// strings can be converted to numeric values  
// using the atol functions.  
#include <stdlib.h>  
#include <stdio.h>  
#include <errno.h>  
  
int main( void )  
{  
    char    *str = NULL;  
    long    value = 0;  
  
    // An example of the atol function  
    // with leading and trailing white spaces.  
    str = "  -2309 ";  
    value = atol( str );  
    printf( "Function: atol( \"%s\" ) = %d\n", str, value );  
  
    // Another example of the atol function   
    // with an arbitrary decimal point.  
    str = "314127.64";  
    value = atol( str );  
    printf( "Function: atol( \"%s\" ) = %d\n", str, value );  
  
    // Another example of the atol function  
    // with an overflow condition occurring.  
    str = "3336402735171707160320";  
    value = atol( str );  
    printf( "Function: atol( \"%s\" ) = %d\n", str, value );  
    if (errno == ERANGE)  
    {  
       printf("Overflow condition occurred.\n");  
    }  
}  
```  
  
```Output  
Function: atol( "  -2309 " ) = -2309  
Function: atol( "314127.64" ) = 314127  
Function: atol( "3336402735171707160320" ) = 2147483647  
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
 [_atodbl —, _atodbl_l —, _atoldbl —, _atoldbl_l — _atoflt —, _atoflt_l —](../../c-runtime-library/reference/atodbl-atodbl-l-atoldbl-atoldbl-l-atoflt-atoflt-l.md)