---
title: "_spawnvp —, _wspawnvp — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _wspawnvp
- _spawnvp
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
- _wspawnvp
- _spawnvp
- wspawnvp
dev_langs: C++
helpviewer_keywords:
- wspawnvp function
- processes, creating
- _wspawnvp function
- processes, executing new
- spawnvp function
- process creation
- _spawnvp function
ms.assetid: 8d8774ec-6ad4-4680-a5aa-440cde1e0249
caps.latest.revision: "16"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 646921389ee4f6473872b55bc7c1e2f430385c3f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="spawnvp-wspawnvp"></a>_spawnvp, _wspawnvp
Tworzy proces i go uruchomi.  
  
> [!IMPORTANT]
>  Nie można używać tego interfejsu API w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT, nie są obsługiwane z parametrem /ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## <a name="syntax"></a>Składnia  
  
```  
intptr_t _spawnvp(  
   int mode,  
   const char *cmdname,  
   const char *const *argv   
);  
intptr_t _wspawnvp(  
   int mode,  
   const wchar_t *cmdname,  
   const wchar_t *const *argv   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `mode`  
 Tryb wykonywania wywoływania procesu.  
  
 `cmdname`  
 Ścieżka pliku do wykonania.  
  
 `argv`  
 Tablicy wskaźników do argumentów. Argument `argv`[0] jest zwykle wskaźnik do ścieżki w trybie rzeczywistym lub nazwę programu w trybie chronionym i `argv`[1] za pomocą `argv`[`n`] są wskaźnikami do ciągów znaków, które tworzą nowe listy argumentów. Argument `argv`[`n` + 1] musi być `NULL` wskaźnik do znaku na końcu listy argumentów.  
  
## <a name="return-value"></a>Wartość zwracana  
 Wartość zwrócona przez synchronicznego `_spawnvp` lub `_wspawnvp` (`_P_WAIT` określona dla `mode`) jest stan zakończenia nowego procesu. Wartość zwrócona przez asynchronicznego `_spawnvp` lub `_wspawnvp` (`_P_NOWAIT` lub `_P_NOWAITO` określona dla `mode`) jest uchwytu procesu. Stan zakończenia to 0, jeśli proces zakończony normalnie. Jeśli działania zduplikowanego procesu używa w szczególności argument różną od zera do wywołania, można ustawić stanu zakończenia na wartość niezerową `exit` procedury. Jeśli nowy proces nie zostanie jawnie ustawiona stanu zakończenia dodatnią, stan zakończenia dodatnią wskazuje nietypowe wyjście z przerwania lub przerwania. Zwracana wartość -1 wskazuje błąd (nie jest zainicjowany nowy proces). W takim przypadku `errno` ustawiono na jedną z następujących wartości:  
  
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
  
 Aby uzyskać więcej informacji na temat tych i innych kody powrotne, zobacz [errno _doserrno —, _sys_errlist — i _sys_nerr —](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
## <a name="remarks"></a>Uwagi  
 Każda z tych funkcji tworzy nowy proces wykonuje go i przekazuje tablicy wskaźników do argumentów wiersza polecenia i używa `PATH` zmiennej środowiskowej można znaleźć pliku do wykonania.  
  
 Te funkcje walidację ich parametrów. Jeśli dowolny `cmdname` lub `argv` jest wskaźnika o wartości null, lub jeśli `argv` wskazuje wskaźnika o wartości null, lub `argv[0]` to ciąg pusty wywołany program obsługi nieprawidłowych parametrów, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli dozwolone jest wykonywanie aby kontynuować, ustawianie tych funkcji `errno` do `EINVAL`i zwróć -1. Nie nowego procesu jest zduplikowany.  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`_spawnvp`|\<stdio.h > lub \<process.h >|  
|`_wspawnvp`|\<stdio.h > lub \<wchar.h >|  
  
 Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).  
  
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