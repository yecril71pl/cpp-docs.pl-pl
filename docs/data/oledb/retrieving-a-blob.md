---
title: Pobieranie obiektu BLOB | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- retrieving BLOBs
- BLOB (binary large object), retrieving
- OLE DB, BLOBs (binary large objects)
ms.assetid: 2893eb0a-5c05-4016-8914-1e40ccbaf0b3
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 9a0519631d843f875788b394b72d56795c562ae0
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2018
---
# <a name="retrieving-a-blob"></a>Pobieranie obiektu BLOB
Można pobrać dużego obiektu binarnego (BLOB) na różne sposoby. Można użyć **DBTYPE_BYTES** można pobrać obiektu BLOB jako sekwencję bajtów lub korzystają z interfejsu, takich jak `ISequentialStream`. Aby uzyskać więcej informacji, zobacz [obiekty BLOB i obiektów OLE](https://msdn.microsoft.com/en-us/library/ms711511.aspx) w *OLE DB Podręcznik programisty*.  
  
 Poniższy kod przedstawia sposób pobrać za pomocą obiektu BLOB `ISequentialStream`. Makro [BLOB_ENTRY](../../data/oledb/blob-entry.md) umożliwia określenie interfejsu oraz flagi używane dla interfejsu. Po otwarciu tabeli, kod wywołuje **odczytu** wielokrotnie na `ISequentialStream` do odczytywania bajtów z obiektu BLOB. Kod wywołuje **wersji** zlikwidować wskaźnika interfejsu przed wywołaniem `MoveNext` uzyskać następnego rekordu.  
  
```  
class CCategories  
{  
public:  
   ISequentialStream*   pPicture;  
  
BEGIN_COLUMN_MAP(CCategories)  
   BLOB_ENTRY(4, IID_ISequentialStream, STGM_READ, pPicture)  
END_COLUMN_MAP()  
};  
  
CTable<CAccessor<CCategories>> categories;  
ULONG          cb;  
BYTE            myBuffer[65536];  
  
categories.Open(session, "Categories");  

while (categories.MoveNext() == S_OK)  
{  
   do  
   {  
      categories.pPicture->Read(myBuffer, 65536, &cb);  
      // Do something with the buffer  
   } while (cb > 0);  
   categories.pPicture->Release();  
}  
```  
  
 Aby uzyskać więcej informacji na temat makr, które obsługują dane obiektów BLOB, zobacz "Makra mapy kolumny" w [makra i funkcje globalne dla OLE DB szablonów konsumentów](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z metod dostępu](../../data/oledb/using-accessors.md)   
 [Makra i funkcje globalne dla szablonów konsumentów OLE DB](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)