---
title: Interfacetraits — struktura | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::InterfaceTraits
dev_langs:
- C++
helpviewer_keywords:
- InterfaceTraits structure
ms.assetid: ede0c284-19a7-4892-9738-ff3da4923d0a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 63725d5d3e0edaea328d5753640aa74bdf35c7e0
ms.sourcegitcommit: 4586bfc32d8bc37ab08b24816d7fad5df709bfa3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2018
ms.locfileid: "39606751"
---
# <a name="interfacetraits-structure"></a>InterfaceTraits — Struktura
Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.  
  
## <a name="syntax"></a>Składnia  
  
```  
template<  
   typename I0  
>  
struct __declspec(novtable) InterfaceTraits;  
template<typename CloakedType>  
struct __declspec(novtable) InterfaceTraits<CloakedIid<CloakedType>>;  
  
template<>  
struct __declspec(novtable) InterfaceTraits<Nil>;  
```  
  
### <a name="parameters"></a>Parametry  
 *I0*  
 Nazwa interfejsu.  
  
 *CloakedType*  
 Aby uzyskać `RuntimeClass`, `Implements` i `ChainInterfaces`, interfejs, który nie będzie na liście obsługiwanych identyfikatorami interfejsu.  
  
## <a name="remarks"></a>Uwagi  
 Implementuje typowe cechy interfejsu.  
  
 Drugi szablon jest specjalizacją osłonięty interfejsów. Trzeci szablon jest specjalizacją zero parametrów.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-typedefs"></a>Publiczne definicje typów  
  
|Nazwa|Opis|  
|----------|-----------------|  
|`Base`|Synonim dla *I0* parametru szablonu.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[InterfaceTraits::CanCastTo, metoda](../windows/interfacetraits-cancastto-method.md)|Wskazuje, czy określony wskaźnik może być rzutowany na wskaźnik do `Base`.|  
|[InterfaceTraits::CastToBase, metoda](../windows/interfacetraits-casttobase-method.md)|Rzutuje określony wskaźnik do wskaźnika do `Base`.|  
|[InterfaceTraits::CastToUnknown, metoda](../windows/interfacetraits-casttounknown-method.md)|Rzutuje określony wskaźnik do wskaźnika do `IUnknown`.|  
|[InterfaceTraits::FillArrayWithIid, metoda](../windows/interfacetraits-fillarraywithiid-method.md)|Przypisuje identyfikator interfejsu `Base` do elementu tablicy, określonego przez argument indeksu.|  
|[InterfaceTraits::Verify, metoda](../windows/interfacetraits-verify-method.md)|Sprawdza, prawidłowo pochodzi Base.|  
  
### <a name="public-constants"></a>Publiczne stałe  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[InterfaceTraits::IidCount, stała](../windows/interfacetraits-iidcount-constant.md)|Przechowuje liczbę interfejsu identyfikatorów skojarzonych z bieżącym **interfacetraits —** obiektu.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `InterfaceTraits`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** implements.h  
  
 **Namespace:** Microsoft::wrl:: details  
  
## <a name="see-also"></a>Zobacz też  
 [Microsoft::WRL::Details, przestrzeń nazw](../windows/microsoft-wrl-details-namespace.md)