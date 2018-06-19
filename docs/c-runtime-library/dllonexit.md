---
title: __dllonexit | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1c0105ccc5a40c4e5fe789814adfabe6c9749650
ms.sourcegitcommit: 6e3cf8df676d59119ce88bf5321d063cf479108c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/22/2018
ms.locfileid: "34450722"
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
 W przypadku powodzenia wskaźnika do funkcji użytkownika. W przeciwnym razie **NULL** wskaźnika.  
  
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