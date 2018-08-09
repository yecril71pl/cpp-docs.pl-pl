---
title: AsyncBase::ContinueAsyncOperation, metoda | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::AsyncBase::ContinueAsyncOperation
dev_langs:
- C++
helpviewer_keywords:
- ContinueAsyncOperation method
ms.assetid: ce38181d-2fc3-4579-b0ce-237a3c7648bc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: a335d379c1797e6152ea1b6011830423082693bb
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/08/2018
ms.locfileid: "39648051"
---
# <a name="asyncbasecontinueasyncoperation-method"></a>AsyncBase::ContinueAsyncOperation — Metoda
Określa, czy operacja asynchroniczna przetwarzanie powinno być kontynuowane, czy należy wstrzymać.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
inline bool ContinueAsyncOperation();  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 **wartość true,** Jeśli bieżący stan operacji asynchronicznej jest *pracę*, co oznacza, że operacja powinno być kontynuowane. W przeciwnym razie **false**, co oznacza, że operacja należy wstrzymać.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** async.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Zobacz też  
 [AsyncBase, klasa](../windows/asyncbase-class.md)