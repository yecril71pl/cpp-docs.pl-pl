---
title: "ClassFactory::LockServer — metoda | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::ClassFactory::LockServer
dev_langs:
- C++
helpviewer_keywords:
- LockServer method
ms.assetid: 8d859815-956d-4f81-a5af-7cdee7e945de
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 5f646f198d884e677b622a312cfdb6187802e1c6
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="classfactorylockserver-method"></a>ClassFactory::LockServer — Metoda
Zwiększa lub zmniejsza liczbę podstawowych obiektów, które są śledzone przez bieżący obiekt ClassFactory —.  
  
## <a name="syntax"></a>Składnia  
  
```  
STDMETHOD(  
   LockServer  
)(BOOL fLock);  
```  
  
#### <a name="parameters"></a>Parametry  
 `fLock`  
 `true`Aby zwiększyć liczbę śledzonych obiektów. `false`Aby zmniejszyć liczbę śledzonych obiektów.  
  
## <a name="return-value"></a>Wartość zwracana  
 S_OK w przypadku powodzenia; w przeciwnym razie E_FAIL.  
  
## <a name="remarks"></a>Uwagi  
 ClassFactory — przechowuje informacje o obiektów w wystąpieniu podstawowej [modułu](../windows/module-class.md) klasy.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** module.h  
  
 **Namespace:** Microsoft::wrl —  
  
## <a name="see-also"></a>Zobacz też  
 [ClassFactory, klasa](../windows/classfactory-class.md)