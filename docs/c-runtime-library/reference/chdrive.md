---
title: "_chdrive — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- _chdrive
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
- api-ms-win-crt-filesystem-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- chdrive
- _chdrive
dev_langs:
- C++
helpviewer_keywords:
- drives, changing
- _chdrive function
- chdrive function
ms.assetid: 212a1a4b-4fa8-444e-9677-7fca4c8c47e3
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 1290f5a29ce2b6d80f98889fbb0fc5709cfa43e4
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2018
---
# <a name="chdrive"></a>_chdrive
Zmienia bieżący stacji roboczych.  
  
> [!IMPORTANT]
> Nie można używać tego interfejsu API w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT, nie są obsługiwane w aplikacjach platformy uniwersalnej systemu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).  
  
## <a name="syntax"></a>Składnia  
  
```  
int _chdrive(   
   int drive   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `drive`  
 Liczba całkowita od 1 do 26, który określa bieżący roboczy dysku (1 = A, 2 = B i tak dalej).  
  
## <a name="return-value"></a>Wartość zwracana  
 Wartość zero (0), jeśli pomyślnie; zmieniono bieżącej stacji roboczych w przeciwnym razie wartość -1.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli `drive` jest nie jest w zakresie od 1 do 26 obsługi nieprawidłowy parametr jest wywoływany, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli jest dozwolone wykonywanie, aby kontynuować, **_chdrive —** funkcja zwraca wartość -1, `errno` ustawiono `EACCES`, i `_doserrno` ma ustawioną wartość `ERROR_INVALID_DRIVE`.  
  
 **_Chdrive —** funkcja nie jest bezpieczne wątkowo, ponieważ zależy on od **SetCurrentDirectory** funkcji, która jest elementem nie wątkowo. Aby użyć **_chdrive —** bezpiecznie w aplikacji wielowątkowej, musisz podać własne synchronizacja wątku. Aby uzyskać więcej informacji, przejdź do [biblioteki MSDN Library](http://go.microsoft.com/fwlink/p/?linkid=150542) , a następnie wyszukaj **SetCurrentDirectory**.  
  
 **_Chdrive —** funkcja zmienia tylko bieżący pracy dysk;  **_chdir —** zmienia bieżący katalog roboczy.  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|**_chdrive**|\<direct.h>|  
  
 Aby uzyskać więcej informacji, zobacz [zgodności](../../c-runtime-library/compatibility.md).  
  
## <a name="example"></a>Przykład  
 Zobacz przykład [_getdrive —](../../c-runtime-library/reference/getdrive.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Kontrola katalogu](../../c-runtime-library/directory-control.md)   
 [_chdir, _wchdir](../../c-runtime-library/reference/chdir-wchdir.md)   
 [_fullpath, _wfullpath](../../c-runtime-library/reference/fullpath-wfullpath.md)   
 [_getcwd, _wgetcwd](../../c-runtime-library/reference/getcwd-wgetcwd.md)   
 [_getdrive](../../c-runtime-library/reference/getdrive.md)   
 [_mkdir, _wmkdir](../../c-runtime-library/reference/mkdir-wmkdir.md)   
 [_rmdir, _wrmdir](../../c-runtime-library/reference/rmdir-wrmdir.md)   
 [system, _wsystem](../../c-runtime-library/reference/system-wsystem.md)