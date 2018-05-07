---
title: Irowsetcreatorimpl — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 0492994193130ffa6a547691490b4da1ae557c8f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
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