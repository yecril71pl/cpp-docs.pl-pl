---
title: _daylight, _dstbias, _timezone, i _tzname
ms.date: 11/04/2016
f1_keywords:
- tzname
- _timezone
- timezone
- _daylight
- _tzname
- daylight
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
ms.openlocfilehash: 3f9f78d0798140399960cade7ead408f958450ba
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62344645"
---
# <a name="daylight-dstbias-timezone-and-tzname"></a>_daylight, _dstbias, _timezone, i _tzname

`_daylight`, `_dstbias`, `_timezone`, i `_tzname` są używane w niektórych procedur Data i godzina zmiany czasu lokalnego. Tych zmiennych globalnych są używane w bardziej bezpieczne wersje funkcjonalności, które powinny być używane zamiast zmiennych globalnych.

|Zmienna globalna|Odpowiednik funkcjonalności|
|---------------------|---------------------------|
|`_daylight`|[_get_daylight](../c-runtime-library/reference/get-daylight.md)|
|`_dstbias`|[_get_dstbias](../c-runtime-library/reference/get-dstbias.md)|
|`_timezone`|[_get_timezone](../c-runtime-library/reference/get-timezone.md)|
|`_tzname`|[_get_tzname](../c-runtime-library/reference/get-tzname.md)|

Są deklarowane w czasie.h w następujący sposób.

## <a name="syntax"></a>Składnia

```
extern int _daylight;
extern int _dstbias;
extern long _timezone;
extern char *_tzname[2];
```

## <a name="remarks"></a>Uwagi

W wywołaniu `_ftime`, `localtime`, lub `_tzset`, wartości `_daylight`, `_dstbias`, `_timezone`, i `_tzname` są ustalane na podstawie wartości `TZ` zmiennej środowiskowej. Jeśli nie jawnie ustawiona wartość `TZ`, `_tzname[0]` i `_tzname[1]` zawierają odpowiednio domyślne ustawienie opcji "PST" i "(PDT)".  Funkcje manipulowania czasu ([_tzset —](../c-runtime-library/reference/tzset.md), [_ftime](../c-runtime-library/reference/ftime-ftime32-ftime64.md), i [localtime](../c-runtime-library/reference/localtime-localtime32-localtime64.md)) próba ustawienia wartości `_daylight`, `_dstbias` i `_timezone` przez wykonywanie zapytania systemu operacyjnego dla wartości domyślnej dla każdej zmiennej. Wartości zmiennych globalnych strefy czasowej są wyświetlane w poniższej tabeli.

|Zmienna|Wartość|
|--------------|-----------|
|`_daylight`|Wartość różną od zera, jeśli określono strefę czasu letniego (DST) w `TZ` lub określone z systemu operacyjnego, w przeciwnym razie 0. Wartość domyślna to 1.|
|`_dstbias`|Przesunięcie czasu.|
|`_timezone`|Różnica w sekundach między uniwersalny czas koordynowany i czasem lokalnym. Wartością domyślną jest 28 800.|
|`_tzname[0]`|Nazwa strefy czasowej pochodną `TZ` zmiennej środowiskowej. Wartość domyślna to "PST".|
|`_tzname[1]`|Nazwa strefy czasu letniego pochodną `TZ` zmiennej środowiskowej. Wartość domyślna to "PDT" (Pacyfik czas letni).|

## <a name="see-also"></a>Zobacz także

[Zmienne globalne](../c-runtime-library/global-variables.md)<br/>
[_get_daylight](../c-runtime-library/reference/get-daylight.md)<br/>
[_get_dstbias](../c-runtime-library/reference/get-dstbias.md)<br/>
[_get_timezone](../c-runtime-library/reference/get-timezone.md)<br/>
[_get_tzname](../c-runtime-library/reference/get-tzname.md)
