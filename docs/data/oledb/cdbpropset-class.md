---
title: "Cdbpropset — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CDBPropSet
- ATL.CDBPropSet
- ATL::CDBPropSet
dev_langs: C++
helpviewer_keywords: CDBPropSet class
ms.assetid: 54190149-c277-4679-b81a-ef484d4d1c00
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 2b2523e37c3015bb49d123e99f39c1ea4bdb9045
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="cdbpropset-class"></a>CDBPropSet — Klasa
Dziedziczy **DBPROPSET** struktury i dodaje konstruktora, który inicjuje pola klucza, jak również `AddProperty` metody dostępu.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CDBPropSet : public tagDBPROPSET  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="methods"></a>Metody  
  
|||  
|-|-|  
|[AddProperty](../../data/oledb/cdbpropset-addproperty.md)|Dodaje właściwość do zestawu właściwości.|  
|[Cdbpropset —](../../data/oledb/cdbpropset-cdbpropset.md)|Konstruktor.|  
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