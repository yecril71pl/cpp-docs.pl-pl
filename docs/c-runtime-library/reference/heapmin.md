---
title: "_heapmin — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _heapmin
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
- api-ms-win-crt-heap-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _heapmin
- heapmin
dev_langs: C++
helpviewer_keywords:
- heap memory
- minimizing heaps
- memory, releasing
- heaps, releasing unused memory
- _heapmin function
- heapmin function
ms.assetid: c0bccdf6-2d14-4d7b-a7ff-d6a17bdb410f
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 1318e8d18ddeb5031efdf3066f9fa3020c8e9afd
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="heapmin"></a>_heapmin
Zwalnia pamięć sterty nieużywane do systemu operacyjnego.  
  
## <a name="syntax"></a>Składnia  
  
```  
int _heapmin( void );  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 W przypadku powodzenia `_heapmin` zwraca 0; w przeciwnym razie funkcja zwraca wartość -1 i ustawia `errno` do `ENOSYS`.  
  
 Aby uzyskać więcej informacji dotyczących tego i innych kody powrotu, zobacz [_doserrno —, errno, _sys_errlist — i _sys_nerr —](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
## <a name="remarks"></a>Uwagi  
 `_heapmin` Funkcja minimalizuje sterty, zwalniając pamięć sterty nieużywane do systemu operacyjnego. Jeśli system operacyjny nie obsługuje `_heapmin`(na przykład Windows 98), funkcja zwraca wartość -1 i ustawia `errno` do `ENOSYS`.  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|Opcjonalne nagłówki|  
|-------------|---------------------|---------------------|  
|`_heapmin`|\<malloc.h >|\<errno.h >|  
  
 Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md) we wprowadzeniu.  
  
## <a name="see-also"></a>Zobacz też  
 [Alokacja pamięci](../../c-runtime-library/memory-allocation.md)   
 [w warstwie bezpłatna](../../c-runtime-library/reference/free.md)   
 [_heapadd —](../../c-runtime-library/heapadd.md)   
 [_heapchk —](../../c-runtime-library/reference/heapchk.md)   
 [_heapset —](../../c-runtime-library/heapset.md)   
 [_heapwalk —](../../c-runtime-library/reference/heapwalk.md)   
 [— funkcja malloc](../../c-runtime-library/reference/malloc.md)