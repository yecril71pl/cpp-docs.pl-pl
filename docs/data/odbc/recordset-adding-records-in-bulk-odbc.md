---
title: 'Zestaw rekordów: zbiorcze dodawanie rekordów (ODBC)'
ms.date: 11/04/2016
helpviewer_keywords:
- ODBC recordsets, adding records
- recordsets, adding records
- bulk record additions to recordsets
ms.assetid: 4685f656-14b9-4f10-a1c5-147b2b89a0b4
ms.openlocfilehash: f561cb0275933a973e97ef0518148e81e14a0234
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213021"
---
# <a name="recordset-adding-records-in-bulk-odbc"></a>Zestaw rekordów: zbiorcze dodawanie rekordów (ODBC)

Ten temat dotyczy klas MFC ODBC.

Klasa MFC [CRecordset](../../mfc/reference/crecordset-class.md) ma nową optymalizację, która zwiększa wydajność, gdy do tabeli są dodawane nowe rekordy.

> [!NOTE]
> Ten temat dotyczy obiektów pochodnych `CRecordset`, w których nie zaimplementowano pobierania wierszy zbiorczych. Jeśli używasz pobierania wierszy zbiorczych, zobacz [zestaw rekordów: pobieranie rekordów zbiorczo (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

Nowa opcja dla parametru *dwOptions* do funkcji [CRecordset:: Open](../../mfc/reference/crecordset-class.md#open) member, `optimizeBulkAdd`, zwiększa wydajność w przypadku dodawania wielu rekordów po kolei bez wywoływania `Requery` lub `Close`. Tylko pola, które są zanieczyszczone przed pierwszym wywołaniem `Update` są oznaczane jako zanieczyszczone dla kolejnych `AddNew`/`Update` wywołań.

Jeśli używasz klas baz danych, aby skorzystać z funkcji `::SQLSetPos` ODBC API do dodawania, edytowania i usuwania rekordów, Ta optymalizacja nie jest konieczna.

Jeśli Biblioteka kursorów ODBC jest załadowana lub sterownik ODBC nie obsługuje dodawania, edytowania i usuwania za pośrednictwem `::SQLSetPos`, Ta optymalizacja powinna zwiększyć wydajność zbiorczą. Aby włączyć tę optymalizację, należy ustawić parametr *dwOptions* w wywołaniu `Open` dla zestawu rekordów:

```
appendOnly | optimizeBulkAdd
```

## <a name="see-also"></a>Zobacz też

[Zestaw rekordów (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Zestaw rekordów: dodawanie, aktualizowanie i usuwanie rekordów (ODBC)](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md)<br/>
[Zestaw rekordów: blokowanie rekordów (ODBC)](../../data/odbc/recordset-locking-records-odbc.md)
