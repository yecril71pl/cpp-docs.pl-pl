---
title: "Icolumnsinfoimpl — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL.IColumnsInfoImpl<T>
- ATL::IColumnsInfoImpl
- IColumnsInfoImpl
- ATL.IColumnsInfoImpl
- ATL::IColumnsInfoImpl<T>
dev_langs: C++
helpviewer_keywords: IColumnsInfoImpl class
ms.assetid: ba74c1c5-2eda-4452-8b57-84919fa0d066
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 18d23120a4a84f9d637a50e379a579389354ff08
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="icolumnsinfoimpl-class"></a>IColumnsInfoImpl — Klasa
Udostępnia implementację elementu [IColumnsInfo](https://msdn.microsoft.com/en-us/library/ms724541.aspx) interfejsu.  
  
## <a name="syntax"></a>Składnia  
  
```  
template <class T>  
class ATL_NO_VTABLE IColumnsInfoImpl :   
   public IColumnsInfo,    
   public CDBIDOps  
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Z klasą pochodną `IColumnsInfoImpl`.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="methods"></a>Metody  
  
|||  
|-|-|  
|[GetColumnInfo](../../data/oledb/icolumnsinfoimpl-getcolumninfo.md)|Zwraca metadane kolumny wymagane przez większość konsumentów.|  
|[MapColumnIDs](../../data/oledb/icolumnsinfoimpl-mapcolumnids.md)|Zwraca tablicę porządkowe kolumn w zestawie wierszy, które są identyfikowane za pomocą określonej kolumny identyfikatorów.|  
  
## <a name="remarks"></a>Uwagi  
 Obowiązkowego interfejsu na polecenia i zestawy wierszy. Aby zmodyfikować zachowanie Twój dostawca `IColumnsInfo` implementacji, należy zmodyfikować dostawcy mapowania kolumn.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldb.h  
  
## <a name="see-also"></a>Zobacz też  
 [Szablony dostawców OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Architektura szablonu dostawcy OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)