---
title: AsyncBase::ContinueAsyncOperation — metoda | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: caf7cd1cbee97761c6877ec6ab3a51ea956cbfd1
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33859595"
---
# <a name="asyncbasecontinueasyncoperation-method"></a>AsyncBase::ContinueAsyncOperation — Metoda
Określa, czy operacja asynchroniczna przetwarzanie powinno być kontynuowane, czy należy zatrzymać.  
  
## <a name="syntax"></a>Składnia  
  
```  
inline bool ContinueAsyncOperation();  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 `true` Jeśli bieżący stan operacji asynchronicznej jest *uruchomiona*, co oznacza operacji powinno być kontynuowane. W przeciwnym razie `false`, co oznacza operacji należy zatrzymać.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** async.h  
  
 **Namespace:** Microsoft::wrl —  
  
## <a name="see-also"></a>Zobacz też  
 [AsyncBase, klasa](../windows/asyncbase-class.md)