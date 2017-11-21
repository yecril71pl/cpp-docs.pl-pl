---
title: "InterfaceTraits::CastToUnknown — metoda | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: implements/Microsoft::WRL::Details::InterfaceTraits::CastToUnknown
dev_langs: C++
helpviewer_keywords: CastToUnknown method
ms.assetid: aca47fa0-3c60-47f2-a73c-258f7160adff
caps.latest.revision: "5"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 9c37be3cd27c70a0128d1a382af3efe9c96d6cc8
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="interfacetraitscasttounknown-method"></a>InterfaceTraits::CastToUnknown — Metoda
Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.  
  
## <a name="syntax"></a>Składnia  
  
```  
template<  
   typename T  
>  
static __forceinline IUnknown* CastToUnknown(  
   _In_ T* ptr  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Typ parametru `ptr`.  
  
 `ptr`  
 Wskaźnik do typu `T`.  
  
## <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do elementu IUnknown, z którego `Base` pochodzi.  
  
## <a name="remarks"></a>Uwagi  
 Rzutuje określony wskaźnik na wskaźnik do elementu IUnknown.  
  
 Aby uzyskać więcej informacji na temat `Base`, zobacz sekcję publicznego definicje typów w [interfacetraits — struktura](../windows/interfacetraits-structure.md).  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** implements.h  
  
 **Namespace:** Microsoft::wrl:: details —  
  
## <a name="see-also"></a>Zobacz też  
 [Interfacetraits — struktura](../windows/interfacetraits-structure.md)   
 [Microsoft::wrl:: details — Namespace](../windows/microsoft-wrl-details-namespace.md)