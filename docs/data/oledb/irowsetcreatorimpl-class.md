---
title: "Irowsetcreatorimpl — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ATL::IRowsetCreatorImpl
- ATL.IRowsetCreatorImpl
- ATL::IRowsetCreatorImpl<T>
- ATL.IRowsetCreatorImpl<T>
- IRowsetCreatorImpl
dev_langs:
- C++
helpviewer_keywords:
- IRowsetCreatorImpl class
ms.assetid: 92cc950f-7978-4754-8d9a-defa63867d82
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 51d984f2254c8a2a135b5ecb386e8f195946366b
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="irowsetcreatorimpl-class"></a>IRowsetCreatorImpl — Klasa
Wykonuje te same funkcje jak `IObjectWithSite` , lecz także właściwości OLE DB **DBPROPCANSCROLLBACKWARDS DBPROPCANFETCHBACKWARDS**.  
  
## <a name="syntax"></a>Składnia

```cpp
template < class T >  
class ATL_NO_VTABLE IRowsetCreatorImpl   
   : public IObjectWithSiteImpl< T >  
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Klasa pochodna od **IRowsetCreator**.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="methods"></a>Metody  
  
|||  
|-|-|  
|[SetSite](../../data/oledb/irowsetcreatorimpl-setsite.md)|Określa lokację, która zawiera obiekt zestawu wierszy.|  
  
## <a name="remarks"></a>Uwagi  
 Ta klasa dziedziczy [IObjectWithSite](http://msdn.microsoft.com/library/windows/desktop/ms693765) i zastępuje [IObjectWithSite::SetSite](http://msdn.microsoft.com/library/windows/desktop/ms683869). Gdy obiekt dostawcy polecenia lub sesji tworzy zestawu wierszy, wywołuje `QueryInterface` obiektu zestawu wierszy wyszukiwanie `IObjectWithSite` i wywołania `SetSite` przekazywanie obiektu zestawu wierszy **IUnkown** interfejsu jako interfejsu lokacji.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldb.h  
  
## <a name="see-also"></a>Zobacz też  
 [Szablony dostawców OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Architektura szablonu dostawcy OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)