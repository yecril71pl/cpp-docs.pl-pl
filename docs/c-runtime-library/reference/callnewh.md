---
title: _callnewh | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _callnewh
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
f1_keywords: _callnewh
dev_langs: C++
helpviewer_keywords: _callnewh
ms.assetid: 4dcb73e9-6384-4d12-a973-a8807d4de7a8
caps.latest.revision: "3"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 86085472c63d2ad3fbc1cf53d893bd8da2f8c244
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="callnewh"></a>_callnewh
Wywołuje aktualnie zainstalowany *nowy program obsługi*.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
int _callnewh(  
   size_t size  
   )  
```  
  
#### <a name="parameters"></a>Parametry  
 `size`  
 Ilość pamięci, która [operatora new](../../cpp/new-operator-cpp.md) próbował przydzielić.  
  
## <a name="return-value"></a>Wartość zwracana  
  
|Wartość|Opis|  
|-----------|-----------------|  
|0|Błąd: Bez nowego obsługi są zainstalowane lub nie nowy program obsługi jest aktywny.|  
|1|Powodzenie: Nowy program obsługi ma zainstalowaną i aktywną. Alokacja pamięci można wycofać.|  
  
## <a name="exceptions"></a>Wyjątki  
 Ta funkcja zwraca [bad_alloc —](../../standard-library/bad-alloc-class.md) Jeśli *nowy program obsługi* nie powiodło się.  
  
## <a name="remarks"></a>Uwagi  
 *Nowy program obsługi* jest wywoływana, gdy [operatora new](../../cpp/new-operator-cpp.md) nie powiedzie się pomyślnie przydzielić pamięci. Nowy program obsługi może następnie zainicjuj odpowiednich działań, takich jak zwolnić pamięć, aby pomyślnie kolejnych alokacji.  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|_callnewh|internal.h|  
  
## <a name="see-also"></a>Zobacz też  
 [_set_new_handler —](../../c-runtime-library/reference/set-new-handler.md)   
 [_set_new_mode](../../c-runtime-library/reference/set-new-mode.md)