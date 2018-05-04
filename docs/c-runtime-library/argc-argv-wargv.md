---
title: __argc __argv, __wargv | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
apiname:
- __wargv
- __argv
- __argc
apilocation:
- msvcrt120.dll
apitype: DLLExport
f1_keywords:
- __argv
- __argc
- __wargv
dev_langs:
- C++
helpviewer_keywords:
- __argv
- __wargv
- __argc
ms.assetid: 17001b0a-04ad-4762-b3a6-c54847f02d7c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4d5d9762f02a06e697ce164910755431e8a59009
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="argc-argv-wargv"></a>__argc __argv, __wargv
`__argc` — Zmienna globalna jest liczba liczba argumentów wiersza polecenia przekazywane do programu. `__argv` wskaźnik do tablicy bajtów jednoznakowym lub kilku byte znak ciągi, które zawierają argumenty programu i `__wargv` wskaźnika do tablicy znaków dwubajtowych ciągi, które zawierają argumenty programu. Te zmienne globalne podać argumenty `main` lub `wmain`.  
  
## <a name="syntax"></a>Składnia  
  
```  
extern int __argc;  
extern char ** __argv;  
extern wchar_t ** __wargv;  
```  
  
## <a name="remarks"></a>Uwagi  
 W programie, który używa `main` funkcji `__argc` i `__argv` są inicjowane w momencie uruchamiania programu przy użyciu wiersza polecenia, który służy do uruchomienia programu. W wierszu polecenia jest analizowana w oddzielne argumenty i symbole wieloznaczne są rozwinięte. Liczba argumentów jest przypisany do `__argc` ciągów argumentu są przydzielone na stercie i wskaźnika do tablicy argumentów jest przypisany do `__argv`. W programie skompilowany do użycia znaki dwubajtowe i `wmain` funkcji, argumenty są parsowane symbole wieloznaczne są rozwijane jako ciągi znaków dwubajtowych i wskaźnika do tablicy ciągów argument jest przypisany do `__wargv`.  
  
 Kod przenośny, zalecane jest użycie Argumenty przekazane do `main` uzyskać argumenty wiersza polecenia w programie.  
  
### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu  
  
|Procedura tchar.h|_Unicode — nie zdefiniowany|_UNICODE zdefiniowano|  
|---------------------|---------------------------|-----------------------|  
|`__targv`|`__argv`|`__wargv`|  
  
## <a name="requirements"></a>Wymagania  
  
|Zmienna globalna|Wymagany nagłówek|  
|---------------------|---------------------|  
|`__argc`, `__argv`, `__wargv`|\<stdlib.h>, \<cstdlib> (C++)|  
  
 `__argc`, `__argv`, i `__wargv` są rozszerzenia Microsoft. Aby uzyskać informacje dotyczące zgodności, zobacz [zgodności](../c-runtime-library/compatibility.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Zmienne globalne](../c-runtime-library/global-variables.md)   
 [main: uruchamianie programu](../cpp/main-program-startup.md)   
 [Korzystanie z wmain zamiast main](../cpp/using-wmain-instead-of-main.md)