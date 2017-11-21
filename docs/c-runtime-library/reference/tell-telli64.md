---
title: "_tell —, _telli64 — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _telli64
- _tell
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
- tell
- telli64
- _telli64
- _tell
dev_langs: C++
helpviewer_keywords:
- tell function
- file pointers [C++], getting
- _tell function
- file pointers [C++]
- telli64 function
- _telli64 function
ms.assetid: 1500e8f9-8fec-4253-9eec-ec66125dfc9b
caps.latest.revision: "14"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 57e628419bbf074418d053c755269618f480743e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="tell-telli64"></a>_tell, _telli64
Pobierz pozycję wskaźnika pliku.  
  
## <a name="syntax"></a>Składnia  
  
```  
long _tell(  
   int handle  
);  
__int64 _telli64(  
   int handle   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `handle`  
 Plik deskryptora odwołujące się do otwarcia pliku.  
  
## <a name="return-value"></a>Wartość zwracana  
 Bieżąca pozycja wskaźnika pliku. Na urządzeniach niezdolne do wyszukiwania wartość zwracana jest niezdefiniowany.  
  
 Zwracana wartość L-1 wskazuje błąd. Jeśli `handle` jest deskryptora nieprawidłowy plik wywołany program obsługi nieprawidłowych parametrów, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli dozwolone jest wykonywanie aby kontynuować, ustawianie tych funkcji `errno` do `EBADF` i zwracać L-1.  
  
 Zobacz [_doserrno —, errno, _sys_errlist — i _sys_nerr —](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) kody powrotne — Aby uzyskać więcej informacji na ten i inne.  
  
## <a name="remarks"></a>Uwagi  
 `_tell` Funkcja pobiera bieżącą pozycję wskaźnika pliku (jeśli istnieje) skojarzone z `handle` argumentu. Pozycja jest wyrażone jako liczba bajtów od początku pliku. Aby uzyskać `_telli64` funkcji, ta wartość jest wyrażona jako 64-bitową liczbę całkowitą.  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`_tell`, `_telli64`|\<IO.h >|  
  
 Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md) we wprowadzeniu.  
  
## <a name="example"></a>Przykład  
  
```  
// crt_tell.c  
// This program uses _tell to tell the  
// file pointer position after a file read.  
//  
  
#include <io.h>  
#include <stdio.h>  
#include <fcntl.h>  
#include <share.h>  
#include <string.h>  
  
int main( void )  
{  
   int  fh;  
   char buffer[500];  
  
   if ( _sopen_s( &fh, "crt_tell.txt", _O_RDONLY, _SH_DENYNO, 0) )  
   {  
      char buff[50];  
      _strerror_s( buff, sizeof(buff), NULL );  
      printf( buff );  
      exit( -1 );  
   }  
  
   if( _read( fh, buffer, 500 ) > 0 )  
      printf( "Current file position is: %d\n", _tell( fh ) );  
   _close( fh );  
}  
```  
  
## <a name="input-crttelltxt"></a>Dane wejściowe: crt_tell.txt  
  
```  
Line one.  
Line two.  
```  
  
### <a name="output"></a>Dane wyjściowe  
  
```  
Current file position is: 20  
```  
  
## <a name="see-also"></a>Zobacz też  
 [We/Wy niskiego poziomu](../../c-runtime-library/low-level-i-o.md)   
 [ftell —, _ftelli64 —](../../c-runtime-library/reference/ftell-ftelli64.md)   
 [_lseek —, _lseeki64 —](../../c-runtime-library/reference/lseek-lseeki64.md)