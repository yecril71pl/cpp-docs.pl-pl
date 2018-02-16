---
title: SCHEMA_ENTRY | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- SCHEMA_ENTRY
dev_langs:
- C++
helpviewer_keywords:
- SCHEMA_ENTRY macro
ms.assetid: e8bee479-80f3-417e-8f41-cdaddd49690c
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 4b1ddabb976cdf4897dbd414433f013a84825d01
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2018
---
# <a name="schemaentry"></a>SCHEMA_ENTRY
Kojarzy identyfikator GUID z klasy.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
      SCHEMA_ENTRY(guid,  
   rowsetClass);   
```  
  
#### <a name="parameters"></a>Parametry  
 `guid`  
 Zestaw wierszy schematu identyfikatora GUID. Zobacz [IDBSchemaRowset](https://msdn.microsoft.com/en-us/library/ms713686.aspx) w *OLE DB Podręcznik programisty* listę zestawów wierszy schematu i ich identyfikatorów GUID.  
  
 *rowsetClass*  
 Klasa, która zostanie utworzone w celu reprezentowania zestawu wierszy schematu.  
  
## <a name="remarks"></a>Uwagi  
 [Idbschemarowsetimpl —](../../data/oledb/idbschemarowsetimpl-class.md) można następnie zapytania mapy listę identyfikatorów GUID lub można utworzyć zestawu wierszy, jeśli zostanie podany, identyfikator GUID. Zestaw wierszy schematu `IDBSchemaRowsetImpl` tworzy przypomina standardowego `CRowsetImpl`-pochodnej klasy, z wyjątkiem przekazuje **Execute** metodę, która ma następującą sygnaturą:  
  
```  
HRESULT Execute (LONG* pcRowsAffected,  
    ULONG cRestrictions,  
    const VARIANT* rgRestrictions);  
```  
  
 To **Execute** funkcja wypełnia zestawu wierszy danych. Kreator projektu ATL tworzy, zgodnie z opisem w [IDBSchemaRowset](https://msdn.microsoft.com/en-us/library/ms713686.aspx) w *OLE DB Podręcznik programisty*, zestawy wierszy schematu w projekcie trzy początkowej dla każdego z trzech wymagane schematy OLE DB:  
  
-   `DBSCHEMA_TABLES`  
  
-   **DBSCHEMA_COLUMNS**  
  
-   **DBSCHEMA_PROVIDER_TYPES**  
  
 Kreator dodaje również trzy odpowiednie pozycje w mapie schematu. Zobacz [Tworzenie dostawcy OLE DB szablonu](../../data/oledb/creating-an-ole-db-provider.md) uzyskać więcej informacji o za pomocą kreatora, aby utworzyć dostawcę.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldb.h  
  
## <a name="see-also"></a>Zobacz też  
 [Makra dla szablonów dostawców OLE DB](../../data/oledb/macros-for-ole-db-provider-templates.md)   
 [BEGIN_SCHEMA_MAP](../../data/oledb/begin-schema-map.md)   
 [END_SCHEMA_MAP](../../data/oledb/end-schema-map.md)