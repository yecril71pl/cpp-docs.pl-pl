---
title: _daylight, _dstbias, _timezone i _tzname | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- tzname
- _timezone
- timezone
- _daylight
- _tzname
- daylight
dev_langs:
- C++
helpviewer_keywords:
- time zones
- time adjustments
- timezone variables
- _tzname function
- _daylight function
- _timezone function
- daylight function
- local time adjustments
- timezone function
- tzname function
- time-zone variables
ms.assetid: d06c7292-6b99-4aba-b284-16a96570c856
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 944a127fb71beb7dba1ba9434cbc5d778230c055
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="daylight-dstbias-timezone-and-tzname"></a>_daylight, _dstbias, _timezone, i _tzname
`_daylight`, `_dstbias`, `_timezone`, i `_tzname` są używane w niektórych procedury Data i godzina zmiany czasu lokalnego. Te zmienne globalne są używane w bardziej bezpieczne wersji funkcjonalności, których należy użyć zamiast zmiennych globalnych.  
  
|Zmienna globalna|Odpowiednik funkcjonalności|  
|---------------------|---------------------------|  
|`_daylight`|[_get_daylight](../c-runtime-library/reference/get-daylight.md)|  
|`_dstbias`|[_get_dstbias](../c-runtime-library/reference/get-dstbias.md)|  
|`_timezone`|[_get_timezone](../c-runtime-library/reference/get-timezone.md)|  
|`_tzname`|[_get_tzname](../c-runtime-library/reference/get-tzname.md)|  
  
 Zostały zgłoszone następujące w Time.h.  
  
## <a name="syntax"></a>Składnia  
  
```  
extern int _daylight;   
extern int _dstbias;   
extern long _timezone;   
extern char *_tzname[2];  
```  
  
## <a name="remarks"></a>Uwagi  
 W wywołaniu `_ftime`, `localtime`, lub `_tzset`, wartości `_daylight`, `_dstbias`, `_timezone`, i `_tzname` zależą od wartości `TZ` zmiennej środowiskowej. Jeśli nie zostanie jawnie ustawiona wartość `TZ`, `_tzname[0]` i `_tzname[1]` zawierają odpowiednio ustawienia domyślne "PST" i "PDT".  Funkcje manipulowania czasu ([_tzset —](../c-runtime-library/reference/tzset.md), [_ftime —](../c-runtime-library/reference/ftime-ftime32-ftime64.md), i [konwersję](../c-runtime-library/reference/localtime-localtime32-localtime64.md)) próba ustawienia wartości `_daylight`, `_dstbias` i `_timezone` przez Kwerenda systemu operacyjnego dla domyślnej wartości poszczególnych zmiennych. W poniższej tabeli przedstawiono wartości zmiennych globalnych strefy czasowej.  
  
|Zmienna|Wartość|  
|--------------|-----------|  
|`_daylight`|Różna od zera, jeśli strefa czasu (DST) został określony w `TZ` lub określonego systemu operacyjnego, a w przeciwnym razie 0. Wartość domyślna to 1.|  
|`_dstbias`|Przesunięcie czasu letniego.|  
|`_timezone`|Różnica w sekundach między uniwersalny czas koordynowany i czasem lokalnym. Wartością domyślną jest 28 800.|  
|`_tzname[0]`|Nazwa strefy czasowej pochodną `TZ` zmiennej środowiskowej. Wartość domyślna to "PST".|  
|`_tzname[1]`|Nazwa strefy czasu letniego pochodną `TZ` zmiennej środowiskowej. Wartość domyślna to "PDT" (pacyficzny czas letni).|  
  
## <a name="see-also"></a>Zobacz też  
 [Zmienne globalne](../c-runtime-library/global-variables.md)   
 [_get_daylight](../c-runtime-library/reference/get-daylight.md)   
 [_get_dstbias](../c-runtime-library/reference/get-dstbias.md)   
 [_get_timezone](../c-runtime-library/reference/get-timezone.md)   
 [_get_tzname](../c-runtime-library/reference/get-tzname.md)