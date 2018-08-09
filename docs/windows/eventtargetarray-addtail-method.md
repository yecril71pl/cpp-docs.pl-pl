---
title: EventTargetArray::AddTail, metoda | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::Details::EventTargetArray::AddTail
dev_langs:
- C++
helpviewer_keywords:
- AddTail method
ms.assetid: d0fafab9-049c-40e0-a40c-d126c9ee63e6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 3e80bf6d4313be5c90b4b4486cb31f3705252f33
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/08/2018
ms.locfileid: "39651268"
---
# <a name="eventtargetarrayaddtail-method"></a>EventTargetArray::AddTail — Metoda
Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
void AddTail(  
   _In_ IUnknown* element  
);  
```  
  
### <a name="parameters"></a>Parametry  
 *Element*  
 Wskaźnik do narzędzia obsługi zdarzeń do dołączenia.  
  
## <a name="remarks"></a>Uwagi  
 Dołącza określona procedura obsługi zdarzeń do końca tablicy wewnętrzne programów obsługi zdarzeń.  
  
 **AddTail()** mają być używane wewnętrznie przez tylko `EventSource` klasy.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** event.h  
  
 **Namespace:** Microsoft::wrl:: details  
  
## <a name="see-also"></a>Zobacz też  
 [Eventtargetarray — klasa](../windows/eventtargetarray-class.md)   
 [Microsoft::WRL::Details, przestrzeń nazw](../windows/microsoft-wrl-details-namespace.md)