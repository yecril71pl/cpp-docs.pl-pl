---
title: "InterfaceTraits::FillArrayWithIid — metoda | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: implements/Microsoft::WRL::Details::InterfaceTraits::FillArrayWithIid
dev_langs: C++
helpviewer_keywords: FillArrayWithIid method
ms.assetid: 73583177-adc9-4fcb-917d-fa7e6d07c990
caps.latest.revision: "5"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c626955e957bd3db4b4d34255a38751f3339dcf9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="interfacetraitsfillarraywithiid-method"></a>InterfaceTraits::FillArrayWithIid — Metoda
Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.  
  
## <a name="syntax"></a>Składnia  
  
```  
__forceinline static void FillArrayWithIid(  
   _Inout_ unsigned long &index,  
   _In_ IID* iids  
);  
  
```  
  
#### <a name="parameters"></a>Parametry  
 `index`  
 Wskaźnik do pola, które zawiera wartość indeksu.  
  
 `iids`  
 Tablica interfejsu identyfikatorów.  
  
## <a name="remarks"></a>Uwagi  
 Przypisuje identyfikator interfejsu `Base` do elementu tablicy argumentu indeksu.  
  
 Sprzecznie nazwę tego interfejsu API elementu tylko jedna tablica jest modyfikowany; nie całej tablicy.  
  
 Aby uzyskać więcej informacji na temat `Base`, zobacz sekcję publicznego definicje typów w [interfacetraits — struktura](../windows/interfacetraits-structure.md).  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** implements.h  
  
 **Namespace:** Microsoft::wrl:: details —  
  
## <a name="see-also"></a>Zobacz też  
 [Interfacetraits — struktura](../windows/interfacetraits-structure.md)   
 [Microsoft::WRL::Details, przestrzeń nazw](../windows/microsoft-wrl-details-namespace.md)