---
title: Zmienne globalne | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- c.variables
dev_langs:
- C++
helpviewer_keywords:
- global variables
- variables, global
- global variables, Microsoft run-time library
ms.assetid: 01d1551c-2f0c-4f72-935c-6442caccf84f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a2da3dd07c7088bee4be750b764b4a467bfebeae
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32392042"
---
# <a name="global-variables"></a>Zmienne globalne
Biblioteki wykonawcze języka Microsoft C zawiera następujące zmienne globalne lub makr. Niektóre z tych zmiennych globalnych lub makra ma została zastąpiona bardziej bezpiecznych funkcjonalne wersje, które firma Microsoft zaleca się, że można użyć zamiast zmiennych globalnych.  
  
|Zmienna|Opis|  
|--------------|-----------------|  
|[__argc, \__argv, \__wargv](../c-runtime-library/argc-argv-wargv.md)|Zawiera argumenty wiersza polecenia.|  
|[_daylight, _dstbias, _timezone i _tzname](../c-runtime-library/daylight-dstbias-timezone-and-tzname.md)|Przestarzałe. Zamiast tego należy użyć `_get_daylight`, `_get_dstbias`, `_get_timezone`, i `_get_tzname`.<br /><br /> Dopasowuje dla czasu lokalnego; używane w niektórych funkcji daty i godziny.|  
|[errno, _doserrno, _sys_errlist i _sys_nerr](../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)|Przestarzałe. Zamiast tego należy użyć `_get_errno`, `_set_errno`, `_get_doserrno`, `_set_doserrno`, `perror` i `strerror`.<br /><br /> Przechowuje kody błędów oraz powiązane informacje.|  
|[_environ, _wenviron](../c-runtime-library/environ-wenviron.md)|Przestarzałe. Zamiast tego należy użyć `getenv_s`, `_wgetenv_s`, `_dupenv_s`, `_wdupenv_s`, `_putenv_s`, i `_wputenv_s`.<br /><br /> Wskaźniki do tablic wskaźników do procesu ciągów środowiska; zainicjowane przy uruchamianiu.|  
|[_fmode](../c-runtime-library/fmode.md)|Przestarzałe. Zamiast tego należy użyć `_get_fmode` lub `_set_fmode`.<br /><br /> Ustawia domyślny tryb tłumaczenia pliku.|  
|[_iob](../c-runtime-library/iob.md)|Tablica struktury sterujące We/Wy dla konsoli, plików i urządzeń.|  
|[_pctype, _pwctype, _wctype, _mbctype, _mbcasemap](../c-runtime-library/pctype-pwctype-wctype-mbctype-mbcasemap.md)|Zawiera informacje używane przez funkcje klasyfikacji znaków.|  
|[_pgmptr, _wpgmptr](../c-runtime-library/pgmptr-wpgmptr.md)|Przestarzałe. Zamiast tego należy użyć `_get_pgmptr` lub `_get_wpgmptr`.<br /><br /> Zainicjowane w momencie uruchamiania programu w pełni kwalifikowaną lub względną ścieżkę program, pełną nazwę programu lub nazwę programu, bez jego rozszerzenie nazwy pliku, w zależności od tego, jak program został wywołany.|  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do biblioteki wykonawcze języka C](../c-runtime-library/c-run-time-library-reference.md)   
 [Stałe globalne](../c-runtime-library/global-constants.md)   
 [__argc, \__argv, \__wargv](../c-runtime-library/argc-argv-wargv.md)   
 [_get_daylight](../c-runtime-library/reference/get-daylight.md)   
 [_get_dstbias](../c-runtime-library/reference/get-dstbias.md)   
 [_get_timezone](../c-runtime-library/reference/get-timezone.md)   
 [_get_tzname —](../c-runtime-library/reference/get-tzname.md)   
 [perror](../c-runtime-library/reference/perror-wperror.md)   
 [strerror —](../c-runtime-library/reference/strerror-strerror-wcserror-wcserror.md)   
 [_get_doserrno](../c-runtime-library/reference/get-doserrno.md)   
 [_set_doserrno](../c-runtime-library/reference/set-doserrno.md)   
 [_get_errno](../c-runtime-library/reference/get-errno.md)   
 [_set_errno](../c-runtime-library/reference/set-errno.md)   
 [_dupenv_s —, _wdupenv_s —](../c-runtime-library/reference/dupenv-s-wdupenv-s.md)   
 [getenv —, _wgetenv —](../c-runtime-library/reference/getenv-wgetenv.md)   
 [getenv_s, _wgetenv_s](../c-runtime-library/reference/getenv-s-wgetenv-s.md)   
 [_putenv —, _wputenv —](../c-runtime-library/reference/putenv-wputenv.md)   
 [_putenv_s —, _wputenv_s —](../c-runtime-library/reference/putenv-s-wputenv-s.md)   
 [_get_fmode](../c-runtime-library/reference/get-fmode.md)   
 [_set_fmode](../c-runtime-library/reference/set-fmode.md)