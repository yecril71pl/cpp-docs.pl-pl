---
title: Comptrrefbase — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::Details::ComPtrRefBase
dev_langs:
- C++
helpviewer_keywords:
- ComPtrRefBase class
ms.assetid: 6d344c1a-cc13-4a3f-8a0d-f167ccb9348f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 13744a1629ede5575dc992ea15b90e22961a8570
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
---
# <a name="comptrrefbase-class"></a>ComPtrRefBase — Klasa
Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.  
  
## <a name="syntax"></a>Składnia  
  
```  
template <  
   typename T  
>  
class ComPtrRefBase;  
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 A [comptr —\<T >](../windows/comptr-class.md) typu lub typu pochodnego w nie tylko interfejs reprezentowany przez comptr —.  
  
## <a name="remarks"></a>Uwagi  
 Reprezentuje klasę podstawową dla [comptrref —](../windows/comptrref-class.md) klasy.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-typedefs"></a>Definicje typów publicznych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|`InterfaceType`|Synonim dla typu parametru szablonu `T`.|  
  
### <a name="public-operators"></a>Operatory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[Operator ComPtrRefBase::operator IInspectable**](../windows/comptrrefbase-operator-iinspectable-star-star-operator.md)|Rzutuje bieżącego [ptr_ — element](../windows/comptrrefbase-ptr-data-member.md) elementu członkowskiego danych do wskaźnik do a wskaźnik do interfejsie IInspectable.|  
|[Operator ComPtrRefBase::operator IUnknown**](../windows/comptrrefbase-operator-iunknown-star-star-operator.md)|Rzutuje bieżącego [ptr_ — element](../windows/comptrrefbase-ptr-data-member.md) elementu członkowskiego danych do wskaźnik do a wskaźnik do interfejsu IUnknown.|  
  
### <a name="protected-data-members"></a>Dane chronione elementy członkowskie  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[ComPtrRefBase::ptr_, składowa danych](../windows/comptrrefbase-ptr-data-member.md)|Wskaźnik do typu określonego przez parametr bieżącego szablonu.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `ComPtrRefBase`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** client.h  
  
 **Namespace:** Microsoft::wrl:: details —  
  
## <a name="see-also"></a>Zobacz też  
 [Microsoft::WRL::Details, przestrzeń nazw](../windows/microsoft-wrl-details-namespace.md)