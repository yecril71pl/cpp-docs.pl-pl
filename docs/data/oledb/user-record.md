---
title: Rekord użytkownika | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- records, user
- OLE DB providers, user record
- user records
- user records, described
- rowsets, user record
ms.assetid: 9c0d2864-2738-4f62-a750-1016d9c3523f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 5c58807dac8ae320ee69c8e1a372fff5b9d3db02
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="user-record"></a>Rekord użytkownika
Rekord użytkownika zawiera struktura kodu i danych, która reprezentuje dane kolumn dla zestawu wierszy. Rekord użytkownika mogą być tworzone w czasie kompilacji lub w czasie wykonywania. Podczas tworzenia dostawcę przy użyciu ATL OLE DB Provider kreatora, Kreator tworzy domyślny rekord użytkownika, który wygląda następująco (przy założeniu, że określono nazwę dostawcy [krótką nazwę] "MyProvider"):  
  
```  
class CWindowsFile:  
   public WIN32_FIND_DATA  
{  
public:  
  
BEGIN_PROVIDER_COLUMN_MAP(CMyProviderWindowsFile)  
   PROVIDER_COLUMN_ENTRY("FileAttributes", 1, dwFileAttributes)  
   PROVIDER_COLUMN_ENTRY("FileSizeHigh", 2, nFileSizeHigh)  
   PROVIDER_COLUMN_ENTRY("FileSizeLow", 3, nFileSizeLow)  
   PROVIDER_COLUMN_ENTRY_STR("FileName", 4, cFileName)  
   PROVIDER_COLUMN_ENTRY_STR("AltFileName", 5, cAlternateFileName)  
END_PROVIDER_COLUMN_MAP()  
  
};  
```  
  
 Szablony dostawców OLE DB obsługiwać wszystkie szczegóły OLE DB dotyczące interakcji z klientem. Uzyskanie kolumny danych potrzebnych do odpowiedzi, wywołuje dostawcę `GetColumnInfo` funkcji, które należy umieścić w rekordzie użytkownika. Można jawnie przesłonić `GetColumnInfo` w rekordzie użytkownika, na przykład przez zadeklarowanie go w pliku .h w sposób pokazany poniżej:  
  
```  
template <class T>  
static ATLCOLUMNINFO* GetColumnInfo(T* pThis, ULONG* pcCols)   
```  
  
 Jest to równoważne:  
  
```  
static ATLCOLUMNINFO* GetColumnInfo(CommandClass* pThis, ULONG* pcCols)  
static ATLCOLUMNINFO* GetColumnInfo(RowsetClass* pThis, ULONG* pcCols)  
```  
  
 Musi implementować też `GetColumnInfo` w pliku .cpp rekordu użytkownika.  
  
 Makra PROVIDER_COLUMN_MAP pomoc w tworzeniu `GetColumnInfo` funkcji:  
  
-   BEGIN_PROVIDER_COLUMN_MAP definiuje prototyp funkcji i statyczne tablicę **ATLCOLUMNINFO** struktury.  
  
-   PROVIDER_COLUMN_ENTRY definiuje i inicjuje pojedynczy **ATLCOLUMNINFO**.  
  
-   END_PROVIDER_COLUMN_MAP zamyka tablicy i funkcji. Pulpit zapewnia również licznik elementów tablicy w `pcCols` parametru.  
  
 Po utworzeniu rekordu użytkownika w czasie wykonywania, **GetColumnInfo** używa `pThis` parametr, aby otrzymywać wskaźnik do zestawu wierszy lub polecenie wystąpienia. Polecenia i zestawy wierszy musi obsługiwać `IColumnsInfo` interfejsu, dlatego można uzyskać informacji o kolumnie ten wskaźnik.  
  
 **CommandClass** i **RowsetClass** polecenia i zestawu wierszy, które przy użyciu rekordu użytkownika.  
  
 Aby bardziej szczegółowy przykład zastąpić `GetColumnInfo` rekordów użytkowników, zobacz [dynamicznie Określanie kolumn zwracanych do konsumenta](../../data/oledb/dynamically-determining-columns-returned-to-the-consumer.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Architektura szablonu dostawcy OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)