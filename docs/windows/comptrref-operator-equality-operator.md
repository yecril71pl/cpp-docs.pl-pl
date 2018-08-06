---
title: ComPtrRef::operator == — Operator | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::Details::ComPtrRef::operator==
dev_langs:
- C++
ms.assetid: 95fcf781-b473-4317-88cd-e938778d3c3e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 606059712e60ba181998155b55ae02ba8b27c4da
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/02/2018
ms.locfileid: "39463957"
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
 *a*  
 Odwołanie do obiektu comptrref —.  
  
 *b*  
 Odwołanie do innego obiektu comptrref — lub wskaźnik do typu anonimowego (`void*`).  
  
## <a name="return-value"></a>Wartość zwracana  
 Pierwszy plony operator **true** Jeśli obiekt *a* jest równy obiektowi *b*; w przeciwnym razie **false**.  
  
 Operatory drugi i trzeci uzyskanie **true** Jeśli obiekt *a* jest równa **nullptr**; w przeciwnym razie **false**.  
  
 Operatory czwarty i piąty uzyskanie **true** Jeśli obiekt *a* jest równy obiektowi *b*; w przeciwnym razie **false**.  
  
## <a name="remarks"></a>Uwagi  
 Wskazuje, czy dwa obiekty comptrref — są takie same.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** client.h  
  
 **Namespace:** Microsoft::wrl:: details  
  
## <a name="see-also"></a>Zobacz też  
 [Microsoft::wrl:: details Namespace](../windows/microsoft-wrl-details-namespace.md)   
 [ComPtrRef, klasa](../windows/comptrref-class.md)