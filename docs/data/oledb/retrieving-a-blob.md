---
title: Pobieranie obiektu BLOB | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- retrieving BLOBs
- BLOB (binary large object), retrieving
- OLE DB, BLOBs (binary large objects)
ms.assetid: 2893eb0a-5c05-4016-8914-1e40ccbaf0b3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 17e2f5ce1ec78b150e6569fb571f9c08e39efe0e
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/14/2018
ms.locfileid: "42465431"
---
# <a name="retrieving-a-blob"></a>Pobieranie obiektu BLOB
Możesz pobrać dużego obiektu binarnego (BLOB) na różne sposoby. Możesz użyć `DBTYPE_BYTES` można pobrać obiektu BLOB jako sekwencja bajtów lub korzystają z interfejsu, takich jak `ISequentialStream`. Aby uzyskać więcej informacji, zobacz [obiektów blob oraz obiekty OLE](/previous-versions/windows/desktop/ms711511\(v=vs.85\)) w *OLE DB Podręcznik programisty*.  
  
 Poniższy kod przedstawia sposób pobierania obiektu BLOB przy użyciu `ISequentialStream`. Makro [BLOB_ENTRY](../../data/oledb/blob-entry.md) pozwala określić interfejs i flagi używane do interfejsu. Po otwarciu w tabeli, kod wywołuje `Read` wielokrotnie w `ISequentialStream` do odczytywania bajtów z obiektu BLOB. Kod wywołuje `Release` do rozporządzania wskaźnika interfejsu przed wywołaniem `MoveNext` uzyskać następnego rekordu.  
  
```cpp  
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
  
 Aby uzyskać więcej informacji na temat makra, które obsługują danych obiektów BLOB, zobacz "Makra mapy kolumny" w [makra i funkcje globalne dla OLE DB szablonów konsumentów](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z metod dostępu](../../data/oledb/using-accessors.md)   
 [Makra i funkcje globalne dla szablonów konsumentów OLE DB](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)