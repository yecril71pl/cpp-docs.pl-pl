---
title: ClassFactory::LockServer — metoda | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::ClassFactory::LockServer
dev_langs:
- C++
helpviewer_keywords:
- LockServer method
ms.assetid: 8d859815-956d-4f81-a5af-7cdee7e945de
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 9e09a795688c7e2b31771126f9e4036ddfbd8e4f
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33860323"
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
 `true` Aby zwiększyć liczbę śledzonych obiektów. `false` Aby zmniejszyć liczbę śledzonych obiektów.  
  
## <a name="return-value"></a>Wartość zwracana  
 S_OK w przypadku powodzenia; w przeciwnym razie E_FAIL.  
  
## <a name="remarks"></a>Uwagi  
 ClassFactory — przechowuje informacje o obiektów w wystąpieniu podstawowej [modułu](../windows/module-class.md) klasy.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** module.h  
  
 **Namespace:** Microsoft::wrl —  
  
## <a name="see-also"></a>Zobacz też  
 [ClassFactory, klasa](../windows/classfactory-class.md)