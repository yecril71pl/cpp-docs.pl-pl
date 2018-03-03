---
title: ___lc_collate_cp_func | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- ___lc_collate_cp_func
apilocation:
- msvcr120.dll
- msvcrt.dll
- msvcr100.dll
- msvcr80.dll
- msvcr110_clr0400.dll
- msvcr110.dll
- msvcr90.dll
apitype: DLLExport
f1_keywords:
- ___lc_collate_cp_func
dev_langs:
- C++
helpviewer_keywords:
- ___lc_collate_cp_func
ms.assetid: 46ccc084-7ac9-4e5d-9138-e12cb5845615
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: fe7ff6ce073f84a87e2243ab98d3b99af0dfd22c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="lccollatecpfunc"></a>___lc_collate_cp_func
Funkcji CRT wewnętrznej. Pobiera bieżącej stronie kodowej sortowania wątku.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
UINT ___lc_codepage_func(void);  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 Bieżąca strona kodowa sortowania wątku.  
  
## <a name="remarks"></a>Uwagi  
 `___lc_collate_cp_func`jest wewnętrzny funkcji CRT, która jest używana przez inne funkcje CRT można uzyskać z magazynu lokalnego wątku CRT danych bieżącej stronie kodowej sortowania. Informacje te są również dostępne za pomocą [_get_current_locale —](../c-runtime-library/reference/get-current-locale.md) funkcji.  
  
 Funkcje CRT wewnętrznej są specyficzne dla implementacji i może ulec zmianie z każdym wersję. Nie zaleca się ich użycie w kodzie.  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`___lc_collate_cp_func`|crt\src\setlocal.h|  
  
## <a name="see-also"></a>Zobacz też  
 [_get_current_locale —](../c-runtime-library/reference/get-current-locale.md)   
 [setLocale, _wsetlocale —](../c-runtime-library/reference/setlocale-wsetlocale.md)   
 [_create_locale, _wcreate_locale](../c-runtime-library/reference/create-locale-wcreate-locale.md)   
 [_free_locale](../c-runtime-library/reference/free-locale.md)