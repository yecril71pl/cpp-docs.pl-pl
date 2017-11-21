---
title: BLOB_NAME | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: BLOB_NAME
dev_langs: C++
helpviewer_keywords: BLOB_NAME macro
ms.assetid: 757acd0d-946d-447d-937e-94ecd700ba38
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 25198fb70b454b849364a9ff3e61de03a802e9a9
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="blobname"></a>BLOB_NAME
Używane z `BEGIN_COLUMN_MAP` i `END_COLUMN_MAP` powiązać dużego obiektu binarnego ([obiektu BLOB](https://msdn.microsoft.com/en-us/library/ms711511.aspx)). Podobnie jak [BLOB_ENTRY](../../data/oledb/blob-entry.md), ale to makro przyjmuje nazwę kolumny, a liczba kolumn.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
BLOB_NAME(  
pszName  
,   
IID  
,   
flags  
,   
data )  
```  
  
#### <a name="parameters"></a>Parametry  
 `pszName`  
 [in] Wskaźnik do nazwy kolumny. Nazwa musi być ciągiem Unicode. Można to zrobić przez umieszczenie "L" przed nazwą, na przykład: `L"MyColumn"`.  
  
 *IDENTYFIKATOR IID*  
 [in] Interfejs identyfikatora GUID, takich jak **IDD_ISequentialStream**, używana do pobrania obiektu BLOB.  
  
 `flags`  
 [in] Tryb przechowywania flagi zgodnie z definicją w modelu OLE strukturalnego magazynu (na przykład **STGM_READ**).  
  
 `data`  
 [in] Odpowiedni element członkowski danych w rekordzie użytkownika.  
  
## <a name="example"></a>Przykład  
 Zobacz [sposób pobierania obiektu BLOB?](../../data/oledb/retrieving-a-blob.md).  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldbcli.h  
  
## <a name="see-also"></a>Zobacz też  
 [Makra i funkcje globalne dla szablonów konsumentów OLE DB](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)   
 [BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md)   
 [END_COLUMN_MAP](../../data/oledb/end-column-map.md)   
 [COLUMN_ENTRY —](../../data/oledb/column-entry.md)   
 [BLOB_NAME_LENGTH](../../data/oledb/blob-name-length.md)   
 [BLOB_NAME_LENGTH_STATUS](../../data/oledb/blob-name-length-status.md)   
 [BLOB_NAME_STATUS](../../data/oledb/blob-name-status.md)