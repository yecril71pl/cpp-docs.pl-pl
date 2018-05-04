---
title: Przestarzałe funkcje | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp
- devlang-cpp
ms.topic: conceptual
f1_keywords:
- is_wctype
- _loaddll
- _unloaddll
- _getdllprocaddr
- _seterrormode
- _beep
- _sleep
- _getsystime
- corecrt_wctype/is_wctype
- process/_loaddll
- process/_unloaddll
- process/_getdllprocaddr
- stdlib/_seterrormode
- stdlib/_beep
- stdlib/_sleep
- time/_getsystime
- time/_setsystime
dev_langs:
- C++
helpviewer_keywords:
- obsolete functions
- _beep function
- _sleep function
- _seterrormode function
ms.assetid: 8e14c2d4-1481-4240-8586-47eb43db02b0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c6fcb14a91aadb01d3962758b19ce636fddfbe13
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="obsolete-functions"></a>Przestarzałe funkcje
Niektóre funkcje są przestarzałe i mieć nowszą odpowiedniki. Firma Microsoft zaleca się, że możesz zmienić zaktualizowanych wersji. Inne przestarzałe funkcje zostały usunięte z CRT. W tym temacie wymieniono funkcje przestarzałe jako przestarzałe i funkcje usunięte w przypadku konkretnej wersji programu Visual Studio.  
  
## <a name="deprecated-as-obsolete-in-visual-studio-2015"></a>Przestarzałe jako przestarzały w programie Visual Studio 2015  
  
|Funkcja przestarzała|Alternatywne|  
|-----------------------|-----------------|  
|`is_wctype`|[iswctype —](../c-runtime-library/reference/isctype-iswctype-isctype-l-iswctype-l.md)|  
|`_loaddll`|[LoadLibrary](http://go.microsoft.com/fwlink/p/?LinkID=259187), [LoadLibraryEx](http://go.microsoft.com/fwlink/p/?LinkID=236091), lub [LoadPackagedLibrary](https://msdn.microsoft.com/library/windows/desktop/hh447159\(v=vs.85\).aspx)|  
|`_unloaddll`|[FreeLibrary](http://go.microsoft.com/fwlink/p/?LinkID=259188)|  
|`_getdllprocaddr`|[GetProcAddress](../build/getprocaddress.md)|  
|`_seterrormode`|[SetErrorMode](http://go.microsoft.com/fwlink/p/?LinkID=255242)|  
|`_beep`|[Sygnał dźwiękowy](https://msdn.microsoft.com/library/windows/desktop/ms679277\(v=vs.85\).aspx)|  
|`_sleep`|[uśpienia](https://msdn.microsoft.com/library/windows/desktop/ms686298\(v=vs.85\).aspx)|  
|`_getsystime`|[GetLocalTime](https://msdn.microsoft.com/library/windows/desktop/ms724338\(v=vs.85\).aspx)|  
|`_setsystime`|[SetLocalTime](https://msdn.microsoft.com/library/windows/desktop/ms724936\(v=vs.85\).aspx)|  
  
## <a name="removed-from-the-crt-in-visual-studio-2015"></a>Usunięte z CRT w programie Visual Studio 2015  
  
|Funkcja przestarzała|Alternatywne|  
|-----------------------|-----------------|  
|[_cgets, _cgetws](../c-runtime-library/cgets-cgetws.md)|[_cgets_s, _cgetws_s](../c-runtime-library/reference/cgets-s-cgetws-s.md)|  
|[gets, _getws](../c-runtime-library/gets-getws.md)|[gets_s, _getws_s](../c-runtime-library/reference/gets-s-getws-s.md)|  
|[_get_output_format](../c-runtime-library/get-output-format.md)|Brak|  
|[_heapadd](../c-runtime-library/heapadd.md)|Brak|  
|[_heapset](../c-runtime-library/heapset.md)|Brak|  
|[inp, inpw](../c-runtime-library/inp-inpw.md)|Brak|  
|[_inp, _inpw, _inpd](../c-runtime-library/inp-inpw-inpd.md)|Brak|  
|[outp, outpw](../c-runtime-library/outp-outpw.md)|Brak|  
|[_outp, _outpw, _outpd](../c-runtime-library/outp-outpw-outpd.md)|Brak|  
|[_set_output_format](../c-runtime-library/set-output-format.md)|Brak|  
  
## <a name="removed-from-the-crt-in-earlier-versions-of-visual-studio"></a>Usunięte z CRT we wcześniejszych wersjach programu Visual Studio  
 [_lock](../c-runtime-library/lock.md)  
  
 [_unlock](../c-runtime-library/unlock.md)