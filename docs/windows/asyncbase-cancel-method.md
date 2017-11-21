---
title: "AsyncBase::Cancel — metoda | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: async/Microsoft::WRL::AsyncBase::Cancel
dev_langs: C++
helpviewer_keywords: Cancel method
ms.assetid: 8bfebc63-3848-4629-bc89-aa538ed7e7ad
caps.latest.revision: "3"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 5b6215c871da92087a7555bfb5a97f48d60223de
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="asyncbasecancel-method"></a>AsyncBase::Cancel — Metoda
Anuluje operację asynchroniczną.  
  
## <a name="syntax"></a>Składnia  
  
```  
STDMETHOD(  
   Cancel  
)(void);  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 Domyślnie zwraca zawsze wartość S_OK.  
  
## <a name="remarks"></a>Uwagi  
 Cancel() jest domyślną implementację IAsyncInfo::Cancel, a nie rzeczywiste działa. Aby rzeczywiście anulować operację asynchroniczną, przesłonić metodę wirtualną czysty OnCancel().  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** async.h  
  
 **Namespace:** Microsoft::wrl —  
  
## <a name="see-also"></a>Zobacz też  
 [Asyncbase — klasa](../windows/asyncbase-class.md)