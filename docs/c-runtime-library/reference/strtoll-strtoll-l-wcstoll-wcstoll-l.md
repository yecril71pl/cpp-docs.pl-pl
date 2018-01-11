---
title: "strtoll —, _strtoll_l —, wcstoll —, _wcstoll_l — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- strtoll
- wcstoll
- _strtoll_l
- _wcstoll_l
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
- _strtoll_l
- _tcstoll_l
- _tcstoll
- _wcstoll_l
- strtoll
- wcstoll
dev_langs: C++
helpviewer_keywords:
- _tcstoll_l function
- _wcstoll_l function
- strtoll function
- wcstoll function
- _tcstoll function
- _strtoll_l function
ms.assetid: e2d05dcf-d3b2-4291-9e60-dee77e540fd7
caps.latest.revision: "5"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: f449cd73a8536fb7dbdf46b7c7d1d45ad449cb10
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="strtoll-strtolll-wcstoll-wcstolll"></a>strtoll, _strtoll_l, wcstoll, _wcstoll_l
Konwertuje ciąg na `long long` wartość.  
  
## <a name="syntax"></a>Składnia  
  
```  
long long strtoll(  
   const char *nptr,  
   char **endptr,  
   int base   
);  
long long wcstoll(  
   const wchar_t *nptr,  
   wchar_t **endptr,  
   int base   
);  
long long _strtoll_l(  
   const char *nptr,  
   char **endptr,  
   int base,  
   _locale_t locale  
);  
long long _wcstoll_l(  
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
 `strtoll`Zwraca wartość, która jest reprezentowana w ciągu `nptr`, z wyjątkiem przypadków, gdy reprezentacja mogłoby spowodować przepełnienie — w takim przypadku zwraca `LLONG_MAX` lub `LLONG_MIN`. Funkcja zwraca wartość 0, jeśli konwersja nie jest możliwe. `wcstoll`Zwraca wartości analogously do `strtoll`.  
  
 `LLONG_MAX`i `LLONG_MIN` są definiowane w granicach. H.  
  
 Jeśli `nptr` jest `NULL` lub `base` jest różna od zera i mniejszym niż 2 lub większą niż 36 `errno` ma ustawioną wartość `EINVAL`.  
  
 Aby uzyskać więcej informacji na temat kody powrotu, zobacz [errno _doserrno —, _sys_errlist — i _sys_nerr —](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
## <a name="remarks"></a>Uwagi  
 `strtoll` Funkcji konwertuje `nptr` do `long long`. Zatrzymaj funkcjami odczytywania ciąg `nptr` pierwszego znaku, ich nie jest rozpoznawana jako część liczby. Może to być znak końcowy null lub być może jest ona pierwszego znaku liczbowego, który jest większa niż lub równa `base`. `wcstoll`jest to wersja znaków dwubajtowych `strtoll`; `nptr` argument jest ciąg znaków dwubajtowych. W przeciwnym razie funkcje te działają tak samo.  
  
### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu  
  
|Procedura TCHAR.H|_Unicode — & _MBCS nie zdefiniowany|_MBCS zdefiniowano|_UNICODE zdefiniowano|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_tcstoll`|`strtoll`|`strtoll`|`wcstoll`|  
|`_tcstoll_l`|`_strtoll_l`|`_strtoll_l`|`_wcstoll_l`|  
  
 Ustawienia regionalne `LC_NUMERIC` ustawienie kategorii określa rozpoznawania po znaku radix `nptr`; Aby uzyskać więcej informacji, zobacz [setlocale, _wsetlocale —](../../c-runtime-library/reference/setlocale-wsetlocale.md). Funkcje, które nie mają `_l` sufiks Użyj bieżących ustawień regionalnych; `_strtoll_l` i `_wcstoll_l` są takie same jak odpowiednie funkcje, które nie mają sufiks, z wyjątkiem tego, że zamiast tego użyć ustawień regionalnych, który jest przekazywany w. Aby uzyskać więcej informacji, zobacz [ustawień regionalnych](../../c-runtime-library/locale.md).  
  
 Jeśli `endptr` nie jest `NULL`, wskaźnik do znaku zatrzymania skanowania są przechowywane w lokalizacji, która jest wskazywana przez `endptr`. Jeśli konwersja nie można wykonać (nie znaleziono żadnych prawidłowych cyfr lub określono nieprawidłowy atrybut podstawowy), wartość `nptr` są przechowywane w lokalizacji, która jest wskazywana przez `endptr`.  
  
 `strtoll`oczekuje `nptr` wskaż ciąg następującą postać:  
  
 [`whitespace`] [{`+` &#124; `-`}] [`0` [{ `x` &#124; `X` }]] [`digits` &#124; `letters`]  
  
 A `whitespace` może zawierać znaków miejsca i karty, które są ignorowane. `digits` są co najmniej jeden cyfr dziesiętnych; `letters` to jeden lub więcej litery "" do "z" (lub "A" do "Z"). Pierwszy znak należący do tego formularza zatrzymuje skanowania. Jeśli `base` jest od 2 do 36, zostanie użyty jako podstawa liczby. Jeśli `base` ma wartość 0, znaków ciągu, która jest wskazywana przez `nptr` są używane do określenia podstawy. Jeśli pierwszym znakiem "0" i nie jest znak "x" lub "X", ciąg jest interpretowany jako ósemkową liczby całkowitej. Jeśli pierwszym znakiem jest "0" i jest znak "x" lub "X", ciąg jest interpretowany jako szesnastkową liczby całkowitej. Jeśli pierwszym znakiem jest "1" do "9", ciąg jest interpretowany jako dziesiętną liczbą całkowitą. Litery "" do "z" (lub "" do "Z") mają przypisane wartości 10 do 35; tylko litery, w których przypisane wartości są mniej niż `base` są dozwolone. Pierwszy znak poza zakresem podstawy zatrzymuje skanowania. Na przykład jeśli `base` wynosi 0 i pierwszy znak skanowane to "0", zakłada, że całkowitą ósemkowe i skanowania zatrzymuje się od znaku "8" lub "9".  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`strtoll`, `_strtoll_l`|\<stdlib.h >|  
|`wcstoll`, `_wcstoll_l`|\<stdlib.h > lub \<wchar.h >|  
  
 Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Konwersja danych](../../c-runtime-library/data-conversion.md)   
 [Ustawienia regionalne](../../c-runtime-library/locale.md)   
 [localeconv —](../../c-runtime-library/reference/localeconv.md)   
 [setLocale, _wsetlocale —](../../c-runtime-library/reference/setlocale-wsetlocale.md)   
 [Ciąg na wartość liczbową funkcje](../../c-runtime-library/string-to-numeric-value-functions.md)   
 [strtod —, _strtod_l —, wcstod — _wcstod_l —](../../c-runtime-library/reference/strtod-strtod-l-wcstod-wcstod-l.md)   
 [strtol —, wcstol —, _strtol_l — _wcstol_l —](../../c-runtime-library/reference/strtol-wcstol-strtol-l-wcstol-l.md)   
 [strtoul —, _strtoul_l —, wcstoul — _wcstoul_l —](../../c-runtime-library/reference/strtoul-strtoul-l-wcstoul-wcstoul-l.md)   
 [atof, _atof_l, _wtof, _wtof_l](../../c-runtime-library/reference/atof-atof-l-wtof-wtof-l.md)