---
title: "ComPtrRef::operator == — Operator | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: client/Microsoft::WRL::Details::ComPtrRef::operator==
dev_langs: C++
ms.assetid: 95fcf781-b473-4317-88cd-e938778d3c3e
caps.latest.revision: "5"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: cc55ab734229cc256f47185349ce79049d05723b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="comptrrefoperator-operator"></a>ComPtrRef::operator== Operator
Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
bool operator==(  
   const Details::ComPtrRef<ComPtr<T>>& a,  
   const Details::ComPtrRef<ComPtr<U>>& b  
);  
  
bool operator==(  
   const Details::ComPtrRef<ComPtr<T>>& a,  
   decltype(__nullptr)  
);  
  
bool operator==(  
   decltype(__nullptr),  
   const Details::ComPtrRef<ComPtr<T>>& a  
);  
  
bool operator==(  
   const Details::ComPtrRef<ComPtr<T>>& a,  
   void* b  
);  
  
bool operator==(  
   void* b,  
   const Details::ComPtrRef<ComPtr<T>>& a  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `a`  
 Odwołanie do obiektu comptrref —.  
  
 `b`  
 Odwołanie do innego obiektu comptrref — lub wskaźnik do typu anonimowego (`void*`).  
  
## <a name="return-value"></a>Wartość zwracana  
 Pierwszy wydajności operator `true` Jeśli obiekt `a` jest taki sam obiekt `b`; w przeciwnym razie `false`.  
  
 Operatory drugi i trzeci yield `true` Jeśli obiekt `a` jest równa `nullptr`; w przeciwnym razie `false`.  
  
 Operatory czwartym i piątym yield `true` Jeśli obiekt `a` jest taki sam obiekt `b`; w przeciwnym razie `false`.  
  
## <a name="remarks"></a>Uwagi  
 Wskazuje, czy dwa obiekty comptrref — są takie same.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** client.h  
  
 **Namespace:** Microsoft::wrl:: details —  
  
## <a name="see-also"></a>Zobacz też  
 [Microsoft::wrl:: details — Namespace](../windows/microsoft-wrl-details-namespace.md)   
 [Comptrref — klasa](../windows/comptrref-class.md)