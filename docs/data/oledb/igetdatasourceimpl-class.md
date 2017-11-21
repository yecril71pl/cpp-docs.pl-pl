---
title: "Igetdatasourceimpl — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IGetDataSourceImpl
- ATL.IGetDataSourceImpl<T>
- ATL.IGetDataSourceImpl
- ATL::IGetDataSourceImpl
- ATL::IGetDataSourceImpl<T>
dev_langs: C++
helpviewer_keywords: IGetDataSourceImpl class
ms.assetid: d63f3178-d663-4f01-8c09-8aab2dd6805a
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 8af6a2a782bb72a7b306bfdfeda9ebf3a1800a93
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="igetdatasourceimpl-class"></a>IGetDataSourceImpl — Klasa
Udostępnia implementację elementu [IGetDataSource](https://msdn.microsoft.com/en-us/library/ms709721.aspx) obiektu.  
  
## <a name="syntax"></a>Składnia  
  
```  
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