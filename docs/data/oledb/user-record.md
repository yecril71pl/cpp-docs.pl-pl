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
ms.openlocfilehash: e37ed0ac918b004513aa64308870a534a7b2af40
ms.sourcegitcommit: 840033ddcfab51543072604ccd5656fc6d4a5d3a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/29/2018
ms.locfileid: "50216295"
---
# <a name="user-record"></a>Rekord użytkownika

Rekord użytkownika zapewnia struktury kodu i danych, który reprezentuje dane kolumn dla zestawu wierszy. Rekord użytkownika mogą być tworzone w czasie kompilacji lub w czasie wykonywania. Po utworzeniu dostawcy usługi przy użyciu **Kreator biblioteki ATL OLE DB Provider**, Kreator tworzy domyślny rekord użytkownika, który wygląda w następujący sposób (zakładając, że określono nazwę dostawcy [krótką nazwę] *MyProvider*):

```cpp
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

Szablony dostawców OLE DB obsługiwać wszystkie szczegóły OLE DB na interakcje z klientem. Uzyskanie danych kolumny służące do odpowiedzi, wywołuje dostawcę `GetColumnInfo` funkcji, które należy umieścić w rekordzie użytkownika. Można wyraźnie przezwyciężyć `GetColumnInfo` rekordów użytkowników, na przykład przez deklarując jej w plik .h jak pokazano poniżej:

```cpp
template <class T>
static ATLCOLUMNINFO* GetColumnInfo(T* pThis, ULONG* pcCols) 
```

To jest równa:

```cpp
static ATLCOLUMNINFO* GetColumnInfo(CommandClass* pThis, ULONG* pcCols)
static ATLCOLUMNINFO* GetColumnInfo(RowsetClass* pThis, ULONG* pcCols)
```

Następnie należy zaimplementować `GetColumnInfo` w pliku .cpp rekordu użytkownika.

Makra PROVIDER_COLUMN_MAP pomocy w tworzeniu `GetColumnInfo` funkcji:

- BEGIN_PROVIDER_COLUMN_MAP definiuje prototyp funkcji i statyczne tablicę `ATLCOLUMNINFO` struktury.

- PROVIDER_COLUMN_ENTRY definiuje i inicjuje pojedynczy `ATLCOLUMNINFO`.

- END_PROVIDER_COLUMN_MAP zamyka tablicy i funkcji. Również umieszcza liczba elementów tablicy do *pcCols* parametru.

Po utworzeniu rekordu użytkownika w czasie wykonywania, `GetColumnInfo` używa *pThis* parametru, aby uzyskać wskaźnik do wystąpienia polecenia lub zestaw wierszy. Polecenia i zestawy wierszy musi obsługiwać `IColumnsInfo` interfejsu, więc informacji o kolumnie może zostać pobrany z tym wskaźniku.

`CommandClass` i `RowsetClass` polecenia i zestawu wierszy, które rekordu użytkownika.

Aby uzyskać bardziej szczegółowy przykład sposobu zastąpienia `GetColumnInfo` w rekordzie użytkownika, zobacz [dynamicznie Określanie kolumn zwracanych do konsumenta](../../data/oledb/dynamically-determining-columns-returned-to-the-consumer.md).

## <a name="see-also"></a>Zobacz też

[Architektura szablonu dostawcy OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)<br/>
