---
title: strxfrm, wcsxfrm, _strxfrm_l, _wcsxfrm_l | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- strxfrm
- _wcsxfrm_l
- _strxfrm_l
- wcsxfrm
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
- api-ms-win-crt-string-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- strxfrm
- _tcsxfrm
- wcsxfrm
dev_langs:
- C++
helpviewer_keywords:
- strxfrm_l function
- _tcsxfrm function
- _strxfrm_l function
- strxfrm function
- wcsxfrm_l function
- wcsxfrm function
- string comparison [C++], transforming strings
- tcsxfrm function
- strings [C++], comparing locale
- _wcsxfrm_l function
ms.assetid: 6ba8e1f6-4484-49aa-83b8-bc2373187d9e
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0545fd71f571caa2fbb12cefb010c274cbda9f28
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2018
---
# <a name="strxfrm-wcsxfrm-strxfrml-wcsxfrml"></a>strxfrm, wcsxfrm, _strxfrm_l, _wcsxfrm_l
Przekształć ciąg na podstawie informacji specyficznych dla ustawień regionalnych.  
  
## <a name="syntax"></a>Składnia  
  
```  
size_t strxfrm(  
   char *strDest,  
   const char *strSource,  
   size_t count   
);  
size_t wcsxfrm(  
   wchar_t *strDest,  
   const wchar_t *strSource,  
   size_t count   
);  
size_t _strxfrm_l(  
   char *strDest,  
   const char *strSource,  
   size_t count,  
   _locale_t locale  
);  
size_t wcsxfrm_l(  
   wchar_t *strDest,  
   const wchar_t *strSource,  
   size_t count,  
   _locale_t locale  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `strDest`  
 Ciąg docelowego.  
  
 `strSource`  
 Ciąg źródła.  
  
 `count`  
 Maksymalna liczba znaków, które można umieścić w `strDest`.  
  
 `locale`  
 Ustawienia regionalne do użycia.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca długość ciągu przekształcone, nie licząc znak końcowy null. Jeśli wartość zwracana jest większa niż lub równa `count`, treść `strDest` będzie nieprzewidywalny. W przypadku wystąpienia błędu, ustawia każdej funkcji `errno` i zwraca `INT_MAX`. Nieprawidłowy znak `errno` ma ustawioną wartość `EILSEQ`.  
  
## <a name="remarks"></a>Uwagi  
 `strxfrm` Funkcja przekształca ciąg wskazywana przez `strSource` do nowego sortowane formularz, który jest przechowywany w `strDest`. Nie więcej niż `count` znaków, łącznie ze znakiem null są przetwarzane i umieszczane w ciągu wynikowym. Transformacja jest nawiązywane przy użyciu ustawień regionalnych `LC_COLLATE` ustawienie kategorii. Aby uzyskać więcej informacji na temat `LC_COLLATE`, zobacz [setlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md). `strxfrm` używa bieżące ustawienia regionalne dla jego działania zależnego od ustawień regionalnych; `_strxfrm_l` jest identyczny z tą różnicą, że używa ustawień regionalnych przekazano zamiast bieżących ustawień regionalnych. Aby uzyskać więcej informacji, zobacz [ustawień regionalnych](../../c-runtime-library/locale.md).  
  
 Po przekształceniu wywołanie `strcmp` z dwóch ciągów przekształcone daje wyniki identyczne z wywołania `strcoll` stosowane do oryginalnego dwóch ciągów. Jak `strcoll` i `stricoll`, `strxfrm` automatycznie obsługi ciągów znaków wielobajtowych zależnie od potrzeb.  
  
 `wcsxfrm` jest to wersja znaków dwubajtowych `strxfrm`; argumenty ciągu `wcsxfrm` są wskaźnikami znaków dwubajtowych. Dla `wcsxfrm`, po przekształcania ciągu, wywołanie `wcscmp` z dwóch ciągów przekształcone daje wyniki identyczne z wywołania `wcscoll` stosowane do oryginalnego dwóch ciągów. `wcsxfrm` i `strxfrm` zachowują się tak samo w przeciwnym razie wartość. `wcsxfrm` używa bieżące ustawienia regionalne dla jego działania zależnego od ustawień regionalnych; `_wcsxfrm_l` korzysta z ustawień regionalnych przekazano zamiast bieżących ustawień regionalnych.  
  
 Te funkcje walidację ich parametrów. Jeśli `strSource` jest wskaźnika o wartości null, lub `strDest` jest wskaźnik NULL (o ile liczba wynosi zero), lub jeśli `count` jest większa niż `INT_MAX`, program obsługi nieprawidłowych parametrów zostanie wywołany, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md) . Jeśli dozwolone jest wykonywanie aby kontynuować, ustawianie tych funkcji `errno` do `EINVAL` i zwracać `INT_MAX`.  
  
### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu  
  
|Procedura TCHAR.H|_Unicode — & _MBCS nie zdefiniowany|_MBCS zdefiniowano|_UNICODE zdefiniowano|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_tcsxfrm`|`strxfrm`|`strxfrm`|`wcsxfrm`|  
|`_tcsxfrm_l`|`_strxfrm_l`|`_strxfrm_l`|`_wcsxfrm_l`|  
  
 Zgodnie z ustawieniami regionalnymi "C" kolejność znaków w zestawie znaków (zestaw znaków ASCII) jest taka sama jak lexicographic kolejność znaków. Jednak w innych lokalizacjach kolejność znaków w zestawie znaków mogą się różnić od kolejność lexicographic znaków. Na przykład, w niektórych lokalizacjach Europejskich, znaków "" (wartość 0x61) poprzedza znak "&\#x00E4;" (wartość 0xE4) w zestawie znaków, ale znak "ä" poprzedza znak a lexicographically.  
  
 Ustawień regionalnych, dla których różnią się zestaw znaków i kolejność lexicographic znaków, użyj `strxfrm` na oryginalnym ciągów, a następnie `strcmp` na wynikowej ciągów w celu utworzenia porównania ciągów lexicographic zgodnie z bieżących ustawień regionalnych na `LC_COLLATE` ustawienie kategorii. W związku z tym, aby porównać dwa ciągi lexicographically w powyższych ustawień regionalnych, należy użyć `strxfrm` na oryginalnym ciągów, a następnie `strcmp` wynikowy ciągów. Alternatywnie można użyć `strcoll` zamiast `strcmp` na oryginalnym ciągów.  
  
 `strxfrm` jest zasadniczo otokę [LCMapString](http://msdn.microsoft.com/library/windows/desktop/dd318700) z `LCMAP_SORTKEY`.  
  
 Rozmiar tablicy potrzebne do przechowywania jest wartość wyrażenia następujące `strxfrm` przekształcania ciąg źródłowy:  
  
```  
1 + strxfrm( NULL, string, 0 )  
```  
  
 W ramach "C" ustawień regionalnych, `strxfrm` jest odpowiednikiem następujące:  
  
```  
strncpy( _string1, _string2, _count );  
return( strlen( _string1 ) );  
```  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`strxfrm`|\<string.h>|  
|`wcsxfrm`|\<String.h > lub \<wchar.h >|  
|`_strxfrm_l`|\<string.h>|  
|`_wcsxfrm_l`|\<String.h > lub \<wchar.h >|  
  
 Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md) we wprowadzeniu.  
  
## <a name="see-also"></a>Zobacz też  
 [Konwersja danych](../../c-runtime-library/data-conversion.md)   
 [localeconv](../../c-runtime-library/reference/localeconv.md)   
 [setLocale, _wsetlocale —](../../c-runtime-library/reference/setlocale-wsetlocale.md)   
 [Ustawienia regionalne](../../c-runtime-library/locale.md)   
 [Manipulowanie ciągami](../../c-runtime-library/string-manipulation-crt.md)   
 [strcoll — funkcje](../../c-runtime-library/strcoll-functions.md)   
 [strcmp —, wcscmp —, _mbscmp —](../../c-runtime-library/reference/strcmp-wcscmp-mbscmp.md)   
 [strncmp, wcsncmp, _mbsncmp, _mbsncmp_l](../../c-runtime-library/reference/strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)