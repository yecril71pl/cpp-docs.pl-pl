---
title: BEGIN_COLUMN_MAP | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: BEGIN_COLUMN_MAP
dev_langs: C++
helpviewer_keywords: BEGIN_COLUMN_MAP macro
ms.assetid: d6ffe633-e0da-4e33-8faa-f7f259d05420
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 29e62e08ef03d863b17ea0d269cf049b23602774
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="begincolumnmap"></a>BEGIN_COLUMN_MAP
Oznacza początek wpisu mapowania kolumn.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
BEGIN_COLUMN_MAP(  
x  
 )  
  
```  
  
#### <a name="parameters"></a>Parametry  
 *x*  
 [in] Nazwa klasy rekordów użytkowników pochodną `CAccessor`.  
  
## <a name="remarks"></a>Uwagi  
 To makro jest używane w przypadku jedną metodę dostępu w zestawie wierszy. Jeśli masz wiele metod dostępu w zestawie wierszy, użyj [begin_accessor_map —](../../data/oledb/begin-accessor-map.md).  
  
 `BEGIN_COLUMN_MAP` Makro zostało zakończone z `END_COLUMN_MAP` makra. To makro jest używane, gdy istnieje tylko jedną metodę dostępu, wymagane w rekordzie użytkownika.  
  
 Kolumny odpowiadają polom w zestawie wierszy, które chcesz powiązać.  
  
## <a name="example"></a>Przykład  
 Oto przykładowe mapy kolumny i parametr:  
  
 <!--[!CODE [NVC_OLEDB_Consumer#16](../codesnippet/vs_snippets_cpp/nvc_oledb_consumer#16)]  -->
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldbcli.h  
  
## <a name="see-also"></a>Zobacz też  
 [Makra i funkcje globalne dla szablonów konsumentów OLE DB](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)   
 [END_COLUMN_MAP](../../data/oledb/end-column-map.md)   
 [COLUMN_ENTRY —](../../data/oledb/column-entry.md)   
 [COLUMN_ENTRY_EX](../../data/oledb/column-entry-ex.md)