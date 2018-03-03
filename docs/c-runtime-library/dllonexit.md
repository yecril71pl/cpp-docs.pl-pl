---
title: __dllonexit | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- __dllonexit
apilocation:
- msvcrt.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr100.dll
- msvcr80.dll
- msvcr120.dll
- msvcr90.dll
- msvcr120_clr0400.dll
apitype: DLLExport
f1_keywords:
- __dllonexit
dev_langs:
- C++
helpviewer_keywords:
- __dllonexit
ms.assetid: 708f2ceb-f95c-46b0-a58d-d68b3fa36f12
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 7ed3b28381b92f4f11e4be99f97a2615a8379274
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="dllonexit"></a>__dllonexit
Rejestruje procedura ma być wywoływana w momencie zakończenia.  
  
## <a name="syntax"></a>Składnia  
  
```  
_onexit_t __dllonexit(   _onexit_t func,  
   _PVFV **  pbegin,   
   _PVFV **  pend   
   )  
```  
  
#### <a name="parameters"></a>Parametry  
 `func`  
 Wskaźnik do funkcję, która ma być wykonywane przy zamykaniu.  
  
 `pbegin`  
 Wskaźnik do zmiennej, która, odłączyć punktów na początku listy funkcji do wykonania na.  
  
 `pend`  
 Wskaźnik do zmiennej, która odłączyć punktów na końcu listy funkcji do wykonania na.  
  
## <a name="return-value"></a>Wartość zwracana  
 W przypadku powodzenia wskaźnika do funkcji użytkownika. W przeciwnym razie wartość wskaźnika NULL.  
  
## <a name="remarks"></a>Uwagi  
 `__dllonexit` Funkcji jest odpowiednikiem [_onexit —](../c-runtime-library/reference/onexit-onexit-m.md) działać z tą różnicą, że zmienne globalne używane przez tą funkcją nie są widoczne dla tej procedury. Zamiast zmiennych globalnych, korzysta z tej funkcji `pbegin` i `pend` parametrów.  
  
 `_onexit` i `atexit` funkcji w bibliotece DLL połączone z MSVCRT. LIB musi obsługiwać własne listy funkcji atexit/_onexit —. Ta procedura jest procesu roboczego, która jest wywoływana przez takich bibliotek DLL.  
  
 `_PVFV` Typ został zdefiniowany jako `typedef void (__cdecl *_PVFV)(void)`.  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymaganego pliku|  
|-------------|-------------------|  
|__dllonexit|OnExit.c|  
  
## <a name="see-also"></a>Zobacz też  
 [_onexit, _onexit_m](../c-runtime-library/reference/onexit-onexit-m.md)