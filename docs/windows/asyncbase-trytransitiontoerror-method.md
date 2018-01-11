---
title: "AsyncBase::TryTransitionToError — metoda | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: async/Microsoft::WRL::AsyncBase::TryTransitionToError
dev_langs: C++
helpviewer_keywords: TryTransitionToError method
ms.assetid: f6d11c25-1ce3-43f9-af1c-97c4dc0f6f0f
caps.latest.revision: "3"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 6da3d84e3e5e1ee0fd71da1cf59ec79497f81d35
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
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
 `true`Błąd wewnętrzny stan został zmieniony; w przeciwnym razie `false`.  
  
## <a name="remarks"></a>Uwagi  
 Ta operacja modyfikuje stan błędu tylko wtedy, gdy stan błędu jest już ustawiony na wartość S_OK. Ta operacja nie ma efektu Jeśli stan błędu już jest błąd, anulowana, Zakończono lub zamknięty.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** async.h  
  
 **Namespace:** Microsoft::wrl —  
  
## <a name="see-also"></a>Zobacz też  
 [AsyncBase, klasa](../windows/asyncbase-class.md)