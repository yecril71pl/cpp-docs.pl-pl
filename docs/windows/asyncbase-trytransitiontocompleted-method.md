---
title: AsyncBase::TryTransitionToCompleted, metoda | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::AsyncBase::TryTransitionToCompleted
dev_langs:
- C++
helpviewer_keywords:
- TryTransitionToCompleted method
ms.assetid: 8d038e0a-47ec-4cfc-8aeb-6821282df67a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: a44434c530bd0685627e2e807140e31068cb5eb8
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/08/2018
ms.locfileid: "39645763"
---
# <a name="asyncbasetrytransitiontocompleted-method"></a>AsyncBase::TryTransitionToCompleted — Metoda
Wskazuje, czy bieżąca operacja asynchroniczna została ukończona.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
bool TryTransitionToCompleted(  
   void  
);  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 **wartość true,** Jeśli operacja asynchroniczna została ukończona; w przeciwnym razie **false**.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** async.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Zobacz też  
 [AsyncBase, klasa](../windows/asyncbase-class.md)