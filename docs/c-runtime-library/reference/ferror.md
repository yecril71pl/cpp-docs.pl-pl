---
title: "ferror — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- ferror
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
- ferror
dev_langs:
- C++
helpviewer_keywords:
- ferror function
- streams, testing for errors
- errors [C++], testing for stream
ms.assetid: 528a34bc-f2aa-4c3f-b89a-5b148e6864f7
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 7db390539df0761aacdb11de5eace58b2c9c87f8
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2018
---
# <a name="ferror"></a>ferror
Testy wystąpił błąd w strumieniu.  
  
## <a name="syntax"></a>Składnia  
  
```  
int ferror(   
   FILE *stream   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `stream`  
 Wskaźnik do `FILE` struktury.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli błąd nie wystąpił na `stream`, `ferror` zwraca wartość 0. W przeciwnym wypadku zwraca wartość różną od zera. W przypadku strumienia `NULL`, `ferror` wywołuje program obsługi nieprawidłowych parametrów, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może kontynuować, ta funkcja ustawia `errno` do `EINVAL` i zwraca wartość 0.  
  
 Zobacz [_doserrno —, errno, _sys_errlist — i _sys_nerr —](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) Aby uzyskać więcej informacji na temat tych i innych kodów błędów.  
  
## <a name="remarks"></a>Uwagi  
 `ferror` Procedura (zaimplementowano funkcji oraz w makrze) testów dla odczytu lub zapisu błędu w pliku skojarzone z `stream`. Jeśli wystąpi błąd, wskaźnik błędów dla strumienia pozostaje Ustaw dopóki strumień jest zamknięty lub przewinięta lub do czasu `clearerr` nazywa się przed nim.  
  
## <a name="requirements"></a>Wymagania  
  
|Funkcja|Wymagany nagłówek|  
|--------------|---------------------|  
|`ferror`|\<stdio.h>|  
  
 Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md) we wprowadzeniu.  
  
## <a name="example"></a>Przykład  
 Zobacz przykład [feof —](../../c-runtime-library/reference/feof.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Obsługa błędów](../../c-runtime-library/error-handling-crt.md)   
 [We/Wy strumienia](../../c-runtime-library/stream-i-o.md)   
 [clearerr —](../../c-runtime-library/reference/clearerr.md)   
 [_eof —](../../c-runtime-library/reference/eof.md)   
 [feof —](../../c-runtime-library/reference/feof.md)   
 [fopen —, _wfopen —](../../c-runtime-library/reference/fopen-wfopen.md)   
 [perror, _wperror](../../c-runtime-library/reference/perror-wperror.md)