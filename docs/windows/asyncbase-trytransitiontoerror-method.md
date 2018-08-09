---
title: AsyncBase::TryTransitionToError, metoda | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::AsyncBase::TryTransitionToError
dev_langs:
- C++
helpviewer_keywords:
- TryTransitionToError method
ms.assetid: f6d11c25-1ce3-43f9-af1c-97c4dc0f6f0f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 61b56472e490d95e22c1013595c5c088d2b58dcd
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/08/2018
ms.locfileid: "39643033"
---
# <a name="asyncbasetrytransitiontoerror-method"></a>AsyncBase::TryTransitionToError — Metoda
Wskazuje, czy określonego kodu błędu, można zmodyfikować stanu błędu wewnętrznego.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
bool TryTransitionToError(  
   const HRESULT error  
);  
```  
  
### <a name="parameters"></a>Parametry  
 *Błąd*  
 Błąd HRESULT.  
  
## <a name="return-value"></a>Wartość zwracana  
 **wartość true,** Jeśli stan wewnętrzny błąd zostało zmienione; w przeciwnym razie **false**.  
  
## <a name="remarks"></a>Uwagi  
 Ta operacja modyfikuje stanu błędu, tylko wtedy, gdy stan błędu są już ustawione na S_OK. Ta operacja nie obowiązuje, jeśli stan błędu jest już błędu, anulowany, ukończone lub zamknięte.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** async.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Zobacz też  
 [AsyncBase, klasa](../windows/asyncbase-class.md)