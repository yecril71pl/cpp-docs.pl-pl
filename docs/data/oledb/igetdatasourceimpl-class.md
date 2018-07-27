---
title: Igetdatasourceimpl — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- IGetDataSourceImpl
- ATL.IGetDataSourceImpl<T>
- ATL.IGetDataSourceImpl
- ATL::IGetDataSourceImpl
- ATL::IGetDataSourceImpl<T>
- GetDataSource
- IGetDataSourceImpl.GetDataSource
- IGetDataSourceImpl::GetDataSource
dev_langs:
- C++
helpviewer_keywords:
- IGetDataSourceImpl class
- GetDataSource method
ms.assetid: d63f3178-d663-4f01-8c09-8aab2dd6805a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 558578a82f1906d7481abebc5e1f1719b1983724
ms.sourcegitcommit: b0d6777cf4b580d093eaf6104d80a888706e7578
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/26/2018
ms.locfileid: "39269940"
---
# <a name="igetdatasourceimpl-class"></a>IGetDataSourceImpl — Klasa
Udostępnia implementację [IGetDataSource](https://msdn.microsoft.com/library/ms709721.aspx) obiektu.  
  
## <a name="syntax"></a>Składnia

```cpp
template <class T>  
class ATL_NO_VTABLE IGetDataSourceImpl : public IGetDataSource  
```  
  
### <a name="parameters"></a>Parametry  
 *T*  
 Z klasą pochodną `IGetDataSourceImpl`.  

## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldb.h  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="interface-methods"></a>Metody interfejsu  
  
|||  
|-|-|  
|[GetDataSource](#getdatasource)|Zwraca wskaźnik interfejsu na obiekt źródła danych, do utworzenia sesji.|  
  
## <a name="remarks"></a>Uwagi  
 To obowiązkowego interfejsu na sesję umożliwiającą uzyskanie wskaźnika interfejsu do obiektu źródła danych.  

## <a name="getdatasource"></a> IGetDataSourceImpl::GetDataSource
Zwraca wskaźnik interfejsu na obiekt źródła danych, do utworzenia sesji.  
  
### <a name="syntax"></a>Składnia  
  
```cpp
      STDMETHOD(GetDataSource)(REFIID riid,   
   IUnknown ** ppDataSource);  
```  
  
#### <a name="parameters"></a>Parametry  
 Zobacz [IGetDataSource::GetDataSource](https://msdn.microsoft.com/library/ms725443.aspx) w *OLE DB Podręcznik programisty*.  
  
### <a name="remarks"></a>Uwagi  
 Parametr jest przydatne, jeśli potrzebujesz uzyskać dostęp do właściwości w obiekcie źródła danych.  
  
## <a name="see-also"></a>Zobacz też  
 [Szablony dostawców OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Architektura szablonu dostawcy OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)
