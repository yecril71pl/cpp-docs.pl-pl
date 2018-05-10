---
title: AsyncBase::Start — metoda | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 0acc6f62530daf641a2e4d568ed511d6fd831c20
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
---
# <a name="asyncbasestart-method"></a>AsyncBase::Start — Metoda
Rozpoczyna operację asynchroniczną.  
  
## <a name="syntax"></a>Składnia  
  
```  
STDMETHOD(  
   Start  
)(void);  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 S_OK, jeśli operacja rozpoczyna się lub jest już uruchomiona; w przeciwnym razie E_ILLEGAL_STATE_CHANGE.  
  
## <a name="remarks"></a>Uwagi  
 Start() jest domyślna implementacja elementu IAsyncInfo::Start, a nie rzeczywiste działa. Uruchamia operację asynchroniczną, przesłonić metodę wirtualną czysty OnStart().  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** async.h  
  
 **Namespace:** Microsoft::wrl —  
  
## <a name="see-also"></a>Zobacz też  
 [AsyncBase, klasa](../windows/asyncbase-class.md)