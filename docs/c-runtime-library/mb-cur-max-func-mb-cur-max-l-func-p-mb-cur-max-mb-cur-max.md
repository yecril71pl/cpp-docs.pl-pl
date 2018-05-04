---
title: ___mb_cur_max_func, ___mb_cur_max_l_func, __p___mb_cur_max, __mb_cur_max | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
apiname:
- ___mb_cur_max_l_func
- __p___mb_cur_max
- ___mb_cur_max_func
- __mb_cur_max
apilocation:
- msvcr110_clr0400.dll
- msvcr110.dll
- msvcr80.dll
- msvcr100.dll
- msvcrt.dll
- msvcr90.dll
- msvcr120.dll
apitype: DLLExport
f1_keywords:
- ___mb_cur_max_func
- ___mb_cur_max_l_func
- __p___mb_cur_max
- __mb_cur_max
dev_langs:
- C++
helpviewer_keywords:
- __mb_cur_max
- ___mb_cur_max_func
- ___mb_cur_max_l_func
- __p___mb_cur_max
ms.assetid: 60d36108-1ca7-45a6-8ce7-68a91f13e3a1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2ea2a6d07a6664b74abaa1513a39f8f908f72fa1
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="mbcurmaxfunc-mbcurmaxlfunc-pmbcurmax-mbcurmax"></a>___mb_cur_max_func, ___mb_cur_max_l_func, __p___mb_cur_max, __mb_cur_max
Funkcji CRT wewnętrznej. Pobiera maksymalną liczbę bajtów w znaków wielobajtowych dla ustawień regionalnych bieżącego lub został określony.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
int ___mb_cur_max_func(void);  
int ___mb_cur_max_l_func(_locale_t locale);  
int * __p___mb_cur_max(void);  
#define __mb_cur_max (___mb_cur_max_func())  
```  
  
#### <a name="parameters"></a>Parametry  
 locale  
 Struktura ustawień regionalnych, które można pobrać wyników z. Jeśli ta wartość jest równa null, używana jest bieżące ustawienia regionalne wątku.  
  
## <a name="return-value"></a>Wartość zwracana  
 Maksymalna liczba bajtów w znaków wielobajtowych dla bieżącego ustawienia regionalne wątku lub określone ustawienia regionalne.  
  
## <a name="remarks"></a>Uwagi  
 Jest to wewnętrzny użycia funkcji CRT można pobrać bieżącą wartość [mb_cur_max —](../c-runtime-library/mb-cur-max.md) makro z magazynu lokalnego wątku. Firma Microsoft zaleca użycie `MB_CUR_MAX` makra w kodzie przenośności.  
  
 `__mb_cur_max` Makro jest wygodny sposób wywołania `___mb_cur_max_func()` funkcji. `__p___mb_cur_max` Funkcji jest zdefiniowany dla zgodności z programu Visual C++ 5.0 i wcześniejszych wersjach.  
  
 Funkcje CRT wewnętrznej są specyficzne dla implementacji i może ulec zmianie z każdym wersję. Nie zaleca się ich użycie w kodzie.  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`___mb_cur_max_func`, `___mb_cur_max_l_func`, `__p___mb_cur_max`|\<CType.h >, \<stdlib.h >|  
  
## <a name="see-also"></a>Zobacz też  
 [MB_CUR_MAX](../c-runtime-library/mb-cur-max.md)