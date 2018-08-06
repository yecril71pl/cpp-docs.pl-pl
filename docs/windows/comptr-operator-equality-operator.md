---
title: ComPtr::operator == — Operator | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::ComPtr::operator==
dev_langs:
- C++
ms.assetid: 6a26e936-29d4-4b7d-b44a-7c575ad07509
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 9750f0d49f4c7a580b2c99d0c833c5381ba20997
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/02/2018
ms.locfileid: "39467342"
---
# <a name="comptroperator-operator"></a>ComPtr::operator== Operator
Wskazuje, czy dwa **ComPtr** obiekty są sobie równe.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
bool operator==(  
   const ComPtr<T>& a,  
   const ComPtr<U>& b  
);  
  
bool operator==(  
   const ComPtr<T>& a,  
   decltype(__nullptr)  
);  
  
bool operator==(  
   decltype(__nullptr),  
   const ComPtr<T>& a  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 *a*  
 Odwołanie do **ComPtr** obiektu.  
  
 *b*  
 Odwołanie do innego **ComPtr** obiektu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Pierwszy plony operator **true** Jeśli obiekt *a* jest równy obiektowi *b*; w przeciwnym razie **false**.  
  
 Operatory drugi i trzeci uzyskanie **true** Jeśli obiekt *a* jest równa **nullptr**; w przeciwnym razie **false**.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** client.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Zobacz też  
 [Microsoft::WRL Namespace](../windows/microsoft-wrl-namespace.md)   
 [ComPtr, klasa](../windows/comptr-class.md)