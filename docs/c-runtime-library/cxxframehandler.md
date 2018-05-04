---
title: __CxxFrameHandler | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
apiname:
- __CxxFrameHandler
apilocation:
- msvcr110.dll
- msvcrt.dll
- msvcr80.dll
- msvcr100.dll
- msvcr110_clr0400.dll
- msvcr90.dll
- msvcr120.dll
apitype: DLLExport
f1_keywords:
- __CxxFrameHandler
dev_langs:
- C++
helpviewer_keywords:
- __CxxFrameHandler
ms.assetid: b79ac97f-425a-42ae-9b91-8beaef935333
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 53659b462f811bca79209dd141d90527401cbc95
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="cxxframehandler"></a>__CxxFrameHandler
Funkcji CRT wewnętrznej. Używany przez CRT do obsługi wyjątków strukturalnych ramki.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
EXCEPTION_DISPOSITION __CxxFrameHandler(  
      EHExceptionRecord  *pExcept,  
      EHRegistrationNode *pRN,  
      void               *pContext,   
      DispatcherContext  *pDC  
   )  
```  
  
#### <a name="parameters"></a>Parametry  
 `pExcept`  
 Rekord wyjątek, który jest przekazywany do możliwe `catch` instrukcje.  
  
 `pRN`  
 Dynamiczne informacje o ramki stosu, który służy do obsługi wyjątku. Aby uzyskać więcej informacji zobacz ehdata.h.  
  
 `pContext`  
 Kontekst. (Nie używany na procesory Intel).  
  
 `pDC`  
 Dodatkowe informacje o funkcji ramki wejścia i stosu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeden z *wyrażenie filtru* wartości używane przez [spróbuj-except — instrukcja](../cpp/try-except-statement.md).  
  
## <a name="remarks"></a>Uwagi  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|__CxxFrameHandler|excpt.h, ehdata.h|