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
ms.openlocfilehash: 2450b5d473d1caadae171516cf337479bfd5d603
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33881884"
---
# <a name="comptroperator-operator"></a>ComPtr::operator!= Operator
Wskazuje, czy dwa obiekty comptr — nie są takie same.  
  
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
  
#### <a name="parameters"></a>Parametry  
 `a`  
 Odwołanie do obiektu comptr —.  
  
 `b`  
 Odwołanie do innego obiektu comptr —.  
  
## <a name="return-value"></a>Wartość zwracana  
 Pierwszy wydajności operator `true` Jeśli obiekt `a` nie jest równa obiekt `b`; w przeciwnym razie `false`.  
  
 Operatory drugi i trzeci yield `true` Jeśli obiekt `a` nie jest równa `nullptr`; w przeciwnym razie `false`.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** client.h  
  
 **Namespace:** Microsoft::wrl —  
  
## <a name="see-also"></a>Zobacz też  
 [Microsoft::wrl — Namespace](../windows/microsoft-wrl-namespace.md)   
 [ComPtr, klasa](../windows/comptr-class.md)