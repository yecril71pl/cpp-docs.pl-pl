---
title: "_execvpe —, _wexecvpe — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _execvpe
- _wexecvpe
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
- wexecvpe
- execvpe
- _wexecvpe
- _execvpe
dev_langs: C++
helpviewer_keywords:
- wexecvpe function
- execvpe function
- _wexecvpe function
- _execvpe function
ms.assetid: c0c3c986-d9c0-4814-a96c-10f0b3092766
caps.latest.revision: "23"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 7d9a7edb225afeba4b7d091db9a7a25103361913
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="execvpe-wexecvpe"></a>_execvpe, _wexecvpe
Ładuje i uruchamia nowe procesy podrzędne.  
  
> [!IMPORTANT]
>  Nie można używać tego interfejsu API w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT, nie są obsługiwane z parametrem /ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## <a name="syntax"></a>Składnia  
  
```  
intptr_t _execvpe(   
   const char *cmdname,  
   const char *const *argv,  
   const char *const *envp   
);  
intptr_t _wexecvpe(   
   const wchar_t *cmdname,  
   const wchar_t *const *argv,  
   const wchar_t *const *envp   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `cmdname`  
 Ścieżka pliku do wykonania.  
  
 `argv`  
 Tablicy wskaźników do parametrów.  
  
 `envp`  
 Tablicy wskaźników do ustawienia środowiska.  
  
## <a name="return-value"></a>Wartość zwracana  
 W przypadku powodzenia tych funkcji nie powróci do procesu wywołującego. Zwracana wartość -1 wskazuje błąd, w którym to przypadku `errno` ustawiono zmiennej globalnej.  
  
|`errno`wartość|Opis|  
|-------------------|-----------------|  
|`E2BIG`|Miejsca, które są wymagane dla argumentów i ustawienia środowiska przekracza 32 KB.|  
|`EACCES`|Określony plik ma blokowania lub udostępniania naruszenie.|  
|`EMFILE`|Zbyt wiele plików są otwarte. (Aby ustalić, czy jest pliku wykonywalnego musi można otworzyć określonego pliku.)|  
|`ENOENT`|Nie znaleziono pliku lub ścieżki.|  
|`ENOEXEC`|Określony plik nie jest wykonywalne lub ma nieprawidłowy format pliku wykonywalnego.|  
|`ENOMEM`|Za mało pamięci jest dostępna do wykonania w nowym procesie; dostępna pamięć jest uszkodzona; lub istnieje nieprawidłowy blok, co oznacza, że proces wywołujący nie został poprawnie przydzielony.|  
  
 Aby uzyskać więcej informacji na temat tych i innych kody powrotu, zobacz [errno _doserrno —, _sys_errlist — i _sys_nerr —](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
## <a name="remarks"></a>Uwagi  
 Każda z tych funkcji ładuje wykonuje nowego procesu i przekazuje tablicy wskaźników do argumentów wiersza polecenia i tablicy wskaźników do ustawienia środowiska. Użyj tych funkcji `PATH` zmiennej środowiskowej można znaleźć pliku do wykonania.  
  
 `_execvpe` Funkcje walidację ich parametrów. Jeśli `cmdname` jest wskaźnika o wartości null, lub jeśli `argv` jest wskaźnika o wartości null, wskaźnik do pustą tablicę lub wskaźnika do tablicy, która zawiera pusty ciąg jako pierwszego argumentu, te funkcje Wywołaj program obsługi nieprawidłowych parametrów, zgodnie z opisem w [Sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli dozwolone jest wykonywanie aby kontynuować, ustawianie tych funkcji `errno` do `EINVAL` i zwróć -1. Żaden proces nie jest uruchomiona.  
  
## <a name="requirements"></a>Wymagania  
  
|Funkcja|Wymagany nagłówek|Opcjonalne nagłówki|  
|--------------|---------------------|---------------------|  
|`_execvpe`|\<process.h >|\<errno.h >|  
|`_wexecvpe`|\<process.h > lub \<wchar.h >|\<errno.h >|  
  
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
 [System, _wsystem —](../../c-runtime-library/reference/system-wsystem.md)