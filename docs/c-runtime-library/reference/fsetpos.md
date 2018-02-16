---
title: "fsetpos — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- fsetpos
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
- fsetpos
dev_langs:
- C++
helpviewer_keywords:
- streams, setting position indicators
- fsetpos function
ms.assetid: 6d19ff48-1a2b-47b3-9f23-ed0a47b5a46e
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 483cf151374c1c3a03e53e49ce67a00a148406fd
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2018
---
# <a name="fsetpos"></a>fsetpos
Ustawia wskaźnik pozycji w strumieniu.  
  
## <a name="syntax"></a>Składnia  
  
```  
int fsetpos(   
   FILE *stream,  
   const fpos_t *pos   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `stream`  
 Wskaźnik do `FILE` struktury.  
  
 `pos`  
 Wskaźnik położenia magazynu.  
  
## <a name="return-value"></a>Wartość zwracana  
 W przypadku powodzenia `fsetpos` zwraca wartość 0. W przypadku awarii, funkcja zwraca wartość różną od zera i ustawia `errno` do jednej z następujących manifestu — stałe (zdefiniowany w numer błędu. H): `EBADF`, co oznacza, że plik nie jest dostępny lub obiekt który `stream` punktów nie jest prawidłowym plikiem strukturą; lub `EINVAL`, co oznacza nieprawidłową wartość dla `stream` lub `pos` został przekazany. Jeśli przekazano nieprawidłowy parametr tych funkcji Wywołaj program obsługi nieprawidłowych parametrów, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md).  
  
 Zobacz [_doserrno —, errno, _sys_errlist — i _sys_nerr —](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) kody powrotne — Aby uzyskać więcej informacji na temat tych i innych.  
  
## <a name="remarks"></a>Uwagi  
 `fsetpos` Funkcja ustawia wskaźnik położenia pliku `stream` wartość `pos`, jest uzyskiwany wcześniejszym wywołaniu `fgetpos` przed `stream`. Funkcja usuwa plik końcowy wskaźnika i cofa efekty [ungetc —](../../c-runtime-library/reference/ungetc-ungetwc.md) na `stream`. Po wywołaniu `fsetpos`, następnej operacji na `stream` mogą być danych wejściowych lub wyjściowych.  
  
## <a name="requirements"></a>Wymagania  
  
|Funkcja|Wymagany nagłówek|  
|--------------|---------------------|  
|`fsetpos`|\<stdio.h>|  
  
 Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md) we wprowadzeniu.  
  
## <a name="example"></a>Przykład  
 Zobacz przykład [fgetpos —](../../c-runtime-library/reference/fgetpos.md).  
  
## <a name="see-also"></a>Zobacz też  
 [We/Wy strumienia](../../c-runtime-library/stream-i-o.md)   
 [fgetpos](../../c-runtime-library/reference/fgetpos.md)