---
title: Makra dla szablonów dostawców OLE DB | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- vc.templates.ole
dev_langs:
- C++
helpviewer_keywords:
- OLE DB provider templates, macros
- macros, OLE DB Provider Templates
- Provider Template macros (OLE DB)
- OLE DB Provider Template macros
ms.assetid: 909482c5-64ab-4e52-84a9-1c07091db183
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: ab7611c49f625a36023b4e31bf6aff47ab16f156
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33111746"
---
# <a name="macros-for-ole-db-provider-templates"></a>Makra dla szablonów dostawców OLE DB
Dostawca OLE DB szablony makra oferują funkcje w ramach następujących kategorii:  
  
### <a name="property-set-map-macros"></a>Makra mapy zestaw właściwości  
  
|||  
|-|-|  
|[BEGIN_PROPERTY_SET](../../data/oledb/begin-property-set.md)|Oznacza początek zestawu właściwości.|  
|[BEGIN_PROPERTY_SET_EX](../../data/oledb/begin-property-set-ex.md)|Oznacza początek zestawu właściwości.|  
|[BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md)|Znaczniki ustawione na początku właściwości, które można ukryte lub zdefiniowany poza zakresem dostawcy.|  
|[CHAIN_PROPERTY_SET](../../data/oledb/chain-property-set.md)|Łańcuchy grupy właściwości jednocześnie.|  
|[END_PROPERTY_SET](../../data/oledb/end-property-set.md)|Oznacza koniec zestaw właściwości.|  
|[END_PROPSET_MAP](../../data/oledb/end-propset-map.md)|Oznacza koniec mapę zestawu właściwości.|  
|[PROPERTY_INFO_ENTRY](../../data/oledb/property-info-entry.md)|Ustawia określoną właściwość we właściwości ustawiono wartość domyślną.|  
|[PROPERTY_INFO_ENTRY_EX](../../data/oledb/property-info-entry-ex.md)|Ustawia określoną właściwość we właściwości ustawić wartość dostarczone przez użytkownika. Umożliwia także ustawić opcje i flagi.|  
|[PROPERTY_INFO_ENTRY_VALUE](../../data/oledb/property-info-entry-value.md)|Ustawia określoną właściwość we właściwości ustawić wartość dostarczone przez użytkownika.|  
  
### <a name="column-map-macros"></a>Makra mapy kolumny  
  
|||  
|-|-|  
|[BEGIN_PROVIDER_COLUMN_MAP](../../data/oledb/begin-provider-column-map.md)|Oznacza początek wpisów map kolumny dostawcy.|  
|[END_PROVIDER_COLUMN_MAP](../../data/oledb/end-provider-column-map.md)|Oznacza koniec wpisów map kolumny dostawcy.|  
|[PROVIDER_COLUMN_ENTRY](../../data/oledb/provider-column-entry.md)|Przedstawia kolumnę określonych obsługiwane przez dostawcę.|  
|[PROVIDER_COLUMN_ENTRY_GN](../../data/oledb/provider-column-entry-gn.md)|Przedstawia kolumnę określonych obsługiwane przez dostawcę. Można określić kolumny rozmiar, typ danych precyzja, skala i identyfikatorem GUID zestawu wierszy schematu.|  
|[PROVIDER_COLUMN_ENTRY_FIXED](../../data/oledb/provider-column-entry-fixed.md)|Przedstawia kolumnę określonych obsługiwane przez dostawcę. Można określić typu danych kolumny.|  
|[PROVIDER_COLUMN_ENTRY_LENGTH](../../data/oledb/provider-column-entry-length.md)|Przedstawia kolumnę określonych obsługiwane przez dostawcę. Można określić rozmiar kolumny.|  
|[PROVIDER_COLUMN_ENTRY_STR](../../data/oledb/provider-column-entry-str.md)|Przedstawia kolumnę określonych obsługiwane przez dostawcę. Zakłada się, że typem kolumny jest ciąg.|  
|[PROVIDER_COLUMN_ENTRY_TYPE_LENGTH](../../data/oledb/provider-column-entry-type-length.md)|Przedstawia kolumnę określonych obsługiwane przez dostawcę. PROVIDER_COLUMN_ENTRY_LENGTH, takich jak, ale można też określić typ danych kolumny, a także rozmiar.|  
|[PROVIDER_COLUMN_ENTRY_WSTR](../../data/oledb/provider-column-entry-wstr.md)|Przedstawia kolumnę określonych obsługiwane przez dostawcę. Zakłada się, że typem kolumny jest ciąg znaków Unicode.|  
  
### <a name="schema-rowset-macros"></a>Makra zestawu wierszy schematu  
  
|||  
|-|-|  
|[BEGIN_SCHEMA_MAP](../../data/oledb/begin-schema-map.md)|Oznacza początek mapy schematu.|  
|[SCHEMA_ENTRY](../../data/oledb/schema-entry.md)|Kojarzy identyfikator GUID z klasy.|  
|[END_SCHEMA_MAP](../../data/oledb/end-schema-map.md)|Oznacza koniec mapy schematu.|  
  
## <a name="see-also"></a>Zobacz też  
 [Szablony dostawców OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Architektura szablonu dostawcy OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)   
 [Tworzenie dostawcy OLE DB](../../data/oledb/creating-an-ole-db-provider.md)   
 [Szablony dostawców OLE DB — dokumentacja](../../data/oledb/ole-db-provider-templates-reference.md)