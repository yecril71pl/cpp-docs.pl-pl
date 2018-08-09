---
title: RemoveIUnknown, klasa | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: dd52dcdc5fed543d65311aaa7e8a61a9d2019b8a
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2018
ms.locfileid: "40020294"
---
# <a name="removeiunknown-class"></a>RemoveIUnknown — Klasa
Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
template <  
   typename T  
>  
struct RemoveIUnknown;  
  
template <  
   typename T  
>  
class RemoveIUnknown : public T;  
```  
  
### <a name="parameters"></a>Parametry  
 *T*  
 Klasa.  
  
## <a name="remarks"></a>Uwagi  
 Tworzy typ, który jest odpowiednikiem `IUnknown`— na podstawie typu, ale ma niewirtualne `QueryInterface`, `AddRef`, i `Release` funkcji elementów członkowskich.  
  
 Domyślnie metody COM zapewniają wirtualnego `QueryInterface`, `AddRef`, i `Release` metody. Jednak `ComPtr` nie wymaga pracy związanej z metod wirtualnych. `RemoveIUnknown` eliminuje obciążenie tego, zapewniając prywatne i niewirtualne `QueryInterface`, `AddRef`, i `Release` metody.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-typedefs"></a>Publiczne definicje typów  
  
|Nazwa|Opis|  
|----------|-----------------|  
|`ReturnType`|Synonim dla typu, który jest odpowiednikiem parametru szablonu *T* , ale ma niewirtualne `IUnknown` elementów członkowskich.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `T`  
  
 `RemoveIUnknown`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** client.h  
  
 **Namespace:** Microsoft::wrl:: details  
  
## <a name="see-also"></a>Zobacz też  
 [Microsoft::WRL::Details, przestrzeń nazw](../windows/microsoft-wrl-details-namespace.md)