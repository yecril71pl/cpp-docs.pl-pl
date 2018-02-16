---
title: BLOB_ENTRY_STATUS | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- BLOB_ENTRY_STATUS
dev_langs:
- C++
helpviewer_keywords:
- BLOB_ENTRY_STATUS macro
ms.assetid: 191007f4-dfcc-4ae2-a7fc-6f7899accc9f
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 465d8ab8ddfce53131307ca4910a89882142c687
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2018
---
# <a name="blobentrystatus"></a>BLOB_ENTRY_STATUS
Używane z `BEGIN_COLUMN_MAP` lub `BEGIN_ACCESSOR_MAP` powiązać dużego obiektu binarnego ([obiektu BLOB](https://msdn.microsoft.com/en-us/library/ms711511.aspx)). Podobnie jak [BLOB_ENTRY](../../data/oledb/blob-entry.md), ale to makro również pobiera stan dla kolumny obiektu BLOB.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
BLOB_ENTRY_STATUS(nOrdinal, IID, flags, data, status)  
  
```  
  
#### <a name="parameters"></a>Parametry  
 `nOrdinal`  
 [in] Numer kolumny.  
  
 *IID*  
 [in] Interfejs identyfikatora GUID, takich jak **IDD_ISequentialStream**, używana do pobrania obiektu BLOB.  
  
 `flags`  
 [in] Tryb przechowywania flagi zgodnie z definicją w modelu OLE strukturalnego magazynu (na przykład **STGM_READ**).  
  
 `data`  
 [in] Odpowiedni element członkowski danych w rekordzie użytkownika.  
  
 *status*  
 [out] Stan pola obiektu BLOB.  
  
## <a name="example"></a>Przykład  
 Zobacz [sposób pobierania obiektu BLOB?](../../data/oledb/retrieving-a-blob.md).  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldbcli.h  
  
## <a name="see-also"></a>Zobacz też  
 [Makra i funkcje globalne dla szablonów konsumentów OLE DB](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)   
 [BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md)   
 [END_COLUMN_MAP](../../data/oledb/end-column-map.md)   
 [COLUMN_ENTRY —](../../data/oledb/column-entry.md)   
 [BLOB_ENTRY](../../data/oledb/blob-entry.md)   
 [BLOB_ENTRY_LENGTH](../../data/oledb/blob-entry-length.md)   
 [BLOB_ENTRY_LENGTH_STATUS](../../data/oledb/blob-entry-length-status.md)