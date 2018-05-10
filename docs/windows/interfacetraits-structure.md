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
ms.openlocfilehash: 4203fbb639b06e7e421809f9d901c70933d586d1
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
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
  
#### <a name="parameters"></a>Parametry  
 `I0`  
 Nazwa interfejsu.  
  
 `CloakedType`  
 Runtimeclass —, narzędzi i chaininterfaces — interfejs, który nie będzie na liście obsługiwanych identyfikatorów interfejsu.  
  
## <a name="remarks"></a>Uwagi  
 Wspólne cechy zawiera implementację interfejsu.  
  
 Drugi szablon jest osłonięty interfejsów. Trzeci szablonu jest Nil parametrów.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-typedefs"></a>Definicje typów publicznych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|`Base`|Jest to synonim `I0` parametru szablonu.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[InterfaceTraits::CanCastTo, metoda](../windows/interfacetraits-cancastto-method.md)|Wskazuje, czy określony wskaźnik mogą być rzutowane na wskaźnik do `Base`.|  
|[InterfaceTraits::CastToBase, metoda](../windows/interfacetraits-casttobase-method.md)|Rzutuje określony wskaźnik na wskaźnik do `Base`.|  
|[InterfaceTraits::CastToUnknown, metoda](../windows/interfacetraits-casttounknown-method.md)|Rzutuje określony wskaźnik na wskaźnik do elementu IUnknown.|  
|[InterfaceTraits::FillArrayWithIid, metoda](../windows/interfacetraits-fillarraywithiid-method.md)|Przypisuje identyfikator interfejsu `Base` do elementu tablicy argumentu indeksu.|  
|[InterfaceTraits::Verify, metoda](../windows/interfacetraits-verify-method.md)|Sprawdza, czy poprawnie pochodzi Base.|  
  
### <a name="public-constants"></a>Publiczny — stałe  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[InterfaceTraits::IidCount, stała](../windows/interfacetraits-iidcount-constant.md)|Przechowuje numer interfejsu identyfikatory z bieżącym obiektem interfacetraits —.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `InterfaceTraits`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** implements.h  
  
 **Namespace:** Microsoft::wrl:: details —  
  
## <a name="see-also"></a>Zobacz też  
 [Microsoft::WRL::Details, przestrzeń nazw](../windows/microsoft-wrl-details-namespace.md)