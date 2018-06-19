---
title: AsyncBase::Close — metoda | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::AsyncBase::Close
dev_langs:
- C++
helpviewer_keywords:
- Close method
ms.assetid: a52b1124-754b-4393-b491-64aae0c22f1c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 4f3f36656b9316fb6ad980349a836fad31c3a9a0
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33860798"
---
# <a name="asyncbaseclose-method"></a>AsyncBase::Close — Metoda
Zamyka operację asynchroniczną.  
  
## <a name="syntax"></a>Składnia  
  
```  
STDMETHOD(  
   Close  
)(void) override;  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 Wartość S_OK, jeśli operacja zostanie zamknięte lub jest już zamknięty; w przeciwnym razie E_ILLEGAL_STATE_CHANGE.  
  
## <a name="remarks"></a>Uwagi  
 Close() jest domyślną implementację IAsyncInfo::Close, a nie rzeczywiste działa. Aby zamknąć faktycznie operację asynchroniczną, przesłonić metodę wirtualną czysty OnClose().  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** async.h  
  
 **Namespace:** Microsoft::wrl —  
  
## <a name="see-also"></a>Zobacz też  
 [AsyncBase, klasa](../windows/asyncbase-class.md)