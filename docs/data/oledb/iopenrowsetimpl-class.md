---
title: Iopenrowsetimpl — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- IOpenRowsetImpl
dev_langs:
- C++
helpviewer_keywords:
- IOpenRowsetImpl class
ms.assetid: d259cedc-1db4-41cf-bc9f-5030907ab486
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: dd34987fcff3bee663a06276e3ded3c44d7ae77c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
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