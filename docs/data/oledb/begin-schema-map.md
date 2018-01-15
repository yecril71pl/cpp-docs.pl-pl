---
title: BEGIN_SCHEMA_MAP | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: BEGIN_SCHEMA_MAP
dev_langs: C++
helpviewer_keywords: BEGIN_SCHEMA_MAP macro
ms.assetid: 4e751023-35bc-4efd-9018-5448dd1ad751
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 9682ac8a31ec7c585b1da7b9bc14388413ba56fa
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="beginschemamap"></a>BEGIN_SCHEMA_MAP
Oznacza początek mapy schematu.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
      BEGIN_SCHEMA_MAP(  
   SchemaClass   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 *SchemaClass*  
 Klasa, która zawiera mapy. Zazwyczaj jest to klasa sesji.  
  
## <a name="remarks"></a>Uwagi  
 Zobacz [IDBSchemaRowset](https://msdn.microsoft.com/en-us/library/ms713686.aspx) w zestawie SDK systemu Windows, aby uzyskać więcej informacji na temat zestawów wierszy schematu.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldb.h  
  
## <a name="see-also"></a>Zobacz też  
 [Makra dla szablonów dostawców OLE DB](../../data/oledb/macros-for-ole-db-provider-templates.md)   
 [SCHEMA_ENTRY](../../data/oledb/schema-entry.md)   
 [END_SCHEMA_MAP](../../data/oledb/end-schema-map.md)   
 [IDBSchemaRowsetImpl, klasa](../../data/oledb/idbschemarowsetimpl-class.md)