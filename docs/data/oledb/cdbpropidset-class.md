---
title: "Cdbpropidset — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: ee03feb715ebf96bd4de1af5374a2029f52bbf86
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
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