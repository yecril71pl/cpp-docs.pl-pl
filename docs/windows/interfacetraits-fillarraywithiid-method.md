---
title: InterfaceTraits::FillArrayWithIid, metoda | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::InterfaceTraits::FillArrayWithIid
dev_langs:
- C++
helpviewer_keywords:
- FillArrayWithIid method
ms.assetid: 73583177-adc9-4fcb-917d-fa7e6d07c990
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 1ef552e5025a18eb4c778f9d08389d2b7e3634d5
ms.sourcegitcommit: 4586bfc32d8bc37ab08b24816d7fad5df709bfa3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2018
ms.locfileid: "39605659"
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
  
### <a name="parameters"></a>Parametry  
 *index*  
 Wskaźnik do pola, które zawiera wartość indeksu zaczynającego się od zera.  
  
 *IID*  
 Tablica identyfikatorów interfejsu.  
  
## <a name="remarks"></a>Uwagi  
 Przypisuje identyfikator interfejsu `Base` do elementu tablicy, określonego przez argument indeksu.  
  
 Sprzecznie nazwę tego interfejsu API tylko jedna tablica element zostanie zmodyfikowany; nie macierz w całości.  
  
 Aby uzyskać więcej informacji na temat `Base`, zobacz sekcję publiczne definicje typów w [interfacetraits — struktura](../windows/interfacetraits-structure.md).  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** implements.h  
  
 **Namespace:** Microsoft::wrl:: details  
  
## <a name="see-also"></a>Zobacz też  
 [Interfacetraits — struktura](../windows/interfacetraits-structure.md)   
 [Microsoft::WRL::Details, przestrzeń nazw](../windows/microsoft-wrl-details-namespace.md)