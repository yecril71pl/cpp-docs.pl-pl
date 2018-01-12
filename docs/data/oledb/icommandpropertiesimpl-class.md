---
title: "Icommandpropertiesimpl — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ICommandPropertiesImpl
- ATL.ICommandPropertiesImpl
- ATL::ICommandPropertiesImpl
dev_langs: C++
helpviewer_keywords: ICommandPropertiesImpl class
ms.assetid: b3cf6aea-527e-4f0d-96e0-669178b021a2
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 5878e7fa6345e294025b45474b1b384d01283c49
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="icommandpropertiesimpl-class"></a>ICommandPropertiesImpl — Klasa
Udostępnia implementację elementu [ICommandProperties](https://msdn.microsoft.com/en-us/library/ms723044.aspx) interfejsu.  
  
## <a name="syntax"></a>Składnia  
  
```  
template <class T, class PropClass = T>  
class ATL_NO_VTABLE ICommandPropertiesImpl   
   : public ICommandProperties, public CUtlProps<PropClass>  
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Klasy pochodne  
  
 `PropClass`  
 Właściwości klasy.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="interface-methods"></a>Metody interfejsu  
  
|||  
|-|-|  
|[GetProperties](../../data/oledb/icommandpropertiesimpl-getproperties.md)|Zwraca listę właściwości, w grupie właściwości zestawu wierszy, która obecnie są wymagane dla zestawu wierszy.|  
|[SetProperties](../../data/oledb/icommandpropertiesimpl-setproperties.md)|Ustawia właściwości w grupie właściwości zestawu wierszy.|  
  
## <a name="remarks"></a>Uwagi  
 Jest to obowiązkowa w przypadku poleceń. Implementacja jest zapewniana przez statycznych funkcji zdefiniowanej przez [BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md) makra.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldb.h  
  
## <a name="see-also"></a>Zobacz też  
 [Szablony dostawców OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Architektura szablonu dostawcy OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)