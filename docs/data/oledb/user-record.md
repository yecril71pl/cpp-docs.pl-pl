---
title: Rekord użytkownika
ms.date: 11/04/2016
helpviewer_keywords:
- records, user
- OLE DB providers, user record
- user records
- user records, described
- rowsets, user record
ms.assetid: 9c0d2864-2738-4f62-a750-1016d9c3523f
ms.openlocfilehash: b37835f1a3161edd10f61f9b4e76cfb5f558e07b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62389115"
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

## <a name="see-also"></a>Zobacz także

[Architektura szablonu dostawcy OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)<br/>
