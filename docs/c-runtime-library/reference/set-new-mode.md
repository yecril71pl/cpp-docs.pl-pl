---
title: "_set_new_mode — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _set_new_mode
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
- set_new_mode
- _set_new_mode
dev_langs: C++
helpviewer_keywords:
- handler modes
- _set_new_mode function
- set_new_mode function
ms.assetid: 4d14039a-e54e-4689-8c70-74a4b9834768
caps.latest.revision: "14"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 31fb5217c70c41e633fffc69cd05624366fa29eb
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="setnewmode"></a>_set_new_mode
Ustawia tryb obsługi nowych `malloc`.  
  
## <a name="syntax"></a>Składnia  
  
```  
int _set_new_mode(  
   int newhandlermode   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `newhandlermode`  
 Nowy tryb obsługi dla `malloc`; prawidłowe wartości to 0 lub 1.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca poprzednią procedurę obsługi trybu zestawie `malloc`. Zwracana wartość 1 oznacza, że, nie można przydzielić pamięci, `malloc` wcześniej nazywane nowe procedury obsługi; wartość zwracana 0 wskazuje nie zostało. Jeśli `newhandlermode` argument nie jest równa 0 lub 1, zwraca -1.  
  
## <a name="remarks"></a>Uwagi  
 C++ `_set_new_mode` funkcja ustawia tryb obsługi nowych [— funkcja malloc](../../c-runtime-library/reference/malloc.md). Nowy tryb obsługi wskazuje, czy w przypadku awarii, `malloc` jest wywołanie nowe procedury obsługi zgodnie z ustawieniami [_set_new_handler —](../../c-runtime-library/reference/set-new-handler.md). Domyślnie `malloc` nie wywołuje nowe procedury obsługi nie można przydzielić pamięci. Można zastąpić to zachowanie domyślne, aby, gdy `malloc` nie może przydzielić pamięci, `malloc` wywołuje nowe procedury obsługi tak samo jak robi `new` operator nie w przypadku niepowodzenia tego samego powodu. Aby uzyskać więcej informacji, zobacz [nowe](../../cpp/new-operator-cpp.md) i [usunąć](../../cpp/delete-operator-cpp.md) operatory w *dokumentacja języka C++*. Aby zastąpić domyślną, należy wywołać:  
  
```  
_set_new_mode(1)  
```  
  
 wczesne programu w lub Połącz z Newmode.obj (zobacz [opcje łącza](../../c-runtime-library/link-options.md)).  
  
 Ta funkcja weryfikuje jej parametr. Jeśli `newhandlermode` żadnych innych niż 0 lub 1, funkcja wywołuje program obsługi nieprawidłowych parametrów, jak opisano w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli jest dozwolone wykonywanie, aby kontynuować, **_** `set_new_mode` zwraca wartość -1 i ustawia `errno` do `EINVAL`.  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`_set_new_mode`|\<New.h >|  
  
 Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md) we wprowadzeniu.  
  
## <a name="see-also"></a>Zobacz też  
 [Alokacja pamięci](../../c-runtime-library/memory-allocation.md)   
 [calloc —](../../c-runtime-library/reference/calloc.md)   
 [w warstwie bezpłatna](../../c-runtime-library/reference/free.md)   
 [realloc](../../c-runtime-library/reference/realloc.md)   
 [_query_new_handler —](../../c-runtime-library/reference/query-new-handler.md)   
 [_query_new_mode](../../c-runtime-library/reference/query-new-mode.md)