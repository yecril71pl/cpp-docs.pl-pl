---
title: WeakReference::DecrementStrongReference — metoda | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::WeakReference::DecrementStrongReference
dev_langs:
- C++
helpviewer_keywords:
- DecrementStrongReference method
ms.assetid: 97d70d9f-41b8-4f8d-a6fa-4137cc4f9029
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 7d5605670e05f91f9f1293c8bff0f4d74e458d25
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33890339"
---
# <a name="weakreferencedecrementstrongreference-method"></a>WeakReference::DecrementStrongReference — Metoda
Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.  
  
## <a name="syntax"></a>Składnia  
  
```  
ULONG DecrementStrongReference();  
```  
  
## <a name="remarks"></a>Uwagi  
 Zmniejsza silne odwołanie liczba bieżące weakreference — obiektu.  
  
 Gdy liczba silne odwołanie wynosi zero, silne odwołanie ma wartość `nullptr`.  
  
## <a name="return-value"></a>Wartość zwracana  
 Liczba zmniejszany silne odwołanie.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** implements.h  
  
 **Namespace:** Microsoft::wrl:: details —  
  
## <a name="see-also"></a>Zobacz też  
[Weakreference — klasa](../windows/weakreference-class1.md)  
 [Microsoft::WRL::Details, przestrzeń nazw](../windows/microsoft-wrl-details-namespace.md)