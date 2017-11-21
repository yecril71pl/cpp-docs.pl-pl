---
title: "Interfacelisthelper — struktura | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: implements/Microsoft::WRL::Details::InterfaceListHelper
dev_langs: C++
helpviewer_keywords: InterfaceListHelper structure
ms.assetid: 4297e419-c96b-45df-8a00-7568062125ba
caps.latest.revision: "5"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 4465a380d24cbb9607785e958a88801c5de68b15
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
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
  
#### <a name="parameters"></a>Parametry  
 `T0`  
 Parametr szablonu 0, co jest wymagane.  
  
 `T1`  
 Parametr szablonu 1, która domyślnie jest nieokreślony.  
  
 `T2`  
 Parametr szablonu 2, która domyślnie jest nieokreślony. Trzeci parametr szablonu.  
  
 `T3`  
 Parametr szablonu 3, która domyślnie jest nieokreślony.  
  
 `T4`  
 Parametr szablonu 4, która domyślnie jest nieokreślony.  
  
 `T5`  
 Parametr szablonu 5, która domyślnie jest nieokreślony.  
  
 `T6`  
 Parametr szablonu 6, która domyślnie jest nieokreślony.  
  
 `T7`  
 Parametr szablonu 7, która domyślnie jest nieokreślony.  
  
 `T8`  
 Parametr szablonu 8, która domyślnie jest nieokreślony.  
  
 `T9`  
 Parametr szablonu 9, która domyślnie jest nieokreślony.  
  
## <a name="remarks"></a>Uwagi  
 Tworzy typ interfacelist — przy rekursywnie stosowania argumentów parametru określonego szablonu.  
  
 Szablon interfacelisthelper — używa parametru szablonu `T0` do definiowania danych pierwszego elementu członkowskiego w interfacelist — struktura, a następnie rekursywnie dotyczy szablonu interfacelisthelper — wszystkie pozostałe parametry szablonu. Interfacelisthelper — zatrzymywana, gdy nie ma żadnych pozostałych parametrów szablonu.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-typedefs"></a>Definicje typów publicznych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|`TypeT`|Synonim dla typu interfacelist —.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `InterfaceListHelper`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** implements.h  
  
 **Namespace:** Microsoft::wrl:: details —  
  
## <a name="see-also"></a>Zobacz też  
 [Microsoft::wrl:: details — Namespace](../windows/microsoft-wrl-details-namespace.md)