---
title: _setmaxstdio | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- _setmaxstdio
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
- setmaxstdio
- _setmaxstdio
dev_langs:
- C++
helpviewer_keywords:
- maximum open files
- _setmaxstdio function
- setmaxstdio function
- open files, maximum
ms.assetid: 9e966875-9ff5-47c4-9b5f-e79e83b70249
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 5317437202cef423759ac850aab2360892521746
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2018
---
# <a name="setmaxstdio"></a>_setmaxstdio
Ustawia maksymalną liczbę równocześnie otwarte pliki w `stdio` poziom.  
  
## <a name="syntax"></a>Składnia  
  
```  
int _setmaxstdio(  
   int newmax   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `newmax`  
 Nowe maksymalną liczbę równocześnie otwarte pliki w `stdio` poziom.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca `newmax` w przypadku powodzenia; w przeciwnym razie -1.  
  
 Jeśli `newmax` jest mniejsza niż `_IOB_ENTRIES` lub nowszej, a następnie wywołać maksymalna liczba dojść do dostępnych w systemie, program obsługi nieprawidłowych parametrów, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli jest dozwolone wykonywanie, aby kontynuować, ta funkcja zwraca wartość -1 i zestawy `errno` do `EINVAL`.  
  
 Aby uzyskać informacje na temat tych i innych kodów błędów, zobacz [_doserrno —, errno, _sys_errlist — i _sys_nerr —](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
## <a name="remarks"></a>Uwagi  
 `_setmaxstdio` Funkcji zmienia się wartość maksymalna liczba plików, które mogą być jednocześnie otwarte `stdio` poziom.  
  
 C czasu wykonywania operacji We/Wy teraz obsługuje wiele więcej otwartych plików na platformach Win32 niż w poprzednich wersjach. Maksymalnie 2048 pliki można otworzyć jednocześnie w [poziom lowio](../../c-runtime-library/low-level-i-o.md) (oznacza to, że otwarte i dostępne za pomocą klasy `_open`, `_read`, `_write`itd rodzinnych funkcje We/Wy). Maksymalnie 512 pliki można otworzyć jednocześnie na [stdio — poziom](../../c-runtime-library/stream-i-o.md) (oznacza to, że otwarte i dostępne za pomocą klasy `fopen`, `fgetc`, `fputc`, rodziny i funkcji). Limit równy 512 otwarte pliki w `stdio` maksymalnie 2048 za pomocą klasy można zwiększyć poziom `_setmaxstdio` funkcji.  
  
 Ponieważ `stdio`-poziomu funkcji, takich jak `fopen`, są tworzone nad `lowio` funkcje, jest maksymalnie 2048 twardych górny limit liczby jednocześnie otwarte pliki dostępne za pośrednictwem biblioteki wykonawczej języka C.  
  
> [!NOTE]
>  Tego limitu górnego może być poza to, co jest obsługiwana przez konkretnego platformy Win32 i konfiguracji.  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`_setmaxstdio`|\<stdio.h>|  
  
 Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md) we wprowadzeniu.  
  
## <a name="example"></a>Przykład  
 Zobacz [_getmaxstdio —](../../c-runtime-library/reference/getmaxstdio.md) przykład przy użyciu `_setmaxstdio`.  
  
## <a name="see-also"></a>Zobacz też  
 [We/Wy strumienia](../../c-runtime-library/stream-i-o.md)