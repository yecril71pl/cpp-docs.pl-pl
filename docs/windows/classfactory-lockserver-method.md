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
ms.openlocfilehash: ee858346fdb70e136edfbc562c2dfffb1f63e462
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/08/2018
ms.locfileid: "39652375"
---
# <a name="classfactorylockserver-method"></a>ClassFactory::LockServer — Metoda
Zwiększa lub zmniejsza liczbę podstawowych obiektów, które są śledzone przez bieżącą **ClassFactory —** obiektu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
STDMETHOD(  
   LockServer  
)(BOOL fLock);  
```  
  
### <a name="parameters"></a>Parametry  
 *Stada*  
 **wartość true,** się zwiększać liczbę śledzonych obiektów. **FALSE** zmniejszyć liczbę obiektów śledzonych.  
  
## <a name="return-value"></a>Wartość zwracana  
 S_OK w przypadku powodzenia; w przeciwnym razie E_FAIL.  
  
## <a name="remarks"></a>Uwagi  
 **ClassFactory —** śledzi informacje o obiektów w wystąpieniu bazowego [modułu](../windows/module-class.md) klasy.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** module.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Zobacz też  
 [ClassFactory, klasa](../windows/classfactory-class.md)