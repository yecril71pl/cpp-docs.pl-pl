---
title: "Cdbpropidset — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CDBPropIDSet
- ATL.CDBPropIDSet
- ATL::CDBPropIDSet
dev_langs: C++
helpviewer_keywords: CDBPropIDSet class
ms.assetid: 52bb806c-9581-494d-9af7-50d8a4834805
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 996e1a04e9870a9cd3cf02ca6a8c7c05a1dc3e56
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="cdbpropidset-class"></a>CDBPropIDSet — Klasa
Dziedziczy **DBPROPIDSET** struktury i dodaje konstruktora, który inicjuje pola klucza, jak również [AddPropertyID](../../data/oledb/cdbpropidset-addpropertyid.md) metody dostępu.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CDBPropIDSet : public tagDBPROPIDSET  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="methods"></a>Metody  
  
|||  
|-|-|  
|[AddPropertyID](../../data/oledb/cdbpropidset-addpropertyid.md)|Dodaje właściwość do zestawu identyfikator właściwości.|  
|[Cdbpropidset —](../../data/oledb/cdbpropidset-cdbpropidset.md)|Konstruktor.|  
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
 [Dokumentacja szablonów konsumentów OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)