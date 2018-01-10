---
title: "Chaininterfaces — struktura | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: implements/Microsoft::WRL::ChainInterfaces
dev_langs: C++
helpviewer_keywords: ChainInterfaces structure
ms.assetid: d7415b59-5468-4bef-a3fd-8d82b12f0e9c
caps.latest.revision: "3"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e9417b3950e4df98ed4e13ea1bb40e76c383868e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="chaininterfaces-structure"></a>ChainInterfaces — Struktura
Określa weryfikacji i inicjowania funkcje, które można zastosować do zestawu interfejsu identyfikatorów.  
  
## <a name="syntax"></a>Składnia  
  
```  
template <  
   typename I0,  
   typename I1,  
   typename I2 = Details::Nil,  
   typename I3 = Details::Nil,  
   typename I4 = Details::Nil,  
   typename I5 = Details::Nil,  
   typename I6 = Details::Nil,  
   typename I7 = Details::Nil,  
   typename I8 = Details::Nil,  
   typename I9 = Details::Nil  
>  
struct ChainInterfaces : I0;  
template <  
   typename DerivedType,  
   typename BaseType,  
   bool hasImplements,  
   typename I1,  
   typename I2,  
   typename I3,  
   typename I4,  
   typename I5,  
   typename I6,  
   typename I7,  
   typename I8,  
   typename I9  
>  
struct ChainInterfaces<MixIn<DerivedType, BaseType, hasImplements>, I1, I2, I3, I4, I5, I6, I7, I8, I9>;  
```  
  
#### <a name="parameters"></a>Parametry  
 `I0`  
 (Wymagane) Identyfikator interfejs: 0.  
  
 `I1`  
 (Wymagane) Identyfikator interfejsu 1.  
  
 `I2`  
 (Opcjonalnie) Identyfikator interfejsu 2.  
  
 `I3`  
 (Opcjonalnie) Identyfikator interfejsu 3.  
  
 `I4`  
 (Opcjonalnie) Identyfikator interfejsu 4.  
  
 `I5`  
 (Opcjonalnie) Identyfikator interfejsu 5.  
  
 `I6`  
 (Opcjonalnie) Identyfikator interfejsu 6.  
  
 `I7`  
 (Opcjonalnie) Identyfikator interfejsu 7.  
  
 `I8`  
 (Opcjonalnie) Identyfikator interfejsu 8.  
  
 `I9`  
 (Opcjonalnie) Identyfikator interfejsu 9.  
  
 `DerivedType`  
 Typ pochodny.  
  
 `BaseType`  
 Typ podstawowy typu pochodnego.  
  
 `hasImplements`  
 Wartość logiczna, że jeśli `true`, oznacza, że nie można użyć [domieszki](../windows/mixin-structure.md) struktury z klasy, która nie pochodzi od [implementuje](../windows/implements-structure.md) stucture.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="protected-methods"></a>Metody chronione  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[ChainInterfaces::CanCastTo, metoda](../windows/chaininterfaces-cancastto-method.md)|Wskazuje, czy identyfikator określonego interfejsu, mogą być rzutowane na każdej specjalizacje zdefiniowane przez ChainInterface parametrów szablonu.|  
|[ChainInterfaces::CastToUnknown, metoda](../windows/chaininterfaces-casttounknown-method.md)|Rzutuje wskaźnik interfejsu z typem zdefiniowanym przez `I0` parametr szablonu na wskaźnik do elementu IUnknown.|  
|[ChainInterfaces::FillArrayWithIid, metoda](../windows/chaininterfaces-fillarraywithiid-method.md)|Identyfikator interfejsu zdefiniowanych przez magazynów `I0` parametr szablonu do określonej lokalizacji w określonej tablicy interfejsu identyfikatorów.|  
|[ChainInterfaces::Verify, metoda](../windows/chaininterfaces-verify-method.md)|Sprawdza, czy każdy interfejs zdefiniowane przez parametry szablonu `I0` za pośrednictwem `I9` dziedziczy IUnknown i/lub IInspectable oraz że `I0` dziedziczy `I1` za pośrednictwem `I9`.|  
  
### <a name="protected-constants"></a>Stałe chronione  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[ChainInterfaces::IidCount, stała](../windows/chaininterfaces-iidcount-constant.md)|Całkowita liczba interfejsu identyfikatorów zawarte w interfejsach określona przez parametry szablonu `I0` za pośrednictwem `I9`.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `I0`  
  
 `ChainInterfaces`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** implements.h  
  
 **Namespace:** Microsoft::wrl —  
  
## <a name="see-also"></a>Zobacz też  
 [Microsoft::WRL, przestrzeń nazw](../windows/microsoft-wrl-namespace.md)