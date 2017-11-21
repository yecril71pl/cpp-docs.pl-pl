---
title: "Eventtargetarray::eventtargetarray — Konstruktor | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: event/Microsoft::WRL::Details::EventTargetArray::EventTargetArray
dev_langs: C++
helpviewer_keywords: EventTargetArray, constructor
ms.assetid: 6c6d3737-3cd3-4515-a8f6-d27901bb8ed2
caps.latest.revision: "5"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 6dbe316310e04172c659460c08137edd2a401df6
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
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
 [Microsoft::wrl:: details — Namespace](../windows/microsoft-wrl-details-namespace.md)