---
title: "Chaininterfaces::iidcount — stała | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: implements/Microsoft::WRL::ChainInterfaces::IidCount
dev_langs: C++
helpviewer_keywords: IidCount constant
ms.assetid: d4a90aa0-513c-4e99-b978-e12149734936
caps.latest.revision: "3"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: a1a3409452fcae3764519c4beeb3557e5fd877b0
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="chaininterfacesiidcount-constant"></a>ChainInterfaces::IidCount — Stała
Całkowita liczba interfejsu identyfikatorów zawarte w interfejsach określona przez parametry szablonu `I0` za pośrednictwem `I9`.  
  
## <a name="syntax"></a>Składnia  
  
```  
static const unsigned long IidCount = Details::InterfaceTraits<I0>::IidCount + Details::InterfaceTraits<I1>::IidCount + Details::InterfaceTraits<I2>::IidCount + Details::InterfaceTraits<I3>::IidCount + Details::InterfaceTraits<I4>::IidCount + Details::InterfaceTraits<I5>::IidCount + Details::InterfaceTraits<I6>::IidCount + Details::InterfaceTraits<I7>::IidCount + Details::InterfaceTraits<I8>::IidCount + Details::InterfaceTraits<I9>::IidCount;  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 Całkowita liczba identyfikatorów interfejsu.  
  
## <a name="remarks"></a>Uwagi  
 Parametry szablonu `I0` i `I1` są wymagane, parametry i `I2` za pośrednictwem `I9` są opcjonalne. Liczba identyfikatora IID interfejsu każdego zwykle wynosi 1.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** implements.h  
  
 **Namespace:** Microsoft::wrl —  
  
## <a name="see-also"></a>Zobacz też  
 [Chaininterfaces — struktura](../windows/chaininterfaces-structure.md)