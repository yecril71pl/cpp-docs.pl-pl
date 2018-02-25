---
title: BLOB_NAME_STATUS | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- BLOB_NAME_STATUS
dev_langs:
- C++
helpviewer_keywords:
- BLOB_NAME_STATUS macro
ms.assetid: 4564e4a0-8e5e-436a-bd1e-012d2a1b8642
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 4d55e65872a2939a8aa252f0a839ed41570bbcd4
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="blobnamestatus"></a>BLOB_NAME_STATUS
Używane z `BEGIN_COLUMN_MAP` i `END_COLUMN_MAP` powiązać dużego obiektu binarnego ([obiektu BLOB](https://msdn.microsoft.com/en-us/library/ms711511.aspx)). Podobnie jak [BLOB_NAME](../../data/oledb/blob-name.md), ale to makro również pobiera stan kolumny danych obiektów BLOB.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
BLOB_NAME_STATUS(pszName, IID, flags, data  
, status )  
```  
  
#### <a name="parameters"></a>Parametry  
 `pszName`  
 [in] Wskaźnik do nazwy kolumny. Nazwa musi być ciągiem Unicode. Można to zrobić przez umieszczenie "L" przed nazwą, na przykład: `L"MyColumn"`.  
  
 *IID*  
 [in] Interfejs identyfikatora GUID, takich jak **IDD_ISequentialStream**, używana do pobrania obiektu BLOB.  
  
 `flags`  
 [in] Tryb przechowywania flagi zgodnie z definicją w modelu OLE strukturalnego magazynu (na przykład **STGM_READ**).  
  
 `data`  
 [in] Odpowiedni element członkowski danych w rekordzie użytkownika.  
  
 *status*  
 [out] Stan pola obiektu BLOB.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldbcli.h  
  
## <a name="see-also"></a>Zobacz też  
 [Makra i funkcje globalne dla szablonów konsumentów OLE DB](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)   
 [BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md)   
 [END_COLUMN_MAP](../../data/oledb/end-column-map.md)   
 [COLUMN_ENTRY —](../../data/oledb/column-entry.md)   
 [BLOB_NAME](../../data/oledb/blob-name.md)   
 [BLOB_NAME_LENGTH](../../data/oledb/blob-name-length.md)   
 [BLOB_NAME_LENGTH_STATUS](../../data/oledb/blob-name-length-status.md)