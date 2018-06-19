---
title: __getmainargs, __wgetmainargs | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
apiname:
- __wgetmainargs
- __getmainargs
apilocation:
- msvcr100.dll
- msvcrt.dll
- msvcr110_clr0400.dll
- msvcr80.dll
- msvcr110.dll
- msvcr90.dll
- msvcr120.dll
apitype: DLLExport
f1_keywords:
- __wgetmainargs
- __getmainargs
dev_langs:
- C++
helpviewer_keywords:
- __wgetmainargs
- __getmainargs
ms.assetid: f72f54eb-9509-4bdf-8752-40fc49055439
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 13707791b78de2c000535d60ed3f298046e4576c
ms.sourcegitcommit: 6e3cf8df676d59119ce88bf5321d063cf479108c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/22/2018
ms.locfileid: "34451289"
---
# <a name="getmainargs-wgetmainargs"></a>__getmainargs, __wgetmainargs
Wywołuje wiersza polecenia analizy i kopiuje argumenty `main()` za pośrednictwem przekazanych wskaźników.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
int __getmainargs(  
    int * _Argc,   
   char *** _Argv,   
   char *** _Env,   
   int _DoWildCard,  
_startupinfo * _StartInfo);  
  
 int __wgetmainargs (  
   int *_Argc,  
   wchar_t ***_Argv,  
   wchar_t ***_Env,  
   int _DoWildCard,  
   _startupinfo * _StartInfo)  
  
```  
  
#### <a name="parameters"></a>Parametry  
 `_Argc`  
 Liczba całkowita, która zawiera liczbę argumentów, które należy wykonać w `argv`. Parametr `argc` jest zawsze większy lub równy 1.  
  
 `_Argv`  
 Tablica ciągów zakończonych znakiem null, która reprezentuje argumenty wiersza polecenia wprowadzone przez użytkownika programu. Według konwencji `argv[0]` polecenia, z którym program jest wywoływany, ARGV — [1] jest pierwszy argument wiersza polecenia i tak dalej, aż do ARGV — [argc —], która jest zawsze **NULL**. Pierwszy argument wiersza polecenia jest zawsze `argv[1]` i jest ostatni z nich `argv[argc - 1]`.  
  
 `_Env`  
 Tablica ciągów reprezentujących zmienne w środowisku użytkownika. Ta tablica jest został przerwany przez **NULL** wpisu.  
  
 `_DoWildCard`  
 Liczba całkowita który Jeśli ustawiona na 1 rozszerza symbole wieloznaczne w argumentach wiersza polecenia lub wartość 0 nie działają.  
  
 `_StartInfo`  
 Inne informacje, które mają być przekazane do biblioteki DLL CRT.  
  
## <a name="return-value"></a>Wartość zwracana  
 0 w przypadku powodzenia; wartość ujemna w przypadku niepowodzenia.  
  
## <a name="remarks"></a>Uwagi  
 Użyj `__getmainargs` na platformach znaków innych niż całej i `__wgetmainargs` na platformach znaków dwubajtowych (Unicode).  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|__getmainargs|internal.h|  
|__wgetmainargs|internal.h|