---
title: "Eventtargetarray::eventtargetarray — Konstruktor | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::Details::EventTargetArray::EventTargetArray
dev_langs:
- C++
helpviewer_keywords:
- EventTargetArray, constructor
ms.assetid: 6c6d3737-3cd3-4515-a8f6-d27901bb8ed2
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 3e8c8ada61a18437ed159452355e8286bc9d190f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="eventtargetarrayeventtargetarray-constructor"></a>EventTargetArray::EventTargetArray — Konstruktor
Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.  
  
## <a name="syntax"></a>Składnia  
  
```  
EventTargetArray(  
   _Out_ HRESULT* hr,  
   size_t items  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `hr`  
 Po tej operacji konstruktora parametru `hr` wskazuje, czy alokacji tablicy powodzeniem lub niepowodzeniem. W poniższej tabeli przedstawiono możliwe wartości `hr`.  
  
 S_OK  
 Operacja zakończyła się pomyślnie.  
  
 E_OUTOFMEMORY  
 Nie można przydzielić pamięci dla tablicy.  
  
 WARTOŚCI S_FALSE  
 Parametr `items` jest mniejsza niż lub równa zero.  
  
 `items`  
 Liczba elementów tablicy do przydzielenia.  
  
## <a name="remarks"></a>Uwagi  
 Inicjuje nowe wystąpienie klasy eventtargetarray —.  
  
 Eventtargetarray — jest używany do przechowywania tablicę procedury obsługi zdarzeń w obiektu EventSource.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** event.h  
  
 **Namespace:** Microsoft::wrl:: details —  
  
## <a name="see-also"></a>Zobacz też  
 [Eventtargetarray — klasa](../windows/eventtargetarray-class.md)   
 [Microsoft::WRL::Details, przestrzeń nazw](../windows/microsoft-wrl-details-namespace.md)