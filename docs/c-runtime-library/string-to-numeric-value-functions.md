---
title: "Ciąg na wartość liczbową funkcje | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apilocation:
- msvcr80.dll
- msvcr110.dll
- msvcr120.dll
- msvcr100.dll
- msvcr110_clr0400.dll
- msvcr90.dll
apitype: DLLExport
f1_keywords:
- _tcstoui64
- _tcstoi64
dev_langs: C++
helpviewer_keywords:
- parsing, numeric strings
- string conversion, to numeric values
ms.assetid: 11cbd9ce-033b-4914-bf66-029070e7e385
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 68586bac573018bceb7dc982625ff6a859d18871
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="string-to-numeric-value-functions"></a>Konwertowanie ciągów na wartości
-   [strtod, _strtod_l, wcstod, _wcstod_l](../c-runtime-library/reference/strtod-strtod-l-wcstod-wcstod-l.md)  
  
-   [strtol, wcstol, _strtol_l, _wcstol_l](../c-runtime-library/reference/strtol-wcstol-strtol-l-wcstol-l.md)  
  
-   [strtoul, _strtoul_l, wcstoul, _wcstoul_l](../c-runtime-library/reference/strtoul-strtoul-l-wcstoul-wcstoul-l.md)  
  
-   [_strtoi64, _wcstoi64, _strtoi64_l, _wcstoi64_l](../c-runtime-library/reference/strtoi64-wcstoi64-strtoi64-l-wcstoi64-l.md)  
  
-   [_strtoui64, _wcstoui64, _strtoui64_l, _wcstoui64_l](../c-runtime-library/reference/strtoui64-wcstoui64-strtoui64-l-wcstoui64-l.md)  
  
## <a name="remarks"></a>Uwagi  
 Każda funkcja w **strtod —** rodziny konwertuje ciąg znaków zakończony znakiem null na wartość liczbową. W poniższej tabeli wymieniono dostępne funkcje.  
  
|Funkcja|Opis|  
|--------------|-----------------|  
|`strtod`|Konwertowanie ciągu na wartość zmiennoprzecinkową o podwójnej precyzji|  
|`strtol`|Konwertowanie ciągu na długich liczb całkowitych|  
|`strtoul`|Przekonwertować ciągu na liczbę całkowitą bez znaku długa|  
|`_strtoi64`|Konwertowanie ciągu na 64-bitowych `__int64` liczba całkowita|  
|`_strtoui64`|64-bitowych unsigned przekonwertować ciągu na `__int64` liczba całkowita|  
  
 `wcstod`, `wcstol`, `wcstoul`, i `_wcstoi64` wersji znaków dwubajtowych `strtod`, `strtol`, `strtoul`, i `_strtoi64`odpowiednio. Argument ciągu do każdego z tych funkcji znaków dwubajtowych jest ciąg znaków dwubajtowych. Każda funkcja zachowuje się tak samo z jego odpowiednikiem pojedynczych bajtów znaków w przeciwnym razie wartość.  
  
 `strtod` Funkcja przyjmuje dwa argumenty: ciąg wejściowy jest pierwszy i drugi wskaźnik do znaku, która kończy proces konwersji. `strtol`, `strtoul`, **_strtoi64 —** i **_strtoui64 —** przyjmować trzeci argument jako numer podstawowy używany w procesie konwersji.  
  
 Ciąg wejściowy jest sekwencji znaków, które mogą być interpretowane jako wartość liczbowa określonego typu. Każda funkcja zatrzymuje odczytywania ciągu pierwszego znaku, który nie jest rozpoznawana jako część liczby. Może to być znak końcowy null. Aby uzyskać `strtol`, `strtoul`, `_strtoi64`, i `_strtoui64`, to znaku zakończenia można też pierwszego znaku numerycznego większa lub równa liczbie dostarczone przez użytkownika podstawowego.  
  
 Jeśli nie ustawiono dostarczone przez użytkownika wskaźnik do znaku zakończenia z konwersji **NULL** w momencie wywołania wskaźnik do znaku zatrzymania skanowania będzie znajdować się zamiast tego. Jeśli konwersja nie można wykonać (nie znaleziono żadnych prawidłowych cyfr lub określono nieprawidłowy atrybut podstawowy), wartość wskaźnika ciągu znajduje się pod tym adresem.  
  
 `strtod`spodziewa się ciągu na następującą postać:  
  
 [*odstępem*] [*znak*] [`digits`] [**.** `digits`] [{**d** &#124; **D** &#124; **e** &#124; **E**} [*znak*]`digits`]  
  
 A *odstępem* może zawierać znaków spację lub tabulator, które są ignorowane. *znak* jest plus (**+**) lub minus (**-**); i `digits` są co najmniej jeden cyfr dziesiętnych. Jeśli cyfr nie pojawia się przed znakiem podstawa, co najmniej jeden musi występować po znaku podstawę systemu liczbowego. Wykładnik, obejmującego wprowadzające litery może zawierać wyłącznie cyfr dziesiętnych (**d**, **D**, **e**, lub **E**) i opcjonalnie liczbę całkowitą ze znakiem. Jeśli pojawi się części wykładnika ani znaków podstawa, znak radix — zakłada się, że wykonaj ostatnich cyfr w ciągu. Pierwszy znak należący do tego formularza zatrzymuje skanowania.  
  
 `strtol`, `strtoul`, `_strtoi64`, I `_strtoui64` funkcje oczekiwany ciąg następującą postać:  
  
 [*odstępem*] [{ **+**  &#124;  **-** }] [**0** [{ **x** &#124; **X** }]] [`digits`]  
  
 W przypadku podstawowej argument od 2 do 36, następnie jest używany jako bazowy liczby. Jeśli jest 0 znaków odwołuje się do wskaźnika celu z konwersji są używane na podstawie. Jeśli pierwszym znakiem 0 i nie jest znak "x" lub "X", ciąg jest interpretowany jako ósemkową liczby całkowitej; w przeciwnym razie wartość jest interpretowana jako liczbę dziesiętną. Jeśli pierwszym znakiem jest "0" i jest znak "x" lub "X", ciąg jest interpretowany jako szesnastkową liczby całkowitej. Jeśli pierwszym znakiem jest "1" do "9", ciąg jest interpretowany jako dziesiętną liczbą całkowitą. Litery "" do "z" (lub "" do "Z") mają przypisane wartości 10 do 35; tylko litery, w których przypisane wartości są mniej niż *podstawowej* są dozwolone. `strtoul`i `_strtoui64` Zezwalaj znakiem plus (**+**) lub minus (**-**) znak prefiksu; wiodący znak minus wskazuje, że wartość zwracana jest zanegowane.  
  
 Wartość wyjściowa jest zagrożony ustawienie `LC_NUMERIC` ustawienie kategorii ustawień regionalnych; zobacz [setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md) Aby uzyskać więcej informacji. Wersje tych funkcji bez **_l** Użyj sufiksu bieżące ustawienia regionalne tego zachowania zależnych od ustawień regionalnych; wersje z **_l** sufiks są identyczne, z wyjątkiem tego, aby używały parametr ustawień regionalnych Przekazano zamiast tego.  
  
 Jeśli wartość zwracana przez te funkcje mogłoby spowodować przepełnienie lub niedopełnienie lub po konwersji nie jest możliwe, specjalne wielkość wartości są zwracane, jak pokazano:  
  
|Funkcja|Warunek|Wartość zwracana|  
|--------------|---------------|--------------------|  
|`strtod`|Przepełnienie|+/- `HUGE_VAL`|  
|`strtod`|Niedopełnienie lub brak konwersji|0|  
|`strtol`|+ Przepełnienie|**LONG_MAX —**|  
|`strtol`|-Przepełnienia|**LONG_MIN —**|  
|`strtol`|Niedopełnienie lub brak konwersji|0|  
|`_strtoi64`|+ Przepełnienie|**_I64_MAX**|  
|`_strtoi64`|-Przepełnienia|**_I64_MIN**|  
|`_strtoi64`|Brak konwersji|0|  
|`_strtoui64`|Przepełnienie|**_UI64_MAX**|  
|`_strtoui64`|Brak konwersji|0|  
  
 **_I64_MAX**, _**I64_MIN**, i **_UI64_MAX** są definiowane w granicach. H.  
  
 `wcstod`, `wcstol`, `wcstoul`, `_wcstoi64`, i `_wcstoui64` wersji znaków dwubajtowych `strtod`, `strtol`, `strtoul`, `_strtoi64`, i `_strtoui64`odpowiednio; wskaźnik do Każda z tych funkcji znaków dwubajtowych zakończenia z konwersji argument jest ciąg znaków dwubajtowych. W przeciwnym wypadku każda z tych funkcji znaków dwubajtowych zachowuje się tak samo z jego odpowiednikiem pojedynczych bajtów znaków.  
  
## <a name="see-also"></a>Zobacz też  
 [Konwersja danych](../c-runtime-library/data-conversion.md)   
 [Ustawienia regionalne](../c-runtime-library/locale.md)   
 [Interpretacja wielobajtowych sekwencji znaków](../c-runtime-library/interpretation-of-multibyte-character-sequences.md)   
 [Obsługa liczb zmiennoprzecinkowych](../c-runtime-library/floating-point-support.md)   
 [atof, _atof_l, _wtof, _wtof_l](../c-runtime-library/reference/atof-atof-l-wtof-wtof-l.md)