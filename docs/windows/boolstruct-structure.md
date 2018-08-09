---
title: Boolstruct — struktura | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- internal/Microsoft::WRL::Details::BoolStruct
dev_langs:
- C++
helpviewer_keywords:
- BoolStruct structure
ms.assetid: 666eae78-e81d-4fb7-a9e4-1ba617d6d4cd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 14e3d81ca273bf96b4812f08a46904c9d521c5cf
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/08/2018
ms.locfileid: "39650485"
---
# <a name="boolstruct-structure"></a>BoolStruct — Struktura
Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
struct BoolStruct;  
```  
  
## <a name="remarks"></a>Uwagi  
 **Boolstruct —** definiuje strukturę czy `ComPtr` Zarządzanie okresem istnienia interfejsu. **Boolstruct —** jest używana wewnętrznie przez [BoolType()](../windows/comptr-operator-microsoft-wrl-details-booltype-operator.md) operatora.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-data-members"></a>Publiczne elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[BoolStruct::Member, składowa danych](../windows/boolstruct-member-data-member.md)|Określa, że [ComPtr](../windows/comptr-class.md) jest lub nie jest dostępna, zarządzanie okresem istnienia obiektu interfejsu.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `BoolStruct`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** internal.h  
  
 **Namespace:** Microsoft::wrl:: details  
  
## <a name="see-also"></a>Zobacz też  
 [Microsoft::wrl:: details Namespace](../windows/microsoft-wrl-details-namespace.md)   
 [Operator ComPtr::operator Microsoft::WRL::Details::BoolType](../windows/comptr-operator-microsoft-wrl-details-booltype-operator.md)