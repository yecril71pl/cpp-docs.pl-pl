---
title: Przechowywanie ciągów w dostawcy OLE DB
ms.date: 05/09/2019
helpviewer_keywords:
- user records, editing
ms.assetid: 36cb9635-067c-4cad-8f85-962f28026f6a
ms.openlocfilehash: f0ae4a3718858c4de5417aaf5a4f9bc0c0ba9984
ms.sourcegitcommit: 00e26915924869cd7eb3c971a7d0604388abd316
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/10/2019
ms.locfileid: "65525354"
---
# <a name="storing-strings-in-the-ole-db-provider"></a>Przechowywanie ciągów w dostawcy OLE DB

> [!NOTE] 
> Kreator ATL OLE DB Provider nie jest dostępne w programie Visual Studio 2019 r i nowszych wersjach.


W *niestandardowe*RS.h, **Kreator biblioteki ATL OLE DB Provider** tworzy rekord użytkownika domyślnego o nazwie `CWindowsFile`. Aby obsługiwać dwa ciągi, zmodyfikuj `CWindowsFile` jak pokazano w poniższym kodzie:

```cpp
////////////////////////////////////////////////////////////////////////
class CCustomWindowsFile:
   public WIN32_FIND_DATA
{
public:
DWORD dwBookmark;
static const int iSize = 256;    // Add this
TCHAR szCommand[iSize];          // Add this
TCHAR szText[iSize];             // Add this
TCHAR szCommand2[iSize];         // Add this
TCHAR szText2[iSize];            // Add this

BEGIN_PROVIDER_COLUMN_MAP(CCustomWindowsFile)
   PROVIDER_COLUMN_ENTRY("FileAttributes", 1, dwFileAttributes)
   PROVIDER_COLUMN_ENTRY("FileSizeHigh", 2, nFileSizeHigh)
   PROVIDER_COLUMN_ENTRY("FileSizeLow", 3, nFileSizeLow)
   PROVIDER_COLUMN_ENTRY_STR("FileName", 4, cFileName)
   PROVIDER_COLUMN_ENTRY_STR("AltFileName", 5, cAlternateFileName)

   PROVIDER_COLUMN_ENTRY_STR("Command", 6, szCommand)    // Add this
   PROVIDER_COLUMN_ENTRY_STR("Text", 7, szText)          // Add this
   PROVIDER_COLUMN_ENTRY_STR("Command2", 8, szCommand2)  // Add this
   PROVIDER_COLUMN_ENTRY_STR("Text2", 9, szText2)        // Add this
END_PROVIDER_COLUMN_MAP()

   bool operator==(const CCustomWindowsFile& am) // This is optional
   {
      return (lstrcmpi(cFileName, am.cFileName) == 0);
   }
};
```

Elementy członkowskie danych `szCommand` i `szText` reprezentują dwa ciągi przy użyciu `szCommand2` i `szText2` za pomocą dodatkowych kolumn, jeśli to konieczne. Element członkowski danych `dwBookmark` nie jest wymagane dla tego prostego dostawcy tylko do odczytu, ale jest używany później dodać `IRowsetLocate` interfejsu; zobacz [udoskonalanie prostego odczytu tylko dostawcy](../../data/oledb/enhancing-the-simple-read-only-provider.md). `==` Operator porównuje wystąpienia (Implementowanie Ten operator jest opcjonalny).

Po zakończeniu tej operacji można dodawać funkcjonalność [wczytywanie ciągów do dostawcy OLE DB](../../data/oledb/reading-strings-into-the-ole-db-provider.md).

## <a name="see-also"></a>Zobacz także

[Implementowanie prostego dostawcy tylko do odczytu](../../data/oledb/implementing-the-simple-read-only-provider.md)<br/>
