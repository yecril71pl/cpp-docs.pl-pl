---
title: "_get_pgmptr — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _get_pgmptr
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
- api-ms-win-crt-runtime-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- get_pgmptr
- _get_pgmptr
dev_langs: C++
helpviewer_keywords:
- get_pgmptr function
- _get_pgmptr function
- pgmptr global variable
- _pgmptr global variable
ms.assetid: 29f16a9f-a685-4721-add3-7fad4f67eece
caps.latest.revision: "15"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 962d6198a9daeeca0a79a814da11d1d60438d18f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="getpgmptr"></a>_get_pgmptr
Pobiera bieżącą wartość `_pgmptr` zmiennej globalnej.  
  
## <a name="syntax"></a>Składnia  
  
```  
errno_t _get_pgmptr(   
   char **pValue   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 [out]`pValue`  
 Wskaźnik do ciągu należy podać bieżącą wartość `_pgmptr` zmiennej.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość zero w przypadku powodzenia; błąd o kodzie błędu. Jeśli `pValue` jest `NULL`, zgodnie z opisem w wywołaniu program obsługi nieprawidłowych parametrów [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może kontynuować, ta funkcja ustawia `errno` do `EINVAL` i zwraca `EINVAL`.  
  
## <a name="remarks"></a>Uwagi  
 `_pgmptr` — Zmienna globalna zawiera pełną ścieżkę do pliku wykonywalnego skojarzonych z procesem. Aby uzyskać więcej informacji, zobacz [_pgmptr —, _wpgmptr —](../../c-runtime-library/pgmptr-wpgmptr.md).  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`_get_pgmptr`|\<stdlib.h >|  
  
 Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md) we wprowadzeniu.  
  
## <a name="see-also"></a>Zobacz też  
 [_get_wpgmptr](../../c-runtime-library/reference/get-wpgmptr.md)