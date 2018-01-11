---
title: "_execvp —, _wexecvp — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _execvp
- _wexecvp
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
- _execvp
- wexecvp
- _wexecvp
dev_langs: C++
helpviewer_keywords:
- _execvp function
- _wexecvp function
- wexecvp function
- execvp function
ms.assetid: a4db15df-b204-4987-be7c-de84c3414380
caps.latest.revision: "21"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 38ab921dc120fc82e05845c62dcc355167ad09c1
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="execvp-wexecvp"></a>_execvp, _wexecvp
Ładuje i wykonuje nowych procesów podrzędnych.  
  
> [!IMPORTANT]
>  Nie można używać tego interfejsu API w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT, nie są obsługiwane z parametrem /ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## <a name="syntax"></a>Składnia  
  
```  
intptr_t _execvp(   
   const char *cmdname,  
   const char *const *argv   
);  
intptr_t _wexecvp(   
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
  
|`errno`wartość|Opis|  
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
 Każda z tych funkcji ładuje i wykonuje nowy proces, przekazanie tablicy wskaźników do argumentów wiersza polecenia i za pomocą `PATH` zmiennej środowiskowej można znaleźć pliku do wykonania.  
  
 `_execvp` Funkcje walidację ich parametrów. Jeśli `cmdname` jest wskaźnika o wartości null, lub `argv` wskaźnik null wskaźnika do tablicy puste lub jeśli tablica zawiera pusty ciąg jako pierwszego argumentu, te funkcje wywołanie program obsługi nieprawidłowych parametrów, zgodnie z opisem w [parametru Sprawdzanie poprawności](../../c-runtime-library/parameter-validation.md). Jeśli dozwolone jest wykonywanie aby kontynuować, ustawianie tych funkcji `errno` do `EINVAL` i zwróć -1. Żaden proces nie jest uruchomiona.  
  
## <a name="requirements"></a>Wymagania  
  
|Funkcja|Wymagany nagłówek|Opcjonalne nagłówki|  
|--------------|---------------------|---------------------|  
|`_execvp`|\<process.h >|\<errno.h >|  
|`_wexecvp`|\<process.h > lub \<wchar.h >|\<errno.h >|  
  
 Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).  
  
## <a name="example"></a>Przykład  
 Zapoznaj się z przykładem w [_execwexec — funkcje](../../c-runtime-library/exec-wexec-functions.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Proces i kontroli środowiska](../../c-runtime-library/process-and-environment-control.md)   
 [_execwexec — funkcje](../../c-runtime-library/exec-wexec-functions.md)   
 [przerwania](../../c-runtime-library/reference/abort.md)   
 [atexit —](../../c-runtime-library/reference/atexit.md)   
 [exit, _exit — _exit —](../../c-runtime-library/reference/exit-exit-exit.md)   
 [_onexit —, _onexit_m —](../../c-runtime-library/reference/onexit-onexit-m.md)   
 [_spawn, _wspawn — funkcje](../../c-runtime-library/spawn-wspawn-functions.md)   
 [system, _wsystem](../../c-runtime-library/reference/system-wsystem.md)