---
title: Icommandpropertiesimpl — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ICommandPropertiesImpl
- ATL.ICommandPropertiesImpl
- ATL::ICommandPropertiesImpl
dev_langs:
- C++
helpviewer_keywords:
- ICommandPropertiesImpl class
ms.assetid: b3cf6aea-527e-4f0d-96e0-669178b021a2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 25be1548bd41f832a007f102c138fc01f8818774
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33099004"
---
# <a name="icommandpropertiesimpl-class"></a>ICommandPropertiesImpl — Klasa
Udostępnia implementację elementu [ICommandProperties](https://msdn.microsoft.com/en-us/library/ms723044.aspx) interfejsu.  
  
## <a name="syntax"></a>Składnia

```cpp
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