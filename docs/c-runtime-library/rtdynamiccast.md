---
title: __RTDynamicCast | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: __RTDynamicCast
apilocation:
- msvcr90.dll
- msvcr110.dll
- msvcr120.dll
- msvcrt.dll
- msvcr100.dll
- msvcr80.dll
- msvcr110_clr0400.dll
apitype: DLLExport
f1_keywords: __RTDynamicCast
dev_langs: C++
helpviewer_keywords: __RTDynamicCast
ms.assetid: 56aa2d7a-aa47-46ef-830d-e37175611239
caps.latest.revision: "3"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 375fcbb4d059ebd431cfd3f86bbf7e3ddb7a3d93
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="rtdynamiccast"></a>__RTDynamicCast
Implementacja interfejsu środowiska wykonawczego [dynamic_cast](../cpp/dynamic-cast-operator.md) operatora.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
PVOID __RTDynamicCast (  
   PVOID inptr,   
   LONG VfDelta,  
   PVOID SrcType,  
   PVOID TargetType,   
   BOOL isReference  
   ) throw(...)  
```  
  
#### <a name="parameters"></a>Parametry  
 `inptr`  
 Wskaźnik do obiektu polimorficznym.  
  
 `VfDelta`  
 Przesunięcie wskaźnika funkcji wirtualnego w obiekcie.  
  
 `SrcType`  
 Typ statyczny obiektu wskazywana przez `inptr` parametru.  
  
 `TargetType`  
 Żądany wynik rzutowania.  
  
 `isReference`  
 `true`Jeśli dane wejściowe jest odwołaniem; `false` Jeśli wejściowy jest wskaźnik.  
  
## <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do odpowiedniego obiektu podrzędnego, w przypadku powodzenia; w przeciwnym razie wartość NULL.  
  
## <a name="exceptions"></a>Wyjątki  
 `bad_cast()`Jeśli w danych wejściowych `dynamic_cast<>` jest odwołaniem i Rzutowanie nie powiedzie się.  
  
## <a name="remarks"></a>Uwagi  
 Konwertuje `inptr` do obiektu typu `TargetType`. Typ `inptr` musi być wskaźnikiem, jeśli `TargetType` jest wskaźnikiem lub l wartość, jeśli `TargetType` to odwołanie. `TargetType`musi być wskaźnikiem lub odwołaniem do typu klasy uprzednio zdefiniowany lub wskaźnika do typu void.  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|__RTDynamicCast|rtti.h|