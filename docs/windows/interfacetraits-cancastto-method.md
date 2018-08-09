---
title: InterfaceTraits::CanCastTo, metoda | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::InterfaceTraits::CanCastTo
dev_langs:
- C++
helpviewer_keywords:
- CanCastTo method
ms.assetid: 275847cb-69ea-42bf-910f-05ba6ef8b48d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: a2f8712e06838fb2d2269ba307a551997d7bd57c
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2018
ms.locfileid: "40018234"
---
# <a name="interfacetraitscancastto-method"></a>InterfaceTraits::CanCastTo — Metoda
Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
template<typename T>  
static __forceinline bool CanCastTo(  
   _In_ T* ptr,  
   REFIID riid,  
   _Deref_out_ void **ppv  
);  
```  
  
### <a name="parameters"></a>Parametry  
 *ptr*  
 Nazwa wskaźnika do typu.  
  
 *Parametr riid*  
 Identyfikator interfejsu `Base`.  
  
 *ppv*  
 Jeśli operacja zakończy się pomyślnie, *ppv* wskazuje interfejs określony przez `Base`. W przeciwnym razie *ppv* ustawiono **nullptr**.  
  
## <a name="return-value"></a>Wartość zwracana  
 **wartość true,** Jeśli operacja zakończy się pomyślnie i *ptr* jest rzutowany na wskaźnik do `Base`; w przeciwnym razie **false** .  
  
## <a name="remarks"></a>Uwagi  
 Wskazuje, czy określony wskaźnik może być rzutowany na wskaźnik do `Base`.  
  
 Aby uzyskać więcej informacji na temat `Base`, zobacz **publiczne definicje typów** sekcji [interfacetraits — struktura](../windows/interfacetraits-structure.md).  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** implements.h  
  
 **Namespace:** Microsoft::wrl:: details  
  
## <a name="see-also"></a>Zobacz też  
 [Interfacetraits — struktura](../windows/interfacetraits-structure.md)   
 [Microsoft::WRL::Details, przestrzeń nazw](../windows/microsoft-wrl-details-namespace.md)