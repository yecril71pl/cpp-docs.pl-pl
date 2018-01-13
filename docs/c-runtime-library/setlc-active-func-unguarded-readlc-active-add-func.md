---
title: ___setlc_active_func, ___unguarded_readlc_active_add_func | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
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
dev_langs: C++
helpviewer_keywords:
- ___setlc_active_func
- ___unguarded_readlc_active_add_func
ms.assetid: 605ec4e3-81e5-4ece-935a-f434768cc702
caps.latest.revision: "5"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 0a1ecc14403a7a08fed73fb10f15dd25051b0a28
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="setlcactivefunc-unguardedreadlcactiveaddfunc"></a>___setlc_active_func, ___unguarded_readlc_active_add_func
PRZESTARZAŁE. CRT eksportuje tych funkcji wewnętrznych, tylko w celu zachowania zgodności plików binarnych.  
  
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