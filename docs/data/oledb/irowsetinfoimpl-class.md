---
title: "Irowsetinfoimpl — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL.IRowsetInfoImpl
- IRowsetInfoImpl
- ATL::IRowsetInfoImpl
dev_langs: C++
helpviewer_keywords: IRowsetInfoImpl class
ms.assetid: 9c654155-7727-464e-bd31-143e68391a47
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: d34fdaa37901d8bdce3dce312d674024a84ad0e8
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="irowsetinfoimpl-class"></a>IRowsetInfoImpl — Klasa
Udostępnia implementację dla [IRowsetInfo](https://msdn.microsoft.com/en-us/library/ms724541.aspx) interfejsu.  
  
## <a name="syntax"></a>Składnia  
  
```  
template <class T, class PropClass = T>  
class ATL_NO_VTABLE IRowsetInfoImpl :   
   public IRowsetInfo,    
   public CUtlProps<PropClass>  
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Z klasą pochodną `IRowsetInfoImpl`.  
  
 `PropClass`  
 Klasa właściwości definiowane przez użytkownika, która domyślnie `T`.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="interface-methods"></a>Metody interfejsu  
  
|||  
|-|-|  
|[GetProperties](../../data/oledb/irowsetinfoimpl-getproperties.md)|Zwraca bieżące ustawienia właściwości wszystkich obsługiwanych przez zestaw wierszy.|  
|[GetReferencedRowset](../../data/oledb/irowsetinfoimpl-getreferencedrowset.md)|Zwraca wskaźnik interfejsu zestawu wierszy, do którego jest stosowana zakładki.|  
|[GetSpecification](../../data/oledb/irowsetinfoimpl-getspecification.md)|Zwraca wskaźnik interfejsu na obiekcie (polecenie lub sesji), który utworzył ten zestaw wierszy.|  
  
## <a name="remarks"></a>Uwagi  
 Interfejs obowiązkowy zestawów wierszy. Ta klasa implementuje właściwości zestawu wierszy za pomocą [mapę zestaw właściwości](../../data/oledb/begin-propset-map.md) zdefiniowany w klasie polecenia. Mimo że klasy zestawu wierszy jest dostępna, można za pomocą właściwości klasy poleceń zestawy, po utworzeniu obiektu polecenia lub sesji zestawu wierszy jest dostarczany z własną kopię właściwości czasu wykonywania.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** altdb.h  
  
## <a name="see-also"></a>Zobacz też  
 [Szablony dostawców OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Architektura szablonu dostawcy OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)