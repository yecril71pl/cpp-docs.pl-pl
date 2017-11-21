---
title: "_filelength —, _filelengthi64 — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _filelengthi64
- _filelength
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
- api-ms-win-crt-stdio-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _filelength
- _filelengthi64
- filelengthi64
dev_langs: C++
helpviewer_keywords:
- filelengthi64 function
- lengths, file
- filelength function
- _filelength function
- files [C++], length
- _filelengthi64 function
ms.assetid: 3ab83d5a-543c-4079-b9d9-0abfc7da0275
caps.latest.revision: "14"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 3e455fd53bcbf981cccd5b75b44738070eb614d0
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="filelength-filelengthi64"></a>_filelength, _filelengthi64
Pobiera długość pliku.  
  
## <a name="syntax"></a>Składnia  
  
```  
long _filelength(   
   int fd   
);  
__int64 _filelengthi64(   
   int fd   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `fd`  
 Obiekt docelowy deskryptorów plików.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zarówno `_filelength` i `_filelengthi64` zwraca długość pliku w bajtach skojarzone z pliku docelowego `fd`. Jeśli `fd` jest deskryptora nieprawidłowy plik tej funkcji wywołuje program obsługi nieprawidłowych parametrów, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może kontynuować, zarówno zwracają L-1 wskazuje błąd i ustawić `errno` do `EBADF`.  
  
## <a name="requirements"></a>Wymagania  
  
|Funkcja|Wymagany nagłówek|  
|--------------|---------------------|  
|`_filelength`|\<IO.h >|  
|`_filelengthi64`|\<IO.h >|  
  
 Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md) we wprowadzeniu.  
  
## <a name="example"></a>Przykład  
 Zobacz przykład [_chsize —](../../c-runtime-library/reference/chsize.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Obsługa plików](../../c-runtime-library/file-handling.md)   
 [_chsize —](../../c-runtime-library/reference/chsize.md)   
 [_fileno —](../../c-runtime-library/reference/fileno.md)   
 [_fstat —, _fstat32 —, _fstat64 —, _fstati64 — _fstat32i64 —, _fstat64i32 —](../../c-runtime-library/reference/fstat-fstat32-fstat64-fstati64-fstat32i64-fstat64i32.md)   
 [_fstat —, _fstat32 —, _fstat64 —, _fstati64 — _fstat32i64 —, _fstat64i32 —](../../c-runtime-library/reference/fstat-fstat32-fstat64-fstati64-fstat32i64-fstat64i32.md)   
 [_stat, _wstat — funkcje](../../c-runtime-library/reference/stat-functions.md)   
 [_stat, _wstat — funkcje](../../c-runtime-library/reference/stat-functions.md)