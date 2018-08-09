---
title: EventTargetArray::EventTargetArray, Konstruktor | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::Details::EventTargetArray::EventTargetArray
dev_langs:
- C++
helpviewer_keywords:
- EventTargetArray, constructor
ms.assetid: 6c6d3737-3cd3-4515-a8f6-d27901bb8ed2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 59753f592f099f80396f408fa531756ba91b308e
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/08/2018
ms.locfileid: "39652542"
---
# <a name="eventtargetarrayeventtargetarray-constructor"></a>EventTargetArray::EventTargetArray — Konstruktor
Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
EventTargetArray(  
   _Out_ HRESULT* hr,  
   size_t items  
);  
```  
  
### <a name="parameters"></a>Parametry  
 *godz.*  
 Po tej operacji konstruktora parametru *hr* wskazuje, czy przydział tablicy zakończonych powodzeniem lub niepowodzeniem. Poniższa tabela zawiera listę możliwych wartości dla *hr*.  
  
 S_OK  
 Operacja zakończyła się pomyślnie.  
  
 E_OUTOFMEMORY  
 Nie można przydzielić pamięci dla tablicy.  
  
 S_FALSE  
 Parametr *elementów* jest mniejsza niż zero.  
  
 *Elementy*  
 Liczba elementów tablicy można przydzielić.  
  
## <a name="remarks"></a>Uwagi  
 Inicjuje nowe wystąpienie klasy **EventTargetArray** klasy.  
  
 **EventTargetArray** jest używany do przechowywania programu obsługi zdarzeń w tablicy `EventSource` obiektu.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** event.h  
  
 **Namespace:** Microsoft::wrl:: details  
  
## <a name="see-also"></a>Zobacz też  
 [Eventtargetarray — klasa](../windows/eventtargetarray-class.md)   
 [Microsoft::WRL::Details, przestrzeń nazw](../windows/microsoft-wrl-details-namespace.md)