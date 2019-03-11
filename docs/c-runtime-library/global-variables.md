---
title: Zmienne globalne
ms.date: 11/04/2016
f1_keywords:
- c.variables
helpviewer_keywords:
- global variables
- variables, global
- global variables, Microsoft run-time library
ms.assetid: 01d1551c-2f0c-4f72-935c-6442caccf84f
ms.openlocfilehash: dfa78bd2c7aae7cc6059443066cbef58512755ce
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/11/2019
ms.locfileid: "57744368"
---
# <a name="global-variables"></a>Zmienne globalne

Biblioteka środowiska uruchomieniowego Microsoft C zawiera następujące zmienne globalne i makra. Niektóre z tych zmiennych globalnych lub makra zostały zaniechane i zastąpione bardziej bezpieczne funkcjonalności wersje, które firma Microsoft zaleca używanie zamiast zmiennych globalnych.

|Zmienna|Opis|
|--------------|-----------------|
|[__argc, \__argv, \__wargv](../c-runtime-library/argc-argv-wargv.md)|Zawiera argumenty wiersza polecenia.|
|[_daylight, _dstbias, _timezone i _tzname](../c-runtime-library/daylight-dstbias-timezone-and-tzname.md)|Przestarzałe. Zamiast tego należy użyć `_get_daylight`, `_get_dstbias`, `_get_timezone`, i `_get_tzname`.<br /><br /> Dopasowuje dla czasu lokalnego; używane w niektórych funkcji daty i godziny.|
|[errno, _doserrno, _sys_errlist i _sys_nerr](../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)|Przestarzałe. Zamiast tego należy użyć `_get_errno`, `_set_errno`, `_get_doserrno`, `_set_doserrno`, `perror` i `strerror`.<br /><br /> Kody błędów i powiązane informacje są przechowywane.|
|[_environ, _wenviron](../c-runtime-library/environ-wenviron.md)|Przestarzałe. Zamiast tego należy użyć `getenv_s`, `_wgetenv_s`, `_dupenv_s`, `_wdupenv_s`, `_putenv_s`, i `_wputenv_s`.<br /><br /> Wskaźniki do tablic wskaźników do zmiennych środowiskowych przetwarzania; zainicjowany przy uruchamianiu.|
|[_fmode](../c-runtime-library/fmode.md)|Przestarzałe. Zamiast tego należy użyć `_get_fmode` lub `_set_fmode`.<br /><br /> Ustawia domyślny tryb tłumaczenia pliku.|
|[_iob](../c-runtime-library/iob.md)|Tablica struktur sterujących operacji We/Wy dla konsoli, pliki i urządzeń.|
|[_pctype, _pwctype, _wctype, _mbctype, _mbcasemap](../c-runtime-library/pctype-pwctype-wctype-mbctype-mbcasemap.md)|Zawiera informacje używane przez funkcje klasyfikacji znaków.|
|[_pgmptr, _wpgmptr](../c-runtime-library/pgmptr-wpgmptr.md)|Przestarzałe. Zamiast tego należy użyć `_get_pgmptr` lub `_get_wpgmptr`.<br /><br /> Inicjowane w momencie uruchamiania programu, w pełni kwalifikowaną lub względną ścieżkę do programu, pełną nazwę programu lub nazwę programu bez rozszerzenie nazwy pliku, w zależności od tego, w jaki sposób program został wywołany.|

## <a name="see-also"></a>Zobacz także

[Dokumentacja biblioteki środowiska uruchomieniowego języka C](../c-runtime-library/c-run-time-library-reference.md)<br/>
[Stałe globalne](../c-runtime-library/global-constants.md)<br/>
[__argc, \__argv, \__wargv](../c-runtime-library/argc-argv-wargv.md)<br/>
[_get_daylight](../c-runtime-library/reference/get-daylight.md)<br/>
[_get_dstbias](../c-runtime-library/reference/get-dstbias.md)<br/>
[_get_timezone](../c-runtime-library/reference/get-timezone.md)<br/>
[_get_tzname](../c-runtime-library/reference/get-tzname.md)<br/>
[perror](../c-runtime-library/reference/perror-wperror.md)<br/>
[strerror](../c-runtime-library/reference/strerror-strerror-wcserror-wcserror.md)<br/>
[_get_doserrno](../c-runtime-library/reference/get-doserrno.md)<br/>
[_set_doserrno](../c-runtime-library/reference/set-doserrno.md)<br/>
[_get_errno](../c-runtime-library/reference/get-errno.md)<br/>
[_set_errno](../c-runtime-library/reference/set-errno.md)<br/>
[_dupenv_s, _wdupenv_s](../c-runtime-library/reference/dupenv-s-wdupenv-s.md)<br/>
[getenv, _wgetenv](../c-runtime-library/reference/getenv-wgetenv.md)<br/>
[getenv_s, _wgetenv_s](../c-runtime-library/reference/getenv-s-wgetenv-s.md)<br/>
[_putenv, _wputenv](../c-runtime-library/reference/putenv-wputenv.md)<br/>
[_putenv_s, _wputenv_s](../c-runtime-library/reference/putenv-s-wputenv-s.md)<br/>
[_get_fmode](../c-runtime-library/reference/get-fmode.md)<br/>
[_set_fmode](../c-runtime-library/reference/set-fmode.md)
