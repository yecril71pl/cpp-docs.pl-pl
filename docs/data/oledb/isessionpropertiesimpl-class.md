---
title: Isessionpropertiesimpl — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ISessionPropertiesImpl
dev_langs:
- C++
helpviewer_keywords:
- ISessionPropertiesImpl class
ms.assetid: ca0ba254-c7dc-4c52-abec-cf895a0c6a63
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 62b1321c9d7d50ff2cd459b395efa1e8147a06ea
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33106052"
---
# <a name="isessionpropertiesimpl-class"></a>ISessionPropertiesImpl — Klasa
Udostępnia implementację elementu [ISessionProperties](https://msdn.microsoft.com/en-us/library/ms713721.aspx) interfejsu.  
  
## <a name="syntax"></a>Składnia

```cpp
template <class T, class PropClass = T>  
class ATL_NO_VTABLE ISessionPropertiesImpl :  
   public ISessionProperties,    
   public CUtlProps<PropClass>  
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Z klasą pochodną `ISessionPropertiesImpl`.  
  
 `PropClass`  
 Klasa właściwości definiowane przez użytkownika, która domyślnie `T`.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="interface-methods"></a>Metody interfejsu  
  
|||  
|-|-|  
|[GetProperties](../../data/oledb/isessionpropertiesimpl-getproperties.md)|Zwraca listę właściwości grupy właściwości sesji, które są aktualnie ustawione w tej sesji.|  
|[SetProperties](../../data/oledb/isessionpropertiesimpl-setproperties.md)|Ustawia właściwości w grupie właściwości sesji.|  
  
## <a name="remarks"></a>Uwagi  
 Obowiązkowego interfejsu na sesji. Ta klasa implementuje właściwości sesji przez wywołanie metody statycznej funkcji zdefiniowanej przez [mapę zestaw właściwości](../../data/oledb/begin-propset-map.md). Mapa zestaw właściwości powinny być określone w klasie sesji.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldb.h  
  
## <a name="see-also"></a>Zobacz też  
 [Szablony dostawców OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Architektura szablonu dostawcy OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)