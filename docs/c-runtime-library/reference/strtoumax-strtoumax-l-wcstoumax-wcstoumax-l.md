---
title: "strtoumax —, _strtoumax_l —, wcstoumax —, _wcstoumax_l — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _wcstoumax_l
- _strtoumax_l
- wcstoumax
- strtoumax
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
- wcstoumax
- _tcstoumax
- _strtoumax_l
- _wcstoumax_l
- _tcstoumax_l
- strtoumax
dev_langs: C++
helpviewer_keywords:
- _strtoumax_l function
- conversion functions
- wcstoumax function
- _wcstoumax_l function
- strtoumax function
ms.assetid: 566769f9-495b-4508-b9c6-02217a578897
caps.latest.revision: "5"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 15553980eb54bf5be149abddc17fb69ceb648aee
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="strtoumax-strtoumaxl-wcstoumax-wcstoumaxl"></a>strtoumax, _strtoumax_l, wcstoumax, _wcstoumax_l
Konwertuje ciągów na wartość całkowitą typu największy obsługiwanej liczby całkowitej bez znaku.  
  
## <a name="syntax"></a>Składnia  
  
```  
uintmax_t strtoumax(  
   const char *nptr,  
   char **endptr,  
   int base   
);  
uintmax_t _strtoumax_l(  
   const char *nptr,  
   char **endptr,  
   int base,  
   _locale_t locale  
);  
uintmax_t wcstoumax(  
   const wchar_t *nptr,  
   wchar_t **endptr,  
   int base   
);  
uintmax_t _wcstoumax_l(  
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
 `strtoumax`Zwraca wartość przekonwertowana, lub `UINTMAX_MAX` na przepełnienia. `strtoumax`Zwraca wartość 0, jeśli konwersja nie jest możliwe. `wcstoumax`Zwraca wartości analogously do `strtoumax`. Dla obu tych funkcji `errno` ustawiono `ERANGE` Jeśli wystąpi przepełnienie lub niedomiar.  
  
 Aby uzyskać więcej informacji na temat kody powrotu, zobacz [errno _doserrno —, _sys_errlist — i _sys_nerr —](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
## <a name="remarks"></a>Uwagi  
 Każda z tych funkcji konwertuje ciąg wejściowy `nptr` do `uintmax_t` wartości całkowitej.  
  
 `strtoumax`Zatrzymuje czytanie ciąg `nptr` pierwszego znaku nie jest rozpoznawana jako część liczby. Może to być znak końcowy null lub być może jest ona pierwszego znaku liczbowego, który jest większa niż lub równa `base`. `LC_NUMERIC` Ustawienie kategorii ustawień regionalnych określa rozpoznawania znaku podstawa w `nptr`. Aby uzyskać więcej informacji, zobacz [setlocale, _wsetlocale —](../../c-runtime-library/reference/setlocale-wsetlocale.md). `strtoumax`i `wcstoumax` Użyj bieżących ustawień regionalnych; `_strtoumax_l` i `_wcstoumax_l` są identyczne z tą różnicą, że zamiast tego użyć ustawień regionalnych, który jest przekazywany w. Aby uzyskać więcej informacji, zobacz [ustawień regionalnych](../../c-runtime-library/locale.md).  
  
 Jeśli `endptr` nie jest `NULL`, wskaźnik do znaku zatrzymania skanowania są przechowywane w lokalizacji, która jest wskazywana przez `endptr`. Jeśli konwersja nie można wykonać (nie znaleziono żadnych prawidłowych cyfr lub określono nieprawidłowy atrybut podstawowy), wartość `nptr` są przechowywane w lokalizacji, która jest wskazywana przez `endptr`.  
  
 Wersja znaków dwubajtowych `strtoumax` jest `wcstoumax`; `nptr` argument jest ciąg znaków dwubajtowych. W przeciwnym razie funkcje te działają tak samo.  
  
### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu  
  
|Procedura TCHAR.H|_Unicode — & _MBCS nie zdefiniowany|_MBCS zdefiniowano|_UNICODE zdefiniowano|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_tcstoumax`|`strtoumax`|`strtoumax`|`wcstoumax`|  
|`_tcstoumax_l`|`strtoumax_l`|`_strtoumax_l`|`_wcstoumax_l`|  
  
 `strtoumax`oczekuje `nptr` wskaż ciąg następującą postać:  
  
 [`whitespace`] [{`+` &#124; `-`}] [`0` [{ `x` &#124; `X` }]] [`digits` &#124; [`letters`]]  
  
 A `whitespace` może zawierać znaków miejsca i karty, które są ignorowane. `digits` są co najmniej jeden cyfr dziesiętnych; `letters` to jeden lub więcej litery "" do "z" (lub "A" do "Z"). Pierwszy znak należący do tego formularza zatrzymuje skanowania. Jeśli `base` jest od 2 do 36, zostanie użyty jako podstawa liczby. Jeśli `base` ma wartość 0, znaków ciągu, która jest wskazywana przez `nptr` są używane do określenia podstawy. Jeśli pierwszym znakiem "0" i nie jest znak "x" lub "X", ciąg jest interpretowany jako ósemkową liczby całkowitej. Jeśli pierwszym znakiem jest "0" i jest znak "x" lub "X", ciąg jest interpretowany jako szesnastkową liczby całkowitej. Jeśli pierwszym znakiem jest "1" do "9", ciąg jest interpretowany jako dziesiętną liczbą całkowitą. Litery "" do "z" (lub "" do "Z") mają przypisane wartości 10 do 35; tylko litery, w których przypisane wartości są mniej niż `base` są dozwolone. Pierwszy znak poza zakresem podstawy zatrzymuje skanowania. Na przykład jeśli `base` wynosi 0 i pierwszy znak skanowane to "0", zakłada, że całkowitą ósemkowe i się od znaku "8" lub "9" spowoduje zatrzymanie skanowania. `strtoumax`Umożliwia znak plus (`+`) lub znak minus (`-`) prefiks; wiodącego znak minus wskazuje, że wartość zwracana jest dopełnienia dwa jego wartości bezwzględne skonwertowany ciąg.  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`strtoumax`|\<stdlib.h >|  
|`wcstoumax`|\<stdlib.h > lub \<wchar.h >|  
|`_strtoumax_l`|\<stdlib.h >|  
|`_wcstoumax_l`|\<stdlib.h > lub \<wchar.h >|  
  
 Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).  
  
## <a name="example"></a>Przykład  
 Zobacz przykład [strtod —](../../c-runtime-library/reference/strtod-strtod-l-wcstod-wcstod-l.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Konwersja danych](../../c-runtime-library/data-conversion.md)   
 [Ustawienia regionalne](../../c-runtime-library/locale.md)   
 [localeconv —](../../c-runtime-library/reference/localeconv.md)   
 [setLocale, _wsetlocale —](../../c-runtime-library/reference/setlocale-wsetlocale.md)   
 [Ciąg na wartość liczbową funkcje](../../c-runtime-library/string-to-numeric-value-functions.md)   
 [strtod —, _strtod_l —, wcstod — _wcstod_l —](../../c-runtime-library/reference/strtod-strtod-l-wcstod-wcstod-l.md)   
 [strtoimax, _strtoimax_l —, wcstoimax — _wcstoimax_l —](../../c-runtime-library/reference/strtoimax-strtoimax-l-wcstoimax-wcstoimax-l.md)   
 [strtol —, wcstol —, _strtol_l — _wcstol_l —](../../c-runtime-library/reference/strtol-wcstol-strtol-l-wcstol-l.md)   
 [strtoul —, _strtoul_l —, wcstoul — _wcstoul_l —](../../c-runtime-library/reference/strtoul-strtoul-l-wcstoul-wcstoul-l.md)   
 [strtoll —, _strtoll_l —, wcstoll — _wcstoll_l —](../../c-runtime-library/reference/strtoll-strtoll-l-wcstoll-wcstoll-l.md)   
 [atof —, _atof_l —, _wtof — _wtof_l —](../../c-runtime-library/reference/atof-atof-l-wtof-wtof-l.md)