---
title: ComPtr::operator! = — Operator | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::ComPtr::operator!=
dev_langs:
- C++
ms.assetid: 63647240-dec7-4eb9-9272-96c07d01493c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 91b1bb70450cac677abcc886ab2eb911280f86dd
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/08/2018
ms.locfileid: "39642096"
---
# <a name="comptroperator-operator"></a>ComPtr::operator!= Operator
Wskazuje, czy dwa **ComPtr** obiekty nie są równe.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
bool operator!=(  
   const ComPtr<T>& a,  
   const ComPtr<U>& b  
);  
  
bool operator!=(  
   const ComPtr<T>& a,  
   decltype(__nullptr)  
);  
  
bool operator!=(  
   decltype(__nullptr),  
   const ComPtr<T>& a  
);  
```  
  
### <a name="parameters"></a>Parametry  
 *a*  
 Odwołanie do **ComPtr** obiektu.  
  
 *b*  
 Odwołanie do innego **ComPtr** obiektu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Pierwszy plony operator **true** Jeśli obiekt *a* nie jest równa obiektu *b*; w przeciwnym razie **false**.  
  
 Operatory drugi i trzeci uzyskanie **true** Jeśli obiekt *a* nie jest równa **nullptr**; w przeciwnym razie **false**.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** client.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Zobacz też  
 [Microsoft::WRL Namespace](../windows/microsoft-wrl-namespace.md)   
 [ComPtr, klasa](../windows/comptr-class.md)