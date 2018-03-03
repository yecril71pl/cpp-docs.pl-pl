---
title: _Unlock | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _unlock
apilocation:
- msvcrt.dll
- msvcr100.dll
- msvcr110_clr0400.dll
- msvcr110.dll
- msvcr80.dll
- msvcr120.dll
- msvcr90.dll
- msvcr120_clr0400.dll
apitype: DLLExport
f1_keywords:
- unlock
- _unlock
dev_langs:
- C++
helpviewer_keywords:
- unlock function
- _unlock function
ms.assetid: 2eda2507-a134-4997-aa12-f2f8cb319e14
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e057bb0ee2b9e90d111ec4ba8b5783d9f8c32738
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="unlock"></a>_unlock
Zwalnia blokadę wielu wątków.  
  
> [!IMPORTANT]
>  Ta funkcja jest przestarzała. Począwszy od programu Visual Studio 2015, nie jest dostępna w CRT.  
  
## <a name="syntax"></a>Składnia  
  
```  
void __cdecl _unlock(  
   int locknum  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 [in]`locknum`  
 Identyfikator blokady do zwolnienia.  
  
## <a name="requirements"></a>Wymagania  
 **Źródło:** mlock.c  
  
## <a name="see-also"></a>Zobacz też  
 [Alfabetyczne odwołanie funkcji](../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [_lock](../c-runtime-library/lock.md)