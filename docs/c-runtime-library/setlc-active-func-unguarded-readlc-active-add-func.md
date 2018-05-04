---
title: ___setlc_active_func, ___unguarded_readlc_active_add_func | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
apiname:
- ___setlc_active_func
- ___unguarded_readlc_active_add_func
apilocation:
- msvcr90.dll
- msvcr110_clr0400.dll
- msvcrt.dll
- msvcr110.dll
- msvcr80.dll
- msvcr120.dll
- msvcr100.dll
apitype: DLLExport
f1_keywords:
- ___unguarded_readlc_active_add_func
- ___setlc_active_func
dev_langs:
- C++
helpviewer_keywords:
- ___setlc_active_func
- ___unguarded_readlc_active_add_func
ms.assetid: 605ec4e3-81e5-4ece-935a-f434768cc702
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 532aac2e47a402ae04ba4d4bf4fcb133c997bd31
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="setlcactivefunc-unguardedreadlcactiveaddfunc"></a>___setlc_active_func, ___unguarded_readlc_active_add_func
OBSOLETE. CRT eksportuje tych funkcji wewnętrznych, tylko w celu zachowania zgodności plików binarnych.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
int ___setlc_active_func(void);  
int * ___unguarded_readlc_active_add_func(void);  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 Wartość zwracana nie ma znaczenia.  
  
## <a name="remarks"></a>Uwagi  
 Chociaż funkcje CRT wewnętrznej `___setlc_active_func` i `___unguarded_readlc_active_add_func` są przestarzałe i nie jest już używane, są one eksportowane przez bibliotekę CRT w celu zachowania zgodności plików binarnych. Pierwotnym celem `___setlc_active_func` było zwrócenie liczby aktywnych wywołań `setlocale` funkcji. Pierwotnym celem `___unguarded_readlc_active_add_func` było zwrócenie liczby funkcji, które odwołuje się do ustawień regionalnych bez blokowania go.  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`___setlc_active_func`, `___unguarded_readlc_active_add_func`|brak|  
  
## <a name="see-also"></a>Zobacz też  
 [setlocale, _wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)