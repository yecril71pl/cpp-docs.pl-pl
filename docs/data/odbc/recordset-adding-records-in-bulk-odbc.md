---
title: 'Zestaw rekordów: Dodawanie rekordów zbiorcze (ODBC) | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- ODBC recordsets, adding records
- recordsets, adding records
- bulk record additions to recordsets
ms.assetid: 4685f656-14b9-4f10-a1c5-147b2b89a0b4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 53daf818b0ba17848723e3cad233452146d1c891
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50062577"
---
# <a name="recordset-adding-records-in-bulk-odbc"></a>Zestaw rekordów: zbiorcze dodawanie rekordów (ODBC)

Ten temat dotyczy klas MFC ODBC.

MFC [CRecordset](../../mfc/reference/crecordset-class.md) klasa ma nowy optymalizacji, które zwiększa wydajność podczas dodawania nowych rekordów zbiorczo do tabeli.

> [!NOTE]
> Ten temat dotyczy obiektów pochodzących od `CRecordset` w wierszu zbiorczego, które podczas pobierania nie została zaimplementowana. Jeśli używasz zbiorcze pobieranie z wiersza, zobacz [zestaw rekordów: pobieranie rekordów w zbiorcze (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

Nowa opcja dla *dwOptions* parametr [CRecordset::Open](../../mfc/reference/crecordset-class.md#open) funkcja elementu członkowskiego `optimizeBulkAdd`, zwiększa wydajność podczas dodawania wielu rekordów pod rząd bez wywoływania `Requery` lub `Close`. Te pola, które zostały zmienione przed pierwszym `Update` wywołania są oznaczane jako zmienione kolejnych `AddNew` / `Update` wywołania.

Jeśli używasz klasy bazy danych, aby móc korzystać z `::SQLSetPos` interfejsu API ODBC funkcji dodawania, edytowania i usuwania rekordów, tego rodzaju optymalizacji jest niepotrzebne.

Jeśli jest ładowany z biblioteki kursorów ODBC lub sterownik ODBC nie obsługuje dodawania, edytowania i usuwania za pośrednictwem `::SQLSetPos`, tego rodzaju optymalizacji należy poprawić zbiorcze Dodawanie wydajności. Aby włączyć tego rodzaju optymalizacji, należy ustawić *dwOptions* parametru w `Open` wywołania dla rekordów do następującego:

```
appendOnly | optimizeBulkAdd
```

## <a name="see-also"></a>Zobacz też

[Zestaw rekordów (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Zestaw rekordów: dodawanie, aktualizowanie i usuwanie rekordów (ODBC)](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md)<br/>
[Zestaw rekordów: blokowanie rekordów (ODBC)](../../data/odbc/recordset-locking-records-odbc.md)