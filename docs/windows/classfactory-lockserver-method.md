---
title: ClassFactory::LockServer, metoda | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 654ef60c924a14e861971c651899c8baea0300ef
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/02/2018
ms.locfileid: "39462709"
---
# <a name="classfactorylockserver-method"></a>ClassFactory::LockServer — Metoda
Zwiększa lub zmniejsza liczbę podstawowych obiektów, które są śledzone przez bieżącą **ClassFactory —** obiektu.  
  
## <a name="syntax"></a>Składnia  
  
```  
STDMETHOD(  
   LockServer  
)(BOOL fLock);  
```  
  
#### <a name="parameters"></a>Parametry  
 *Stada*  
 **wartość true,** się zwiększać liczbę śledzonych obiektów. **FALSE** zmniejszyć liczbę obiektów śledzonych.  
  
## <a name="return-value"></a>Wartość zwracana  
 S_OK w przypadku powodzenia; w przeciwnym razie E_FAIL.  
  
## <a name="remarks"></a>Uwagi  
 ClassFactory — śledzi informacje o obiektów w wystąpieniu bazowego [modułu](../windows/module-class.md) klasy.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** module.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Zobacz też  
 [ClassFactory, klasa](../windows/classfactory-class.md)