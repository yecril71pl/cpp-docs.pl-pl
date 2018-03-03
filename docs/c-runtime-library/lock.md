---
title: _Lock | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _lock
apilocation:
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr100.dll
- msvcr90.dll
- msvcr80.dll
- msvcr110.dll
- msvcrt.dll
- msvcr120_clr0400.dll
apitype: DLLExport
f1_keywords:
- lock
- _lock
dev_langs:
- C++
helpviewer_keywords:
- lock function
- _lock function
ms.assetid: 29f77c37-30de-4b3d-91b6-030216e645a6
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 069a13626c2fcfab62c47d3142f2f5b810f0945a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="lock"></a>_lock
Uzyskuje blokadę wielu wątków.  
  
> [!IMPORTANT]
>  Ta funkcja jest przestarzała. Począwszy od programu Visual Studio 2015, nie jest dostępna w CRT.  
  
## <a name="syntax"></a>Składnia  
  
```  
void __cdecl _lock  
   int locknum  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 [in]`locknum`  
 Identyfikator blokady do uzyskania dostępu.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli już uzyskano blokady, ta metoda uzyskuje blokadę mimo to i powoduje, że wystąpił błąd wewnętrzny C czasu wykonywania (CRT). Jeśli metoda nie może uzyskać blokady, kończy działanie z powodu błędu krytycznego i ustawia kod błędu: `_RT_LOCK`.  
  
## <a name="requirements"></a>Wymagania  
 **Źródło:** mlock.c  
  
## <a name="see-also"></a>Zobacz też  
 [Alfabetyczne odwołanie funkcji](../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [_unlock](../c-runtime-library/unlock.md)