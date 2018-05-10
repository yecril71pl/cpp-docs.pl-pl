---
title: Eventtargetarray::eventtargetarray — Konstruktor | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: fbfd12ea513044f1062e60f5c73f5089683f043d
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
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
  
 S_FALSE  
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