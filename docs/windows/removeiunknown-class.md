---
title: Removeiunknown — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::Details::RemoveIUnknown
dev_langs:
- C++
ms.assetid: 998e711a-7d1a-44c6-a016-e6167aa40863
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: eb005bc3cbf411a7d5b5ddbfa44cd6aecf802105
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
---
# <a name="removeiunknown-class"></a>RemoveIUnknown — Klasa
Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.  
  
## <a name="syntax"></a>Składnia  
  
```  
template <  
   typename T  
>  
struct RemoveIUnknown;  
  
template <  
   typename T  
>  
class RemoveIUnknown : public T;  
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Klasa.  
  
## <a name="remarks"></a>Uwagi  
 Sprawia, że typ, który jest odpowiednikiem `IUnknown`— oparte na typie, ale ma niewirtualne `QueryInterface`, `AddRef`, i `Release` funkcji elementów członkowskich.  
  
 Domyślnie metody COM udostępniają wirtualnego `QueryInterface`, `AddRef`, wersja: metody. Jednak `ComPtr` nie wymaga obciążenie metodach wirtualnych. `RemoveIUnknown` eliminuje koszty tego zapewniając prywatne i niewirtualna `QueryInterface`, `AddRef`, i `Release` metody.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-typedefs"></a>Definicje typów publicznych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|`ReturnType`|Synonim dla typu, który jest odpowiednikiem parametru szablonu `T` , ale ma niewirtualne członków IUnknown.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `T`  
  
 `RemoveIUnknown`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** client.h  
  
 **Namespace:** Microsoft::wrl:: details —  
  
## <a name="see-also"></a>Zobacz też  
 [Microsoft::WRL::Details, przestrzeń nazw](../windows/microsoft-wrl-details-namespace.md)