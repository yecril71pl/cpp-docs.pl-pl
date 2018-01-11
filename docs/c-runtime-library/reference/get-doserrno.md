---
title: "_get_doserrno — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _get_doserrno
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
- _get_doserrno
- get_doserrno
dev_langs: C++
helpviewer_keywords:
- get_doserrno function
- _get_doserrno function
ms.assetid: 7fec7be3-6e39-4181-846b-8ef24489361c
caps.latest.revision: "19"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: c8eff0ac1a97c9a1d48b82601eb0d6dc0bb8bed0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="getdoserrno"></a>_get_doserrno
Pobiera wartość błędu zwrócony przez system operacyjny, zanim jest przekształcana na `errno` wartość.  
  
## <a name="syntax"></a>Składnia  
  
```  
errno_t _get_doserrno(   
   int * pValue   
);   
```  
  
#### <a name="parameters"></a>Parametry  
 [out]`pValue`  
 Wskaźnik do wartości całkowitej, należy podać bieżącą wartość `_doserrno` makro globalnego.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli `_get_doserrno` zakończy się powodzeniem, zwraca zero; w przypadku niepowodzenia zwraca kod błędu. Jeśli `pValue` jest `NULL`, program obsługi nieprawidłowych parametrów zostanie wywołany, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może kontynuować, ta funkcja ustawia `errno` do `EINVAL` i zwraca `EINVAL`.  
  
## <a name="remarks"></a>Uwagi  
 `_doserrno` Globalne makro jest ustawione na zero podczas inicjowania CRT, zanim proces rozpoczyna się wykonanie. Ma ustawioną wartość błędu systemu operacyjnego zwracanych przez każde wywołanie funkcji na poziomie systemu, która zwraca błąd systemu operacyjnego, i jest nigdy nie jest resetowany do zera podczas wykonywania. Podczas pisania kodu, aby sprawdzić wartość błędu zwrócony przez funkcję, zawsze wyczyść `_doserrno` za pomocą [_set_doserrno —](../../c-runtime-library/reference/set-doserrno.md) przed wywołaniem funkcji. Ponieważ mogą zastąpić inne wywołanie funkcji `_doserrno`, sprawdź wartość przy użyciu `_get_doserrno` natychmiast po wywołaniu funkcji.  
  
 Firma Microsoft zaleca [_get_errno —](../../c-runtime-library/reference/get-errno.md) zamiast `_get_doserrno` kodów błędów przenośnej.  
  
 Możliwe wartości `_doserrno` są zdefiniowane w \<errno.h >.  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|Opcjonalne nagłówki|  
|-------------|---------------------|---------------------|  
|`_get_doserrno`|\<stdlib.h >, \<cstdlib — > (C++)|\<errno.h >, \<cerrno — > (C++)|  
  
 `_get_doserrno`to rozszerzenie firmy Microsoft. Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).  
  
## <a name="see-also"></a>Zobacz też  
 [_set_doserrno —](../../c-runtime-library/reference/set-doserrno.md)   
 [errno, _doserrno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)