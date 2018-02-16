---
title: _query_new_mode | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- _query_new_mode
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
- query_new_mode
- _query_new_mode
dev_langs:
- C++
helpviewer_keywords:
- query_new_mode function
- handler modes
- _query_new_mode function
ms.assetid: e185c5f9-b73b-4257-8eff-b47648374768
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: cbbdec8c5a8cd9af5e6a17518cc40bca455b3f98
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2018
---
# <a name="querynewmode"></a>_query_new_mode
Zwraca liczbę całkowitą wskazującą nowy tryb obsługi ustawione przez `_set_new_mode` dla `malloc`.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
      int _query_new_mode(  
   void   
);  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca bieżący nowy tryb obsługi, a mianowicie 0 lub 1, `malloc`. Zwracana wartość 1 oznacza, że, nie można przydzielić pamięci, `malloc` wywołuje nowe procedury obsługi; wartość zwracana 0 wskazuje, nie ma.  
  
## <a name="remarks"></a>Uwagi  
 C++ `_query_new_mode` funkcja zwróci liczbę całkowitą wskazującą nowy tryb obsługi, który jest uporządkowany według języka C++ [_set_new_mode —](../../c-runtime-library/reference/set-new-mode.md) działać w ramach [— funkcja malloc](../../c-runtime-library/reference/malloc.md). Nowy tryb obsługi wskazuje, czy w przypadku awarii można przydzielić pamięci, `malloc` jest wywołanie nowe procedury obsługi zgodnie z ustawieniami [_set_new_handler —](../../c-runtime-library/reference/set-new-handler.md). Domyślnie `malloc` nie wywołuje nowe procedury obsługi w przypadku awarii. Można użyć `_set_new_mode` Aby zmienić to zachowanie, tak że w przypadku niepowodzenia `malloc` wywołuje nowe procedury obsługi, w tym samym jak robi **nowe** operator nie w przypadku niepowodzenia można przydzielić pamięci. Aby uzyskać więcej informacji, zobacz Omówienie [nowy i delete — operatory](../../cpp/new-and-delete-operators.md) w dokumentacja języka C++.  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`_query_new_mode`|\<new.h>|  
  
 Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md) we wprowadzeniu.  
  
## <a name="libraries"></a>Biblioteki  
 Wszystkie wersje [biblioteki wykonawcze języka C](../../c-runtime-library/crt-library-features.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Alokacja pamięci](../../c-runtime-library/memory-allocation.md)   
 [calloc](../../c-runtime-library/reference/calloc.md)   
 [W warstwie bezpłatna](../../c-runtime-library/reference/free.md)   
 [realloc](../../c-runtime-library/reference/realloc.md)   
 [_query_new_handler](../../c-runtime-library/reference/query-new-handler.md)