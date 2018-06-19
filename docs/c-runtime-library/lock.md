---
title: _Lock | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f9a518402d027ae128fcf403752fafb448461628
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32390472"
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
 [in] `locknum`  
 Identyfikator blokady do uzyskania dostępu.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli już uzyskano blokady, ta metoda uzyskuje blokadę mimo to i powoduje, że wystąpił błąd wewnętrzny C czasu wykonywania (CRT). Jeśli metoda nie może uzyskać blokady, kończy działanie z powodu błędu krytycznego i ustawia kod błędu: `_RT_LOCK`.  
  
## <a name="requirements"></a>Wymagania  
 **Źródło:** mlock.c  
  
## <a name="see-also"></a>Zobacz też  
 [Alfabetyczne odwołanie funkcji](../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [_unlock](../c-runtime-library/unlock.md)