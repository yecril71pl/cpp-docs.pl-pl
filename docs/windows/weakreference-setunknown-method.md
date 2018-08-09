---
title: WeakReference::SetUnknown, metoda | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::WeakReference::SetUnknown
dev_langs:
- C++
helpviewer_keywords:
- SetUnknown method
ms.assetid: 5dddb9e3-a7c1-4195-8166-97c5ab6e972f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 2a46db38bf17b1af5ae748cf90689509d6d21b0d
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/08/2018
ms.locfileid: "39647683"
---
# <a name="weakreferencesetunknown-method"></a>WeakReference::SetUnknown — Metoda
Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.  
  
## <a name="syntax"></a>Składnia  
  
```  
void SetUnknown(  
   _In_ IUnknown* unk  
);  
```  
  
### <a name="parameters"></a>Parametry  
 *UNK*  
 Wskaźnik do `IUnknown` interfejs obiektu.  
  
## <a name="remarks"></a>Uwagi  
 Ustawia silne odwołanie bieżącego **WeakReference** obiekt określony wskaźnik interfejsu.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** implements.h  
  
 **Namespace:** Microsoft::wrl:: details  
  
## <a name="see-also"></a>Zobacz też
 [Weakreference — klasa](../windows/weakreference-class1.md)  
 [Microsoft::WRL::Details, przestrzeń nazw](../windows/microsoft-wrl-details-namespace.md)