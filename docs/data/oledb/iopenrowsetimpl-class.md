---
title: "Iopenrowsetimpl — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- IOpenRowsetImpl
dev_langs:
- C++
helpviewer_keywords:
- IOpenRowsetImpl class
ms.assetid: d259cedc-1db4-41cf-bc9f-5030907ab486
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 67f457b4a56d57f33a18473e987fa00b6c10b0df
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="iopenrowsetimpl-class"></a>IOpenRowsetImpl — Klasa
Udostępnia implementację dla `IOpenRowset` interfejsu.  
  
## <a name="syntax"></a>Składnia

```cpp
template <class SessionClass>  
class IOpenRowsetImpl : public IOpenRowset  
```  
  
#### <a name="parameters"></a>Parametry  
 `SessionClass`  
 Z klasą pochodną `IOpenRowsetImpl`.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="methods"></a>Metody  
  
|||  
|-|-|  
|[CreateRowset](../../data/oledb/iopenrowsetimpl-createrowset.md)|Tworzy obiekt zestawu wierszy. Nie należy wywoływać bezpośrednio przez użytkownika.|  
|[OpenRowset](../../data/oledb/iopenrowsetimpl-openrowset.md)|Otwiera i zwraca zestaw wierszy, która obejmuje wszystkie wiersze z jednej tabeli podstawowej lub indeks. (Nie w ATLDB. H)|  
  
## <a name="remarks"></a>Uwagi  
 [IOpenRowset](https://msdn.microsoft.com/en-us/library/ms716946.aspx) interfejsu jest wymagane dla obiekt sesji. Otwiera i zwraca zestaw wierszy, która obejmuje wszystkie wiersze z jednej tabeli podstawowej lub indeks.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldb.h  
  
## <a name="see-also"></a>Zobacz też  
 [Szablony dostawców OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Architektura szablonu dostawcy OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)