---
title: "Comptrrefbase — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: client/Microsoft::WRL::Details::ComPtrRefBase
dev_langs: C++
helpviewer_keywords: ComPtrRefBase class
ms.assetid: 6d344c1a-cc13-4a3f-8a0d-f167ccb9348f
caps.latest.revision: "5"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 2c010b85095da67a91c0b4c1df6f3da7a4f677dd
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
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
|[ComPtrRefBase::operator IInspectable ** — Operator](../windows/comptrrefbase-operator-iinspectable-star-star-operator.md)|Rzutuje bieżącego [ptr_ — element](../windows/comptrrefbase-ptr-data-member.md) elementu członkowskiego danych do wskaźnik do a wskaźnik do interfejsie IInspectable.|  
|[ComPtrRefBase::operator IUnknown ** — Operator](../windows/comptrrefbase-operator-iunknown-star-star-operator.md)|Rzutuje bieżącego [ptr_ — element](../windows/comptrrefbase-ptr-data-member.md) elementu członkowskiego danych do wskaźnik do a wskaźnik do interfejsu IUnknown.|  
  
### <a name="protected-data-members"></a>Dane chronione elementy członkowskie  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[Comptrrefbase::ptr_ — członek danych](../windows/comptrrefbase-ptr-data-member.md)|Wskaźnik do typu określonego przez parametr bieżącego szablonu.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `ComPtrRefBase`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** client.h  
  
 **Namespace:** Microsoft::wrl:: details —  
  
## <a name="see-also"></a>Zobacz też  
 [Microsoft::wrl:: details — Namespace](../windows/microsoft-wrl-details-namespace.md)