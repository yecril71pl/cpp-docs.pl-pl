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
ms.openlocfilehash: 18f7f08362c14ab0d09019a5b9348750c96ddbd7
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/08/2018
ms.locfileid: "39643413"
---
# <a name="comptrrefbase-class"></a>ComPtrRefBase — Klasa
Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
template <  
   typename T  
>  
class ComPtrRefBase;  
```  
  
### <a name="parameters"></a>Parametry  
 *T*  
 A [ComPtr\<T >](../windows/comptr-class.md) typu lub typu pochodnego w nie tylko interfejs, reprezentowane przez **ComPtr**.  
  
## <a name="remarks"></a>Uwagi  
 Reprezentuje klasę bazową dla [comptrref —](../windows/comptrref-class.md) klasy.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-typedefs"></a>Publiczne definicje typów  
  
|Nazwa|Opis|  
|----------|-----------------|  
|`InterfaceType`|Synonim dla typu parametru szablonu *T*.|  
  
### <a name="public-operators"></a>Operatory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[Operator ComPtrRefBase::operator IInspectable**](../windows/comptrrefbase-operator-iinspectable-star-star-operator.md)|Rzutuje bieżącego [ptr_ — element](../windows/comptrrefbase-ptr-data-member.md) element członkowski danych do wskaźnik do a wskaźnik do `IInspectable` interfejsu.|  
|[Operator ComPtrRefBase::operator IUnknown**](../windows/comptrrefbase-operator-iunknown-star-star-operator.md)|Rzutuje bieżącego [ptr_ — element](../windows/comptrrefbase-ptr-data-member.md) element członkowski danych do wskaźnik do a wskaźnik do `IUnknown` interfejsu.|  
  
### <a name="protected-data-members"></a>Chronione elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[ComPtrRefBase::ptr_, składowa danych](../windows/comptrrefbase-ptr-data-member.md)|Wskaźnik do typu określonego przez parametr bieżącego szablonu.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `ComPtrRefBase`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** client.h  
  
 **Namespace:** Microsoft::wrl:: details  
  
## <a name="see-also"></a>Zobacz też  
 [Microsoft::WRL::Details, przestrzeń nazw](../windows/microsoft-wrl-details-namespace.md)