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
dev_langs:
- C++
helpviewer_keywords:
- IGetDataSourceImpl class
ms.assetid: d63f3178-d663-4f01-8c09-8aab2dd6805a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 50ffa3f176bbd5691a3ea0bc4e23aa8245712e17
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="igetdatasourceimpl-class"></a>IGetDataSourceImpl — Klasa
Udostępnia implementację elementu [IGetDataSource](https://msdn.microsoft.com/en-us/library/ms709721.aspx) obiektu.  
  
## <a name="syntax"></a>Składnia

```cpp
template <class T>  
class ATL_NO_VTABLE IGetDataSourceImpl : public IGetDataSource  
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Z klasą pochodną `IGetDataSourceImpl`.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="interface-methods"></a>Metody interfejsu  
  
|||  
|-|-|  
|[GetDataSource](../../data/oledb/igetdatasourceimpl-getdatasource.md)|Zwraca obiekt źródła danych, która utworzona sesja wskaźnika interfejsu.|  
  
## <a name="remarks"></a>Uwagi  
 W tej sesji do uzyskiwania wskaźnika interfejsu do obiektu źródła danych jest obowiązkowego interfejsu.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldb.h  
  
## <a name="see-also"></a>Zobacz też  
 [Szablony dostawców OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Architektura szablonu dostawcy OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)