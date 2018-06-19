---
title: Implementuje struktury | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 1ecbf0b77feef7abeb67f8d0dc300da067d1f2da
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33880923"
---
# <a name="implements-structure"></a>Implements — Struktura
Implementuje metody QueryInterface i GetIid dla określonych interfejsów.  
  
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
  
#### <a name="parameters"></a>Parametry  
 `I0`  
 Identyfikator zeroth interfejsu. (Wymagane)  
  
 `I1`  
 Pierwszy identyfikator interfejsu. (opcjonalnie)  
  
 `I2`  
 Drugi identyfikatora interfejsu. (opcjonalnie)  
  
 `I3`  
 Trzeci identyfikatora interfejsu. (opcjonalnie)  
  
 `I4`  
 Czwarty identyfikatora interfejsu. (opcjonalnie)  
  
 `I5`  
 Piąty identyfikatora interfejsu. (opcjonalnie)  
  
 `I6`  
 Szóstym identyfikatora interfejsu. (opcjonalnie)  
  
 `I7`  
 Siódmego identyfikatora interfejsu. (opcjonalnie)  
  
 `I8`  
 Identyfikator osiem interfejsu. (opcjonalnie)  
  
 `I9`  
 Dziewiąty identyfikatora interfejsu. (opcjonalnie)  
  
 `flags`  
 Konfiguracja flagi dla tej klasy. Co najmniej jeden [runtimeclasstype —](../windows/runtimeclasstype-enumeration.md) wyliczenia, które są określone w [runtimeclassflags —](../windows/runtimeclassflags-structure.md) struktury.  
  
## <a name="remarks"></a>Uwagi  
 Pochodzi z listy określonych interfejsów i implementuje szablony pomocnika QueryInterface i GetIid.  
  
 Każdy `I0` za pośrednictwem `I9` parametru interfejs musi pochodzić od elementu IUnknown, albo IInspectable, lub [chaininterfaces —](../windows/chaininterfaces-structure.md) szablonu. `flags` Parametr określa, czy obsługa jest generowany IUnknown lub IInspectable.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-typedefs"></a>Definicje typów publicznych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|`ClassFlags`|Jest to synonim `RuntimeClassFlags<WinRt>`.|  
  
### <a name="protected-methods"></a>Metody chronione  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[Implements::CanCastTo, metoda](../windows/implements-cancastto-method.md)|Pobiera wskaźnik do określonego interfejsu.|  
|[Implements::CastToUnknown, metoda](../windows/implements-casttounknown-method.md)|Pobiera wskaźnik do podstawowego interfejsu IUnknown.|  
|[Implements::FillArrayWithIid, metoda](../windows/implements-fillarraywithiid-method.md)|Wstawia podany identyfikator interfejsu przez bieżący parametr szablonu zeroth w element określonej tablicy.|  
  
### <a name="protected-constants"></a>Stałe chronione  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[Implements::IidCount, stała](../windows/implements-iidcount-constant.md)|Przechowuje numer zaimplementowany interfejs identyfikatorów.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `I0`  
  
 `ChainInterfaces`  
  
 `I0`  
  
 `ImplementsBase`  
  
 `ImplementsHelper`  
  
 `Implements`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** implements.h  
  
 **Namespace:** Microsoft::wrl —  
  
## <a name="see-also"></a>Zobacz też  
 [Microsoft::WRL, przestrzeń nazw](../windows/microsoft-wrl-namespace.md)