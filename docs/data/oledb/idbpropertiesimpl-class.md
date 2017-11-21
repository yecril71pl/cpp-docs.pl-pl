---
title: "Idbpropertiesimpl — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDBPropertiesImpl
- ATL.IDBPropertiesImpl
- ATL.IDBPropertiesImpl<T>
- ATL::IDBPropertiesImpl<T>
- ATL::IDBPropertiesImpl
dev_langs: C++
helpviewer_keywords: IDBPropertiesImpl class
ms.assetid: a7f15a8b-95b2-4316-b944-d5d03f8d74ab
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 98dd7c0ea8000d2f86283cadb9a92fd2caa059a9
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="idbpropertiesimpl-class"></a>IDBPropertiesImpl — Klasa
Udostępnia implementację dla `IDBProperties` interfejsu.  
  
## <a name="syntax"></a>Składnia  
  
```  
template <class T>   
class ATL_NO_VTABLE IDBPropertiesImpl   
   : public IDBProperties, public CUtlProps<T>  
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Z klasą pochodną `IDBPropertiesImpl`.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="interface-methods"></a>Metody interfejsu  
  
|||  
|-|-|  
|[GetProperties](../../data/oledb/idbpropertiesimpl-getproperties.md)|Zwraca wartości właściwości w grupach właściwości źródła danych, informacje o źródle danych i inicjowania, aktualnie ustawione dla obiekt źródła danych lub wartości właściwości w grupie właściwości Initialization, które są aktualnie ustawione na Moduł wyliczający.|  
|[GetPropertyInfo](../../data/oledb/idbpropertiesimpl-getpropertyinfo.md)|Zwraca informacje o wszystkich właściwości obsługiwane przez dostawcę.|  
|[SetProperties](../../data/oledb/idbpropertiesimpl-setproperties.md)|Ustawia właściwości źródła danych i inicjalizacji grup właściwości, dla obiekty źródła danych, lub grupie właściwości Initialization dla wyliczenia.|  
  
## <a name="remarks"></a>Uwagi  
 [IDBProperties](https://msdn.microsoft.com/en-us/library/ms719607.aspx) obowiązkowego interfejsu dla obiekty źródła danych i opcjonalny interfejs dla wyliczenia. Jednak jeśli udostępnia moduł wyliczający [IDBInitialize](https://msdn.microsoft.com/en-us/library/ms713706.aspx), musi on ujawniać `IDBProperties`. `IDBPropertiesImpl`implementuje `IDBProperties` przy użyciu statycznych funkcji zdefiniowanej przez [BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md).  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldb.h  
  
## <a name="see-also"></a>Zobacz też  
 [Szablony dostawców OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Architektura szablonu dostawcy OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)