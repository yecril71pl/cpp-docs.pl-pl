---
title: AsyncBase::Start, metoda | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::AsyncBase::Start
dev_langs:
- C++
helpviewer_keywords:
- Start method
ms.assetid: 67405c9d-0d1a-4c1e-8ea4-6ba01c1f90d9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 32c59c00180b26a2856b1fc210302ffff0e72f0c
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/08/2018
ms.locfileid: "39641307"
---
# <a name="asyncbasestart-method"></a>AsyncBase::Start — Metoda
Rozpoczyna operację asynchroniczną.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
STDMETHOD(  
   Start  
)(void);  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 S_OK, jeśli operacja rozpoczyna się lub jest już uruchomiona; w przeciwnym razie E_ILLEGAL_STATE_CHANGE.  
  
## <a name="remarks"></a>Uwagi  
 **Start()** jest domyślna Implementacja klasy `IAsyncInfo::Start`, a nie rzeczywiste działa. Uruchamia operację asynchroniczną, należy zastąpić `OnStart()` czystej wirtualnej metody.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** async.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Zobacz też  
 [AsyncBase, klasa](../windows/asyncbase-class.md)