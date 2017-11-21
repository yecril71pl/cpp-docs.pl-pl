---
title: "InterfaceTraits::CanCastTo — metoda | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: implements/Microsoft::WRL::Details::InterfaceTraits::CanCastTo
dev_langs: C++
helpviewer_keywords: CanCastTo method
ms.assetid: 275847cb-69ea-42bf-910f-05ba6ef8b48d
caps.latest.revision: "5"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 107c89c7643e137b20492f9ae932a736cc0ba603
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="interfacetraitscancastto-method"></a>InterfaceTraits::CanCastTo — Metoda
Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
template<typename T>  
static __forceinline bool CanCastTo(  
   _In_ T* ptr,  
   REFIID riid,  
   _Deref_out_ void **ppv  
);  
  
```  
  
#### <a name="parameters"></a>Parametry  
 `ptr`  
 Nazwa wskaźnika do typu.  
  
 `riid`  
 Identyfikator interfejsu `Base`.  
  
 `ppv`  
 Jeśli ta operacja zakończy się pomyślnie, `ppv` wskazuje określony przez interfejs `Base`. W przeciwnym razie `ppv` ma ustawioną wartość `nullptr`.  
  
## <a name="return-value"></a>Wartość zwracana  
 `true`Jeśli ta operacja zakończy się pomyślnie i `ptr` jest rzutowane na wskaźnik do `Base`; w przeciwnym razie `false` .  
  
## <a name="remarks"></a>Uwagi  
 Wskazuje, czy określony wskaźnik mogą być rzutowane na wskaźnik do `Base`.  
  
 Aby uzyskać więcej informacji na temat `Base`, zobacz sekcję publicznego definicje typów w [interfacetraits — struktura](../windows/interfacetraits-structure.md).  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** implements.h  
  
 **Namespace:** Microsoft::wrl:: details —  
  
## <a name="see-also"></a>Zobacz też  
 [Interfacetraits — struktura](../windows/interfacetraits-structure.md)   
 [Microsoft::wrl:: details — Namespace](../windows/microsoft-wrl-details-namespace.md)