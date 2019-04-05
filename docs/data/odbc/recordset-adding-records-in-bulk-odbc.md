---
title: 'Zestaw rekordów: Dodawanie rekordów zbiorcze (ODBC)'
ms.date: 11/04/2016
helpviewer_keywords:
- ODBC recordsets, adding records
- recordsets, adding records
- bulk record additions to recordsets
ms.assetid: 4685f656-14b9-4f10-a1c5-147b2b89a0b4
ms.openlocfilehash: a2c3eab8bb4c0e8db76fceb5a2dafd16a4a07079
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/05/2019
ms.locfileid: "59038612"
---
# <a name="recordset-adding-records-in-bulk-odbc"></a>Zestaw rekordów: Dodawanie rekordów zbiorcze (ODBC)

Ten temat dotyczy klas MFC ODBC.

MFC [CRecordset](../../mfc/reference/crecordset-class.md) klasa ma nowy optymalizacji, które zwiększa wydajność podczas dodawania nowych rekordów zbiorczo do tabeli.

> [!NOTE]
> Ten temat dotyczy obiektów pochodzących od `CRecordset` w wierszu zbiorczego, które podczas pobierania nie została zaimplementowana. Jeśli używasz zbiorcze pobieranie z wiersza, zobacz [zestaw rekordów: Pobieranie rekordów (ODBC) zbiorcze](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

Nowa opcja dla *dwOptions* parametr [CRecordset::Open](../../mfc/reference/crecordset-class.md#open) funkcja elementu członkowskiego `optimizeBulkAdd`, zwiększa wydajność podczas dodawania wielu rekordów pod rząd bez wywoływania `Requery` lub `Close`. Te pola, które zostały zmienione przed pierwszym `Update` wywołania są oznaczane jako zmienione kolejnych `AddNew` / `Update` wywołania.

Jeśli używasz klasy bazy danych, aby móc korzystać z `::SQLSetPos` interfejsu API ODBC funkcji dodawania, edytowania i usuwania rekordów, tego rodzaju optymalizacji jest niepotrzebne.

Jeśli jest ładowany z biblioteki kursorów ODBC lub sterownik ODBC nie obsługuje dodawania, edytowania i usuwania za pośrednictwem `::SQLSetPos`, tego rodzaju optymalizacji należy poprawić zbiorcze Dodawanie wydajności. Aby włączyć tego rodzaju optymalizacji, należy ustawić *dwOptions* parametru w `Open` wywołania dla rekordów do następującego:

```
appendOnly | optimizeBulkAdd
```

## <a name="see-also"></a>Zobacz także

[Zestaw rekordów (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Zestaw rekordów: Dodawanie, aktualizowanie i usuwanie rekordów (ODBC)](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md)<br/>
[Zestaw rekordów: Blokowanie rekordów (ODBC)](../../data/odbc/recordset-locking-records-odbc.md)