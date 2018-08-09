---
title: AsyncBase::Cancel, metoda | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::AsyncBase::Cancel
dev_langs:
- C++
helpviewer_keywords:
- Cancel method
ms.assetid: 8bfebc63-3848-4629-bc89-aa538ed7e7ad
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 439a118bbea5adce4c306298e573bed85da26291
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/08/2018
ms.locfileid: "39641907"
---
# <a name="asyncbasecancel-method"></a>AsyncBase::Cancel — Metoda
Anuluje operację asynchroniczną.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
STDMETHOD(  
   Cancel  
)(void);  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 Domyślnie zawsze zwraca wartość S_OK.  
  
## <a name="remarks"></a>Uwagi  
 **Cancel()** jest domyślna Implementacja klasy `IAsyncInfo::Cancel`, a nie rzeczywiste działa. Aby rzeczywiście anulować operację asynchroniczną, Zastąp `OnCancel()` czystej wirtualnej metody.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** async.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Zobacz też  
 [AsyncBase, klasa](../windows/asyncbase-class.md)