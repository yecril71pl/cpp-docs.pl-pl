---
title: "Cutlprops — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: CUtlProps
dev_langs: C++
helpviewer_keywords: CUtlProps class
ms.assetid: bb525178-765c-4e23-a110-c0fd70c05437
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 0f57894bc22cc469e000663d871be7c4739db22e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="cutlprops-class"></a>CUtlProps — Klasa
Implementuje właściwości dla różnych interfejsy właściwości OLE DB (na przykład `IDBProperties`, `IDBProperties`, i `IRowsetInfo`).  
  
## <a name="syntax"></a>Składnia  
  
```  
template < class T >  
class ATL_NO_VTABLE CUtlProps : public CUtlPropsBase  
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Klasa, która zawiera `BEGIN_PROPSET_MAP`.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="methods"></a>Metody  
  
|||  
|-|-|  
|[GetPropValue](../../data/oledb/cutlprops-getpropvalue.md)|Pobiera właściwości z zestawu właściwości.|  
|[IsValidValue](../../data/oledb/cutlprops-isvalidvalue.md)|Używany do sprawdzania poprawności wartości przed ustawieniem właściwości.|  
|[OnInterfaceRequested](../../data/oledb/cutlprops-oninterfacerequested.md)|Obsługuje żądania dla interfejsu opcjonalny, gdy klient wywołuje metodę dla interfejsu tworzenia obiektu.|  
|[OnPropertyChanged](../../data/oledb/cutlprops-onpropertychanged.md)|Wywołuje się po ustawieniu właściwości w celu obsługi łańcuchowa właściwości.|  
|[SetPropValue](../../data/oledb/cutlprops-setpropvalue.md)|Ustawia właściwość w zestawie właściwości.|  
  
## <a name="remarks"></a>Uwagi  
 W większości tej klasy jest szczegóły implementacji.  
  
 `CUtlProps`zawiera dwa elementy członkowskie do ustawiania właściwości wewnętrznie: [GetPropValue](../../data/oledb/cutlprops-getpropvalue.md) i [SetPropValue](../../data/oledb/cutlprops-setpropvalue.md).  
  
 Aby uzyskać więcej informacji na makra używane w mapowaniu zestawu właściwości, zobacz [BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md) i [END_PROPSET_MAP](../../data/oledb/end-propset-map.md).  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldb.h  
  
## <a name="see-also"></a>Zobacz też  
 [Szablony dostawców OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Architektura szablonu dostawcy OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)