---
title: "strtoul —, _strtoul_l —, wcstoul —, _wcstoul_l — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _wcstoul_l
- _strtoul_l
- strtoul
- wcstoul
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
- strtoul
- _tcstoul
- wcstoul
dev_langs: C++
helpviewer_keywords:
- _wcstoul_l function
- _tcstoul function
- _strtoul_l function
- string conversion, to integers
- wcstoul function
- strtoul function
- wcstoul_l function
- strtoul_l function
- tcstoul function
ms.assetid: 38f2afe8-8178-4e0b-8bbe-d5c6ad66e3ab
caps.latest.revision: "21"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 32bc9c63ec148d8e5c39d2aa6a38da974bfc6d96
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="strtoul-strtoull-wcstoul-wcstoull"></a>strtoul, _strtoul_l, wcstoul, _wcstoul_l
Konwertowanie ciągów na wartość long całkowitą bez znaku.  
  
## <a name="syntax"></a>Składnia  
  
```  
unsigned long strtoul(  
   const char *nptr,  
   char **endptr,  
   int base   
);  
unsigned long _strtoul_l(  
   const char *nptr,  
   char **endptr,  
   int base,  
   _locale_t locale  
);  
unsigned long wcstoul(  
   const wchar_t *nptr,  
   wchar_t **endptr,  
   int base   
);  
unsigned long _wcstoul_l(  
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
 `strtoul`Zwraca wartość przekonwertowana, lub `ULONG_MAX` na przepełnienia. `strtoul`Zwraca wartość 0, jeśli konwersja nie jest możliwe. `wcstoul`Zwraca wartości analogously do `strtoul`. Dla obu tych funkcji `errno` ustawiono `ERANGE` Jeśli wystąpi przepełnienie lub niedomiar.  
  
 Zobacz [_doserrno —, errno, _sys_errlist — i _sys_nerr —](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) kody powrotne — Aby uzyskać więcej informacji na ten i inne.  
  
## <a name="remarks"></a>Uwagi  
 Każda z tych funkcji konwertuje ciąg wejściowy `nptr` do `unsigned` `long`.  
  
 `strtoul`Zatrzymuje czytanie ciąg `nptr` pierwszego znaku nie jest rozpoznawana jako część liczby. Może to być znak końcowy null lub może być pierwszym znaku numerycznego większa niż lub równa `base`. `LC_NUMERIC` Ustawienie kategorii ustawień regionalnych określa rozpoznawania po znaku radix `nptr`; Aby uzyskać więcej informacji, zobacz [setlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md). `strtoul`i `wcstoul` Użyj bieżących ustawień regionalnych; `_strtoul_l` i `_wcstoul_l` są identyczne, z wyjątkiem tego, aby używały przekazano zamiast ustawień regionalnych. Aby uzyskać więcej informacji, zobacz [ustawień regionalnych](../../c-runtime-library/locale.md).  
  
 Jeśli `endptr` nie jest `NULL`, wskaźnik do znaku zatrzymania skanowania są przechowywane w lokalizacji wskazywanej przez `endptr`. Jeśli konwersja nie można wykonać (nie znaleziono żadnych prawidłowych cyfr lub określono nieprawidłowy atrybut podstawowy), wartość `nptr` są przechowywane w lokalizacji wskazywanej przez `endptr`.  
  
 `wcstoul`jest to wersja znaków dwubajtowych `strtoul`; `nptr` argument jest ciąg znaków dwubajtowych. W przeciwnym razie funkcje te działają tak samo.  
  
### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu  
  
|Procedura TCHAR.H|_Unicode — & _MBCS nie zdefiniowany|_MBCS zdefiniowano|_UNICODE zdefiniowano|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_tcstoul`|`strtoul`|`strtoul`|`wcstoul`|  
|`_tcstoul_l`|`strtoul_l`|`_strtoul_l`|`_wcstoul_l`|  
  
 `strtoul`oczekuje `nptr` wskaż ciąg następującą postać:  
  
 [`whitespace`] [{`+` &#124; `-`}] [`0` [{ `x` &#124; `X` }]] [`digits`]  
  
 A `whitespace` może zawierać znaków miejsca i karty, które są ignorowane. `digits` są co najmniej jeden cyfr dziesiętnych. Pierwszy znak należący do tego formularza zatrzymuje skanowania. Jeśli `base` jest od 2 do 36, zostanie użyty jako podstawa liczby. Jeśli `base` ma wartość 0, znaków ciągu wskazywana przez `nptr` są używane do określenia podstawy. Jeśli pierwszym znakiem 0 i nie jest znak "x" lub "X", ciąg jest interpretowany jako ósemkową liczby całkowitej. Jeśli pierwszym znakiem jest "0" i jest znak "x" lub "X", ciąg jest interpretowany jako szesnastkową liczby całkowitej. Jeśli pierwszym znakiem jest "1" do "9", ciąg jest interpretowany jako dziesiętną liczbą całkowitą. Litery "" do "z" (lub "" do "Z") mają przypisane wartości 10 do 35; tylko litery, w których przypisane wartości są mniej niż `base` są dozwolone. Pierwszy znak poza zakresem podstawy zatrzymuje skanowania. Na przykład jeśli `base` wynosi 0 i pierwszy znak skanowane to "0", zakłada, że całkowitą ósemkowe i się od znaku "8" lub "9" spowoduje zatrzymanie skanowania. `strtoul`Umożliwia znakiem plus (`+`) lub minus (`-`) znak prefiksu; wiodący znak minus wskazuje, że wartość zwracana jest zanegowane.  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`strtoul`|\<stdlib.h >|  
|`wcstoul`|\<stdlib.h > lub \<wchar.h >|  
|`_strtoul_l`|\<stdlib.h >|  
|`_wcstoul_l`|\<stdlib.h > lub \<wchar.h >|  
  
 Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md) we wprowadzeniu.  
  
## <a name="example"></a>Przykład  
 Zobacz przykład [strtod —](../../c-runtime-library/reference/strtod-strtod-l-wcstod-wcstod-l.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Konwersja danych](../../c-runtime-library/data-conversion.md)   
 [Ustawienia regionalne](../../c-runtime-library/locale.md)   
 [localeconv —](../../c-runtime-library/reference/localeconv.md)   
 [setLocale, _wsetlocale —](../../c-runtime-library/reference/setlocale-wsetlocale.md)   
 [Ciąg na wartość liczbową funkcje](../../c-runtime-library/string-to-numeric-value-functions.md)   
 [strtod —, _strtod_l —, wcstod — _wcstod_l —](../../c-runtime-library/reference/strtod-strtod-l-wcstod-wcstod-l.md)   
 [strtol —, wcstol —, _strtol_l — _wcstol_l —](../../c-runtime-library/reference/strtol-wcstol-strtol-l-wcstol-l.md)   
 [atof, _atof_l, _wtof, _wtof_l](../../c-runtime-library/reference/atof-atof-l-wtof-wtof-l.md)