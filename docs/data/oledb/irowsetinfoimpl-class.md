---
title: Irowsetinfoimpl — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL.IRowsetInfoImpl
- IRowsetInfoImpl
- ATL::IRowsetInfoImpl
dev_langs:
- C++
helpviewer_keywords:
- IRowsetInfoImpl class
ms.assetid: 9c654155-7727-464e-bd31-143e68391a47
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: f9b784dbb13ff39be21ccd353d514dd244d5ae41
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="irowsetinfoimpl-class"></a>IRowsetInfoImpl — Klasa
Udostępnia implementację dla [IRowsetInfo](https://msdn.microsoft.com/en-us/library/ms724541.aspx) interfejsu.  
  
## <a name="syntax"></a>Składnia

```cpp
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