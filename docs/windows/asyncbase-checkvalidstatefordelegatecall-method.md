---
title: AsyncBase::CheckValidStateForDelegateCall, metoda | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::AsyncBase::CheckValidStateForDelegateCall
dev_langs:
- C++
helpviewer_keywords:
- CheckValidStateForDelegateCall method
ms.assetid: d997ebe7-2378-4e74-a379-f0f85e6922f0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: a03f0dcb8f6d35c1d5fc8aec5bf1cc899d575861
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/08/2018
ms.locfileid: "39653075"
---
# <a name="asyncbasecheckvalidstatefordelegatecall-method"></a>AsyncBase::CheckValidStateForDelegateCall — Metoda
Sprawdza, czy można zmodyfikować właściwości delegata w bieżącym stanie asynchronicznego.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
inline HRESULT CheckValidStateForDelegateCall();  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 S_OK, jeśli można zmodyfikować właściwości delegata; w przeciwnym razie E_ILLEGAL_METHOD_CALL.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** async.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Zobacz też  
 [AsyncBase, klasa](../windows/asyncbase-class.md)