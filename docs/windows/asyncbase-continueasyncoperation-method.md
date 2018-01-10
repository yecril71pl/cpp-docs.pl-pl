---
title: "AsyncBase::ContinueAsyncOperation — metoda | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: async/Microsoft::WRL::AsyncBase::ContinueAsyncOperation
dev_langs: C++
helpviewer_keywords: ContinueAsyncOperation method
ms.assetid: ce38181d-2fc3-4579-b0ce-237a3c7648bc
caps.latest.revision: "3"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 7e86c4857aab7c0e1a23dcd03695d906a3d9e5e0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="asyncbasecontinueasyncoperation-method"></a>AsyncBase::ContinueAsyncOperation — Metoda
Określa, czy operacja asynchroniczna przetwarzanie powinno być kontynuowane, czy należy zatrzymać.  
  
## <a name="syntax"></a>Składnia  
  
```  
inline bool ContinueAsyncOperation();  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 `true`Jeśli bieżący stan operacji asynchronicznej jest *uruchomiona*, co oznacza operacji powinno być kontynuowane. W przeciwnym razie `false`, co oznacza operacji należy zatrzymać.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** async.h  
  
 **Namespace:** Microsoft::wrl —  
  
## <a name="see-also"></a>Zobacz też  
 [AsyncBase, klasa](../windows/asyncbase-class.md)