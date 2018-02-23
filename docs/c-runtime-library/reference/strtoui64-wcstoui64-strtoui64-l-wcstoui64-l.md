---
title: _strtoui64, _wcstoui64, _strtoui64_l, _wcstoui64_l | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- _strtoui64
- _strtoui64_l
- _wcstoui64
- _wcstoui64_l
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
- _wcstoui64_l
- strtoui64_l
- wcstoui64
- _wcstoui64
- _strtoui64_l
- strtoui64
- _strtoui64
- wcstoui64_l
dev_langs:
- C++
helpviewer_keywords:
- _strtoui64_l function
- _wcstoui64_l function
- string conversion, to integers
- wcstoui64_l function
- _strtoui64 function
- _wcstoui64 function
- wcstoui64 function
- strtoui64_l function
- strtoui64 function
ms.assetid: 7fcb537e-4554-4ceb-a5b6-bc09244e72ef
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 2ad6ce06ef428005ea07214b426df0c61f623429
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2018
---
# <a name="strtoui64-wcstoui64-strtoui64l-wcstoui64l"></a>_strtoui64, _wcstoui64, _strtoui64_l, _wcstoui64_l
Konwertowanie ciągu na typ unsigned `__int64` wartość.  
  
## <a name="syntax"></a>Składnia  
  
```  
unsigned __int64 _strtoui64(  
   const char *nptr,  
   char **endptr,  
   int base   
);  
unsigned __int64 _wcstoui64(  
   const wchar_t *nptr,  
   wchar_t **endptr,  
   int base   
);  
unsigned __int64 _strtoui64_l(  
   const char *nptr,  
   char **endptr,  
   int base,  
   _locale_t locale  
);  
unsigned __int64 _wcstoui64(  
   const wchar_t *nptr,  
   wchar_t **endptr,  
   int base,  
   _locale_t locale  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `nptr`  
 Zerem ciąg do konwersji.  
  
 `endptr`  
 Wskaźnik do znaku, który zatrzymuje skanowania.  
  
 `base`  
 Podstawowy numer do użycia.  
  
 `locale`  
 Ustawienia regionalne do użycia.  
  
## <a name="return-value"></a>Wartość zwracana  
 `_strtoui64` Zwraca wartość w ciągu `nptr`, z wyjątkiem gdy reprezentacja mogłoby spowodować przepełnienie, w takim przypadku go zwraca `_UI64_MAX`. `_strtoui64` Zwraca wartość 0, jeśli konwersja nie jest możliwe.  
  
 `_UI64_MAX` jest zdefiniowany w granicach. H.  
  
 Jeśli `nptr` jest `NULL` lub `base` jest różna od zera i mniejszym niż 2 lub większą niż 36 `errno` ma ustawioną wartość `EINVAL`.  
  
 Zobacz [_doserrno —, errno, _sys_errlist — i _sys_nerr —](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) kody powrotne — Aby uzyskać więcej informacji na temat tych i innych.  
  
## <a name="remarks"></a>Uwagi  
 `_strtoui64` Funkcji konwertuje `nptr` do `unsigned` `__int64`. `_wcstoui64` jest to wersja znaków dwubajtowych `_strtoui64`; `nptr` argument jest ciąg znaków dwubajtowych. W przeciwnym razie funkcje te działają tak samo.  
  
 Zatrzymaj funkcjami odczytywania ciąg `nptr` pierwszego znaku, ich nie jest rozpoznawana jako część liczby. Może to być znak końcowy null lub może być pierwszym znaku numerycznego większa niż lub równa `base`.  
  
### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu  
  
|Procedura TCHAR.H|_Unicode — & _MBCS nie zdefiniowany|_MBCS zdefiniowano|_UNICODE zdefiniowano|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_tcstoui64`|`_strtoui64`|`_strtoui64`|`_wstrtoui64`|  
|`_tcstoui64_l`|`_strtoui64_l`|`_strtoui64_l`|`_wstrtoui64_l`|  
  
 Bieżące ustawienia regionalne `LC_NUMERIC` ustawienie kategorii określa rozpoznawania po znaku radix `nptr`; Aby uzyskać więcej informacji, zobacz [setlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md). Funkcje sufiksu _l Użyj bieżących ustawień regionalnych; `_strtoui64_l` i `_wcstoui64_l` są takie same jak odpowiednie funkcje bez `_l` sufiks z wyjątkiem tego, aby używały przekazano zamiast ustawień regionalnych. Aby uzyskać więcej informacji, zobacz [ustawień regionalnych](../../c-runtime-library/locale.md).  
  
 Jeśli `endptr` nie jest `NULL`, wskaźnik do znaku zatrzymania skanowania są przechowywane w lokalizacji wskazywanej przez `endptr`. Jeśli konwersja nie można wykonać (nie znaleziono żadnych prawidłowych cyfr lub określono nieprawidłowy atrybut podstawowy), wartość `nptr` są przechowywane w lokalizacji wskazywanej przez `endptr`.  
  
 `_strtoui64` oczekuje `nptr` wskaż ciąg następującą postać:  
  
 [`whitespace`] [{`+` &#124; `-`}] [`0` [{ `x` &#124; `X` }]] [`digits`]  
  
 A `whitespace` może zawierać znaków miejsca i karty, które są ignorowane. `digits` są co najmniej jeden cyfr dziesiętnych. Pierwszy znak należący do tego formularza zatrzymuje skanowania. Jeśli `base` jest od 2 do 36, zostanie użyty jako podstawa liczby. Jeśli `base` ma wartość 0, znaków ciągu wskazywana przez `nptr` są używane do określenia podstawy. Jeśli pierwszym znakiem 0 i nie jest znak "x" lub "X", ciąg jest interpretowany jako ósemkową liczby całkowitej. Jeśli pierwszym znakiem jest "0" i jest znak "x" lub "X", ciąg jest interpretowany jako szesnastkową liczby całkowitej. Jeśli pierwszym znakiem jest "1" do "9", ciąg jest interpretowany jako dziesiętną liczbą całkowitą. Litery "" do "z" (lub "" do "Z") mają przypisane wartości 10 do 35; tylko litery, w których przypisane wartości są mniej niż `base` są dozwolone. Pierwszy znak poza zakresem podstawy zatrzymuje skanowania. Na przykład jeśli `base` wynosi 0 i pierwszy znak skanowane to "0", zakłada, że całkowitą ósemkowe i się od znaku "8" lub "9" spowoduje zatrzymanie skanowania.  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`_strtoui64`|\<stdlib.h>|  
|`_wcstoui64`|\<stdlib.h > lub \<wchar.h >|  
|`_strtoui64_l`|\<stdlib.h>|  
|`_wcstoui64_l`|\<stdlib.h > lub \<wchar.h >|  
  
 Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md) we wprowadzeniu.  
  
## <a name="example"></a>Przykład  
  
```  
// crt_strtoui64.c  
#include <stdio.h>  
  
unsigned __int64 atoui64(const char *szUnsignedInt) {  
   return _strtoui64(szUnsignedInt, NULL, 10);  
}  
  
int main() {  
   unsigned __int64 u = atoui64("18446744073709551615");  
   printf( "u = %I64u\n", u );  
}  
```  
  
```Output  
u = 18446744073709551615  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Konwersja danych](../../c-runtime-library/data-conversion.md)   
 [Ustawienia regionalne](../../c-runtime-library/locale.md)   
 [localeconv](../../c-runtime-library/reference/localeconv.md)   
 [setLocale, _wsetlocale —](../../c-runtime-library/reference/setlocale-wsetlocale.md)   
 [Ciąg na wartość liczbową funkcje](../../c-runtime-library/string-to-numeric-value-functions.md)   
 [strtod —, _strtod_l —, wcstod — _wcstod_l —](../../c-runtime-library/reference/strtod-strtod-l-wcstod-wcstod-l.md)   
 [strtoul —, _strtoul_l —, wcstoul — _wcstoul_l —](../../c-runtime-library/reference/strtoul-strtoul-l-wcstoul-wcstoul-l.md)   
 [atof, _atof_l, _wtof, _wtof_l](../../c-runtime-library/reference/atof-atof-l-wtof-wtof-l.md)