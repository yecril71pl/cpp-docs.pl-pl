---
title: Cdbpropidset — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CDBPropIDSet
- ATL.CDBPropIDSet
- ATL::CDBPropIDSet
dev_langs:
- C++
helpviewer_keywords:
- CDBPropIDSet class
ms.assetid: 52bb806c-9581-494d-9af7-50d8a4834805
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 67bfd11a46d8e0c852c1881ff8874b7fbd817164
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="cdbpropidset-class"></a>CDBPropIDSet — Klasa
Dziedziczy **DBPROPIDSET** struktury i dodaje konstruktora, który inicjuje pola klucza, jak również [AddPropertyID](../../data/oledb/cdbpropidset-addpropertyid.md) metody dostępu.  
  
## <a name="syntax"></a>Składnia

```cpp
class CDBPropIDSet : public tagDBPROPIDSET  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="methods"></a>Metody  
  
|||  
|-|-|  
|[AddPropertyID](../../data/oledb/cdbpropidset-addpropertyid.md)|Dodaje właściwość do zestawu identyfikator właściwości.|  
|[CDBPropIDSet](../../data/oledb/cdbpropidset-cdbpropidset.md)|Konstruktor.|  
|[SetGUID](../../data/oledb/cdbpropidset-setguid.md)|Ustawia ustawiony identyfikator GUID identyfikator właściwości.|  
  
### <a name="operators"></a>Operatory  
  
|||  
|-|-|  
|[operator =](../../data/oledb/cdbpropidset-operator-equal.md)|Przypisuje do innego zestawu zawartości jedną właściwość Identyfikatora.|  
  
## <a name="remarks"></a>Uwagi  
 Użyj konsumentów OLE DB **DBPROPIDSET** struktury tak, aby przekazać tablicę identyfikatorów właściwości, dla których użytkownik chce uzyskać informacje dotyczące właściwości. Właściwości określone w jednej [DBPROPIDSET](https://msdn.microsoft.com/en-us/library/ms717981.aspx) struktury należą do zestawu jedną właściwość.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldbcli.h  
  
## <a name="see-also"></a>Zobacz też  
 [Szablony konsumentów OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [Szablony konsumentów OLE DB — dokumentacja](../../data/oledb/ole-db-consumer-templates-reference.md)