---
title: "_heapadd — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _heapadd
apilocation:
- msvcr100.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr80.dll
- msvcrt.dll
- msvcr110.dll
- msvcr90.dll
apitype: DLLExport
f1_keywords:
- heapadd
- _heapadd
dev_langs:
- C++
helpviewer_keywords:
- _heapadd function
- memory, adding to heaps
- heaps, adding memory
- heapadd function
ms.assetid: 4d691fe2-2763-49f4-afb1-62738b7cd3ff
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 9c046f9e26848edbbc609b9f3c729a0654fe3718
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="heapadd"></a>_heapadd
Dodaje pamięci sterty.  
  
> [!IMPORTANT]
>  Ta funkcja jest przestarzała. Począwszy od programu Visual Studio 2015, nie jest dostępna w CRT.  
  
## <a name="syntax"></a>Składnia  
  
```  
int _heapadd(   
   void *memblock,  
   size_t size   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `memblock`  
 Wskaźnik do pamięci sterty.  
  
 `size`  
 Rozmiar pamięci, aby dodać w bajtach.  
  
## <a name="return-value"></a>Wartość zwracana  
 W przypadku powodzenia `_heapadd` zwraca 0; w przeciwnym razie funkcja zwraca wartość -1 i ustawia `errno` do `ENOSYS`.  
  
 Aby uzyskać więcej informacji dotyczących tego i innych kody powrotu, zobacz [_doserrno —, errno, _sys_errlist — i _sys_nerr —](../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
## <a name="remarks"></a>Uwagi  
 Począwszy od programu Visual C++ w wersji 4.0, wewnętrzna struktura sterty został przeniesiony do biblioteki wykonawcze języka C do obsługi nowych funkcji debugowania. W związku z tym `_heapadd` nie jest obsługiwane na dowolnej platformie, który jest oparty na interfejsie API Win32.  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|Opcjonalne nagłówki|  
|-------------|---------------------|---------------------|  
|`_heapadd`|\<malloc.h >|\<errno.h >|  
  
 Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../c-runtime-library/compatibility.md) we wprowadzeniu.  
  
## <a name="see-also"></a>Zobacz też  
 [Alokacja pamięci](../c-runtime-library/memory-allocation.md)   
 [w warstwie bezpłatna](../c-runtime-library/reference/free.md)   
 [_heapchk —](../c-runtime-library/reference/heapchk.md)   
 [_heapmin —](../c-runtime-library/reference/heapmin.md)   
 [_heapset —](../c-runtime-library/heapset.md)   
 [_heapwalk —](../c-runtime-library/reference/heapwalk.md)   
 [— funkcja malloc](../c-runtime-library/reference/malloc.md)   
 [realloc](../c-runtime-library/reference/realloc.md)