---
title: "Usuń _wremove — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _wremove
- remove
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
- remove
- _wremove
- _tremove
dev_langs: C++
helpviewer_keywords:
- tremove function
- _wremove function
- files [C++], deleting
- _tremove function
- files [C++], removing
- wremove function
- remove function
ms.assetid: b6345ec3-3289-4645-93a4-28b9e478cc19
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 43e7443204404f79a797cab09cb56560e719a896
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="remove-wremove"></a>remove, _wremove
Usuń plik.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
      int remove(  
   const char *path   
);  
int _wremove(  
   const wchar_t *path   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 *Ścieżka*  
 Ścieżka pliku do usunięcia.  
  
## <a name="return-value"></a>Wartość zwracana  
 Każda z tych funkcji zwraca wartość 0, jeśli plik zostanie pomyślnie usunięty. W przeciwnym razie zwraca wartość -1 i ustawia `errno` albo `EACCES` aby wskazać, że ścieżka Określa plik tylko do odczytu lub plik jest otwarty, lub do **enoent —** wskazująca, że nazwa pliku lub ścieżka nie został znaleziony lub ścieżki Określa katalog.  
  
 Zobacz [_doserrno —, errno, _sys_errlist — i _sys_nerr —](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) Aby uzyskać więcej informacji na temat tych i innych kodów powrotnych.  
  
## <a name="remarks"></a>Uwagi  
 **Usuń** funkcja usuwa plik określony przez *ścieżki.* `_wremove`jest to wersja znaków dwubajtowych **_Usuń**; *ścieżki* argument `_wremove` jest ciągiem znaków dwubajtowych. `_wremove`i **_Usuń** zachowują się tak samo w przeciwnym razie wartość. Należy zamknąć wszystkie dojścia do pliku, aby można było usunąć.  
  
### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu  
  
|Procedura TCHAR.H|_Unicode — & _MBCS nie zdefiniowany|_MBCS zdefiniowano|_UNICODE zdefiniowano|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_tremove`|**Usuń**|**Usuń**|`_wremove`|  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|**Usuń**|\<stdio.h > lub \<io.h >|  
|`_wremove`|\<stdio.h > lub \<wchar.h >|  
  
 Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md) we wprowadzeniu.  
  
## <a name="libraries"></a>Biblioteki  
 Wszystkie wersje [biblioteki wykonawcze języka C](../../c-runtime-library/crt-library-features.md).  
  
## <a name="example"></a>Przykład  
  
```  
// crt_remove.c  
/* This program uses remove to delete crt_remove.txt */  
  
#include <stdio.h>  
  
int main( void )  
{  
   if( remove( "crt_remove.txt" ) == -1 )  
      perror( "Could not delete 'CRT_REMOVE.TXT'" );  
   else  
      printf( "Deleted 'CRT_REMOVE.TXT'\n" );  
}  
```  
  
## <a name="input-crtremovetxt"></a>Dane wejściowe: crt_remove.txt  
  
```  
This file will be deleted.  
```  
  
## <a name="sample-output"></a>Przykładowe dane wyjściowe  
  
```  
Deleted 'CRT_REMOVE.TXT'  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Obsługa plików](../../c-runtime-library/file-handling.md)   
 [_unlink —, _wunlink —](../../c-runtime-library/reference/unlink-wunlink.md)