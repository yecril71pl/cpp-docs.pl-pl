---
title: AsyncBase::TryTransitionToError — metoda | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 97fcade98e82a289c172c7651f62f3de0394fe16
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
---
# <a name="asyncbasetrytransitiontoerror-method"></a>AsyncBase::TryTransitionToError — Metoda
Wskazuje, czy określonego kodu błędu, można zmodyfikować stanu błędu wewnętrznego.  
  
## <a name="syntax"></a>Składnia  
  
```  
bool TryTransitionToError(  
   const HRESULT error  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `error`  
 Wystąpił błąd HRESULT.  
  
## <a name="return-value"></a>Wartość zwracana  
 `true` Błąd wewnętrzny stan został zmieniony; w przeciwnym razie `false`.  
  
## <a name="remarks"></a>Uwagi  
 Ta operacja modyfikuje stan błędu tylko wtedy, gdy stan błędu jest już ustawiony na wartość S_OK. Ta operacja nie ma efektu Jeśli stan błędu już jest błąd, anulowana, Zakończono lub zamknięty.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** async.h  
  
 **Namespace:** Microsoft::wrl —  
  
## <a name="see-also"></a>Zobacz też  
 [AsyncBase, klasa](../windows/asyncbase-class.md)