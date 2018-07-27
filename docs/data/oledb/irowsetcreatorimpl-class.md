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
- IRowsetCreatorImpl.SetSite
- IRowsetCreatorImpl<T>::SetSite
- IRowsetCreatorImpl::SetSite
- SetSite
- ATL.IRowsetCreatorImpl.SetSite
- ATL::IRowsetCreatorImpl<T>::SetSite
- ATL::IRowsetCreatorImpl::SetSite
- ATL.IRowsetCreatorImpl<T>.SetSite
dev_langs:
- C++
helpviewer_keywords:
- IRowsetCreatorImpl class
- SetSite method
ms.assetid: 92cc950f-7978-4754-8d9a-defa63867d82
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: b8d43c0824b2f4783b9a09782360940fb1327d99
ms.sourcegitcommit: e5792fcb89b9ba64c401f90f4f26a8e45d4a2359
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2018
ms.locfileid: "39322062"
---
# <a name="irowsetcreatorimpl-class"></a>IRowsetCreatorImpl — Klasa
Wykonuje te same funkcje co `IObjectWithSite` , lecz także właściwości OLE DB `DBPROPCANSCROLLBACKWARDS DBPROPCANFETCHBACKWARDS`.  
  
## <a name="syntax"></a>Składnia

```cpp
template < class T >  
class ATL_NO_VTABLE IRowsetCreatorImpl   
   : public IObjectWithSiteImpl< T >  
```  
  
### <a name="parameters"></a>Parametry  
 *T*  
 Klasa pochodząca z `IRowsetCreator`.  

## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldb.h  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="methods"></a>Metody  
  
|||  
|-|-|  
|[Setsite —](#setsite)|Określa lokację, która zawiera obiektu zestawu wierszy.|  
  
## <a name="remarks"></a>Uwagi  
 Ta klasa dziedziczy [IObjectWithSite](http://msdn.microsoft.com/library/windows/desktop/ms693765) i zastępuje [IObjectWithSite::SetSite](http://msdn.microsoft.com/library/windows/desktop/ms683869). Gdy obiekt polecenia lub sesji dostawcy tworzy zestawu wierszy, wywołuje `QueryInterface` obiektu zestawu wierszy, wyszukiwanie `IObjectWithSite` i wywołania `SetSite` przekazanie obiektu zestawu wierszy `IUnkown` interfejs jako interfejs witryny.  

## <a name="setsite"></a> IRowsetCreatorImpl::SetSite
Określa lokację, która zawiera obiektu zestawu wierszy. Aby uzyskać więcej informacji, zobacz [IObjectWithSite::SetSite](http://msdn.microsoft.com/library/windows/desktop/ms683869).  
  
### <a name="syntax"></a>Składnia  
  
```cpp
      STDMETHOD(SetSite )(IUnknown* pCreator);  
```  
  
#### <a name="parameters"></a>Parametry  
 *pCreator*  
 [in] Wskaźnik do `IUnknown` wskaźnika interfejsu lokacji zarządzania obiektu zestawu wierszy.  
  
### <a name="return-value"></a>Wartość zwracana  
 Standardowa HRESULT.  
  
### <a name="remarks"></a>Uwagi  
 Ponadto `IRowsetCreatorImpl::SetSite` umożliwia OLE DB `DBPROPCANSCROLLBACKWARDS DBPROPCANFETCHBACKWARDS` właściwości. 

## <a name="see-also"></a>Zobacz też  
 [Szablony dostawców OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Architektura szablonu dostawcy OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)
