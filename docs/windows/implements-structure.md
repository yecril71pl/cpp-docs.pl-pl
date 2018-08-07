---
title: Struktura implementuje | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Implements
dev_langs:
- C++
helpviewer_keywords:
- Implements structure
ms.assetid: 29b13e90-34d4-4a0b-babd-5187c9eb0c36
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 0dc23a9c90fc2112d67180ceae86ebde0e057b06
ms.sourcegitcommit: 4586bfc32d8bc37ab08b24816d7fad5df709bfa3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2018
ms.locfileid: "39607809"
---
# <a name="implements-structure"></a>Implements — Struktura
Implementuje `QueryInterface` i `GetIid` dla określonych interfejsów.  
  
## <a name="syntax"></a>Składnia  
  
```  
template <  
   typename I0,  
   typename I1 = Details::Nil,  
   typename I2 = Details::Nil,  
   typename I3 = Details::Nil,  
   typename I4 = Details::Nil,  
   typename I5 = Details::Nil,  
   typename I6 = Details::Nil,  
   typename I7 = Details::Nil,  
   typename I8 = Details::Nil,  
   typename I9 = Details::Nil  
>  
struct __declspec(novtable) Implements : Details::ImplementsHelper<RuntimeClassFlags<WinRt>, typename Details::InterfaceListHelper<I0, I1, I2, I3, I4, I5, I6, I7, I8, I9>::TypeT>, Details::ImplementsBase;  
template <  
   int flags,  
   typename I0,  
   typename I1,  
   typename I2,  
   typename I3,  
   typename I4,  
   typename I5,  
   typename I6,  
   typename I7,  
   typename I8  
>  
struct __declspec(novtable) Implements<RuntimeClassFlags<flags>, I0, I1, I2, I3, I4, I5, I6, I7, I8> : Details::ImplementsHelper<RuntimeClassFlags<flags>, typename Details::InterfaceListHelper<I0, I1, I2, I3, I4, I5, I6, I7, I8>::TypeT>, Details::ImplementsBase;  
```  
  
### <a name="parameters"></a>Parametry  
 *I0*  
 Identyfikator interfejsu zerowego. (Obowiązkowe)  
  
 *I1*  
 Identyfikator pierwszego interfejsu. (opcjonalnie)  
  
 *I2*  
 Identyfikator drugiego interfejsu. (opcjonalnie)  
  
 *I3*  
 Identyfikator trzeciego interfejsu. (opcjonalnie)  
  
 *I4*  
 Identyfikator czwartego interfejsu. (opcjonalnie)  
  
 *I5*  
 Identyfikator piątego interfejsu. (opcjonalnie)  
  
 *I6*  
 Identyfikator szóstego interfejsu. (opcjonalnie)  
  
 *I7*  
 Identyfikator siódmego interfejsu. (opcjonalnie)  
  
 *I8*  
 Identyfikator ósmego interfejsu. (opcjonalnie)  
  
 *I9*  
 Identyfikator dziewiątego interfejsu. (opcjonalnie)  
  
 *flagi*  
 Flagi konfiguracji dla klasy. Co najmniej jeden [RuntimeClassType](../windows/runtimeclasstype-enumeration.md) wyliczenia, które są określone w [runtimeclassflags —](../windows/runtimeclassflags-structure.md) struktury.  
  
## <a name="remarks"></a>Uwagi  
 Pochodzi z listy określonych interfejsów i implementuje szablony pomocnika na potrzeby `QueryInterface` i `GetIid`.  
  
 Każdy *I0* za pośrednictwem *I9* parametru interfejs musi pochodzić z klasy `IUnknown`, `IInspectable`, lub [chaininterfaces —](../windows/chaininterfaces-structure.md) szablonu. *Flagi* parametr określa, czy obsługa jest generowany dla `IUnknown` lub `IInspectable`.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-typedefs"></a>Publiczne definicje typów  
  
|Nazwa|Opis|  
|----------|-----------------|  
|`ClassFlags`|Synonim dla `RuntimeClassFlags<WinRt>`.|  
  
### <a name="protected-methods"></a>Metody chronione  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[Implements::CanCastTo, metoda](../windows/implements-cancastto-method.md)|Pobiera wskaźnik do określonego interfejsu.|  
|[Implements::CastToUnknown, metoda](../windows/implements-casttounknown-method.md)|Pobiera wskaźnik do bazowego `IUnknown` interfejsu.|  
|[Implements::FillArrayWithIid, metoda](../windows/implements-fillarraywithiid-method.md)|Wstawia identyfikator interfejsu określonego przez bieżący parametr szablonu zerowego do elementu określonej tablicy.|  
  
### <a name="protected-constants"></a>Stałe chronione  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[Implements::IidCount, stała](../windows/implements-iidcount-constant.md)|Przechowuje liczbę zaimplementowanego interfejsu identyfikatorów.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `I0`  
  
 `ChainInterfaces`  
  
 `I0`  
  
 `ImplementsBase`  
  
 `ImplementsHelper`  
  
 `Implements`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** implements.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Zobacz też  
 [Microsoft::WRL, przestrzeń nazw](../windows/microsoft-wrl-namespace.md)