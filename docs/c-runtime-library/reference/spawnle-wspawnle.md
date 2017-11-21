---
title: "_spawnle —, _wspawnle — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _spawnle
- _wspawnle
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
- api-ms-win-crt-process-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- spawnle
- _spawnle
- wspawnle
- _wspawnle
dev_langs: C++
helpviewer_keywords:
- spawnle function
- processes, creating
- _wspawnle function
- processes, executing new
- process creation
- wspawnle function
- _spawnle function
ms.assetid: 80308892-2815-49b1-8cca-53894c366f5a
caps.latest.revision: "17"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 1db331aa1f424e96cc10f89a944abc1e4ac43d2f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="spawnle-wspawnle"></a>_spawnle, _wspawnle
Tworzy i wykonuje nowego procesu.  
  
> [!IMPORTANT]
>  Nie można używać tego interfejsu API w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT, nie są obsługiwane z parametrem /ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## <a name="syntax"></a>Składnia  
  
```  
intptr_t _spawnle(  
   int mode,  
   const char *cmdname,  
   const char *arg0,  
   const char *arg1,  
   ... const char *argn,  
   NULL,  
   const char *const *envp   
);  
intptr_t _wspawnle(  
   int mode,  
   const wchar_t *cmdname,  
   const wchar_t *arg0,  
   const wchar_t *arg1,  
   ... const wchar_t *argn,  
   NULL,  
   const wchar_t *const *envp   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `mode`  
 Tryb wykonywania dla procesu wywołującego.  
  
 `cmdname`  
 Ścieżka pliku do wykonania.  
  
 `arg0, arg1, ... argn`  
 Lista wskaźników do argumentów. `arg0` Argument jest zwykle wskaźnik do `cmdname`. Argumenty `arg1` za pośrednictwem `argn` są wskaźnikami do ciągów znaków tworzących nowe listy argumentów. Po `argn`, musi istnieć `NULL` wskaźnik do znaku na końcu listy argumentów.  
  
 `envp`  
 Tablicy wskaźników do ustawienia środowiska.  
  
## <a name="return-value"></a>Wartość zwracana  
 Wartość zwrócona przez synchronicznego `_spawnle` lub `_wspawnle` (`_P_WAIT` określona dla `mode`) jest stan zakończenia nowego procesu. Wartość zwrócona przez asynchronicznego `_spawnle` lub `_wspawnle` (`_P_NOWAIT` lub `_P_NOWAITO` określona dla `mode`) jest uchwytu procesu. Stan zakończenia to 0, jeśli proces zakończony normalnie. W szczególności wywołuje działania zduplikowanego procesu można ustawić stanu zakończenia na wartość niezerową `exit` rutynowych z argumentem różną od zera. Jeśli nowy proces nie zostanie jawnie ustawiona stanu zakończenia dodatnią, stan zakończenia dodatnią wskazuje nietypowe wyjście z przerwania lub przerwania. Zwracana wartość -1 wskazuje błąd (nie jest zainicjowany nowy proces). W takim przypadku `errno` ustawiono na jedną z następujących wartości.  
  
 `E2BIG`  
 Lista argumentów przekracza 1024 bajty.  
  
 `EINVAL`  
 `mode`argument jest nieprawidłowy.  
  
 `ENOENT`  
 Nie znaleziono pliku lub ścieżki.  
  
 `ENOEXEC`  
 Określony plik nie jest wykonywalne lub ma nieprawidłowy format pliku wykonywalnego.  
  
 `ENOMEM`  
 Za mało pamięci jest dostępna do wykonania w nowym procesie.  
  
 Aby uzyskać więcej informacji na temat tych i innych kody powrotu, zobacz [_doserrno —, errno, _sys_errlist — i _sys_nerr —](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
## <a name="remarks"></a>Uwagi  
 Każda z tych funkcji tworzy i wykonuje nowy proces przekazywaniem każdy argument wiersza polecenia jako osobny parametr, a także przekazanie tablicy wskaźników do ustawienia środowiska.  
  
 Te funkcje walidację ich parametrów. Jeśli dowolny `cmdname` lub `arg0` jest ciągiem pustym lub wskaźnika o wartości null, program obsługi nieprawidłowych parametrów zostanie wywołany, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli dozwolone jest wykonywanie aby kontynuować, ustawianie tych funkcji `errno` do `EINVAL`i zwróć -1. Nie nowego procesu jest zduplikowany.  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`_spawnle`|\<process.h >|  
|`_wspawnle`|\<stdio.h > lub \<wchar.h >|  
  
 Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).  
  
## <a name="example"></a>Przykład  
 Zapoznaj się z przykładem w [_spawn, _wspawn — funkcje](../../c-runtime-library/spawn-wspawn-functions.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Proces i kontroli środowiska](../../c-runtime-library/process-and-environment-control.md)   
 [_spawn, _wspawn — funkcje](../../c-runtime-library/spawn-wspawn-functions.md)   
 [przerwania](../../c-runtime-library/reference/abort.md)   
 [atexit —](../../c-runtime-library/reference/atexit.md)   
 [_execwexec — funkcje](../../c-runtime-library/exec-wexec-functions.md)   
 [exit, _exit — _exit —](../../c-runtime-library/reference/exit-exit-exit.md)   
 [_flushall —](../../c-runtime-library/reference/flushall.md)   
 [_getmbcp —](../../c-runtime-library/reference/getmbcp.md)   
 [_onexit —, _onexit_m —](../../c-runtime-library/reference/onexit-onexit-m.md)   
 [_setmbcp —](../../c-runtime-library/reference/setmbcp.md)   
 [System, _wsystem —](../../c-runtime-library/reference/system-wsystem.md)