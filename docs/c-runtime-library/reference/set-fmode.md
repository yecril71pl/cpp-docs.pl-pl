---
title: "_set_fmode — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _set_fmode
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
- _set_fmode
- set_fmode
dev_langs: C++
helpviewer_keywords:
- file translation [C++], default mode
- _set_fmode function
- file translation [C++], setting mode
- set_fmode function
ms.assetid: f80eb9c7-733b-4652-a9bc-6b3790a35f12
caps.latest.revision: "19"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 317f4ac24d44008f58deeb62e8362b2d09d8309a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="setfmode"></a>_set_fmode
Ustawia domyślny tryb tłumaczenia pliku dla operacji We/Wy pliku.  
  
## <a name="syntax"></a>Składnia  
  
```  
errno_t _set_fmode(   
   int mode   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 [in]`mode`  
 Tryb tłumaczenia pliku żądanego: `_O_TEXT` lub `_O_BINARY`.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość zero, jeśli to się powiedzie, kod błędu w przypadku awarii. Jeśli `mode` nie jest `_O_TEXT` lub `_O_BINARY` lub `_O_WTEXT`, program obsługi nieprawidłowych parametrów zostanie wywołany, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może kontynuować, ta funkcja ustawia `errno` do `EINVAL` i zwraca `EINVAL`.  
  
## <a name="remarks"></a>Uwagi  
 Zestawy funkcji [_fmode —](../../c-runtime-library/fmode.md) zmiennej globalnej. Ta zmienna Określa domyślny tryb tłumaczenia pliku dla operacji We/Wy pliku `_open` i `_pipe`.  
  
 `_O_TEXT`i `_O_BINARY` są zdefiniowane w Fcntl.h. `EINVAL`jest zdefiniowany w Errno.h.  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|Opcjonalne nagłówki|  
|-------------|---------------------|---------------------|  
|`_set_fmode`|\<stdlib.h >|\<fcntl.h >, \<errno.h >|  
  
 Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md) we wprowadzeniu.  
  
## <a name="example"></a>Przykład  
  
```  
// crt_set_fmode.c  
#include <stdlib.h>  
#include <stdio.h>  
#include <fcntl.h>     /* for _O_TEXT and _O_BINARY */  
#include <errno.h>     /* for EINVAL */  
#include <sys\stat.h>  /* for _S_IWRITE */  
#include <share.h>     /* for _SH_DENYNO */  
  
int main()  
{  
   int mode, fd, ret;  
   errno_t err;  
   int buf[12] = { 65, 66, 67, 68, 69, 70, 71, 72, 73, 74,  
                   75, 76 };  
   char * filename = "fmode.out";  
  
   err = _get_fmode(&mode);  
   if (err == EINVAL)  
   {  
      printf( "Invalid parameter: mode\n");  
      return 1;  
   }  
   else  
      printf( "Default Mode is %s\n", mode == _O_TEXT ? "text" :  
              "binary");  
  
   err = _set_fmode(_O_BINARY);  
   if (err == EINVAL)  
   {  
      printf( "Invalid mode.\n");  
      return 1;  
   }  
  
   if ( _sopen_s(&fd, filename, _O_RDWR | _O_CREAT, _SH_DENYNO, _S_IWRITE | _S_IREAD) != 0 )  
   {  
      printf( "Error opening the file %s\n", filename);  
      return 1;  
   }  
  
   if (ret = _write(fd, buf, 12*sizeof(int)) < 12*sizeof(int))  
   {  
      printf( "Problem writing to the file %s.\n", filename);  
      printf( "Number of bytes written: %d\n", ret);  
   }  
  
   if (_close(fd) != 0)  
   {  
      printf("Error closing the file %s. Error code %d.\n",  
             filename, errno);  
   }  
  
   system("type fmode.out");  
}  
```  
  
```Output  
Default Mode is binary  
A   B   C   D   E   F   G   H   I   J   K   L     
```  
  
## <a name="see-also"></a>Zobacz też  
 [_fmode —](../../c-runtime-library/fmode.md)   
 [_get_fmode —](../../c-runtime-library/reference/get-fmode.md)   
 [_setmode —](../../c-runtime-library/reference/setmode.md)   
 [We/Wy pliku w trybie binarnym i tekstowym](../../c-runtime-library/text-and-binary-mode-file-i-o.md)