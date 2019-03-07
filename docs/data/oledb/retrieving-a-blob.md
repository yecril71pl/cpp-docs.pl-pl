---
title: Pobieranie obiektu BLOB
ms.date: 10/24/2018
helpviewer_keywords:
- retrieving BLOBs
- BLOB (binary large object), retrieving
- OLE DB, BLOBs (binary large objects)
ms.assetid: 2893eb0a-5c05-4016-8914-1e40ccbaf0b3
ms.openlocfilehash: 42b7b95f2da4313bdfcb1d9d8a064ca5be563e40
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57423251"
---
# <a name="retrieving-a-blob"></a>Pobieranie obiektu BLOB

Możesz pobrać dużego obiektu binarnego (BLOB) na różne sposoby. Możesz użyć `DBTYPE_BYTES` można pobrać obiektu BLOB jako sekwencja bajtów lub korzystają z interfejsu, takich jak `ISequentialStream`. Aby uzyskać więcej informacji, zobacz [obiektów blob oraz obiekty OLE](/previous-versions/windows/desktop/ms711511(v=vs.85)) w **OLE DB Podręcznik programisty**.

Poniższy kod przedstawia sposób pobierania obiektu BLOB przy użyciu `ISequentialStream`. Makro [BLOB_ENTRY](../../data/oledb/blob-entry.md) pozwala określić interfejs i flagi używane do interfejsu. Po otwarciu w tabeli, kod wywołuje `Read` wielokrotnie w `ISequentialStream` do odczytywania bajtów z obiektu BLOB. Kod wywołuje `Release` do rozporządzania wskaźnika interfejsu przed wywołaniem `MoveNext` można pobrać następny rekord.

```cpp
class CCategories
{
public:
   ISequentialStream* pPicture;

BEGIN_COLUMN_MAP(CCategories)
   BLOB_ENTRY(4, IID_ISequentialStream, STGM_READ, pPicture)
END_COLUMN_MAP()
};
```

Następnie używany przez następujący kod:

```cpp
CTable<CAccessor<CCategories>> categories;
ULONG cb;
BYTE myBuffer[65536];

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

Aby uzyskać więcej informacji na temat makra, które obsługują danych obiektów BLOB, zobacz **makra mapy kolumny** w [makra i funkcje globalne dla OLE DB szablonów konsumentów](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md).

## <a name="see-also"></a>Zobacz też

[Korzystanie z metod dostępu](../../data/oledb/using-accessors.md)<br/>
[Makra i funkcje globalne dla szablonów konsumentów OLE DB](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)<br/>
