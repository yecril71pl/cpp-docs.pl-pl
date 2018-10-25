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
ms.openlocfilehash: 1c1958604edbb2f9d9c10e58082e70c2df400b8c
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50077377"
---
# <a name="user-record"></a>Rekord użytkownika

Rekord użytkownika zapewnia struktury kodu i danych, który reprezentuje dane kolumn dla zestawu wierszy. Rekord użytkownika mogą być tworzone w czasie kompilacji lub w czasie wykonywania. Po utworzeniu dostawcy usługi przy użyciu biblioteki ATL OLE DB Provider kreatora, Kreator tworzy domyślny rekord użytkownika, który wygląda w następujący sposób (zakładając, że określono nazwę dostawcy [krótką nazwę] *niestandardowe*):

```cpp
class CWindowsFile:
   public WIN32_FIND_DATA
{
public:

BEGIN_PROVIDER_COLUMN_MAP(CCustomWindowsFile)
   PROVIDER_COLUMN_ENTRY("FileAttributes", 1, dwFileAttributes)
   PROVIDER_COLUMN_ENTRY("FileSizeHigh", 2, nFileSizeHigh)
   PROVIDER_COLUMN_ENTRY("FileSizeLow", 3, nFileSizeLow)
   PROVIDER_COLUMN_ENTRY_STR("FileName", 4, cFileName)
   PROVIDER_COLUMN_ENTRY_STR("AltFileName", 5, cAlternateFileName)
END_PROVIDER_COLUMN_MAP()

};
```

Szablony dostawców OLE DB obsługiwać wszystkie szczegóły OLE DB dotyczące interakcji z klientem. Uzyskanie danych kolumny służące do odpowiedzi, wywołuje dostawcę `GetColumnInfo` funkcji, które należy umieścić w rekordzie użytkownika. Można wyraźnie przezwyciężyć `GetColumnInfo` rekordów użytkowników, na przykład przez deklarując jej w plik .h jak pokazano poniżej:

```cpp
template <class T>
static ATLCOLUMNINFO* GetColumnInfo(T* pThis, ULONG* pcCols)
```

Jest to równoważne:

```cpp
static ATLCOLUMNINFO* GetColumnInfo(CommandClass* pThis, ULONG* pcCols)
static ATLCOLUMNINFO* GetColumnInfo(RowsetClass* pThis, ULONG* pcCols)
```

Należy także zaimplementować `GetColumnInfo` w pliku .cpp rekordu użytkownika.

Makra PROVIDER_COLUMN_MAP pomocy w tworzeniu `GetColumnInfo` funkcji:

- BEGIN_PROVIDER_COLUMN_MAP definiuje prototyp funkcji i statyczne tablicę `ATLCOLUMNINFO` struktury.

- PROVIDER_COLUMN_ENTRY definiuje i inicjuje pojedynczy `ATLCOLUMNINFO`.

- END_PROVIDER_COLUMN_MAP zamyka tablicy i funkcji. Również umieszcza liczba elementów tablicy do *pcCols* parametru.

Po utworzeniu rekordu użytkownika w czasie wykonywania, `GetColumnInfo` używa *pThis* parametru, aby uzyskać wskaźnik do wystąpienia polecenia lub zestaw wierszy. Polecenia i zestawy wierszy musi obsługiwać `IColumnsInfo` interfejsu, aby z tego wskaźnika można uzyskać informacji o kolumnie.

`CommandClass` i `RowsetClass` polecenia i zestawu wierszy, które rekordu użytkownika.

Aby uzyskać bardziej szczegółowy przykład sposobu zastąpienia `GetColumnInfo` w rekordzie użytkownika, zobacz [dynamicznie Określanie kolumn zwracanych do konsumenta](../../data/oledb/dynamically-determining-columns-returned-to-the-consumer.md).

## <a name="see-also"></a>Zobacz też

[Architektura szablonu dostawcy OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)