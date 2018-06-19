---
title: ComPtrRef::operator! = — Operator | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::Details::ComPtrRef::operator!=
dev_langs:
- C++
ms.assetid: ab3093cc-6fbd-4039-890a-6df1cde992b6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 3d5a6e7389215452177add30b587004c312aeae1
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33883557"
---
# <a name="comptrrefoperator-operator"></a>ComPtrRef::operator!= Operator
Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
bool operator!=(  
   const Details::ComPtrRef<ComPtr<T>>& a,  
   const Details::ComPtrRef<ComPtr<U>>& b  
);  
  
bool operator!=(  
   const Details::ComPtrRef<ComPtr<T>>& a,  
   decltype(__nullptr)  
);  
  
bool operator!=(  
   decltype(__nullptr),  
   const Details::ComPtrRef<ComPtr<T>>& a  
);  
  
bool operator!=(  
   const Details::ComPtrRef<ComPtr<T>>& a,  
   void* b  
);  
  
bool operator!=(  
   void* b,  
   const Details::ComPtrRef<ComPtr<T>>& a  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `a`  
 Odwołanie do obiektu comptrref —.  
  
 `b`  
 Odwołanie do innego obiektu comptrref — lub wskaźnik do obiektu anonimowego (`void*`).  
  
## <a name="return-value"></a>Wartość zwracana  
 Pierwszy wydajności operator `true` Jeśli obiekt `a` nie jest równa obiekt `b`; w przeciwnym razie `false`.  
  
 Operatory drugi i trzeci yield `true` Jeśli obiekt `a` nie jest równa `nullptr`; w przeciwnym razie `false`.  
  
 Operatory czwartym i piątym yield `true` Jeśli obiekt `a` nie jest równa obiekt `b`; w przeciwnym razie `false`.  
  
## <a name="remarks"></a>Uwagi  
 Wskazuje, czy dwa obiekty comptrref — nie są takie same.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** client.h  
  
 **Namespace:** Microsoft::wrl —  
  
## <a name="see-also"></a>Zobacz też  
 [Microsoft::wrl:: details — Namespace](../windows/microsoft-wrl-details-namespace.md)   
 [ComPtrRef, klasa](../windows/comptrref-class.md)