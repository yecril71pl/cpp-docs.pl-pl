---
title: Cdbpropset — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CDBPropSet
- ATL.CDBPropSet
- ATL::CDBPropSet
dev_langs:
- C++
helpviewer_keywords:
- CDBPropSet class
ms.assetid: 54190149-c277-4679-b81a-ef484d4d1c00
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 8d75715ed0dc65fbbf5b581bfea48816e5bd00ce
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="cdbpropset-class"></a>CDBPropSet — Klasa
Dziedziczy **DBPROPSET** struktury i dodaje konstruktora, który inicjuje pola klucza, jak również `AddProperty` metody dostępu.  
  
## <a name="syntax"></a>Składnia

```cpp
class CDBPropSet : public tagDBPROPSET  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="methods"></a>Metody  
  
|||  
|-|-|  
|[addProperty](../../data/oledb/cdbpropset-addproperty.md)|Dodaje właściwość do zestawu właściwości.|  
|[CDBPropSet](../../data/oledb/cdbpropset-cdbpropset.md)|Konstruktor.|  
|[SetGUID](../../data/oledb/cdbpropset-setguid.md)|Ustawia **guidPropertySet** pole **DBPROPSET** struktury.|  
  
### <a name="operators"></a>Operatory  
  
|||  
|-|-|  
|[operator =](../../data/oledb/cdbpropset-operator-equal.md)|Przypisuje zawartość jedną właściwość do innego zestawu.|  
  
## <a name="remarks"></a>Uwagi  
 Użyj dostawcy i konsumentów OLE DB **DBPROPSET** struktury tak, aby przekazać tablice `DBPROP` struktury. Każdy `DBPROP` struktury reprezentuje jedną właściwość, która może być ustawiona.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldbcli.h  
  
## <a name="see-also"></a>Zobacz też  
 [Szablony konsumentów OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [Dokumentacja szablonów konsumentów OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)   
 [Cdbpropidset — klasa](../../data/oledb/cdbpropidset-class.md)   
 [Struktura DBPROPSET](https://msdn.microsoft.com/en-us/library/ms714367.aspx)   
 [Struktura DBPROP](https://msdn.microsoft.com/en-us/library/ms717970.aspx)