---
title: Interfacelisthelper — struktura | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::InterfaceListHelper
dev_langs:
- C++
helpviewer_keywords:
- InterfaceListHelper structure
ms.assetid: 4297e419-c96b-45df-8a00-7568062125ba
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 91012112cebf6fe33858df8904691944a810f69a
ms.sourcegitcommit: 4586bfc32d8bc37ab08b24816d7fad5df709bfa3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2018
ms.locfileid: "39608134"
---
# <a name="interfacelisthelper-structure"></a>InterfaceListHelper — Struktura
Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.  
  
## <a name="syntax"></a>Składnia  
  
```  
template <  
   typename T0,  
   typename T1 = Nil,  
   typename T2 = Nil,  
   typename T3 = Nil,  
   typename T4 = Nil,  
   typename T5 = Nil,  
   typename T6 = Nil,  
   typename T7 = Nil,  
   typename T8 = Nil,  
   typename T9 = Nil  
>  
struct InterfaceListHelper;  
  
template <  
   typename T0  
>  
struct InterfaceListHelper<T0, Nil, Nil, Nil, Nil, Nil, Nil, Nil, Nil>;  
```  
  
### <a name="parameters"></a>Parametry  
 *T0*  
 Parametr szablonu, 0, który jest wymagany.  
  
 *T1*  
 Parametr szablonu, 1, która domyślnie jest nieokreślona.  
  
 *T2*  
 Parametr szablonu, 2, która domyślnie jest nieokreślona. Trzeci parametr szablonu.  
  
 *T3*  
 Parametr szablonu, 3, która domyślnie jest nieokreślona.  
  
 *T4*  
 Parametr szablonu, 4, która domyślnie jest nieokreślona.  
  
 *T5*  
 Parametr szablonu, 5, która domyślnie jest nieokreślona.  
  
 *T6*  
 Parametr szablonu, 6, która domyślnie jest nieokreślona.  
  
 *T7*  
 Parametr szablonu, 7, która domyślnie jest nieokreślona.  
  
 *T8*  
 Parametr szablonu, 8, która domyślnie jest nieokreślona.  
  
 *T9*  
 Parametr szablonu, 9, która domyślnie jest nieokreślona.  
  
## <a name="remarks"></a>Uwagi  
 Kompilacje `InterfaceList` typu przez rekursywnie stosowanie argumentów parametru określonego szablonu.  
  
 **Interfacelisthelper —** szablon używa parametru szablonu *T0* do definiowania pierwszy element członkowski danych w `InterfaceList` struktury, a następnie rekursywnie stosuje  **Interfacelisthelper —** szablon, aby wszystkie pozostałe parametry szablonu. **Interfacelisthelper —** zatrzymuje, gdy nie ma żadnych pozostałych parametrów szablonu.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-typedefs"></a>Publiczne definicje typów  
  
|Nazwa|Opis|  
|----------|-----------------|  
|`TypeT`|Synonim dla typu interfacelist —.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `InterfaceListHelper`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** implements.h  
  
 **Namespace:** Microsoft::wrl:: details  
  
## <a name="see-also"></a>Zobacz też  
 [Microsoft::WRL::Details, przestrzeń nazw](../windows/microsoft-wrl-details-namespace.md)