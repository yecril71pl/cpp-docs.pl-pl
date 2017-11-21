---
title: "atof —, _atof_l —, _wtof —, _wtof_l — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _wtof_l
- atof
- _atof_l
- _wtof
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
- _tstof
- _ttof
- atof
- stdlib/atof
- math/atof
- _atof_l
- stdlib/_atof_l
- math/_atof_l
- _wtof
- corecrt_wstdlib/_wtof
- _wtof_l
- corecrt_wstdlib/_wtof_l
dev_langs: C++
helpviewer_keywords:
- tstof function
- atof_l function
- _atof_l function
- atof function
- _tstof function
- _ttof function
- wtof function
- _wtof_l function
- ttof function
- wtof_l function
- _wtof function
- string conversion, to floating point values
ms.assetid: eb513241-c9a9-4f5c-b7e7-a49b14abfb75
caps.latest.revision: "26"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 72c6538cea2b1eaca61615a8b2db9041aa1eb74b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="atof-atofl-wtof-wtofl"></a>atof, _atof_l, _wtof, _wtof_l
Konwertowanie ciągu na dwa razy.  
  
## <a name="syntax"></a>Składnia  
  
```  
double atof(  
   const char *str   
);  
double _atof_l(  
   const char *str,  
   _locale_t locale  
);  
double _wtof(  
   const wchar_t *str   
);  
double _wtof_l(  
   const wchar_t *str,  
   _locale_t locale  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `str`  
 Ciąg do przekonwertowania.  
  
 `locale`  
 Ustawienia regionalne do użycia.  
  
## <a name="return-value"></a>Wartość zwracana  
 Każda funkcja zwraca `double` wartość utworzonego przez interpretowanie znaków wejściowy jako liczby. Wartość zwracana jest 0.0, jeśli dane wejściowe nie można przekonwertować wartości tego typu.  
  
 We wszystkich przypadkach out-of-range ustawiono errno `ERANGE`. Jeśli parametr przekazano `NULL`, program obsługi nieprawidłowych parametrów zostanie wywołany, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli dozwolone jest wykonywanie aby kontynuować, ustawianie tych funkcji `errno` do `EINVAL` i zwraca 0.  
  
## <a name="remarks"></a>Uwagi  
 Te funkcje przekonwertować ciągu znaków na wartość podwójnej precyzji, zmiennoprzecinkowych.  
  
 Ciąg wejściowy jest sekwencji znaków, które mogą być interpretowane jako wartość liczbowa określonego typu. Funkcja zatrzymuje odczytywania ciąg wejściowy pierwszego znaku, który nie jest rozpoznawana jako część liczby. Ten znak może być znak null ('\0' lub L '\0') zakończenie ciągu.  
  
 `str` Argument `atof` i `_wtof` ma następujący format:  
  
 [`whitespace`] [`sign`] [`digits`] [`.digits`] [ {`e` &#124; `E` }[`sign`]`digits`]  
  
 A `whitespace` zawiera spację lub tabulator znaki, które są ignorowane. `sign` jest plus (+) lub minus (-); i `digits` są co najmniej jeden cyfr dziesiętnych. Jeśli cyfr nie pojawia się przed separatorem dziesiętnym, co najmniej jeden musi występować po punkcie dziesiętnym. Cyfr dziesiętnych może następować wykładnik, obejmującego wprowadzające litery (`e`, lub `E`) i opcjonalnie podpisem dziesiętną liczbą całkowitą.  
 
 Biblioteka UCRT wersje tych funkcji nie obsługują konwersji Fortran stylu (`d` lub `D`) wykładnika litery. To rozszerzenie niestandardowe była obsługiwana przez wcześniejsze wersje CRT i może być istotne zmiany kodu.  
  
 Wersje tych funkcji z `_l` sufiks są identyczne, z wyjątkiem tego, aby używały parametr ustawień regionalnych przekazano zamiast bieżących ustawień regionalnych.  
  
### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu  
  
|Procedura TCHAR.H|_Unicode — & _MBCS nie zdefiniowany|_MBCS zdefiniowano|_UNICODE zdefiniowano|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_tstof`|`atof`|`atof`|`_wtof`|  
|`_ttof`|`atof`|`atof`|`_wtof`|  
  
## <a name="requirements"></a>Wymagania  
  
|Routine(s)|Wymagany nagłówek|  
|------------------|---------------------|  
|`atof`, `_atof_l`|C: \<math.h > lub \<stdlib.h > C++: \<cstdlib — >, \<stdlib.h >, \<cmath > lub \<math.h >|  
|`_wtof`, `_wtof_l`|C: \<stdlib.h > lub \<wchar.h > C++: \<cstdlib — >, \<stdlib.h > lub \<wchar.h >|  
  
## <a name="example"></a>Przykład  
 Ten program pokazuje, jak liczby przechowywane jako ciąg można przekonwertować wartości liczbowych za pomocą `atof` i `_atof_l` funkcji.  
  
```C  
// crt_atof.c  
//  
// This program shows how numbers stored as   
// strings can be converted to numeric  
// values using the atof and _atof_l functions.  

#include <stdlib.h>  
#include <stdio.h>  
#include <locale.h>  

int main(void)
{
    char    *str = NULL;
    double value = 0;
    _locale_t fr = _create_locale(LC_NUMERIC, "fr-FR");

    // An example of the atof function  
    // using leading and training spaces.  
    str = "  3336402735171707160320 ";
    value = atof(str);
    printf("Function: atof(\"%s\") = %e\n", str, value);

    // Another example of the atof function  
    // using the 'E' exponential formatting keyword.  
    str = "3.1412764583E210";
    value = atof(str);
    printf("Function: atof(\"%s\") = %e\n", str, value);

    // An example of the atof and _atof_l functions  
    // using the 'e' exponential formatting keyword  
    // and showing different decimal point interpretations.  
    str = "  -2,309e-25";
    value = atof(str);
    printf("Function: atof(\"%s\") = %e\n", str, value);
    value = _atof_l(str, fr);
    printf("Function: _atof_l(\"%s\", fr)) = %e\n", str, value);
}  
```  
  
```Output  
Function: atof("  3336402735171707160320 ") = 3.336403e+21
Function: atof("3.1412764583E210") = 3.141276e+210
Function: atof("  -2,309e-25") = -2.000000e+00
Function: _atof_l("  -2,309e-25", fr)) = -2.309000e-25  
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