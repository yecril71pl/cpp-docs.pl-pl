---
title: WeakReference::DecrementStrongReference, metoda | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 19dcb3e90faef86fd291381a7082e8b5bfa89069
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2018
ms.locfileid: "40013460"
---
# <a name="weakreferencedecrementstrongreference-method"></a>WeakReference::DecrementStrongReference — Metoda
Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
ULONG DecrementStrongReference();  
```  
  
## <a name="remarks"></a>Uwagi  
 Dekrementuje silne odwołanie zliczane bieżącego **WeakReference** obiektu.  
  
 Gdy liczba silne odwołanie staje się zerem, silne odwołanie jest ustawiona na **nullptr**.  
  
## <a name="return-value"></a>Wartość zwracana  
 Liczba wraz z przydzielaniem silne odwołanie.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** implements.h  
  
 **Namespace:** Microsoft::wrl:: details  
  
## <a name="see-also"></a>Zobacz też  
 [Weakreference — klasa](../windows/weakreference-class1.md)  
 [Microsoft::WRL::Details, przestrzeń nazw](../windows/microsoft-wrl-details-namespace.md)