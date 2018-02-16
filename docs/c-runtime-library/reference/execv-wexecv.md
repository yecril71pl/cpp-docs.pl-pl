---
title: _execv, _wexecv | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- _wexecv
- _execv
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
- _execv
- _wexecv
- wexecv
dev_langs:
- C++
helpviewer_keywords:
- _wexecv function
- _execv function
- wexecv function
- execv function
ms.assetid: 8dbaf7bc-9040-4316-a0c1-db7e866b52af
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a9520c8975d342b423bf61a1f5973a4bdabfcc37
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2018
---
# <a name="execv-wexecv"></a>_execv, _wexecv
Ładuje i wykonuje nowych procesów podrzędnych.  
  
> [!IMPORTANT]
>  Nie można używać tego interfejsu API w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT, nie są obsługiwane w aplikacjach platformy uniwersalnej systemu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).  
  
## <a name="syntax"></a>Składnia  
  
```  
intptr_t _execv(   
   const char *cmdname,  
   const char *const *argv   
);  
intptr_t _wexecv(   
   const wchar_t *cmdname,  
   const wchar_t *const *argv   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `cmdname`  
 Ścieżka pliku do wykonania.  
  
 `argv`  
 Tablicy wskaźników do parametrów.  
  
## <a name="return-value"></a>Wartość zwracana  
 W przypadku powodzenia tych funkcji nie powróci do procesu wywołującego. Zwracana wartość -1 wskazuje błąd, w którym to przypadku `errno` ustawiono zmiennej globalnej.  
  
|`errno` Wartość|Opis|  
|-------------------|-----------------|  
|`E2BIG`|Miejsce wymagane do argumentów i ustawienia środowiska przekracza 32 KB.|  
|`EACCES`|Określony plik ma blokowania lub udostępniania naruszenie.|  
|`EINVAL`|Nieprawidłowy parametr.|  
|`EMFILE`|Za dużo plików Otwórz (czy jest pliku wykonywalnego musi można otworzyć określonego pliku).|  
|`ENOENT`|Plik lub nie można odnaleźć ścieżki.|  
|`ENOEXEC`|Określony plik nie jest wykonywalne lub ma nieprawidłowy format pliku wykonywalnego.|  
|`ENOMEM`|Za mało pamięci jest dostępna do wykonania w nowym procesie; dostępna pamięć jest uszkodzona; lub istnieje nieprawidłowy blok, wskazujący, że proces wywołujący nie został poprawnie przydzielony.|  
  
 Aby uzyskać więcej informacji na temat tych i innych kody powrotu, zobacz [_doserrno —, errno, _sys_errlist — i _sys_nerr —](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
## <a name="remarks"></a>Uwagi  
 Każda z tych funkcji ładuje i wykonuje nowy proces, przekazanie tablicy wskaźników do argumentów wiersza polecenia.  
  
 `_execv` Funkcje walidację ich parametrów. Jeśli `cmdname` jest wskaźnika o wartości null, lub, jeśli `argv` wskaźnik null wskaźnika do tablicy puste lub jeśli tablica zawiera pusty ciąg jako pierwszy argument `_execv` funkcji Wywołaj program obsługi nieprawidłowych parametrów, zgodnie z opisem w [ Sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli dozwolone jest wykonywanie aby kontynuować, ustawianie tych funkcji `errno` do `EINVAL` i zwróć -1. Żaden proces nie jest uruchomiona.  
  
## <a name="requirements"></a>Wymagania  
  
|Funkcja|Wymagany nagłówek|Opcjonalne nagłówki|  
|--------------|---------------------|---------------------|  
|`_execv`|\<process.h >|\<errno.h>|  
|`_wexecv`|\<process.h > lub \<wchar.h >|\<errno.h>|  
  
 Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).  
  
## <a name="example"></a>Przykład  
 Zapoznaj się z przykładem w [_execwexec — funkcje](../../c-runtime-library/exec-wexec-functions.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Proces i kontroli środowiska](../../c-runtime-library/process-and-environment-control.md)   
 [_execwexec — funkcje](../../c-runtime-library/exec-wexec-functions.md)   
 [Przerwania](../../c-runtime-library/reference/abort.md)   
 [atexit —](../../c-runtime-library/reference/atexit.md)   
 [exit, _Exit, _exit](../../c-runtime-library/reference/exit-exit-exit.md)   
 [_onexit, _onexit_m](../../c-runtime-library/reference/onexit-onexit-m.md)   
 [_spawn, _wspawn — funkcje](../../c-runtime-library/spawn-wspawn-functions.md)   
 [system, _wsystem](../../c-runtime-library/reference/system-wsystem.md)